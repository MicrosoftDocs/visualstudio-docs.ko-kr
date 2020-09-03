---
title: IDebugStopCompleteEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719449"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

디버그 엔진 (DE)은 프로그램이 중지 될 때이 선택적 이벤트를 세션 디버그 관리자 (SDM)로 보낼 수 있습니다.

## <a name="syntax"></a>Syntax

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항

이 인터페이스는 Visual Studio 2005에서 도입 되었습니다. 이전 릴리스에서는 비동기 중지를 지원 하지 않았습니다.

- [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 은 다중 프로세스 또는 다중 프로그램 시나리오에서 SDM에 의해 호출 됩니다. 한 프로그램에서 SDM로 중지 이벤트를 보내면 SDM은 다른 프로그램을 중지 하도록 요청 합니다.

Stop은 프로그램이 중지 되었음을 SDM에 게 비동기적으로 알리는 데 사용 됩니다. 코드를 디버그 된 프로그램 내에서 실행 하지 않는 경우에는 인터프리터 디버그 엔진에 SDM이 유용 하다는 것을 확인할 수 있으므로, [중지](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 를 동기적으로 완료할 수 없습니다. 디버그 엔진이이 비동기 알림을 사용 하려는 경우 `S_ASYNC_STOP` [중지](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)에서 반환 해야 합니다.

## <a name="requirements"></a>요구 사항

헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
