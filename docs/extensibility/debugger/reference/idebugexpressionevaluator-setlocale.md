---
title: IDebug표현평가자::세트로컬 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57ddee6e1796159c505b67982f25d1ba09684561
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729464"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
이 메서드는 인쇄 가능한 결과를 만드는 데 사용할 언어를 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>매개 변수
`wLangID`\
【인】 언어 식별자입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 식 평가기(EE)가 로드되는 동안 이 메서드를 여러 번 호출할 수 있으므로 EE는 즉시 언어를 전환할 수 있어야 합니다. EE는 이 로캘을 사용하여 오류 메시지와 문자열을 적절한 언어로 반환합니다.

## <a name="see-also"></a>참조
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
