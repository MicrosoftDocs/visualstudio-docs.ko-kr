---
title: IDebug표현문맥상2::ParseText | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8494c9c90c4cb6e94115c542a25e12e948f7064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729655"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
나중에 평가를 위해 식을 텍스트 형식으로 구문 분석합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>매개 변수
`pszCode`\
【인】 구문 분석할 식입니다.

`dwFlags`\
【인】 구문 분석기능을 제어하는 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) 열거형의 플래그 조합입니다.

`nRadix`\
【인】 의 모든 숫자 정보를 구문 분석하는 데 `pszCode`사용할 radix입니다.

`ppExpr`\
【아웃】 바인딩 및 평가할 준비가 된 구문 분석식을 나타내는 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 개체를 반환합니다.

`pbstrError`\
【아웃】 식에 오류가 포함된 경우 오류 메시지를 반환합니다.

`pichError`\
【아웃】 식에 오류가 포함된 경우 `pszCode` 오류의 문자 인덱스를 반환합니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
이 메서드를 호출 하는 경우 debug 엔진 (DE) 식을 구문 분석 하 고 정확성에 대 한 유효성을 검사 해야 합니다. `pbstrError` 및 `pichError` 매개 변수는 식이 잘못되면 채워질 수 있습니다.

표현식은 평가되지 않고 구문 분석만 됩니다. [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 메서드에 대한 이후 호출은 구문 분석된 식을 평가합니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) `CEnvBlock` 인터페이스를 노출 하는 간단한 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다. 이 예제는 식을 환경 변수의 이름으로 구문 분석하고 해당 변수에서 값을 검색합니다.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>참조
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
