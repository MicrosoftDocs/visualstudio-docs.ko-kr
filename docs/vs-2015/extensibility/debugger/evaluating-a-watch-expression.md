---
title: 조사식 식 계산 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd33a7c225e0cdc14ac3f1af9f4c78a7c1459615
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841427"
---
# <a name="evaluating-a-watch-expression"></a>조사식 창 계산
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 Visual Studio가 조사식 식의 값을 표시할 준비가 되 면 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 를 호출 하 여 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)를 호출 합니다. 그러면 식의 값과 형식이 포함 된 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체가 생성 됩니다.  
  
 이 구현에서는 `IDebugParsedExpression::EvaluateSync` 식이 동시에 구문 분석 되 고 계산 됩니다. 이 구현에서는 다음 작업을 수행 합니다.  
  
1. 식의 구문을 분석 하 고 평가 하 여 값과 해당 형식을 포함 하는 제네릭 개체를 생성 합니다. C #에서이는 `object` c + +에서로 표현 됩니다 .이는로 표시 됩니다 `VARIANT` .  
  
2. `CValueProperty`인터페이스를 구현 하 `IDebugProperty2` 고 반환 될 값을 클래스에 저장 하는 클래스 (이 예제에서는 호출 됨)를 인스턴스화합니다.  
  
3. `IDebugProperty2`개체에서 인터페이스를 반환 합니다 `CValueProperty` .  
  
## <a name="managed-code"></a>관리 코드  
 이는 `IDebugParsedExpression::EvaluateSync` 관리 코드에서의 구현입니다. 도우미 메서드는 `Tokenize` 식을 구문 분석 트리로 구문 분석 합니다. 도우미 함수는 `EvalToken` 토큰을 값으로 변환 합니다. 도우미 함수는 `FindTerm` `EvalToken` 값을 나타내는 각 노드에 대해를 호출 하 고 식에 연산 (더하기 또는 빼기)을 적용 하 여 구문 분석 트리를 재귀적으로 트래버스 합니다.  
  
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
  
## <a name="unmanaged-code"></a>비관리 코드  
 비관리 코드에서의 구현입니다 `IDebugParsedExpression::EvaluateSync` . 도우미 함수는 `Evaluate` 결과 값을 포함 하는을 반환 하 여 식을 구문 분석 하 고 계산 합니다 `VARIANT` . 도우미 함수는 `VariantValueToProperty` 를 `VARIANT` `CValueProperty` 개체로 묶습니다.  
  
```  
[C++]  
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
  
## <a name="see-also"></a>참고 항목  
 [조사식 창 식 계산](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [식 계산의 샘플 구현](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
