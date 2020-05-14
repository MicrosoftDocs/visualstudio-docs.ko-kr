---
title: 알림디버거의웨이트완성방법 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8963e29a067754c0e8c89b9db336b239ac682ce1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738337"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>알림디버거의웨이트완료 방법
디버거에서 중단점 대상으로 사용되는 자리 표시자 메서드입니다. 이 메서드는 인라인 또는 최적화되지 않아야 합니다.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **조립:** mscorlib *(mscorlib.dll)*

## <a name="syntax"></a>구문

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>설명
 작업의 모든 조인 작업은 디버거 알림 비트가 설정된 경우 이 메서드를 호출해야 합니다.

## <a name="requirements"></a>요구 사항

## <a name="see-also"></a>참조
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
