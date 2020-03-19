---
title: Copy 작업 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28fd0033f5ef6f83ca29432f95d6b635fcd36116
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634372"
---
# <a name="copy-task"></a>Copy 작업

파일 시스템의 새 위치에 파일을 복사합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 `Copy` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`CopiedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 실제로 복사되지 않았지만 이미 최신 상태이고 *가* 이기 때문에 건너뛴 항목을 비롯하여 성공적으로 복사된 항목을 포함합니다.`SkipUnchangedFiles``true`|
|`DestinationFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 소스 파일을 복사할 파일의 목록을 지정합니다. 이 목록은 `SourceFiles` 매개 변수에 지정된 목록이 포함된 일대일 매핑이어야 합니다. 즉, `SourceFiles`에 지정된 첫 번째 파일이 `DestinationFiles` 등에 지정된 첫 번째 위치에 복사됩니다.|
|`DestinationFolder`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 파일을 복사하려는 디렉터리를 지정합니다. 파일이 아닌 디렉터리여야 합니다. 디렉터리가 없는 경우 자동으로 생성됩니다.|
|`OverwriteReadOnlyFiles`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 파일이 읽기 전용으로 표시된 경우에 파일을 덮어씁니다.|
|`Retries`|선택적 `Int32` 매개 변수입니다.<br /><br /> 이전 시도가 모두 실패한 경우 복사를 시도할 횟수를 지정합니다. 기본값은 0입니다.<br /><br /> **참고:** 다시 시도하면 빌드 프로세스에서 동기화 문제를 마스킹할 수 있습니다.|
|`RetryDelayMilliseconds`|선택적 `Int32` 매개 변수입니다.<br /><br /> 필요한 다시 시도 간의 지연 시간을 지정합니다. 기본값은 CopyTask 생성자에 전달되는 RetryDelayMillisecondsDefault 인수입니다.|
|`SkipUnchangedFiles`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 소스와 대상 간에 변경되지 않은 파일의 복사를 건너뜁니다. 파일 크기가 같고 마지막으로 수정된 시간이 같으면 `Copy` 작업에서 파일이 변경되지 않은 것으로 간주합니다. <br /><br /> **참고:**  이 매개 변수를 `true`로 설정하면 포함 대상에 대한 종속성 분석을 사용하지 않아야 합니다. 소스 파일의 마지막으로 수정된 시간이 대상 파일의 마지막으로 수정된 시간보다 더 최신일 경우에만 작업을 수행하기 때문입니다.|
|`SourceFiles`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 복사할 파일을 지정합니다.|
|`UseHardlinksIfPossible`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 파일을 복사 하는 대신 복사된 파일에 대한 하드 링크를 만듭니다.|

## <a name="warnings"></a>경고

다음을 포함하여 경고가 기록됩니다.

- `Copy.DestinationIsDirectory`

- `Copy.SourceIsDirectory`

- `Copy.SourceFileNotFound`

- `Copy.CreatesDirectory`

- `Copy.HardLinkComment`

- `Copy.RetryingAsFileCopy`

- `Copy.FileComment`

- `Copy.RemovingReadOnlyAttribute`

## <a name="remarks"></a>설명

`DestinationFolder` 또는 `DestinationFiles` 매개 변수 중 하나(둘 다가 아닌)를 지정해야 합니다. 둘 다를 지정하는 경우 작업이 실패하고 오류가 기록됩니다.

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Utilities.Task> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 `MySourceFiles` 항목 컬렉션의 항목을 *c:\MyProject\Destination* 폴더로 복사합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFolder="c:\MyProject\Destination"
        />
    </Target>

</Project>
```

## <a name="example"></a>예제

다음 예제에서는 재귀적 복사를 수행하는 방법을 보여 줍니다. 이 프로젝트는 디렉터리 구조를 유지하면서 *c:\MySourceTree*의 모든 파일을 재귀적으로 *c:\MyDestinationTree*에 복사합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
