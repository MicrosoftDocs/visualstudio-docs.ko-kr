---
title: Csc 작업 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c88e5aaef9262d320cdf61564078246dee46b10
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634268"
---
# <a name="csc-task"></a>Csc 작업

*csc.exe*를 래핑하고 실행( *.exe* 파일), 동적 연결 라이브러리( *.dll* 파일) 또는 코드 모듈( *.netmodule* 파일)을 생성합니다. *csc.exe*에 대한 자세한 내용은 [C# 컴파일러 옵션](/dotnet/csharp/language-reference/compiler-options/index)을 참조하세요.

## <a name="parameters"></a>매개 변수

다음 표에서는 `Csc` 작업의 매개 변수에 대해 설명합니다.

| 매개 변수 | 설명 |
|------------------------------| - |
| `AdditionalLibPaths` | 선택적 `String[]` 매개 변수입니다.<br /><br /> 참조를 검색할 추가 디렉터리를 지정합니다. 자세한 내용은 [-lib(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option)를 참조하세요. |
| `AddModules` | 선택적 `String` 매개 변수입니다.<br /><br /> 이 어셈블리의 일부가 될 모듈을 하나 이상 지정합니다. 자세한 내용은 [-addmodule(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option)을 참조하세요. |
| `AllowUnsafeBlocks` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) 키워드를 사용하는 코드를 컴파일합니다. 자세한 내용은 [-unsafe(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option)를 참조하세요. |
| `ApplicationConfiguration` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리 바인딩 설정을 포함하는 애플리케이션 구성 파일을 지정합니다. |
| `BaseAddress` | 선택적 `String` 매개 변수입니다.<br /><br /> DLL을 로드할 기본 설정 기준 주소를 지정합니다. DLL에 대한 기본 기준 주소는 .NET Framework 공용 언어 런타임에 의해 설정됩니다. 자세한 내용은 [-baseaddress(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option)를 참조하세요. |
| `CheckForOverflowUnderflow` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> 데이터 형식 범위를 오버플로하는 정수 연산이 있는 경우 런타임에 예외가 발생되는지 여부를 지정합니다. 자세한 내용은 [-checked(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option)를 참조하세요. |
| `CodePage` | 선택적 `Int32` 매개 변수입니다.<br /><br /> 컴파일할 때 모든 소스 코드 파일에 사용할 코드 페이지를 지정합니다. 자세한 내용은 [-codepage(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option)를 참조하세요. |
| `DebugType` | 선택적 `String` 매개 변수입니다.<br /><br /> 디버그 형식을 지정합니다. `DebugType`은 `full` 또는 `pdbonly`가 될 수 있습니다. 기본값은 `full`로, 디버거가 실행 중인 프로그램에 연결할 수 있습니다. `pdbonly`를 지정하면 디버거에서 프로그램이 시작되는 경우 소스 코드 디버깅이 가능하지만, 실행 중인 프로그램이 디버거에 연결되는 경우 어셈블러만 표시됩니다.<br /><br /> 이 매개 변수는 `EmitDebugInformation` 매개 변수를 재정의합니다.<br /><br /> 자세한 내용은 [-debug(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)를 참조하세요. |
| `DefineConstants` | 선택적 `String` 매개 변수입니다.<br /><br /> 전처리기 기호를 정의합니다. 자세한 내용은 [-define(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option)을 참조하세요. |
| `DelaySign` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> 어셈블리에 공개 키만 저장하려 경우 `true`를 지정합니다. 완전히 서명된 어셈블리를 만들려는 경우 `false`를 지정합니다.<br /><br /> 이 매개 변수는 `KeyFile` 또는 `KeyContainer` 매개 변수와 함께 사용하지 않는 한 효과가 없습니다.<br /><br /> 자세한 내용은 [-delaysign(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option)을 참조하세요. |
| `Deterministic` | 선택적 `Boolean` 매개 변수입니다.<br/><br/> `true`인 경우 입력이 동일하면 컴파일 간에 이진 콘텐츠가 동일한 어셈블리를 컴파일러에서 출력하도록 합니다.<br/><br/>자세한 내용은 [-deterministic(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option)을 참조하세요. |
| `DisabledWarnings` | 선택적 `String` 매개 변수입니다.<br /><br /> 사용하지 않을 경고 목록을 지정합니다. 자세한 내용은 [-nowarn(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option)을 참조하세요. |
| `DocumentationFile` | 선택적 `String` 매개 변수입니다.<br /><br /> XML 파일에 대해 문서 주석을 처리합니다. 자세한 내용은 [-doc(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)를 참조하세요. |
| `EmitDebugInformation` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 작업에서 디버깅 정보를 생성하여 프로그램 데이터베이스(.pdb) 파일에 저장합니다. `false`인 경우 작업에서 디버그 정보를 내보내지 않습니다. 기본값은 `false`입니다. 자세한 내용은 [-debug(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)를 참조하세요. |
| `ErrorReport` | 선택적 `String` 매개 변수입니다.<br /><br /> Microsoft에 C# 내부 오류를 보고하는 편리한 방법을 제공합니다. 이 매개 변수는 `prompt`, `send` 또는 `none` 값을 가질 수 있습니다. 매개 변수를 `prompt`로 설정한 경우 내부 컴파일러 오류가 발생하면 메시지(프롬프트)가 표시됩니다. 프롬프트를 통해 Microsoft에 버그 보고서를 전자적으로 보낼 수 있습니다. 매개 변수를 `send`로 설정한 경우 버그 보고서가 자동으로 전송됩니다. 매개 변수를 `none`으로 설정한 경우 오류가 컴파일러의 텍스트 출력으로만 보고됩니다. 기본값은 `none`입니다. 자세한 내용은 [-errorreport(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)를 참조하세요. |
| `FileAlignment` | 선택적 `Int32` 매개 변수입니다.<br /><br /> 출력 파일에 있는 섹션의 크기를 지정합니다. 자세한 내용은 [-filealign(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option)을 참조하세요. |
| `GenerateFullPaths` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 컴파일러 출력에서 파일의 절대 경로를 지정합니다. `false`인 경우 파일의 이름을 지정합니다. 기본값은 `false`입니다. 자세한 내용은 [-fullpaths(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option)를 참조하세요. |
| `KeyContainer` | 선택적 `String` 매개 변수입니다.<br /><br /> 암호화 키 컨테이너의 이름을 지정합니다. 자세한 내용은 [-keycontainer(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option)를 참조하세요. |
| `KeyFile` | 선택적 `String` 매개 변수입니다.<br /><br /> 암호화 키를 포함하는 파일 이름을 지정합니다. 자세한 내용은 [-keyfile(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option)을 참조하세요. |
| `LangVersion` | 선택적 `String` 매개 변수입니다.<br /><br /> 사용할 언어의 버전을 지정합니다. 자세한 내용은 [-langversion(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)을 참조하세요. |
| `LinkResources` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 출력 파일에 .NET Framework 리소스에 대한 링크를 만듭니다. 리소스 파일은 출력 파일에 저장되지 않습니다.<br /><br /> 이 매개 변수로 전달된 항목에는 이름이 `LogicalName` 및 `Access`인 선택적 메타데이터 항목이 있을 수 있습니다. `LogicalName`은 `/linkresource` 스위치의 `identifier` 매개 변수에 해당하며, `Access`는 `accessibility-modifier` 매개 변수에 해당합니다. 자세한 내용은 [-linkresource(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option)를 참조하세요. |
| `MainEntryPoint` | 선택적 `String` 매개 변수입니다.<br /><br /> `Main` 메서드의 위치를 지정합니다. 자세한 내용은 [-main(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option)을 참조하세요. |
| `ModuleAssemblyName` | 선택적 `String` 매개 변수입니다.<br /><br /> 이 모듈이 속할 어셈블리의 이름을 지정합니다. |
| `NoConfig` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 *csc.rsp* 파일을 사용하여 컴파일하지 않도록 컴파일러에 지시합니다. 자세한 내용은 [-noconfig(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option)를 참조하세요. |
| `NoLogo` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 컴파일러 배너 정보를 표시하지 않습니다. 자세한 내용은 [-nologo(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option)를 참조하세요. |
| `NoStandardLib` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 전체 시스템 네임스페이스를 정의하는 *mscorlib.dll*을 가져올 수 없습니다. 고유한 시스템 네임스페이스와 개체를 정의하거나 만들려면 이 매개 변수를 사용합니다. 자세한 내용은 [-nostdlib(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option)를 참조하세요. |
| `NoWin32Manifest` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 기본 Win32 매니페스트를 포함하지 않습니다. |
| `Optimize` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 최적화를 사용할 수 있습니다. `false`인 경우 최적화를 사용하지 않습니다. 자세한 내용은 [-optimize(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option)를 참조하세요. |
| `OutputAssembly` | 선택적 `String` 출력 매개 변수입니다.<br /><br /> 출력 파일의 이름을 지정합니다. 자세한 내용은 [-out(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option)을 참조하세요. |
| `OutputRefAssembly` | 선택적 `String` 매개 변수입니다.<br /><br /> 출력 참조 어셈블리 파일의 이름을 지정합니다. 자세한 내용은 [-refout(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option)을 참조하세요. |
| `PdbFile` | 선택적 `String` 매개 변수입니다.<br /><br /> 디버그 정보 파일 이름을 지정합니다. 기본 이름은 확장명이 *.pdb*인 출력 파일 이름입니다. |
| `Platform` | 선택적 `String` 매개 변수입니다.<br /><br /> 출력 파일의 대상으로 프로세서 플랫폼을 지정합니다. 이 매개 변수는 `x86`, `x64` 또는 `anycpu` 값을 가질 수 있습니다. 기본값은 `anycpu`입니다. 자세한 내용은 [-platform(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)을 참조하세요. |
| `References` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 작업에서 지정된 항목의 공용 형식 정보를 현재 프로젝트로 가져옵니다. 자세한 내용은 [-reference(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)를 참조하세요.<br /><br /> 메타데이터 `Aliases`를 원래 "참조" 항목에 추가하여 MSBuild 파일에서 C# 참조 별칭을 지정할 수 있습니다. 예를 들어 다음 Csc 명령줄에서 별칭 “LS1”을 설정하려면<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> 다음과 같이 사용합니다.<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> .NET Framework 리소스를 출력 파일에 포함합니다.<br /><br /> 이 매개 변수로 전달된 항목에는 이름이 `LogicalName` 및 `Access`인 선택적 메타데이터 항목이 있을 수 있습니다. `LogicalName`은 `/resource` 스위치의 `identifier` 매개 변수에 해당하며, `Access`는 `accessibility-modifier` 매개 변수에 해당합니다. 자세한 내용은 [-resource(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)를 참조하세요. |
| `ResponseFiles` | 선택적 `String` 매개 변수입니다.<br /><br /> 이 작업에 대한 명령을 포함하는 지시 파일을 지정합니다. 자세한 내용은 [@(지시 파일 지정)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option)을 참조하세요. |
| `Sources` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> C# 소스 파일을 하나 이상 지정합니다. |
| `TargetType` | 선택적 `String` 매개 변수입니다.<br /><br /> 출력 파일의 파일 형식을 지정합니다. 이 매개 변수는 각각 코드 라이브러리를 만드는 `library`, 콘솔 애플리케이션을 만드는 `exe`, 모듈을 만드는 `module` 또는 Windows 프로그램을 만드는 `winexe`를 값으로 가질 수 있습니다. 기본값은 `library`입니다. 자세한 내용은 [-target(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option)을 참조하세요. |
| `TreatWarningsAsErrors` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 모든 경고를 오류로 처리합니다. 자세한 내용은 [-warnaserror(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)를 참조하세요. |
| `UseHostCompilerIfAvailable` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> 사용 가능한 경우 In Process 컴파일러 개체를 사용하도록 작업에 지시합니다. Visual Studio에서만 사용됩니다. |
| `Utf8Output` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> UTF-8 인코딩을 사용하여 컴파일러 출력을 기록합니다. 자세한 내용은 [-utf8output(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option)을 참조하세요. |
| `WarningLevel` | 선택적 `Int32` 매개 변수입니다.<br /><br /> 컴파일러에서 표시할 경고 수준을 지정합니다. 자세한 내용은 [-warn(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option)을 참조하세요. |
| `WarningsAsErrors` | 선택적 `String` 매개 변수입니다.<br /><br /> 오류로 처리할 경고 목록을 지정합니다. 자세한 내용은 [-warnaserror(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)를 참조하세요.<br /><br /> 이 매개 변수는 `TreatWarningsAsErrors` 매개 변수를 재정의합니다. |
| `WarningsNotAsErrors` | 선택적 `String` 매개 변수입니다.<br /><br /> 오류로 처리하지 않을 경고 목록을 지정합니다. 자세한 내용은 [-warnaserror(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)를 참조하세요.<br /><br /> 이 매개 변수는 `TreatWarningsAsErrors` 매개 변수가 `true`로 설정된 경우에만 유용합니다. |
| `Win32Icon` | 선택적 `String` 매개 변수입니다.<br /><br /> **파일 탐색기**에서 출력 파일을 원하는 모양으로 표시하는 *.ico* 파일을 어셈블리에 삽입합니다. 자세한 내용은 [-win32icon(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)을 참조하세요. |
| `Win32Manifest` | 선택적 `String` 매개 변수입니다.<br /><br /> 포함할 Win32 매니페스트를 지정합니다. |
| `Win32Resource` | 선택적 `String` 매개 변수입니다.<br /><br /> Win32 리소스( *.res*) 파일을 출력 파일에 삽입합니다. 자세한 내용은 [-win32res(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option)를 참조하세요. |

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.ToolTask> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 클래스에서 상속하는 `Microsoft.Build.Tasks.ManagedCompiler` 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [ToolTaskExtension 기본 클래스](../msbuild/tooltaskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 `Csc` 작업을 사용하여 `Compile` 항목 컬렉션의 소스 파일에서 실행 파일을 컴파일합니다.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [작업](../msbuild/msbuild-tasks.md)
