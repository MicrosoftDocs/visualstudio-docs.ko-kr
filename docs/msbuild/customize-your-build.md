---
title: 빌드 사용자 지정 | Microsoft Docs
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7ddf87f5fa9f937c0272e37f3a6b4aba29f2d6c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652796"
---
# <a name="customize-your-build"></a>빌드 사용자 지정

표준 빌드 프로세스(*Microsoft.Common.props* 및 *Microsoft.Common.targets* 가져오기)를 사용하는 MSBuild 프로젝트에는 빌드 프로세스를 사용자 지정하는 데 사용할 수 있는 몇 가지 확장성 후크가 있습니다.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>프로젝트에 대한 명령줄 MSBuild 호출에 인수 추가

원본 디렉터리 이상의 *Directory.Build.rsp* 파일은 프로젝트의 명령줄 빌드에 적용됩니다. 자세한 내용은 [MSBuild 지시 파일](../msbuild/msbuild-response-files.md#directorybuildrsp)을 참조하세요.

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props 및 Directory.Build.targets

MSBuild 15 이전 버전에서는 솔루션의 프로젝트에 대한 새로운 사용자 지정 속성을 제공하려면 해당 속성에 대한 참조를 솔루션의 모든 프로젝트 파일에 수동으로 추가해야 했습니다. 또는 *.props* 파일에서 속성을 정의하고 나서 무엇보다 솔루션의 모든 프로젝트에서 *.props* 파일을 명시적으로 가져와야 했습니다.

그러나 지금은 원본을 포함하는 루트 폴더에서 *Directory.Build.props*라는 단일 파일에 새 속성을 정의하여 한 단계로 모든 프로젝트에 새 속성을 추가할 수 있습니다. MSBuild가 실행되면 *Microsoft.Common.props*는 *Directory.Build.props* 파일에 대한 디렉터리 구조를 검색하고 *Microsoft.Common.targets*는 *Directory.Build.targets*를 검색합니다. 속성을 찾으면 해당 속성을 가져옵니다. *Directory.Build.props*는 디렉터리에 있는 프로젝트에 대한 사용자 지정을 제공하는 사용자 지정 파일입니다.

> [!NOTE]
> Linux 기반 파일 시스템은 대/소문자를 구분합니다. Directory.Build.props 파일 이름의 대/소문자가 정확히 일치하는지 확인합니다. 일치하지 않으면 빌드 프로세스 중에 파일이 검색되지 않습니다.
>
> 자세한 내용은 [이 GitHub 문제](https://github.com/dotnet/core/issues/1991#issue-368441031)를 참조하세요.

### <a name="directorybuildprops-example"></a>Directory.Build.props 예제

예를 들어 모든 프로젝트가 새 Roslyn **/deterministic** 기능(속성 `$(Deterministic)`에 의해 Roslyn `CoreCompile` 대상에 표시됨)에 액세스하도록 허용하려면 다음을 수행합니다.

1. *Directory.Build.props*라는 리포지토리의 루트에 새 파일을 만듭니다.
2. 파일에 다음 XML을 추가합니다.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. MSBuild를 실행합니다. 프로젝트의 기존 *Microsoft.Common.props* 및 *Microsoft.Common.targets* 가져오기는 파일을 찾아서 가져옵니다.

### <a name="search-scope"></a>검색 범위

*Directory.Build.props* 파일을 검색할 때 MSBuild는 프로젝트 위치(`$(MSBuildProjectFullPath)`)에서 위쪽으로 디렉터리 구조를 이동하여 *Directory.Build.props* 파일을 찾은 후 멈춥니다. 예를 들어 `$(MSBuildProjectFullPath)`가 *c:\users\username\code\test\case1*인 경우 MSBuild는 여기에서 검색을 시작하고 *Directory.Build.props* 파일을 찾을 때까지 위쪽으로 다음 디렉터리 구조와 같은 디렉터리 구조를 검색합니다.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

솔루션 파일 위치는 *Directory.Build.props*와 관련이 없습니다.

### <a name="import-order"></a>가져오기 순서

*Directory.Build.props*는 *Microsoft.Common.props*에서 초기에 가져오고 나중에 정의된 속성을 적용할 수 없습니다. 따라서 아직 정의되지 않은 속성을 참조하지 마세요. 참조할 경우 비어 있는 것으로 평가됩니다.

*Directory.Build.targets*는 NuGet 패키지에서 *.targets* 파일을 가져온 후 *Microsoft.Common.targets*에서 가져옵니다. 따라서 대부분의 빌드 논리에 정의된 속성 및 대상을 재정의할 수 있으나, 마지막으로 가져온 후 프로젝트를 사용자 지정해야 할 수 있습니다.

### <a name="use-case-multi-level-merging"></a>사용 사례: 다단계 병합

이 표준 솔루션 구조체가 있다고 가정합니다.

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

모든 프로젝트 *(1)* 의 공통 속성, *src* 프로젝트 *(2-src)* 의 공통 속성 및 *test* 프로젝트 *(2-test)* 의 공통 속성이 있는 것이 바람직할 수도 있습니다.

MSBuild에서 “내부” 파일(*2-src* 및 *2-test*)을 “외부” 파일(*1*)과 올바르게 병합하려면 MSBuild가 *Directory.Build.props* 파일을 찾으면 추가 검사를 중지하도록 고려해야 합니다. 계속 검사하고 외부 파일에 병합하려면 이 코드를 모든 내부 파일에 배치합니다.

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

MSBuild의 일반적인 방법의 요약 정보는 다음과 같습니다.

- 지정된 프로젝트의 경우 MSBuild는 솔루션 구조체에서 위쪽으로 첫 번째 *Directory.Build.props*를 찾고, 기본값과 병합하고, 추가 검사를 중지합니다.
- 다단계를 찾고 병합하려는 경우 "내부" 파일에서 "외부" 파일을 [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove)(위에 표시)합니다.
- "외부" 파일이 자체로 상위 항목을 가져오지 않으면 거기서 검색을 중지합니다.
- 검사/병합 프로세스를 제어하려면 `$(DirectoryBuildPropsPath)` 및 `$(ImportDirectoryBuildProps)`를 사용합니다.

간단히 말하면 아무것도 가져오지 않는 첫 번째 *Directory.Build.props*에서 MSBuild가 중지됩니다.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>.props 또는 .targets 파일에 속성 추가 중에서 선택

MSBuild는 가져오기 순서에 종속되며, 속성(`UsingTask` 또는 대상)의 마지막 정의가 사용됩니다.

명시적 가져오기를 사용하는 경우, 언제든지 *.props* 또는 *.targets* 파일에서 가져올 수 있습니다. 일반적으로 사용되는 규칙은 다음과 같습니다.

- *.props* 파일은 가져오기 순서의 초기에 가져옵니다.

- *.targets* 파일은 빌드 순서의 이후에 가져옵니다.

이 규칙은 `<Project Sdk="SdkName">` 가져오기에 의해 적용됩니다. 즉, *Sdk.props* 가져오기가 파일의 모든 내용 앞에 오고, *Sdk.targets*가 파일의 모든 내용 뒤에 마지막으로 옵니다.

속성을 배치할 위치를 결정하는 경우 다음 일반 지침을 따르세요.

- 대부분의 속성은 덮어쓰지 않고 실행 시간에 읽기만 하므로 정의된 위치가 중요하지 않습니다.

- 개별 프로젝트에서 사용자 지정할 수 있는 동작의 경우 *.props* 파일에서 기본값을 설정합니다.

- MSBuild에서 사용자 프로젝트를 읽어야 사용자 지정이 발생하므로, 가능한 사용자 지정 속성 값을 읽어 *.props* 파일에서 종속 속성을 설정하지 마세요.

- *.targets* 파일에서 종속 속성을 설정합니다. 그러면 속성이 개별 프로젝트에서 사용자 지정을 선택합니다.

- 속성을 재정의해야 하는 경우 모든 사용자 프로젝트 사용자 지정이 적용된 후에 *.targets* 파일에 재정의합니다. 파생 속성을 사용할 때는 주의합니다. 파생 속성도 재정의해야 할 수 있습니다.

- *.props* 파일에 항목을 포함합니다(속성에 따라 조건부). 모든 속성이 항목보다 먼저 고려되므로, 사용자 프로젝트 속성 사용자 지정이 선택되어 사용자 프로젝트에서 가져오기를 통해 가져오는 항목을 `Remove` 또는 `Update`할 기회를 제공합니다.

- *.targets* 파일에서 대상을 정의합니다. 그러나 SDK를 통해 *.targets* 파일을 가져오는 경우, 이 시나리오를 사용하면 대상 재정의가 더 어려워집니다. 사용자 프로젝트에서는 기본적으로 대상을 재정의할 수 없기 때문입니다.

- 가능한 경우, 대상 내의 속성을 변경하는 대신 평가 시간에 속성을 사용자 지정하는 것이 좋습니다. 이 지침을 따르면 보다 간편하게 프로젝트를 로드하고 프로젝트에서 수행하는 작업을 파악할 수 있습니다.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

기본적으로 *Microsoft.Common.props*가 `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props`를 가져오고 *Microsoft.Common.targets*가 `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`를 가져옵니다. `MSBuildProjectExtensionsPath`의 기본값은 `$(BaseIntermediateOutputPath)`, `obj/`입니다. NuGet에서 패키지와 함께 제공되는 빌드 논리를 참조하는 데 이 메커니즘을 사용합니다. 즉, 복원 시 패키지 콘텐츠를 참조하는 `{project}.nuget.g.props` 파일을 만듭니다.

*Directory.Build.props*에서 속성 `ImportProjectExtensionProps`을 `false`로 설정하거나 *Microsoft.Common.props*를 가져오기 전에 이 확장성 메커니즘을 사용하지 않도록 설정할 수 있습니다.

> [!NOTE]
> MSBuildProjectExtensionsPath 가져오기를 비활성화하면 NuGet 패키지에 제공된 빌드 논리가 프로젝트에 적용되는 것을 방지합니다. 일부 NuGet 패키지는 해당 기능을 수행하기 위해 빌드 논리가 필요하고 비활성화될 때 쓸모 없는 것으로 렌더링됩니다.

## <a name="user-file"></a>.user 파일

*Microsoft.Common.CurrentVersion.targets*는 있는 경우 `$(MSBuildProjectFullPath).user`를 가져오므로 해당 추가 확장을 사용하여 프로젝트 옆에 파일을 만들 수 있습니다. 장기 변경을 위해 원본 제어를 확인하려는 경우 향후 유지 관리자가 이 확장 메커니즘에 대해 알 필요가 없도록 프로젝트 자체를 변경하는 것이 좋습니다.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath 및 MSBuildUserExtensionsPath

> [!WARNING]
> 이러한 확장 메커니즘을 사용하면 컴퓨터에서 반복 가능한 빌드를 가져오기 어렵게 됩니다. 원본 제어 시스템을 확인하고 코드 베이스의 모든 개발자와 공유할 수 있는 구성을 사용하도록 시도합니다.

관례상 많은 핵심 빌드 논리 파일 가져오기는

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

해당 콘텐츠 전과 후에

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

이루어집니다. 이 규칙을 사용하면 설치된 SDK에서 공용 프로젝트 형식의 빌드 논리를 확장할 수 있습니다.

동일한 디렉터리 구조는 사용자당 폴더 *%LOCALAPPDATA%\Microsoft\MSBuild*인 `$(MSBuildUserExtensionsPath)`에서 검색됩니다. 해당 폴더에 있는 파일을 해당 사용자의 자격 증명으로 실행되는 해당 프로젝트 형식의 모든 빌드에 가져옵니다. 사용자 확장은 패턴 `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`에서 가져오는 파일에 따라 명명된 속성을 설정하여 비활성화할 수 있습니다. 예를 들어 `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps`를 `false`로 설정하면 `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` 가져오기를 방지합니다.

## <a name="customize-the-solution-build"></a>솔루션 빌드 사용자 지정

> [!IMPORTANT]
> 이러한 방식의 솔루션 빌드 사용자 지정은 *MSBuild.exe*를 사용하여 명령줄 빌드에만 적용됩니다. Visual Studio 내의 빌드에 적용되지 **않습니다**.

MSBuild에서 솔루션 파일을 빌드할 때 먼저 프로젝트 파일로 내부적으로 변환한 다음, 빌드합니다. 생성된 프로젝트 파일은 `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` 및 `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` 디렉터리에 설치된 대상을 포함하여 대상을 정의하기 전에 `before.{solutionname}.sln.targets`를 가져오고 대상을 가져온 후에 `after.{solutionname}.sln.targets`를 가져옵니다.

예를 들어 포함하는 *after.MyCustomizedSolution.sln.targets*라는 동일한 디렉터리에 파일을 만들어 *MyCustomizedSolution.sln*을 빌드한 후 사용자 지정 로그 메시지를 작성하도록 새 대상을 정의할 수 있습니다.

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="customize-all-net-builds"></a>모든 .NET 빌드 사용자 지정

빌드 서버를 유지 관리할 때는 서버에 있는 모든 빌드에 대해 MSBuild 설정을 전역적으로 구성해야 할 수 있습니다.  원칙적으로 전역 *Microsoft.Common.Targets* 또는 *Microsoft.Common.Props* 파일을 수정할 수 있지만 더 좋은 방법이 있습니다. 특정 MSBuild 속성을 사용하고 특정 사용자 지정 `.targets` 및 `.props` 파일을 추가하여 특정 프로젝트 형식(예: 모든 C# 프로젝트)의 모든 빌드에 영향을 줄 수 있습니다.

MSBuild 또는 Visual Studio 설치가 관리하는 모든 C# 또는 Visual Basic 빌드에 영향을 주려면 *Microsoft.Common.targets* 파일 전이나 후에 실행될 대상과 함께 *Custom.Before.Microsoft.Common.Targets* 또는 *Custom.After.Microsoft.Common.Targets* 파일을 만들거나 *Microsoft.Common.props* 전이나 후에 처리될 속성과 함께 *Custom.Before.Microsoft.Common.Props* 또는 *Custom.After.Microsoft.Common.Props* 파일을 만듭니다.

다음 MSBuild 속성을 사용하여 이러한 파일의 위치를 지정할 수 있습니다.

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

이러한 속성의 *공통* 버전은 C# 프로젝트와 Visual Basic 프로젝트 모두에 영향을 줍니다. MSBuild 명령줄에서 이러한 속성을 설정할 수 있습니다.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

가장 좋은 방법은 시나리오에 따라 달라집니다. 전용 빌드 서버가 있고 해당 서버에서 실행되는 적절한 프로젝트 형식의 모든 빌드에서 항상 특정 대상이 실행되도록 하려면 전역 사용자 지정 `.targets` 또는 `.props` 파일을 사용하는 것이 좋습니다.  특정 조건이 적용될 때만 사용자 지정 대상이 실행되도록 하려면 다른 파일 위치를 사용하고 필요한 경우에만 MSBuild 명령줄에서 적절한 MSBuild 속성을 설정하여 해당 파일의 경로를 설정합니다.

> [!WARNING]
> Visual Studio는 형식이 일치하는 프로젝트를 빌드할 때마다 MSBuild 폴더에서 사용자 지정 `.targets` 또는 `.props` 파일을 찾으면 이를 사용합니다. 이로 인해 의도하지 않은 결과가 발생할 수 있으며, 제대로 수행되지 않으면 컴퓨터에서 Visual Studio의 빌드 기능을 사용하지 못할 수 있습니다.

## <a name="customize-all-c-builds"></a>모든 C++ 빌드 사용자 지정

C++ 프로젝트에서는 앞에서 언급한 사용자 지정 `.targets` 및 `.props` 파일이 무시됩니다. C++ 프로젝트에서는 플랫폼마다 `.targets` 파일을 만들어 해당 플랫폼의 적절한 가져오기 폴더에 배치할 수 있습니다.

Win32 플랫폼용 `.targets` 파일인 *Microsoft.Cpp.Win32.targets*에는 다음 `Import` 요소가 포함되어 있습니다.

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

같은 파일의 끝에는 비슷한 요소가 있습니다.

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

*%ProgramFiles32%\MSBuild\Microsoft.Cpp\v{version}\Platforms\*에는 다른 대상 플랫폼을 위한 비슷한 import 요소가 있습니다.

플랫폼에 따라 적절한 폴더에 `.targets` 파일을 배치하면 MSBuild는 해당 플랫폼의 모든 C++ 빌드에 해당 파일을 가져옵니다. 필요한 경우, 여기에 여러 `.targets` 파일을 넣을 수 있습니다.

### <a name="specify-a-custom-import-on-the-command-line"></a>명령줄에서 사용자 지정 가져오기 지정

C++ 프로젝트의 특정 빌드에 포함하려는 사용자 지정 `.targets`의 경우 명령줄에서 `ForceImportBeforeCppTargets` 속성과 `ForceImportAfterCppTargets` 속성 중 하나 또는 둘 모두를 설정합니다.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

(예를 들어 빌드 서버의 플랫폼에 대한 모든 C++ 빌드에 영향을 주기 위한) 전역 설정의 경우, 두 가지 방법이 있습니다. 첫째, 항상 설정되어 있는 시스템 환경 변수를 사용하여 이러한 속성을 설정할 수 있습니다. MSBuild는 항상 환경을 읽고 모든 환경 변수의 속성을 만들거나 재정의하기 때문에 이 방법은 효과적입니다.

## <a name="see-also"></a>참조

- [MSBuild 개념](../msbuild/msbuild-concepts.md)

- [MSBuild 참조](../msbuild/msbuild-reference.md)
