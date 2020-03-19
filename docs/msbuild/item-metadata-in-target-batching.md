---
title: 대상 일괄 처리의 항목 메타데이터 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a5d0c9dec280633d0a39573581c083e6ddd4d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633670"
---
# <a name="item-metadata-in-target-batching"></a>대상 일괄 처리의 항목 메타데이터

MSBuild에는 빌드 대상의 입력 및 출력에 대한 종속성 분석을 수행하는 기능이 있습니다. 대상의 입력 또는 출력이 최신 상태인지를 확인한 경우 대상을 건너뛰고 빌드를 계속합니다. `Target` 요소는 `Inputs` 및 `Outputs` 특성을 사용하여 종속성을 분석하는 동안 검사할 항목을 지정합니다.

대상이 일괄 처리 항목을 사용하는 작업을 입력 또는 출력으로 포함하는 경우 대상의 `Target` 요소는 해당 `Inputs` 또는 `Outputs` 특성에서 일괄 처리를 사용하여 MSBuild가 이미 최신 상태인 항목의 일괄 처리를 건너뛰도록 해야 합니다.

## <a name="batch-targets"></a>일괄 처리 대상

다음 예제에는 `Culture` 항목 메타데이터를 기반으로 하는 두 개의 일괄 처리로 나뉜 `Res`라는 항목 목록이 포함됩니다. 이러한 일괄 처리는 각각 `AL` 작업에 전달됩니다. 여기서는 각 일괄 처리에 대한 출력 어셈블리를 만듭니다. MSBuild는 `Target` 요소의 `Outputs` 특성에서 일괄 처리를 사용하여 대상을 실행하기 전에 개별 일괄 처리 각각이 최신 상태인지 확인할 수 있습니다. 대상 일괄 처리를 사용하지 않고 항목이 실행될 때마다 작업에서 항목의 두 일괄 처리를 실행합니다.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Res Include="Strings.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Strings.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.jp.resources">
            <Culture>jp</Culture>
        </Res>
    </ItemGroup>

    <Target Name="Build"
        Inputs="@(Res)"
        Outputs="%(Culture)\MyApp.resources.dll">

        <AL Resources="@(Res)"
            TargetType="library"
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>참조

- [방법: 증분 방식으로 빌드](../msbuild/how-to-build-incrementally.md)
- [일괄 처리](../msbuild/msbuild-batching.md)
- [Target 요소(MSBuild)](../msbuild/target-element-msbuild.md)
- [작업 일괄 처리의 항목 메타데이터](../msbuild/item-metadata-in-task-batching.md)
