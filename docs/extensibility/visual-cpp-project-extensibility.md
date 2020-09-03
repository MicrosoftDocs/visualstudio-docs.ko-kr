---
title: Visual C++ 프로젝트 확장성
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10869ad290b0b8df614d25d792d0b3ed1e88eb17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825562"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio c + + 프로젝트 시스템 확장성 및 도구 집합 통합

Visual C++ 프로젝트 시스템은 .vcxproj 파일에 사용 됩니다. 이 도구는 [Visual STUDIO CPS (Common Project System)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) 를 기반으로 하며, 새로운 도구 집합, 빌드 아키텍처 및 대상 플랫폼을 쉽게 통합 하기 위한 추가 c + + 관련 확장성 위치를 제공 합니다.

## <a name="c-msbuild-targets-structure"></a>C + + MSBuild 대상 구조

모든 .vcxproj 파일은 다음 파일을 가져옵니다.

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

이러한 파일은 자체적으로 정의 되지 않습니다. 대신, 이러한 속성 값에 따라 다른 파일을 가져옵니다.

- `$(ApplicationType)`

   예: Windows 스토어, Android, Linux

- `$(ApplicationTypeRevision)`

   이것은 major [. build [. revision]] 형식의 유효한 버전 문자열 이어야 합니다.

   예: 1.0, 10.0.0.0

- `$(Platform)`

   기록 이유 때문에 "Platform" 이라는 빌드 아키텍처가 있습니다.

   예: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   예: v140, v141, v141_xp, llvm

이러한 속성 값은 루트 폴더 아래에 폴더 이름을 지정 합니다 `$(VCTargetsPath)` .

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*응용 프로그램 유형*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*플랫폼*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets 집합*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*플랫폼*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets 집합*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

`$(VCTargetsPath)` \\ *플랫폼* \\ 폴더는 `$(ApplicationType)` 가 비어 있을 때 Windows 데스크톱 프로젝트에 사용 됩니다.

### <a name="add-a-new-platform-toolset"></a>새 플랫폼 도구 집합 추가

기존 Win32 플랫폼에 대 한 새 도구 집합 (예: "mytoolset 집합")을 추가 하려면 *MyToolset* `$(VCTargetsPath)` * \\ 플랫폼 \\ Win32 \\ platformtoolsets 집합 \\ *아래에 mytoolset 집합 폴더를 만들고 여기에 *도구 집합* 및 *도구 집합* 파일을 만듭니다.

*Platformtoolsets 집합* 의 각 폴더 이름은 다음과 같이 **프로젝트 속성** 대화 상자에 지정 된 플랫폼에 대 한 사용 가능한 **플랫폼 도구 집합** 으로 나타납니다.

![프로젝트 속성 페이지 대화 상자의 플랫폼 도구 집합 속성](media/vc-project-extensibility-platform-toolset-property.png "프로젝트 속성 페이지 대화 상자의 플랫폼 도구 집합 속성")

이 도구 집합에서 지 원하는 각 기존 플랫폼 폴더에 비슷한 *Mytoolset 집합* 폴더 및 *도구* 집합 및 *도구* 집합 파일을 만듭니다.

### <a name="add-a-new-platform"></a>새 플랫폼 추가

새 플랫폼 (예: "myplatform")을 추가 *MyPlatform* 하려면 플랫폼 `$(VCTargetsPath)` * \\ \\ *아래에 myplatform 폴더를 만들고 해당 폴더에 *platform.string*, platform.string 및 *platform.string* 파일 *을*만듭니다. 또한 `$(VCTargetsPath)` * \\ 플랫폼 \\ *<strong><em>myplatform</em></strong>* \\ \\ platformtoolsets 집합* 폴더를 만들고 하나 이상의 도구 집합을 만듭니다.

각에 대 한 Platform *폴더 아래의 모든 폴더 이름이* `$(ApplicationType)` `$(ApplicationTypeRevision)` IDE에서 프로젝트에 대해 사용 가능한 **플랫폼** 선택 항목으로 나타납니다.

![새 프로젝트 플랫폼 대화 상자에서 새 플랫폼 선택](media/vc-project-extensibility-new-project-platform.png "새 프로젝트 플랫폼 대화 상자에서 새 플랫폼 선택")

### <a name="add-a-new-application-type"></a>새 응용 프로그램 유형 추가

새 응용 프로그램 종류를 추가 하려면 *MyApplicationType* 응용 프로그램 종류 `$(VCTargetsPath)` * \\ \\ * 아래에서 myapplicationtype 폴더를 만들고 여기에 *기본값.* s t a t e r 파일을 만듭니다. 응용 프로그램 형식에는 하나 이상의 수정이 필요 하므로 `$(VCTargetsPath)` * \\ 응용 프로그램 유형 \\ myapplicationtype \\ 1.0* 폴더를 만들고 여기에 *기본값.* s t a t e r 파일을 만듭니다. 또한 `$(VCTargetsPath)` * \\ applicationtype \\ myapplicationtype \\ 1.0 \\ * platform 폴더를 만들고 하나 이상의 플랫폼을 만들어야 합니다.

`$(ApplicationType)` 및 `$(ApplicationTypeRevision)` 속성은 사용자 인터페이스에 표시 되지 않습니다. 이러한 파일은 프로젝트 템플릿에 정의 되며 프로젝트를 만든 후에는 변경할 수 없습니다.

## <a name="the-vcxproj-import-tree"></a>.Vcxproj 가져오기 트리

Microsoft c + + props 및 targets 파일에 대 한 가져오기의 단순화 된 트리는 다음과 같습니다.

> `$(VCTargetsPath)`\\*Microsoft .Cpp. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importbefore* \\ *기본값* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*응용 프로그램 유형* \\ `$(ApplicationType)` \\ *기본값. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*응용 프로그램* \\ `$(ApplicationType)` \\ 유형 `$(ApplicationTypeRevision)` \\ *기본값. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*응용 프로그램* \\ `$(ApplicationType)` \\ 유형 `$(ApplicationTypeRevision)` \\ *Platforms* \\ `$(Platform)` 플랫폼 \\ *Platform.object. 기본값. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importafter* \\ *기본값* \\ \* . *props*

Windows 데스크톱 프로젝트 `$(ApplicationType)` 는을 정의 하지 않으므로 가져오기만

> `$(VCTargetsPath)`\\*Microsoft .Cpp. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importbefore* \\ *기본값* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platforms* \\ `$(Platform)` 플랫폼 \\ *Platform.object. 기본값. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importafter* \\ *기본값* \\ \* . *props*

속성을 사용 `$(_PlatformFolder)` 하 여 `$(Platform)` 플랫폼 폴더 위치를 저장 합니다. 이 속성은

> `$(VCTargetsPath)`\\*플랫폼*\\`$(Platform)`

Windows 데스크톱 앱의 경우

> `$(VCTargetsPath)`\\*응용 프로그램* \\ `$(ApplicationType)` \\ 유형 `$(ApplicationTypeRevision)` \\ *플랫폼*\\`$(Platform)`

다른 모든 항목

다음 순서로 props 파일을 가져옵니다.

> `$(VCTargetsPath)`\\*Microsoft .Cpp.* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.object* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft .Cpp. Platform.object.* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importbefore* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platformtoolsets 집합* \\ `$(PlatformToolset)` \\ *도구 집합 props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importafter* \\ \* . *props*

대상 파일은 다음 순서로 가져옵니다.

> `$(VCTargetsPath)`\\*Microsoft .Cpp 대상* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft .Cpp. .targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.object* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft .Cpp. Platform.object. .targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importbefore* \\ \* . *대상* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platformtoolsets 집합* \\ `$(PlatformToolset)` \\ *도구 집합. 대상* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importafter* \\ \* . *대상*

도구 집합에 대 한 몇 가지 기본 속성을 정의 해야 하는 경우 파일을 해당 ImportBefore 및 Importbefore 폴더에 추가할 수 있습니다.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>도구 집합 props 및 도구 집합 파일을 작성 합니다.

*도구* 집합 및 *도구* 집합 파일은이 도구 집합을 사용할 때 빌드 중에 발생 하는 작업을 완전히 제어 합니다. **속성 페이지** 대화 상자의 콘텐츠와 같은 IDE 사용자 인터페이스와 프로젝트 동작의 다른 측면에서 사용 가능한 디버거를 제어할 수도 있습니다.

도구 집합은 전체 빌드 프로세스를 재정의할 수 있지만, 일반적으로 도구 집합에서 일부 빌드 단계를 수정 또는 추가 하거나 기존 빌드 프로세스의 일부로 다른 빌드 도구를 사용 하 게 하려는 경우를 예로 들 수 있습니다. 이러한 목표를 달성 하기 위해 도구 집합에서 가져올 수 있는 일반적인 props 및 대상 파일이 많이 있습니다. 도구 집합에서 수행 하려는 작업에 따라 이러한 파일은 가져오기 또는 예제로 사용 하는 데 유용할 수 있습니다.

- `$(VCTargetsPath)`\\*CppCommon*

  이 파일은 기본 빌드 프로세스의 주요 부분을 정의 하 고도 가져옵니다.

  - `$(VCTargetsPath)`\\*CppBuild*

  - `$(VCTargetsPath)`\\*Microsoft BuildSteps. 대상*

  - `$(MSBuildToolsPath)`\\*Microsoft 일반 .Targets*

- `$(VCTargetsPath)`\\*Microsoft .Cpp.*

   Microsoft 컴파일러 및 대상 창을 사용 하는 도구 집합에 대 한 기본값을 설정 합니다.

- `$(VCTargetsPath)`\\*Microsoft .Cpp.*

   이 파일은 Windows SDK 위치를 확인 하 고 Windows를 대상으로 하는 앱에 대 한 일부 중요 한 속성을 정의 합니다.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>도구 집합 관련 대상을 기본 c + + 빌드 프로세스에 통합

기본 c + + 빌드 프로세스는 *CppCommon*에 정의 되어 있습니다. 특정 빌드 도구를 호출 하지 않는 대상입니다. 주 빌드 단계, 해당 순서 및 종속성을 지정 합니다.

C + + 빌드에는 다음 대상으로 표시 되는 세 가지 주요 단계가 있습니다.

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

각 빌드 단계는 독립적으로 실행 될 수 있으므로 한 번에 실행 되는 대상은 다른 단계의 일부로 실행 되는 대상에 정의 된 항목 그룹 및 속성을 사용할 수 없습니다. 이러한 분할은 특정 빌드 성능 최적화를 허용 합니다. 이는 기본적으로 사용 되지 않지만 여전히 이러한 분리를 적용 하는 것이 좋습니다.

각 단계 내에서 실행 되는 대상은 다음과 같은 속성으로 제어 됩니다.

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

각 단계에는 속성 전후에도 있습니다.

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

각 단계에 포함 된 대상의 예는 *CppBuild* 파일을 참조 하세요.

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

과 같은 대상을 살펴보면 `_ClCompile` 다음을 비롯 한 다른 대상에 종속 되지 않는 것을 볼 수 있습니다 `ClCompile` .

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` 및 기타 빌드 도구 관련 대상은 *CppBuild*에서 빈 대상으로 정의 됩니다.

```xml
<Target Name="ClCompile"/>
```

`ClCompile`대상은 비어 있으므로 도구 집합에 의해 재정의 되지 않으면 실제 빌드 작업이 수행 되지 않습니다. 도구 집합 대상은 대상을 재정의할 수 있습니다. 즉 `ClCompile` , CppBuild를 가져온 후 다른 정의를 포함할 수 있습니다 `ClCompile` . *Microsoft.CppBuild.targets*

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Visual Studio에서 플랫폼 간 지원을 구현 하기 전에 만든 이름에도 불구 `ClCompile` 하 고 대상은 CL.exe를 호출할 필요가 없습니다. 또한 적절 한 MSBuild 작업을 사용 하 여 Clang, gcc 또는 기타 컴파일러를 호출할 수 있습니다.

대상에 `ClCompile` 는 `SelectClCompile` 단일 파일 컴파일 명령이 IDE에서 작동 하는 데 필요한 대상을 제외한 종속성이 없어야 합니다.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>도구 집합 대상에 사용할 MSBuild 작업

실제 빌드 도구를 호출 하려면 대상이 MSBuild 작업을 호출 해야 합니다. 실행할 명령줄을 지정할 수 있는 기본 [Exec 태스크가](../msbuild/exec-task.md) 있습니다. 그러나 일반적으로 빌드 도구에는 입력의 많은 옵션이 있습니다. 그리고 증분 빌드에 대 한 추적을 출력 하므로 특수 한 작업을 수행 하는 것이 더 적합 합니다. 예를 들어, `CL` 작업은 MSBuild 속성을 CL.exe 스위치로 변환 하 고 지시 파일에 쓴 다음 CL.exe를 호출 합니다. 또한 이후 증분 빌드에 대 한 모든 입력 및 출력 파일을 추적 합니다. 자세한 내용은 [증분 빌드 및 최신 검사](#incremental-builds-and-up-to-date-checks)를 참조 하세요.

Microsoft.Cpp.Common.Tasks.dll는 다음과 같은 작업을 구현 합니다.

- `BSCMake`

- `CL`

- `ClangCompile` (clang-gcc 스위치)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (예: Exec) 및 입력 및 출력 추적

- `SetEnv`

- `GetOutOfDateItems`

기존 도구와 동일한 작업을 수행 하는 도구를 사용 하 고 clang-cl 및 CL과 비슷한 명령줄 스위치를 사용 하는 도구를 사용 하는 경우 둘 다에 대해 동일한 작업을 사용할 수 있습니다.

빌드 도구에 대 한 새 작업을 만들어야 하는 경우 다음 옵션 중에서 선택할 수 있습니다.

1. 이 작업을 거의 사용 하지 않거나 빌드에 몇 초가 중요 하지 않은 경우 MSBuild ' 인라인 ' 작업을 사용할 수 있습니다.

   - Xaml 작업 (사용자 지정 빌드 규칙)

     Xaml 작업 선언의 한 예를 보려면 `$(VCTargetsPath)` \\ *buildcustomizations 지정* \\ *masm.xml*를 참조 하 고 해당 사용법에 대해 `$(VCTargetsPath)` \\ *buildcustomizations 지정* \\ *masm. 대상*을 참조 하세요.

   - [코드 작업](../msbuild/msbuild-inline-tasks.md)

1. 더 나은 작업 성능을 원하는 경우 또는 보다 복잡 한 기능만 필요한 경우 일반 MSBuild [작업 쓰기](../msbuild/task-writing.md) 프로세스를 사용 합니다.

   도구에 있는 모든 입력 및 출력이, 및 사례와 같이 도구 명령줄에 나열 되지 않으며, `CL` `MIDL` `RC` 자동 입력 및 출력 파일 추적과. tlog 파일을 만들려면 클래스에서 작업을 파생 시킵니다 `Microsoft.Build.CPPTasks.TrackedVCToolTask` . 현재 기본 [Tooltask](/dotnet/api/microsoft.build.utilities.tooltask) 클래스에 대 한 설명서가 있지만 클래스의 세부 정보에 대 한 예제 또는 설명서는 없습니다 `TrackedVCToolTask` . 특히 관심이 있는 경우 [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html)의 요청에 음성을 추가 합니다.

## <a name="incremental-builds-and-up-to-date-checks"></a>증분 빌드 및 최신 검사

기본 MSBuild 증분 빌드 대상은 및 특성을 사용 합니다 `Inputs` `Outputs` . 지정 하는 경우 MSBuild는 입력에 모든 출력 보다 최신 타임 스탬프가 있는 경우에만 대상을 호출 합니다. 소스 파일은 종종 다른 파일을 포함 하거나 가져오고, 빌드 도구는 도구 옵션에 따라 다양 한 출력을 생성 하기 때문에 MSBuild 대상에서 가능한 모든 입력 및 출력을 지정 하는 것은 어렵습니다.

이 문제를 관리 하기 위해 c + + 빌드는 다른 기술을 사용 하 여 증분 빌드를 지원 합니다. 대부분의 대상은 입력 및 출력을 지정 하지 않으며, 결과적으로 빌드 중에 항상 실행 됩니다. 대상이에서 호출 하는 작업은 확장명이 tlog 인 *tlog* 파일에 모든 입력 및 출력에 대 한 정보를 기록 합니다. Tlog 파일은 변경 된 내용을 확인 하 고 다시 작성 해야 하는 것과 최신 버전을 확인 하기 위해 이후 빌드에서 사용 됩니다. 또한 tlog 파일은 IDE의 기본 빌드 최신 체크 인에 대 한 유일한 원본입니다.

모든 입력 및 출력을 확인 하기 위해 네이티브 도구 작업에서는 tracker.exe 및 MSBuild에서 제공 하는 [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) 클래스를 사용 합니다.

Microsoft.Build.CPPTasks.Common.dll `TrackedVCToolTask` 공용 추상 기본 클래스를 정의 합니다. 대부분의 네이티브 도구 작업은이 클래스에서 파생 됩니다.

Visual Studio 2017 업데이트 15.8부터 `GetOutOfDateItems` Microsoft.Cpp.Common.Tasks.dll에 구현 된 작업을 사용 하 여 알려진 입력과 출력을 포함 하는 사용자 지정 대상에 대 한 tlog 파일을 생성할 수 있습니다.
또는 작업을 사용 하 여 만들 수 있습니다 `WriteLinesToFile` . `_WriteMasmTlogs` `$(VCTargetsPath)` \\ 예제로 *buildcustomizations 지정*의 대상 \\ *masm.targets* 을 참조 하세요.

## <a name="tlog-files"></a>tlog 파일

Tlog 파일에는 *읽기*, *쓰기*및 *명령줄*의 세 가지 유형이 있습니다. 읽기 및 쓰기 tlog 파일은 증분 빌드와 IDE의 최신 검사에 사용 됩니다. 명령줄 tlog 파일은 증분 빌드에서만 사용 됩니다.

MSBuild는 다음과 같은 도우미 클래스를 제공 하 여 tlog 파일을 읽고 씁니다.

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) 클래스를 사용 하 여 읽기 및 쓰기 tlog 파일에 액세스 하 고 출력 보다 최신 인 입력을 식별 하거나 출력이 없는 경우에도 사용할 수 있습니다. 최신 검사에 사용 됩니다.

명령줄 tlog 파일에는 빌드에 사용 되는 명령줄에 대 한 정보가 포함 되어 있습니다. 이러한 항목은 최신 검사가 아닌 증분 빌드에서만 사용 되므로 내부 형식은 생성 하는 MSBuild 작업에 의해 결정 됩니다.

### <a name="read-tlog-format"></a>Tlog 형식 읽기

*Read* Tlog 파일 ( \* . read \* . tlog)에는 원본 파일 및 해당 종속성에 대 한 정보가 포함 되어 있습니다.

**^** 줄의 시작 부분에 있는 캐럿 ()은 하나 이상의 소스를 나타냅니다. 동일한 종속성을 공유 하는 원본은 세로 막대 ()로 구분 됩니다 **\|** .

종속성 파일은 각각 별도의 줄에 있는 원본 뒤에 나열 됩니다. 모든 파일 이름은 전체 경로입니다.

예를 들어 프로젝트 소스가 *F: \\ test \\ consoleapplication1.exe \\ consoleapplication1.exe*에 있는 것으로 가정 합니다. 원본 파일인 *Class1 .cpp*에는 다음이 포함 되어 있습니다.

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

그런 다음, *cl.exe* 파일에는 원본 파일과 두 개의 종속성이 포함 됩니다.

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

대문자는 파일 이름을 쓸 필요가 없지만 일부 도구에서는 편리 합니다.

### <a name="write-tlog-format"></a>Tlog 형식 작성

*Write* Tlog ( \* . write ... \* tlog) 파일은 원본과 출력을 연결 합니다.

**^** 줄의 시작 부분에 있는 캐럿 ()은 하나 이상의 소스를 나타냅니다. 여러 소스는 세로 막대 ()로 구분 됩니다 **\|** .

원본에서 빌드된 출력 파일은 각각 별도의 줄에 있는 소스 뒤에 나열 되어야 합니다. 모든 파일 이름은 전체 경로 여야 합니다.

예를 들어 추가 *원본 파일이 ConsoleApplication 인 간단한*프로젝트의 경우 *에는 파일에* 다음이 포함 될 수 있습니다.

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>디자인 타임 빌드

IDE에서 .vcxproj 프로젝트는 MSBuild 대상 집합을 사용 하 여 프로젝트에서 추가 정보를 가져오고 출력 파일을 다시 생성 합니다. 이러한 대상 중 일부는 디자인 타임 빌드 에서만 사용 되지만 대부분은 일반적인 빌드와 디자인 타임 빌드에 모두 사용 됩니다.

디자인 타임 빌드에 대 한 일반 정보는 [디자인 타임 빌드](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md)에 대 한 CPS 설명서를 참조 하세요. 이 설명서는 Visual C++ 프로젝트에 부분적 으로만 적용 됩니다.

`CompileDesignTime` `Compile` 디자인 타임 빌드 설명서에 언급 된 및 대상은 .vcxproj 프로젝트에 대해서는 실행 되지 않습니다. Visual C++ .vcxproj 프로젝트는 다양 한 디자인 타임 대상을 사용 하 여 IntelliSense 정보를 가져옵니다.

### <a name="design-time-targets-for-intellisense-information"></a>IntelliSense 정보에 대 한 디자인 타임 대상

.Vcxproj 프로젝트에 사용 되는 디자인 타임 대상은 `$(VCTargetsPath)` \\ *Microsoft .cpp designtime. .targets*에 정의 되어 있습니다.

`GetClCommandLines`대상은 IntelliSense의 컴파일러 옵션을 수집 합니다.

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – 디자인 타임 빌드를 초기화 하는 데 필요한 디자인 타임 전용 대상입니다. 무엇 보다도 이러한 대상은 일부 일반 빌드 기능을 사용 하지 않도록 설정 하 여 성능을 향상 시킵니다.

- `ComputeCompileInputsTargets` – 컴파일러 옵션 및 항목을 수정 하는 대상 집합입니다. 이러한 대상은 디자인 타임 및 일반 빌드에서 실행 됩니다.

대상은 작업을 호출 `CLCommandLine` 하 여 IntelliSense에 사용할 명령줄을 만듭니다. 그 이름에도 불구 하 고 CL 옵션 뿐만 아니라 Clang 및 gcc 옵션도 처리할 수 있습니다. 컴파일러 스위치의 형식은 속성에 의해 제어 됩니다 `ClangMode` .

현재 작업에 의해 생성 되는 명령줄은 `CLCommandLine` IntelliSense 엔진이 구문 분석 하기 쉬우므로 항상 Clang 모드에서 CL 스위치를 사용 합니다.

일반 또는 디자인 타임에 대해 컴파일하기 전에 실행 되는 대상을 추가 하는 경우 디자인 타임 빌드를 중단 하거나 성능에 영향을 주지 않도록 해야 합니다. 대상을 테스트 하는 가장 간단한 방법은 개발자 명령 프롬프트를 열고 다음 명령을 실행 하는 것입니다.

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

이 명령은 끝에 대상 및 작업에 대 한 성능 요약이 있는 자세한 빌드 로그 인 *msbuild.exe*를 생성 합니다.

`Condition ="'$(DesignTimeBuild)' != 'true'"`디자인 타임 빌드가 아닌 일반 빌드에만 적합 한 모든 작업에서를 사용 해야 합니다.

### <a name="design-time-targets-that-generate-sources"></a>소스를 생성 하는 디자인 타임 대상

*이 기능은 데스크톱 네이티브 프로젝트에 대해 기본적으로 사용 하지 않도록 설정 되며 캐시 된 프로젝트에서는 현재 지원 되지*않습니다.

`GeneratorTarget`프로젝트 항목에 대해 메타 데이터가 정의 된 경우 프로젝트가 로드 될 때와 소스 파일이 변경 될 때 대상이 자동으로 실행 됩니다.

::: moniker range="vs-2017"

예를 들어 .xaml 파일에서 .cpp 또는 .h 파일을 자동으로 생성 하려면 `$(VSInstallDir)` \\ *MSBuild* \\ *microsoft* \\ *windowsxaml* \\ *v 15.0* \\ \* \\ *Microsoft.Windows.UI.Xaml.CPP.Targets* 파일에서 다음과 같은 엔터티를 정의 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

예를 들어 .xaml 파일에서 .cpp 또는 .h 파일을 자동으로 생성 하려면 `$(VSInstallDir)` \\ *MSBuild* \\ *microsoft* \\ *windowsxaml* \\ *v 16.0* \\ \* \\ *Microsoft.Windows.UI.Xaml.CPP.Targets* 파일에서 다음과 같은 엔터티를 정의 합니다.

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

을 사용 하 여 `Task.HostObject` 소스 파일의 저장 되지 않은 콘텐츠를 가져오기 위해 대상 및 작업을 .pkgdef의 지정 된 프로젝트에 대 한 [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) 으로 등록 해야 합니다.

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual Studio IDE에서 프로젝트 확장성 Visual C++

Visual C++ 프로젝트 시스템은 [VS 프로젝트 시스템](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)을 기반으로 하며 확장성 지점이 사용 됩니다. 그러나 프로젝트 계층 구조 구현은 CPS를 기반으로 하지 않고 Visual C++에만 적용 되므로 계층 확장성은 프로젝트 항목으로 제한 됩니다.

### <a name="project-property-pages"></a>프로젝트 속성 페이지

일반적인 디자인 정보는 [VC + + 프로젝트에 대 한 프레임 워크 다중 대상 지정](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/)을 참조 하세요.

간단히 말해, c + + 프로젝트에 대 한 **프로젝트 속성** 대화 상자에 표시 되는 속성 페이지는 *규칙* 파일에 의해 정의 됩니다. 규칙 파일은 속성 페이지에 표시할 속성 집합과 프로젝트 파일에 저장 해야 하는 방법 및 위치를 지정 합니다. 규칙 파일은 Xaml 형식을 사용 하는 .xml 파일입니다. 이를 serialize 하는 데 사용 되는 형식은 [Microsoft. Build. XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes)에 설명 되어 있습니다. 프로젝트에서 규칙 파일을 사용 하는 방법에 대 한 자세한 내용은 [속성 페이지 XML 규칙 파일](/cpp/build/reference/property-page-xml-files)을 참조 하세요.

규칙 파일은 항목 그룹에 추가 해야 합니다 `PropertyPageSchema` .

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` 메타 데이터 제한 규칙 표시 여부는 규칙 형식에 의해 제어 되며, 다음 값 중 하나를 사용할 수 있습니다.

`Project` | `File` | `PropertySheet`

CPS는 컨텍스트 형식에 대해 다른 값을 지원 하지만 Visual C++ 프로젝트에는 사용 되지 않습니다.

하나 이상의 컨텍스트에서 규칙을 표시 해야 하는 경우 다음과 같이 세미콜론 (**;**)을 사용 하 여 컨텍스트 값을 구분 합니다.

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>규칙 형식 및 기본 형식

규칙 형식은 간단 하므로이 섹션에서는 사용자 인터페이스에서 규칙이 표시 되는 방법에 영향을 주는 특성만 설명 합니다.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate`특성은 **속성 페이지** 대화 상자에 규칙이 표시 되는 방법을 정의 합니다. 특성에는 다음 값 중 하나를 사용할 수 있습니다.

| 특성 | 설명 |
|------------| - |
| `generic` | 모든 속성은 범주 제목 아래에 있는 한 페이지에 표시 됩니다.<br/>규칙은 및 컨텍스트에 대해서는 볼 수 있지만는 볼 수 `Project` `PropertySheet` 없습니다 `File` .<br/><br/> 예: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | 범주는 하위 페이지로 표시 됩니다.<br/>규칙은 `Project` , 및의 모든 컨텍스트에서 볼 수 있습니다 `PropertySheet` . `File`<br/>규칙 `ItemType` `Rule.DataSource` 이름이 항목 그룹에 포함 되지 않은 경우 프로젝트에가에 정의 된 항목이 있는 경우에만 프로젝트 속성에 규칙이 표시 됩니다 `ProjectTools` .<br/><br/>예: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | 페이지는 디버깅 페이지의 일부로 표시 됩니다.<br/>범주는 현재 무시 됩니다.<br/>규칙 이름은 디버그 시작 관리자 MEF 개체의 특성과 일치 해야 합니다 `ExportDebugger` .<br/><br/>예: `$(VCTargetsPath)` \\ *1033* \\ *디버거 \_ 로컬 \_windows.xml* |
| *재구성* | 사용자 지정 템플릿입니다. 템플릿의 이름은 `ExportPropertyPageUIFactoryProvider` MEF 개체의 특성과 일치 해야 합니다 `PropertyPageUIFactoryProvider` . **VisualStudio. IPropertyPageUIFactoryProvider**를 참조 하세요.<br/><br/> 예: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

규칙에서 속성 그리드 기반 템플릿 중 하나를 사용 하는 경우 해당 속성에 다음과 같은 확장성을 사용할 수 있습니다.

- [속성 값 편집기](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [동적 열거형 값 공급자](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>규칙 확장

기존 규칙을 사용 하려는 경우 몇 가지 속성만 추가 하거나 제거 (즉, 숨기기) 해야 하는 경우 [확장 규칙](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md)을 만들 수 있습니다.

#### <a name="override-a-rule"></a>규칙 재정의

도구 집합에서 대부분의 프로젝트 기본 규칙을 사용 하지만 하나 또는 몇 개의 규칙을 바꾸도록 하려는 경우가 있습니다. 예를 들어, 다른 컴파일러 스위치를 표시 하도록 C/c + + 규칙만 변경 하려는 경우를 가정해 보겠습니다. 기존 규칙과 이름 및 표시 이름이 같은 새 규칙을 제공 하 고 `PropertyPageSchema` 기본 cpp 대상을 가져온 후 항목 그룹에 포함 시킬 수 있습니다. 프로젝트에는 지정 된 이름의 규칙이 하나만 사용 되며 항목 그룹에 마지막으로 포함 된 규칙은 `PropertyPageSchema` wins입니다.

#### <a name="project-items"></a>프로젝트 항목

*ProjectItemsSchema.xml* 파일은 `ContentType` `ItemType` 프로젝트 항목으로 처리 되는 항목에 대 한 및 값을 정의 하 고, `FileExtension` 새 파일이 추가 되는 항목 그룹을 결정 하는 요소를 정의 합니다.

1033ProjectItemsSchema.xml에서 기본 ProjectItemsSchema 파일을 찾을 수 `$(VCTargetsPath)` \\ *1033* \\ * *있습니다. 이를 확장 하려면 *MyProjectItemsSchema.xml*와 같은 새 이름을 사용 하 여 스키마 파일을 만들어야 합니다.

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

그런 다음 대상 파일에서 다음을 추가 합니다.

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

예: `$(VCTargetsPath)` \\ *buildcustomizations 지정* \\ *masm.xml*

### <a name="debuggers"></a>디버거

Visual Studio의 디버그 서비스는 디버그 엔진에 대 한 확장성을 지원 합니다. 자세한 내용은 다음 샘플을 참조 하세요.

- [MIEngine, lldb 디버깅을 지 원하는 오픈 소스 프로젝트](https://github.com/Microsoft/MIEngine)

- [Visual Studio 디버그 엔진 샘플](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

디버그 세션에 대 한 디버그 엔진과 기타 속성을 지정 하려면 [디버그 시작 관리자](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) MEF 구성 요소를 구현 하 고 규칙을 추가 해야 합니다 `debugger` . 예제는 `$(VCTargetsPath)` \\ 1033 \\ 디버거 \_ 로컬windows.xml 파일을 참조 \_ 하세요.

### <a name="deploy"></a>배포

.vcxproj 프로젝트는 [공급자 배포](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md)를 위해 Visual Studio 프로젝트 시스템 확장성을 사용 합니다.

### <a name="build-up-to-date-check"></a>최신 검사 빌드

기본적으로 빌드 최신 검사를 수행 하려면 `$(TlogLocation)` 모든 빌드 입력 및 출력에 대해 빌드하는 동안 폴더에 생성 되는 tlog 및 파일을 작성 해야 합니다.

사용자 지정 최신 검사를 사용 하려면 다음을 수행 합니다.

1. `NoVCDefaultBuildUpToDateCheckProvider` *도구 집합* 파일에 기능을 추가 하 여 기본적인 최신 검사를 사용 하지 않도록 설정 합니다.

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. 사용자 고유의 [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md)을 구현 합니다.

## <a name="project-upgrade"></a>프로젝트 업그레이드

### <a name="default-vcxproj-project-upgrader"></a>기본값 .vcxproj 프로젝트 업그레이 더

기본 .vcxproj 프로젝트 업그레이 더는 `PlatformToolset` , `ApplicationTypeRevision` , MSBuild 도구 집합 버전 및 .net framework를 변경 합니다. 마지막 두 개는 항상 Visual Studio 버전 기본값으로 변경 되지만 `PlatformToolset` 및는 `ApplicationTypeRevision` 특수 MSBuild 속성에 의해 제어 될 수 있습니다.

업그레이 더는 이러한 기준을 사용 하 여 프로젝트를 업그레이드할 수 있는지 여부를 결정 합니다.

1. 및를 정의 하는 프로젝트의 경우 `ApplicationType` `ApplicationTypeRevision` 현재 항목 보다 더 높은 수정 번호가 있는 폴더가 있습니다.

1. 속성이 `_UpgradePlatformToolsetFor_<safe_toolset_name>` 현재 도구 집합에 대해 정의 되 고 해당 값이 현재 도구 집합과 같지 않은 경우

   이러한 속성 이름에서는 *\<safe_toolset_name>* 모든 영숫자가 아닌 문자가 밑줄 ()로 바뀐 도구 집합 이름을 나타냅니다 **\_** .

프로젝트를 업그레이드할 수 있는 경우 *솔루션*대상 변경에 참여 합니다. 자세한 내용은 [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2)를 참조 하세요.

프로젝트에서 특정 도구 집합을 사용 하는 경우 **솔루션 탐색기** 에서 프로젝트 이름을 장식할 하려면 속성을 정의 `_PlatformToolsetShortNameFor_<safe_toolset_name>` 합니다.

`_UpgradePlatformToolsetFor_<safe_toolset_name>`및 속성 정의의 예제를 `_PlatformToolsetShortNameFor_<safe_toolset_name>` 보려면 *Microsoft .cpp* 파일을 참조 하십시오. 사용법에 대 한 예제는 `$(VCTargetPath)` \\ *Microsoft .cpp. .targets* 파일을 참조 하십시오.

### <a name="custom-project-upgrader"></a>사용자 지정 프로젝트 업그레이 더

사용자 지정 프로젝트 업그레이 더 개체를 사용 하려면 다음과 같이 MEF 구성 요소를 구현 합니다.

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

코드에서 기본. .vcxproj 업그레이 더 개체를 가져오고 호출할 수 있습니다.

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` 는 *Microsoft.VisualStudio.ProjectSystem.VS.dll* 정의 되며와 비슷합니다 `IVsRetargetProjectAsync` .

속성을 정의 `VCProjectUpgraderObjectName` 하 여 사용자 지정 업그레이 더 개체를 사용 하도록 프로젝트 시스템에 지시 합니다.

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>프로젝트 업그레이드 사용 안 함

프로젝트 업그레이드를 사용 하지 않도록 설정 하려면 다음 값을 사용 합니다 `NoUpgrade` .

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>프로젝트 캐시 및 확장성

Visual Studio 2017에서 많은 c + + 솔루션으로 작업할 때 성능을 향상 시키기 위해 [프로젝트 캐시가](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) 도입 되었습니다. 이는 프로젝트 데이터로 채워진 SQLite 데이터베이스로 구현 된 다음 MSBuild 또는 CPS 프로젝트를 메모리로 로드 하지 않고 프로젝트를 로드 하는 데 사용 됩니다.

캐시에서 로드 된 .vcxproj 프로젝트에 대 한 CPS 개체가 없으므로 가져오거나 만들 수 없는 확장의 MEF 구성 요소가 있습니다 `UnconfiguredProject` `ConfiguredProject` . 확장성을 지원 하기 위해 Visual Studio에서 프로젝트가 MEF 확장을 사용 하는지 (또는 사용할 가능성이 높음) 검색 하는 경우 프로젝트 캐시가 사용 되지 않습니다.

이러한 프로젝트 형식은 항상 완전히 로드 되며 CPS 개체가 메모리에 있으므로 모든 MEF 확장이 만들어집니다.

- 시작 프로젝트

- 사용자 지정 프로젝트 업그레이 더를 포함 하는 프로젝트 (즉, 속성을 정의 합니다. `VCProjectUpgraderObjectName`

- 데스크톱 창을 대상으로 하지 않는 프로젝트 즉, 속성을 정의 합니다. `ApplicationType`

- .Vcxitems 프로젝트를 가져와 공유 항목 프로젝트 (. .vcxitems) 및이를 참조 하는 모든 프로젝트.

이러한 조건 중 어느 것도 검색 되지 않으면 프로젝트 캐시가 생성 됩니다. 캐시에는 `get` 인터페이스에 대 한 쿼리에 응답 하는 데 필요한 MSBuild 프로젝트의 모든 데이터가 포함 됩니다 `VCProjectEngine` . 즉, MSBuild props 및 대상 파일 수준의 모든 수정 내용이 캐시에서 로드 된 프로젝트 에서만 작동 해야 합니다.

## <a name="shipping-your-extension"></a>내선 번호 전달

VSIX 파일을 만드는 방법에 대 한 자세한 내용은 [Visual Studio 확장](../extensibility/shipping-visual-studio-extensions.md)제공을 참조 하세요. 에서 파일을 추가 하는 등의 특수 설치 위치에 파일을 추가 하는 방법에 대 한 자세한 내용은 `$(VCTargetsPath)` [extensions 폴더 외부에 설치](../extensibility/set-install-root.md)를 참조 하세요.

## <a name="additional-resources"></a>추가 자료

[MSBuild](../msbuild/msbuild.md)(Microsoft Build System)는 프로젝트 파일에 대 한 확장 가능한 XML 기반 형식 및 빌드 엔진을 제공 합니다. 기본 [msbuild 개념](../msbuild/msbuild-concepts.md) 및 Visual C++ 프로젝트 시스템을 확장 하기 위해 [Visual C++의 msbuild](/cpp/build/reference/msbuild-visual-cpp-overview) 작동 방식을 잘 알고 있어야 합니다.

[MEF](/dotnet/framework/mef/)(Managed Extensibility Framework)는 CPS 및 Visual C++ 프로젝트 시스템에서 사용 하는 확장 api를 제공 합니다. CPS에서 MEF를 사용 하는 방법에 대 한 개요는 [mef의 Vsprojectsystem 개요](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md)에서 [cps 및 mef](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) 를 참조 하세요.

빌드 단계 또는 새 파일 형식을 추가 하도록 기존 빌드 시스템을 사용자 지정할 수 있습니다. 자세한 내용은 [MSBuild (Visual C++) 개요](/cpp/build/reference/msbuild-visual-cpp-overview) 및 [프로젝트 속성 작업](/cpp/build/working-with-project-properties)을 참조 하세요.
