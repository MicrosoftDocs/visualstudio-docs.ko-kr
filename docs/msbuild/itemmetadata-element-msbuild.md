---
title: ItemMetadata 요소(MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18e1722fcd6867ca5e8ae52e220ff0a3dd2a3b7f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633618"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata 요소(MSBuild)

항목 메타데이터 값을 포함하는 사용자 정의 항목 메타데이터 키를 포함합니다. 한 항목에 메타데이터 키-값 쌍이 얼마든지 포함될 수 있습니다.

 \<Project> \<ItemGroup> \<Item>

## <a name="syntax"></a>구문

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Condition`|선택적 특성입니다.<br /><br /> 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|

### <a name="child-elements"></a>자식 요소

 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|빌드 프로세스에 대한 입력을 정의하는 사용자 정의 요소입니다.|

## <a name="text-value"></a>텍스트 값

 텍스트 값은 선택적입니다.

 이 텍스트는 항목 메타데이터 값을 텍스트 또는 XML로 지정합니다.

## <a name="example"></a>예제

 다음 코드 예제에서는 `CSFile` 항목에 `fr` 값을 가진 `Culture` 메타데이터를 추가하는 방법을 보여 줍니다.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>참조

- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
- [항목](../msbuild/msbuild-items.md)
