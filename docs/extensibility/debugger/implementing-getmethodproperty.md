---
title: GetMethodProperty | 구현 Microsoft Docs
description: Visual Studio 디버그 엔진의 GetDebugProperty를 사용하여 스택 프레임의 현재 메서드에 대한 정보를 가져오는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ab7b0ba5e51ba8ea47b473934e825b82dec320c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903296"
---
# <a name="implement-getmethodproperty"></a>GetMethodProperty 구현
> [!IMPORTANT]
> 2015년 Visual Studio 식 계산기를 구현하는 이 방법은 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리되는 식 계산기 샘플 를 참조하세요.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Visual Studio 디버그 엔진의 (DE) [GetDebugProperty를](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)호출합니다. 이 메서드는 [GetMethodProperty를](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 호출하여 스택 프레임의 현재 메서드에 대한 정보를 얻습니다.

이 `IDebugExpressionEvaluator::GetMethodProperty` 구현은 다음 작업을 수행합니다.

1. [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 개체를 전달하여 [GetContainerField를](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)호출합니다. SP(기호 공급자)는 지정된 주소를 포함하는 메서드를 나타내는 [IDebugContainerField를](../../extensibility/debugger/reference/idebugcontainerfield.md) 반환합니다.

2. 에서 [IDebugMethodField를](../../extensibility/debugger/reference/idebugmethodfield.md) `IDebugContainerField` 얻습니다.

3. `CFieldProperty` [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 구현하고 SP에서 반환된 개체를 포함하는 클래스(이 예제에서는 호출)를 `IDebugMethodField` 인스턴스화합니다.

4. `IDebugProperty2`개체에서 인터페이스를 `CFieldProperty` 반환합니다.

## <a name="managed-code"></a>관리 코드
이 예제에서는 관리 코드에서 의 `IDebugExpressionEvaluator::GetMethodProperty` 구현을 보여줍니다.

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

## <a name="unmanaged-code"></a>비 관리 코드
이 예제에서는 비 관리 코드에서 의 구현을 `IDebugExpressionEvaluator::GetMethodProperty` 보여줍니다.

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
- [로컬의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)
