---
title: NotifyDebuggerOfWaitCompletion 메서드 | Microsoft Docs
description: 디버거에서 중단점 대상으로 사용되는 자리 표시자인 NotifyDebuggerOfWaitCompletion 메서드에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b9d6b5fbdcb8195709a751117056bcaa0617eff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904219"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion 메서드
디버거에서 중단점 대상으로 사용되는 자리 표시자 메서드입니다. 이 메서드는 인라인되거나 최적화되지 않아야 합니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib(mscorlib.dll) **

## <a name="syntax"></a>구문

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>설명
 작업을 사용하는 모든 조인 작업은 디버거 알림 비트가 설정된 경우 이 메서드를 호출해야 합니다.

## <a name="requirements"></a>요구 사항

## <a name="see-also"></a>참고 항목
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
