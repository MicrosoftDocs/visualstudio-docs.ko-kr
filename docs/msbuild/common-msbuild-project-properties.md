---
title: 일반적인 MSBuild 프로젝트 속성 | Microsoft Docs
ms.date: 01/18/2018
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7502644c9820b47149acb4a9b8a749bec70551e4
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180430"
---
# <a name="common-msbuild-project-properties"></a>일반적인 MSBuild 프로젝트 속성

다음 표에서는 Visual Studio 프로젝트 파일에 정의되거나 MSBuild가 제공하는 *.targets* 파일에 포함된 자주 사용하는 속성을 보여 줍니다.

 Visual Studio의 프로젝트 파일( *.csproj*, *.vbproj*, *.vcxproj* 등)은 IDE를 사용하여 프로젝트를 빌드할 때 실행하는 MSBuild XML 코드를 포함합니다. 일반적으로 프로젝트에서는 하나 이상의 *.targets* 파일을 가져와서 빌드 프로세스를 정의합니다. 자세한 내용은 [MSBuild .targets 파일](../msbuild/msbuild-dot-targets-files.md)을 참조하세요.

## <a name="list-of-common-properties-and-parameters"></a>공용 속성 및 매개 변수 목록

| 속성 또는 매개 변수 이름 | 설명 |
|------------------------------------| - |
| AdditionalLibPaths | 컴파일러에서 참조 어셈블리를 조회해야 하는 추가 폴더를 지정합니다. |
| AddModules | 컴파일러에서 지정된 파일의 모든 형식 정보를 컴파일하고 있는 프로젝트에 사용할 수 있도록 합니다. 이 속성은 `/addModules` 컴파일러 스위치와 동일합니다. |
| ALToolPath | *AL.exe*를 찾을 수 있는 경로입니다. 이 속성은 다른 버전의 *AL.exe*를 사용으로 설정하기 위해 현재 버전을 재정의합니다. |
| ApplicationIcon | Win32 아이콘으로 포함하기 위해 컴파일러에 전달할 *.ico* 아이콘 파일입니다. 이 속성은 `/win32icon` 컴파일러 스위치와 동일합니다. |
| ApplicationManifest | 외부 UAC(사용자 계정 컨트롤) 매니페스트 정보를 생성하는 데 사용되는 파일의 경로를 지정합니다. Windows Vista를 대상으로 하는 Visual Studio 프로젝트에만 적용됩니다.<br /><br /> 대부분의 경우 매니페스트는 포함되어 있지만 등록이 필요 없는 COM 또는 ClickOnce 배포를 사용할 경우 매니페스트가 애플리케이션 어셈블리와 함께 설치되는 외부 파일일 수 있습니다. 자세한 내용은 이 항목에서 NoWin32Manifest 속성을 참조하십시오. |
| AssemblyOriginatorKeyFile | 어셈블리를 서명하는 데 사용되는 파일( *.snk* 또는 *.pfx*) 및 [ResolveKeySource 작업](../msbuild/resolvekeysource-task.md)으로 전달되어 어셈블리를 서명하는 데 사용되는 실제 키를 생성하는 파일을 지정합니다. |
| AssemblySearchPaths | 빌드 시간 참조 어셈블리 확인 동안 검색할 위치의 목록입니다. 앞에 있는 경로가 뒤에 있는 항목보다 우선하므로 이 목록에 경로가 표시되는 순서는 중요합니다. |
| AssemblyName | 프로젝트가 빌드된 후의 마지막 출력 어셈블리 이름입니다. |
| BaseAddress | 주 출력 어셈블리의 기준 주소를 지정합니다. 이 속성은 `/baseaddress` 컴파일러 스위치와 동일합니다. |
| BaseIntermediateOutputPath | 모든 구성 관련 중간 출력 폴더가 만들어지는 최상위 폴더입니다. 기본값은 `obj\`입니다. 코드 예: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | 출력 파일의 기본 경로를 지정합니다. 설정되어 있으면 MSBuild는 `OutputPath = $(BaseOutputPath)\$(Configuration)\`을 사용합니다. 구문 예: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Multi-Proc MSBuild가 사용될 때 프로젝트 참조를 병렬로 빌드 또는 정리할지 여부를 나타내는 부울 값입니다. 기본값은 `true`이며, 시스템에 다중 코어 또는 프로세서가 있을 경우 프로젝트가 병렬로 빌드됨을 나타냅니다. |
| BuildProjectReferences | MSBuild에서 프로젝트 참조를 빌드할지 여부를 나타내는 부울 값입니다. Visual Studio IDE(통합 개발 환경)에서 프로젝트를 빌드하는 경우 자동으로 `false`로 설정되고, 그렇지 않으면 `true`로 설정됩니다. 참조된 프로젝트가 최신 상태인지 확인할 필요가 없도록 명령줄에 `-p:BuildProjectReferences=false`를 지정할 수 있습니다. |
| CleanFile | "정리 캐시"로 사용할 파일의 이름입니다. 정리 캐시는 생성 파일 중 정리 작업 시 삭제할 파일의 목록입니다. 이 파일은 빌드 프로세스에 의해 중간 출력 경로에 저장됩니다.<br /><br /> 이 속성은 경로 정보가 없는 파일 이름만 지정합니다. |
| CodePage | 컴파일할 때 모든 소스 코드 파일에 사용할 코드 페이지를 지정합니다. 이 속성은 `/codepage` 컴파일러 스위치와 동일합니다. |
| CompilerResponseFile | 컴파일러 작업에 전달할 수 있는 선택적 지시 파일입니다. |
| Configuration | 빌드하고 있는 구성으로, "디버그" 또는 "릴리스"입니다. |
| CscToolPath | C# 컴파일러인 *csc.exe*의 경로입니다. |
| CustomBeforeMicrosoftCommonTargets | 공통 대상을 가져오기 전에 자동으로 가져올 프로젝트 파일 또는 대상 파일의 이름입니다. |
| DebugSymbols | 빌드 시 기호의 생성 여부를 나타내는 부울 값입니다.<br /><br /> 명령줄에서 **-p:DebugSymbols=false**를 설정하면 프로그램 데이터베이스( *.pdb*) 기호 파일이 생성되지 않습니다. |
| DebugType | 생성할 디버그 정보의 수준을 정의합니다. 유효한 값은 “full”, “pdbonly”, “portable”, “embedded” 및 “none”입니다. |
| DefineConstants | 조건부 컴파일러 상수를 정의합니다. 기호/값 쌍은 세미콜론으로 구분되고 다음 구문을 사용하여 지정됩니다.<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> 이 속성은 `/define` 컴파일러 스위치와 동일합니다. |
| DefineDebug | DEBUG 상수를 정의할지 여부를 나타내는 부울 값입니다. |
| DefineTrace | TRACE 상수를 정의할지 여부를 나타내는 부울 값입니다. |
| DelaySign | 어셈블리에 전체 서명하는 대신 어셈블리 서명을 연기할지 여부를 나타내는 부울 값입니다. |
| 명확함 | 컴파일러가 동일한 입력에 대해 동일한 어셈블리를 생성해야 하는지를 나타내는 부울 값입니다. 이 매개 변수는 *vbc.exe* 및 *csc.exe* 컴파일러의 `/deterministic` 스위치에 해당합니다. |
| DisabledWarnings | 지정한 경고를 표시하지 않습니다. 경고 식별자의 숫자 부분만 지정해야 합니다. 경고가 여러 개인 경우 세미콜론으로 구분할 수 있습니다. 이 매개 변수는 *vbc.exe* 컴파일러의 `/nowarn` 스위치에 해당합니다. |
| DisableFastUpToDateCheck | Visual Studio에만 적용되는 부울 값입니다. Visual Studio 빌드 관리자는 FastUpToDateCheck 프로세스를 사용하여 프로젝트를 최신 상태로 다시 빌드해야 하는지 여부를 확인합니다. 확인할 때 MSBuild를 사용하는 것보다 이 프로세스가 더 빠릅니다. DisableFastUpToDateCheck 속성을 `true`로 설정하면 Visual Studio 빌드 관리자를 사용하지 않고 대신 MSBuild를 사용하여 프로젝트가 최신 상태인지 여부를 확인할 수 있습니다. |
| DocumentationFile | XML 문서 파일로 생성된 파일의 이름입니다. 이 이름에는 파일 이름만 포함되고 경로 정보는 포함되지 않습니다. |
| ErrorReport | 컴파일러 작업에서 내부 컴파일러 오류를 보고하는 방식을 지정합니다. 유효한 값은 "prompt", "send" 또는 "none"입니다. 이 속성은 `/errorreport` 컴파일러 스위치와 동일합니다. |
| ExcludeDeploymentUrl | [GenerateDeploymentManifest 작업](../msbuild/generatedeploymentmanifest-task.md)에서는 프로젝트 파일에 다음 요소가 하나라도 포함된 경우 배포 매니페스트에 deploymentProvider 태그를 추가합니다.<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> 그러나 ExcludeDeploymentUrl을 사용하면 위의 URL이 지정되더라도 deploymentProvider 태그가 배포 매니페스트에 추가되지 않습니다. 이렇게 하려면 프로젝트 파일에 다음 속성을 추가합니다.<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**참고:**  ExcludeDeploymentUrl은 Visual Studio IDE에 노출되지 않으며 프로젝트 파일을 수동으로만 편집하여 설정할 수 있습니다. 이 속성을 설정해도 Visual Studio 내의 게시에는 영향을 주지 않습니다. 즉, deploymentProvider 태그는 PublishUrl로 지정된 URL에 계속 추가됩니다. |
| FileAlignment | 출력 파일의 섹션에 맞출 위치(바이트)를 지정합니다. 올바른 값은 512, 1024, 2048, 4096, 8192입니다. 이 속성은 `/filealignment` 컴파일러 스위치와 동일합니다. |
| FrameworkPathOverride | *mscorlib.dll* 및 *microsoft.visualbasic.dll*의 위치를 지정합니다. 이 매개 변수는 *vbc.exe* 컴파일러의 `/sdkpath` 스위치와 동일합니다. |
| GenerateDocumentation | (C#, Visual Basic) 빌드 시 문서의 생성 여부를 나타내는 부울 매개 변수입니다. `true`이면 빌드 시 문서 정보를 생성하여 이 정보를 빌드 작업에서 만든 실행 파일이나 라이브러리의 이름과 함께 *.xml* 파일에 배치합니다. |
| GenerateFullPaths | (C#) [-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) 컴파일러 옵션을 사용하여 출력의 파일 이름에 대한 전체 경로를 생성합니다. |
| GenerateSerializationAssemblies | *SGen.exe*에서 XML 직렬화 어셈블리를 생성할지 여부를 표시하며 on, auto 또는 off로 설정할 수 있습니다. 이 속성은 .NET Framework만을 대상으로 하는 어셈블리에 사용됩니다. .NET 표준 또는 .NET Core 어셈블리에 대한 XML 직렬화 어셈블리를 생성하려면 *Microsoft.XmlSerializer.Generator* NuGet 패키지를 참조하세요. |
| IntermediateOutputPath | 경로가 지정되지 않은 경우 `BaseIntermediateOutputPath`에서 파생된 것과 같은 전체 중간 출력 경로입니다. 예를 들어 *\obj\debug\\* 입니다. |
| KeyContainerName | 강력한 이름 키 컨테이너의 이름입니다. |
| KeyOriginatorFile | 강력한 이름 키 파일의 이름입니다. |
| ModuleAssemblyName | 컴파일된 모듈이 통합되어야 하는 어셈블리의 이름입니다. 이 속성은 `/moduleassemblyname` 컴파일러 스위치와 동일합니다. |
| MSBuildProjectExtensionsPath | 프로젝트 확장명이 있는 경로를 지정합니다. 기본적으로 `BaseIntermediateOutputPath`와 동일한 값을 사용합니다. |
| NoLogo | 컴파일러 로고를 해제할지 여부를 나타내는 부울 값입니다. 이 속성은 `/nologo` 컴파일러 스위치와 동일합니다. |
| NoStdLib | 표준 라이브러리(*mscorlib.dll*)를 참조하지 않을지 여부를 나타내는 부울 값입니다. 기본값은 `false`입니다. |
| NoVBRuntimeReference | Visual Basic 런타임(*Microsoft.VisualBasic.dll*)이 프로젝트에 참조로 포함되어야 하는지 여부를 나타내는 부울 값입니다. |
| NoWin32Manifest | 애플리케이션의 실행 파일에 UAC(사용자 계정 컨트롤) 매니페스트 정보를 포함할지 여부를 나타내는 부울 값입니다. Windows Vista를 대상으로 하는 Visual Studio 프로젝트에만 적용됩니다. ClickOnce 및 등록이 필요 없는 COM을 사용하여 배포된 프로젝트에서는 이 요소가 무시됩니다. `False`(기본값)는 애플리케이션의 실행 파일에 UAC(사용자 계정 컨트롤) 매니페스트 정보를 포함할지 여부를 지정합니다. `True`는 UAC 매니페스트 정보가 포함되지 않음을 지정합니다.<br /><br /> 이 속성은 Windows Vista를 대상으로 하는 Visual Studio 프로젝트에만 적용됩니다. ClickOnce 및 등록이 필요 없는 COM을 사용하여 배포된 프로젝트에서는 이 속성이 무시됩니다.<br /><br /> Visual Studio에서 애플리케이션의 실행 파일에 매니페스트 정보를 포함하지 않으려는 경우에만 NoWin32Manifest를 추가해야 합니다. 이 프로세스를 *가상화*라고 합니다. 가상화를 사용하려면 다음과 같이 `<ApplicationManifest>`와 `<NoWin32Manifest>`를 함께 설정합니다.<br /><br /> - Visual Basic 프로젝트의 경우 `<ApplicationManifest>` 노드를 제거합니다. (Visual Basic 프로젝트에서는 `<ApplicationManifest>` 노드가 있으면 `<NoWin32Manifest>`가 무시됩니다.)<br />- C# 프로젝트의 경우 `<ApplicationManifest>`를 `False`로, `<NoWin32Manifest>`를 `True`로 설정합니다. (C# 프로젝트에서는 `<ApplicationManifest>`가 `<NoWin32Manifest>`를 재정의합니다.)<br /> 이 속성은 *vbc.exe*의 `/nowin32manifest` 컴파일러 스위치와 동일합니다. |
| Optimize | `true`로 설정하면 컴파일러 최적화를 사용으로 설정하는 부울 값입니다. 이 속성은 `/optimize` 컴파일러 스위치와 동일합니다. |
| OptionCompare | 문자열 비교 방법을 지정합니다. 유효한 값은 "binary" 또는 "text"입니다. 이 속성은 *vbc.exe*의 `/optioncompare` 컴파일러 스위치와 동일합니다. |
| OptionExplicit | `true`로 설정하면 소스 코드에서 변수를 명시적으로 선언해야 하는 부울 값입니다. 이 속성은 `/optionexplicit` 컴파일러 스위치와 동일합니다. |
| OptionInfer | `true`로 설정하면 변수의 형식 유추를 사용으로 설정하는 부울 값입니다. 이 속성은 `/optioninfer` 컴파일러 스위치와 동일합니다. |
| OptionStrict | `true`로 설정하면 빌드 작업에서 엄격한 형식 의미를 적용하여 암시적 형식 변환을 제한하게 하는 부울 값입니다. 이 속성은 *vbc.exe* 컴파일러의 `/optionstrict` 스위치와 동일합니다. |
| OutDir | 프로젝트 또는 솔루션의 최종 출력 위치를 나타냅니다. 솔루션을 빌드하는 경우 OutDir를 사용하여 한 위치에서 여러 프로젝트 출력을 수집할 수 있습니다. 또한 OutDir는 참조를 확인하는 데 사용되는 AssemblySearchPaths에 포함됩니다. 예를 들어 *bin\Debug*입니다. |
| OutputPath | 프로젝트 디렉터리에 상대적인 출력 디렉터리 경로(예: *bin\Debug*)를 지정합니다. |
| OutputType | 출력 파일의 파일 형식을 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   Library. 코드 라이브러리를 만듭니다. 기본값입니다.<br />-   Exe. 콘솔 애플리케이션을 만듭니다.<br />-   Module. 모듈을 만듭니다.<br />-   Winexe. Windows 기반 프로그램을 만듭니다.<br /><br /> 이 속성은 *vbc.exe* 컴파일러의 `/target` 스위치와 동일합니다. |
| OverwriteReadOnlyFiles | 빌드에서 읽기 전용 파일을 덮어쓸지 아니면 오류를 트리거할지 여부를 나타내는 부울 값입니다. |
| PathMap | 실제 경로를 컴파일러에서 출력되는 소스 경로 이름에 매핑하는 방법을 지정합니다. 이 속성은 *csc.exe* 컴파일러의 `/pathmap` 스위치와 동일합니다. |
| PdbFile | 내보낼 *.pdb* 파일의 파일 이름입니다. 이 속성은 *csc.exe* 컴파일러의 `/pdb` 스위치와 동일합니다. |
| 플랫폼 | 빌드하고 있는 운영 체제입니다. 유효한 값은 "Any CPU", "x86" 및 "x64"입니다. |
| ProcessorArchitecture | 어셈블리 참조를 확인할 때 사용되는 프로세서 아키텍처입니다. 유효한 값은 "msil", "x86", "amd64" 또는 "ia64"입니다. |
| ProduceOnlyReferenceAssembly | 컴파일러에 컴파일된 코드가 아닌 참조 어셈블리만 내보내도록 지시하는 부울 값입니다. `ProduceReferenceAssembly`와 함께 사용할 수 없습니다.  이 속성은 *vbc.exe* 및 *csc.exe* 컴파일러의 `/refonly` 스위치에 해당합니다. |
| ProduceReferenceAssembly | 부울 값으로, `true`로 설정하면 현재 어셈블리에 대한 [참조 어셈블리](/dotnet/standard/assembly/reference-assemblies)를 생성합니다. 이 기능을 사용할 경우 `Deterministic`이 `true`여야 합니다. 이 속성은 *vbc.exe* 및 *csc.exe* 컴파일러의 `/refout` 스위치에 해당합니다. |
| RemoveIntegerChecks | 정수 오버플로 오류 검사를 비활성화할지 여부를 나타내는 부울 값입니다. 기본값은 `false`입니다. 이 속성은 *vbc.exe* 컴파일러의 `/removeintchecks` 스위치와 동일합니다. |
| RootNamespace | 포함 리소스의 이름을 지정할 때 사용할 루트 네임스페이스입니다. 이 네임스페이스는 포함 리소스 매니페스트 이름의 일부입니다. |
| Satellite_AlgorithmId | 위성 어셈블리를 만들 때 사용할 *AL.exe* 해시 알고리즘의 ID입니다. |
| Satellite_BaseAddress | `CreateSatelliteAssemblies` 대상을 사용하여 문화권별 위성 어셈블리를 빌드할 때 사용할 기준 주소입니다. |
| Satellite_CompanyName | 위성 어셈블리 생성 시 *AL.exe*에 전달할 회사 이름입니다. |
| Satellite_Configuration | 위성 어셈블리 생성 시 *AL.exe*에 전달할 구성 이름입니다. |
| Satellite_Description | 위성 어셈블리 생성 시 *AL.exe*에 전달할 설명 텍스트입니다. |
| Satellite_EvidenceFile | 리소스 이름이 "Security.Evidence"인 위성 어셈블리에 지정된 파일을 포함합니다. |
| Satellite_FileVersion | 위성 어셈블리의 File Version 필드에 대한 문자열을 지정합니다. |
| Satellite_Flags | 위성 어셈블리의 Flags 필드에 대한 값을 지정합니다. |
| Satellite_GenerateFullPaths | 빌드 작업에서 오류 메시지에 보고되는 모든 파일에 절대 경로를 사용하도록 합니다. |
| Satellite_LinkResource | 지정한 리소스 파일을 위성 어셈블리에 링크합니다. |
| Satellite_MainEntryPoint | 위성 어셈블리 생성 시 모듈이 실행 파일로 변환될 때 진입점으로 사용할 메서드의 정규화된 이름(즉, class.method)을 지정합니다. |
| Satellite_ProductName | 위성 어셈블리의 Product 필드에 대한 문자열을 지정합니다. |
| Satellite_ProductVersion | 위성 어셈블리의 ProductVersion 필드에 대한 문자열을 지정합니다. |
| Satellite_TargetType | 위성 어셈블리 출력 파일의 파일 형식을 "library", "exe" 또는 "win"으로 지정합니다. 기본값은 "library"입니다. |
| Satellite_Title | 위성 어셈블리의 Title 필드에 대한 문자열을 지정합니다. |
| Satellite_Trademark | 위성 어셈블리의 Trademark 필드에 대한 문자열을 지정합니다. |
| Satellite_Version | 위성 어셈블리의 버전 정보를 지정합니다. |
| Satellite_Win32Icon | 위성 어셈블리에 *.ico* 아이콘 파일을 삽입합니다. |
| Satellite_Win32Resource | 위성 어셈블리에 Win32 리소스( *.res* 파일)를 삽입합니다. |
| SGenToolPath | 현재 버전의 *SGen.exe*를 재정의할 때 *SGen.exe*를 구할 수 있는 위치를 나타내는 선택적 도구 경로입니다. 이 속성은 .NET Framework에만 사용됩니다.|
| SGenUseProxyTypes | *SGen.exe*에서 프록시 형식을 생성해야 하는지 여부를 나타내는 부울 값입니다. *GenerateSerializationAssemblies*를 on으로 설정했으며 .NET Framework만 대상으로 할 경우에만 적용됩니다.<br /><br /> SGen 대상은 이 속성을 사용하여 UseProxyTypes 플래그를 설정합니다. 이 속성은 기본적으로 true로 설정되어 있으며 이를 변경할 UI가 없습니다. 웹 서비스가 아닌 형식에 대해 serialization 어셈블리를 생성하려면 이 속성을 프로젝트 파일에 추가하고 *Microsoft.Common.Targets* 또는 *C#/VB.targets*를 가져오기 전에 false로 설정합니다. |
| SkipInvalidConfigurations | `true`이면 잘못된 플랫폼 및 구성 조합에 대해 경고를 생성하지만 빌드가 실패하지 않고, `false`이거나 정의되지 않은 경우(기본값) 오류를 생성합니다. |
| StartupObject | Main 메서드 또는 Sub Main 프로시저가 포함된 클래스나 모듈을 지정합니다. 이 속성은 `/main` 컴파일러 스위치와 동일합니다. |
| SubsystemVersion | 생성된 실행 파일이 사용할 수 있는 하위 시스템의 최소 버전을 지정합니다. 이 속성은 `/subsystemversion` 컴파일러 스위치와 동일합니다. 이 속성의 기본값에 대한 자세한 내용은 [/subsystemversion(Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) 또는 [/subsystemversion(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option)을 참조하세요. |
| TargetCompactFramework | 빌드하고 있는 애플리케이션을 실행하는 데 필요한 .NET Compact Framework의 버전입니다. 이를 지정하면 다른 경우에는 참조할 수 없는 특정 프레임워크 어셈블리를 참조할 수 있습니다. |
| TargetFrameworkVersion | 빌드하고 있는 애플리케이션을 실행하는 데 필요한 .NET Framework의 버전입니다. 이를 지정하면 다른 경우에는 참조할 수 없는 특정 프레임워크 어셈블리를 참조할 수 있습니다. |
| TreatWarningsAsErrors | `true`이면 모든 경고가 오류로 처리되도록 하는 부울 매개 변수입니다. 이 매개 변수는 `/nowarn` 컴파일러 스위치와 동일합니다. |
| UseHostCompilerIfAvailable | `true`이면 빌드 작업에서 가능한 경우 in-process 컴파일러 개체를 사용하도록 하는 부울 매개 변수입니다. 이 매개 변수는 Visual Studio에서만 사용됩니다. |
| Utf8Output | `true`이면 UTF-8 인코딩을 사용하여 컴파일러 출력을 기록하는 부울 매개 변수입니다. 이 매개 변수는 `/utf8Output` 컴파일러 스위치와 동일합니다. |
| VbcToolPath | 현재 버전의 *vbc.exe*가 재정의될 때 다른 *vbc.exe*의 위치를 나타내는 선택적 경로입니다. |
| VbcVerbosity | Visual Basic 컴파일러 출력의 자세한 정도를 지정합니다. 유효한 값은 “Quiet”, “Normal”(기본값) 또는 “Verbose”입니다. |
| VisualStudioVersion | 이 프로젝트가 실행 중인 것으로 간주되는 Visual Studio의 버전을 지정합니다. 이 속성이 지정되지 않으면 MSBuild는 적절한 기본값을 설정합니다.<br /><br /> 이 속성은 빌드에 사용되는 대상 집합을 지정하기 위해 여러 프로젝트 형식에 사용됩니다. `ToolsVersion`을 4.0 이상의 프로젝트로 설정하면 `VisualStudioVersion`은 사용할 하위 도구 집합을 지정하는 데 사용됩니다. 자세한 내용은 [도구 집합(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)을 참조하세요. |
| WarningsAsErrors | 오류로 처리할 경고 목록을 지정합니다. 이 매개 변수는 `/warnaserror` 컴파일러 스위치와 동일합니다. |
| WarningsNotAsErrors | 오류로 처리하지 않을 경고 목록을 지정합니다. 이 매개 변수는 `/warnaserror` 컴파일러 스위치와 동일합니다. |
| Win32Manifest | 최종 어셈블리에 포함해야 하는 매니페스트 파일의 이름입니다. 이 매개 변수는 `/win32Manifest` 컴파일러 스위치와 동일합니다. |
| Win32Resource | 최종 어셈블리에 포함할 Win32 리소스의 파일 이름입니다. 이 매개 변수는 `/win32resource` 컴파일러 스위치와 동일합니다. |

## <a name="see-also"></a>참조

- [일반적인 MSBuild 프로젝트 항목](../msbuild/common-msbuild-project-items.md)
