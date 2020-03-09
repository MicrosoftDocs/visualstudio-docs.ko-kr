---
title: ImportGroup 요소 | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76dadd1a064a64884e3ff1cd1f2431bc1b94c3c4
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633735"
---
# <a name="importgroup-element"></a>ImportGroup 요소

  
선택적인 조건으로 그룹화된 `Import` 요소의 컬렉션을 포함합니다. 자세한 내용은 [Import 요소(MSBuild)](../msbuild/import-element-msbuild.md)를 참조하세요.

```xml
<Project>
  <ImportGroup>
```

## <a name="syntax"></a>구문

```xml
<ImportGroup Condition="'String A' == 'String B'">
    <Import ... />
    <Import ... />
</ImportGroup>
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Condition`|선택적 특성입니다.<br /><br /> 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Import](../msbuild/import-element-msbuild.md)|한 프로젝트 파일의 내용을 다른 프로젝트 파일로 가져옵니다.|

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| - | - |
| [프로젝트](../msbuild/project-element-msbuild.md) | MSBuild 프로젝트 파일의 필수 루트 요소입니다. |

## <a name="example"></a>예제

 다음 코드 예제에서는 `ImportGroup` 요소를 보여 줍니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ImportGroup>
        <Import Project="$(Targets1.targets)" />
        <Import Project="$(Targets2.targets)" />
    </ImportGroup>
...
</Project>
```

## <a name="see-also"></a>참조

- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
- [항목](../msbuild/msbuild-items.md)
