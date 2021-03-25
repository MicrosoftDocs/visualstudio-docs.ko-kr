---
description: 프로그램에 세션을 연결 합니다.
title: 'IDebugProgramEx2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4f7f6a083c37ece73be488ab0c4f6d4c25ce24c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084157"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
프로그램에 세션을 연결 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>매개 변수
`pCallback`\
진행 연결 된 디버그 엔진이 이벤트를 보내는 콜백 함수를 나타내는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.

`dwReason`\
진행 연결 작업의 원인을 설명 하는 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 열거형의 값입니다.

`pSession`\
진행 프로그램에 연결 되는 세션을 고유 하 게 식별 하는 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 프로그램이 이미 연결 되어 있으면이 메서드는를 반환 해야 합니다 `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` .

## <a name="remarks"></a>설명
 프로그램을 포함 하는 포트는의 값을 사용 `pSession` 하 여 프로그램에 연결 하려고 하는 세션을 확인할 수 있습니다. 예를 들어 포트에서 한 번에 하나의 디버그 세션만 프로세스에 연결할 수 있는 경우 포트는 동일한 세션이 프로세스의 다른 프로그램에 이미 연결 되어 있는지 확인할 수 있습니다.

> [!NOTE]
> 전달 된 인터페이스는 `pSession` 이 프로그램에 연결 하는 세션 디버그 관리자를 고유 하 게 식별 하는 값인 쿠키로만 처리 됩니다. 제공 된 인터페이스의 메서드는 모두 작동 하지 않습니다.

## <a name="see-also"></a>참조
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
