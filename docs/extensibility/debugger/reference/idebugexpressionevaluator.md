---
title: IDebugExpressionEvaluator | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729377"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

이 인터페이스는 식 계산기를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
식 계산기는이 인터페이스를 구현 해야 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
이 인터페이스를 얻으려면 `CoCreateInstance` 평가기의 클래스 ID (CLSID)를 사용 하 여 메서드를 통해 식 계산기를 인스턴스화합니다. 예제를 참조 하세요.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는의 메서드를 보여 줍니다 `IDebugExpressionEvaluator` .

|메서드|설명|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|식 문자열을 구문 분석 된 식으로 변환 합니다.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|메서드의 지역 변수, 인수 및 기타 속성을 가져옵니다.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|메서드 위치와 오프셋을 메모리 주소로 변환 합니다.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|인쇄 가능한 결과를 만드는 데 사용할 언어를 결정 합니다.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|레지스트리 루트를 설정 합니다. 병렬 디버깅에 사용 됩니다.|

## <a name="remarks"></a>설명
일반적인 상황에서 디버그 엔진 (DE)은 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)에 대 한 호출의 결과로 식 계산기 (EE)를 인스턴스화합니다. DE는 사용 하려는 EE의 언어와 공급 업체를 인식 하기 때문에 레지스트리에서 EE의 CLSID를 가져옵니다. 디버깅 함수를 [위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 는 `GetEEMetric` 이 검색을 지원 합니다.

EE를 인스턴스화한 후 DE는 [구문](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 분석을 호출 하 여 식을 구문 분석 하 고 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 개체에 저장 합니다. 나중에 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 에 대 한 호출은 식을 계산 합니다.

## <a name="requirements"></a>요구 사항
헤더: ee. h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>예
이 예제에서는 기호 공급자와 소스 코드의 주소가 지정 된 경우 식 계산기를 인스턴스화하는 방법을 보여 줍니다. 이 예제에서는 `GetEEMetric` 디버깅 라이브러리 dbgmetric의 [SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 에서 함수를 사용 합니다.

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

## <a name="see-also"></a>추가 정보
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
