---
title: MSBuild 일괄 처리 | Microsoft Docs
ms.date: 06/09/2020
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d7c72d1da270220144cd5e6167ebecb66462ba9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289276"
---
# <a name="msbuild-batching"></a>MSBuild 일괄 처리

MSBuild는 항목 목록을 항목 메타데이터에 따라 여러 다른 범주 또는 일괄 처리로 나누고 각 일괄 처리를 사용하여 한 번에 하나의 대상 또는 작업을 실행합니다.

## <a name="task-batching"></a>작업 일괄 처리

작업 일괄 처리를 사용하면 항목 목록을 다른 일괄 처리로 나누고 해당 일괄 처리 각각을 별도로 작업에 전달하는 방법을 제공하여 프로젝트 파일을 간소화할 수 있습니다. 즉, 프로젝트 파일은 여러 번 실행될 수 있지만 작업 및 해당 특성을 한 번만 선언해야 합니다.

작업 특성 중 하나에서 `%(ItemMetaDataName)` 표기법을 사용하여 MSBuild가 작업에서 일괄 처리를 수행하도록 지정합니다. 다음 예제에서는 `Example` 항목 목록을 `Color` 항목 메타데이터 값에 기반한 일괄 처리로 분할하고 일괄 처리 각각을 `MyTask` 작업에 개별적으로 전달합니다.

> [!NOTE]
> 작업 특성의 다른 위치에서 항목 목록을 참조하지 않거나 메타데이터 이름이 모호할 수 있는 경우 %(<ItemCollection.ItemMetaDataName>) 표기법을 사용하여 일괄 처리에 사용할 항목 메타데이터 값을 정규화할 수 있습니다.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

특정 일괄 처리 예제는 [작업 일괄 처리의 항목 메타데이터](../msbuild/item-metadata-in-task-batching.md)를 참조하세요.

## <a name="target-batching"></a>대상 일괄 처리

MSBuild는 대상이 실행되기 전에 대상의 입력 및 출력이 최신 상태인지를 확인합니다. 입력 및 출력이 모두 최신 상태인 경우 대상을 건너뜁니다. 대상 내의 작업이 일괄 처리를 사용하는 경우 MSBuild는 항목의 각 일괄 처리에 대한 입력 및 출력이 최신 상태인지를 확인해야 합니다. 그렇지 않으면 대상이 적중될 때마다 실행됩니다.

다음 예제에서는 `%(ItemMetadataName)` 표기법을 사용하는 `Outputs` 특성이 포함된 `Target` 요소를 보여줍니다. MSBuild는 `Example` 항목 목록을 `Color` 항목 메타데이터를 기반으로 하는 일괄 처리로 나누고, 각 일괄 처리에 대한 출력 파일의 타임스탬프를 분석합니다. 일괄 처리의 출력이 최신 상태가 아닌 경우 대상이 실행됩니다. 그렇지 않으면 대상을 건너뜁니다.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

대상 일괄 처리의 또 다른 예제는 [대상 일괄 처리의 항목 메타데이터](../msbuild/item-metadata-in-target-batching.md)를 참조하세요.

## <a name="item-and-property-mutations"></a>항목 및 속성 변경

이 섹션에서는 대상 일괄 처리 또는 작업 일괄 처리를 사용할 때 속성 및/또는 항목 메타데이터 변경의 영향을 이해하는 방법을 설명합니다.

대상 일괄 처리 및 작업 일괄 처리는 서로 다른 MSBuild 작업이므로 각 경우에서 MSBuild가 사용하는 일괄 처리의 형태를 정확하게 이해하는 것이 중요합니다. 일괄 처리 구문 `%(ItemMetadataName)`가 대상의 작업에는 표시되지만 대상의 특성에는 없을 경우 MSBuild가 작업 일괄 처리를 사용합니다. 대상 일괄 처리를 지정하는 유일한 방법은 대상 특성에 대한 일괄 처리 구문(일반적으로 `Outputs` 특성)을 사용하는 것입니다.

대상 일괄 처리와 작업 일괄 처리 모두에서 일괄 처리는 독립적으로 실행하는 것으로 간주될 수 있습니다. 모든 일괄 처리는 속성 및 항목 메타데이터 값의 동일한 초기 상태 복사본으로 시작합니다. 일괄 처리 실행 중 속성 값 변경은 다른 일괄 처리에 표시되지 않습니다. 다음 예제를 참조하세요.

```xml
  <ItemGroup>
    <Thing Include="2" Color="blue" />
    <Thing Include="1" Color="red" />
  </ItemGroup>

  <Target Name="DemoIndependentBatches">
    <ItemGroup>
      <Thing Condition=" '%(Color)' == 'blue' ">
        <Color>red</Color>
        <NeededColorChange>true</NeededColorChange>
      </Thing>
    </ItemGroup>
    <Message Importance="high"
             Text="Things: @(Thing->'%(Identity) is %(Color); needed change=%(NeededColorChange)')"/>
  </Target>
```

출력은 다음과 같습니다.

```output
Target DemoIndependentBatches:
  Things: 2 is red; needed change=true;1 is red; needed change=
```

대상의 `ItemGroup`은 암시적으로 작업이며 `Condition` 특성의 `%(Color)`를 사용하여 작업 일괄 처리가 수행됩니다. 일괄 처리에는 빨간색 및 파란색 두 가지가 있습니다. 속성 `%(NeededColorChange)`는 `%(Color)` 메타데이터가 파란색인 경우에만 설정되며, 이 설정은 파란색 일괄 처리가 실행되었을 때 조건과 일치했던 개별 항목에만 영향을 줍니다. `Message` 작업의 `Text` 특성은 항목 변환 내에서 사용되기 때문에 `%(ItemMetadataName)` 구문에도 불구하고 일괄 처리를 트리거하지 않습니다.

일괄 처리는 독립적으로 실행되지만 병렬로 실행되지는 않습니다. 그러므로 일괄 처리된 실행에서 변경되는 메타데이터 값에 액세스할 때 차이가 있습니다. 일괄 처리된 실행의 일부 메타데이터를 기반으로 속성을 설정하는 경우 속성은 마지막 값 집합을 사용합니다.

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

일괄 처리 실행 후 속성은 `%(MetadataValue)`의 최종 값을 유지합니다.

일괄 처리는 독립적으로 실행되지만 대상 일괄 처리와 작업 일괄 처리의 차이를 고려하여 상황에 적용되는 유형을 파악하는 것이 중요합니다. 이러한 구분의 중요성을 보다 잘 이해하기 위해 다음 예제를 생각해 보겠습니다.

작업은 명시적이 아니라 암시적일 수 있습니다. 그러므로 암시적 작업에서 작업 일괄 처리가 발생할 때 혼동될 수 있습니다. `PropertyGroup` 또는 `ItemGroup` 요소가 `Target`에 표시되는 경우 그룹의 각 속성 선언은 암시적으로 개별 [CreateProperty](createproperty-task.md) 또는 [CreateItem](createitem-task.md) 작업과 유사하게 처리됩니다. 이는 대상이 일괄 처리되는 경우와 일괄 처리되지 않는 경우(즉, `Outputs` 특성에 `%(ItemMetadataName)` 구문이 없음)에 대한 동작이 다르다는 것을 의미합니다. 대상이 일괄 처리되는 경우 `ItemGroup`을 대상마다 한 번씩 실행되지만, 대상이 일괄 처리되지 않는 경우에는 작업 일괄 처리를 사용하여 `CreateItem` 또는 `CreateProperty` 작업의 암시적 해당 항목이 일괄 처리되어 대상이 한 번만 실행되고 그룹의 각 항목 또는 속성이 작업 일괄 처리를 사용하여 개별적으로 일괄 처리됩니다.

다음 예제에서는 메타데이터가 변경되는 경우 대상 일괄 처리와 작업 일괄 처리를 보여 줍니다. 폴더 A 및 B에 일부 파일이 포함되어 있습니다.

```
A\1.stub
B\2.stub
B\3.stub
```

이제 다음 두 유사한 프로젝트의 출력을 살펴봅니다.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build" Outputs="%(StubDirs.Identity)">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

출력은 다음과 같습니다.

```output
Test1:
  >> A\ 'A\' 'A'
Test1:
  >> B\ 'B\' 'B'
```

이제 대상 일괄 처리를 지정하는 `Outputs` 특성을 제거합니다.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

출력은 다음과 같습니다.

```output
Test1:
  >> A\ 'B\' 'B'
  >> B\ 'B\' 'B'
```

재목 `Test1`은 한 번만 출력되지만 앞의 예제에서는 두 번 출력되었습니다. 즉, 대상이 일괄 처리되지 않습니다.  그 결과 출력이 달라 혼동을 초래합니다.

그 이유는 대상 일괄 처리를 사용하는 경우 각 대상 일괄 처리는 모든 속성 및 항목의 독립적인 복사본을 사용하여 대상의 모든 항목을 실행하지만, `Outputs` 특성을 생략하면 속성 그룹의 개별 줄이 잠재적으로 일괄 처리된 개별 작업으로 처리됩니다. 이 경우 `ComponentDir` 작업은 일괄 처리됩니다(`%(ItemMetadataName)` 구문을 사용). 따라서 `ComponentName` 줄이 실행될 때는 `ComponentDir` 줄의 일괄 처리가 모두 완료되고 실행된 두 번째 줄은 두 번째 줄에 표시된 대로 값을 결정한 상태입니다.

## <a name="property-functions-using-metadata"></a>메타데이터를 사용하는 속성 함수

메타데이터를 포함하는 속성 함수에서 일괄 처리를 제어할 수 있습니다. 예를 들면 다음과 같습니다.

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

<xref:System.IO.Path.Combine%2A>를 사용하여 컴파일 항목 경로와 루트 폴더 경로를 결합합니다.

속성 함수는 메타데이터 값 내에 나타나지 않을 수 있습니다. 예를 들면 다음과 같습니다.

`%(Compile.FullPath.Substring(0,3))`

사용할 수 없습니다.

속성 함수에 대한 자세한 내용은 [속성 함수](../msbuild/property-functions.md)를 참조하세요.

## <a name="see-also"></a>참조

- [ItemMetadata 요소(MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [고급 개념](../msbuild/msbuild-advanced-concepts.md)
