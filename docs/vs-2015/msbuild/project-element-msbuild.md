---
title: Project 요소(MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b11449626050c4da75b09f2d348a4b1b0190ec4d
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476928"
---
# <a name="project-element-msbuild"></a>Project 요소(MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트 파일의 필수 루트 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|       특성        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `DefaultTargets`    |                                                                                                                                                                                                                                                                                                 선택적 특성입니다.<br /><br /> 대상이 지정되지 않은 경우 빌드 진입점으로 사용할 하나 이상의 기본 대상입니다. 대상이 여러 개인 경우 세미콜론(;)으로 구분합니다.<br /><br /> `DefaultTargets` 특성 또는 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 명령줄에 기본 대상이 없으면 엔진은 [Import](../msbuild/import-element-msbuild.md) 요소를 평가한 후 프로젝트 파일의 첫 번째 대상을 실행합니다.                                                                                                                                                                                                                                                                                                  |
|    `InitialTargets`    |                                                                                                                                                                                                                                                                                                                                                                                                                                             선택적 특성입니다.<br /><br /> `DefaultTargets` 특성 또는 명령줄에 지정된 대상을 실행하기 전에 실행할 하나 이상의 초기 대상입니다. 대상이 여러 개인 경우 세미콜론(;)으로 구분합니다.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     `ToolsVersion`     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             선택적 특성입니다.<br /><br /> $(MSBuildBinPath) 및 $(MSBuildToolsPath)의 값을 확인하기 위해 MSBuild가 사용하는 도구 집합의 버전입니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreatAsLocalProperty` | 선택적 특성입니다.<br /><br /> 전역으로 간주하지 않을 속성 이름입니다. 이 특성을 사용하는 경우 특정 명령줄 속성이 프로젝트 또는 대상 파일과 모든 후속 가져오기에서 설정되는 속성값을 재정의할 수 없습니다. 속성이 여러 개인 경우 세미콜론(;)으로 구분합니다.<br /><br /> 일반적으로 전역 속성은 프로젝트 또는 대상 파일에서 설정되는 속성값을 재정의합니다. `TreatAsLocalProperty` 값에 속성이 나열되어 있는 경우에는 전역 속성값이 해당 파일 및 모든 후속 가져오기에서 설정되는 속성값을 재정의하지 않습니다. 자세한 내용은 [방법: 동일한 소스 파일을 다른 옵션을 사용하여 빌드](../msbuild/how-to-build-the-same-source-files-with-different-options.md)를 참조하세요. **참고:****/property** 또는 **/p**) 스위치를 사용하여 명령 프롬프트에서 전역 속성을 설정합니다. MSBuild 작업의 `Properties` 특성을 사용하여 다중 프로젝트 빌드의 자식 프로젝트에 대해 전역 속성을 설정하거나 수정할 수도 있습니다. 자세한 내용은 [MSBuild 작업](../msbuild/msbuild-task.md)을 참조하세요. |
|        `Xmlns`         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 필수 특성 (MSBuild 4.x 및 이전 버전).<br /><br /> `xmlns` 특성에는 `http://schemas.microsoft.com/developer/msbuild/2003`값이 있어야 합니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|선택적 요소입니다.<br /><br /> 자식 요소를 평가하여 평가할 `ItemGroup` 요소 및/또는 `PropertyGroup` 요소의 집합 하나를 선택합니다.|  
|[가져오기](../msbuild/import-element-msbuild.md)|선택적 요소입니다.<br /><br /> 프로젝트 파일이 다른 프로젝트 파일을 가져올 수 있도록 설정합니다. 프로젝트에는 `Import` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|선택적 요소입니다.<br /><br /> 개별 항목에 대한 grouping 요소입니다. [Item](../msbuild/item-element-msbuild.md) 요소를 사용하여 항목을 지정합니다. 프로젝트에는 `ItemGroup` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|선택적 요소입니다.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트 파일에서 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 이외의 정보를 유지하는 방법을 제공합니다. 프로젝트에는 `ProjectExtensions` 요소가 없을 수도 있고 하나 있을 수 있습니다.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|선택적 요소입니다.<br /><br /> 개별 속성에 대한 grouping 요소입니다. [Property](../msbuild/property-element-msbuild.md) 요소를 사용하여 속성을 지정합니다. 프로젝트에는 `PropertyGroup` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다.|  
|[대상](../msbuild/target-element-msbuild.md)|선택적 요소입니다.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에 대해 순차적으로 실행할 작업 집합을 포함합니다. [Task](../msbuild/task-element-msbuild.md) 요소를 사용하여 작업을 지정합니다. 프로젝트에는 `Target` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|선택적 요소입니다.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에서 작업을 등록하는 방법을 제공합니다. 프로젝트에는 `UsingTask` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다.|  
  
### <a name="parent-elements"></a>부모 요소  
 None.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 먼저 빌드할 대상 지정](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)   
 [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](msbuild.md)
