---
title: 식 평가의 샘플 구현 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713106"
---
# <a name="sample-implementation-of-expression-evaluation"></a>식 평가의 샘플 구현
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 **보기** 창 표현식의 경우 Visual [Studio는 ParseText를](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 호출하여 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체를 생성합니다. `IDebugExpressionContext2::ParseText`는 식 평가기(EE)를 인스턴스화하고 [구문 분석(Parse)을](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 호출하여 [IDebugParsedExpression 개체를](../../extensibility/debugger/reference/idebugparsedexpression.md) 가져옵니다.

 는 `IDebugExpressionEvaluator::Parse` 다음 작업을 수행합니다.

1. [C++ 전용] 오류를 찾기 위해 식을 구문 분석합니다.

2. 인터페이스를 실행하고 구문 `CParsedExpression` 분석할 식을 클래스에 저장하는 클래스(이 예제에서 호출)를 인스턴스화합니다. `IDebugParsedExpression`

3. 개체에서 `IDebugParsedExpression` 인터페이스를 `CParsedExpression` 반환합니다.

> [!NOTE]
> MyCEE 샘플의 다음 예제와 식 계산기는 구문 분석과 평가구를 분리하지 않습니다.

## <a name="managed-code"></a>관리 코드
 다음 코드는 관리 `IDebugExpressionEvaluator::Parse` 코드의 구현을 보여 주며, 이 메서드 버전은 구문 분석코드도 동시에 평가할 때 [EvaluateSync에](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 대한 구문 분석(Watch 식 평가 참조)로 구문 [분석이](../../extensibility/debugger/evaluating-a-watch-expression.md)연기됩니다.

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

## <a name="unmanaged-code"></a>관리되지 않는 코드
다음 코드는 관리되지 `IDebugExpressionEvaluator::Parse` 않는 코드의 구현입니다. 이 메서드는 도우미 함수를 `Parse`호출하여 식을 구문 분석하고 오류를 확인하지만 이 메서드는 결과 값을 무시합니다. 공식 평가는 평가되는 동안 식이 구문 분석되는 [EvaluateSync로](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 연기됩니다(Watch [식 평가](../../extensibility/debugger/evaluating-a-watch-expression.md)참조).

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
- [감시 창 표현식 평가](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [시계 표현식 평가](../../extensibility/debugger/evaluating-a-watch-expression.md)
