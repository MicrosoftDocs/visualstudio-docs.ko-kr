---
title: 작업 클래스-내부 멤버 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712742"
---
# <a name="task-class---internal-members"></a>작업 클래스-내부 멤버
이 문서에서는 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 사용자 지정 디버거를 구현 하는 데 도움이 되는 클래스의 내부 멤버에 대해 설명 합니다. 이 클래스에 대 한 일반 정보는 <xref:System.Threading.Tasks.Task> 참조 문서를 참조 하세요.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib ( *mscorlib.dll*)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.

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

|속성|설명|
|----------|-----------------|
|[SetNotificationForWaitCompletion 메서드](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|TASK_STATE_WAIT_COMPLETION_NOTIFICATION 상태 비트를 설정 하거나 해제 합니다.|
|[NotifyDebuggerOfWaitCompletion 메서드](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|디버거에서 중단점 대상으로 사용 되는 자리 표시자 메서드입니다.|

### <a name="fields"></a>필드

|Name|설명|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|개체에서 실행할 코드를 나타내는 대리자입니다 <xref:System.Threading.Tasks.Task> .|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|개체의 추가 속성을 저장 <xref:System.Threading.Tasks.Task> 합니다.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|부모 속성에 대 한 지원 필드 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 입니다.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|개체의 현재 상태에 대 한 정보를 저장 <xref:System.Threading.Tasks.Task> 합니다.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|작업에서 사용 되는 데이터를 나타내는 개체입니다.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|속성의 지원 필드 <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> 입니다.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|개체의 다음으로 사용할 수 있는 식별자 <xref:System.Threading.Tasks.Task> 입니다.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|작업이 실행 중 상태에 도달 하기 전에 취소 되었거나 태스크가 취소를 확인 하 고 예외 없이 완료 되었음을 나타냅니다.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|태스크가 실행 중임을 나타냅니다.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|처리 되지 않은 예외로 인해 태스크가 완료 되었음을 나타냅니다.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|태스크 실행이 성공적으로 완료 되었음을 나타냅니다.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|태스크가 대리자 실행을 완료 하 고 연결 된 자식 작업이 완료 될 때까지 암시적으로 대기 중임을 나타냅니다.|

## <a name="remarks"></a>설명
 다음 내부 메서드는 코드 실행에 대 한 표시를 표시 하기 때문에 디버거 엔진에 유용 합니다 <xref:System.Threading.Tasks.Task> .

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>참고 항목
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [.NET Framework에 대 한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
