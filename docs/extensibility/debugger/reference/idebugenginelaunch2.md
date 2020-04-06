---
title: 아이데버그엔진런칭2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730499"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
디버그 엔진(DE)이 프로그램을 시작하고 종료하는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 사용자 지정 포트에서 완전히 처리할 수 없는 프로세스를 실행하기 위한 특별한 요구 사항이 있는 경우 사용자 지정 DE에 의해 구현됩니다. 일반적으로 DE가 인터프리터의 일부이고 디버깅되는 프로세스가 스크립트인 경우인터프리터를 먼저 시작한 다음 스크립트를 로드하고 시작해야 합니다. 포트는 인터프리터를 시작할 수 있지만 스크립트에는 특별한 처리가 필요할 수 있습니다(DE에 역할이 있는 경우). 이 인터페이스는 사용자 지정 포트가 처리할 수 없는 프로그램을 실행하기 위한 고유한 요구 사항이 있는 경우에만 구현됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 SDM이 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 인터페이스(QueryInterface 사용)에서 이 인터페이스를 얻을 수 있는 경우 이 인터페이스는 세션 디버그 관리자(SDM)에서 호출됩니다. 이 인터페이스를 가져올 수 있는 경우 SDM은 DE에 특별한 요구 사항이 있음을 알고 있으며 포트가 프로그램을 시작하지 않고 프로그램을 실행하기 위해 이 인터페이스를 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugEngineLaunch2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|DE를 통해 프로세스를 시작합니다.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|프로세스 실행을 다시 시작합니다.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|프로세스를 종료할 수 있는지 여부를 결정합니다.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|프로세스를 종료합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
