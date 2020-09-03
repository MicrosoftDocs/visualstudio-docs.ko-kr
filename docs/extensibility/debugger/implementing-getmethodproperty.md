---
title: GetMethodProperty 구현 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738521"
---
# <a name="implement-getmethodproperty"></a>GetMethodProperty 구현
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

Visual Studio는 디버그 엔진의 [Getdebugproperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)를 호출 하며,이는 [getdebugproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 를 호출 하 여 스택 프레임의 현재 메서드에 대 한 정보를 가져옵니다.

이 구현 `IDebugExpressionEvaluator::GetMethodProperty` 에서는 다음 작업을 수행 합니다.

1. [Idebugaddress](../../extensibility/debugger/reference/idebugaddress.md) 개체를 전달 하 여 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)를 호출 합니다. SP (기호 공급자)는 지정 된 주소가 포함 된 메서드를 나타내는 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 을 반환 합니다.

2. 에서 [Idebugmethodfield](../../extensibility/debugger/reference/idebugmethodfield.md) 를 가져옵니다 `IDebugContainerField` .

3. `CFieldProperty` [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 구현 하 고 SP에서 반환 된 개체를 포함 하는 클래스 (이 예제에서는 호출 됨)를 인스턴스화합니다 `IDebugMethodField` .

4. `IDebugProperty2`개체에서 인터페이스를 반환 합니다 `CFieldProperty` .

## <a name="managed-code"></a>관리 코드
이 예제에서는 관리 코드에서의 구현을 보여 줍니다 `IDebugExpressionEvaluator::GetMethodProperty` .

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

## <a name="unmanaged-code"></a>비관리 코드
이 예제에서는 비관리 코드에서의 구현을 보여 줍니다 `IDebugExpressionEvaluator::GetMethodProperty` .

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

## <a name="see-also"></a>추가 정보
- [로컬의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)
