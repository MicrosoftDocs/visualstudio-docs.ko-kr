---
title: 소프트웨어 개발 키트 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61e547be5f240cafccc058eb7ea2249fd492554b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904114"
---
# <a name="create-a-software-development-kit"></a>소프트웨어 개발 키트 만들기

SDK (소프트웨어 개발 키트)는 Visual Studio에서 단일 항목으로 참조할 수 있는 Api 컬렉션입니다. **참조 관리자** 대화 상자에는 프로젝트와 관련 된 모든 sdk가 나열 됩니다. 프로젝트에 SDK를 추가 하면 Visual Studio에서 Api를 사용할 수 있습니다.

Sdk에는 다음과 같은 두 가지 유형이 있습니다.

- 플랫폼 Sdk는 플랫폼에 대 한 앱을 개발 하기 위한 필수 구성 요소입니다. 예를 들어 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK는 앱을 개발 하는 데 필요 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 합니다.

- 확장 Sdk는 플랫폼을 확장 하는 선택적 구성 요소 이지만 해당 플랫폼에 대 한 앱을 개발 하는 데 반드시 필요한 것은 아닙니다.

다음 섹션에서는 Sdk의 일반 인프라 및 플랫폼 SDK와 확장 SDK를 만드는 방법에 대해 설명 합니다.

## <a name="platform-sdks"></a>플랫폼 SDK

플랫폼 Sdk는 플랫폼에 대 한 앱을 개발 하는 데 필요 합니다. 예를 들어 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK는 용 응용 프로그램을 개발 하는 데 필요 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 합니다.

### <a name="installation"></a>설치

모든 플랫폼 Sdk는 *HKLM\Software\Microsoft\Microsoft sdk \\ [tpi] \v [tpi] \\ @InstallationFolder = [SDK root]* 에 설치 됩니다. 따라서 SDK는 [!INCLUDE[win81](../debugger/includes/win81_md.md)] *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*에 설치 됩니다.

### <a name="layout"></a>Layout

플랫폼 Sdk의 레이아웃은 다음과 같습니다.

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
| *참조* 폴더 | 코딩 될 수 있는 Api를 포함 하는 이진 파일을 포함 합니다. 여기에는 Windows 메타 데이터 (WinMD) 파일 또는 어셈블리가 포함 될 수 있습니다. |
| *Designtime* 폴더 | 사전 실행/디버깅 시간에만 필요한 파일을 포함 합니다. 여기에는 XML 문서, 라이브러리, 헤더, 도구 상자 디자인 타임 이진 파일, MSBuild 아티팩트 등이 포함 될 수 있습니다.<br /><br /> XML 문서를 *\Designtime* 폴더에 배치 하는 것이 가장 좋지만, 참조용 xml 문서는 Visual Studio의 참조 파일과 함께 계속 배치 됩니다. 예를 들어 참조에 대 한 XML doc<em> \\ [config] \\ [아치] \sample.dll</em> 은 *\references \\ [config] \\ [\sample.xml*)가 되며 해당 문서의 지역화 된 버전은 *\references \\ [config] \\ [아치] \\ [locale] \sample.xml*됩니다. |
| *구성* 폴더 | *Debug*, *Retail* 및 *CommonConfiguration*의 폴더는 3 개만 있을 수 있습니다. Sdk 작성자는 sdk 소비자가 대상으로 하는 구성에 관계 없이 동일한 SDK 파일 집합을 사용 해야 하는 경우 *CommonConfiguration* 아래에 해당 파일을 저장할 수 있습니다. |
| *아키텍처* 폴더 | 지원 되는 모든 *아키텍처* 폴더가 있을 수 있습니다. Visual Studio는 x86, x64, ARM 및 중립적인 아키텍처를 지원 합니다. 참고: Win32는 x 86에 매핑되고 AnyCPU는 중립에 매핑됩니다.<br /><br /> MSBuild는 플랫폼 Sdk에 대 한 *\CommonConfiguration\neutral* 에서만 보입니다. |
| *SDKManifest.xml* | 이 파일은 Visual Studio에서 SDK를 사용 하는 방법을 설명 합니다. 다음에 대 한 SDK 매니페스트를 확인 합니다 [!INCLUDE[win81](../debugger/includes/win81_md.md)] .<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** 개체 브라우저 찾아보기 목록에 표시 되는 값입니다.<br /><br /> **Platformidentity:** 이 특성이 있으면 SDK가 플랫폼 SDK이 고이 sdk에서 추가 된 참조를 로컬로 복사 하지 않는다는 것을 Visual Studio 및 MSBuild에 알립니다.<br /><br /> **Targetframework:** 이 특성은 Visual Studio에서이 특성의 값에 지정 된 것과 같은 프레임 워크를 대상으로 하는 프로젝트 에서만 SDK를 사용할 수 있도록 하는 데 사용 됩니다.<br /><br /> **Minvsversion:** 이 특성은 Visual Studio에서 해당 특성에 적용 되는 Sdk만을 사용 하는 데 사용 됩니다.<br /><br /> **참조:** 이 특성은 컨트롤을 포함 하는 참조에 대해서만 지정 해야 합니다. 참조에 컨트롤이 포함 되어 있는지 여부를 지정 하는 방법에 대 한 자세한 내용은 아래를 참조 하세요. |

## <a name="extension-sdks"></a>확장 SDK

다음 섹션에서는 확장 SDK를 배포 하기 위해 수행 해야 하는 작업에 대해 설명 합니다.

### <a name="installation"></a>설치

확장 Sdk는 특정 사용자에 대해 설치 하거나 레지스트리 키를 지정 하지 않고 모든 사용자에 게 설치할 수 있습니다. 모든 사용자 용 SDK를 설치 하려면 다음 경로를 사용 합니다.

*% Program Files%\Microsoft Sdk \<target platform\> \v<platform 버전 번호 \> \Extensionsdk*

사용자 특정 설치의 경우 다음 경로를 사용 합니다.

*%USERPROFILE%\AppData\Local\Microsoft Sdk \<target platform\> \v<플랫폼 버전 번호 \> \Extensionsdk*

다른 위치를 사용 하려면 다음 두 가지 작업 중 하나를 수행 해야 합니다.

1. 레지스트리 키에 지정 합니다.

     **HKLM\Software\Microsoft\Microsoft Sdk \<target platform> \v<플랫폼 버전 번호 \> \Extensionsdk\<SDKName>\<SDKVersion>**\

     및의 값이 인 (기본) 하위 키를 추가 `<path to SDK><SDKName><SDKVersion>` 합니다.

2. MSBuild 속성을 `SDKReferenceDirectoryRoot` 프로젝트 파일에 추가 합니다. 이 속성의 값은 참조 하려는 확장 Sdk가 상주 하는 디렉터리의 세미콜론으로 구분 된 목록입니다.

### <a name="installation-layout"></a>설치 레이아웃

확장 Sdk의 설치 레이아웃은 다음과 같습니다.

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

1. \\<SDKName \> \\<SDKVersion \> : 확장 sdk의 이름과 버전은 sdk 루트 경로에 있는 해당 폴더 이름에서 파생 됩니다. MSBuild는이 id를 사용 하 여 디스크에서 SDK를 검색 하 고, Visual Studio는 **속성** 창 및 **참조 관리자** 대화 상자에이 id를 표시 합니다.

2. *References* 폴더: api를 포함 하는 이진 파일입니다. 이러한 파일은 Windows 메타 데이터 (WinMD) 파일 또는 어셈블리가 될 수 있습니다.

3. *Redist* 폴더: 런타임/디버깅에 필요한 파일이 며 사용자 응용 프로그램의 일부로 패키지 되어야 합니다. 모든 이진 파일은 *\redist \\<config \> \\ \><아치*아래에 배치 해야 하며, 이진 이름에는 고유성을 보장 하기 위해 다음과 같은 형식이 있어야 합니다. *]* \<company> ... \<product> \<purpose> \<extension> <em>. 예를 들면 * Microsoft.Cpp.Build.dll</em>입니다. 다른 Sdk의 파일 이름 (예: javascript, css, pri, xaml, png, jpg 파일)과 충돌 하는 이름을 가진 모든 파일은 <em> \\ \> \\ \> \\ xaml 컨트롤에 연결 된 파일을 제외 하 고 sdkname<아치<<\> \* 아래에 배치 해야 합니다. 이러한 파일은 * \redist \\<config \> \\<아치 \> \\<componentname \> \\ 아래에 배치 해야</em>합니다.

4. *Designtime* 폴더: 사전 실행/디버깅 시간에만 필요한 파일 이며 사용자 응용 프로그램의 일부로 패키지할 수 없습니다. XML 문서, 라이브러리, 헤더, 도구 상자 디자인 타임 이진 파일, MSBuild 아티팩트 등이 될 수 있습니다. 네이티브 프로젝트에서 사용 하기 위한 모든 SDK에는 *SDKName* 파일이 있어야 합니다. 다음은 이러한 파일 형식의 샘플을 보여 줍니다.

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

    XML 참조 문서는 참조 파일과 함께 배치 됩니다. 예를 들어 *\references \\<구성 \> \\<아치 \>\sample.dll* 어셈블리에 대 한 XML 참조 문서는 * \\ 구성 \> \\<아치 \>\sample.xml<구성<* 의 *지역화 된 버전입니다. \\ \> \\ \> \\ \> *

5. *구성* 폴더: *Debug*, *Retail*및 *CommonConfiguration*의 세 하위 폴더입니다. Sdk 작성자는 sdk 소비자의 대상 구성에 관계 없이 동일한 SDK 파일 집합을 사용 해야 하는 경우 *CommonConfiguration* 에 파일을 저장할 수 있습니다.

6. *아키텍처* 폴더: x86, X64, ARM, 중립적 아키텍처가 지원 됩니다. Win32는 x 86에 매핑되고 AnyCPU는 중립으로 매핑됩니다.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

*SDKManifest.xml* 파일은 Visual STUDIO에서 SDK를 사용 하는 방법을 설명 합니다. 다음은 이에 대한 예입니다.

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

다음 목록에서는 파일의 요소를 제공 합니다.

1. DisplayName: Visual Studio 용 사용자 인터페이스에서 참조 관리자, 솔루션 탐색기 개체 브라우저 및 기타 위치에 표시 되는 값입니다.

2. ProductFamilyName: 전체 SDK 제품 이름입니다. 예를 들어 [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] sdk의 이름은 "WinJS" 및 "WinJS" 이며,이는 동일한 sdk 제품 제품군 ("WinJS")에 속합니다. 이 특성을 사용 하면 Visual Studio 및 MSBuild에서 해당 연결을 설정할 수 있습니다. 이 특성이 없으면 SDK 이름이 제품군 이름으로 사용 됩니다.

3. FrameworkIdentity: 하나 이상의 Windows 구성 요소 라이브러리에 대 한 종속성을 지정 합니다. 이 특성의 값은 소비 하는 앱의 매니페스트에 배치 됩니다. 이 특성은 Windows 구성 요소 라이브러리에만 적용 됩니다.

4. TargetFramework: 참조 관리자 및 도구 상자에서 사용할 수 있는 Sdk를 지정 합니다. 이것은 세미콜론으로 구분 된 대상 프레임 워크 모니커 목록입니다 (예: ".NET Framework, version = v2.0; .NET Framework, version = v 4.5.1"). 동일한 대상 프레임 워크의 여러 버전을 지정 하는 경우 참조 관리자는 필터링 목적으로 가장 낮은 지정 된 버전을 사용 합니다. 예를 들어 ".NET Framework, version = v2.0; .NET Framework, version = v 4.5.1"이 지정 된 경우 참조 관리자는 ".NET Framework, version = v 2.0"을 사용 합니다. 특정 대상 프레임 워크 프로필을 지정 하는 경우에는 해당 프로필만 참조 관리자에서 필터링 용도로 사용 됩니다. 예를 들어, "Silverlight, version = v 4.0, profile = Appname.windowsphone"이 지정 된 경우 참조 관리자는 Windows Phone 프로필만 필터링 합니다. 전체 Silverlight 4.0 프레임 워크를 대상으로 하는 프로젝트에는 참조 관리자의 SDK가 표시 되지 않습니다.

5. MinVSVersion: 최소 Visual Studio 버전입니다.

6. MaxPlatformVerson: 확장 SDK가 작동 하지 않는 플랫폼 버전을 지정 하려면 최대 대상 플랫폼 버전을 사용 해야 합니다. 예를 들어 Microsoft Visual C++ 런타임 패키지 v 11.0은 Windows 8 프로젝트 에서만 참조 해야 합니다. 따라서 Windows 8 프로젝트의 MaxPlatformVersion은 8.0입니다. 즉, 참조 관리자는 Windows 8.1 프로젝트에 대 한 Microsoft Visual C++ 런타임 패키지를 필터링 하 고, 프로젝트에서 참조 하는 경우 MSBuild에서 오류를 throw 합니다 [!INCLUDE[win81](../debugger/includes/win81_md.md)] . 참고:이 요소는부터 지원 됩니다 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] .

7. AppliesTo: 해당 하는 Visual Studio 프로젝트 형식을 지정 하 여 참조 관리자에서 사용할 수 있는 Sdk를 지정 합니다. 3 개의 값이 인식 됩니다 (WindowsAppContainer, VisualC, VB, CSharp, Windowsappcontainer, JavaScript, 관리 및 네이티브). SDK 작성자는 and ("+ '), or (" &#124; "), not ("! ")을 사용할 수 있습니다. 연산자를 통해 SDK에 적용 되는 프로젝트 형식의 범위를 정확 하 게 지정할 수 있습니다.

    WindowsAppContainer는 앱에 대 한 프로젝트를 식별 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 합니다.

8. SupportPrefer32Bit: 지원 되는 값은 "True" 및 "False"입니다. 기본값은 "True"입니다. 값이 "False"로 설정 되어 있으면 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] SDK를 참조 하는 프로젝트에서 Prefer32Bit를 사용 하도록 설정한 경우 MSBuild는 프로젝트 (또는 데스크톱 프로젝트의 경우 경고)에 대 한 오류를 반환 합니다. Prefer32Bit에 대 한 자세한 내용은 [빌드 페이지, 프로젝트 디자이너 (c #)](../ide/reference/build-page-project-designer-csharp.md) 또는 [컴파일 페이지, 프로젝트 디자이너 (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)를 참조 하세요.

9. SupportedArchitectures: SDK에서 지 원하는 아키텍처의 세미콜론으로 구분 된 목록입니다. 소비 하는 프로젝트의 대상 SDK 아키텍처가 지원 되지 않는 경우 MSBuild에서 경고를 표시 합니다. 이 특성을 지정 하지 않으면 MSBuild는이 유형의 경고를 표시 하지 않습니다.

10. SupportsMultipleVersions:이 특성이 **오류** 또는 **경고**로 설정 된 경우 MSBuild는 동일한 프로젝트가 동일한 SDK 제품군의 여러 버전을 참조할 수 없음을 나타냅니다. 이 특성이 없거나 **허용**으로 설정 되어 있으면 MSBuild는이 유형의 오류 또는 경고를 표시 하지 않습니다.

11. AppX: 디스크의 Windows 구성 요소 라이브러리에 대 한 앱 패키지의 경로를 지정 합니다. 이 값은 로컬 디버깅 중에 Windows 구성 요소 라이브러리의 등록 구성 요소에 전달 됩니다. 파일 이름에 대 한 명명 규칙은 ... * \<Company> \<Product> \<Architecture> \<Configuration> 입니다 \<Version> . appx*. 구성 및 아키텍처는 Windows 구성 요소 라이브러리에 적용 되지 않는 경우 특성 이름 및 특성 값에서 선택 사항입니다. 이 값은 Windows 구성 요소 라이브러리에만 적용 됩니다.

12. CopyRedistToSubDirectory: 앱 패키지 루트 (즉, **앱 패키지 만들기** 마법사에서 선택한 **패키지 위치** )와 런타임 레이아웃 루트를 기준으로 *\redist* 폴더 아래의 파일을 복사할 위치를 지정 합니다. 기본 위치는 앱 패키지 및 **F5** 레이아웃의 루트입니다.

13. DependsOn:이 SDK가 종속 된 sdk를 정의 하는 SDK id 목록입니다. 이 특성은 참조 관리자의 세부 정보 창에 표시 됩니다.

14. MoreInfo: 도움말 및 자세한 정보를 제공 하는 웹 페이지의 URL입니다. 이 값은 참조 관리자의 오른쪽 창에 있는 추가 정보 링크에 사용 됩니다.

15. 등록 형식: 응용 프로그램 매니페스트에서 WinMD 등록을 지정 하며, 해당 구현 DLL이 있는 네이티브 WinMD에 필요 합니다.

16. 파일 참조: 컨트롤을 포함 하거나 네이티브 Winmd 참조에 대해서만 지정 됩니다. 참조에 컨트롤이 포함 되는지 여부를 지정 하는 방법에 대 한 자세한 내용은 아래 [도구 상자 항목의 위치 지정](#ToolboxItems) 을 참조 하세요.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a> 도구 상자 항목의 위치 지정

*SDKManifest.xml* 스키마의 **ToolBoxItems** 요소는 플랫폼과 확장 sdk 둘 다에서 도구 상자 항목의 범주 및 위치를 지정 합니다. 다음 예에서는 다른 위치를 지정 하는 방법을 보여 줍니다. 이는 WinMD 또는 DLL 참조에 적용 됩니다.

1. 도구 상자 기본 범주에 컨트롤을 추가 합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. 특정 범주 이름 아래에 컨트롤을 추가 합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. 특정 범주 이름 아래에 컨트롤을 추가 합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Blend 및 Visual Studio에서 다양 한 범주 이름 아래에 컨트롤을 추가 합니다.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Blend 및 Visual Studio에서 특정 컨트롤을 다르게 열거 합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. 특정 컨트롤을 열거 하 고 Visual Studio 공통 경로 아래 또는 모든 컨트롤 그룹에만 놓습니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. 특정 컨트롤을 열거 하 고 도구 상자에 표시 되지 않고 ChooseItems의 특정 집합만 표시 합니다.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>추가 정보

- [연습: c + +를 사용 하 여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [연습: c # 또는 Visual Basic를 사용 하 여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [프로젝트에서 참조 관리](../ide/managing-references-in-a-project.md)
