---
title: CombinePath 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7e6a79198ad54d3432f30fe9b57b3133a94165e
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288964"
---
# <a name="combinepath-task"></a>CombinePath 작업

지정된 경로를 단일 경로로 결합합니다.
## <a name="task-parameters"></a>작업 매개 변수

 다음 표에서는 [CombinePath 작업](../msbuild/combinepath-task.md)의 매개 변수에 대해 설명합니다.


|매개 변수|설명|
|---------------|-----------------|
|`BasePath`|필수 `String` 매개 변수입니다.<br /><br /> 다른 경로와 결합할 기본 경로입니다. 상대 경로, 절대 경로 또는 빈 값일 수 있습니다.|
|`Paths`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> BasePath와 결합되어 결합된 경로를 구성할 개별 경로의 목록입니다. 경로는 상대 경로이거나 절대 경로일 수 있습니다.|
|`CombinedPaths`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 이 작업에서 만든 조합된 경로입니다.|

## <a name="remarks"></a>설명

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

 다음 예제에서는 `CombinePath`를 사용하여 `$(ReleaseDirectory)`와 연결된 루트 경로 `$(PublishRoot)`와 하위 폴더 목록 `$(LangDirectories)`를 결합함으로써 `$(OutputDirectory)` 속성을 구성하여 출력 폴더 구조를 만드는 방법을 보여 줍니다.

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

`CombinePath`가 목록이 될 수 있는 유일한 속성은 `Paths`입니다. 이 경우 출력도 목록입니다. 따라서 `$(PublishRoot)`가 *C:\Site1\\* 이고, `$(ReleaseDirectory)`가 *Release\\* 이고, `@(LangDirectories)`가 *en-us\;fr-fr\\* 인 경우 이 예제는 다음 폴더를 만듭니다.

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
