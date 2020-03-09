---
title: Visual Studio 통합(MSBuild)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631200"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio 통합(MSBuild)

Visual Studio는 MSBuild를 호스트하여 관리되는 프로젝트를 로드하고 빌드합니다. MSBuild에서 프로젝트를 관리하므로 프로젝트가 다른 도구에서 빌드되어 사용자 지정된 빌드 프로세스를 가지더라도 MSBuild 형식의 프로젝트는 대부분 Visual Studio에서 사용될 수 있습니다.

 이 문서에서는 Visual Studio의 MSBuild 호스팅 중 Visual Studio에서 로드하고 빌드할 프로젝트와 *.targets* 파일을 사용자 지정할 때 고려해야 하는 부분을 설명합니다. 이를 통해 IntelliSense 및 디버깅 작업과 같은 Visual Studio 기능이 사용자 지정 프로젝트에서 작동하는지 확인할 수 있습니다.

 C++ 프로젝트에 대한 자세한 내용은 [프로젝트 파일](/cpp/build/reference/project-files)을 참조하세요.

## <a name="project-file-name-extensions"></a>프로젝트 파일 이름 확장명

 *MSBuild.exe*에서는 *.\*proj* 패턴과 일치하는 모든 프로젝트 파일 이름 확장명을 인식합니다. 하지만 Visual Studio에서는 프로젝트를 로드할 언어별 프로젝트 시스템을 결정하는 이러한 프로젝트 파일 확장명의 일부만 인식합니다. Visual Studio에는 언어 중립적인 MSBuild 기반 프로젝트 시스템이 없습니다.

 예를 들어, C# 프로젝트 시스템에서는 *.csproj* 파일을 로드하지만 Visual Studio에서는 *.xxproj* 파일을 로드할 수 없습니다. 임의의 언어로 된 소스 파일의 프로젝트 파일은 Visual Studio에 로드되는 Visual Basic 또는 C# 프로젝트 파일과 동일한 확장명을 사용해야 합니다.

## <a name="well-known-target-names"></a>잘 알려진 대상 이름

 Visual Studio에서 **빌드** 명령을 클릭하면 프로젝트의 기본 대상이 실행됩니다. 보통 이 대상을 `Build`라고도 합니다. **다시 빌드** 또는 **정리** 명령을 선택하면 프로젝트에서 같은 이름의 대상이 실행됩니다. **게시** 를 클릭하면 프로젝트에서 `PublishOnly` 라는 대상이 실행됩니다.

## <a name="configurations-and-platforms"></a>구성 및 플랫폼

 구성은 `Condition` 특성을 포함하는 `PropertyGroup` 요소에서 그룹화된 속성으로 MSBuild 프로젝트에 표시됩니다. Visual Studio에서는 표시할 프로젝트 구성과 플랫폼 목록을 만들기 위해 이러한 조건을 확인합니다. 이 목록을 추출하려면 조건의 형식이 다음과 비슷해야 합니다.

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio에서는 이를 위해 `PropertyGroup`, `ItemGroup`, `Import`, 속성 및 항목 요소에서 조건을 확인합니다.

## <a name="additional-build-actions"></a>추가 빌드 작업

 Visual Studio에서는 **파일 속성** 창의 **빌드 작업** 속성을 사용하여 프로젝트에 있는 파일의 항목 형식 이름을 변경할 수 있습니다. **Compile**, **EmbeddedResource**, **Content** 및 **None** 항목 형식 이름은 프로젝트에 이미 있는 다른 모든 항목 형식 이름과 함께 항상 이 메뉴에 표시됩니다. 사용자 지정 항목 형식 이름이 항상 이 메뉴에 표시되도록 하려면 `AvailableItemName`이라는 항목 형식에 해당 이름을 추가하면 됩니다. 예를 들어 프로젝트 파일에 다음을 추가하면 해당 파일을 가져오는 모든 프로젝트에 대해 **JScript** 사용자 지정 형식이 이 메뉴에 추가됩니다.

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> 일부 항목 형식 이름은 Visual Studio에 고유하지만 이 드롭다운에는 나열되어 있지 않습니다.

## <a name="in-process-compilers"></a>In-Process 컴파일러

 가능한 경우 Visual Studio에서는 성능 향상을 위해 in-process 버전의 Visual Basic 컴파일러를 사용하려고 시도합니다. (C#에는 적용되지 않습니다.) 이러한 시도는 다음 조건이 충족되어야 제대로 작동합니다.

- 프로젝트 대상에 Visual Basic 프로젝트에 대한 `Vbc`라는 이름의 작업이 있어야 합니다.

- 작업의 `UseHostCompilerIfAvailable` 매개 변수가 true로 설정되어 있어야 합니다.

## <a name="design-time-intellisense"></a>디자인 타임 IntelliSense

 빌드에서 출력 어셈블리를 생성하기 전에 Visual Studio에서 IntelliSense 지원을 받으려면 다음 조건이 충족되어야 합니다.

- `Compile`이라는 대상이 있어야 합니다.

- `Compile` 대상 또는 해당 종속 대상 중 하나는 프로젝트에 대해 `Csc` 또는 `Vbc`와 같은 컴파일러 작업을 호출해야 합니다.

- `Compile` 대상 또는 해당 종속 대상 중 하나를 통해 컴파일러가 IntelliSense에 필요한 모든 매개 변수, 특히 모든 참조를 받도록 해야 합니다.

- [In-Process 컴파일러](#in-process-compilers) 섹션에 나열된 조건이 충족되어야 합니다.

## <a name="build-solutions"></a>솔루션 빌드

 Visual Studio내에서 솔루션 파일 및 프로젝트 빌드 순서는 Visual Studio 자체에서 제어합니다. 명령줄에서 *msbuild.exe*를 사용하여 솔루션을 빌드할 때 MSBuild에서는 솔루션 파일을 구문 분석하고 프로젝트 빌드 순서를 정합니다. 두 경우 모두 프로젝트는 종속성 순서에 따라 개별적으로 빌드되며 프로젝트 간 참조는 검색되지 않습니다. 이와 대조적으로 *msbuild.exe*를 사용하여 개별 프로젝트를 빌드하면 프로젝트 간 참조가 검색됩니다.

 Visual Studio 내에서 빌드할 때 `$(BuildingInsideVisualStudio)` 속성은 `true`로 설정됩니다. 프로젝트 또는 *.targets* 파일에서 이 속성을 사용하여 빌드가 다르게 동작하도록 할 수 있습니다.

## <a name="display-properties-and-items"></a>속성 및 항목 표시

 Visual Studio에서는 특정 속성 이름과 값을 인식합니다. 예를 들어, 프로젝트의 다음 속성을 사용하면 **Windows 애플리케이션** 이 **프로젝트 디자이너** 의 **애플리케이션 형식**상자에 나타납니다.

```xml
<OutputType>WinExe</OutputType>
```

 속성 값은 **프로젝트 디자이너** 에서 편집할 수 있으며 프로젝트 파일에 저장할 수 있습니다. 이러한 속성을 직접 편집하여 잘못된 값이 지정되면 프로젝트가 로드될 때 Visual Studio에서 경고를 표시하고 잘못된 값을 기본값으로 바꿉니다.

 Visual Studio에서는 일부 속성의 기본값을 기억하고 있습니다. 이러한 속성은 기본값이 아닌 값을 가져야 프로젝트 파일에서 지속됩니다.

 임의의 이름을 갖는 속성은 Visual Studio에 표시되지 않습니다. Visual Studio에서 임의의 속성을 수정하려면 XML 편집기에서 프로젝트 파일을 열고 직접 편집해야 합니다. 자세한 내용은 이 항목의 뒷부분에 있는 [Visual Studio에서 프로젝트 파일 편집](#edit-project-files-in-visual-studio)을 참조하세요.

 임의의 항목 형식 이름을 사용하여 프로젝트에 정의된 항목은 기본적으로 **솔루션 탐색기**에서 해당 프로젝트 노드 아래 표시됩니다. 항목이 표시되지 않도록 하려면 `Visible` 메타데이터를 `false`로 설정합니다. 예를 들어, 다음 항목은 빌드 프로세스에 사용되지만 **솔루션 탐색기**에는 표시되지 않습니다.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> C++ 프로젝트용 **솔루션 탐색기**에서는 `Visible` 메타데이터가 무시됩니다. `Visible`이 false로 설정된 경우에도 항목이 항상 표시됩니다.

 프로젝트로 가져온 파일에 선언한 항목은 기본적으로 표시되지 않습니다. 빌드 프로세스 동안 만들어진 항목은 **솔루션 탐색기**에 표시되지 않습니다.

## <a name="conditions-on-items-and-properties"></a>항목 및 속성에 대한 조건

 빌드하는 동안 모든 조건이 완전히 고려됩니다.

 표시할 속성 값을 결정할 때 Visual Studio에서 구성에 종속적인 속성은 구성에 무관한 속성과 다르게 확인됩니다. 구성에 종속적인 속성인 경우 Visual Studio에서는 `Configuration` 및 `Platform` 속성을 적절하게 설정하고 MSBuild에 프로젝트를 다시 확인하도록 지시합니다. 구성에 무관한 속성인 경우 조건이 확인되는 방법이 확실하지 않습니다.

 항목을 **솔루션 탐색기**에 표시해야 하는지 여부를 결정할 수 있도록 항목에 대한 조건식은 항상 무시됩니다.

## <a name="debugging"></a>디버깅

 출력 어셈블리를 찾아서 시작하고 디버거를 연결하려면 Visual Studio에서 `OutputPath`, `AssemblyName` 및 `OutputType` 속성이 올바르게 정의되어 있어야 합니다. 빌드 프로세스에서 컴파일러를 통해 *.pdb* 파일을 생성하지 않으면 디버거가 연결되지 않습니다.

## <a name="design-time-target-execution"></a>디자인 타임 대상 실행

 Visual Studio에서는 프로젝트를 로드할 때 특정 이름의 대상을 실행하려고 시도합니다. 이러한 대상에는 `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` 및 `CopyRunEnvironmentFiles`가 있습니다. Visual Studio에서는 이러한 대상을 실행하여 컴파일러가 IntelliSense를 제공하도록 초기화되거나, 디버거가 초기화되거나, 솔루션 탐색기에 표시된 참조가 확인될 수 있도록 할 수 있습니다. 이러한 대상이 없어도 프로젝트를 제대로 로드하고 빌드할 수는 있지만 Visual Studio에서 디자인 타임 환경이 완전하게 작동하지 않습니다.

## <a name="edit-project-files-in-visual-studio"></a>Visual Studio에서 프로젝트 파일 편집

 MSBuild 프로젝트를 직접 편집하려면 Visual Studio XML 편집기에서 프로젝트 파일을 열 수 있습니다.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio에서 프로젝트 파일을 언로드 및 편집하려면

1. **솔루션 탐색기**에서 프로젝트의 바로 가기 메뉴를 열고 **프로젝트 언로드**를 선택합니다.

     해당 프로젝트가 **(사용할 수 없음)** 으로 표시됩니다.

2. **솔루션 탐색기**에서 사용할 수 없는 프로젝트의 바로 가기 메뉴를 열고 **편집 \<프로젝트 파일>** 을 선택합니다.

     해당 프로젝트 파일이 Visual Studio XML 편집기에 열립니다.

3. 프로젝트 파일을 편집 및 저장한 후 닫습니다.

4. **솔루션 탐색기**에서 사용할 수 없는 프로젝트의 바로 가기 메뉴를 열고 **프로젝트 다시 로드**를 선택합니다.

## <a name="intellisense-and-validation"></a>IntelliSense 및 유효성 검사

 XML 편집기를 사용하여 프로젝트 파일을 편집할 경우 MSBuild 스키마 파일에서 IntelliSense 및 유효성 검사를 실행합니다. 이러한 스키마 파일은 *\<Visual Studio 설치 디렉터리>\Xml\Schemas\1033\MSBuild*에 있는 스키마 캐시에 설치됩니다.

 핵심 MSBuild 형식은 *Microsoft.Build.Core.xsd*에 정의되고 Visual Studio에서 사용되는 일반 형식은 *Microsoft.Build.CommonTypes.xsd*에 정의됩니다. 사용자 지정 항목 형식 이름, 속성, 작업 등에 대해 IntelliSense 및 유효성 검사를 적용하도록 스키마를 사용자 지정하려면 *Microsoft.Build.xsd*를 편집하거나 CommonTypes 또는 핵심 스키마를 포함하는 스키마를 직접 만들면 됩니다. 스키마를 직접 만들 경우 **속성** 창을 사용하여 해당 스키마를 찾도록 XML 편집기에 지시해야 합니다.

## <a name="edit-loaded-project-files"></a>로드된 프로젝트 파일 편집

 Visual Studio에서는 프로젝트 파일과 프로젝트 파일이 가져온 파일의 내용을 캐시합니다. 로드된 프로젝트 파일을 편집할 경우 Visual Studio에서는 변경 내용이 적용되도록 프로젝트를 다시 로드하라는 메시지를 자동으로 표시합니다. 하지만 로드된 프로젝트에서 가져온 파일을 편집할 경우에는 다시 로드하라는 메시지가 표시되지 않으므로 변경 내용을 적용하려면 수동으로 프로젝트를 언로드한 후 다시 직접 로드해야 합니다.

## <a name="output-groups"></a>출력 그룹

 *Microsoft.Common.targets*에 정의된 몇 가지 대상의 이름은 `OutputGroups` 또는 `OutputGroupDependencies`로 끝납니다. Visual Studio에서는 이러한 대상을 호출하여 특정한 프로젝트 출력 목록을 얻습니다. 예를 들어, `SatelliteDllsProjectOutputGroup` 대상은 빌드에서 만드는 모든 위성 어셈블리 목록을 만듭니다. 이러한 출력 그룹은 게시, 배포 및 프로젝트 간 참조와 같은 기능에서 사용됩니다. 출력 그룹이 정의되지 않은 프로젝트는 Visual Studio에서 로드되고 빌드되지만 일부 기능은 제대로 작동하지 않을 수 있습니다.

## <a name="reference-resolution"></a>참조 확인

 참조 확인은 프로젝트 파일에 저장된 참조 항목을 사용하여 실제 어셈블리를 찾는 과정입니다. Visual Studio에서는 **속성** 창에 각 참조에 대한 자세한 속성을 표시하기 위해 참조 확인을 트리거해야 합니다. 다음 목록에서는 세 가지 참조 형식과 참조 확인 방법을 설명합니다.

- 어셈블리 참조:

   프로젝트 시스템에서 잘 알려진 이름이 `ResolveAssemblyReferences`인 대상을 호출합니다. 이 대상은 항목 형식 이름이 `ReferencePath`인 항목을 출력해야 합니다. 이러한 항목에는 각각 참조에 대한 전체 경로를 포함하는 항목 사양(항목의 `Include` 특성 값)이 있어야 합니다. 항목에는 다음과 같은 새 메타데이터 외에 전달된 입력 항목의 모든 메타데이터가 있어야 합니다.

  - `CopyLocal`: 어셈블리를 출력 폴더로 복사할지 여부를 true 또는 false로 설정하여 나타냅니다.

  - `OriginalItemSpec`: 참조의 원본 항목 사양이 포함되어 있습니다.

  - `ResolvedFrom`: .NET Framework 디렉터리에서 확인된 경우 "{TargetFrameworkDirectory}"로 설정됩니다.

- COM 참조:

   프로젝트 시스템에서 잘 알려진 이름이 `ResolveCOMReferences`인 대상을 호출합니다. 이 대상은 항목 형식 이름이 `ComReferenceWrappers`인 항목을 출력해야 합니다. 이러한 항목에는 각각 COM 참조에 대해 Interop 어셈블리의 전체 경로를 포함하는 항목 사양이 있어야 합니다. 항목에는 전달된 입력 항목의 모든 메타데이터와 함께, 어셈블리를 출력 폴더로 복사할지 여부를 true 또는 false로 설정하여 나타내는 `CopyLocal`이라는 이름의 새 메타데이터가 있어야 합니다.

- 네이티브 참조

   프로젝트 시스템에서 잘 알려진 이름이 `ResolveNativeReferences`인 대상을 호출합니다. 이 대상은 항목 형식 이름이 `NativeReferenceFile`인 항목을 출력해야 합니다. 항목에는 전달된 입력 항목의 모든 메타데이터와 함께, 참조의 원본 항목 사양이 포함되어 있는 `OriginalItemSpec`이라는 새로운 메타데이터 부분이 있어야 합니다.

## <a name="performance-shortcuts"></a>성능 바로 가기

 Visual Studio IDE를 사용하여 디버깅을 시작하거나(F5 키를 선택하거나 메뉴 모음에서 **디버그** > **디버깅 시작** 선택) 프로젝트를 빌드하는 경우(예를 들어 **빌드** > **솔루션 빌드**) 빌드 프로세스는 성능 향상을 위해 빠른 업데이트 검사를 사용합니다. 사용자 지정된 빌드가 이후에 다시 빌드되는 파일을 생성하는 경우, 빠른 업데이트 검사에서 변경된 파일이 올바르게 식별되지 않습니다. 보다 철저한 업데이트 검사가 필요한 프로젝트에서는 환경 변수 `DISABLEFASTUPTODATECHECK=1`을 설정하여 빠른 검사를 해제할 수 있습니다. 또는 프로젝트에서 이 항목을 프로젝트의 또는 프로젝트가 가져오는 파일의 MSBuild 속성으로 설정할 수 있습니다.

 Visual Studio의 일반 빌드에는 빠른 업데이트 검사가 적용되지 않으며, 명령 프롬프트에서 빌드를 호출한 것처럼 프로젝트가 빌드됩니다.

## <a name="see-also"></a>참조

- [방법: Visual Studio 빌드 프로세스 확장](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [IDE에서 빌드 시작](../msbuild/starting-a-build-from-within-the-ide.md)
- [.NET Framework 확장명 등록](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [Item 요소(MSBuild)](../msbuild/item-element-msbuild.md)
- [Property 요소(MSBuild)](../msbuild/property-element-msbuild.md)
- [Target 요소(MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc 작업](../msbuild/csc-task.md)
- [Vbc 작업](../msbuild/vbc-task.md)
