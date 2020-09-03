---
title: 로컬 값을 가져오는 중 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, local values
- debugging [Debugging SDK], local values
- expression evaluation, getting local values
ms.assetid: a10b0764-65ac-476f-bf42-b4a9c38e20de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75cc530f13de22a994eff70492f340059d2a5839
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738612"
---
# <a name="get-local-values"></a>로컬 값 가져오기
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

로컬의 값을 가져오기 위해 Visual Studio는 해당 로컬에 대해 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 를 호출 합니다. 이 구현에서 클래스는 `CFieldProperty` 각 지역에 대 한 IDebugProperty2 인터페이스를 구현 합니다.

이 구현 `IDebugProperty2::GetPropertyInfo` 에서는 다음 작업을 수행 합니다.

1. 클래스가 인스턴스화되고 초기화 될 때 채워진 [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) 구조체에서 로컬의 이름, 속성 및 특성을 가져옵니다.

2. [Idebugfield](../../extensibility/debugger/reference/idebugfield.md) 개체에서 로컬의 유형을 가져옵니다.

3. 개체에서 로컬 값을 가져옵니다 `IDebugField` . 이 필드는 [Idebugbinder](../../extensibility/debugger/reference/idebugbinder.md) 개체를 사용 하 여 로컬의 메모리 위치에 바인딩되고 결과 [idebugbinder](../../extensibility/debugger/reference/idebugobject.md) 개체에서 값을 가져옵니다.

4. [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 구조체에서 요청 된 모든 속성을 반환 합니다.

## <a name="managed-code"></a>관리 코드
이 예제에서는 `IDebugProperty2::GetPropertyInfo` 관리 코드에서 메서드의 로컬에 대 한의 구현을 보여 줍니다. 또한 `Field.GetType` 필드 형식을 가져오는 데 사용 되는 도우미 함수를 보여 줍니다. `Field.GetValue` 는 [지역 평가](../../extensibility/debugger/evaluating-locals.md)에 표시 됩니다. 도우미 함수 `Field.MapModifiersToAttributes` (표시 되지 않음)는 단순히 필드의 [FIELD_MODIFIERS](../../extensibility/debugger/reference/field-modifiers.md) 플래그를 [DBG_ATTRIB_FLAGS](../../extensibility/debugger/reference/dbg-attrib-flags.md) 값으로 변환 합니다.

```csharp
namespace EEMC
{
    public class CFieldProperty : IDebugProperty2
    {
        public HRESULT GetPropertyInfo(
            uint                  dwFields,
            uint                  radix,
            uint                  timeout,
            IDebugReference2[]    refArgs,
            uint                  argCount,
            DEBUG_PROPERTY_INFO[] infoArray)
        {
            DEBUGPROP_INFO_FLAGS flags = (DEBUGPROP_INFO_FLAGS) dwFields;
            DEBUGPROP_INFO_FLAGS infoFields = DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_NONE;

            // Initialize the structure.
            DEBUG_PROPERTY_INFO info = infoArray[0];
            info.pProperty = null;

            // Fill in the full name, if requested.
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_FULLNAME))
            {
                info.bstrFullName = fieldInfo.bstrFullName;
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_FULLNAME;
            }
            // Fill in the name, if requested.
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_NAME))
            {
                info.bstrName = fieldInfo.bstrName;
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_NAME;
            }
            // Fill in the type, if requested.
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_TYPE))
            {
                if (fieldType == null)
                    fieldType = Field.GetType(field, out fieldSize);
                if (fieldType == null)
                    info.bstrType = "unknown";
                else
                    info.bstrType = fieldType.ToString();
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_TYPE;
            }
            // The property associated with this property is this property.
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_PROP))
            {
                info.pProperty = this;
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_PROP;
            }
            // Get the property value, if requested.
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_VALUE))
            {
                if (fieldType == null)
                    fieldType = Field.GetType(field, out fieldSize);
                if (fieldType == null)
                    info.bstrValue = "?";
                else
                {
                    object o = Field.GetValue(binder, field, fieldType, fieldSize);
                    if (o == null)
                        info.bstrValue = "?";
                    else
                        info.bstrValue = o.ToString();
                }
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_VALUE;
            }
            // Get the property attributes, if requested.
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_ATTRIB))
            {
                info.dwAttrib =
                    (ulong) Field.MapModifiersToAttributes(
                        (FIELD_MODIFIERS) fieldInfo.dwModifiers,
                        fieldKind);
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_ATTRIB;
            }
            info.dwFields = (uint) infoFields;
            infoArray[0] = info;
            return COM.S_OK;
        }
    }

//----------------------------------------------------------------------------

    internal class Field
    {
        internal static Type GetType(IDebugField field, out uint size)
        {
            size = 0;

            IDebugField fieldType = null;
            field.GetType(out fieldType);
            if (fieldType == null)  return null;

            // Get field size.
            fieldType.GetSize(out size);

            // Get approximate type name.
            FIELD_INFO[] fieldTypeInfo = new FIELD_INFO[1];
            fieldType.GetInfo((uint) FIELD_INFO_FIELDS.FIF_NAME,
                fieldTypeInfo);

            // Map approximate name to type name.
            switch (fieldTypeInfo[0].bstrName)
            {
                case "whole":
                switch (size)
                {
                    case 1: return typeof(sbyte);
                    case 2: return typeof(short);
                    case 4: return typeof(int);
                    case 8: return typeof(long);
                }
                    break;
                case "uwhole":
                switch (size)
                {
                    case 1: return typeof(byte);
                    case 2: return typeof(char);
                    case 4: return typeof(uint);
                    case 8: return typeof(ulong);
                }
                    break;
                case "real":
                switch (size)
                {
                    case 4: return typeof(float);
                    case 8: return typeof(double);
                }
                    break;
                case "bool": return typeof(bool);
                case "string": return typeof(string);
            }
            return null;
        }
}
```

## <a name="unmanaged-code"></a>비관리 코드
 이 예제에서는 `IDebugProperty2::GetPropertyInfo` 비관리 코드에서 메서드의 로컬에 대 한의 구현을 보여 줍니다. 또한 두 개의 도우미 함수도 보여 주며 `FieldGetType` , `FieldGetValue` 각각 필드의 형식과 값을 가져오는 데 사용 됩니다. 는 `VARIANT` 필드의 값 및 형식에 사용 되며 `VARIANT` 다양 한 값 형식을 처리할 수 있습니다. 이 구현에서는 `FieldGetValue` 나중에에 대 한 호출에서 값으로 변환 된 [Idebugfield](../../extensibility/debugger/reference/idebugfield.md) 개체를 반환 `FieldGetPrimitiveValue` 합니다 .이 개체는 [지역 평가](../../extensibility/debugger/evaluating-locals.md)에 표시 됩니다.

```cpp
STDMETHODIMP CFieldProperty::GetPropertyInfo(
    in  DEBUGPROP_INFO_FLAGS infoFlags,
    in  DWORD                radix,
    in  DWORD                timeout,
    in  IDebugReference2**   ppargs,
    in  DWORD                argCount,
    out DEBUG_PROPERTY_INFO* ppropertyInfo
    )
{
    if (!ppropertyInfo)
        return E_INVALIDARG;
    else
        memset(ppropertyInfo,0,sizeof(*ppropertyInfo));

    if (infoFlags & DEBUGPROP_INFO_FULLNAME)
    {
        ppropertyInfo->dwFields |= DEBUGPROP_INFO_FULLNAME;
        ppropertyInfo->bstrFullName = SysAllocString( m_fieldInfo.bstrFullName );
    }

    if (infoFlags & DEBUGPROP_INFO_NAME)
    {
        ppropertyInfo->dwFields |= DEBUGPROP_INFO_NAME;
        ppropertyInfo->bstrName  = SysAllocString( m_fieldInfo.bstrName );
    }

    if (infoFlags & DEBUGPROP_INFO_TYPE)
    {
        ppropertyInfo->dwFields |= DEBUGPROP_INFO_TYPE;

        VARIANT type;
        if (SUCCEEDED(FieldGetType( m_field, &type )))
        {
            // Convert the variant's type to a string
            VariantTypeToString( type, &(ppropertyInfo->bstrType) );
            VariantClear(&type);

        }
        if (ppropertyInfo->bstrType == NULL)
            ppropertyInfo->bstrType = SysAllocString( GetString(IDS_MSG_UNKNOWNTYPE) );
    }

    if (infoFlags & DEBUGPROP_INFO_PROP)
    {
        ppropertyInfo->dwFields |= DEBUGPROP_INFO_PROP;
        QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(&(ppropertyInfo->pProperty)) );
    }

    if (infoFlags & DEBUGPROP_INFO_VALUE)
    {
        ppropertyInfo->dwFields |= DEBUGPROP_INFO_VALUE;

        //only show primitive values
        VARIANT value;
        if (SUCCEEDED(FieldGetValue(m_field, &value)))
        {
            VariantValueToString( radix, m_binder, value,
                                  &(ppropertyInfo->bstrValue) );
            VariantClear(&value);
        }

        if (ppropertyInfo->bstrValue == NULL)
            ppropertyInfo->bstrValue = SysAllocString( GetString(IDS_MSG_UNKNOWNVALUE) );
    }

    if (infoFlags & DEBUGPROP_INFO_VALUE_AUTOEXPAND)
    {
    // AUTOEXPAND is ignored in this example
    }

    if (infoFlags & DEBUGPROP_INFO_ATTRIB)
    {
        ppropertyInfo->dwFields |= DEBUGPROP_INFO_ATTRIB;

        FIELD_MODIFIERS   modifiers = m_fieldInfo.dwModifiers;
        DBG_ATTRIB_FLAGS  attrib    = DBG_ATTRIB_NONE;

        //access
        if (modifiers & FIELD_MOD_ACCESS_PUBLIC)
            attrib |= DBG_ATTRIB_ACCESS_PUBLIC;
        if (modifiers & FIELD_MOD_ACCESS_PRIVATE)
            attrib |= DBG_ATTRIB_ACCESS_PRIVATE;
        if (modifiers & FIELD_MOD_ACCESS_PROTECTED)
            attrib |= DBG_ATTRIB_ACCESS_PROTECTED;
        if (modifiers & FIELD_MOD_FINAL)
            attrib |= DBG_ATTRIB_ACCESS_FINAL;

        //constant
        if (modifiers & FIELD_MOD_CONSTANT)
            attrib |= DBG_ATTRIB_VALUE_READONLY;

        //storage
        if (m_fieldKind & FIELD_SYM_GLOBAL)
            attrib |= DBG_ATTRIB_STORAGE_GLOBAL;
        if (modifiers & FIELD_MOD_STATIC)
            attrib |= DBG_ATTRIB_STORAGE_STATIC;

        //type modifier
        if (modifiers & FIELD_MOD_VIRTUAL)
            attrib |= DBG_ATTRIB_TYPE_VIRTUAL;
        if (modifiers & FIELD_MOD_CONSTANT)
            attrib |= DBG_ATTRIB_TYPE_CONSTANT;
        if (modifiers & FIELD_MOD_SYNCHRONIZED)
            attrib |= DBG_ATTRIB_TYPE_SYNCHRONIZED;
        if (modifiers & FIELD_MOD_VOLATILE)
            attrib |= DBG_ATTRIB_TYPE_VOLATILE;

        //type
        if (m_fieldKind & FIELD_TYPE_METHOD)
            attrib |= DBG_ATTRIB_METHOD;
        if (m_fieldKind & FIELD_TYPE_PROP)
            attrib |= DBG_ATTRIB_PROPERTY;
        if (m_fieldKind & FIELD_TYPE_CLASS)
            attrib |= DBG_ATTRIB_CLASS;
        if (m_fieldKind & FIELD_TYPE_INTERFACE)
            attrib |= DBG_ATTRIB_INTERFACE;
        if (m_fieldKind & FIELD_TYPE_INNERCLASS)
            attrib |= DBG_ATTRIB_INNERCLASS;
        if (m_fieldKind & FIELD_KIND_SYMBOL)
            attrib |= DBG_ATTRIB_DATA;

        //set the debug attributes
        ppropertyInfo->dwAttrib = attrib;
    }

    return S_OK;
}

//////////////////////////////////////////////////////////////////////
// Helper functions

struct PrimitiveTypeInfo
{
    LPCOLESTR  pszName;
    UINT       size;
    VARTYPE    vt;
};

PrimitiveTypeInfo primitiveTypeTable[] =
{
    { OLE("string"),    0,    VT_BSTR },
    { OLE("whole"),     1,    VT_I1   },
    { OLE("whole"),     2,    VT_I2   },
    { OLE("whole"),     4,    VT_I4   },
    { OLE("whole"),     8,    VT_I8   },
    { OLE("uwhole"),    1,    VT_UI1  },
    { OLE("uwhole"),    2,    VT_UI2  },
    { OLE("uwhole"),    4,    VT_UI4  },
    { OLE("uwhole"),    8,    VT_UI8  },
    { OLE("real"),      4,    VT_R4   },
    { OLE("real"),      8,    VT_R8   },
    { OLE("bool"),      1,    VT_BOOL },
    { OLE("bool"),      2,    VT_BOOL },
    { OLE("bool"),      4,    VT_BOOL },

    { OLE("System.String"),   0,  VT_BSTR },
    { OLE("System.SByte"),    1,  VT_I1   },
    { OLE("System.Int16"),    2,  VT_I2   },
    { OLE("System.Int32"),    4,  VT_I4   },
    { OLE("System.Int64"),    8,  VT_I8   },
    { OLE("System.Byte"),     1,  VT_UI1  },
    { OLE("System.Char"),     1,  VT_UI2  },
    { OLE("System.UInt16"),   2,  VT_UI2  },
    { OLE("System.UInt32"),   4,  VT_UI4  },
    { OLE("System.UInt64"),   8,  VT_UI8  },
    { OLE("System.Single"),   4,  VT_R4   },
    { OLE("System.Double"),   8,  VT_R8   },
    { OLE("System.Boolean"),  1,  VT_BOOL },
    { OLE("System.Boolean"),  2,  VT_BOOL },
    { OLE("System.Boolean"),  4,  VT_BOOL },

    { NULL, 0, VT_EMPTY }
};

HRESULT FieldGetType( in IDebugField* pfield, out VARIANT* pvarType )
{
    HRESULT hr;

    if (pfield == NULL)
        return E_INVALIDARG;
    if (pvarType == NULL)
        return E_INVALIDARG;
    else
        *pvarType = 0;

    //get type size and name
    DWORD        fieldTypeSize;
    FIELD_INFO   fieldTypeInfo;
    IDebugField* pfieldType = NULL;

    hr = pfield->GetType( &pfieldType );
    if (FAILED(hr))
        return hr;

    hr = pfieldType->GetSize( &fieldTypeSize );
    if (FAILED(hr))
    {
        pfieldType->Release();
        return hr;
    }

    hr = pfieldType->GetInfo( FIF_NAME, &fieldTypeInfo );
    if (FAILED(hr))
    {
        pfieldType->Release();
        return hr;
    }

    //check for primitive types
    memset( pvarType, 0, sizeof(*pvarType) );
    VariantInit(pvarType);

    for (PrimitiveTypeInfo* pprimTypeInfo = primitiveTypeTable;
         pprimTypeInfo->pszName != NULL;
         pprimTypeInfo++)
    {
        if (pprimTypeInfo->size == fieldTypeSize &&
           (wcscmp(pprimTypeInfo->pszName,fieldTypeInfo.bstrName) == 0))
        {
            pvarType->vt = pprimTypeInfo->vt;
            break;
        }
    }

    //VT_UNKNOWN is used for all other (structured) types
    if (pvarType->vt == VT_EMPTY)
    {
        pvarType->vt      = VT_UNKNOWN;
        pvarType->punkVal = pfieldType;
        pvarType->punkVal->AddRef();
    }

    if (fieldTypeInfo.bstrName != NULL)
        SysFreeString(fieldTypeInfo.bstrName);
    pfieldType->Release();
    return S_OK;
}

//----------------------------------------------------------------------------

HRESULT FieldGetValue( in IDebugField* pfield, out VARIANT* pvarValue )
{
    if (pvarValue == NULL)
        return E_INVALIDARG;
    else
        *pvarValue = 0;
    if (pfield == NULL)
        return E_INVALIDARG;

    //we delay getting the primitive value by just setting VT_UNKNOWN
    pvarValue->vt      = VT_UNKNOWN;
    pvarValue->punkVal = pfield;
    pvarValue->punkVal->AddRef();

    return S_OK;
}
```

## <a name="see-also"></a>추가 정보
- [로컬의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)
- [로컬 속성 가져오기](../../extensibility/debugger/getting-local-properties.md)
- [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)
