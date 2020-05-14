---
title: 아이데버그엔진프로그램2::워치포스레드스텝 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730347"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
지정된 스레드에서 실행(또는 실행 감시 중지)을 감시합니다.

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
【인】 단계별 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

`dwTid`\
【인】 시청할 스레드의 식별자를 지정합니다.

`fWatch`\
【인】 0이 아닌`TRUE`() 은 로 식별된 `dwTid`스레드에서 실행을 감시하기 시작합니다. 그렇지 않으면`FALSE`0 () 에서 `dwTid`실행을 감시중지하는 것을 의미합니다.

`dwFrame`\
【인】 단계 유형을 제어하는 프레임 인덱스를 지정합니다. 값이 0(0)이면 단계 형식은 "단계 입력"이며 스레드가 `dwTid` 실행될 때마다 프로그램이 중지되어야 합니다. 0이 아닌 경우 `dwFrame` 단계 유형은 "단계 별"이며 인덱스가 스택에서 `dwTid` 보다 `dwFrame`높거나 높은 프레임에서 식별된 스레드가 실행되는 경우에만 프로그램이 중지되어야 합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 세션 디버그 관리자(SDM)가 `pOriginatingProgram` 매개 변수로 식별된 프로그램을 단계별로 수행하면 이 메서드를 호출하여 연결된 다른 모든 프로그램에 알게 됩니다.

 이 메서드는 동일한 스레드 스테핑에만 적용할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
