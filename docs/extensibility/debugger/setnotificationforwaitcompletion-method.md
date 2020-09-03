---
title: SetNotificationForWaitCompletion 메서드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712869"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion 메서드
TASK_STATE_WAIT_COMPLETION_NOTIFICATION 상태 비트를 설정 하거나 해제 합니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib ( *mscorlib.dll*)

## <a name="syntax"></a>구문

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>매개 변수
 `enabled`

 `true` 비트를 설정 하려면 `false` 비트를 설정 하지 않습니다.

## <a name="exceptions"></a>예외

## <a name="remarks"></a>설명
 디버거는 비동기 메서드 본문에서 프로시저를 실행 하는 데 도움이 되도록이 비트를 설정 합니다. `enabled`가 이면 `true` 이 메서드는 아직 완료 되지 않은 작업에 대해서만 호출 해야 합니다. `enabled`가 이면 `false` 완료 된 작업에 대해이 메서드를 호출할 수 있습니다. 어느 경우 든 약속 스타일 작업에만 사용 해야 합니다.

## <a name="requirements"></a>요구 사항

## <a name="see-also"></a>참고 항목
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
