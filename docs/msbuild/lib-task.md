---
title: LIB 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), LIB task
- LIB task (MSBuild (C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5794d059a17f39531a7788895b604ae0e9590ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633592"
---
# <a name="lib-task"></a>LIB 작업

Microsoft 32비트 라이브러리 관리자 도구인 *lib.exe*를 래핑합니다. 라이브러리 관리자는 COFF(공용 개체 파일 형식) 개체 파일의 라이브러리를 만들고 관리합니다. 또한 라이브러리 관리자를 사용하여 내보내기 파일을 만들고 내보낸 정의를 참조하는 라이브러리를 가져올 수 있습니다. 자세한 내용은 [LIB 참조](/cpp/build/reference/lib-reference) 및 [LIB 실행](/cpp/build/reference/running-lib)을 참조하세요.

## <a name="parameters"></a>매개 변수

 다음 표에서는 **LIB** 작업의 매개 변수에 대해 설명합니다. 대부분의 작업 매개 변수는 명령줄 옵션에 해당합니다.

|매개 변수|Description|
|---------------|-----------------|
|**AdditionalDependencies**|선택적 **String[]** 매개 변수입니다.<br /><br /> 명령줄에 추가할 추가 항목을 지정합니다.|
|**AdditionalLibraryDirectories**|선택적 **String[]** 매개 변수입니다.<br /><br /> 환경 라이브러리 경로를 재정의합니다. 디렉터리 이름을 지정합니다.<br /><br /> 자세한 내용은 [/LIBPATH(추가 Libpath)](/cpp/build/reference/libpath-additional-libpath)를 참조하세요.|
|**AdditionalOptions**|선택적 **String** 매개 변수입니다.<br /><br /> 명령줄에 지정된 것처럼 *lib.exe* 옵션 목록입니다. 예를 들어 /\<option1> /\<option2> /\<option#>을 참조하십시오. 이 매개 변수를 사용하여 다른 **LIB** 작업 매개 변수로 표현되지 않는 *lib.exe* 옵션을 지정합니다.<br /><br /> 자세한 내용은 [LIB 실행](/cpp/build/reference/running-lib)을 참조하세요.|
|**DisplayLibrary**|선택적 **String** 매개 변수입니다.<br /><br /> 출력 라이브러리에 대한 정보를 표시합니다. 정보를 파일로 리디렉션하는 파일 이름을 지정합니다. 콘솔에 정보를 리디렉션하려면 "CON"을 지정하거나 아무 것도 지정하지 않습니다.<br /><br /> 이 매개 변수는 *lib.exe*의 **/LIST** 옵션에 해당합니다.|
|**ErrorReporting**|선택적 **String** 매개 변수입니다.<br /><br /> 런타임에 *lib.exe*가 실패할 경우 내부 오류 정보를 Microsoft에 보내는 방법을 지정합니다.<br /><br /> 각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.<br /><br /> -   **NoErrorReport** -  **/ERRORREPORT:NONE**<br />-   **PromptImmediately** -  **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** -  **/ERRORREPORT:SEND**<br /><br /> 자세한 내용은 [LIB 실행](/cpp/build/reference/running-lib)에서 **/ERRORREPORT** 명령줄 옵션을 참조하세요.|
|**ExportNamedFunctions**|선택적 **String[]** 매개 변수입니다.<br /><br /> 내보낼 하나 이상의 함수를 지정합니다.<br /><br /> 이 매개 변수는 *lib.exe*의 **/EXPORT:** 옵션에 해당합니다.|
|**ForceSymbolReferences**|선택적 **String** 매개 변수입니다.<br /><br /> 지정한 기호의 참조를 포함하도록 *lib.exe*를 적용합니다.<br /><br /> 이 매개 변수는 *lib.exe*의 **/INCLUDE:** 옵션에 해당합니다.|
|**IgnoreAllDefaultLibraries**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 외부 참조를 확인할 때 *lib.exe*가 검색하는 라이브러리 목록에서 모든 기본 라이브러리를 제거합니다.<br /><br /> 이 매개 변수는 *lib.exe*의 **/NODEFAULTLIB** 옵션의 매개 변수를 사용하지 않는 형식에 해당합니다.|
|**IgnoreSpecificDefaultLibraries**|선택적 **String[]** 매개 변수입니다.<br /><br /> 외부 참조를 확인할 때 *lib.exe*가 검색하는 라이브러리 목록에서 지정된 라이브러리를 제거합니다.<br /><br /> 이 매개 변수는 `library` 인수를 사용하는 *lib.exe*의 **/NODEFAULTLIB** 옵션에 해당합니다.|
|**LinkLibraryDependencies**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 프로젝트 종속성의 라이브러리 출력이 자동으로 링크되도록 지정합니다.|
|**LinkTimeCodeGeneration**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 링크 타임 코드 생성을 지정합니다.<br /><br /> 이 매개 변수는 *lib.exe*의 **/LCTG** 옵션에 해당합니다.|
|**MinimumRequiredVersion**|선택적 **String** 매개 변수입니다.<br /><br /> 하위 시스템의 최소 필수 버전을 지정합니다. 0~65535 범위의 10진수의 쉼표로 구분된 목록을 지정합니다.|
|**ModuleDefinitionFile**|선택적 **String** 매개 변수입니다.<br /><br /> 모듈 정의 파일( *.def*)의 이름을 지정합니다.<br /><br /> 이 매개 변수는 `filename` 인수를 사용하는 *lib.exe*의 **/DEF** 옵션에 해당합니다.|
|**이름**|선택적 **String** 매개 변수입니다.<br /><br /> 가져오기 라이브러리를 빌드할 때 사용할 DLL의 이름을 지정합니다.<br /><br /> 이 매개 변수는 `filename` 인수를 사용하는 *lib.exe*의 **/NAME** 옵션에 해당합니다.|
|**OutputFile**|선택적 **String** 매개 변수입니다.<br /><br /> *lib.exe*에서 만드는 프로그램의 기본 이름과 위치는 무시됩니다.<br /><br /> 이 매개 변수는 `filename` 인수를 사용하는 *lib.exe*의 **/OUT** 옵션에 해당합니다.|
|**RemoveObjects**|선택적 **String[]** 매개 변수입니다.<br /><br /> 지정된 개체를 출력 라이브러리에서 제거합니다. *Lib.exe*는 모든 개체(개체 파일 또는 라이브러리)를 결합하여 출력 라이브러리를 만든 다음, 이 개체로 지정된 개체를 삭제합니다.<br /><br /> 이 매개 변수는 `membername` 인수를 사용하는 *lib.exe*의 **/REMOVE** 옵션에 해당합니다.|
|**Sources**|필수 `ITaskItem[]` 매개 변수입니다.<br /><br /> 공백으로 구분된 소스 파일 목록을 지정합니다.|
|**SubSystem**|선택적 **String** 매개 변수입니다.<br /><br /> 실행 환경을 지정합니다. 어떠한 하위 시스템을 선택하는가에 따라 진입점 기호 또는 진입점 함수가 달라질 수 있습니다.<br /><br /> 각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.<br /><br /> -   **콘솔** -  **/SUBSYSTEM:CONSOLE**<br />-   **Windows** -  **/SUBSYSTEM:WINDOWS**<br />-   **네이티브** -  **/SUBSYSTEM:NATIVE**<br />-   **EFI 애플리케이션** -  **/SUBSYSTEM:EFI_APPLICATION**<br />-   **EFI 부트 서비스 드라이버** -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** -  **/SUBSYSTEM:EFI_ROM**<br />-   **EFI 런타임** -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** -  **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX** -  **/SUBSYSTEM:POSIX**<br /><br /> 자세한 내용은 [/SUBSYSTEM(하위 시스템 지정)](/cpp/build/reference/subsystem-specify-subsystem)을 참조하세요.|
|**SuppressStartupBanner**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.<br /><br /> 자세한 내용은 [LIB 실행](/cpp/build/reference/running-lib)의 **/NOLOGO** 옵션을 참조하세요.|
|**TargetMachine**|선택적 **String** 매개 변수입니다.<br /><br /> 프로그램 또는 DLL에 대한 대상 플랫폼을 지정합니다.<br /><br /> 각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.<br /><br /> -   **MachineARM** -  **/MACHINE:ARM**<br />-   **MachineEBC** -  **/MACHINE:EBC**<br />-   **MachineIA64** -  **/MACHINE:IA64**<br />-   **MachineMIPS** -  **/MACHINE:MIPS**<br />-   **MachineMIPS16** -  **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** -  **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** -  **/MACHINE:SH4**<br />-   **MachineTHUMB** -  **/MACHINE:THUMB**<br />-   **MachineX64** -  **/MACHINE:X64**<br />-   **MachineX86** -  **/MACHINE:X86**<br /><br /> 자세한 내용은 [/MACHINE(대상 플랫폼 지정)](/cpp/build/reference/machine-specify-target-platform)을 참조하세요.|
|**TrackerLogDirectory**|선택적 **String** 매개 변수입니다.<br /><br /> 추적기 로그의 디렉터리를 지정합니다.|
|**TreatLibWarningAsErrors**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true`인 경우 *lib.exe*가 경고를 생성하면 **LIB** 작업이 출력 파일을 생성하지 않습니다. `false`인 경우 출력 파일이 생성됩니다.<br /><br /> 자세한 내용은 [LIB 실행](/cpp/build/reference/running-lib)의 **/WX** 옵션을 참조하세요.|
|**UseUnicodeResponseFiles**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true`인 경우 프로젝트 시스템에 라이브러리가 생성할 때 UNICODE 응답 파일을 생성하도록 지시합니다. 프로젝트의 파일이 유니코드 경로를 갖고 있으면 `true`를 지정합니다.|
|**자세한 정보**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true`인 경우 세션 진행에 대한 자세한 정보를 표시하며 추가하려는 *.obj* 파일의 이름이 포함됩니다. 이 정보는 표준 출력으로 보내지며 파일로 리디렉션될 수 있습니다.<br /><br /> 자세한 내용은 [LIB 실행](/cpp/build/reference/running-lib)의 **/VERBOSE** 옵션을 참조하세요.|

## <a name="see-also"></a>참고 항목

- [작업 참조](../msbuild/msbuild-task-reference.md)