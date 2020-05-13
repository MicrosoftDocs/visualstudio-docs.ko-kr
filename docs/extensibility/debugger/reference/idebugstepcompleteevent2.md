---
title: 이데버그스텝완료이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 289609c93cf0e58eb44500bff135282d01212bbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719454"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
이 인터페이스는 디버깅 중인 프로그램이 소스 코드 또는 명령문 또는 명령줄에서 단계, 단계 또는 단계를 완료할 때 세션 디버그 관리자(SDM)로 디버그 엔진(DE)에 의해 전송됩니다.

## <a name="syntax"></a>구문

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 단계 작업의 완료를 보고하기 위해 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 `IDebugEvent2` 인터페이스에 액세스합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 이 이벤트 개체를 만들고 보내 단계 작업의 완료를 보고합니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="remarks"></a>설명
 단계가 완료되면 디버깅중인 프로그램이 한 번 더 일시 중지되고 IDE는 모든 창을 업데이트합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
