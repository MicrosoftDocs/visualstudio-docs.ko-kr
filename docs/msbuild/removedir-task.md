---
title: RemoveDir 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RemoveDir task [MSBuild]
- MSBuild, RemoveDir task
ms.assetid: 7ab214be-26b2-4bcd-9de8-c1b2091c0b74
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26a6feeca7c89a67e7dd51bd0a1f99a182ffac59
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632799"
---
# <a name="removedir-task"></a>RemoveDir 작업

지정한 디렉터리와 모든 파일 및 하위 디렉터리를 제거합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `RemoveDir` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`Directories`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 삭제할 디렉터리를 지정합니다.|
|`RemovedDirectories`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 삭제된 디렉터리를 포함합니다.|

## <a name="remarks"></a>설명

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 예제에서는 `OutputDirectory` 및 `DebugDirectory` 속성에서 지정된 디렉터리를 제거합니다. 이러한 경로는 프로젝트 디렉터리에 상대적으로 처리됩니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2005">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
        <DebugDirectory>\Debug\</DebugDirectory>
    </PropertyGroup>

    <Target Name="RemoveDirectories">
        <RemoveDir
            Directories="$(OutputDirectory);$(DebugDirectory)" />
    </Target>

</Project>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
