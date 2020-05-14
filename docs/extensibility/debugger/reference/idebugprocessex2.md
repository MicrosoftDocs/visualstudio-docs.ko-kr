---
title: 아이디버그프로세스2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723333"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
이 인터페이스를 사용하면 세션 디버그 관리자(SDM)가 프로세스에 연결하거나 프로세스에서 분리하는 프로세스에 알릴 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 사용자 지정 포트 공급자는 다음을 수행하기 위해 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스와 동일한 개체에서 이 인터페이스를 구현합니다.

- 프로세스에 연결된 세션 추적 지원

- 여러 디버그 엔진에서 자동 연결 지원

  사용자 지정 포트 공급자가 선택한 경우 이 인터페이스를 구현할 수 있습니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항

- SDM은 이 인터페이스를 `IDebugProcess2` 얻기 위해 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProcessEx2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[연결](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|이제 세션이 프로세스를 디버깅하고 있음을 프로세스에 알립니다.|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|세션이 더 이상 프로세스를 디버깅하지 않는다는 것을 프로세스에 알립니다.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|디버그 엔진 목록에 대한 프로그램 노드를 추가합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 SDM과 프로세스 간에 비공개입니다.

## <a name="requirements"></a>요구 사항
 헤더: 포트프리브.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
