---
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5789681b0da70f46dadac1e29d0d6bb9dc905d1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724992"
---
# <a name="idebugportex2"></a>IDebugPortEx2
이 인터페이스를 통해 세션 디버그 관리자 (SDM)는 포트에서 실행 되는 프로그램 및 프로세스를 제어할 수 있습니다.

## <a name="syntax"></a>Syntax

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자는 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 SDM에서 인터페이스에 대 한 [QueryInterface](/cpp/atl/queryinterface) `IDebugPort2` 를 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugPortEx2` .

|메서드|설명|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|실행 파일을 시작 합니다.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|프로세스의 실행을 다시 시작 합니다.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|프로세스를 종료할 수 있는지 여부를 확인 합니다.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|프로세스를 종료 합니다.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|포트 자체의 프로세스 ID를 가져옵니다.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|프로그램 노드와 연결 된 프로그램을 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 일반적으로 SDM과 사용자 지정 포트 공급자 사이에서 전용입니다.

 원할 경우 디버그 엔진 (DE)은 [launchsuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 로 전달 된 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스에서이 인터페이스를 찾고, [launchsuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) 를 사용 하 여 프로그램을 시작할 수 있습니다. 그러나이는 요구 사항이 아니며, DE는 요청 프로그램을 시작 하는 데 필요한 모든 작업을 수행할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: portpriv. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
