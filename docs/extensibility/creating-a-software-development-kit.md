---
title: 소프트웨어 개발 키트 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739598"
---
# <a name="create-a-software-development-kit"></a>소프트웨어 개발 키트 만들기

소프트웨어 개발 키트(SDK)는 Visual Studio에서 단일 항목으로 참조할 수 있는 API 모음입니다. **참조 관리자** 대화 상자에는 프로젝트와 관련된 모든 SDK가 나열됩니다. 프로젝트에 SDK를 추가하면 Visual Studio에서 API를 사용할 수 있습니다.

SDK에는 두 가지 유형이 있습니다.

- 플랫폼 SDK는 플랫폼을 위한 앱을 개발하기 위한 필수 구성 요소입니다. 예를 들어 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK는 앱을 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 개발해야 합니다.

- 확장 SDK는 플랫폼을 확장하는 선택적 구성 요소이지만 해당 플랫폼에 대한 앱을 개발하는 데 필수는 아닙니다.

다음 섹션에서는 SDK의 일반 인프라와 플랫폼 SDK 및 확장 SDK를 만드는 방법에 대해 설명합니다.

## <a name="platform-sdks"></a>플랫폼 SDK

플랫폼 SDK는 플랫폼을 위한 앱을 개발해야 합니다. 예를 들어 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK는 에 대한 [!INCLUDE[win81](../debugger/includes/win81_md.md)]앱을 개발하는 데 필요합니다.

### <a name="installation"></a>설치

모든 플랫폼 SDK는 *HKLM\Software\Microsoft\Microsoft SDK\\[TPI]\v[TPV]\\ @InstallationFolder = [SDK 루트]에*설치됩니다. 따라서 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK는 *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1에*설치됩니다.

### <a name="layout"></a>레이아웃

플랫폼 SDK에는 다음과 같은 레이아웃이 있습니다.

```
\[InstallationFolder root]
            SDKManifest.xml
            \References
                  \[config]
                        \[arch]
            \DesignTime
                  \[config]
                        \[arch]
```

| 노드 | 설명 |
|------------------------| - |
| *참조* 폴더 | 코딩할 수 있는 API를 포함하는 바이너리를 포함합니다. 여기에는 Windows 메타데이터(WinMD) 파일 또는 어셈블리가 포함될 수 있습니다. |
| *디자인 타임* 폴더 | 사전 실행/디버깅 시간에만 필요한 파일을 포함합니다. 여기에는 XML 문서, 라이브러리, 헤더, 도구 상자 디자인 시간 바이너리, MSBuild 아티팩트 등이 포함될 수 있습니다.<br /><br /> XML 문서는 *이상적으로는 \DesignTime* 폴더에 배치되지만 참조용 XML 문서는 Visual Studio의 참조 파일 과 함께 계속 배치됩니다. 예를 들어 참조 \참조에 대한 XML 문서는<em>\\참조 [구성]\\[아치]\sample.dll</em> *\참조\\[구성] [아치]\sample.xml이\\*될 것이며, 해당 문서의 지역화된 버전은 *\References\\[config] [아치]\\\\[로케일]\sample.xml입니다.* |
| *구성* 폴더 | *디버그,* *소매* 및 *공통 구성*: 세 가지 폴더가 있을 수 있습니다 . SDK 작성자는 SDK 소비자가 대상으로 하는 구성에 관계없이 동일한 SDK 파일 집합을 사용해야 하는 경우 *공통 구성* 에 따라 파일을 배치할 수 있습니다. |
| *아키텍처* 폴더 | 지원되는 모든 *아키텍처* 폴더가 존재할 수 있습니다. Visual Studio는 x86, x64, ARM 및 중립 아키텍처를 지원합니다. 참고: Win32는 x86으로 매핑하고 AnyCPU는 중립으로 매핑합니다.<br /><br /> MSBuild는 플랫폼 SDK에 대한 *\CommonConfiguration\neutral* 에서만 보입니다. |
| *SDK매니페스트.xml* | 이 파일은 Visual Studio에서 SDK를 사용하는 방법을 설명합니다. SDK 매니페스트를 [!INCLUDE[win81](../debugger/includes/win81_md.md)]살펴보십시오.<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **디스플레이 이름:** 개체 브라우저가 찾아보기 목록에 표시되는 값입니다.<br /><br /> **플랫폼 정체성:** 이 특성의 존재는 Visual Studio 및 MSBuild에 SDK가 플랫폼 SDK이며 해당 특성에서 추가된 참조를 로컬로 복사해서는 안 된다는 것을 알려줍니다.<br /><br /> **대상 프레임워크:** 이 특성은 Visual Studio에서 이 특성의 값에 지정된 것과 동일한 프레임워크를 대상으로 하는 프로젝트만 SDK를 사용할 수 있도록 하는 데 사용됩니다.<br /><br /> **최소 VS버전:** 이 특성은 Visual Studio에서 해당 특성에 적용되는 SDK만 사용하는 데 사용됩니다.<br /><br /> **참조:** 이 특성은 컨트롤을 포함하는 해당 참조에 대해서만 지정해야 합니다. 참조에 컨트롤이 포함되어 있는지 여부를 지정하는 방법에 대한 자세한 내용은 아래를 참조하십시오. |

## <a name="extension-sdks"></a>확장 SDK

다음 섹션에서는 확장 SDK를 배포하기 위해 수행해야 하는 작업을 설명합니다.

### <a name="installation"></a>설치

확장 SDK는 레지스트리 키를 지정하지 않고 특정 사용자 또는 모든 사용자에 대해 설치할 수 있습니다. 모든 사용자에 대해 SDK를 설치하려면 다음 경로를 사용합니다.

*% 프로그램 파일 %\마이크로\<소프트\>SDKs 대상\>플랫폼 \v<플랫폼 버전 번호 \ ExtensionSDKs*

사용자 별 설치의 경우 다음 경로를 사용합니다.

*%USERPROFILE%\AppData\로컬\Microsoft SDKs\<\>대상 플랫폼 \v\><플랫폼 버전 번호 \ExtensionSDKs*

다른 위치를 사용하려면 다음 두 가지 중 하나를 수행해야 합니다.

1. 레지스트리 키에 지정합니다.

     **HKLM\소프트웨어\마이크로소프트\<SDKs 대상 플랫폼>\v<\>플랫폼 버전 번호\<\ExtensionSDKs SDKName>\<SDKVersion>**\

     및 의 값이 있는 (기본값) `<path to SDK><SDKName><SDKVersion>`하위 키를 추가합니다.

2. 프로젝트 파일에 MSBuild 속성을 `SDKReferenceDirectoryRoot` 추가합니다. 이 속성의 값은 참조하려는 확장 SDK가 상주하는 디렉터리의 세미콜론 으로 구분된 목록입니다.

### <a name="installation-layout"></a>설치 레이아웃

확장 SDK에는 다음과 같은 설치 레이아웃이 있습니다.

```
\<ExtensionSDKs root>
           \<SDKName>
                 \<SDKVersion>
                        SDKManifest.xml
                        \References
                              \<config>
                                    \<arch>
                        \Redist
                              \<config>
                                    \<arch>
                        \DesignTime
                               \<config>
                                     \<arch>

```

1. \\<SDKName\> \\<SDKVersion\>: 확장 SDK의 이름과 버전은 SDK 루트에 대한 경로의 해당 폴더 이름에서 파생됩니다. MSBuild는 이 ID를 사용하여 디스크에서 SDK를 찾고 Visual Studio는 **속성** 창 및 **참조 관리자** 대화 상자에 이 ID를 표시합니다.

2. *참조* 폴더: API를 포함하는 바이너리입니다. 이러한 파일은 Windows 메타데이터(WinMD) 파일 또는 어셈블리일 수 있습니다.

3. *Redist* 폴더: 런타임/디버깅에 필요한 파일이며 사용자 응용 프로그램의 일부로 패키징되어야 합니다. 모든 바이너리는 *<아치에\> \\ \>\\<redist*아래에 배치되어야하며 이진 이름은 고유성을 보장하기 위해 다음과 같은 형식을 가져야합니다 *>.*\< \<제품>. \<목적>. \<확장><em>. 예를 들어, *Microsoft.Cpp.Build.dll</em>. 다른 SDK의 파일 이름과 충돌할 수 있는 모든 파일(예: 자바스크립트, css, pri, xaml, png 및 jpg 파일)은 <em>XAML 컨트롤과\> \* 연결된 파일을 제외한\\ 모든\> \\ \> \\ 파일(예:<javascript, css, pri, xaml, png 및 jpg 파일)<<아치<sdkname 아래에 배치해야 합니다. 이러한\> \\ 파일은<\>구성 요소 이름<*\redist\\<\> \\ 아래에 배치되어야 합니다.</em>

4. *DesignTime* 폴더: 사전 실행/디버깅 시간에만 필요하며 사용자 응용 프로그램의 일부로 패키징되어서는 안 되는 파일입니다. 이러한 문서는 XML 문서, 라이브러리, 헤더, 도구 상자 디자인 시간 바이너리, MSBuild 아티팩트 등이 될 수 있습니다. 네이티브 프로젝트에서 사용할 수 있는 모든 SDK에는 *SDKName.props 파일이* 있어야 합니다. 다음은 이러한 유형의 파일의 샘플을 보여 주며, 이 중 과거의 예는 다음과 같은 것이다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>
       <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>
       <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>
       <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>
       <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>
       <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>
       <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>
     </PropertyGroup>
   </Project>

   ```

    XML 참조 문서는 참조 파일 옆에 배치됩니다. 예를 *들어, \references\\ \> \\<<참조<아치\>에* 대한 XML 참조 문서는<아치에 *\\ \> \\ \><*<설정에<대한 참조이며, 해당 문서의 지역화된 버전은 \references *\\<\> \\<아치\> \\<arch\>\sample.xml입니다.*

5. *구성* 폴더: 세 개의 하위 폴더: *디버그,* *소매*및 *공용 구성*. SDK 작성자는 SDK 소비자가 대상으로 하는 구성에 관계없이 동일한 SDK 파일 집합을 사용해야 하는 경우 *CommonConfiguration* 아래에 파일을 배치할 수 있습니다.

6. *아키텍처* 폴더: x86, x64, ARM, 중립 아키텍처가 지원됩니다. Win32는 x86에 매핑하고 AnyCPU는 중립으로 매핑합니다.

### <a name="sdkmanifestxml"></a>SDK매니페스트.xml

*SDKManifest.xml* 파일은 Visual Studio에서 SDK를 사용하는 방법을 설명합니다. 다음은 이에 대한 예입니다.

```
<FileList>
DisplayName = "My SDK"
ProductFamilyName = "My SDKs"
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"
MinVSVersion = "14.0"
MaxPlatformVersion = "8.1"
AppliesTo = "WindowsAppContainer + WindowsXAML"
SupportPrefer32Bit = "True"
SupportedArchitectures = "x86;x64;ARM"
SupportsMultipleVersions = "Error"
CopyRedistToSubDirectory = "."
DependsOn = "SDKB, version=2.0"
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

다음 목록은 파일의 요소를 제공합니다.

1. DisplayName: 참조 관리자, 솔루션 탐색기, 개체 브라우저 및 Visual Studio용 사용자 인터페이스의 다른 위치에 표시되는 값입니다.

2. 제품패밀리이름: 전체 SDK 제품 이름입니다. 예를 [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] 들어, SDK는 "Microsoft.WinJS.1.0"과 "Microsoft.WinJS.2.0"이라는 이름으로, SDK 제품군의 동일한 제품군인 "Microsoft.WinJS"에 속합니다. 이 특성을 사용하면 Visual Studio 및 MSBuild에서 해당 연결을 만들 수 있습니다. 이 특성이 없으면 SDK 이름이 제품군 이름으로 사용됩니다.

3. FrameworkIdentity: 하나 이상의 Windows 구성 요소 라이브러리에 대한 종속성을 지정합니다. 이 특성의 값은 소비 앱의 매니페스트에 넣습니다. 이 특성은 Windows 구성 요소 라이브러리에만 적용할 수 있습니다.

4. TargetFramework: 참조 관리자 및 도구 상자에서 사용할 수 있는 SDK를 지정합니다. 이 목록은 ".NET 프레임워크, 버전=v2.0; .NET 프레임워크, 버전=v4.5.1"과 같은 세미콜론으로 구분된 대상 프레임워크 모니커 목록입니다. 동일한 대상 프레임워크의 여러 버전이 지정되면 참조 관리자는 필터링을 위해 가장 지정된 가장 낮은 버전을 사용합니다. 예를 들어 ".NET 프레임워크, 버전=v2.0, .NET 프레임워크, 버전=v4.5.1"이 지정되면 참조 관리자는 ".NET 프레임워크, 버전=v2.0"을 사용합니다. 특정 대상 프레임워크 프로필을 지정하면 해당 프로필만 필터링을 위해 참조 관리자에서 사용됩니다. 예를 들어 "Silverlight, version=v4.0, profile=WindowsPhone"을 지정하면 참조 관리자는 Windows Phone 프로필에서만 필터를 사용합니다. 전체 Silverlight 4.0 프레임워크를 대상으로 하는 프로젝트에는 참조 관리자에 SDK가 표시되지 않습니다.

5. MinVSVersion: 최소 비주얼 스튜디오 버전입니다.

6. MaxPlatformVerson: 최대 대상 플랫폼 버전을 사용하여 확장 SDK가 작동하지 않는 플랫폼 버전을 지정해야 합니다. 예를 들어 Microsoft Visual C++ 런타임 패키지 v11.0은 Windows 8 프로젝트에서만 참조해야 합니다. 따라서, 윈도우 8 프로젝트의 맥스 플랫폼버전은 8.0입니다. 즉, 참조 관리자는 Windows 8.1 프로젝트에 대 한 Microsoft 시각적 C ++ 런타임 패키지를 필터링 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 하 고 MSBuild 프로젝트를 참조 하는 경우 오류를 throw 합니다. 참고: 이 요소는 에서 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]부터 지원됩니다.

7. 적용대상: 해당 Visual Studio 프로젝트 유형을 지정하여 참조 관리자에서 사용할 수 있는 SDK를 지정합니다. 9개의 값이 인식됩니다: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, 자바스크립트, 관리형 및 네이티브. SDK 작성자는 ("+") 또는 ("&#124;") ("!") SDK에 적용되는 프로젝트 유형의 범위를 정확하게 지정할 수 있습니다.

    WindowsAppContainer앱에 대한 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 프로젝트를 식별합니다.

8. SupportPrefer32Bit: 지원되는 값은 "True" 및 "False"입니다. 기본값은 "True"입니다. 값이 "False"로 설정된 경우 MSBuild는 SDK를 참조하는 프로젝트가 Prefer32Bit를 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 사용하도록 설정한 경우 프로젝트(또는 데스크톱 프로젝트에 대한 경고)에 대한 오류를 반환합니다. Prefer32Bit에 대한 자세한 내용은 [빌드 페이지, 프로젝트 디자이너(C#)](../ide/reference/build-page-project-designer-csharp.md) 또는 [컴파일 페이지, 프로젝트 디자이너(Visual Basic)를](../ide/reference/compile-page-project-designer-visual-basic.md)참조하십시오.

9. 지원되는 아키텍처: SDK가 지원하는 세미콜론아키텍처 목록입니다. MSBuild는 소비 프로젝트의 대상 SDK 아키텍처가 지원되지 않는 경우 경고를 표시합니다. 이 특성을 지정하지 않으면 MSBuild는 이러한 유형의 경고를 표시하지 않습니다.

10. 지원MultipleVersion: 이 특성이 **오류** 또는 **경고로**설정된 경우 MSBuild는 동일한 프로젝트가 동일한 SDK 제품군의 여러 버전을 참조할 수 없다는 것을 나타냅니다. 이 특성이 없거나 **허용으로**설정된 경우 MSBuild는 이 유형의 오류 또는 경고를 표시하지 않습니다.

11. AppX: 디스크의 Windows 구성 요소 라이브러리에 대한 앱 패키지 경로를 지정합니다. 이 값은 로컬 디버깅 중에 Windows 구성 요소 라이브러리의 등록 구성 요소에 전달됩니다. 파일 이름의 명명 규칙은 * \<회사>.\< 제품>. \<아키텍처>. \<구성>. 버전 \<>.appx*. 구성 및 아키텍처는 특성 이름과 Windows 구성 요소 라이브러리에 적용되지 않는 경우 특성 값에서 선택 사항입니다. 이 값은 Windows 구성 요소 라이브러리에만 적용할 수 있습니다.

12. CopyRedistToSubDirectory: *\redist* 폴더 아래의 파일을 앱 패키지 루트(즉, 앱 패키지 **만들기** 마법사에서 선택한 **패키지 위치)와** 런타임 레이아웃 루트를 기준으로 복사해야 하는 위치를 지정합니다. 기본 위치는 앱 패키지 및 **F5** 레이아웃의 루트입니다.

13. On: 이 SDK가 종속되는 SDK를 정의하는 SDK ID 목록입니다. 이 특성은 참조 관리자의 세부 정보 창에 나타납니다.

14. MoreInfo: 도움말 및 추가 정보를 제공하는 웹 페이지의 URL입니다. 이 값은 참조 관리자의 오른쪽 창에 있는 추가 정보 링크에서 사용됩니다.

15. 등록 유형: 앱 매니페스트에서 WinMD 등록을 지정하며 DLL 구현이 있는 네이티브 WinMD에 필요합니다.

16. 파일 참조: 컨트롤을 포함하거나 기본 WinMD인 참조에만 지정됩니다. 참조에 컨트롤이 포함되어 있는지 여부를 지정하는 방법에 대한 자세한 내용은 아래 [도구 상자 항목의 위치 지정을](#ToolboxItems) 참조하십시오.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>도구 상자 항목의 위치 지정

*SDKManifest.xml* 스키마의 **ToolBoxItems** 요소는 플랫폼 및 확장 SDK 모두에서 도구 상자 항목의 범주 및 위치를 지정합니다. 다음 예제는 다른 위치를 지정하는 방법을 보여 주며 있습니다. 이는 WinMD 또는 DLL 참조에 적용할 수 있습니다.

1. 도구 상자 기본 범주에 컨트롤을 배치합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. 특정 범주 이름 아래에 컨트롤을 배치합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. 특정 범주 이름 아래에 컨트롤을 배치합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. 블렌드 및 비주얼 스튜디오에서 다른 범주 이름 아래에 컨트롤을 배치합니다.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. 블렌드 및 비주얼 스튜디오에서 특정 컨트롤을 다르게 열거합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. 특정 컨트롤을 열거하고 Visual Studio 공통 경로 아래에 배치하거나 모든 컨트롤 그룹에만 배치합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. 특정 컨트롤을 열거하고 도구 상자에 없는 SelectItem의 특정 집합만 표시합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>참조

- [연습: C++를 사용하여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [연습: C# 또는 시각적 기본을 사용하여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [프로젝트에서 참조 관리](../ide/managing-references-in-a-project.md)
