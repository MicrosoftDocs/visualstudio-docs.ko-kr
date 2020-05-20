---
title: CreateItem 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4364e6c3f637fdf2c3e02a52d3163e5cdd8a5861
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634333"
---
# <a name="createitem-task"></a>CreateItem 작업

항목 컬렉션을 입력 항목으로 채웁니다. 이를 통해 한 목록의 항목을 다른 목록으로 복사할 수 있습니다.

> [!NOTE]
> 이 작업은 더 이상 사용되지 않습니다. .NET Framework 3.5부터 항목 그룹은 [Target](../msbuild/target-element-msbuild.md) 요소 내에 배치될 수 있습니다. 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

## <a name="attributes"></a>특성

 다음 표에서는 `CreateItem` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`AdditionalMetadata`|선택적 `String` 배열 매개 변수입니다.<br /><br /> 출력 항목에 연결할 추가 메타데이터를 지정합니다.  다음 구문을 사용하여 항목의 메타데이터 이름 및 값을 지정합니다.<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> 여러 메타데이터 이름/값 쌍은 세미콜론으로 구분해야 합니다. 이름 또는 값에 세미콜론이나 기타 특수 문자가 포함되는 경우 이스케이프되어야 합니다. 자세한 내용은 [방법: MSBuild의 이스케이프 특수 문자](../msbuild/how-to-escape-special-characters-in-msbuild.md)를 참조하세요.|
|`Exclude`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 출력 항목 컬렉션에서 제외할 항목을 지정합니다. 이 매개 변수는 와일드카드 지정을 포함할 수 있습니다. 자세한 내용은 [항목](../msbuild/msbuild-items.md) 및 [방법: 빌드에서 파일 제외](../msbuild/how-to-exclude-files-from-the-build.md)를 참조하세요.|
|`Include`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수<br /><br /> 출력 항목 컬렉션에 포함할 항목을 지정합니다. 이 매개 변수는 와일드카드 지정을 포함할 수 있습니다.|
|`PreserveExistingMetadata`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `True`인 경우 추가 메타데이터만 적용합니다(아직 존재하지 않을 경우).|

## <a name="remarks"></a>설명

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 코드 예제에서는 항목 컬렉션 `MySourceItems`에서 `MySourceItemsWithMetadata`라는 새 항목 컬렉션을 만듭니다. `CreateItem` 작업은 `MySourceItems` 항목에 있는 항목으로 새 항목 컬렉션을 채웁니다. 그런 다음 값이 `Hello`인 `MyMetadata`라는 추가 메타데이터 항목을 새 컬렉션의 각 항목에 추가합니다.

 작업이 실행된 후 `MySourceItemsWithMetadata` 항목 컬렉션에는 `MyMetadata`에 대한 메타데이터 항목을 포함하는 *file1.resx* 및 *file2.resx* 항목이 포함됩니다. `MySourceItems` 항목 컬렉션은 변경되지 않습니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceItems Include="file1.resx;file2.resx" />
    </ItemGroup>

    <Target Name="NewItems">
        <CreateItem
            Include="@(MySourceItems)"
            AdditionalMetadata="MyMetadata=Hello">
           <Output
               TaskParameter="Include"
               ItemName="MySourceItemsWithMetadata"/>
        </CreateItem>

    </Target>

</Project>
```

 다음 표에서는 작업 실행 이후의 출력 항목 값을 설명합니다. 항목 뒤에 괄호로 묶은 내용이 항목 메타데이터입니다.

|항목 컬렉션입니다.|콘텐츠|
|---------------------|--------------|
|`MySourceItemsWithMetadata`|*file1.resx*(`MyMetadata="Hello"`)<br /><br /> *file2.resx*(`MyMetadata="Hello"`)|

## <a name="see-also"></a>참고 항목

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [작업](../msbuild/msbuild-tasks.md)
