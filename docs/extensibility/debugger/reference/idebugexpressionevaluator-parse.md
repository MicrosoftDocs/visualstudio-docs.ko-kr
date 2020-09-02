---
title: IDebugExpressionEvaluator::P arse | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729498"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
이 메서드는 식 문자열을 구문 분석 된 식으로 변환 합니다.

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
진행 구문 분석할 식 문자열입니다.

`dwFlags`\
진행 식을 구문 분석 하는 방법을 결정 하는 [Parseflags](../../../extensibility/debugger/reference/parseflags.md) 상수 컬렉션입니다.

`nRadix`\
진행 숫자 정보를 해석 하는 데 사용할 기 수입니다.

`pbstrError`\
제한이 오류를 사람이 읽을 수 있는 텍스트로 반환 합니다.

`pichError`\
제한이 식 문자열에서 오류 시작의 문자 위치를 반환 합니다.

`ppParsedExpression`\
제한이 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 개체의 구문 분석 된 식을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 실제 값이 아니라 구문 분석 된 식을 생성 합니다. 구문 분석 된 식이 계산 될 준비가 되었습니다. 즉, 값으로 변환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
