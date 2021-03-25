---
description: De (디버그 엔진)는 DE-DE 인스턴스가 만들어질 때이 인터페이스를 세션 디버그 관리자 (SDM)로 보냅니다.
title: IDebugEngineCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da6b249581f4cf51d22ceb86eb0fd5837a42e8ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054363"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
De (디버그 엔진)는 DE-DE 인스턴스가 만들어질 때이 인터페이스를 세션 디버그 관리자 (SDM)로 보냅니다.

## <a name="syntax"></a>구문

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는 정상적인 작업의 일부로이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. 즉, SDM은 메서드를 사용 하 여 `QueryInterface` 인터페이스에 액세스 합니다 `IDebugEvent2` .

## <a name="notes-for-callers"></a>호출자 참고 사항
 De가 인스턴스화되면이 이벤트 개체를 만들어 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugEngineCreateEvent2` .

|메서드|Description|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|새로 만든 디버그 엔진 (DE)을 나타내는 개체를 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
