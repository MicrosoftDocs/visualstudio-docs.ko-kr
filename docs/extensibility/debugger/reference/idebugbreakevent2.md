---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735398"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
이 인터페이스는 세션 디버그 관리자 (SDM)에 비동기 중단이 성공적으로 완료 되었음을 알려 줍니다.

## <a name="syntax"></a>Syntax

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는 프로그램의 사용자 중단을 지원 하기 위해이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. 즉, SDM에서 인터페이스에 액세스 하는 데 [QueryInterface](/cpp/atl/queryinterface) 를 사용 합니다 `IDebugEvent2` .

## <a name="notes-for-callers"></a>호출자 참고 사항
 사용자가 디버그 중인 프로그램을 일시 중지 하도록 요청 하면 SDM이 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) 를 호출 합니다. 프로그램이 성공적으로 일시 중지 되 면 DE는 이벤트를 보냅니다 `IDebugBreakEvent2` . 이 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback 함수를 사용 하 여 보냅니다.

## <a name="remarks"></a>설명
 예를 들어 사용자는 **디버그** 메뉴에서 **모두 중단** 명령을 선택 하 여 무한 루프를 실행 하는 프로그램을 중단할 수 있습니다. SDM은 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)를 호출 하 여 프로그램을 중지 하도록 지시 합니다. `IDebugBreakEvent2`프로그램을 마지막으로 중지할 때 DE가 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
