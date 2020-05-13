---
title: IDebug표현평가자::Parse | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1af9d3f253a9849f54bb5a50d432b98eb4ad7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729498"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
이 메서드는 식 문자열을 구문 분석된 식으로 변환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>매개 변수
`upstrExpression`\
【인】 구문 분석할 식 문자열입니다.

`dwFlags`\
【인】 식을 구문 분석하는 방법을 결정하는 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) 상수의 컬렉션입니다.

`nRadix`\
【인】 모든 수치 정보를 해석하는 데 사용되는 Radix.

`pbstrError`\
【아웃】 오류를 사람이 읽을 수 있는 텍스트로 반환합니다.

`pichError`\
【아웃】 식 문자열에서 오류 시작의 문자 위치를 반환합니다.

`ppParsedExpression`\
【아웃】 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 개체에서 구문 분석된 식을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 실제 값이 아닌 구문 분석식을 생성합니다. 구문 분석식은 평가할 준비가 되었습니다.

## <a name="see-also"></a>참조
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
