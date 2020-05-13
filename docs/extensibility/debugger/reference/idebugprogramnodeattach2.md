---
title: 아이디버그프로그램노드첨부2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721825"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
프로그램 노드가 연결된 프로그램에 연결하려는 시도에 대한 알림을 받을 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 연결 작업에 대한 알림을 수신하고 연결 작업을 취소할 수 있는 기회를 제공하기 위해 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스를 구현하는 동일한 클래스에서 구현됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 `QueryInterface` [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체에서 메서드를 호출 하 여이 인터페이스를 가져옵니다. [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드는 프로그램 노드에 연결 프로세스를 중지할 수 있는 기회를 제공하기 위해 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드 앞에 호출되어야 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|연결된 프로그램에 연결하거나 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드에 대한 연결 프로세스를 연기합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 더 이상 사용되지 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) 메서드에 대한 기본 대안입니다. 모든 디버그 엔진은 항상 `CoCreateInstance` 디버깅중인 프로그램의 주소 공간 외부에서 인스턴스화되는 함수와 함께 로드됩니다.

 `IDebugProgramNode2::Attach_V7` 메서드의 이전 구현이 디버깅 `GUID` 중인 프로그램의 단순히 설정한 경우 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드만 구현해야 합니다.

 메서드의 이전 구현에서 제공된 콜백 인터페이스를 사용한 경우 해당 기능을 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드의 구현으로 `IDebugProgramNodeAttach2` 이동해야 하며 인터페이스를 구현할 필요가 없습니다. `IDebugProgramNode2::Attach_V7`

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
