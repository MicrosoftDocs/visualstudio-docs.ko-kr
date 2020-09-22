---
title: 식 계산의 샘플 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713106"
---
# <a name="sample-implementation-of-expression-evaluation"></a>식 계산의 샘플 구현
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 **조사식** 창 식의 경우 Visual Studio는 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 를 호출 하 여 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체를 생성 합니다. `IDebugExpressionContext2::ParseText` 식 계산기 (EE)를 인스턴스화하고 [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 을 호출 하 여 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 개체를 가져옵니다.

 는 `IDebugExpressionEvaluator::Parse` 다음 작업을 수행 합니다.

1. [C + + 전용] 식을 구문 분석 하 여 오류를 찾습니다.

2. `CParsedExpression`인터페이스를 실행 하 `IDebugParsedExpression` 고 구문 분석할 식을 클래스에 저장 하는 클래스 (이 예제에서는 호출 됨)를 인스턴스화합니다.

3. `IDebugParsedExpression`개체에서 인터페이스를 반환 합니다 `CParsedExpression` .

> [!NOTE]
> 다음 예제와 MyCEE 샘플에서 식 계산기는 계산의 구문 분석을 구분 하지 않습니다.

## <a name="managed-code"></a>관리 코드
 다음 코드에서는 관리 코드에서의 구현을 보여 줍니다 `IDebugExpressionEvaluator::Parse` . 이 버전의 메서드는 구문 분석을 위한 코드도 동시에 계산 되기 때문에 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 에 대 한 구문 분석을 지연 시킵니다 ( [조사식 식 계산](../../extensibility/debugger/evaluating-a-watch-expression.md)참조).

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
다음 코드는 `IDebugExpressionEvaluator::Parse` 비관리 코드에서의 구현입니다. 이 메서드는 도우미 함수를 호출 `Parse` 하 여 식을 구문 분석 하 고 오류를 확인 하지만,이 메서드는 결과 값을 무시 합니다. 식이 계산 되는 동안 식이 구문 분석 되는 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 로 공식 평가가 지연 됩니다 ( [조사식 계산](../../extensibility/debugger/evaluating-a-watch-expression.md)참조).

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
- [조사식 창 식 계산](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [조사식 식 계산](../../extensibility/debugger/evaluating-a-watch-expression.md)
