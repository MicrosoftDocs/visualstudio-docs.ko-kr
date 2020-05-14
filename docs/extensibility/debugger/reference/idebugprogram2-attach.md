---
title: IDebugProgram2::연결 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d0b182ba7a873816e3a7aa32d39beb2c63cc5ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723143"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
프로그램에 연결합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>매개 변수
`pCallback`\
【인】 디버그 이벤트 알림에 사용할 [IDebugEventCallback2 개체입니다.](../../../extensibility/debugger/reference/idebugeventcallback2.md)

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 다음 표에는 몇 가지 가능한 오류 코드가 표시됩니다.

|값|Description|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|지정된 프로그램이 디버거에 이미 연결되어 있습니다.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|연결 절차 중에 보안 위반이 발생했습니다.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|데스크톱 프로그램을 디버거에 연결할 수 없습니다.|

## <a name="remarks"></a>설명
 디버그 엔진(DE)은 이 메서드를 호출하여 프로그램에 연결하지 않습니다. DE가 프로그램의 주소 공간에서 실행되는 경우 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드가 호출됩니다. 세션 디버그 관리자(SDM) 주소 공간에서 DE가 실행되는 경우 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드가 호출됩니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
