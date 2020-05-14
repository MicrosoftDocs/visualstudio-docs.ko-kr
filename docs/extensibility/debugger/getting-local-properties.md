---
title: 로컬 프로퍼티 얻기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e084f28257ddede388468f36e1635e87c8f65961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738624"
---
# <a name="get-local-properties"></a>로컬 속성 받기
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

비주얼 스튜디오는 [에이넘아이들을](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 호출하여 **지역 주민** 창에 표시할 모든 지역 주민에 대한 액세스를 제공하는 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 개체를 가져옵니다. 그런 다음 Visual Studio를 [호출하여](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 각 로컬에 대해 표시할 정보를 가져옵니다. 이 예제에서 클래스는 `CEnumPropertyInfo` 인터페이스를 `IEnumDebugPropertyInfo2` 구현합니다.

이 구현은 다음 작업을 `IEnumDebugPropertyInfo2::Next` 수행합니다.

1. 정보가 저장될 배열을 지웁히 됩니다.

2. 각 로컬에 대해 [Next를](../../extensibility/debugger/reference/ienumdebugfields-next.md) 호출하여 반환되는 배열에 반환된 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 저장합니다. 이 `CEnumPropertyInfo` 클래스가 인스턴스화되었을 때 [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) 개체가 제공되었습니다.

## <a name="managed-code"></a>관리 코드
이 예제에서는 관리 `IEnumDebugPropertyInfo2::EnumChildren` 코드에서 메서드의 지역 메서드에 대한 구현을 보여 주며 있습니다.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>관리되지 않는 코드
 이 예제에서는 관리되지 않는 코드에서 메서드의 지역 `IEnumDebugPropertyInfo2::EnumChildren` 메서드에 대한 구현을 보여 주습니다.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>참조
- [지역 주민의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)
- [지역 주민 을 내사](../../extensibility/debugger/enumerating-locals.md)
