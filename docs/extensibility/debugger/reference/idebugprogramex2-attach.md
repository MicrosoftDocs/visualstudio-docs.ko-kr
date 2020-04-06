---
title: 아이디버그프로그램Ex2::첨부 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722383"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
프로그램에 세션을 연결합니다.

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
【인】 연결된 디버그 엔진이 이벤트를 보내는 콜백 함수를 나타내는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.

`dwReason`\
【인】 첨부 작업의 이유를 설명하는 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 열거형의 값입니다.

`pSession`\
【인】 프로그램에 첨부되는 세션을 고유하게 식별하는 값입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 프로그램이 이미 `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` 연결되어 있는 경우 이 메서드가 반환됩니다.

## <a name="remarks"></a>설명
 프로그램을 포함하는 포트는 에서 값을 `pSession` 사용하여 프로그램에 연결하려는 세션을 결정할 수 있습니다. 예를 들어 포트에서 한 번에 하나의 디버그 세션만 프로세스에 연결할 수 있도록 허용하는 경우 포트는 동일한 세션이 프로세스의 다른 프로그램에 이미 연결되어 있는지 확인할 수 있습니다.

> [!NOTE]
> 전달된 `pSession` 인터페이스는 이 프로그램에 연결하는 세션 디버그 관리자를 고유하게 식별하는 값인 쿠키로만 처리됩니다. 제공된 인터페이스의 메서드가 작동하지 않습니다.

## <a name="see-also"></a>참조
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
