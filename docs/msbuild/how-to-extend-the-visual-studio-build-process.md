---
title: 빌드 프로세스 확장
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac3bebc0a64f814e71e7b5ab30282a70fd7eb85e
ms.sourcegitcommit: d293c0e3e9cc71bd4117b6dfd22990d52964addc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "88041040"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>방법: Visual Studio 빌드 프로세스 확장

Visual Studio 빌드 프로세스는 프로젝트 파일로 가져온 일련의 MSBuild *.targets* 파일로 정의됩니다. 이러한 가져온 파일 중 하나인 *Microsoft.Common.targets*는 빌드 프로세스의 여러 지점에서 사용자 지정 작업을 실행할 수 있도록 확장될 수 있습니다. 이 문서에서는 Visual Studio 빌드 프로세스를 확장하는 데 사용할 수 있는 두 가지 방법을 설명합니다.

- 공통 대상(*Microsoft.Common.targets* 또는 가져오는 파일)에 정의된 미리 정의된 특정 대상을 재정의합니다.

- 공통 대상에 정의된 “DependsOn” 속성을 재정의합니다.

## <a name="override-predefined-targets"></a>미리 정의된 대상 재정의

공통 대상은 빌드 프로세스의 일부 주요 대상의 전후에 호출되는 미리 정의된 빈 대상 집합을 포함합니다. 예를 들어 MSBuild는 메인 `CoreBuild` 대상 전에 `BeforeBuild` 대상을 호출하고 `CoreBuild` 대상 후에 `AfterBuild` 대상을 호출합니다. 기본적으로 공통 대상의 빈 대상은 아무것도 수행하지 않지만 공통 대상을 가져오는 프로젝트 파일에서 원하는 대상을 정의하여 해당 기본 동작을 재정의할 수 있습니다. 미리 정의된 대상을 재정의하면 MSBuild 작업을 사용하여 빌드 프로세스를 더 세부적으로 제어할 수 있습니다.

> [!NOTE]
> SDK 스타일 프로젝트에는 *프로젝트 파일의 마지막 줄 뒤*에 대상의 암시적 가져오기가 있습니다. 즉, [방법: MSBuild 프로젝트 SDK 사용](how-to-use-project-sdk.md)의 설명대로 가져오기를 수동으로 지정하지 않는 한 기본 대상을 재정의할 수 없습니다.

#### <a name="to-override-a-predefined-target"></a>미리 정의된 대상을 재정의하려면

1. 재정의하려는 공통 대상에서 미리 정의된 대상을 식별합니다. 안전하게 재정의할 수 있는 대상의 전체 목록은 아래 표를 참조하세요.

2. `</Project>` 태그 바로 앞에, 프로젝트 파일의 끝에 하나 이상의 대상을 정의합니다. 예를 들면 다음과 같습니다.

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. 프로젝트 파일을 빌드합니다.

다음 표는 안전하게 재정의할 수 있는 공통 대상에서 모든 대상을 표시합니다.

|대상 이름|Description|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|이러한 대상 중 하나에 삽입된 작업은 핵심 컴파일이 완료되기 전이나 후에 실행됩니다. 대부분의 사용자 지정은 이러한 두 개의 대상 중 하나에서 수행됩니다.|
|`BeforeBuild`, `AfterBuild`|이러한 대상 중 하나에 삽입된 작업은 빌드의 모든 작업 전이나 후에 실행됩니다. **참고:**`BeforeBuild` 및 `AfterBuild` 대상은 프로젝트 파일 대부분의 끝에 삽입된 주석에서 이미 정의되어 있습니다. 따라서 프로젝트 파일에 빌드 전후 이벤트를 쉽게 추가할 수 있습니다.|
|`BeforeRebuild`, `AfterRebuild`|이러한 대상 중 하나에 삽입된 작업은 핵심 다시 빌드 기능이 호출되기 전 또는 후에 실행됩니다. *Microsoft.Common.targets*에서 대상 실행 순서는 차례로 `BeforeRebuild`, `Clean`, `Build` 및 `AfterRebuild`입니다.|
|`BeforeClean`, `AfterClean`|이러한 대상 중 하나에 삽입된 작업은 핵심 정리 기능이 호출되기 전 또는 후에 실행됩니다.|
|`BeforePublish`, `AfterPublish`|이러한 대상 중 하나에 삽입된 작업은 핵심 게시 기능이 호출되기 전 또는 후에 실행됩니다.|
|`BeforeResolveReferences`, `AfterResolveReferences`|이러한 대상 중 하나에 삽입된 작업은 어셈블리 참조가 확인되기 전이나 후에 실행됩니다.|
|`BeforeResGen`, `AfterResGen`|이러한 대상 중 하나에 삽입된 작업은 어셈블리 리소스가 생성되기 전이나 후에 실행됩니다.|

## <a name="example-aftertargets-and-beforetargets"></a>예: AfterTargets 및 BeforeTargets

다음 예제에서는 `AfterTargets` 특성을 사용하여 출력 파일에 무언가를 수행하는 사용자 지정 대상을 추가하는 방법을 보여 줍니다. 이 경우에는 새 폴더 *CustomOutput*에 출력 파일을 복사합니다.  이 예제에서는 또한, `BeforeTargets` 특성을 사용하고 `CoreClean` 대상보다 먼저 사용자 지정 정리 작업이 실행되도록 지정하여 `CustomClean` 대상이 있는 사용자 지정 빌드 작업을 통해 만들어진 파일을 정리하는 방법도 보여 줍니다.

```xml
<Project Sdk="Microsoft.NET.Sdk">

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
   <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
</PropertyGroup>

<Target Name="CustomAfterBuild" AfterTargets="Build">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> 이전 섹션의 표에 나열된 사전 정의된 대상과 다른 이름을 사용해야 합니다(예: 여기서는 사용자 지정 빌드 대상을 `AfterBuild`가 아니라 `CustomAfterBuild`로 지정함). 사전 정의된 대상이 이 대상을 역시 지정하는 SDK 가져오기에 의해 재정의되기 떄문입니다. 이 대상을 재정의하는 대상 파일의 가져오기는 가시적으로 확인되지 않지만 SDK를 참조하는 `Sdk` 특성 메서드를 사용할 때 프로젝트 파일 끝에 암시적으로 추가됩니다.

## <a name="override-dependson-properties"></a>DependsOn 속성 재정의

미리 정의된 대상 재정의는 빌드 프로세스를 확장하는 쉬운 방법이지만 MSBuild에서 대상의 정의를 순차적으로 평가하므로 프로젝트를 가져오는 다른 프로젝트에서 이미 재정의한 대상을 재정의하는 것을 방지할 방법이 없습니다. 따라서 예를 들어 다른 모든 프로젝트를 가져온 후 프로젝트에서 정의된 마지막 `AfterBuild` 대상은 빌드 중 사용되는 대상이 됩니다.

공통 대상 전체의 `DependsOnTargets` 특성에서 사용되는 DependsOn 속성을 재정의하여 의도하지 않은 대상의 재정의를 방지할 수 있습니다. 예를 들어 `Build` 대상은 `"$(BuildDependsOn)"`의 `DependsOnTargets` 특성 값을 포함합니다. 고려할 사항은 다음과 같습니다.

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

이 XML 조각은 `Build` 대상 전에 실행할 수 있음을 나타내며 `BuildDependsOn` 속성에 지정된 모든 대상은 먼저 실행되어야 합니다. `BuildDependsOn` 속성은 다음으로 정의됩니다.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

프로젝트 파일의 끝에서 `BuildDependsOn`이라는 다른 속성을 선언하여 이 속성 값을 재정의할 수 있습니다. 새 속성에서 이전 `BuildDependsOn` 속성을 포함하여 대상 목록의 시작과 끝에 새 대상을 추가할 수 있습니다. 예를 들면 다음과 같습니다.

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

프로젝트 파일을 가져오는 프로젝트는 만든 사용자 지정 항목을 덮어쓰지 않고 이러한 속성을 재정의할 수 있습니다.

#### <a name="to-override-a-dependson-property"></a>DependsOn 속성을 재정의하려면

1. 재정의하려는 공통 대상에서 미리 정의된 DependsOn 속성을 식별합니다. 일반적으로 재정의된 DependsOn 속성의 목록은 아래 표를 참조하세요.

2. 프로젝트 파일의 끝에서 속성의 다른 인스턴스를 정의합니다. 새 속성에 원래 속성을 포함합니다(예: `$(BuildDependsOn)`).

3. 속성 정의 앞 또는 뒤에 사용자 지정 대상을 정의합니다.

4. 프로젝트 파일을 빌드합니다.

### <a name="commonly-overridden-dependson-properties"></a>일반적으로 재정의된 DependsOn 속성

|속성 이름|Description|
|-------------------|-----------------|
|`BuildDependsOn`|전체 빌드 프로세스 앞이나 뒤에 사용자 지정 대상을 삽입하려는 경우 재정의할 속성입니다.|
|`CleanDependsOn`|사용자 지정 빌드 프로세스에서 출력을 정리하려는 경우 재정의할 속성입니다.|
|`CompileDependsOn`|컴파일 단계 앞이나 뒤에 사용자 지정 프로세스를 삽입하려는 경우 재정의할 속성입니다.|

## <a name="example-builddependson-and-cleandependson"></a>예: BuildDependsOn 및 CleanDependsOn

다음 예제는 `BeforeTargets` 및 `AfterTargets` 예제와 비슷하지만 비슷한 기능을 구현하는 방법을 보여 줍니다. `BuildDependsOn`을 사용해 빌드를 확장하여 빌드 후 출력 파일을 복사하는 고유 작업 `CustomAfterBuild`를 추가할 뿐만 아니라 `CleanDependsOn`을 사용하여 해당하는 `CustomClean` 작업을 추가합니다.  

이 예제에서는 SDK 스타일 프로젝트입니다. 이 문서 앞부분에서 SDK 스타일 프로젝트에 대해 설명한 대로 Visual Studio에서 프로젝트 파일을 생성할 때 사용하는 `Sdk` 특성 대신 수동 가져오기 메서드를 사용해야 합니다.

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

<Target Name="CustomAfterBuild">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

요소의 순서가 중요합니다. `BuildDependsOn` 및 `CleanDependsOn` 요소는 표준 SDK 대상 파일을 가져온 후에 표시되어야 합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio 통합](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [.targets 파일](../msbuild/msbuild-dot-targets-files.md)
