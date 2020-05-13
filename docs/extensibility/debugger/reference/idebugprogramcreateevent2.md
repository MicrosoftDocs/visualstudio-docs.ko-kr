---
title: 아이디버그프로그램만들기2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78088d6e5da61c32302c13b08143c9ed902452e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722634"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
이 인터페이스는 프로그램이 연결될 때 DE(디버그 엔진)를 세션 디버그 관리자(SDM)로 보냄.

## <a name="syntax"></a>구문

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE 또는 사용자 지정 포트 공급자는 이 인터페이스를 구현하여 프로그램이 생성된 지 보고합니다( 일반적으로 프로그램이 연결될 때). [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 이 `QueryInterface` 메서드를 `IDebugEvent2` 사용하여 인터페이스에 액세스합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE 또는 사용자 지정 포트 공급자는 이 이벤트 개체를 만들고 보내 프로그램 만들기를 보고합니다. DE는 디버깅 중인 프로그램에 연결할 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 이 이벤트를 보냅니다. 사용자 지정 포트 공급자는 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 인터페이스를 사용하여 이 이벤트를 보냅니다.

## <a name="remarks"></a>설명
 DE 또는 사용자 지정 포트 공급자는 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)를 호출하여 새 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스를 게시합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
