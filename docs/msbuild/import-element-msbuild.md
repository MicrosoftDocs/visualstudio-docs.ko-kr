---
title: Import 요소(MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 044c531432de987fc7f3d34ce5344ad0374bcd00
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633748"
---
# <a name="import-element-msbuild"></a>Import 요소(MSBuild)

한 프로젝트 파일의 내용을 다른 프로젝트 파일로 가져옵니다.

\<프로젝트> \<가져오기>

## <a name="syntax"></a>구문

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Project`|필수 특성입니다.<br /><br /> 가져올 프로젝트 파일의 경로입니다. 경로에 와일드카드를 포함할 수 있습니다. 일치하는 파일은 정렬된 순서로 가져오게 됩니다. 이 기능을 사용하여, 디렉터리에 코드 파일을 추가함으로써 프로젝트에 코드를 추가할 수 있습니다.|
|`Condition`|선택적 특성입니다.<br /><br /> 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|
|`Sdk`| 선택적 특성입니다.<br /><br /> 프로젝트 SDK를 참조합니다.|

### <a name="child-elements"></a>자식 요소

 없음

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| - | - |
| [프로젝트](../msbuild/project-element-msbuild.md) | MSBuild 프로젝트 파일의 필수 루트 요소입니다. |
| [ImportGroup](../msbuild/importgroup-element.md) | 선택적인 조건으로 그룹화된 `Import` 요소의 컬렉션을 포함합니다. |

## <a name="remarks"></a>설명

 `Import` 요소를 사용하면 여러 프로젝트 파일에 공통된 코드를 다시 사용할 수 있습니다. 이렇게 하면 공유 코드에 대한 업데이트가 그것을 가져오는 모든 프로젝트에 전파되므로 코드를 더 쉽게 유지 관리할 수 있습니다.

 규칙상 가져온 공유 프로젝트 파일은 *.targets* 파일로 저장되지만 실제로는 표준 MSBuild 프로젝트 파일입니다. MSBuild에서는 다른 파일 이름 확장명을 가진 프로젝트를 가져오는 것이 금지되지 않지만, 일관성을 위해 *.targets* 확장명을 사용할 것을 권장합니다.

 가져온 프로젝트의 상대 경로는 가져오는 프로젝트의 디렉터리를 기준으로 해석됩니다. 따라서 프로젝트 파일을 서로 다른 위치의 여러 프로젝트 파일로 가져온 경우, 가져온 프로젝트 파일의 상대 경로는 가져온 각 프로젝트에 대해 다르게 해석됩니다.

 가져온 프로젝트에서 참조되는, 프로젝트 파일과 관련된 MSBuild의 모든 예약된 속성(예: `MSBuildProjectDirectory` 및 `MSBuildProjectFile`)은 가져오는 프로젝트 파일을 기반으로 값이 할당됩니다.

 가져온 프로젝트에 `DefaultTargets` 특성이 없는 경우 가져온 프로젝트는 가져온 순서대로 검사되며, 처음 검색된 `DefaultTargets` 특성의 값이 사용됩니다. 예를 들어 ProjectA가 ProjectB와 ProjectC를 순서대로 가져오고 ProjectB가 ProjectD를 가져오는 경우에 MSBuild는 먼저 ProjectA에 지정된 `DefaultTargets`를 검색한 다음 ProjectB, ProjectD, 마지막으로 ProjectC를 검색합니다.

 가져온 프로젝트의 스키마는 표준 프로젝트의 스키마와 동일합니다. MSBuild는 가져온 프로젝트를 빌드할 수는 있지만 그럴 가능성은 매우 낮습니다. 일반적으로 가져온 프로젝트에는 설정할 속성 또는 대상을 실행할 순서에 대한 정보가 포함되어 있지 않기 때문입니다. 가져온 프로젝트는 그것을 가져온 상위 프로젝트에 의존하여 해당 정보를 제공합니다.

## <a name="wildcards"></a>와일드카드

 .NET Framework 4에서는 MSBuild가 Project 특성에 와일드카드를 사용하도록 허용합니다. 와일드카드가 있으면 발견되는 모든 일치 항목이 정렬되고(재현 가능성을 위해), 마치 해당 순서가 명시적으로 설정된 것처럼 순서대로 가져오기가 수행됩니다.

 이는 파일 이름을 가져오기 파일에 명시적으로 추가하지 않고도 다른 사람이 파일을 가져올 수 있도록 확장성 지점을 제공하려는 경우 유용합니다. 이를 위해 *Microsoft.Common.Targets*는 파일의 상단에 다음 줄을 포함합니다.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>예제

 다음 예제에서는 여러 항목과 속성이 있는 프로젝트를 보여주고 일반 프로젝트 파일을 가져옵니다.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>참조

- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
- [방법: 여러 프로젝트 파일에서 동일한 대상 사용](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
