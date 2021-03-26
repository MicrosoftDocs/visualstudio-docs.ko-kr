---
description: 이 인터페이스는 프로그램을에 연결할 때 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 보냅니다.
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1fb183bfc11cb3e2711d83c7cb5f18cbe908d8e5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084352"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
이 인터페이스는 프로그램을에 연결할 때 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 보냅니다.

## <a name="syntax"></a>구문

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 또는 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 프로그램이 생성 된 시간에 일반적으로 프로그램이 연결 된 것을 보고 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 메서드를 사용 하 여 `QueryInterface` 인터페이스에 액세스 `IDebugEvent2` 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE 또는 사용자 지정 포트 공급자는 프로그램 만들기를 보고 하기 위해이 이벤트 개체를 만들어 보냅니다. DE는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여이 이벤트를 보냅니다. 사용자 지정 포트 공급자는 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 인터페이스를 사용 하 여이 이벤트를 보냅니다.

## <a name="remarks"></a>설명
 DE 또는 사용자 지정 포트 공급자는 새 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스를 호출 하 여 새 인터페이스를 [게시 합니다.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
