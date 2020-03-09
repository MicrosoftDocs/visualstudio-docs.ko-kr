---
title: MSBuild를 사용하여 병렬로 여러 프로젝트 빌드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1723fba810450fe5e31a43d63f3704ab74f455f4
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634502"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>MSBuild를 사용하여 병렬로 여러 프로젝트 빌드

다중 프로젝트를 빌드하기 위해 MSBuild를 사용하여 병렬로 실행하면 더 빠를 수 있습니다. 빌드를 병렬로 실행하려면 다중 코어 또는 다중 프로세서 컴퓨터에서 다음 설정을 사용합니다.

- 명령 프롬프트에서 `-maxcpucount` 스위치.

- MSBuild 작업에서 <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> 작업 매개 변수.

> [!NOTE]
> 명령줄의 **verbosity**(**-v**) 스위치는 빌드 성능에 영향을 줄 수도 있습니다. 빌드 로그 정보의 자세한 정도는 문제 해결을 위해 사용되는 자세히 또는 진단으로 설정되어 있는 경우 빌드 성능이 저하될 수 있습니다. 자세한 내용은 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md) 및 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조하세요.

## <a name="-maxcpucount-switch"></a>-maxcpucount 스위치

시간을 줄이기 위해 `-maxcpucount` 스위치 또는 `-m`을 사용하는 경우 MSBuild는 병렬로 실행될 수 있는 *MSBuild.exe* 프로세스를 지정된 수만큼 생성할 수 있습니다. 이러한 프로세스는 "작업자 프로세스"라고도 합니다. 각 작업자 프로세스는 사용 가능한 다른 프로세스가 다른 프로젝트를 빌드할 때 동시에 별도의 코어 또는 프로세서(사용 가능한 경우)를 사용하여 프로젝트를 빌드합니다. 예를 들어, 해당 스위치의 값을 "4"로 설정하면 MSBuild에서 4개의 작업자 프로세스를 만들어 프로젝트를 빌드할 수 있습니다.

값을 지정하지 않고 `-maxcpucount` 스위치를 포함하는 경우, MSBuild는 컴퓨터의 최대 프로세서 수만큼 사용합니다.

MSBuild 3.5에 소개된 이 스위치에 대한 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조하세요.

다음 예제에서는 세 개의 작업자 프로세스를 사용하도록 MSBuild에 지시합니다. 이 구성을 사용하면 MSBuild는 동시에 세 개의 프로젝트를 빌드할 수 있습니다.

```cmd
msbuild.exe myproj.proj -maxcpucount:3
```

## <a name="buildinparallel-task-parameter"></a>BuildInParallel 작업 매개 변수

`BuildInParallel`은 MSBuild 작업에 대한 선택적 부울 매개 변수입니다. `BuildInParallel`을 `true`(기본값은 `true`)로 설정하면 가능한 많은 프로젝트를 동시에 빌드하기 위해 여러 작업자 프로세스가 생성됩니다. 이러한 방식이 제대로 작동하려면 `-maxcpucount` 스위치를 1보다 큰 값으로 설정해야 하며 시스템에는 최소한 듀얼 코어나 두 개 이상의 프로세서가 있어야 합니다.

다음은 `BuildInParallel` 매개 변수를 설정하는 방법에 대한 *microsoft.common.targets*의 예제입니다.

```xml
<PropertyGroup>
    <BuildInParallel Condition="'$(BuildInParallel)' ==
        ''">true</BuildInParallel>
</PropertyGroup>
<MSBuild
    Projects="@(_MSBuildProjectReferenceExistent)"
    Targets="GetTargetPath"
    BuildInParallel="$(BuildInParallel)"
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);
        %(_MSBuildProjectReferenceExistent.SetPlatform)"
    Condition="'@(NonVCProjectReference)'!='' and
        ('$(BuildingSolutionFile)' == 'true' or
        '$(BuildingInsideVisualStudio)' == 'true' or
        '$(BuildProjectReferences)' != 'true') and
        '@(_MSBuildProjectReferenceExistent)' != ''"
    ContinueOnError="!$(BuildingProject)">
    <Output TaskParameter="TargetOutputs"
        ItemName="_ResolvedProjectReferencePaths"/>
</MSBuild>
```

## <a name="see-also"></a>참조

- [다중 프로세서를 사용하여 프로젝트 빌드](../msbuild/using-multiple-processors-to-build-projects.md)
- [다중 프로세서 인식 로거 작성](../msbuild/writing-multi-processor-aware-loggers.md)
- [C++ 빌드 병렬 처리 블로그](https://devblogs.microsoft.com/visualstudio/tuning-c-build-parallelism-in-vs2010/)
