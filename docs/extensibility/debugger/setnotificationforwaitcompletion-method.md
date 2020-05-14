---
title: 설정 알림대기 완료 방법 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712869"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion 메서드
TASK_STATE_WAIT_COMPLETION_NOTIFICATION 상태 비트를 설정하거나 지웁습니다.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **조립:** mscorlib *(mscorlib.dll)*

## <a name="syntax"></a>구문

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>매개 변수
 `enabled`

 `true`비트를 설정합니다. `false` 을 사용하여 비트를 설정 해제합니다.

## <a name="exceptions"></a>예외

## <a name="remarks"></a>설명
 디버거는 비동기 메서드 본문에서 벗어나는 데 도움이 되는 이 비트를 설정합니다. 이 `enabled` `true`경우 이 메서드는 아직 완료되지 않은 작업에서만 호출해야 합니다. 때 `enabled` `false`, 이 메서드는 완료 된 작업에 호출할 수 있습니다. 두 경우 모두 약속 스타일 작업에만 사용해야 합니다.

## <a name="requirements"></a>요구 사항

## <a name="see-also"></a>참조
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
