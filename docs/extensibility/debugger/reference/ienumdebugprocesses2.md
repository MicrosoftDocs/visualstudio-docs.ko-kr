---
title: 이넘디버그프로세스2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b9fe0e96ade081e8da11b5e1c06c5b45279b10b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715754"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
이 인터페이스는 디버그 포트에서 실행되는 프로세스를 개명합니다.

## <a name="syntax"></a>구문

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 사용자 지정 포트 공급자는 이 인터페이스를 구현하여 포트에서 실행되는 프로세스 목록을 제공합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 비주얼 스튜디오는 이 인터페이스를 얻기 위해 [EnumProcesses를](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugProcesses2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|열거 순서에서 지정된 수의 프로세스를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|열거 순서에서 지정된 수의 프로세스를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|열거형의 프로세스 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 이 인터페이스를 사용하여 **프로세스** 창을 채웁니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
