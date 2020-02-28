---
title: MarkupCompilePass1 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d72b0a63235de4cc93e97f6e85dc5728e5ebbf43
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579674"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 작업

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 작업은 지역화할 수 없는 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 프로젝트 파일을 컴파일된 이진 형식 파일로 변환합니다.

## <a name="task-parameters"></a>작업 매개 변수

| 매개 변수 | 설명 |
| - | - |
| `AllGeneratedFiles` | 선택적 **ITaskItem** 출력 매개 변수입니다.<br /><br /> <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 작업에 의해 생성되는 파일의 전체 목록을 포함합니다. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | 선택적 **Boolean** 매개 변수입니다.<br /><br /> 별도의 <xref:System.AppDomain>에서 작업을 실행할지 여부를 지정합니다. 이 매개 변수가 **false**를 반환하는 경우 작업은 [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]와 동일한 <xref:System.AppDomain>에서 더 빠르게 실행됩니다. 이 매개 변수가 **true**를 반환하는 경우 작업은 [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)]에서 분리된 또 다른 <xref:System.AppDomain>에서 실행되며 더 느리게 실행됩니다. |
| `ApplicationMarkup` | 선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> 애플리케이션 정의 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일의 이름을 지정합니다. |
| `AssembliesGeneratedDuringBuild` | 선택적 **String[]** 매개 변수입니다.<br /><br /> 빌드 프로세스 중에 변경되는 어셈블리에 대한 참조를 지정합니다. 예를 들어 Visual Studio 솔루션에는 다른 프로젝트의 컴파일된 출력을 참조하는 하나의 프로젝트가 포함될 수 있습니다. 이 경우 두 번째 프로젝트의 컴파일된 출력을 **AssembliesGeneratedDuringBuild** 매개 변수에 추가할 수 있습니다.<br /><br /> 참고: **AssembliesGeneratedDuringBuild** 매개 변수는 빌드 솔루션에 의해 생성되는 어셈블리의 전체 집합에 대한 참조를 포함해야 합니다. |
| `AssemblyName` | 필수 **문자열** 매개 변수입니다.<br /><br /> 프로젝트에 대해 생성되는 어셈블리의 약식 이름을 지정합니다. 예를 들어 프로젝트가 이름이 *WinExeAssembly.exe*인 [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 실행 파일을 생성하는 경우 **AssemblyName** 매개 변수는 **WinExeAssembly** 값을 갖습니다. |
| `AssemblyPublicKeyToken` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 어셈블리의 공개 키 토큰을 지정합니다. |
| `AssemblyVersion` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 어셈블리의 버전 번호를 지정합니다. |
| `ContentFiles` | 선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> 느슨한 콘텐츠 파일의 목록을 지정합니다. |
| `DefineConstants` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 현재 값 **DefineConstants**가 유지되도록 지정합니다. 대상 어셈블리 생성에 영향을 미칩니다. 이 매개 변수가 변경되면 대상 어셈블리의 공용 API를 변경할 수 있으며 로컬 형식을 참조하는 [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] 파일의 컴파일에 영향을 줄 수 있습니다. |
| `ExtraBuildControlFiles` | 선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 작업이 다시 실행될 때 다시 빌드가 트리거되는지 여부를 제어하는 파일의 목록을 지정합니다. 이러한 파일 중 하나가 변경되면 다시 빌드가 트리거됩니다. |
| `GeneratedBamlFiles` | 선택적 **ITaskItem** 출력 매개 변수입니다.<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 이진 형식으로 생성된 파일 목록을 포함합니다. |
| `GeneratedCodeFiles` | 선택적 **ITaskItem** 출력 매개 변수입니다.<br /><br /> 생성된 관리 코드 파일의 목록을 포함합니다. |
| `GeneratedLocalizationFiles` | 선택적 **ITaskItem** 출력 매개 변수입니다.<br /><br /> 지역화할 수 있는 각 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 대해 생성된 지역화 파일의 목록을 포함합니다. |
| `HostInBrowser` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 생성된 어셈블리가 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]인지 여부를 지정합니다. 유효한 옵션은 **true** 및 **false**입니다. **true**이면 브라우저 호스팅을 지원하기 위한 코드가 생성됩니다. |
| `KnownReferencePaths` | 선택적 **String[]** 매개 변수입니다.<br /><br /> 빌드 프로세스 중에 변경되지 않는 어셈블리에 대한 참조를 지정합니다. [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] 설치 디렉터리 등에 있는 어셈블리를 포함합니다. |
| `Language` | 필수 **String** 매개 변수입니다.<br /><br /> 컴파일러가 지원하는 관리되는 언어를 지정합니다. 유효한 옵션은 **C#** , **VB**, **JScript** 및 **C++** 입니다. |
| `LanguageSourceExtension` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 생성된 관리되는 코드 파일의 확장에 추가되는 확장명을 지정합니다.<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> **LanguageSourceExtension** 매개 변수가 특정 값으로 설정되지 않으면 언어에 대한 기본 소스 파일 이름 확장명이 사용됩니다. 즉, [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)]의 경우 *.vb*이고, [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]의 경우 *.csharp*입니다. |
| `LocalizationDirectivesToLocFile` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 각 소스 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 대한 지역화 정보를 생성하는 방법을 지정입니다. 유효한 옵션은 **None**, **CommentsOnly** 및 **All**입니다. |
| `OutputPath` | 필수 **String** 매개 변수입니다.<br /><br /> 생성된 관리 코드 파일 및 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 이진 형식 파일이 생성되는 디렉터리를 지정합니다. |
| `OutputType` | 필수 **String** 매개 변수입니다.<br /><br /> 프로젝트에서 생성되는 어셈블리의 형식을 지정합니다. 유효한 옵션은 **winexe**, **exe**, **library** 및 **netmodule**입니다. |
| `PageMarkup` | 선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> 처리할 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일 목록을 지정합니다. |
| `References` | 선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에서 사용되는 형식을 포함하는 어셈블리에 대한 파일의 참조 목록을 지정합니다. |
| `RequirePass2ForMainAssembly` | 선택적 **Boolean** 출력 매개 변수입니다.<br /><br /> 프로젝트에 주 어셈블리에 포함되는 로컬 형식을 참조하는 지역화할 수 없는 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일이 포함되는지 여부를 나타냅니다. |
| `RequirePass2ForSatelliteAssembly` | 선택적 **Boolean** 출력 매개 변수입니다.<br /><br /> 프로젝트에 주 어셈블리에 포함되는 로컬 형식을 참조하는 지역화할 수 있는 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일이 포함되는지 여부를 나타냅니다. |
| `RootNamespace` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 프로젝트 내에 있는 클래스에 대한 루트 네임스페이스를 지정합니다. **RootNamespace**는 해당 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 `x:Class` 특성이 포함되어 있지 않을 때 생성된 관리 코드 파일의 기본 네임스페이스로도 사용됩니다. |
| `SourceCodeFiles` | 선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> 현재 프로젝트에 대한 코드 파일의 목록을 지정합니다. 이 목록에 생성된 언어별 관리 코드 파일은 포함되지 않습니다. |
| `UICulture` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 생성된 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 이진 형식 파일이 포함되는 UI 문화권에 대한 위성 어셈블리를 지정합니다. **UICulture**가 설정되지 않은 경우 생성된 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 이진 형식 파일은 주 어셈블리에 포함됩니다. |
| `XAMLDebuggingInformation` | 선택적 **Boolean** 매개 변수입니다.<br /><br /> **true**이면 디버깅에 도움을 주기 위해 진단 정보가 생성되고 컴파일된 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]에 포함됩니다. |

## <a name="remarks"></a>설명

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 작업은 일반적으로 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]를 이진 형식으로 컴파일한 후 코드 파일을 생성합니다. [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 같은 프로젝트에 정의된 형식에 대한 참조가 포함되면 이진 형식에 대한 컴파일이 **MarkupCompilePass1**에 의해 두 번째 태그 컴파일 패스(**MarkupCompilePass2**)로 연기됩니다. 이러한 파일은 참조된 로컬로 정의된 형식이 컴파일될 때까지 기다려야 하므로 컴파일이 연기되어야 합니다. 그러나 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 `x:Class` 특성이 있으면 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>은 언어별 코드 파일을 생성합니다.

[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일은 `x:Uid` 특성을 사용하는 요소가 포함된 경우 지역화가 가능합니다.

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일은 `clr-namespace` 값을 사용하여 현재 프로젝트의 네임스페이스를 참조하는 [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)] 네임스페이스를 선언할 때 로컬로 정의된 형식을 참조합니다.

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

지역화가 가능하거나 로컬로 정의된 형식을 참조하는 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일이 있는 경우 두 번째 태그 컴파일 패스가 필요합니다. 이를 위해 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)와 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)가 차례로 실행되어야 합니다.

## <a name="example"></a>예제

다음 예제에서는 3개의 *Page* [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일을 이진 형식 파일로 변환하는 방법을 보여줍니다. *Page1*에는 `Class1` 형식에 대한 참조가 포함됩니다. 이 형식은 프로젝트의 루트 네임스페이스에 있으므로 이 태그 컴파일 패스에서 이진 형식 파일로 변환되지 않습니다. 대신 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)가 실행된 다음 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)가 실행됩니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>참조

- [WPF MSBuild 참조](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild 작업 참조](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [MSBuild 작업 참조](../msbuild/msbuild-task-reference.md)
- [WPF 애플리케이션 빌드(WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 브라우저 애플리케이션 개요](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)