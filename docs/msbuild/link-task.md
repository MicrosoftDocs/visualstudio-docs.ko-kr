---
title: 링크 작업 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), Link task
- Link task (MSBuild (C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01105e3fd4c86d57077df7804e66592e32ebae07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78865351"
---
# <a name="link-task"></a>링크 작업

Microsoft C++ 링커 도구 *link.exe*를 래핑합니다. 링커 도구는 COFF(Common Object File Format) 개체 파일과 라이브러리를 연결하여 실행 파일( *.exe*) 또는 DLL(동적 연결 라이브러리)을 만듭니다. 자세한 내용은 [링커 옵션](/cpp/build/reference/linker-options), [명령줄에서 MSBuild 사용](/cpp/build/msbuild-visual-cpp) 및 [명령줄에서 Microsoft C++ 도구 집합 사용](/cpp/build/building-on-the-command-line)을 참조하세요.

## <a name="parameters"></a>매개 변수

 다음에서는 **링크** 작업의 매개 변수에 대해 설명합니다. 대부분의 작업 매개 변수 및 몇 가지 매개 변수 집합은 명령줄 옵션에 해당합니다.

- **AdditionalDependencies**

  선택적 **String[]** 매개 변수입니다.

  명령에 추가할 입력 파일 목록을 지정합니다.

  자세한 내용은 [LINK 입력 파일](/cpp/build/reference/link-input-files)을 참조하세요.

- **AdditionalLibraryDirectories**

  선택적 **String[]** 매개 변수입니다.

  환경 라이브러리 경로를 재정의합니다. 디렉터리 이름을 지정합니다.

  자세한 내용은 [/LIBPATH(추가 Libpath)](/cpp/build/reference/libpath-additional-libpath)를 참조하세요.

- **AdditionalManifestDependencies**

  선택적 **String[]** 매개 변수입니다.

  매니페스트 파일의 `dependency` 섹션에 배치될 특성을 지정합니다.

  자세한 내용은 [/MANIFESTDEPENDENCY(매니페스트 종속성 지정)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies)를 참조하세요. [게시자 구성 파일](/windows/desktop/SbsCs/publisher-configuration-files)도 참조하세요.

- **AdditionalOptions**

  선택적 **문자열** 매개 변수입니다.

  명령줄에 지정된 링커 옵션 목록입니다. 예를 들어 /\<option1> /\<option2> /\<option#>을 참조하십시오. 이 매개 변수를 사용하여 다른 **링크** 작업 매개 변수로 표현되지 않는 링커 옵션을 지정합니다.

  자세한 내용은 [링커 옵션](/cpp/build/reference/linker-options)을 참조하세요.

- **AddModuleNamesToAssembly**

  선택적 **String[]** 매개 변수입니다.

  모듈 참조를 어셈블리에 추가합니다.

  자세한 내용은 [/ASSEMBLYMODULE(MSIL 모듈을 어셈블리에 추가)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly)을 참조하세요.

- **AllowIsolation**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 운영 체제에서 매니페스트 조회 및 로드가 수행되도록 합니다. `false`이면 매니페스트가 없는 것처럼 DLL이 로드됨을 나타냅니다.

  자세한 내용은 [/ALLOWISOLATION(매니페스트 조회)](/cpp/build/reference/allowisolation-manifest-lookup)을 참조하세요.

- **AssemblyDebug**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 디버그 정보 추적과 함께 **DebuggableAttribute** 특성을 내보내고 JIT 최적화를 사용하지 않습니다. `false`이면 **DebuggableAttribute** 특성을 내보내지만 디버그 정보 추적을 사용하지 않고 JIT 최적화를 사용합니다.

  자세한 내용은 [/ASSEMBLYDEBUG(DebuggableAttribute 추가)](/cpp/build/reference/assemblydebug-add-debuggableattribute)를 참조하세요.

- **AssemblyLinkResource**

  선택적 **String[]** 매개 변수입니다.

  출력 파일에 .NET Framework 리소스에 대한 링크를 만듭니다. 리소스 파일은 출력 파일에 저장되지 않습니다. 리소스의 이름을 지정합니다.

  자세한 내용은 [/ASSEMBLYLINKRESOURCE(.NET Framework 리소스에 대한 링크)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource)를 참조하세요.

- **AttributeFileTracking**

  암시적 **Boolean** 매개 변수입니다.

  세부적인 파일 추적을 사용하여 링크 증분 동작을 캡처합니다. 항상 `true`를 반환합니다.

- **BaseAddress**

  선택적 **문자열** 매개 변수입니다.

  빌드할 프로그램 또는 DLL에 대한 기준 주소를 설정합니다. `{address[,size] | @filename,key}`을 지정합니다.

  자세한 내용은 [/BASE(기준 주소)](/cpp/build/reference/base-base-address)를 참조하세요.

- **BuildingInIDE**

  선택적 **Boolean** 매개 변수입니다.

  true이면 MSBuild가 IDE에서 호출됨을 나타냅니다. 그렇지 않으면 MSBuild가 명령줄에서 호출됨을 나타냅니다.

  이 매개 변수는 해당 링커 옵션이 없습니다.

- **CLRImageType**

  선택적 **문자열** 매개 변수입니다.

  CLR(공용 언어 런타임) 이미지의 형식을 설정합니다.

  각 링커 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Default** -  *\<none>*

  - **ForceIJWImage** -  **/CLRIMAGETYPE:IJW**

  - **ForcePureILImage** -  **/CLRIMAGETYPE:PURE**

  - **ForceSafeILImage** -  **/CLRIMAGETYPE:SAFE**

  자세한 내용은 [/CLRIMAGETYPE(CLR 이미지 형식 지정)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image)을 참조하세요.

- **CLRSupportLastError**

  선택적 **문자열** 매개 변수입니다.

  P/Invoke 메커니즘을 통해 호출된 함수의 마지막 오류 코드를 유지합니다.

  각 링커 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Enabled** -  **/CLRSupportLastError**

  - **Disabled** -  **/CLRSupportLastError:NO**

  - **SystemDlls** -  **/CLRSupportLastError:SYSTEMDLL**

  자세한 내용은 [/CLRSUPPORTLASTERROR(PInvoke 호출의 마지막 오류 코드 유지)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls)를 참조하세요.

- **CLRThreadAttribute**

  선택적 **문자열** 매개 변수입니다.

  CLR 프로그램의 진입점에 대한 스레딩 특성을 명시적으로 지정합니다.

  각 링커 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **DefaultThreadingAttribute** -  **/CLRTHREADATTRIBUTE:NONE**

  - **MTAThreadingAttribute** -  **/CLRTHREADATTRIBUTE:MTA**

  - **STAThreadingAttribute** -  **/CLRTHREADATTRIBUTE:STA**

  자세한 내용은 [/CLRTHREADATTRIBUTE(CLR 스레드 특성 설정)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute)를 참조하세요.

- **CLRUnmanagedCodeCheck**

  선택적 **Boolean** 매개 변수입니다.

  관리 코드에서 네이티브 DLL로 호출하는 링커 생성 P/Invoke에 링커가 **SuppressUnmanagedCodeSecurityAttribute**를 적용할지 여부를 지정합니다.

  자세한 내용은 [/CLRUNMANAGEDCODECHECK(SuppressUnmanagedCodeSecurityAttribute 추가)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute)를 참조하세요.

- **CreateHotPatchableImage**

  선택적 **문자열** 매개 변수입니다.

  핫 패치 가능한 이미지를 준비합니다.

  링커 옵션에 해당하는 다음 값 중 하나를 지정 하세요.

  - **Enabled** -  **/FUNCTIONPADMIN**

  - **X86Image** -  **/FUNCTIONPADMIN:5**

  - **X64Image** -  **/FUNCTIONPADMIN:6**

  - **ItaniumImage** -  **/FUNCTIONPADMIN:16**

  자세한 내용은 [/FUNCTIONPADMIN(핫 패치 가능 이미지 만들기)](/cpp/build/reference/functionpadmin-create-hotpatchable-image)을 참조하세요.

- **DataExecutionPrevention**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 실행 파일이 Windows 데이터 실행 방지 기능과 호환되는지 테스트되었음을 나타냅니다.

  자세한 내용은 [/NXCOMPAT(데이터 실행 방지 기능과 호환)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention)를 참조하세요.

- **DelayLoadDLLs**

  선택적 **String[]** 매개 변수입니다.

  이 매개 변수를 사용하면 DLL의 *로드가 지연*됩니다. 로드를 지연할 DLL의 이름을 지정합니다.

  자세한 내용은 [/DELAYLOAD(가져오기 로드 지연)](/cpp/build/reference/delayload-delay-load-import)를 참조하세요.

- **DelaySign**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 어셈블리에 부분적으로 서명합니다. 기본적으로 이 값은 `false`입니다.

  자세한 내용은 [/DELAYSIGN(어셈블리에 부분적으로 서명)](/cpp/build/reference/delaysign-partially-sign-an-assembly)을 참조하세요.

- **Driver**

  선택적 **문자열** 매개 변수입니다.

  Windows NT 커널 모드 드라이버를 작성하려면 이 매개 변수를 지정합니다.

  각 링커 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **NotSet** -  *\<none>*

  - **Driver** -  **/Driver**

  - **UpOnly** -  **/DRIVER:UPONLY**

  - **WDM** -  **/DRIVER:WDM**

  자세한 내용은 [/DRIVER(Windows NT 커널 모드 드라이버)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver)를 참조하세요.

- **EmbedManagedResourceFile**

  선택적 **String[]** 매개 변수입니다.

  어셈블리에 리소스 파일을 포함합니다. 필요한 리소스 파일 이름을 지정합니다. 필요에 따라 리소스를 로드하는 데 사용되는 논리적 이름과 어셈블리 매니페스트에서 리소스 파일이 비공개임을 나타내는 **PRIVATE** 옵션을 지정합니다.

  자세한 내용은 [/ASSEMBLYRESOURCE(관리되는 리소스 포함)](/cpp/build/reference/assemblyresource-embed-a-managed-resource)를 참조하세요.

- **EnableCOMDATFolding**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 동일한 COMDAT 정리를 사용하도록 설정합니다.

  자세한 내용은 [/OPT(최적화)](/cpp/build/reference/opt-optimizations)의 `ICF[= iterations]` 인수를 참조하세요.

- **EnableUAC**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 UAC(사용자 계정 컨트롤) 정보가 프로그램 매니페스트에 포함되도록 지정합니다.

  자세한 내용은 [/MANIFESTUAC(매니페스트에 UAC 정보 포함)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)를 참조하세요.

- **EntryPointSymbol**

  선택적 **문자열** 매개 변수입니다.

  진입점 함수를 *.exe* 파일이나 DLL의 시작 주소로 지정합니다. 함수 이름을 매개 변수 값으로 지정합니다.

  자세한 내용은 [/ENTRY(진입점 기호)](/cpp/build/reference/entry-entry-point-symbol)를 참조하세요.

- **FixedBaseAddress**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 기본 설정 기준 주소에서만 로드할 수 있는 프로그램이나 DLL을 만듭니다.

  자세한 내용은 [/FIXED(고정 기준 주소)](/cpp/build/reference/fixed-fixed-base-address)를 참조하세요.

- **ForceFileOutput**

  선택적 **문자열** 매개 변수입니다.

  기호가 참조되지만 정의되지 않았거나 여러 번 정의된 경우에도 올바른 *.exe* 파일이나 DLL을 만들도록 링커에 지시합니다.

  각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Enabled** -  **/FORCE**

  - **MultiplyDefinedSymbolOnly** -  **/FORCE:MULTIPLE**

  - **UndefinedSymbolOnly** -  **/FORCE:UNRESOLVED**

  자세한 내용은 [/FORCE(파일 출력 강제)](/cpp/build/reference/force-force-file-output)를 참조하세요.

- **ForceSymbolReferences**

  선택적 **String[]** 매개 변수입니다.

  이 매개 변수는 지정된 기호를 기호 테이블에 추가하도록 링커에 지시합니다.

  자세한 내용은 [/INCLUDE(강제 기호 참조)](/cpp/build/reference/include-force-symbol-references)를 참조하세요.

- **FunctionOrder**

  선택적 **문자열** 매개 변수입니다.

  이 매개 변수는 지정된 패키지 함수(COMDAT)를 미리 결정된 순서로 이미지에 배치하여 프로그램을 최적화합니다.

  자세한 내용은 [/ORDER(함수에 순서 지정)](/cpp/build/reference/order-put-functions-in-order)를 참조하세요.

- **GenerateDebugInformation**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 *.exe* 파일이나 DLL에 대한 디버깅 정보를 생성합니다.

  자세한 내용은 [/DEBUG(디버그 정보 생성)](/cpp/build/reference/debug-generate-debug-info)를 참조하세요.

- **GenerateManifest**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 side-by-side 매니페스트 파일을 만듭니다.

  자세한 내용은 [/MANIFEST(병렬 어셈블리 매니페스트 만들기)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest)를 참조하세요.

- **GenerateMapFile**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 *맵 파일*을 만듭니다. 맵 파일의 파일 이름 확장명은 *.map*입니다.

  자세한 내용은 [/MAP(맵 파일 생성)](/cpp/build/reference/map-generate-mapfile)을 참조하세요.

- **HeapCommitSize**

  선택적 **문자열** 매개 변수입니다.

  힙에서 한 번에 할당할 실제 메모리의 양을 지정합니다.

  자세한 내용은 [/HEAP(힙 크기 설정)](/cpp/build/reference/heap-set-heap-size)의 `commit` 인수를 참조하세요. **HeapReserveSize** 매개 변수도 참조하세요.

- **HeapReserveSize**

  선택적 **문자열** 매개 변수입니다.

  가상 메모리의 총 힙 할당을 지정합니다.

  자세한 내용은 [/HEAP(힙 크기 설정)](/cpp/build/reference/heap-set-heap-size)의 `reserve` 인수를 참조하세요. 이 표의 **HeapCommitSize**도 참조하세요.

- **IgnoreAllDefaultLibraries**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 외부 참조를 확인할 때 검색하는 라이브러리 목록에서 하나 이상의 기본 라이브러리를 제거하도록 링커에 지시합니다.

  자세한 내용은 [/NODEFAULTLIB(라이브러리 무시)](/cpp/build/reference/nodefaultlib-ignore-libraries)를 참조하세요.

- **IgnoreEmbeddedIDL**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 소스 코드의 모든 IDL 특성이 *.idl* 파일로 처리되지 않도록 지정합니다.

  자세한 내용은 [/IGNOREIDL(특성을 MIDL로 처리하지 않음)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl)을 참조하세요.

- **IgnoreImportLibrary**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 이 구성에서 생성된 가져오기 라이브러리를 종속 프로젝트로 가져오지 않도록 지정합니다.

  이 매개 변수는 링커 옵션에 해당하지 않습니다.

- **IgnoreSpecificDefaultLibraries**

  선택적 **String[]** 매개 변수입니다.

  무시할 하나 이상의 기본 라이브러리 이름을 지정합니다. 세미콜론을 사용하여 여러 개의 라이브러리를 구분합니다.

  자세한 내용은 [/NODEFAULTLIB(라이브러리 무시)](/cpp/build/reference/nodefaultlib-ignore-libraries)를 참조하세요.

- **ImageHasSafeExceptionHandlers**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 링커는 이미지의 안전한 예외 처리기 테이블도 생성할 수 있는 경우에만 이미지를 생성합니다.

  자세한 내용은 [/SAFESEH(이미지에 안전한 예외 처리기 포함)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers)를 참조하세요.

- **ImportLibrary**

  기본 라이브러리 이름을 대체하는 사용자 지정 가져오기 라이브러리 이름입니다.

  자세한 내용은 [/IMPLIB(가져오기 라이브러리 이름 지정)](/cpp/build/reference/implib-name-import-library)를 참조하세요.

- **KeyContainer**

  선택적 **문자열** 매개 변수입니다.

  서명된 어셈블리에 대한 키를 포함하는 컨테이너입니다.

  자세한 내용은 [/KEYCONTAINER(어셈블리에 서명할 키 컨테이너 지정)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly)를 참조하세요. 이 표의 **KeyFile** 매개 변수도 참조하세요.

- **KeyFile**

  선택적 **문자열** 매개 변수입니다.

  서명된 어셈블리에 대한 키를 포함하는 파일을 지정합니다.

  자세한 내용은 [/KEYFILE(어셈블리에 서명할 키 또는 키 쌍 지정)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly)을 참조하세요. **KeyContainer** 매개 변수도 참조하세요.

- **LargeAddressAware**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 애플리케이션이 2GB보다 큰 주소를 처리할 수 있습니다.

  자세한 내용은 [/LARGEADDRESSAWARE(큰 주소 처리)](/cpp/build/reference/largeaddressaware-handle-large-addresses)를 참조하세요.

- **LinkDLL**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 DLL를 주 출력 파일로 빌드합니다.

  자세한 내용은 [/DLL(DLL 빌드)](/cpp/build/reference/dll-build-a-dll)을 참조하세요.

- **LinkErrorReporting**

  선택적 **문자열** 매개 변수입니다.

  ICE(내부 컴파일러 오류) 정보를 Microsoft에 직접 제공할 수 있도록 합니다.

  각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **NoErrorReport** -  **/ERRORREPORT:NONE**

  - **PromptImmediately** -  **/ERRORREPORT:PROMPT**

  - **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**

  - **SendErrorReport** -  **/ERRORREPORT:SEND**

  자세한 내용은 [/ERRORREPORT(내부 링커 오류 보고)](/cpp/build/reference/errorreport-report-internal-linker-errors)를 참조하세요.

- **LinkIncremental**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 증분 링크를 사용하도록 설정합니다.

  자세한 내용은 [/INCREMENTAL(증분 링크)](/cpp/build/reference/incremental-link-incrementally)을 참조하세요.

- **LinkLibraryDependencies**

  선택적 **Boolean** 매개 변수입니다.

  `true`인 경우 프로젝트 종속성의 라이브러리 출력이 자동으로 링크되도록 지정합니다.

  이 매개 변수는 링커 옵션에 해당하지 않습니다.

- **LinkStatus**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 완료된 링크 비율을 표시하는 진행률 표시기가 링커에 표시되도록 지정합니다.

  자세한 내용은 [/LTCG(링크 타임 코드 생성)](/cpp/build/reference/ltcg-link-time-code-generation)의 `STATUS` 인수를 참조하세요.

- **LinkTimeCodeGeneration**

  선택적 **문자열** 매개 변수입니다.

  프로필 기반 최적화에 대한 옵션을 지정합니다.

  각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Default** -  *\<none>*

  - **UseLinkTimeCodeGeneration** -  **/LTCG**

  - **PGInstrument** -  **/LTCG:PGInstrument**

  - **PGOptimization** -  **/LTCG:PGOptimize**

  - **PGUpdate**

    \- **/LTCG:PGUpdate**

  자세한 내용은 [/LTCG(링크 타임 코드 생성)](/cpp/build/reference/ltcg-link-time-code-generation)를 참조하세요.

- **ManifestFile**

  선택적 **문자열** 매개 변수입니다.

  기본 매니페스트 파일 이름을 지정된 파일 이름으로 변경합니다.

  자세한 내용은 [/MANIFESTFILE(매니페스트 파일 이름 지정)](/cpp/build/reference/manifestfile-name-manifest-file)을 참조하세요.

- **MapExports**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 내보낸 함수를 맵 파일에 포함하도록 링커에 지시합니다.

  자세한 내용은 [/MAPINFO(맵 파일에 정보 포함)](/cpp/build/reference/mapinfo-include-information-in-mapfile)의 `EXPORTS` 인수를 참조하세요.

- **MapFileName**

  선택적 **문자열** 매개 변수입니다.

  기본 맵 파일 이름을 지정된 파일 이름으로 변경합니다.

- **MergedIDLBaseFileName**

  선택적 **문자열** 매개 변수입니다.

  *.idl* 파일의 파일 이름 및 파일 이름 확장명을 지정합니다.

  자세한 내용은 [/IDLOUT(MIDL 출력 파일 이름 지정)](/cpp/build/reference/idlout-name-midl-output-files)을 참조하세요.

- **MergeSections**

  선택적 **문자열** 매개 변수입니다.

  이미지에서 섹션을 결합합니다. `from-section=to-section`을 지정합니다.

  자세한 내용은 [/MERGE(섹션 결합)](/cpp/build/reference/merge-combine-sections)를 참조하세요.

- **MidlCommandFile**

  선택적 **문자열** 매개 변수입니다.

  MIDL 명령줄 옵션을 포함하는 파일의 이름을 지정합니다.

  자세한 내용은 [/MIDL(MIDL 명령줄 옵션 지정)](/cpp/build/reference/midl-specify-midl-command-line-options)을 참조하세요.

- **MinimumRequiredVersion**

  선택적 **문자열** 매개 변수입니다.

  하위 시스템의 최소 필수 버전을 지정합니다. 인수는 0에서 65535 사이의 10진수입니다.

- **ModuleDefinitionFile**

  선택적 **문자열** 매개 변수입니다.

  [모듈 정의 파일](/cpp/build/reference/module-definition-dot-def-files)의 이름을 지정합니다.

  자세한 내용은 [/DEF(모듈 정의 파일 지정)](/cpp/build/reference/def-specify-module-definition-file)를 참조하세요.

- **MSDOSStubFileName**

  선택적 **문자열** 매개 변수입니다.

  지정된 MS-DOS 스텁 프로그램을 Win32 프로그램에 연결합니다.

  자세한 내용은 [/STUB(MS-DOS 스텁 파일 이름)](/cpp/build/reference/stub-ms-dos-stub-file-name)을 참조하세요.

- **NoEntryPoint**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 리소스 전용 DLL을 지정합니다.

  자세한 내용은 [/NOENTRY(진입점 없음)](/cpp/build/reference/noentry-no-entry-point)를 참조하세요.

- **ObjectFiles**

  암시적 **String[]** 매개 변수입니다.

  링크된 개체 파일을 지정합니다.

- **OptimizeReferences**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 참조되지 않는 함수 및/또는 데이터를 제거합니다.

  자세한 내용은 [/OPT(최적화)](/cpp/build/reference/opt-optimizations)의 `REF` 인수를 참조하세요.

- **OutputFile**

  선택적 **문자열** 매개 변수입니다.

  링커가 만드는 프로그램의 기본 이름 및 위치를 재정의합니다.

  자세한 내용은 [/OUT(출력 파일 이름)](/cpp/build/reference/out-output-file-name)을 참조하세요.

- **PerUserRedirection**

  선택적 **Boolean** 매개 변수입니다.

  `true`이고 출력 등록을 사용하도록 설정하면 **HKEY_CLASSES_ROOT**에 대한 레지스트리 쓰기가 **HKEY_CURRENT_USER**로 리디렉션되도록 합니다.

- **PreprocessOutput**

  선택적 `ITaskItem[]` 매개 변수입니다.

  작업에서 사용하고 내보낼 수 있는 전처리기 출력 항목의 배열을 정의합니다.

- **PreventDllBinding**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 *Bind.exe*에서 링크된 이미지가 바인딩되지 않음을 나타냅니다.

  자세한 내용은 [/ALLOWBIND(DLL 바인딩 방지)](/cpp/build/reference/allowbind-prevent-dll-binding)를 참조하세요.

- **Profile**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 **성능 도구** 프로파일러와 함께 사용할 수 있는 출력 파일을 생성합니다.

  자세한 내용은 [/PROFILE(성능 도구 프로파일러)](/cpp/build/reference/profile-performance-tools-profiler)을 참조하세요.

- **ProfileGuidedDatabase**

  선택적 **문자열** 매개 변수입니다.

  실행 중인 프로그램에 대한 정보를 저장하는 데 사용될 *.pgd* 파일의 이름을 지정합니다.

  자세한 내용은 [/PGD(프로필 기반 최적화를 위한 데이터베이스 지정)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations)를 참조하세요.

- **ProgramDatabaseFile**

  선택적 **문자열** 매개 변수입니다.

  링커에서 만든 PDB(프로그램 데이터베이스)에 대한 이름을 지정합니다.

  자세한 내용은 [/PDB(프로그램 데이터베이스 사용)](/cpp/build/reference/pdb-use-program-database)를 참조하세요.

- **RandomizedBaseAddress**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 Windows의 *ASLR(Address Space Layout Randomization)* 기능을 사용하여 로드할 때 무작위로 기준 주소를 다시 지정할 수 있는 실행 가능 이미지를 생성합니다.

  자세한 내용은 [/DYNAMICBASE(주소 공간 레이아웃을 임의로 지정)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization)를 참조하세요.

- **RegisterOutput**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 이 빌드의 기본 출력을 등록합니다.

- **SectionAlignment**

  선택적 **Integer** 매개 변수입니다.

  프로그램의 선형 주소 공간 내에서 각 섹션의 맞춤을 지정합니다. 매개 변수 값은 바이트의 단위 수이며 2의 거듭제곱입니다.

  자세한 내용은 [/ALIGN(섹션 맞춤)](/cpp/build/reference/align-section-alignment)을 참조하세요.

- **SetChecksum**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 *.exe* 파일의 헤더에 체크섬을 설정합니다.

  자세한 내용은 [/RELEASE(체크섬 설정)](/cpp/build/reference/release-set-the-checksum)를 참조하세요.

- **ShowProgress**

  선택적 **문자열** 매개 변수입니다.

  연결 작업에 대한 진행률 보고서의 자세한 정도를 지정합니다.

  각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **NotSet** -  *\<none>*

  - **LinkVerbose** -  **/VERBOSE**

  - **LinkVerboseLib** -  **/VERBOSE:Lib**

  - **LinkVerboseICF** -  **/VERBOSE:ICF**

  - **LinkVerboseREF** -  **/VERBOSE:REF**

  - **LinkVerboseSAFESEH** -  **/VERBOSE:SAFESEH**

  - **LinkVerboseCLR** -  **/VERBOSE:CLR**

  자세한 내용은 [/VERBOSE(진행 메시지 표시)](/cpp/build/reference/verbose-print-progress-messages)를 참조하세요.

- **Sources**

  필수 `ITaskItem[]` 매개 변수입니다.

  작업에서 사용하고 내보낼 수 있는 MSBuild 소스 파일 항목의 배열을 정의합니다.

- **SpecifySectionAttributes**

  선택적 **문자열** 매개 변수입니다.

  섹션의 특성을 지정합니다. 이 매개 변수는 섹션에 대한 *.obj* 파일을 컴파일할 때 설정된 특성을 재정의합니다.

  자세한 내용은 [/SECTION(섹션 특성 지정)](/cpp/build/reference/section-specify-section-attributes)을 참조하세요.

- **StackCommitSize**

  선택적 **문자열** 매개 변수입니다.

  추가 메모리를 할당할 때 각 할당의 실제 메모리 양을 지정합니다.

  자세한 내용은 [/STACK(스택 할당)](/cpp/build/reference/stack-stack-allocations)의 `commit` 인수를 참조하세요.

- **StackReserveSize**

  선택적 **문자열** 매개 변수입니다.

  가상 메모리의 총 스택 할당 크기를 지정합니다.

  자세한 내용은 [/STACK(스택 할당)](/cpp/build/reference/stack-stack-allocations)의 `reserve` 인수를 참조하세요.

- **StripPrivateSymbols**

  선택적 **문자열** 매개 변수입니다.

  고객에게 배포하지 않을 기호를 생략하는 두 번째 PDB(프로그램 데이터베이스) 파일을 만듭니다. 두 번째 PDB 파일의 이름을 지정합니다.

  자세한 내용은 [/PDBSTRIPPED(전용 기호 제거)](/cpp/build/reference/pdbstripped-strip-private-symbols)를 참조하세요.

- **SubSystem**

  선택적 **문자열** 매개 변수입니다.

  실행 환경을 지정합니다.

  각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **NotSet** -  *\<none>*

  - **콘솔** -  **/SUBSYSTEM:CONSOLE**

  - **Windows** -  **/SUBSYSTEM:WINDOWS**

  - **네이티브** -  **/SUBSYSTEM:NATIVE**

  - **EFI 애플리케이션** -  **/SUBSYSTEM:EFI_APPLICATION**

  - **EFI 부트 서비스 드라이버** -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**

  - **EFI ROM** -  **/SUBSYSTEM:EFI_ROM**

  - **EFI 런타임** -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**

  - **WindowsCE** -  **/SUBSYSTEM:WINDOWSCE**

  - **POSIX** -  **/SUBSYSTEM:POSIX**

  자세한 내용은 [/SUBSYSTEM(하위 시스템 지정)](/cpp/build/reference/subsystem-specify-subsystem)을 참조하세요.

- **SupportNobindOfDelayLoadedDLL**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 바인딩할 수 있는 IAT(가져오기 주소 테이블)를 최종 이미지에 포함하지 않도록 링커에 지시합니다.

  자세한 내용은 [/DELAY(가져오기 설정 로드 지연)](/cpp/build/reference/delay-delay-load-import-settings)의 `NOBIND` 인수를 참조하세요.

- **SupportUnloadOfDelayLoadedDLL**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 지연 로드 도우미 함수에 DLL의 명시적 언로드를 지원하도록 지시합니다.

  자세한 내용은 [/DELAY(가져오기 설정 로드 지연)](/cpp/build/reference/delay-delay-load-import-settings)의 `UNLOAD` 인수를 참조하세요.

- **SuppressStartupBanner**

  선택적 **Boolean** 매개 변수입니다.

  `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.

  자세한 내용은 [/NOLOGO(시작 배너 표시 안 함)(링커)](/cpp/build/reference/nologo-suppress-startup-banner-linker)를 참조하세요.

- **SwapRunFromCD**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 먼저 링커 출력을 스왑 파일에 복사한 다음 해당 파일에서 이미지를 실행하도록 운영 체제에 지시합니다.

  자세한 내용은 [/SWAPRUN(링커 출력을 스왑 파일로 로드)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)의 `CD` 인수를 참조하세요. **SwapRunFromNET** 매개 변수도 참조하세요.

- **SwapRunFromNET**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 먼저 링커 출력을 스왑 파일에 복사한 다음 해당 파일에서 이미지를 실행하도록 운영 체제에 지시합니다.

  자세한 내용은 [/SWAPRUN(링커 출력을 스왑 파일로 로드)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)의 `NET` 인수를 참조하세요. 이 표의 **SwapRunFromCD** 매개 변수도 참조하세요.

- **TargetMachine**

  선택적 **문자열** 매개 변수입니다.

  프로그램 또는 DLL에 대한 대상 플랫폼을 지정합니다.

  각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **NotSet** -  *\<none>*

  - **MachineARM** -  **/MACHINE:ARM**

  - **MachineEBC** -  **/MACHINE:EBC**

  - **MachineIA64** -  **/MACHINE:IA64**

  - **MachineMIPS** -  **/MACHINE:MIPS**

  - **MachineMIPS16** -  **/MACHINE:MIPS16**

  - **MachineMIPSFPU** -  **/MACHINE:MIPSFPU**

  - **MachineMIPSFPU16** -  **/MACHINE:MIPSFPU16**

  - **MachineSH4** -  **/MACHINE:SH4**

  - **MachineTHUMB** -  **/MACHINE:THUMB**

  - **MachineX64** -  **/MACHINE:X64**

  - **MachineX86** -  **/MACHINE:X86**

  자세한 내용은 [/MACHINE(대상 플랫폼 지정)](/cpp/build/reference/machine-specify-target-platform)을 참조하세요.

- **TerminalServerAware**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 프로그램 이미지 선택적 헤더의 IMAGE_OPTIONAL_HEADER DllCharacteristics 필드에서 플래그를 설정합니다. 이 플래그를 설정하면 터미널 서버가 애플리케이션에서 특정 변경 작업을 수행할 수 없습니다.

  자세한 내용은 [/TSAWARE(터미널 서버 인식 애플리케이션 만들기)](/cpp/build/reference/tsaware-create-terminal-server-aware-application)를 참조하세요.

- **TrackerLogDirectory**

  선택적 **문자열** 매개 변수입니다.

  추적기 로그의 디렉터리를 지정합니다.

- **TreatLinkerWarningAsErrors**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 링커에서 경고가 생성되는 경우에도 출력 파일이 생성되지 않도록 합니다.

  자세한 내용은 [/WX(링커 경고를 오류로 처리)](/cpp/build/reference/wx-treat-linker-warnings-as-errors)를 참조하세요.

- **TurnOffAssemblyGeneration**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 .NET Framework 어셈블리 없이 현재 출력 파일에 대한 이미지를 만듭니다.

  자세한 내용은 [/NOASSEMBLY(MSIL 모듈 만들기)](/cpp/build/reference/noassembly-create-a-msil-module)를 참조하세요.

- **TypeLibraryFile**

  선택적 **문자열** 매개 변수입니다.

  *.tlb* 파일의 파일 이름 및 파일 이름 확장명을 지정합니다. 파일 이름 또는 경로와 파일 이름을 지정합니다.

  자세한 내용은 [/TLBOUT(.tlb 파일 이름 지정)](/cpp/build/reference/tlbout-name-dot-tlb-file)를 참조하세요.

- **TypeLibraryResourceID**

  선택적 **Integer** 매개 변수입니다.

  링커에서 만든 형식 라이브러리에 대한 사용자 지정 값을 지정합니다. 1에서 65535 사이의 값을 지정합니다.

  자세한 내용은 [/TLBID(TypeLib의 리소스 ID 지정)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib)를 참조하세요.

- **UACExecutionLevel**

  선택적 **문자열** 매개 변수입니다.

  사용자 계정 컨트롤을 사용하여 실행될 때 애플리케이션에 필요한 실행 수준을 지정합니다.

  각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **AsInvoker** - `level='asInvoker'`

  - **HighestAvailable** - `level='highestAvailable'`

  - **RequireAdministrator** - `level='requireAdministrator'`

  자세한 내용은 [/MANIFESTUAC(매니페스트에 UAC 정보 포함)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)의 `level` 인수를 참조하세요.

- **UACUIAccess**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 애플리케이션에서 사용자 인터페이스 보호 수준을 우회하고 데스크톱에서 상위 권한 창에 입력할 수 있게 하고, 그렇지 않으면 `false`입니다.

  자세한 내용은 [/MANIFESTUAC(매니페스트에 UAC 정보 포함)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)의 `uiAccess` 인수를 참조하세요.

- **UseLibraryDependencyInputs**

  선택적 **Boolean** 매개 변수입니다.

  `true`이면 프로젝트 종속성의 라이브러리 출력이 링크될 때 라이브러리 파일 자체가 아닌 라이브러리 관리자 도구에 대한 입력이 사용됩니다.

- **Version**

  선택적 **문자열** 매개 변수입니다.

  *.exe* 또는 *.dll* 파일의 헤더에 버전 번호를 저장합니다. `major[.minor]`를 지정합니다. `major` 및 `minor` 인수는 0에서 65535 사이의 10진수입니다.

  자세한 내용은 [/VERSION(버전 정보)](/cpp/build/reference/version-version-information)을 참조하세요.

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
