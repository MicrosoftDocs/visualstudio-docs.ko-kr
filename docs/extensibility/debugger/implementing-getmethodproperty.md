---
title: GetMethodProperty 구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 252d09eee9c69ca75cb46d28dde807f2c500737f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738521"
---
# <a name="implement-getmethodproperty"></a>GetMethodProperty 구현
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

Visual Studio는 디버그 엔진의 (DE) [GetDebugProperty를](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)호출하며, 이 디버그속성은 [GetMethodProperty를](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 호출하여 스택 프레임의 현재 메서드에 대한 정보를 가져옵니다.

이 구현은 다음 작업을 `IDebugExpressionEvaluator::GetMethodProperty` 수행합니다.

1. [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 개체에서 전달하는 [GetContainerField를](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)호출합니다. SP(심볼 공급자)는 지정된 주소를 포함하는 메서드를 나타내는 [IDebugContainerField를](../../extensibility/debugger/reference/idebugcontainerfield.md) 반환합니다.

2. 에서 [IDebugMethodField를](../../extensibility/debugger/reference/idebugmethodfield.md) `IDebugContainerField`가져옵니다.

3. [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 `CFieldProperty` 구현 하 고 SP에서 반환 된 `IDebugMethodField` 개체를 포함 하는 클래스 (이 예제에서 호출)를 인스턴스화 합니다.

4. 개체에서 `IDebugProperty2` 인터페이스를 `CFieldProperty` 반환합니다.

## <a name="managed-code"></a>관리 코드
이 예제에서는 관리 `IDebugExpressionEvaluator::GetMethodProperty` 코드의 구현을 보여 주며, 이 예제에서는 관리 되는 코드의 구현을 보여 주실 수 있습니다.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        public HRESULT GetMethodProperty(
                IDebugSymbolProvider symbolProvider,
                IDebugAddress        address,
                IDebugBinder         binder,
                int                  includeHiddenLocals,
            out IDebugProperty2      property)
        {
            IDebugContainerField containerField = null;
            IDebugMethodField methodField       = null;
            property = null;

            // Get the containing method field.
            symbolProvider.GetContainerField(address, out containerField);
            methodField = (IDebugMethodField) containerField;

            // Return the property of method field.
            property = new CFieldProperty(symbolProvider, address, binder, methodField);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>관리되지 않는 코드
이 예제에서는 관리되지 않는 코드의 `IDebugExpressionEvaluator::GetMethodProperty` 구현을 보여 주습니다.

```
[CPP]
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(
        in IDebugSymbolProvider *pprovider,
        in IDebugAddress        *paddress,
        in IDebugBinder         *pbinder,
        in BOOL                  includeHiddenLocals,
        out IDebugProperty2    **ppproperty
    )
{
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    IDebugContainerField* pcontainer = NULL;

    hr = pprovider->GetContainerField(paddress, &pcontainer);
    if (FAILED(hr))
        return hr;

    IDebugMethodField*    pmethod    = NULL;
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod));
    pcontainer->Release();
    if (FAILED(hr))
        return hr;

    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,
                                                         paddress,
                                                         pbinder,
                                                         pmethod );
    pmethod->Release();
    if (!pfieldProperty)
        return E_OUTOFMEMORY;

    hr = pfieldProperty->Init();
    if (FAILED(hr))
    {
        pfieldProperty->Release();
        return hr;
    }

    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,
            reinterpret_cast<void**>(ppproperty));
    pfieldProperty->Release();

    return hr;
}
```

## <a name="see-also"></a>참조
- [지역 주민의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)
