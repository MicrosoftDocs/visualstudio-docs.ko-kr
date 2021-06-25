---
title: 작업 클래스 - 내부 멤버 | Microsoft Docs
description: 사용자 지정 디버거를 구현하는 데 도움이 되는 System.Threading.Tasks.Task 클래스의 내부 멤버에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 37691714d0168594b61a1a3849f7b65264e9999e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902893"
---
# <a name="task-class---internal-members"></a>작업 클래스 - 내부 멤버
이 문서에서는 사용자 지정 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 디버거를 구현하는 데 도움이 되는 클래스의 내부 멤버에 대해 설명합니다. 이 클래스에 대한 일반적인 내용은 <xref:System.Threading.Tasks.Task> 참조 문서를 참조하세요.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib(mscorlib.dll) **

 .NET Framework 이러한 내부 멤버에 액세스할 수 없으므로 다음 구문은 CIL(공용 중간 언어)로 제공됩니다.

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
|[SetNotificationForWaitCompletion 메서드](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|TASK_STATE_WAIT_COMPLETION_NOTIFICATION 상태 비트를 설정하거나 지웁니다.|
|[NotifyDebuggerOfWaitCompletion 메서드](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|디버거에서 중단점 대상으로 사용되는 자리 표시자 메서드입니다.|

### <a name="fields"></a>필드

|이름|설명|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|개체에서 실행할 코드를 나타내는 <xref:System.Threading.Tasks.Task> 대리자입니다.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|개체의 추가 속성을 <xref:System.Threading.Tasks.Task> 저장합니다.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|부모 속성의 지원 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 필드입니다.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|개체의 현재 상태에 대한 정보를 <xref:System.Threading.Tasks.Task> 저장합니다.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|작업에서 사용할 데이터를 나타내는 개체입니다.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|속성의 지원 <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> 필드입니다.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|개체에 사용할 수 있는 다음 <xref:System.Threading.Tasks.Task> 식별자입니다.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|작업이 실행 상태에 도달하기 전에 취소되었음을 나타내거나 작업이 취소를 확인하고 예외 없이 완료되었음을 나타냅니다.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|태스크가 실행 중임을 나타냅니다.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|처리되지 않은 예외로 인해 작업이 완료되었음을 나타냅니다.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|태스크 실행이 성공적으로 완료되었음을 나타냅니다.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|태스크가 대리자 실행을 완료했으며 연결된 자식 작업이 완료되는 것을 암시적으로 기다리고 있음을 나타냅니다.|

## <a name="remarks"></a>설명
 다음 내부 메서드는 코드 실행에 대한 진입을 표시하기 때문에 디버거 엔진에 유용합니다. <xref:System.Threading.Tasks.Task>

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>참조
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [.NET Framework 대한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
