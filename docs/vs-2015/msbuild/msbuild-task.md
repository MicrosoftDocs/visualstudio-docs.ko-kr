---
title: MSBuild 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2349c21d55c20bcb3bcd50ab96f383a9afcc00b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842171"
---
# <a name="msbuild-task"></a>MSBuild 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다른 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트에서 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트를 빌드합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `MSBuild` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`BuildInParallel`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 `Projects` 매개 변수에 지정된 프로젝트가 가능한 경우 병렬로 빌드됩니다. 기본값은 `false`입니다.|  
|`Projects`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 빌드할 프로젝트 파일을 지정합니다.|  
|`Properties`|선택적 `String` 매개 변수입니다.<br /><br /> 자식 프로젝트에 전역 속성으로 적용할 속성 이름/값 쌍의 세미콜론으로 구분된 목록입니다. 이 매개 변수를 지정 하는 경우 [MSBuild.exe](../msbuild/msbuild-command-line-reference.md)를 사용 하 여 빌드할 때 **/property** 스위치가 있는 속성을 설정 하는 것과 기능적으로 동일 합니다. 예를 들어:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> `Properties` 매개 변수를 통해 프로젝트에 속성을 전달하면 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에서는 프로젝트 파일이 이미 로드되었더라도 프로젝트의 새 인스턴스를 만듭니다. 프로젝트의 새 인스턴스가 만들어지면 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 해당 인스턴스를 프로젝트의 다른 인스턴스와 병렬로 빌드할 수 있으며 다른 전역 속성이 포함된 다른 프로젝트로 처리합니다. 예를 들어 릴리스 구성을 디버그 구성과 동시에 빌드할 수 있습니다.|  
|`RebaseOutputs`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 빌드한 프로젝트의 대상 출력 항목 상대 경로가 호출 프로젝트를 기준으로 조정됩니다. 기본값은 `false`입니다.|  
|`RemoveProperties`|선택적 `String` 매개 변수입니다.<br /><br /> 제거할 전역 속성의 집합을 지정합니다.|  
|`RunEachTargetSeparately`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 작업이 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에 전달된 목록의 각 대상을 동시에 호출하는 대신 한 번에 하나씩 호출합니다. 이 매개 변수를 `true`로 설정하면 이전에 호출된 대상에 오류가 발생하더라도 후속 대상이 호출됩니다. 그렇지 않은 경우에는 빌드 오류로 인해 모든 후속 대상의 호출이 중지됩니다. 기본값은 `false`입니다.|  
|`SkipNonexistentProjects`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 디스크에 없는 프로젝트 파일을 건너뜁니다. 그렇지 않은 경우 이러한 프로젝트로 인해 오류가 발생합니다.|  
|`StopOnFirstFailure`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 프로젝트 중 하나를 빌드하지 못하면 더 이상 프로젝트를 빌드하지 않습니다. 현재 여러 프로세서를 사용하여 병렬로 빌드할 때는 이 매개 변수가 지원되지 않습니다.|  
|`TargetAndPropertyListSeparators`|선택적 `String[]` 매개 변수입니다.<br /><br /> 대상 및 속성의 목록을 `Project` 항목 메타데이터로 지정합니다. 처리 전에 구분 기호를 이스케이프 해제합니다. 예를 들어 %3B(이스케이프된 ';')는 이스케이프 해제된 ';'로 처리됩니다.|  
|`TargetOutputs`|선택적 읽기 전용 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 모든 프로젝트 파일에서 작성된 대상의 출력을 반환합니다. 해당 대상이 종속된 대상에 있을 수 있는 출력이 아닌, 지정된 대상의 출력만 반환됩니다.<br /><br /> `TargetOutputs` 매개 변수는 다음 메타데이터도 포함합니다.<br /><br /> -   `MSBuildSourceProjectFile`: 출력을 설정하는 대상이 포함된 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트 파일입니다.<br />-   `MSBuildSourceTargetName`: 출력을 설정하는 대상입니다. **참고:**  각 프로젝트 파일이나 대상의 출력을 개별적으로 식별하려는 경우 각 프로젝트 파일 또는 대상에 대해 `MSBuild` 작업을 개별적으로 실행합니다. `MSBuild` 작업을 한 번만 실행하여 모든 프로젝트 파일을 빌드하는 경우에는 모든 대상의 출력이 배열 하나에 수집됩니다.|  
|`Targets`|선택적 `String` 매개 변수입니다.<br /><br /> 프로젝트 파일에서 빌드할 하나 이상의 대상을 지정합니다. 세미콜론을 사용하여 대상 이름 목록을 구분합니다. `MSBuild` 작업에 대상이 지정되어 있지 않으면 프로젝트 파일에 지정된 기본 대상이 빌드됩니다. **참고:**  모든 프로젝트 파일에는 대상이 있어야 합니다. 대상이 없으면 빌드 오류가 발생합니다.|  
|`ToolsVersion`|선택적 `String` 매개 변수입니다.<br /><br /> 이 작업에 전달된 프로젝트를 빌드할 때 사용할 `ToolsVersion`을 지정합니다.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 작업이 프로젝트에 지정된 것과 다른 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전을 대상으로 하는 프로젝트를 빌드할 수 있도록 설정합니다. 유효한 값은 `2.0`, `3.0` 및 `3.5`입니다. 기본값은 `3.5`여야 합니다.|  
|`UnloadProjectsOnCompletion`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 작업이 완료되면 프로젝트가 언로드됩니다.|  
|`UseResultsCache`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 캐시된 결과(있는 경우)가 반환됩니다. MSBuild 작업이 실행되면 해당 결과는 (ProjectFileName, GlobalProperties)[TargetNames] 범위에<br /><br /> 빌드 항목의 목록으로 캐시됩니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
 [Exec Task](../msbuild/exec-task.md)를 사용하여 MSBuild.exe를 시작하는 경우와 달리 이 작업에서는 동일한 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로세스를 사용하여 자식 개체를 빌드합니다. 건너뛸 수 있는 이미 빌드된 대상의 목록은 부모 빌드와 자식 빌드 간에 공유됩니다. 또한 새 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로세스가 만들어지지 않으므로 이 작업은 속도도 더 빠릅니다.  
  
 이 작업에서는 프로젝트 파일뿐 아니라 솔루션 파일도 처리할 수 있습니다.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에서 여러 프로젝트를 동시에 빌드하는 데 필요한 모든 구성(해당 구성이 포트, 프로토콜, 시간 제한, 다시 시도 등의 원격 인프라를 사용하는 경우도 포함됨)은 구성 파일을 통해 구성 가능하도록 지정해야 합니다. 가능한 경우에는 `MSBuild` 작업에 대한 작업 매개 변수로 구성 항목을 지정할 수 있어야 합니다.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5부터는 솔루션 프로젝트가 이제 빌드하는 모든 하위 프로젝트에서 TargetOutputs를 표시합니다.  
  
## <a name="passing-properties-to-projects"></a>프로젝트에 속성 전달  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5 이전 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 버전에서는 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 항목에 나열된 각 프로젝트에 서로 다른 속성 집합을 전달하기가 어려웠습니다. [Msbuild 작업](../msbuild/msbuild-task.md)의 Properties 특성을 사용한 경우 [msbuild 작업](../msbuild/msbuild-task.md) 을 일괄 처리 하 고 항목 목록에서 각 프로젝트에 대 한 다른 속성을 조건부로 제공 하지 않는 한, 빌드 중인 모든 프로젝트에 해당 설정이 적용 되었습니다.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 그러나 3.5에서는 [MSBuild 작업](../msbuild/msbuild-task.md)을 사용 하 여 빌드하는 여러 프로젝트에 대해 다양 한 속성을 전달할 수 있는 유연한 방법을 제공 하는 두 개의 새로운 예약 된 메타 데이터 항목인 Properties와 AdditionalProperties를 제공 합니다.  
  
> [!NOTE]
> 이러한 새 메타 데이터 항목은 [MSBuild 작업](../msbuild/msbuild-task.md)의 Projects 특성에 전달 된 항목에만 적용 됩니다.  
  
## <a name="multi-processor-build-benefits"></a>다중 프로세서 빌드의 이점  
 이러한 새 메타데이터를 사용하는 경우의 주요 이점 중 하나는 다중 프로세서 시스템에서 병렬로 프로젝트를 빌드할 때 제공됩니다. 메타데이터를 사용하면 일괄 처리 또는 조건부 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 작업을 수행하지 않고도 모든 프로젝트를 단일 [MSBuild 작업](../msbuild/msbuild-task.md)에 통합할 수 있습니다. 단일 [MSBuild](../msbuild/msbuild-task.md)작업만 호출 하는 경우 projects 특성에 나열 된 모든 프로젝트는 병렬로 빌드됩니다. 그러나 `BuildInParallel=true` [MSBuild 작업](../msbuild/msbuild-task.md)에 특성이 있는 경우에만 해당 됩니다. 자세한 내용은 [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)를 참조 하세요.  
  
## <a name="properties-metadata"></a>Properties 메타데이터  
 일반적인 시나리오는 [MSBuild 작업](../msbuild/msbuild-task.md)을 사용 하 여 여러 솔루션 파일을 빌드하고 다른 빌드 구성만 사용 하는 경우입니다. 예를 들어 a1 솔루션은 디버그 구성을 사용하여 빌드하고 a2 솔루션은 릴리스 구성을 사용하여 빌드할 수 있습니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0에서 이 프로젝트 파일은 다음과 같이 표시됩니다.  
  
> [!NOTE]
> 다음 예제에서 "..."는 추가 솔루션 파일을 나타냅니다.  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 그러나 속성 메타 데이터를 사용 하면 다음과 같이 단일 [MSBuild 작업](../msbuild/msbuild-task.md)을 사용 하도록 단순화할 수 있습니다.  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \- 또는 -  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## <a name="additionalproperties-metadata"></a>AdditionalProperties 메타데이터  
 [MSBuild 작업](../msbuild/msbuild-task.md)을 사용 하 여 두 개의 솔루션 파일을 빌드하는 경우, 릴리스 구성을 사용 하 고 x86 아키텍처를 사용 하는 시나리오와 ia64 아키텍처를 사용 하는 시나리오를 살펴보겠습니다. 이러한 솔루션 파일을 빌드하려면 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0에서는 [MSBuild 작업](../msbuild/msbuild-task.md)의 여러 인스턴스를 만들어야 했습니다. 즉, x86 아키텍처가 포함된 릴리스 구성을 사용하는 프로젝트를 빌드하는 인스턴스 하나와 ia64 아키텍처가 포함된 릴리스 구성을 사용하는 또 다른 인스턴스를 만들어야 했습니다. 이 경우 프로젝트 파일은 다음과 같이 표시됩니다.  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 AdditionalProperties 메타 데이터를 사용 하면 다음을 사용 하 여 단일 [MSBuild 작업](../msbuild/msbuild-task.md) 을 사용 하도록 단순화할 수 있습니다.  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>예제  
 다음 예제에서는 `MSBuild` 작업을 사용하여 `ProjectReferences` 항목 컬렉션으로 지정된 프로젝트를 빌드합니다. 결과 대상 출력은 `AssembliesBuiltByChildProjects` 항목 컬렉션에 저장됩니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>참고 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
