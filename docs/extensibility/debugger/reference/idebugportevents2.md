---
title: IDebugPortEvents2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725179"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
이 인터페이스는 특정 포트에서 프로세스 및 프로그램 생성 및 소멸에 대 한 수신기 (일반적으로 세션 디버그 관리자 [SDM] 또는 디버그 엔진)에 게 알립니다. 이 정보를 사용 하 여 포트에서 실행 중인 프로세스 및 프로그램의 실시간 보기를 표시할 수 있습니다.

## <a name="syntax"></a>Syntax

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio는 일반적으로 프로그램 만들기 및 소멸에 대 한 알림을 수신 하기 위해이 인터페이스를 구현 합니다. 디버그 엔진은 이러한 포트 이벤트를 수신 하기 위해이 인터페이스를 구현할 수도 있습니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 인터페이스에 대해 모든 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스를 쿼리할 수 있습니다 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> . 그런 다음 인터페이스를 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> 가져오기 위해에 대 한 메서드가 `IDebugPortEvents2` 호출 됩니다 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> . 마지막으로 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> 인터페이스의 메서드를 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 호출 하 여 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md) 메서드를 통해 이벤트를 보냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugPortEvents2` .

|메서드|설명|
|------------|-----------------|
|[이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)|포트에서 프로세스 및 프로그램의 생성 및 소멸을 설명 하는 이벤트를 보냅니다.|

## <a name="remarks"></a>설명
 `IDebugPortEvents2` 는 이미 디버깅 중인 프로세스에서 실행 되는 프로그램을 디버그 하는 데에도 사용 됩니다.

 포트 이벤트는이 인터페이스에 의해 SDM에 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
