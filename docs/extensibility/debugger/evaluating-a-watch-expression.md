---
title: 시계 표현식 평가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a239e430338e88a0be4bc35ad1c357925f7d8f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738861"
---
# <a name="evaluate-a-watch-expression"></a>시계 표현식 평가
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

Visual Studio에서 시계 식의 값을 표시할 준비가 되면 [EvaluateSync를](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)호출하고 이 값을 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)를 호출합니다. 이 프로세스는 식의 값과 형식을 포함하는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체를 생성합니다.

이 구현에서 `IDebugParsedExpression::EvaluateSync`식이 구문 분석 되 고 동시에 평가 됩니다. 이 구현은 다음 작업을 수행합니다.

1. 식을 구문 분석 하 고 값 및 해당 형식을 보유 하는 제네릭 개체를 생성 하도록 평가 합니다. C #에서 이 것은 `object` C++에서 while으로 표시되며, `VARIANT`이 것은 로 표시됩니다.

2. 인터페이스를 구현 하 고 `CValueProperty` 반환할 값을 클래스에 저장 하는 클래스 (이 예제에서 호출)를 인스턴스화 합니다. `IDebugProperty2`

3. 개체에서 `IDebugProperty2` 인터페이스를 `CValueProperty` 반환합니다.

## <a name="managed-code"></a>관리 코드
이는 관리 되는 `IDebugParsedExpression::EvaluateSync` 코드의 구현입니다. 도우미 메서드는 `Tokenize` 구문 분석 트리로 식을 구문 분석합니다. 도우미 함수는 `EvalToken` 토큰을 값으로 변환합니다. 도우미 함수는 `FindTerm` 값을 나타내는 각 노드를 호출하고 `EvalToken` 식에 모든 작업(추가 또는 빼기)을 적용하여 구문 분석 트리를 재귀적으로 통과합니다.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>관리되지 않는 코드
이는 관리되지 않는 `IDebugParsedExpression::EvaluateSync` 코드의 구현입니다. 도우미 함수는 `Evaluate` 표현식을 구문 분석 및 `VARIANT` 평가하여 결과 값을 보유하는 값을 반환합니다. 도우미 함수는 `VariantValueToProperty` 개체에 `VARIANT` 번들로 묶습니다. `CValueProperty`

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>참조
- [시계 창 표현식 평가](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [식 평가의 샘플 구현](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
