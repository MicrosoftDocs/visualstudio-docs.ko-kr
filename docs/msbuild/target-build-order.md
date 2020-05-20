---
title: 대상 빌드 순서 | Microsoft Docs
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 607584b4b41bdfde224bdb35d30eec1c6c8a4197
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585459"
---
# <a name="target-build-order"></a>대상 빌드 순서

단일 대상에 대한 입력이 다른 대상의 출력을 사용하는 경우에는 대상의 순서를 지정해야 합니다. 다음과 같은 특성을 사용하여 대상이 실행되는 순서를 지정할 수 있습니다.

- `InitialTargets`입니다. 이 `Project` 특성은 대상이 명령줄 또는 `DefaultTargets` 특성에 지정되어 있더라도 처음으로 실행할 대상을 지정합니다.

- `DefaultTargets`입니다. 이 `Project` 특성은 대상이 명령줄에 명시적으로 지정되어 있지 않은 경우 실행할 대상을 지정합니다.

- `DependsOnTargets`입니다. 이 `Target` 특성은 이 대상을 실행하려면 먼저 실행해야 하는 대상을 지정합니다.

- `BeforeTargets` 및 `AfterTargets` 이러한 `Target` 특성은 지정된 대상 전이나 후에 이 대상을 실행해야 하도록 지정합니다(MSBuild 4.0).

대상은 빌드의 후속 대상이 종속되더라도 빌드 중에 두 번 실행되지 않습니다. 대상이 실행되고 나면 빌드 내에서 해당 대상의 역할은 완료됩니다.

대상은 `Condition` 특성을 포함할 수 있습니다. 지정된 조건이 `false`로 평가되면 대상은 실행되지 않으며 빌드에 영향을 주지 않습니다. 조건에 대한 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.

## <a name="initial-targets"></a>초기 대상

[Project](../msbuild/project-element-msbuild.md) 요소의 `InitialTargets` 특성은 대상이 명령줄 또는 `DefaultTargets` 특성에 지정되어 있더라도 처음으로 실행할 대상을 지정합니다. 초기 대상은 대개 오류 검사용으로 사용됩니다.

`InitialTargets` 특성의 값은 세미콜론으로 구분되어 순서가 지정된 대상 목록일 수 있습니다. 다음 예제에서는 `Warm` 대상이 실행된 후에 `Eject` 대상이 실행됨을 지정합니다.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

가져온 프로젝트의 경우 자체 `InitialTargets` 특성이 있을 수 있습니다. 모든 초기 대상은 함께 집계되어 순서대로 실행됩니다.

자세한 내용은 [방법: 먼저 빌드할 대상 지정](../msbuild/how-to-specify-which-target-to-build-first.md)을 참조하세요.

## <a name="default-targets"></a>기본 대상

[Project](../msbuild/project-element-msbuild.md) 요소의 `DefaultTargets` 특성은 대상이 명령줄에 명시적으로 지정되어 있지 않은 경우 빌드할 하나 이상의 대상을 지정합니다.

`DefaultTargets` 특성의 값은 세미콜론으로 구분되어 순서가 지정된 기본 대상 목록일 수 있습니다. 다음 예제에서는 `Clean` 대상이 실행된 후에 `Build` 대상이 실행됨을 지정합니다.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

명령줄에서 **-target** 스위치를 사용하여 기본 대상을 재정의할 수 있습니다. 다음 예제에서는 `Build` 대상이 실행된 후에 `Report` 대상이 실행됨을 지정합니다. 이 방식으로 대상을 지정하면 기본 대상은 무시됩니다.

 `msbuild -target:Build;Report`

초기 대상과 기본 대상을 모두 지정하고 명령줄 대상은 지정하지 않는 경우 MSBuild는 초기 대상을 먼저 실행한 후에 기본 대상을 실행합니다.

가져온 프로젝트의 경우 자체 `DefaultTargets` 특성이 있을 수 있습니다. 처음으로 나오는 `DefaultTargets` 특성에 따라 실행될 기본 대상이 결정됩니다.

자세한 내용은 [방법: 먼저 빌드할 대상 지정](../msbuild/how-to-specify-which-target-to-build-first.md)을 참조하세요.

## <a name="first-target"></a>첫 번째 대상

초기 대상, 기본 대상 또는 명령줄 대상이 없으면 MSBuild는 프로젝트 파일이나 가져온 프로젝트 파일에서 처음으로 나오는 대상을 실행합니다.

## <a name="target-dependencies"></a>대상 종속성

대상은 상호 간의 종속 관계를 설명할 수 있습니다. `DependsOnTargets` 특성은 대상이 다른 대상에 종속됨을 나타냅니다. 예를 들면 다음과 같습니다.

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

위의 코드는 `Serve` 대상이 `Chop` 대상과 `Cook` 대상에 종속됨을 지시합니다. MSBuild는 `Chop` 대상, `Cook` 대상, `Serve` 대상을 순서대로 실행합니다.

## <a name="beforetargets-and-aftertargets"></a>BeforeTargets 및 AfterTargets

MSBuild 4.0에서는 `BeforeTargets` 및 `AfterTargets` 특성을 사용하여 대상 순서를 지정할 수 있습니다.

다음 스크립트를 살펴보세요.

```xml
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Compile">
        <Message Text="Compiling" />
    </Target>
    <Target Name="Link">
        <Message Text="Linking" />
    </Target>
</Project>
```

`Compile` 대상이 실행된 이후 `Link` 대상이 실행되기 전에 실행되는 중간 대상 `Optimize`를 만들려면 `Project` 요소의 아무 위치에나 다음 대상을 추가합니다.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>대상 빌드 순서 결정

MSBuild는 다음처럼 대상 빌드 순서를 결정합니다.

1. `InitialTargets` 대상이 실행됩니다.

2. **-target** 스위치를 통해 명령줄에 지정된 대상이 실행됩니다. 명령줄에서 대상을 지정하지 않으면 `DefaultTargets` 대상이 실행됩니다. 이 두 대상이 모두 없으면 처음으로 나오는 대상이 실행됩니다.

3. 대상의 `Condition` 특성을 평가합니다. `Condition` 특성이 있고 `false`로 평가되는 경우 대상은 실행되지 않으며 빌드에 영향을 주지 않습니다.

   `BeforeTargets` 또는 `AfterTargets`에 조건부 대상을 나열하는 다른 대상은 여전히 지정된 순서대로 실행됩니다.

4. 대상이 실행되거나 건너뛰기 전에 `Condition` 특성이 대상에 적용되고 `false`로 평가되지 않는 한 해당 `DependsOnTargets` 대상이 실행됩니다.

   > [!NOTE]
   > 대상이 출력 항목을 최신 상태로 유지하기 때문에 실행되지 않으면 건너뛴 것으로 간주됩니다([증분 빌드](../msbuild/incremental-builds.md) 참조). 이 검사는 대상 내의 작업을 실행하기 직전에 수행되며, 대상 실행 순서에 영향을 주지 않습니다.

5. 대상을 실행하거나 건너뛰기 전에 `BeforeTargets` 특성에 대상을 나열하는 다른 대상이 실행됩니다.

6. 대상이 실행되기 전에 `Inputs` 특성과 `Outputs` 특성을 비교합니다. MSBuild는 해당하는 하나 이상의 입력 파일과 관련하여 출력 파일이 오래된 것으로 확인되면 대상을 실행합니다. 그렇지 않으면 MSBuild는 대상을 건너뜁니다.

7. 대상을 실행하거나 건너뛴 후에는 `AfterTargets` 특성에 나열하는 다른 대상이 실행됩니다.

## <a name="see-also"></a>참고 항목

- [대상](../msbuild/msbuild-targets.md)
