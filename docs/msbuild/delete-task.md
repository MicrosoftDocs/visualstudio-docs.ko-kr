---
title: Delete 작업 | Microsoft Docs
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eddb9804378a4c32de9d1b68f952bc715f32ffd6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288912"
---
# <a name="delete-task"></a>Delete 작업

지정한 파일을 삭제합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 `Delete` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`DeletedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 삭제된 파일을 지정합니다.|
|`Files`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 삭제할 파일을 지정합니다.|
|`TreatErrorsAsWarnings`|선택적 `Boolean` 매개 변수<br /><br /> `true`이면 오류가 경고로 기록됩니다. 기본값은 `false`입니다.|

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

> [!WARNING]
> `Delete` 작업과 함께 와일드카드를 사용할 때는 주의해야 합니다. 특히 속성이 빈 문자열로 평가되는 경우 `$(SomeProperty)\**\*.*` 또는 `$(SomeProperty)/**/*.*`와 같은 식이 포함된 잘못된 파일을 쉽게 삭제할 수 있습니다. 이 경우 `Files` 매개 변수는 드라이브의 루트로 평가되며 삭제하려 했던 것보다 훨씬 많이 삭제할 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 `DeleteDebugSymbolFile` 대상을 빌드할 때 *MyApp.pdb* 파일을 삭제합니다.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

삭제된 파일을 추적해야 하는 경우 다음과 같이 `TaskParameter`를 항목 이름과 함께 `DeletedFiles`로 설정합니다.

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

`Delete` 작업에서 와일드카드를 직접 사용하는 대신 삭제할 파일의 `ItemGroup`을 만들고 해당 파일에 대해 `Delete` 작업을 실행합니다. 그러나 `ItemGroup`은 신중하게 입력해야 합니다. `ItemGroup`을 프로젝트 파일의 최상위 수준에 배치하는 경우 빌드를 시작하기 전에 미리 계산되므로 빌드 프로세스의 일부로 빌드된 파일이 포함되지 않습니다. 따라서 `Delete` 작업에 가까운 대상에 삭제할 항목 목록을 만드는 `ItemGroup`를 배치합니다. 또한 드라이브의 루트에서 시작하는 경로를 사용하여 항목 목록을 만들지 않도록 해당 속성이 비어 있지 않은 상태인지 확인하는 조건을 지정할 수 있습니다.

`Delete` 작업은 파일을 삭제합니다. 디렉터리를 삭제하려면 [RemoveDir](removedir-task.md)를 사용합니다.

`Delete` 작업은 읽기 전용 파일을 삭제하는 옵션을 제공하지 않습니다. 읽기 전용 파일을 삭제하려면 `Exec` 작업을 사용하여 `del` 명령(또는 이와 동등한 명령)을 읽기 전용 파일을 삭제할 수 있는 적절한 옵션으로 실행합니다. 명령줄에 길이 제한이 있으므로 입력 항목 목록의 길이에 주의해야 하며, 또한 다음 예제와 같이 공백으로 파일 이름을 처리하도록 해야 합니다.

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

일반적으로 빌드 스크립트를 작성할 때 삭제가 논리적으로 `Clean` 작업에 포함되는지 여부를 고려합니다. 일반 `Clean` 작업의 일부로 일부 파일을 정리할 수 있도록 설정해야 하는 경우 파일은 `@(FileWrites)` 목록에 추가할 수 있으며 다음 번 `Clean`에서 삭제됩니다. 사용자 지정 처리를 추가로 수행해야 하는 경우에는 대상을 정의하고 `BeforeTargets="Clean"` 또는 `AfterTargets="Clean"` 특성을 설정하여 실행되도록 지정하거나 `BeforeClean` 또는 `AfterClean` 대상의 사용자 지정 버전을 정의합니다. [빌드 사용자 지정](customize-your-build.md)을 참조하세요.

## <a name="see-also"></a>참조

- [RemoveDir 작업](removedir-task.md)
- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
