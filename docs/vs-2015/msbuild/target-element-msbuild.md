---
title: Target 요소(MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f14815502a33fb7d49a10c2724c57a4a0d86e9f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144311"
---
# <a name="target-element-msbuild"></a>Target 요소(MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

순차적으로 실행할 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]의 작업 집합을 포함합니다.  
  
 \<Project>  
 \<Target>  
  
## <a name="syntax"></a>구문  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`Name`|필수 특성입니다.<br /><br /> 대상의 이름입니다.|  
|`Condition`|선택적 특성입니다.<br /><br /> 평가할 조건입니다. 조건이 `false`로 평가되면 해당 대상 또는 `DependsOnTargets` 특성에 설정되어 있는 대상의 본문이 실행되지 않습니다. 조건에 대한 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|  
|`Inputs`|선택적 특성입니다.<br /><br /> 이 대상에 대한 입력을 구성하는 파일입니다. 파일이 여러 개인 경우 세미콜론으로 구분합니다. 파일의 타임스탬프를 `Outputs`에 있는 파일의 타임스탬프와 비교하여 `Target`이 최신 상태인지를 확인합니다. 자세한 내용은 [증분 빌드](../msbuild/incremental-builds.md), [방법: 증분 빌드](../msbuild/how-to-build-incrementally.md)및 [변환](../msbuild/msbuild-transforms.md)을 참조 하세요.|  
|`Outputs`|선택적 특성입니다.<br /><br /> 이 대상에 대한 출력을 구성하는 파일입니다. 파일이 여러 개인 경우 세미콜론으로 구분합니다. 파일의 타임스탬프를 `Inputs`에 있는 파일의 타임스탬프와 비교하여 `Target`이 최신 상태인지를 확인합니다. 자세한 내용은 [증분 빌드](../msbuild/incremental-builds.md), [방법: 증분 빌드](../msbuild/how-to-build-incrementally.md)및 [변환](../msbuild/msbuild-transforms.md)을 참조 하세요.|  
|`Returns`|선택적 특성입니다.<br /><br /> 이 대상을 호출하는 작업(예: MSBuild 작업)에 대해 제공할 항목 집합입니다. 대상이 여러 개인 경우 세미콜론으로 구분합니다. 파일의 대상에 `Returns` 특성이 없으면 Outputs 특성이 이 용도로 대신 사용됩니다.|  
|`KeepDuplicateOutputs`|선택적 부울 특성입니다.<br /><br /> `true`인 경우 대상의 Returns에서 같은 항목에 대한 여러 참조가 기록됩니다.  기본적으로 이 특성은 `false`입니다.|  
|`BeforeTargets`|선택적 특성입니다.<br /><br /> 대상 이름의 세미콜론으로 구분된 목록입니다.  지정하는 경우 하나 이상의 지정된 대상을 실행하기 전에 이 대상을 실행해야 함을 나타납니다. 이렇게 하면 프로젝트 작성자가 기존 대상 집합을 직접 수정하지 않고 확장할 수 있습니다. 자세한 내용은 [대상 빌드 순서](../msbuild/target-build-order.md)를 참조 하세요.|  
|`AfterTargets`|선택적 특성입니다.<br /><br /> 대상 이름의 세미콜론으로 구분된 목록입니다. 지정하는 경우 하나 이상의 지정된 대상을 실행한 후에 이 대상을 실행해야 함을 나타납니다. 이렇게 하면 프로젝트 작성자가 기존 대상 집합을 직접 수정하지 않고 확장할 수 있습니다. 자세한 내용은 [대상 빌드 순서](../msbuild/target-build-order.md)를 참조 하세요.|  
|`DependsOnTargets`|선택적 특성입니다.<br /><br /> 이 대상을 실행하거나 최상위 종속성 분석을 수행하려면 실행해야 하는 대상입니다. 대상이 여러 개인 경우 세미콜론으로 구분합니다.|  
|`Label`|선택적 특성입니다.<br /><br /> 시스템 및 사용자 요소를 식별하거나 정렬할 수 있는 식별자입니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[Task](../msbuild/task-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 작업의 인스턴스를 만들고 실행합니다. 대상에는 작업이 없을 수도 있고 하나 이상 있을 수도 있습니다.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|사용자 정의 `Property` 요소 집합을 포함합니다. .NET Framework 3.5부터는 `Target` 요소가 `PropertyGroup` 요소를 포함할 수 있습니다.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|사용자 정의 `Item` 요소 집합을 포함합니다. .NET Framework 3.5부터는 `Target` 요소가 `ItemGroup` 요소를 포함할 수 있습니다. 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.|  
|[OnError](../msbuild/onerror-element-msbuild.md)|실패한 작업의 `ContinueOnError` 특성이 ErrorAndStop 또는 `false`인 경우 하나 이상의 대상이 실행되도록 합니다. 대상에는 `OnError` 요소가 없을 수도 있고 하나 이상 있을 수도 있습니다. `OnError` 요소는 있는 경우 `Target` 요소의 마지막 요소여야 합니다.<br /><br /> 특성에 대 한 자세한 내용은 `ContinueOnError` [Task 요소 (MSBuild)](../msbuild/task-element-msbuild.md)를 참조 하세요.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[프로젝트](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트 파일의 필수 루트 요소입니다.|  
  
## <a name="remarks"></a>설명  
 실행할 첫 번째 대상은 런타임에 지정됩니다. 대상은 다른 대상에 대한 종속성을 포함할 수 있습니다. 예를 들어 배포용 대상은 컴파일용 대상에 종속됩니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 엔진은 종속성을 `DependsOnTargets` 특성에 나타나는 순서대로 왼쪽에서 오른쪽으로 실행합니다. 자세한 내용은 [대상](../msbuild/msbuild-targets.md)을 참조하세요.  
  
 둘 이상의 대상이 종속성을 포함하고 있더라도 대상은 빌드 중에 한 번만 실행됩니다.  
  
 `Condition` 특성이 `false`로 평가되어 대상을 건너뛰더라도 빌드의 뒷부분에서 해당 대상을 호출하는 시점에 `Condition` 특성이 `true`로 평가되면 대상을 실행할 수 있습니다.  
  
 MSBuild 4 이전 버전에서 `Target`은 `Outputs` 특성에 지정된 모든 항목을 반환했습니다.  이를 위해 MSBuild는 빌드 뒷부분의 작업이 요청할 때를 대비하여 이러한 항목을 기록해야 했습니다. 호출자에게 필요한 출력을 포함하는 대상을 나타낼 방법이 없었으므로 MSBuild는 호출된 모든 `Target`에서 모든 `Outputs`의 항목을 모두 누적 기록했습니다. 이로 인해 출력 항목 수가 많은 빌드의 경우 확장 문제가 발생했습니다.  
  
 사용자가 프로젝트의 `Target` 요소에 대해 `Returns`를 지정하는 경우 `Returns` 특성이 포함된 `Target`만 해당 항목을 기록합니다.  
  
 `Target`은 `Outputs` 특성 및 `Returns` 특성을 모두 포함할 수 있습니다.  `Outputs`는 `Inputs`과 함께 사용되어 대상이 최신 상태인지를 확인합니다. `Returns`(있는 경우)는 `Outputs`의 값을 재정의하여 호출자에게 반환되는 항목을 결정합니다.  `Returns`가 없으면 앞에서 설명하는 경우를 제외하고 `Outputs`가 호출자에게 제공됩니다.  
  
 MSBuild 4 이전 버전에서는 `Target`에 `Outputs`의 같은 항목에 대한 여러 참조가 포함되어 있는 경우 항상 중복 항목이 기록되었습니다. 중복 항목은 전혀 사용되지 않으므로 출력 수와 프로젝트 상호 종속성이 많은 대형 빌드에서는 이러한 방식으로 인해 많은 양의 메모리가 낭비됩니다. `KeepDuplicateOutputs` 특성을 `true`로 설정하면 이러한 중복 항목이 기록됩니다.  
  
## <a name="example"></a>예제  
 다음 코드 예제는 `Csc` 작업을 실행하는 `Target` 요소를 보여 줍니다.  
  
```  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>관련 항목  
 [대상](../msbuild/msbuild-targets.md)   
 [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
