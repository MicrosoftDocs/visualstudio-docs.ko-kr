---
title: 지역 주민 평가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], evaluating locals
- expression evaluation, evaluating locals
ms.assetid: 7d1ed528-4e7a-4d8f-87b4-162440644a75
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaf140a9ddbc7733da4d05450a024c0f0a713712
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738811"
---
# <a name="evaluate-locals"></a>지역 주민 평가
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

[GetPropertyInfo는](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 로컬의 값과 로컬 이름 및 형식을 얻기 위해 호출됩니다. 로컬 값은 프로그램의 현재 상태에 따라 달라지므로 로컬 값을 메모리에서 가져와야 합니다. [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 개체는 로컬을 나타내는 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 개체를 값을 포함하는 메모리의 적절한 위치에 바인딩하는 데 사용됩니다. 메모리의 이 위치는 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 개체로 표시됩니다.

로컬 값을 검색하는 이 기능은 다음 작업을 수행하는 도우미 함수에 캡슐화됩니다.

1. 개체를 `IDebugField` 메모리에 바인딩하여 `IDebugObject` 개체를 가져옵니다.

2. 메모리에서 값을 가져옵니다. 이 값은 일련의 바이트로 표시됩니다.

3. 로컬 형식을 기준으로 값을 서식지정합니다.

4. 로컬 값을 포함하는 제네릭 개체를 반환합니다. C#에서 이 것은 `object`은 이며 C++에서는 `VARIANT`이 것입니다.

## <a name="managed-code"></a>관리 코드
 이것은 관리 되는 코드에서 로컬의 값을 검색 하는 함수의 구현입니다.

```csharp
namespace EEMC
{
    internal class Field
    {
        internal static object GetValue(
            IDebugBinder binder,
            IDebugField field,
            Type t,
            uint size)
        {
            if (t == null || size == 0)  return null;

            IDebugObject debugObject = null;
            binder.Bind(null, field, out debugObject);

            byte[] buffer = new byte[size];
            for (int i = 0; i < size; i++)  buffer[i] = 0;

            debugObject.GetValue(buffer, size);

            if (t == typeof(sbyte)) return (sbyte) buffer[0];
            if (t == typeof(short)) return BitConverter.ToInt16(buffer, 0);
            if (t == typeof(int))   return BitConverter.ToInt32(buffer, 0);
            if (t == typeof(long))  return BitConverter.ToInt64(buffer, 0);
            if (t == typeof(byte))  return buffer[0];
            if (t == typeof(char))  return BitConverter.ToChar(buffer, 0);
            if (t == typeof(uint))  return BitConverter.ToUInt32(buffer, 0);
            if (t == typeof(ulong)) return BitConverter.ToUInt64(buffer, 0);
            if (t == typeof(float)) return BitConverter.ToSingle(buffer, 0);
            if (t == typeof(double))  return BitConverter.ToDouble(buffer, 0);
            if (t == typeof(bool))  return BitConverter.ToBoolean(buffer, 0);
            if (t == typeof(string))  return BitConverter.ToString(buffer, 0);
            return null;
        }
    }
}
```

## <a name="unmanaged-code"></a>관리되지 않는 코드
 이는 관리되지 않는 코드에서 로컬의 값을 검색하는 함수의 구현입니다. `FieldGetType`[로컬 값 얻기에](../../extensibility/debugger/getting-local-values.md)표시됩니다.

```cpp
HRESULT FieldGetPrimitiveValue(
    in  IDebugBinder* pbinder,
    in  IDebugField*  pfield,
    out VARIANT*      pvarValue
    )
{
    if (pvarValue == NULL)
        return E_INVALIDARG;
    else
        *pvarValue = 0;

    if (pfield == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    UINT          valueSize = 0;
    BYTE*         pvalueBits = NULL;
    IDebugObject* pobject    = NULL;

    //get the value as bits
    hr = pbinder->Bind( NULL, pfield, &pobject );
    if (FAILED(hr))
        return hr;

    hr = pobject->GetSize( &valueSize );
    if (FAILED(hr))
    {
        pobject->Release();
        return hr;
    }

    pvalueBits = reinterpret_cast<BYTE *>(malloc(valueSize * sizeof(BYTE)));
    if (!pvalueBits)
    {
        pobject->Release();
        return E_OUTOFMEMORY;
    }

    hr = pobject->GetValue( pvalueBits, valueSize );
    pobject->Release();
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //get the type
    VARIANT     valueType;

    hr = FieldGetType( pfield, &valueType );
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //copy a primitive value
    switch (valueType.vt)
    {
    case VT_BSTR:
        {
            pvarValue->vt = VT_BSTR;
            if (valueSize == 0)
                pvarValue->bstrVal = SysAllocString( OLE("") );
            else
                pvarValue->bstrVal =
                    SysAllocStringByteLen( reinterpret_cast<char*>(pvalueBits),
                                           valueSize );
        }

    case VT_BOOL:
    case VT_I1:
    case VT_I2:
    case VT_I4:
    case VT_I8:
    case VT_UI1:
    case VT_UI2:
    case VT_UI4:
    case VT_UI8:
    case VT_R4:
    case VT_R8:
        pvarValue->vt = valueType.vt;

        if (valueSize > 8)
            valueSize = 8;
        memcpy( &(pvarValue->iVal), pvalueBits, valueSize );
        break;

    case VT_VOID:
    case VT_EMPTY:
        pvarValue->vt = valueType.vt;
        break;

    default:
        //not a primitive type
        VariantClear(&valueType);
        free(pvalueBits);
        return E_FAIL;
    }

    free(pvalueBits);
    VariantClear(&valueType);
    return S_OK;
}
```

## <a name="see-also"></a>참조
- [지역 주민의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)
- [로컬 값 받기](../../extensibility/debugger/getting-local-values.md)
- [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)
