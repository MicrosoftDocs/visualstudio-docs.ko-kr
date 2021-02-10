---
title: ReadLinesFromFile 작업 | Microsoft Docs
description: MSBuild가 ReadLinesFromFile 작업을 사용하여 텍스트 파일에서 항목 목록을 읽는 방법을 알아봅니다. 파일은 각 줄에 하나의 항목이 있어야 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0361d0103afbe662a37b50358e125018a7378f39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931970"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile 작업

텍스트 파일에서 항목 목록을 읽습니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `ReadLinesFromFile` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`File`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 읽을 파일을 지정합니다. 파일은 각 줄에 하나의 항목이 있어야 합니다.|
|`Lines`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 파일에서 읽은 줄을 포함합니다.|

## <a name="remarks"></a>설명

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 예제는 `ReadLinesFromFile` 작업을 사용하여 텍스트 파일의 목록에서 항목을 만듭니다. 파일에서 읽은 항목은 `ItemsFromFile` 항목 컬렉션에 저장됩니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
    </ItemGroup>

    <Target Name="ReadFromFile">
        <ReadLinesFromFile
            File="@(MyTextFile)" >
            <Output
                TaskParameter="Lines"
                ItemName="ItemsFromFile"/>
        </ReadLinesFromFile>
    </Target>

</Project>
```

## <a name="see-also"></a>참고 항목

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [작업](../msbuild/msbuild-tasks.md)
