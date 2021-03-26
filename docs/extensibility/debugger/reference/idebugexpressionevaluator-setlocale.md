---
description: 이 메서드는 인쇄 가능한 결과를 만드는 데 사용할 언어를 설정 합니다.
title: 'IDebugExpressionEvaluator:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f833311fe9029931c0d56cbe828bd027c45c26a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092061"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
이 메서드는 인쇄 가능한 결과를 만드는 데 사용할 언어를 설정 합니다.

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
진행 언어 식별자입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 식 계산기 (EE)가 로드 되는 동안 여러 번 호출 될 수 있으므로 EE에서 언어를 즉시 전환할 수 있어야 합니다. EE는이 로캘을 사용 하 여 오류 메시지 및 문자열을 적절 한 언어로 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
