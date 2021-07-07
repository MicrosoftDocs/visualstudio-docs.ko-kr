---
title: 식 평가 샘플 구현 | Microsoft Docs
description: Visual Studio가 ParseText를 호출하여 조사식 창 식에 대한 IDebugExpression2 개체를 생성하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de0e052fd42f1603889f7521a1e45e50b0f36eea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902308"
---
# <a name="sample-implementation-of-expression-evaluation"></a>식 평가 샘플 구현
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현하는 이 방법은 더 이상 사용되지 않습니다. CLR 식 계산기를 구현하는 방법에 관한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리형 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조하세요.

 **조사식** 창 식의 경우 Visual Studio는 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)를 호출하여 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체를 생성합니다. `IDebugExpressionContext2::ParseText`는 EE(식 계산기)를 인스턴스화하고 [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)를 호출하여 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 개체를 가져옵니다.

 `IDebugExpressionEvaluator::Parse`는 다음 작업을 수행합니다.

1. [C++에만 해당] 식을 구문 분석하여 오류를 찾습니다.

2. `IDebugParsedExpression` 인터페이스를 실행하고 구문 분석할 식을 클래스에 저장하는 클래스(이 예제에서는 `CParsedExpression`이라고 함)를 인스턴스화합니다.

3. `CParsedExpression` 개체에서 `IDebugParsedExpression` 인터페이스를 반환합니다.

> [!NOTE]
> 뒤에 오는 예제와 MyCEE 샘플에서 식 계산기는 구문 분석을 평가와 구별하지 않습니다.

## <a name="managed-code"></a>관리 코드
 다음 코드는 관리 코드에서 `IDebugExpressionEvaluator::Parse` 구현을 보여 줍니다. 이 버전의 메서드는 구문 분석 코드가 동시에 평가될 때 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)에 대한 구문 분석을 연기합니다([조사식 식 평가](../../extensibility/debugger/evaluating-a-watch-expression.md) 참조).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>비관리 코드
다음 코드는 비관리 코드에서 `IDebugExpressionEvaluator::Parse`의 구현입니다. 이 메서드는 도우미 함수 `Parse`를 호출하여 식을 구문 분석하고 오류를 확인하지만 이 메서드는 결과 값을 무시합니다. 식이 평가되는 동안 구문 분석되는 경우 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)에 대한 정형 평가가 지연됩니다([조사식 식 평가](../../extensibility/debugger/evaluating-a-watch-expression.md) 참조).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>참조
- [조사식 창 식 평가](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [조사식 식 평가](../../extensibility/debugger/evaluating-a-watch-expression.md)
