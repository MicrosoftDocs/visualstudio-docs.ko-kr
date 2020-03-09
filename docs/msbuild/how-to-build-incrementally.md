---
title: '방법: 증분 방식으로 빌드 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4911bb131f5c5c878b82865b3dee61fd7bedbe1
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634164"
---
# <a name="how-to-build-incrementally"></a>방법: 증분 방식으로 빌드

큰 프로젝트를 빌드할 경우 최신 상태에 있는 이전에 빌드된 구성 요소를 다시 빌드하지 않는 것이 중요합니다. 매번 모든 대상이 빌드되면 각 빌드를 완료하는 데 시간이 오래 걸릴 수 있습니다. 증분 빌드(이전에 빌드되지 않은 대상만 또는 오래된 대상이 다시 빌드되는 빌드)를 사용하도록 설정하기 위해 Microsoft Build Engine(MSBuild)에서는 입력 파일의 타임스탬프를 출력 파일의 타임스탬프와 비교하고 대상을 건너뛰거나, 빌드하거나, 부분적으로 다시 빌드할지 결정할 수 있습니다. 하지만 입력과 출력 간에는 일대일 매핑이 있어야 합니다. 변환을 사용하여 대상이 이 직접 매핑을 식별하도록 할 수 있습니다. 변환에 대한 자세한 내용은 [변환](../msbuild/msbuild-transforms.md)을 참조하세요.

## <a name="specify-inputs-and-outputs"></a>입력 및 출력 지정

프로젝트 파일에 입력 및 출력이 지정된 경우 대상으로 증분식으로 빌드할 수 있습니다.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>대상에 대한 입력 및 출력을 지정하려면

- `Target` 요소의 `Inputs` 및 `Outputs` 특성을 사용합니다. 예를 들어:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild는 입력 파일의 타임스탬프를 출력 파일의 타임스탬프와 비교하고 대상을 건너뛰거나, 빌드하거나, 부분적으로 다시 빌드할지 결정할 수 있습니다. 다음 예제에서 `@(CSFile)` 항목 목록의 파일이 *hello.exe* 파일보다 최신 파일인 경우 MSBuild에서는 대상을 실행합니다. 그렇지 않으면 대상을 건너뜁니다.

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

대상에 입력 및 출력이 지정된 경우 각 출력은 하나의 입력에만 매핑될 수 있습니다. 그렇지 않으면 출력과 입력 간에 직접 매핑이 없을 수 있습니다. 예를 들어 이전 [Csc 작업](../msbuild/csc-task.md)에서 출력 *hello.exe*는 단일 입력에 매핑될 수 없습니다. 이 출력은 모든 입력을 사용합니다.

> [!NOTE]
> 입력과 출력 간에 직접 매핑이 없는 대상은 항상 각 출력이 하나의 입력에만 매핑될 수 있는 대상보다 더 자주 빌드됩니다. 이는 MSBuild에서는 일부 입력이 변경된 경우 다시 빌드해야 하는 출력을 결정할 수 없기 때문입니다.

출력과 입력 간에 직접 매핑을 식별할 수 있는 작업(예: [LC 작업](../msbuild/lc-task.md))은 많은 입력에서 하나의 출력 어셈블리를 생성하는 [Csc](../msbuild/csc-task.md) 및 [Vbc](../msbuild/vbc-task.md)와 같은 작업과 달리 증분 빌드에 가장 적합합니다.

## <a name="example"></a>예제

다음 예제에서는 가상 도움말 시스템에 대한 도움말 파일을 빌드하는 프로젝트를 사용합니다. 프로젝트는 소스 *.txt* 파일을 중간 *.content* 파일로 변환하는 방식으로 작동합니다. .content 파일은 이후 XML 메타데이터와 결합되어 도움말 시스템에서 사용되는 최종 *.help* 파일을 생성합니다. 프로젝트는 다음 가상 작업을 사용합니다.

- `GenerateContentFiles`: *.txt* 파일을 *.content* 파일로 변환합니다.

- `BuildHelp`: *.content* 파일 및 XML 메타데이터 파일을 결합하여 최종 *.help* 파일을 빌드합니다.

프로젝트는 변환을 사용하여 `GenerateContentFiles` 작업에서 입력과 출력 간의 일대일 매핑을 만듭니다. 자세한 내용은 [변환](../msbuild/msbuild-transforms.md)을 참조하세요. 또한 `Output` 요소는 자동으로 `GenerateContentFiles` 작업의 출력을 `BuildHelp` 작업의 입력으로 사용하도록 설정됩니다.

이 프로젝트 파일에는 `Convert` 및 `Build` 대상이 둘 다 포함됩니다. 각 대상이 증분식으로 빌드될 수 있도록 `GenerateContentFiles` 및 `BuildHelp` 작업은 각각 `Convert` 및 `Build` 대상에 배치됩니다. `Output` 요소를 사용하면 `GenerateContentFiles` 작업의 출력이 `ContentFile` 항목 목록에 배치됩니다. 이 목록에 있는 출력은 `BuildHelp` 작업의 입력으로 사용될 수 있습니다. `Output` 요소를 이 방법으로 사용하면 한 작업의 출력이 다른 작업의 입력으로 자동으로 제공되므로 각 작업에서 개별 항목 또는 항목 목록을 수동으로 나열할 필요가 없습니다.

> [!NOTE]
> `GenerateContentFiles` 대상은 증분식으로 빌드될 수 있지만 대상의 모든 출력은 항상 `BuildHelp` 대상의 입력으로 필요합니다. `Output` 요소를 사용할 경우 MSBuild에서는 한 작업의 모든 출력을 다른 대상의 입력으로 자동으로 제공합니다.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <TXTFile Include="*.txt"/>
        <XMLFiles Include="\metadata\*.xml"/>
    </ItemGroup>

    <Target Name = "Convert"
        Inputs="@(TXTFile)"
        Outputs="@(TXTFile->'%(Filename).content')">

        <GenerateContentFiles
            Sources = "@(TXTFile)">
            <Output TaskParameter = "OutputContentFiles"
                ItemName = "ContentFiles"/>
        </GenerateContentFiles>
    </Target>

    <Target Name = "Build" DependsOnTargets = "Convert"
        Inputs="@(ContentFiles);@(XMLFiles)"
        Outputs="$(MSBuildProjectName).help">

        <BuildHelp
            ContentFiles = "@(ContentFiles)"
            MetadataFiles = "@(XMLFiles)"
            OutputFileName = "$(MSBuildProjectName).help"/>
    </Target>
</Project>
```

## <a name="see-also"></a>참조

- [대상](../msbuild/msbuild-targets.md)
- [Target 요소(MSBuild)](../msbuild/target-element-msbuild.md)
- [변환](../msbuild/msbuild-transforms.md)
- [Csc 작업](../msbuild/csc-task.md)
- [Vbc 작업](../msbuild/vbc-task.md)
