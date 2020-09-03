---
title: IDebugProgramDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2
helpviewer_keywords:
- IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc83e15372a15cefccc47ea60db5ba451546ecba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722596"
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
이 인터페이스는 프로그램 실행이 완료 될 때 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 보냅니다.

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 또는 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 프로그램이 종료 되었으며 더 이상 디버깅에 사용할 수 없음을 보고 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE 또는 사용자 지정 포트 공급자는 프로그램 종료를 보고 하기 위해이 이벤트 개체를 만들어 보냅니다. DE는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여이 이벤트를 보냅니다. 사용자 지정 포트 공급자는 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 인터페이스를 사용 하 여이 이벤트를 보냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProgramDestroyEvent2` .

|메서드|설명|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|프로그램의 종료 코드를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
