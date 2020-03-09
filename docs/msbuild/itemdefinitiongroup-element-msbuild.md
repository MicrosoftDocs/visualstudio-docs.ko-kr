---
title: ItemDefinitionGroup 요소(MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21e3b6554a9d6e0024cc21fd898962177acfffa7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633631"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup 요소(MSBuild)

`ItemDefinitionGroup` 요소를 사용하면 기본적으로 프로젝트의 모든 항목에 적용되는 메타데이터 값인 항목 정의 집합을 정의할 수 있습니다. ItemDefinitionGroup을 사용하면 [CreateItem 작업](../msbuild/createitem-task.md) 및 [CreateProperty 작업](../msbuild/createproperty-task.md)을 사용할 필요가 없습니다. 자세한 내용은 [항목 정의](../msbuild/item-definitions.md)를 참조하세요.

\<Project> \<ItemDefinitionGroup>

## <a name="syntax"></a>구문

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Condition`|선택적 특성입니다. 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|빌드 프로세스에 대한 입력을 정의합니다. `ItemDefinitionGroup`에는 0개 이상의 `Item` 요소가 있을 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| - | - |
| [프로젝트](../msbuild/project-element-msbuild.md) | MSBuild 프로젝트 파일의 필수 루트 요소입니다. |

## <a name="example"></a>예제

다음 코드 예제에서는 m과 n이라는 두 메타 데이터 항목을 ItemDefinitionGroup에 정의합니다. 이 예제에서 기본 메타데이터 "m"은 Item "i"로 명시적으로 정의되지 않으므로 Item "i"에 적용됩니다. 그러나 기본 메타데이터 "n"은 Item "i"로 이미 정의되어 있으므로 Item "i"에 적용되지 않습니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemDefinitionGroup>
        <i>
            <m>m1</m>
            <n>n1</n>
        </i>
    </ItemDefinitionGroup>
    <ItemGroup>
        <i Include="a">
            <o>o1</o>
            <n>n2</n>
        </i>
    </ItemGroup>
    ...
</Project>
```

## <a name="see-also"></a>참조

- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
- [항목](../msbuild/msbuild-items.md)
