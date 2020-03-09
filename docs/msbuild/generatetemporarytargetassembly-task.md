---
title: GenerateTemporaryTargetAssembly 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69333b87720513244e90c131f052d11099b62e35
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634047"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly 작업

프로젝트에서 하나 이상의 XAML 페이지가 해당 프로젝트에서 로컬로 선언된 형식을 참조할 경우 <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> 작업은 어셈블리를 생성합니다. 생성된 어셈블리는 빌드 프로세스가 완료된 후 또는 빌드 프로세스가 실패하는 경우에 제거됩니다.

## <a name="task-parameters"></a>작업 매개 변수

| 매개 변수 | 설명 |
|--------------------------| - |
| `AssemblyName` | 필수 **String** 매개 변수입니다.<br /><br /> 프로젝트에 대해 생성되었으며, 일시적으로 생성된 대상 어셈블리의 이름이기도 하는 어셈블리에 대한 짧은 이름을 지정합니다. 예를 들어 이름이 *WinExeAssembly.exe*인 Windows 실행 파일을 프로젝트가 생성하는 경우 **AssemblyName** 매개 변수는 **WinExeAssembly** 값을 갖습니다. |
| `CompileTargetName` | 필수 **String** 매개 변수입니다.<br /><br /> 소스 코드 파일에서 어셈블리를 생성하는 데 사용되는 MSBuild 대상의 이름을 지정합니다. **CompileTargetName**의 일반적인 값은 **CoreCompile**입니다. |
| `CompileTypeName` | 필수 **String** 매개 변수입니다.<br /><br /> **CompileTargetName** 매개 변수로 지정된 대상에 의해 수행되는 컴파일 형식을 지정합니다. **CoreCompile** 대상의 경우 이 값은 **Compile**입니다. |
| `CurrentProject` | 필수 **String** 매개 변수입니다.<br /><br /> 임시 대상 어셈블리를 필요로 하는 프로젝트에 대한 MSBuild 프로젝트 파일의 전체 경로를 지정합니다. |
| `GeneratedCodeFiles` | 선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) 작업에 의해 생성된 언어별 관리 코드 파일의 목록을 지정합니다. |
| `IntermediateOutputPath` | 필수 **String** 매개 변수입니다.<br /><br /> 임시 대상 어셈블리가 생성되는 디렉터리를 지정합니다. |
| `MSBuildBinPath` | 필수 **String** 매개 변수입니다.<br /><br /> 임시 대상 어셈블리를 컴파일하는 데 필요한 *MSBuild.exe*의 위치를 지정합니다. |
| `ReferencePath` | 선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> 임시 대상 어셈블리로 컴파일되는 형식에 의해 참조되는 어셈블리 목록을 경로 및 파일 이름별로 지정합니다. |
| `ReferencePathTypeName` | 필수 **String** 매개 변수입니다.<br /><br /> 어셈블리 참조의 목록(**ReferencePath**)을 지정하는 컴파일 대상(**CompileTargetName**) 매개 변수에 사용되는 매개 변수를 지정합니다. 적절한 값은 **ReferencePath**입니다. |

## <a name="remarks"></a>설명

[MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)에 의해 실행되는 첫 번째 마크업 컴파일 패스는 XAML 파일을 이진 형식으로 컴파일합니다. 결과적으로 컴파일러에는 XAML 파일에서 사용되는 형식을 포함하는 참조된 어셈블리 목록이 필요합니다. 그러나 XAML 파일이 동일한 프로젝트에 정의된 형식을 사용하는 경우 프로젝트가 빌드될 때까지 해당 프로젝트의 해당 어셈블리는 만들어지지 않습니다. 따라서 첫 번째 마크업 컴파일 패스 동안 어셈블리 참조가 제공될 수 없습니다.

대신 **MarkupCompilePass1**는 동일한 프로젝트의 형식에 대한 참조를 포함하는 XAML 파일의 변환을 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)에 의해 실행되는 두 번째 마크업 컴파일 패스로 연기합니다. **MarkupCompilePass2**가 실행되기 전에 임시 어셈블리가 생성됩니다. 이 어셈블리에는 해당 마크업 컴파일 패스가 지연되는 XAML 파일에서 사용되는 형식이 포함됩니다. 지연된 컴파일 XAML 파일이 이진 형식으로 변환될 수 있도록 하기 위해 생성된 어셈블리에 대한 참조가 **MarkupCompilePass2** 실행 시에 제공됩니다.

## <a name="example"></a>예제

다음 예제에서는 *Page1.xaml*에 동일한 프로젝트에 있는 형식에 대한 참조가 포함되므로 임시 어셈블리를 생성합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GenerateTemporaryTargetAssemblyTask">
    <GenerateTemporaryTargetAssembly
      AssemblyName="WPFMSBuildSample"
      CompileTargetName="CoreCompile"
      CompileTypeName="Compile"
      CurrentProject="FullBuild.proj"
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"
      IntermediateOutputPath=".\obj\debug\"
      MSBuildBinPath="$(MSBuildBinPath)"
      ReferencePathTypeName="ReferencePath"/>
  </Target>
</Project>
```

## <a name="see-also"></a>참조

- [WPF MSBuild 참조](../msbuild/wpf-msbuild-reference.md)
- [작업 참조](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
- [WPF 애플리케이션 빌드(WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 브라우저 애플리케이션 개요](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
