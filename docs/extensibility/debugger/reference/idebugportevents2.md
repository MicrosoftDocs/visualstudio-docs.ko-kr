---
title: 아이데버그포트이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725179"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
이 인터페이스는 특정 포트에서 프로세스 및 프로그램 생성 및 소멸에 대한 리스너(일반적으로 세션 디버그 관리자 [SDM] 또는 디버그 엔진)에게 이를 통보합니다. 이 정보를 사용하여 포트에서 실행되는 프로세스 및 프로그램의 실시간 보기를 표시할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 Visual Studio는 일반적으로 이 인터페이스를 구현하여 프로그램 생성 및 소멸에 대한 알림을 수신합니다. 디버그 엔진은 이러한 포트 이벤트를 수신하기 위해 이 인터페이스를 구현할 수도 있습니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 모든 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스에 대 한 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 쿼리할 수 있습니다. 그런 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> 다음 `IDebugPortEvents2` 메서드는 인터페이스를 얻기 위해 인터페이스에서 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 호출됩니다. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 마지막으로 인터페이스의 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 메서드는 [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md) 메서드를 통해 이벤트를 보내기 위해 호출됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugPortEvents2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)|포트에서 프로세스 및 프로그램의 생성 및 소멸을 설명하는 이벤트를 보냅니다.|

## <a name="remarks"></a>설명
 `IDebugPortEvents2`또한 SDM에서 이미 디버깅 중인 프로세스에서 실행되는 프로그램을 디버깅하는 데 사용됩니다.

 포트 이벤트는 이 인터페이스를 통해 SDM에 전달됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
