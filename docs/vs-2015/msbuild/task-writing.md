---
title: 작업 작성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaf927b1049709a04d8a883615d1997e9316599e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841690"
---
# <a name="task-writing"></a>작업 작성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

작업은 빌드 프로세스 동안 실행되는 코드를 제공합니다. 작업은 대상에 포함되어 있습니다. 일반적인 작업의 라이브러리는 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에 포함되어 있으며 사용자 고유의 작업을 만들 수도 있습니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에 포함된 작업의 라이브러리에 대한 자세한 내용은 [작업 참조](../msbuild/msbuild-task-reference.md)를 참조하세요.  
  
## <a name="tasks"></a>작업  
 작업의 예에는 하나 이상의 파일을 복사하는 [Copy](../msbuild/copy-task.md), 디렉터리를 만드는 [MakeDir](../msbuild/makedir-task.md), [!INCLUDE[csprcs](../includes/csprcs-md.md)] 소스 코드 파일을 컴파일하는 [Csc](../msbuild/csc-task.md)가 포함되어 있습니다. 각 작업은 <xref:Microsoft.Build.Framework.ITask> 인터페이스를 구현하는 .NET 클래스로 구현됩니다. 이 인터페이스는 Microsoft.Build.Framework.dll 어셈블리에서 정의됩니다.  
  
 작업을 구현할 때 다음 두 가지 방법을 사용할 수 있습니다.  
  
- <xref:Microsoft.Build.Framework.ITask> 인터페이스를 직접 구현합니다.  
  
- 도우미 클래스 <xref:Microsoft.Build.Utilities.Task>에서 클래스를 파생합니다. 이 클래스는 Microsoft.Build.Utilities.dll 어셈블리에서 정의됩니다. 작업은 ITask를 구현하고 일부 ITask 멤버의 기본 구현을 제공합니다. 또한 로깅이 쉽습니다.  
  
  두 경우 모두 작업이 실행될 때 호출되는 방법인 `Execute`라는 메서드를 클래스에 추가해야 합니다. 이 메서드는 매개 변수를 사용하지 않으며 `Boolean` 값을 반환합니다. 작업이 성공하는 경우 `true`, 실패하는 경우 `false`를 반환합니다. 다음 예제는 아무 작업도 수행하지 않고 `true`를 반환하는 작업을 보여 줍니다.  
  
```  
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
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 작업이 실행될 때 작업 클래스에서 .NET 속성을 만드는 경우 프로젝트 파일에서 입력을 받을 수도 있습니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]은(는) 작업의 `Execute` 메서드를 호출하기 바로 전에 이러한 속성을 설정합니다. 문자열 속성을 만들려면 다음과 같은 작업 코드를 사용합니다.  
  
```  
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
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 다음 프로젝트 파일은 이 작업을 실행하고 `MyProperty`를 지정된 값으로 설정합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>작업 등록  
 프로젝트가 작업을 실행하려는 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]은(는) 작업 클래스를 포함하는 어셈블리를 찾는 방법을 알고 있어야 합니다. 작업은 [UsingTask 요소(MSBuild)](../msbuild/usingtask-element-msbuild.md)를 사용하여 등록됩니다.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 파일 Microsoft.Common.Tasks는 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]와(과) 함께 제공된 모든 작업을 등록하는 `UsingTask` 요소의 목록을 포함하는 프로젝트 파일입니다. 이 파일은 모든 프로젝트를 빌드할 때 자동으로 포함됩니다. Microsoft.Common.Tasks에 등록된 작업이 현재 프로젝트 파일에도 등록된 경우 현재 프로젝트 파일이 우선 순위를 가집니다. 즉, 동일한 이름을 가진 고유 작업으로 기본 작업을 재정의할 수 있습니다.  
  
> [!TIP]
> Microsoft.Common.Tasks의 내용을 확인하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]와(과) 함께 제공되는 작업의 목록을 볼 수 있습니다.  
  
## <a name="raising-events-from-a-task"></a>작업에서 이벤트 발생시키기  
 작업이 <xref:Microsoft.Build.Utilities.Task> 도우미 클래스에서 파생되는 경우 <xref:Microsoft.Build.Utilities.Task> 클래스의 다음 도우미 클래스 중 하나를 사용하여 모든 등록된 로커로 발견되고 등록되는 이벤트를 발생시킬 수 있습니다.  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 작업이 <xref:Microsoft.Build.Framework.ITask>를 직접 구현하는 경우 이러한 이벤트를 여전히 발생시킬 수 있지만 IBuildEngine 인터페이스를 사용해야 합니다. 다음 예제는 ITask를 구현하고 사용자 지정 이벤트를 발생시키는 작업을 보여 줍니다.  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
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
  
## <a name="requiring-task-parameters-to-be-set"></a>설정하는 데 필요한 작업 매개 변수  
 작업을 실행하는 모든 프로젝트 파일이 이러한 속성의 값을 설정해야 할 수 있도록 특정 작업 속성을 "required"로 표시할 수 있습니다. 그렇지 않으면 빌드가 실패합니다. `[Required]` 특성을 다음과 같이 작업의 .NET 속성에 적용합니다.  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]` 특성은 <xref:Microsoft.Build.Framework> 네임스페이스에서 <xref:Microsoft.Build.Framework.RequiredAttribute>로 정의됩니다.  
  
## <a name="example"></a>예제  
  
### <a name="description"></a>Description  
 다음 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 클래스는 <xref:Microsoft.Build.Utilities.Task> 도우미 클래스에서 파생되는 작업을 보여 줍니다. 이 작업은 성공했음을 나타내는 `true`를 반환합니다.  
  
### <a name="code"></a>코드  
  
```  
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
  
### <a name="description"></a>Description  
 다음 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 클래스는 <xref:Microsoft.Build.Framework.ITask> 인터페이스를 구현하는 작업을 보여 줍니다. 이 작업은 성공했음을 나타내는 `true`를 반환합니다.  
  
### <a name="code"></a>코드  
  
```  
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
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
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
 이 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 클래스는 <xref:Microsoft.Build.Utilities.Task> 도우미 클래스에서 파생되는 작업을 보여 줍니다. 필수 문자열 속성이 있으며 등록된 모든 로거로 표시되는 이벤트를 발생시킵니다.  
  
### <a name="code"></a>코드  
 [!code-csharp[msbuild_SimpleTask3#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs#1)]  
  
## <a name="example"></a>예제  
  
### <a name="description"></a>설명  
 다음 예제에서는 이전 예제 작업, SimpleTask3을 호출하는 프로젝트 파일을 보여 줍니다.  
  
### <a name="code"></a>코드  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>참고 항목  
 [작업 참조](../msbuild/msbuild-task-reference.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
