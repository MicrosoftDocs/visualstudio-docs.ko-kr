---
title: IDebug표현평가자2::GetService | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5428606ad54c7938037c3ffecf04f1cfe41787c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729354"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
고유 식별자가 지정된 서비스 개체를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>매개 변수
`uid`\
【인】 검색할 서비스의 고유 식별자입니다.

`ppService`\
【아웃】 서비스를 나타내는 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 타사 식 평가기에서 다른 식 계산기에서 서비스를 가져오는 데 사용할 수 있습니다. 예를 들어 이 메서드는 기본 식 계산기에서 시각화 도우미 서비스에 대 한 인터페이스를 가져오는 데 사용할 수 있습니다. 타사 식 평가자는 이 인터페이스를 구현할 필요가 없습니다.

## <a name="see-also"></a>참조
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
