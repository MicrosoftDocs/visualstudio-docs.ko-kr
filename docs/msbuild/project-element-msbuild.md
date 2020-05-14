---
title: Project 요소(MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9eff3e941cc21aaa71c2779a72084e12e8e590
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632981"
---
# <a name="project-element-msbuild"></a>Project 요소(MSBuild)

MSBuild 프로젝트 파일의 필수 루트 요소입니다.

## <a name="syntax"></a>구문

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
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

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

| 특성 | 설명 |
|------------------------| - |
| `DefaultTargets` | 선택적 특성입니다.<br /><br /> 대상이 지정되지 않은 경우 빌드 진입점으로 사용할 하나 이상의 기본 대상입니다. 대상이 여러 개인 경우 세미콜론(;)으로 구분합니다.<br /><br /> `DefaultTargets` 특성 또는 MSBuild 명령줄에 지정된 기본 대상이 없으면 엔진은 [Import](../msbuild/import-element-msbuild.md) 요소를 평가한 후 프로젝트 파일의 첫 번째 대상을 실행합니다. |
| `InitialTargets` | 선택적 특성입니다.<br /><br /> `DefaultTargets` 특성 또는 명령줄에 지정된 대상을 실행하기 전에 실행할 하나 이상의 초기 대상입니다. 대상이 여러 개인 경우 세미콜론(`;`)으로 구분합니다. 가져온 여러 파일이 `InitialTargets`를 정의하는 경우 언급된 모든 대상이 가져오기가 발생한 순서대로 실행됩니다. |
| `Sdk` | 선택적 특성입니다. <br /><br /> .proj 파일에 추가되는 암시적 Import 문을 만드는 데 사용할 SDK 이름 및 선택적 버전입니다. 버전을 지정하지 않으면 MSBuild에서 기본 버전을 확인하려고 합니다.  예를 들어 `<Project Sdk="Microsoft.NET.Sdk" />` 또는 `<Project Sdk="My.Custom.Sdk/1.0.0" />`로 이름을 지정할 수 있습니다. |
| `ToolsVersion` | 선택적 특성입니다.<br /><br /> $(MSBuildBinPath) 및 $(MSBuildToolsPath)의 값을 확인하기 위해 MSBuild가 사용하는 도구 집합의 버전입니다. |
| `TreatAsLocalProperty` | 선택적 특성입니다.<br /><br /> 전역으로 간주하지 않을 속성 이름입니다. 이 특성을 사용하는 경우 특정 명령줄 속성이 프로젝트 또는 대상 파일과 모든 후속 가져오기에서 설정되는 속성값을 재정의할 수 없습니다. 속성이 여러 개인 경우 세미콜론(;)으로 구분합니다.<br /><br /> 일반적으로 전역 속성은 프로젝트 또는 대상 파일에서 설정되는 속성값을 재정의합니다. `TreatAsLocalProperty` 값에 속성이 나열되어 있는 경우에는 전역 속성값이 해당 파일 및 모든 후속 가져오기에서 설정되는 속성값을 재정의하지 않습니다. 자세한 내용은 [방법: 동일한 소스 파일을 다른 옵션을 사용하여 빌드](../msbuild/how-to-build-the-same-source-files-with-different-options.md)를 참조하세요. **참고:**  **-property**(또는 **-p**) 스위치를 사용하여 명령 프롬프트에서 글로벌 속성을 설정합니다. MSBuild 작업의 `Properties` 특성을 사용하여 다중 프로젝트 빌드의 자식 프로젝트에 대해 전역 속성을 설정하거나 수정할 수도 있습니다. 자세한 내용은 [MSBuild 작업](../msbuild/msbuild-task.md)을 참조하세요. |
| `xmlns` | 선택적 특성입니다.<br /><br /> 지정하는 경우 `xmlns` 특성은 `http://schemas.microsoft.com/developer/msbuild/2003`의 값이 있어야 합니다. |

### <a name="child-elements"></a>자식 요소

| 요소 | 설명 |
| - | - |
| [Choose](../msbuild/choose-element-msbuild.md) | 선택적 요소입니다.<br /><br /> 자식 요소를 평가하여 평가할 `ItemGroup` 요소 및/또는 `PropertyGroup` 요소의 집합 하나를 선택합니다. |
| [Import](../msbuild/import-element-msbuild.md) | 선택적 요소입니다.<br /><br /> 프로젝트 파일이 다른 프로젝트 파일을 가져올 수 있도록 설정합니다. 프로젝트에는 `Import` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다. |
| [ImportGroup](../msbuild/importgroup-element.md) | 선택적 요소입니다.<br /><br /> 선택적인 조건으로 그룹화된 `Import` 요소의 컬렉션을 포함합니다. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | 선택적 요소입니다.<br /><br /> 개별 항목에 대한 grouping 요소입니다. [Item](../msbuild/item-element-msbuild.md) 요소를 사용하여 항목을 지정합니다. 프로젝트에는 `ItemGroup` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | 선택적 요소입니다.<br /><br /> 기본적으로 프로젝트의 모든 항목에 적용되는 메타데이터 값인 항목 정의 집합을 정의할 수 있습니다. ItemDefinitionGroup을 사용하면 `CreateItem`작업 및 `CreateProperty` 작업을 사용할 필요가 없습니다. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | 선택적 요소입니다.<br /><br /> MSBuild 프로젝트 파일에서 MSBuild 이외의 정보를 유지하는 방법을 제공합니다. 프로젝트에는 `ProjectExtensions` 요소가 없을 수도 있고 하나 있을 수 있습니다. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | 선택적 요소입니다.<br /><br /> 개별 속성에 대한 grouping 요소입니다. [Property](../msbuild/property-element-msbuild.md) 요소를 사용하여 속성을 지정합니다. 프로젝트에는 `PropertyGroup` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | 선택적 요소입니다.<br /><br /> MSBuild 프로젝트 SDK를 참조합니다.  이 요소는 SDK 특성 대신 사용할 수 있습니다. |
| [Target](../msbuild/target-element-msbuild.md) | 선택적 요소입니다.<br /><br /> MSBuild가 순차적으로 실행할 작업 집합을 포함합니다. [Task](../msbuild/task-element-msbuild.md) 요소를 사용하여 작업을 지정합니다. 프로젝트에는 `Target` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | 선택적 요소입니다.<br /><br /> MSBuild에서 작업을 등록하는 방법을 제공합니다. 프로젝트에는 `UsingTask` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다. |

### <a name="parent-elements"></a>부모 요소

 없음

## <a name="see-also"></a>참조

- [방법: 먼저 빌드할 대상 지정](../msbuild/how-to-specify-which-target-to-build-first.md)
- [명령줄 참조](../msbuild/msbuild-command-line-reference.md)
- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
