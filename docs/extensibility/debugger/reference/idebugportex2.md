---
title: 아이디버그포트엑스2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724992"
---
# <a name="idebugportex2"></a>IDebugPortEx2
이 인터페이스를 사용하면 세션 디버그 관리자(SDM)가 포트에서 실행되는 프로그램 및 프로세스를 제어할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 사용자 지정 포트 공급자는 [IDebugPort2를](../../../extensibility/debugger/reference/idebugport2.md)구현하는 동일한 개체에 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 SDM은 이 인터페이스를 `IDebugPort2` 얻기 위해 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugPortEx2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|실행 파일 파일을 시작합니다.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|프로세스 실행을 다시 시작합니다.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|프로세스를 종료할 수 있는지 여부를 결정합니다.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|프로세스를 종료합니다.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|포트 자체의 프로세스 ID를 가져옵니다.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|프로그램 노드와 연결된 프로그램을 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 일반적으로 SDM과 사용자 지정 포트 공급자 간에 비공개입니다.

 원하는 경우 DE(디버그 엔진)는 [LaunchSuspended에](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 전달된 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스에서 이 인터페이스를 찾고 [LaunchSuspended를](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) 사용하여 프로그램을 시작할 수 있습니다. 그러나 이것은 요구 사항이 아니며 DE는 요청 프로그램을 시작하기 위해 수행해야 할 모든 작업을 수행할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: 포트프리브.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
