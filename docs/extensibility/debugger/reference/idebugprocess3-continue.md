---
title: 'IDebugProcess3:: Continue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aba0863ad7c50bf5c14e7a30c06097825b8cf5ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386799"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
중지 된 상태에서이 프로세스를 계속 실행 합니다. 모든 이전 실행 상태 (예: 단계)는 유지 되며 프로세스가 다시 실행 되기 시작 합니다.

> [!NOTE]
> 이 메서드는 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)대신 사용 해야 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Continue(
   IDebugThread2* pThread
);
```

```csharp
int Continue(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>매개 변수
`pThread`\
진행 계속할 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 디버깅 중인 프로세스의 수 또는 중지 이벤트를 생성 한 프로세스에 관계 없이이 프로세스에서 호출 됩니다. 구현은 이전 실행 상태 (예: 단계)를 유지 하 고 이전 실행을 완료 하기 전에 중지 된 적이 없는 경우에도 계속 실행 해야 합니다. 즉,이 프로세스의 스레드가 단계별 작업을 수행 하 고 다른 일부 프로세스가 중지 되어 중지 된 후에 호출 되 면 `Continue` 지정 된 스레드가 원래 단계별 작업을 완료 해야 합니다.

 **경고** 이 호출을 처리 하는 동안 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 에 중지 이벤트 또는 즉각적인 (동기) 이벤트를 보내지 않습니다. 그렇지 않으면 디버거가 응답 하지 않을 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
