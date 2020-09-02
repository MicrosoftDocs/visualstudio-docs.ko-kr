---
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729354"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
고유 식별자가 지정 된 서비스 개체를 검색 합니다.

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
진행 검색할 서비스의 고유 식별자입니다.

`ppService`\
제한이 서비스를 나타내는 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 타사 식 계산기에서이를 사용 하 여 다른 식 계산기에서 서비스를 가져올 수 있습니다. 예를 들어이 메서드를 사용 하 여 기본 식 계산기에서 시각화 도우미 서비스의 인터페이스를 가져올 수 있습니다. 타사 식 계산기는이 인터페이스를 구현 해야 할 가능성이 거의 없습니다.

## <a name="see-also"></a>추가 정보
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
