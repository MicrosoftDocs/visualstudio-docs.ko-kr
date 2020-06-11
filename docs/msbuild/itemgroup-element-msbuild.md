---
title: ItemGroup 요소(MSBuild) | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c058a5986f72192a86d0e554d9e0d0b9bdce1b42
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173514"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup 요소(MSBuild)

사용자 정의 [Item](../msbuild/item-element-msbuild.md) 요소 집합을 포함합니다. MSBuild 프로젝트에서 사용되는 모든 항목은 `ItemGroup` 요소의 자식으로 지정해야 합니다.

\<Project>
\<ItemGroup>

## <a name="syntax"></a>구문

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Condition`|선택적 특성입니다. 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|
|`Label`|선택적 특성입니다. `ItemGroup`를 식별합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|빌드 프로세스에 대한 입력을 정의합니다. `ItemGroup`에는 0개 이상의 `Item` 요소가 있을 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| - | - |
| [프로젝트](../msbuild/project-element-msbuild.md) | MSBuild 프로젝트 파일의 필수 루트 요소입니다. |
| [Target](../msbuild/target-element-msbuild.md) | .NET Framework 3.5부터 `ItemGroup` 요소는 `Target` 요소 내에 표시될 수 있습니다. 자세한 내용은 [대상](../msbuild/msbuild-targets.md)을 참조하세요. |

## <a name="example"></a>예제

다음 코드 예제에서는 사용자 정의 항목 컬렉션 `Res` 및 `ItemGroup` 요소 내에 선언된 `CodeFiles`를 보여 줍니다. `Res` 항목 컬렉션의 각 항목은 사용자 정의 자식 [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) 요소를 포함합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

간단한 프로젝트 파일에서는 일반적으로 단일 `ItemGroup` 요소를 사용하지만 여러 `ItemGroup` 요소를 사용할 수도 있습니다. 여러 `ItemGroup` 요소가 사용되는 경우 항목은 단일 `ItemGroup`으로 결합됩니다. 예를 들어 일부 항목은 가져온 파일에 정의된 별도의 `ItemGroup` 요소에 포함될 수 있습니다.

ItemGroups에는 `Condition` 특성을 사용하여 적용되는 조건이 있을 수 있습니다. 이 경우 조건이 충족되는 경우에만 항목이 항목 목록에 추가됩니다. [MSBuild 조건](msbuild-conditions.md)을 참조하세요.

## <a name="see-also"></a>참조

- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
- [항목](../msbuild/msbuild-items.md)
- [일반적인 MSBuild 프로젝트 항목](../msbuild/common-msbuild-project-items.md)
