---
description: 이 메서드는 세션이 더 이상 프로세스를 디버깅 하 고 있지 않음을 프로세스에 알립니다.
title: IDebugProcessEx2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5ad25fe6461f1df89ada83623ab4e28194ca207
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076331"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
이 메서드는 세션이 더 이상 프로세스를 디버깅 하 고 있지 않음을 프로세스에 알립니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>매개 변수
`pSession`\
진행 이 프로세스를 분리할 세션을 고유 하 게 식별 하는 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 전달 된 인터페이스는 `pSession` 원래이 프로세스에 연결 된 세션 디버그 관리자를 고유 하 게 식별 하는 값인 쿠키로만 처리 됩니다. 제공 된 인터페이스의 메서드는 모두 작동 하지 않습니다.

## <a name="see-also"></a>참조
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
