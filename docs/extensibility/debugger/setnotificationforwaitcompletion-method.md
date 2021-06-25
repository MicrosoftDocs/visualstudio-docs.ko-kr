---
title: SetNotificationForWaitCompletion 메서드 | Microsoft Docs
description: 디버거가 상태 비트를 사용하여 약속 스타일 작업에 대한 비동기 메서드 본문에서 나가는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ec469ed4f9c4fa2e503b2350235299a81a94bf9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902113"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion 메서드
TASK_STATE_WAIT_COMPLETION_NOTIFICATION 상태 비트를 설정하거나 지웁니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib(mscorlib.dll) **

## <a name="syntax"></a>구문

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>매개 변수
 `enabled`

 `true` 비트를 설정하려면 이고, `false` 비트의 설정을 해제하려면 입니다.

## <a name="exceptions"></a>예외

## <a name="remarks"></a>설명
 디버거는 비동기 메서드 본문에서 나가도록 이 비트를 설정합니다. `enabled`가 `true` 이면 이 메서드는 아직 완료되지 않은 작업에서만 호출해야 합니다. `enabled`가 `false` 이면 완료된 작업에서 이 메서드를 호출할 수 있습니다. 두 이벤트 모두 프라미스 스타일 작업에만 사용해야 합니다.

## <a name="requirements"></a>요구 사항

## <a name="see-also"></a>참고 항목
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
