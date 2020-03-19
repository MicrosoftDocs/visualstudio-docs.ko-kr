---
title: FindUnderPath 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d97b727dcba8cd16fe97ee33764947797c36db7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634138"
---
# <a name="findunderpath-task"></a>FindUnderPath 작업

지정된 항목 컬렉션의 항목에 지정된 폴더 및 모든 하위 폴더에 있는 경로가 있는지를 확인합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 `FindUnderPath` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`Files`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 경로를 `Path` 매개 변수에서 지정한 경로와 비교해야 하는 파일을 지정합니다.|
|`InPath`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 지정된 경로에서 발견된 항목을 포함합니다.|
|`OutOfPath`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 지정된 경로에서 발견되지 않은 항목을 포함합니다.|
|`Path`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 참조로 사용할 폴더 경로를 지정합니다.|
|`UpdateToAbsolutePaths`|선택적 `Boolean` 매개 변수입니다.<br /><br /> true인 경우 출력 항목의 경로를 절대 경로로 업데이트합니다.|

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Utilities.Task> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 `FindUnderPath` 작업을 사용하여 `MyFiles` 항목에 포함된 파일에 `SearchPath` 속성에서 지정한 경로 아래에 있는 경로가 포함되어 있는지를 확인합니다. 작업이 완료되면 `FilesNotFoundInPath` 항목에 *File1.txt* 파일이 포함되고 `FilesFoundInPath` 항목에 *File2.txt* 파일이 포함됩니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyFiles Include="C:\File1.txt" />
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />
    </ItemGroup>

    <PropertyGroup>
        <SearchPath>C:\Projects\MyProject</SearchPath>
    </PropertyGroup>

    <Target Name="FindFiles">
        <FindUnderPath
            Files="@(MyFiles)"
            Path="$(SearchPath)">
            <Output
                TaskParameter="InPath"
                ItemName="FilesFoundInPath" />
            <Output
                TaskParameter="OutOfPath"
                ItemName="FilesNotFoundInPath" />
        </FindUnderPath>
    </Target>

</Project>
```

## <a name="see-also"></a>참고 항목

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [작업](../msbuild/msbuild-tasks.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
