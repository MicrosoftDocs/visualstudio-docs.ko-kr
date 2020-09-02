---
title: IDebugProcessCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessCreateEvent2
helpviewer_keywords:
- IDebugProcessCreateEvent2
ms.assetid: c660439d-8b23-4dbb-923e-ebb5e1d7edf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfc9b0bbdebde01af48ab1436dbfd17ac0c3241b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723532"
---
# <a name="idebugprocesscreateevent2"></a>IDebugProcessCreateEvent2
이 인터페이스는 프로세스가 시작 될 때 전송 됩니다.

## <a name="syntax"></a>Syntax

```
IDebugProcessCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 또는 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 프로세스가 생성 되었음을 보고 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE 또는 사용자 지정 포트 공급자는이 이벤트 개체를 만들어 전송 하 여 프로세스 만들기를 보고 합니다. DE는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여이 이벤트를 보냅니다. 사용자 지정 포트 공급자는 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 인터페이스를 사용 하 여이 이벤트를 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
