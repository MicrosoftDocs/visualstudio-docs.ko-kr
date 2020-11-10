---
title: ParameterGroup 요소 | Microsoft Docs
description: UsingTask TaskFactory에서 생성한 작업에 표시되는 선택적 매개 변수 목록을 포함하는 MSBuild ParameterGroup 요소에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 104a7313104e194a85d9eb4fee00e84a8facb5b5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048873"
---
# <a name="parametergroup-element"></a>ParameterGroup 요소

`UsingTask` `TaskFactory`에 의해 생성된 작업에 존재할 매개 변수의 선택적 목록을 포함합니다. 자세한 내용은 [UsingTask 요소(MSBuild)](../msbuild/usingtask-element-msbuild.md)를 참조하세요.

 \<Project> \<UsingTask>
 \<ParameterGroup>

## <a name="syntax"></a>구문

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

 없음

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[매개 변수](../msbuild/parameter-element.md)|`UsingTask` `TaskFactory`에 의해 생성되는 작업에 대한 특정 매개 변수 정보를 포함합니다. 요소의 이름은 매개 변수의 이름입니다.|

### <a name="parent-elements"></a>부모 요소

| 요소 | Description |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | MSBuild에서 작업을 등록하는 방법을 제공합니다. 프로젝트에는 `UsingTask` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다. |

## <a name="example"></a>예제

 다음 예제에서는 `ParameterGroup` 요소를 사용하는 방법을 보여 줍니다.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
