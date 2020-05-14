---
title: IDebug표현평가자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729377"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

이 인터페이스는 식 계산기나타냅니다.

## <a name="syntax"></a>구문

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
식 계산기는 이 인터페이스를 구현해야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
이 인터페이스를 얻으려면 계산기의 클래스 ID(CLSID)를 사용하여 메서드를 `CoCreateInstance` 통해 식 계산기를 인스턴스화합니다. 예제를 참조하십시오.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 의 `IDebugExpressionEvaluator`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[구문 분석](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|식 문자열을 구문 분석된 식으로 변환합니다.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|메서드의 로컬 변수, 인수 및 기타 속성을 가져옵니다.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|메서드 위치와 오프셋을 메모리 주소로 변환합니다.|
|[Setlocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|인쇄 가능한 결과를 만드는 데 사용할 언어를 결정합니다.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|레지스트리 루트를 설정합니다. 나란히 디버깅하는 데 사용됩니다.|

## <a name="remarks"></a>설명
일반적인 상황에서 DE버그 엔진(DE)은 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)에 대한 호출의 결과로 식 평가기(EE)를 인스턴스화합니다. DE는 사용하려는 EE의 언어와 공급업체를 알고 있기 때문에 DE는 레지스트리에서 EE의 CLSID를 가져옵니다(디버깅 [함수를 위한 SDK 도우미,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `GetEEMetric`이 검색을 사용하는 데 도움이).

EE가 인스턴스화되면 [DE는 구문](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 분석하여 구문 분석하여 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 개체에 저장합니다. 나중에 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 호출은 식을 평가합니다.

## <a name="requirements"></a>요구 사항
헤더: ee.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="example"></a>예제
이 예제에서는 기호 공급자와 소스 코드의 주소가 지정된 식 계산기를 인스턴스화하는 방법을 보여 주었습니다. 이 예제에서는 디버깅 라이브러리에 대한 `GetEEMetric` [SDK 도우미의](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 함수, dbgmetric.lib를 사용합니다.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
