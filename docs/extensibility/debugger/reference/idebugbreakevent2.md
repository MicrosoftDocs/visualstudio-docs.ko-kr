---
title: 아이디버그브레이크이벤트2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735398"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
이 인터페이스는 세션 디버그 관리자(SDM)에게 비동기 중단이 성공적으로 완료되었음을 알려줍니다.

## <a name="syntax"></a>구문

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 프로그램의 사용자 중단을 지원하기 위해 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다(SDM은 `IDebugEvent2` [QueryInterface를](/cpp/atl/queryinterface) 사용하여 인터페이스에 액세스합니다).

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 SDM은 사용자가 디버깅 중인 프로그램을 일시 중지하도록 요청했을 때 [CauseBreak를](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) 호출합니다. 프로그램이 성공적으로 일시 중지되면 DE는 `IDebugBreakEvent2` 이벤트를 보냅니다. 이 이벤트는 디버깅 중인 프로그램에 연결할 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="remarks"></a>설명
 예를 들어 사용자는 **디버그** 메뉴에서 **모두 중단** 명령을 선택하여 무한 루프를 실행하는 프로그램에서 벗어날 수 있습니다. SDM은 [프로그램에 CauseBreak를](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)호출하여 중지하도록 지시합니다. DE는 `IDebugBreakEvent2` 프로그램이 마침내 중지될 때 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
