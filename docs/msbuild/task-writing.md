---
title: 작업 작성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cbcf47ec83e1b900ba94ab3842c2cfa63fdcc5d
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631839"
---
# <a name="task-writing"></a>작업 작성

작업은 빌드 프로세스 동안 실행되는 코드를 제공합니다. 작업은 대상에 포함되어 있습니다. 일반적인 작업의 라이브러리는 MSBuild에 포함되어 있으며 사용자 고유의 작업을 만들 수도 있습니다. MSBuild에 포함된 작업의 라이브러리에 대한 자세한 내용은 [작업 참조](../msbuild/msbuild-task-reference.md)에서 확인하세요.

## <a name="tasks"></a>작업

 작업의 예에는 하나 이상의 파일을 복사하는 [Copy](../msbuild/copy-task.md), 디렉터리를 만드는 [MakeDir](../msbuild/makedir-task.md), C# 소스 코드 파일을 컴파일하는 [Csc](../msbuild/csc-task.md)가 포함되어 있습니다. 각 작업은 <xref:Microsoft.Build.Framework.ITask> 인터페이스를 구현하는 .NET 클래스로 구현됩니다. 이 인터페이스는 *Microsoft.Build.Framework.dll* 어셈블리에서 정의됩니다.

 작업을 구현할 때 다음 두 가지 방법을 사용할 수 있습니다.

- <xref:Microsoft.Build.Framework.ITask> 인터페이스를 직접 구현합니다.

- 도우미 클래스 <xref:Microsoft.Build.Utilities.Task>에서 클래스를 파생합니다. 이 클래스는 *Microsoft.Build.Utilities.dll* 어셈블리에서 정의됩니다. 작업은 ITask를 구현하고 일부 ITask 멤버의 기본 구현을 제공합니다. 또한 로깅이 쉽습니다.

두 경우 모두 작업이 실행될 때 호출되는 방법인 `Execute`라는 메서드를 클래스에 추가해야 합니다. 이 메서드는 매개 변수를 사용하지 않으며 `Boolean` 값을 반환합니다. 작업이 성공하는 경우 `true`, 실패하는 경우 `false`를 반환합니다. 다음 예제는 아무 작업도 수행하지 않고 `true`를 반환하는 작업을 보여 줍니다.

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }
    }
}
```

 다음 프로젝트 파일은 이 작업을 실행합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 작업이 실행될 때 작업 클래스에서 .NET 속성을 만드는 경우 프로젝트 파일에서 입력을 받을 수도 있습니다. MSBuild는 작업의 `Execute` 메서드를 호출하기 바로 전에 이러한 속성을 설정합니다. 문자열 속성을 만들려면 다음과 같은 작업 코드를 사용합니다.

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }

        public string MyProperty { get; set; }
    }
}
```

 다음 프로젝트 파일은 이 작업을 실행하고 `MyProperty`를 지정된 값으로 설정합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>작업 등록

 프로젝트가 작업을 실행하려는 경우 MSBuild는 작업 클래스를 포함하는 어셈블리를 찾는 방법을 알고 있어야 합니다. 작업은 [UsingTask 요소(MSBuild)](../msbuild/usingtask-element-msbuild.md)를 사용하여 등록됩니다.

 MSBuild 파일 *Microsoft.Common.Tasks*는 MSBuild와 함께 제공된 모든 작업을 등록하는 `UsingTask` 요소의 목록을 포함하는 프로젝트 파일입니다. 이 파일은 모든 프로젝트를 빌드할 때 자동으로 포함됩니다. *Microsoft.Common.Tasks*에 등록된 작업이 현재 프로젝트 파일에도 등록된 경우 현재 프로젝트 파일이 우선 순위를 가집니다. 즉, 동일한 이름을 가진 고유 작업으로 기본 작업을 재정의할 수 있습니다.

> [!TIP]
> *Microsoft.Common.Tasks*의 내용을 확인하여 MSBuild와 함께 제공되는 작업의 목록을 볼 수 있습니다.

## <a name="raise-events-from-a-task"></a>작업에서 이벤트 발생

 작업이 <xref:Microsoft.Build.Utilities.Task> 도우미 클래스에서 파생되는 경우 <xref:Microsoft.Build.Utilities.Task> 클래스의 다음 도우미 클래스 중 하나를 사용하여 모든 등록된 로커로 발견되고 등록되는 이벤트를 발생시킬 수 있습니다.

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 작업이 <xref:Microsoft.Build.Framework.ITask>를 직접 구현하는 경우 이러한 이벤트를 여전히 발생시킬 수 있지만 IBuildEngine 인터페이스를 사용해야 합니다. 다음 예제는 ITask를 구현하고 사용자 지정 이벤트를 발생시키는 작업을 보여 줍니다.

```csharp
public class SimpleTask : ITask
{
    public IBuildEngine BuildEngine { get; set; }

    public override bool Execute()
    {
        TaskEventArgs taskEvent =
            new TaskEventArgs(BuildEventCategory.Custom,
            BuildEventImportance.High, "Important Message",
           "SimpleTask");
        BuildEngine.LogBuildEvent(taskEvent);
        return true;
    }
}
```

## <a name="require-task-parameters-to-be-set"></a>설정하는 데 필요한 작업 매개 변수

 작업을 실행하는 모든 프로젝트 파일이 이러한 속성의 값을 설정해야 할 수 있도록 특정 작업 속성을 "required"로 표시할 수 있습니다. 그렇지 않으면 빌드가 실패합니다. `[Required]` 특성을 다음과 같이 작업의 .NET 속성에 적용합니다.

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 `[Required]` 특성은 <xref:Microsoft.Build.Framework> 네임스페이스에서 <xref:Microsoft.Build.Framework.RequiredAttribute>로 정의됩니다.

## <a name="how-msbuild-invokes-a-task"></a>MSBuild가 작업을 호출하는 방법

작업을 호출할 때 MSBuild는 먼저 작업 클래스를 인스턴스화한 다음, 프로젝트 파일의 작업 요소에 설정된 작업 매개 변수에 대해 해당 개체의 속성 setter를 호출합니다. 작업 요소가 매개 변수를 지정하지 않거나 요소에 지정된 식이 빈 문자열로 평가되는 경우에는 속성 setter가 호출되지 않습니다.

예를 들어 다음 프로젝트를 가정해 봅시다.

```xml
<Project>
 <Target Name="InvokeCustomTask">
  <CustomTask Input1=""
              Input2="$(PropertyThatIsNotDefined)"
              Input3="value3" />
 </Target>
</Project>
```

이 경우 `Input3`의 setter만 호출됩니다.

작업에서 매개 변수-속성 setter 호출의 상대 순서를 사용하면 안 됩니다.

### <a name="task-parameter-types"></a>작업 매개 변수 형식

MSBuild는 기본적으로 `string`, `bool`, `ITaskItem`, `ITaskItem[]` 형식의 속성을 처리합니다. 작업이 다른 형식의 매개 변수를 허용하는 경우, MSBuild는 <xref:System.Convert.ChangeType%2A>을 호출하여 모든 속성 및 항목 참조가 펼쳐진 `string`에서 대상 형식으로 변환합니다. 변환에 실패한 입력 매개 변수가 하나라도 있으면 MSBuild는 오류를 내보내고 작업의 `Execute()` 메서드를 호출하지 않습니다.

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 C# 클래스는 <xref:Microsoft.Build.Utilities.Task> 도우미 클래스에서 파생되는 작업을 보여 줍니다. 이 작업은 성공했음을 나타내는 `true`를 반환합니다.

### <a name="code"></a>코드

```csharp
using System;
using Microsoft.Build.Utilities;

namespace SimpleTask1
{
    public class SimpleTask1: Task
    {
        public override bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 C# 클래스는 <xref:Microsoft.Build.Framework.ITask> 인터페이스를 구현하는 작업을 보여 줍니다. 이 작업은 성공했음을 나타내는 `true`를 반환합니다.

### <a name="code"></a>코드

```csharp
using System;
using Microsoft.Build.Framework;

namespace SimpleTask2
{
    public class SimpleTask2: ITask
    {
        //When implementing the ITask interface, it is necessary to
        //implement a BuildEngine property of type
        //Microsoft.Build.Framework.IBuildEngine. This is done for
        //you if you derive from the Task class.
        public IBuildEngine BuildEngine { get; set; }

        // When implementing the ITask interface, it is necessary to
        // implement a HostObject property of type object.
        // This is done for you if you derive from the Task class.
        public object HostObject { get; set; }

        public bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example"></a>예제

### <a name="description"></a>설명

이 C# 클래스는 <xref:Microsoft.Build.Utilities.Task> 도우미 클래스에서 파생되는 작업을 보여 줍니다. 필수 문자열 속성이 있으며 등록된 모든 로거로 표시되는 이벤트를 발생시킵니다.

### <a name="code"></a>코드

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 이전 예제 작업, SimpleTask3을 호출하는 프로젝트 파일을 보여 줍니다.

### <a name="code"></a>코드

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <UsingTask TaskName="SimpleTask3.SimpleTask3"
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>

    <Target Name="MyTarget">
        <SimpleTask3 MyProperty="Hello!"/>
    </Target>
</Project>
```

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
