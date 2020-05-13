---
title: 이넘데버그스레드2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbe047c08f8e91264163d028c1b40d94cde97fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715095"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
이 인터페이스는 현재 디버그 세션에서 실행 중인 스레드를 탐색합니다.

## <a name="syntax"></a>구문

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 이 인터페이스를 구현하여 프로그램의 스레드 목록을 나타냅니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [EnumThreads를](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) 호출하여 프로세스에서 실행 중인 모든 프로그램의 모든 스레드 목록을 나타내는 이 인터페이스를 가져옵니다. [EnumThreads를](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 호출하여 프로그램에서 실행 중인 스레드 목록을 나타내는 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugThreads2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|열거 시퀀스에서 지정된 수의 스레드를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|열거 순서에서 지정된 수의 스레드를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|현재 열거 상태와 동일한 열거 상태를 포함하는 열거형 거점을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|열거형의 스레드 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 일반적으로 **스레드** 창을 업데이트하고 목록의 첫 번째 스레드를 가져오도록 이 인터페이스를 가져와 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)및 [Step을](../../../extensibility/debugger/reference/idebugprocess3-step.md)호출합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [단계](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [계속](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [실행](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
