---
title: 아이디버그스탑컴플리트이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719449"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

디버그 엔진(DE)은 프로그램이 중지되면 이 선택적 이벤트를 세션 디버그 관리자(SDM)로 보낼 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항

이 인터페이스는 Visual Studio 2005와 함께 도입되었습니다. 이전 릴리스에서는 비동기 중지를 지원하지 않았습니다.

- [중지는](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 다중 프로세스 또는 다중 프로그램 시나리오에서 SDM에 의해 호출됩니다. 한 프로그램이 중지 이벤트를 SDM에 전송하면 SDM은 다른 프로그램도 중지하도록 요청합니다.

Stop은 프로그램이 중지되었음을 SDM에 비동기적으로 알리는 데 사용됩니다. SDM에 알리는 것은 디버깅된 프로그램 내에서 코드가 실행되지 않는 인터프리터 디버그 엔진에 유용하므로 [Stop을](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 동기적으로 완료할 수 없습니다. 디버그 엔진이 이 비동기 알림을 사용하려는 경우 `S_ASYNC_STOP` [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)에서 반환해야 합니다.

## <a name="requirements"></a>요구 사항

헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
