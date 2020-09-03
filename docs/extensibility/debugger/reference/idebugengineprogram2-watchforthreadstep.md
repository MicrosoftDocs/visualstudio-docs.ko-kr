---
title: 'IDebugEngineProgram2:: WatchForThreadStep | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730347"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
지정 된 스레드에서 실행을 감시 하거나 실행에 대 한 감시를 중지 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>매개 변수
`pOriginatingProgram`\
진행 단계별 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

`dwTid`\
진행 감시할 스레드의 식별자를 지정 합니다.

`fWatch`\
진행 0이 아닌 값 ( `TRUE` )은로 식별 된 스레드에서 실행을 감시 하기 시작 하는 것 `dwTid` 을 의미 합니다. 그렇지 않으면 0 ( `FALSE` )은에서 실행을 감시 하지 않음을 의미 `dwTid` 합니다.

`dwFrame`\
진행 단계 유형을 제어 하는 프레임 인덱스를 지정 합니다. 이 값이 0 이면 단계 형식이 "한 단계씩 코드 실행" 이며로 식별 되는 스레드가 실행 될 때마다 프로그램이 중지 됩니다 `dwTid` . `dwFrame`가 0이 아닌 경우 단계 유형은 "프로시저 단위 실행" 이며,로 식별 된 스레드가 `dwTid` 와 스택에서 같은 인덱스의 프레임에서 실행 중인 경우에만 프로그램을 중지 해야 합니다 `dwFrame` .

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 세션 디버그 관리자 (SDM)는 매개 변수로 식별 되는 프로그램의 단계를 수행 하는 경우 `pOriginatingProgram` 이 메서드를 호출 하 여 다른 모든 연결 된 프로그램에 알립니다.

 이 메서드는 동일한 스레드 단계별 실행에만 적용 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
