---
description: 이 인터페이스는 디버그 포트에서 실행 되는 프로세스를 열거 합니다.
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 75778ea0f02c0e7dcca1f7d2eb0ea8ace82c9b9c
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224384"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
이 인터페이스는 디버그 포트에서 실행 되는 프로세스를 열거 합니다.

## <a name="syntax"></a>구문

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 포트에서 실행 중인 프로세스 목록을 제공 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 Visual Studio는이 인터페이스를 얻기 위해 [enumprocesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) 를 호출 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugProcesses2` .

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|열거형 시퀀스에서 지정 된 수의 프로세스를 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|열거형 시퀀스에서 지정 된 수의 프로세스를 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[원본과](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|열거자의 프로세스 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio에서는이 인터페이스를 사용 하 여 **프로세스** 창을 채웁니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
