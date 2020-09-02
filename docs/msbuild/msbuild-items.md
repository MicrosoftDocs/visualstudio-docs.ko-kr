---
title: MSBuild 항목 | Microsoft Docs
description: ItemGroup의 MSBuild Include 특성을 사용하여 빌드에 포함할 파일 지정
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 020983182706bd6d9382f4d0bd4885ffa0f86f52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247587"
---
# <a name="msbuild-items"></a>MSBuild 항목

MSBuild 항목은 빌드 시스템에 대한 입력이며, 일반적으로 파일을 나타냅니다(파일은 `Include` 특성에 지정됨). 항목은 해당 요소 이름에 따라 항목 종류로 그룹화됩니다. 항목 종류는 작업의 매개 변수로 사용할 수 있는 명명된 항목 목록입니다. 작업은 항목 값을 사용하여 빌드 프로세스의 단계를 수행합니다.

 항목은 속하는 항목 종류를 기준으로 이름이 지정되므로 "항목"과 "항목 값"이라는 용어는 동일한 의미로 사용할 수 있습니다.

## <a name="create-items-in-a-project-file"></a>프로젝트 파일에 항목 만들기

 프로젝트 파일에서 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 요소의 자식 요소로 항목을 선언합니다. 자식 요소의 이름은 항목의 종류입니다. 요소의 `Include` 특성은 해당 항목 종류에 포함할 항목(파일)을 지정합니다. 예를 들어 다음 XML은 두 개의 파일을 포함하는 `Compile`이라는 항목 종류를 만듭니다.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 *file2.cs* 항목이 *file1.cs* 항목으로 바뀌지는 않으며, 대신 `Compile` 항목 종류의 값 목록에 파일 이름이 추가됩니다.

 다음 XML은 `Include` 특성 하나에서 두 파일을 모두 선언하여 같은 항목 종류를 만듭니다. 파일 이름은 세미콜론으로 구분됩니다.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

`Include` 특성은 프로젝트 파일의 폴더 $(MSBuildProjectPath)를 기준으로 해석되는 경로이며, 항목이 *.targets* 파일과 같은 가져온 파일에 있는 경우도 마찬가지입니다.

## <a name="create-items-during-execution"></a>실행 중에 항목 만들기

 [Target](../msbuild/target-element-msbuild.md) 요소 외부에 있는 항목의 경우 빌드의 평가 단계에서 값이 할당됩니다. 후속 실행 단계 중에 다음과 같은 방식으로 항목을 만들거나 수정할 수 있습니다.

- 모든 작업이 항목을 내보낼 수 있습니다. 항목을 내보내려면 [Task](../msbuild/task-element-msbuild.md) 요소에 `ItemName` 특성이 포함된 자식 [Output](../msbuild/output-element-msbuild.md) 요소가 있어야 합니다.

- [CreateItem](../msbuild/createitem-task.md) 작업이 항목을 내보낼 수 있습니다. 이러한 사용법은 더 이상 사용되지 않습니다.

- .NET Framework 3.5부터는 `Target` 요소가 항목 요소가 들어 있을 수 있는 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 요소를 포함할 수 있습니다.

## <a name="reference-items-in-a-project-file"></a>프로젝트 파일의 항목 참조

 프로젝트 파일 전체에서 항목 종류를 참조하려면 (\<ItemType>) 구문을 사용합니다. 예를 들어 `@(Compile)`을 사용하여 이전 예제의 항목 종류를 참조합니다. 이 구문을 사용하면 항목 종류를 작업의 매개 변수로 지정하여 해당 작업에 항목을 전달할 수 있습니다. 자세한 내용은 [방법: 빌드할 파일 선택](../msbuild/how-to-select-the-files-to-build.md)을 참조하세요.

 기본적으로 항목 종류를 확장하면 해당 항목이 세미콜론(;)으로 구분됩니다. @(\<ItemType>, '\<separator>') 구문을 사용하면 기본값이 아닌 구분 기호를 지정할 수 있습니다. 자세한 내용은 [방법: 항목 목록을 쉼표로 구분하여 표시](../msbuild/how-to-display-an-item-list-separated-with-commas.md)를 참조하세요.

## <a name="use-wildcards-to-specify-items"></a>와일드카드를 사용하여 항목 지정

`**`, `*` 및 `?` 와일드카드 문자를 사용하여 각 파일을 개별적으로 나열하는 대신 파일 그룹을 빌드의 입력으로 지정할 수 있습니다.

- `?` 와일드카드 문자는 단일 문자를 찾습니다.
- `*` 와일드카드 문자는 0개 이상의 문자를 찾습니다.
- `**` 와일드카드 문자 시퀀스는 부분 경로를 찾습니다.

예를 들어 프로젝트 파일에서 다음 요소를 사용하여 프로젝트 파일이 포함된 디렉터리의 모든 `.cs` 파일을 지정할 수 있습니다.

```xml
<CSFile Include="*.cs"/>
```

다음 요소는 `D:` 드라이브에 있는 모든 `.vb` 파일을 선택합니다.

```xml
<VBFile Include="D:/**/*.vb"/>
```

와일드카드 확장 없이 항목에 리터럴 `*` 또는 `?` 문자를 포함하려면 [와일드카드 문자를 이스케이프](../msbuild/how-to-escape-special-characters-in-msbuild.md)해야 합니다.

와일드카드 문자에 대한 자세한 내용은 [방법: 빌드할 파일 선택](../msbuild/how-to-select-the-files-to-build.md)을 참조하세요.

## <a name="use-the-exclude-attribute"></a>Exclude 특성 사용

 Item 요소는 `Exclude` 특성을 포함할 수 있습니다. 이 특성은 항목 종류에서 특정 항목(파일)을 제외합니다. `Exclude` 특성은 일반적으로 와일드카드 문자와 함께 사용됩니다. 예를 들어 다음 XML은 *DoNotBuild.cs* 파일을 제외한 디렉터리의 모든 *.cs* 파일을 CSFile 항목 종류에 추가합니다.

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 `Exclude` 특성은 `Include` 특성에 의해 추가된 항목에만 영향을 줍니다(이 두 특성이 모두 포함된 항목 요소에서). 다음 예제에서는 이전 항목 요소에서 추가된 *Form1.cs* 파일을 제외하지 않습니다.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 자세한 내용은 [방법: 빌드에서 파일 제외](../msbuild/how-to-exclude-files-from-the-build.md)를 참조하세요.

## <a name="item-metadata"></a>항목 메타데이터

 항목은 `Include` 및 `Exclude` 특성의 정보 이외에 메타데이터를 포함할 수 있습니다. 이 메타데이터는 항목에 대한 추가 정보를 필요로 하는 작업이나 일괄 처리 작업 및 대상에 사용할 수 있습니다. 자세한 내용은 [일괄 처리](../msbuild/msbuild-batching.md)를 참조하세요.

 메타데이터는 프로젝트 파일에서 항목 요소의 자식 요소로 선언된 키/값 쌍의 컬렉션입니다. 자식 요소의 이름은 메타데이터의 이름이고 자식 요소의 값은 메타데이터의 값입니다.

 메타데이터는 포함되어 있는 항목 요소와 연결됩니다. 예를 들어 다음 XML은 값 `Fr`이 포함된 `Culture` 메타데이터를 CSFile 항목 종류의 *one.cs* 및 *two.cs* 항목에 모두 추가합니다.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 항목은 메타데이터 값을 포함하지 않을 수도 있고 하나 이상 포함할 수도 있습니다. 언제든지 메타데이터 값을 변경할 수 있습니다. 메타데이터를 빈 값으로 설정하면 실제로는 빌드에서 메타데이터가 제거됩니다.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> 프로젝트 파일에서 항목 메타데이터 참조

 프로젝트 파일 전체에서 %(\<ItemMetadataName>) 구문을 사용하여 항목형 메타데이터를 참조할 수 있습니다. 메타데이터가 명확하지 않은 경우에는 항목 종류의 이름을 사용하여 참조를 한정할 수 있습니다. 예를 들어 %(\<ItemType.ItemMetaDataName>)을 지정할 수 있습니다. 다음 예제에서는 표시 메타데이터를 사용하여 메시지 작업을 일괄 처리합니다. 일괄 처리에 항목 메타데이터를 사용하는 방법에 대한 자세한 내용은 [작업 일괄 처리의 항목 메타데이터](../msbuild/item-metadata-in-task-batching.md)를 참조하세요.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Stuff Include="One.cs" >
            <Display>false</Display>
        </Stuff>
        <Stuff Include="Two.cs">
            <Display>true</Display>
        </Stuff>
    </ItemGroup>
    <Target Name="Batching">
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>
    </Target>
</Project>
```

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> 잘 알려진 항목 메타데이터

 항목 종류에 항목을 추가하면 해당 항목에는 몇 가지 잘 알려진 메타데이터가 할당됩니다. 예를 들어 모든 항목에는 잘 알려진 메타데이터 %(\<Filename>)이 포함되며, 이 메타데이터의 값은 항목의 파일 이름(확장명 없음)입니다. 자세한 내용은 [잘 알려진 항목 메타데이터](../msbuild/msbuild-well-known-item-metadata.md)를 참조하세요.

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> 메타데이터를 사용하여 항목 종류 변환

 메타데이터를 사용하여 항목 목록을 새 항목 목록으로 변환할 수 있습니다. 예를 들어 `@(CppFiles -> '%(Filename).obj')` 식을 사용하여 *.cpp* 파일을 나타내는 항목이 포함된 항목 종류 `CppFiles`를 해당하는 *.obj* 파일 목록으로 변환할 수 있습니다.

 다음 코드는 `Culture` 메타데이터가 있는 모든 `EmbeddedResource` 항목의 복사본이 포함된 `CultureResource` 항목 종류를 만듭니다. `Culture` 메타데이터 값이 새 메타데이터 `CultureResource.TargetDirectory`의 값이 됩니다.

```xml
<Target Name="ProcessCultureResources">
    <ItemGroup>
        <CultureResource Include="@(EmbeddedResource)"
            Condition="'%(EmbeddedResource.Culture)' != ''">
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>
        </CultureResource>
    </ItemGroup>
</Target>
```

 자세한 내용은 [변환](../msbuild/msbuild-transforms.md)을 참조하세요.

## <a name="item-definitions"></a>항목 정의

 .NET Framework 3.5부터는 [ItemDefinitionGroup 요소](../msbuild/itemdefinitiongroup-element-msbuild.md)를 사용하여 모든 항목 종류에 기본 메타데이터를 추가할 수 있습니다. 잘 알려진 메타데이터와 마찬가지로 기본 메타데이터는 지정한 항목 종류의 모든 항목과 연결됩니다. 항목 정의에서 기본 메타데이터를 명시적으로 재정의할 수 있습니다. 예를 들어 다음 XML은 `Compile` 항목 *one.cs* 및 *three.cs*에 값이 "Monday"인 메타데이터 `BuildDay`를 제공합니다. 이 코드는 *two.cs* 항목에는 값이 "Tuesday"인 메타데이터 `BuildDay`를 제공합니다.

```xml
<ItemDefinitionGroup>
    <Compile>
        <BuildDay>Monday</BuildDay>
    </Compile>
</ItemDefinitionGroup>
<ItemGroup>
    <Compile Include="one.cs;three.cs" />
    <Compile Include="two.cs">
        <BuildDay>Tuesday</BuildDay>
    </Compile>
</ItemGroup>
```

 자세한 내용은 [항목 정의](../msbuild/item-definitions.md)를 참조하세요.

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>대상의 ItemGroup에 있는 항목에 대한 특성

 .NET Framework 3.5부터는 `Target` 요소가 항목 요소가 들어 있을 수 있는 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 요소를 포함할 수 있습니다. 이 섹션의 특성은 `Target`에 있는 `ItemGroup`에서 항목에 대해 지정되는 경우 유효합니다.

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> 특성 제거

 `Remove` 특성은 항목 종류에서 특정 항목(파일)을 제거합니다. 이 특성은 .NET Framework 3.5에서 도입되었습니다(내부 대상만). MSBuild 15.0부터 내부 및 외부 대상이 모두 지원됩니다.

 다음 예제에서는 컴파일 항목 종류에서 모든 *.config* 파일을 제거합니다.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata 특성

 대상 내에서 항목이 생성되는 경우 항목 요소는 `KeepMetadata` 특성을 포함할 수 있습니다. 이 특성을 지정하면 세미콜론으로 구분된 이름 목록에 지정되어 있는 메타데이터만 소스 항목에서 대상 항목으로 전송됩니다. 이 특성에 빈 값을 지정하는 것은 특성을 지정하지 않는 것과 같습니다. `KeepMetadata` 특성은 .NET Framework 4.5에서 도입되었습니다.

 다음 예제에서는 `KeepMetadata` 특성을 사용하는 방법을 보여 줍니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0">

    <ItemGroup>
        <FirstItem Include="rhinoceros">
            <Class>mammal</Class>
            <Size>large</Size>
        </FirstItem>

    </ItemGroup>
    <Target Name="MyTarget">
        <ItemGroup>
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />
        </ItemGroup>

        <Message Text="FirstItem: %(FirstItem.Identity)" />
        <Message Text="  Class: %(FirstItem.Class)" />
        <Message Text="  Size:  %(FirstItem.Size)"  />

        <Message Text="SecondItem: %(SecondItem.Identity)" />
        <Message Text="  Class: %(SecondItem.Class)" />
        <Message Text="  Size:  %(SecondItem.Size)"  />
    </Target>
</Project>

<!--
Output:
  FirstItem: rhinoceros
    Class: mammal
    Size:  large
  SecondItem: rhinoceros
    Class: mammal
    Size:
-->
```

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> RemoveMetadata 특성

 대상 내에서 항목이 생성되는 경우 항목 요소는 `RemoveMetadata` 특성을 포함할 수 있습니다. 이 특성을 지정하면 이름이 세미콜론으로 구분된 이름 목록에 포함되어 있는 메타데이터를 제외한 모든 메타데이터가 소스 항목에서 대상 항목으로 전송됩니다. 이 특성에 빈 값을 지정하는 것은 특성을 지정하지 않는 것과 같습니다. `RemoveMetadata` 특성은 .NET Framework 4.5에서 도입되었습니다.

 다음 예제에서는 `RemoveMetadata` 특성을 사용하는 방법을 보여 줍니다.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <MetadataToRemove>Size;Material</MetadataToRemove>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)" />
        <Message Text="  Size:     %(Item1.Size)" />
        <Message Text="  Color:    %(Item1.Color)" />
        <Message Text="  Material: %(Item1.Material)" />
        <Message Text="Item2: %(Item2.Identity)" />
        <Message Text="  Size:     %(Item2.Size)" />
        <Message Text="  Color:    %(Item2.Color)" />
        <Message Text="  Material: %(Item2.Material)" />
    </Target>
</Project>

<!--
Output:
  Item1: stapler
    Size:     medium
    Color:    black
    Material: plastic
  Item2: stapler
    Size:
    Color:    black
    Material:
-->
```

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> KeepDuplicates 특성

 대상 내에서 항목이 생성되는 경우 항목 요소는 `KeepDuplicates` 특성을 포함할 수 있습니다. `KeepDuplicates`는 항목이 기존 항목의 정확한 복제본인 경우 대상 그룹에 해당 항목을 추가할지를 지정하는 `Boolean` 특성입니다.

 소스 항목과 대상 항목의 Include 값은 같고 메타데이터는 다르면 `KeepDuplicates`가 `false`로 설정되어 있어도 항목이 추가됩니다. 이 특성에 빈 값을 지정하는 것은 특성을 지정하지 않는 것과 같습니다. `KeepDuplicates` 특성은 .NET Framework 4.5에서 도입되었습니다.

 다음 예제에서는 `KeepDuplicates` 특성을 사용하는 방법을 보여 줍니다.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Item1 Include="hourglass;boomerang" />
        <Item2 Include="hourglass;boomerang" />
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item1 Include="hourglass" KeepDuplicates="false" />
            <Item2 Include="hourglass" />
        </ItemGroup>

        <Message Text="Item1: @(Item1)" />
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />
        <Message Text="Item2: @(Item2)" />
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />
    </Target>
</Project>

<!--
Output:
  Item1: hourglass;boomerang
    hourglass  Count: 1
    boomerang  Count: 1
  Item2: hourglass;boomerang;hourglass
    hourglass  Count: 2
    boomerang  Count: 1
-->
```

## <a name="updating-metadata-on-items-in-an-itemgroup-outside-of-a-target"></a>대상 외부에 있는 ItemGroup의 항목에서 메타데이터 업데이트

대상 외부의 항목에서는 `Update` 특성을 통해 기존 메타데이터를 업데이트할 수 있습니다. 이 특성은 대상 아래의 항목에 사용할 수 **없습니다**.

```xml
<Project>
    <PropertyGroup>
        <MetadataToUpdate>pencil</MetadataToUpdate>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Color>red</Color>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="notebook">
            <Size>SMALL</Size>
            <Color>YELLOW</Color>
        </Item2>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="$(MetadataToUpdate);stapler;er*r;@(Item2)" Price="10" Material="">
            <Color>RED</Color>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: RED
    Material:
    Price: 10
Item1: pencil
    Size: small
    Color: RED
    Material:
    Price: 10
Item1: eraser
    Size:
    Color: RED
    Material:
    Price: 10
Item1: notebook
    Size: large
    Color: RED
    Material:
    Price: 10
-->
```

:::moniker range=">=vs-2019"
MSBuild 버전 16.6 이상에서는 `Update` 특성이 정규화된 메타데이터 참조를 지원하므로 둘 이상의 항목에서 메타데이터를 가져올 수 있습니다.

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item3 Include="notebook">
            <Size>SMALL</Size>
            <Color>BLUE</Color>
            <Price>20</Price>
        </Item3>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="@(Item2);er*r;@(Item3)" Size="%(Size)" Color="%(Item2.Color)" Price="%(Item3.Price)" Model="2020">
            <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: black
    Material: plastic
    Price:
    Model:
Item1: pencil
    Size: small
    Color: RED
    Material: Premium PLASTIC
    Price:
    Model: 2020
Item1: eraser
    Size: small
    Color:
    Material: gum
    Price:
    Model: 2020
Item1: notebook
    Size: large
    Color:
    Material: paper
    Price: 20
    Model: 2020
-->
```

설명:
- 정규화되지 않은 메타데이터(%(M))는 업데이트되는 항목 종류(위 예제에서는 `Item1`)에 바인딩됩니다. 정규화된 메타데이터(`%(Item2.Color)`)는 Update 식에서 캡처된 일치 항목 종류의 집합 안에 바인딩됩니다.
- 항목이 여러 참조 항목 내나 사이에서 여러 번 일치하는 경우:
  - 참조된 각 항목 종류에서 마지막 항목이 캡처됩니다(따라서 항목 종류당 캡처되는 항목 1개).
  - 이는 대상 아래에서 작업 항목 일괄 처리의 동작과 일치합니다.
- %() 참조를 넣을 수 있는 경우:
  - 메타데이터
  - 메타데이터 조건
- 메타데이터 이름 일치는 대/소문자를 구분하지 않습니다.
:::moniker-end

## <a name="updating-metadata-on-items-in-an-itemgroup-of-a-target"></a>대상의 ItemGroup에 있는 항목에서 메타데이터 업데이트

메타데이터는 `Update`보다 덜 명료한 구문을 통해 대상 내에서도 수정할 수 있습니다.

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item2 Include="ruler">
            <Color>GREEN</Color>
        </Item2>

    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <!-- Metadata can be expressed either as attributes or as elements -->
            <Item1 Size="GIGANTIC" Color="%(Item2.Color)">
                <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
            </Item1>
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: pencil
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: eraser
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: notebook
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
-->
```

## <a name="see-also"></a>참조

- [Item 요소(MSBuild)](../msbuild/item-element-msbuild.md)
- [일반적인 MSBuild 프로젝트 항목](../msbuild/common-msbuild-project-items.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [방법: 빌드할 파일 선택](../msbuild/how-to-select-the-files-to-build.md)
- [방법: 빌드에서 파일 제외](../msbuild/how-to-exclude-files-from-the-build.md)
- [방법: 항목 목록을 쉼표로 구분하여 표시](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [항목 정의](../msbuild/item-definitions.md)
- [일괄 처리](../msbuild/msbuild-batching.md)
