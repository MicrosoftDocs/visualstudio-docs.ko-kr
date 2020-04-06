---
title: 작업 클래스 - 내부 구성원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712742"
---
# <a name="task-class---internal-members"></a>작업 클래스 - 내부 멤버
이 문서에서는 사용자 지정 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 디버거를 구현하는 데 도움이 되는 클래스의 내부 멤버에 대해 설명합니다. 이 클래스에 대한 일반적인 <xref:System.Threading.Tasks.Task> 정보는 참조 문서를 참조하십시오.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **조립:** mscorlib *(mscorlib.dll)*

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없으므로 CIL(일반 중간 언어)에서 다음 구문이 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|이름|설명|
|----------|-----------------|
|[SetNotificationForWaitCompletion 메서드](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|TASK_STATE_WAIT_COMPLETION_NOTIFICATION 상태 비트를 설정하거나 지웁습니다.|
|[NotifyDebuggerOfWaitCompletion 메서드](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|디버거에서 중단점 대상으로 사용되는 자리 표시자 메서드입니다.|

### <a name="fields"></a>필드

|이름|설명|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|개체에서 실행할 코드를 나타내는 대리자입니다. <xref:System.Threading.Tasks.Task>|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|개체의 추가 <xref:System.Threading.Tasks.Task> 속성을 저장합니다.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|상위 속성의 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 백업 필드입니다.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|개체의 현재 상태에 대한 <xref:System.Threading.Tasks.Task> 정보를 저장합니다.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|작업에서 사용할 데이터를 나타내는 개체입니다.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|속성의 백업 <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> 필드입니다.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|개체에 대해 사용할 <xref:System.Threading.Tasks.Task> 수 있는 다음 식별자입니다.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|작업이 실행 상태에 도달하기 전에 취소했거나 작업이 취소를 확인하고 예외 없이 완료했음을 나타냅니다.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|작업이 실행 중임을 나타냅니다.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|처리되지 않은 예외로 인해 작업이 완료됨을 나타냅니다.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|작업이 성공적으로 실행을 완료했음을 나타냅니다.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|작업이 대리자 실행이 완료되었으며 연결된 자식 작업이 완료되기를 암시적으로 기다리고 있음을 나타냅니다.|

## <a name="remarks"></a>설명
 다음 내부 메서드는 코드 실행의 입구를 표시하기 <xref:System.Threading.Tasks.Task> 때문에 디버거 엔진에 유용합니다.

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>참조
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [.NET 프레임워크에 대한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
