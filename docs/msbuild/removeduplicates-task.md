---
title: RemoveDuplicates 작업 | Microsoft Docs
ms.date: 03/01/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90366bab14eefd1be4edac81d6b09b3f57aa3332
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632786"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates 작업

지정된 항목 컬렉션에서 중복된 항목을 제거합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `RemoveDuplicates` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`Filtered`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 모든 중복 항목이 제거된 항목 컬렉션을 포함합니다. 입력 항목의 순서는 보존되므로 각 중복 항목의 첫 번째 인스턴스를 유지합니다.|
|`Inputs`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 중복 항목을 제거할 항목 컬렉션입니다.|

## <a name="remarks"></a>설명

 이 작업은 대/소문자를 구분하지 않으며 중복 항목을 결정할 때 항목 메타데이터를 비교하지 않습니다.

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 예제는 `RemoveDuplicates` 작업을 사용하여 `MyItems` 항목 컬렉션에서 중복 항목을 제거합니다. 작업이 완료될 때 `FilteredItems` 항목 컬렉션은 하나의 항목을 포함합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile.cs"/>
        <MyItems Include="MyFile.cs">
            <Culture>fr</Culture>
        </MyItems>
        <MyItems Include="myfile.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

 다음 예제는 `RemoveDuplicates` 작업에서 입력 순서가 보존됨을 보여줍니다. 작업이 완료되면 `FilteredItems` 항목 컬렉션에 *MyFile2.cs*, *MyFile1.cs* 및 *MyFile3.cs* 항목이 순서대로 포함됩니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile2.cs"/>
        <MyItems Include="MyFile1.cs" />
        <MyItems Include="MyFile3.cs" />
        <MyItems Include="myfile1.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [작업](../msbuild/msbuild-tasks.md)
