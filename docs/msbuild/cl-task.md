---
title: CL 작업 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb0e1feee1f7e1d271dd436a1879731354cbd8bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78865338"
---
# <a name="cl-task"></a>CL 작업

Microsoft C++ 컴파일러 도구 *cl.exe*를 래핑합니다. 컴파일러는 실행( *.exe*) 파일, 동적 연결 라이브러리( *.dll*) 파일 또는 코드 모듈( *.netmodule*) 파일을 생성합니다. 자세한 내용은 [컴파일러 옵션](/cpp/build/reference/compiler-options), [명령줄에서 MSBuild 사용](/cpp/build/msbuild-visual-cpp) 및 [명령줄에서 Microsoft C++ 도구 집합 사용](/cpp/build/building-on-the-command-line)을 참조하세요.

## <a name="parameters"></a>매개 변수

 다음 목록에서는 **CL** 작업의 매개 변수에 대해 설명합니다. 대부분의 작업 매개 변수 및 몇 가지 매개 변수 집합은 명령줄 옵션에 해당합니다.

- **AdditionalIncludeDirectories**

   선택적 String[] 매개 변수입니다.

   포함 파일을 검색할 디렉터리 목록에 디렉터리를 추가합니다.

   자세한 내용은 [/I(추가 포함 디렉터리)](/cpp/build/reference/i-additional-include-directories)를 참조하세요.

- **AdditionalOptions**

   선택적 문자열 매개 변수입니다.

   명령줄 옵션의 목록입니다. 예를 들어 "/\<option1> /\<option2> /\<option#>"입니다. 이 매개 변수를 사용하여 다른 작업 매개 변수로 표현되지 않는 명령줄 옵션을 지정합니다.

   자세한 내용은 [컴파일러 옵션](/cpp/build/reference/compiler-options)을 참조하세요.

- **AdditionalUsingDirectories**

   선택적 String[] 매개 변수입니다.

   **#using** 지시문에 전달된 파일 참조를 확인하기 위해 컴파일러가 검색할 디렉터리를 지정합니다.

   자세한 내용은 [/AI(메타데이터 디렉터리 지정)](/cpp/build/reference/ai-specify-metadata-directories)를 참조하세요.

- **AlwaysAppend**

   선택적 문자열 매개 변수입니다.

   명령줄에 항상 내보내지는 문자열입니다. 기본값은 " **/c**"입니다.

- **AssemblerListingLocation**

   어셈블리 코드가 포함된 목록 파일을 만듭니다.

   자세한 내용은 [/FA, /Fa(목록 파일)](/cpp/build/reference/fa-fa-listing-file)의 **/Fa** 옵션을 참조하세요.

- **AssemblerOutput**

   선택적 문자열 매개 변수입니다.

   어셈블리 코드가 포함된 목록 파일을 만듭니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **NoListing** -  *\<none>*

  - **AssemblyCode** -  **/FA**

  - **AssemblyAndMachineCode** -  **/FAc**

  - **AssemblyAndSourceCode** -  **/FAs**

  - **All** -  **/FAcs**

    자세한 내용은 [/FA, /Fa(목록 파일)](/cpp/build/reference/fa-fa-listing-file)의 **/FA**, **/FAc**, **/FAs** 및 **/FAcs** 옵션을 참조하세요.

- **BasicRuntimeChecks**

   선택적 문자열 매개 변수입니다.

   [runtime_checks](/cpp/preprocessor/runtime-checks) pragma와 함께 런타임 오류 검사 기능을 사용하거나 사용하지 않도록 설정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Default** -                           *\<none>*

  - **StackFrameRuntimeCheck** -  **/RTCs**

  - **UninitializedLocalUsageCheck** -  **/RTCu**

  - **EnableFastChecks** -                           **/RTC1**

    자세한 내용은 [/RTC(런타임 오류 검사)](/cpp/build/reference/rtc-run-time-error-checks)를 참조하세요.

- **BrowseInformation**

   선택적 부울 매개 변수입니다.

   `true`인 경우 찾아보기 정보 파일을 만듭니다.

   자세한 내용은 [/FR, /Fr(.sbr 파일 만들기)](/cpp/build/reference/fr-fr-create-dot-sbr-file)의 **/FR** 옵션을 참조하세요.

- **BrowseInformationFile**

   선택적 문자열 매개 변수입니다.

   찾아보기 정보 파일에 대한 파일 이름을 지정합니다.

   자세한 내용은 이 표의 **BrowseInformation** 매개 변수를 참조하고 [/FR, /Fr(.sbr 파일 만들기)](/cpp/build/reference/fr-fr-create-dot-sbr-file)도 참조하세요.

- **BufferSecurityCheck**

   선택적 부울 매개 변수입니다.

   `true`인 경우 버퍼 크기 제한을 적용하지 않는 코드를 악용하기 위한 일반적인 기술인, 반환 주소를 덮어쓰는 일부 버퍼 오버런을 검색합니다.

   자세한 내용은 [/GS(버퍼 보안 검사)](/cpp/build/reference/gs-buffer-security-check)를 참조하세요.

- **BuildingInIDE**

   선택적 부울 매개 변수입니다.

   `true`인 경우 **MSBuild**가 IDE에 의해 호출됨을 나타냅니다. 그렇지 않으면 **MSBuild**가 명령줄에서 호출됩니다.

- **CallingConvention**

   선택적 문자열 매개 변수입니다.

   함수 인수가 스택으로 푸시되는 순서, 호출자 함수 또는 호출된 함수가 호출의 끝에 있는 스택에서 인수를 제거하는지 여부 및 컴파일러가 개별 함수를 식별하는 데 사용하는 이름 데코레이팅 규칙을 결정하는 호출 규칙을 지정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Cdecl** -  **/Gd**

  - **FastCall** -                           **/Gr**

  - **StdCall** -                           **/Gz**

    자세한 내용은 [/Gd, /Gr, /Gv, /Gz(호출 규칙)](/cpp/build/reference/gd-gr-gv-gz-calling-convention)를 참조하세요.

- **CompileAs**

   선택적 문자열 매개 변수입니다.

   입력 파일을 C 또는 C++ 소스 파일로 컴파일할지 지정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Default** -  *\<none>*

  - **CompileAsC** -  **/TC**

  - **CompileAsCpp** -  **/TP**

    자세한 내용은 [/Tc, /Tp, /TC, /TP(소스 파일 형식 지정)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type)를 참조하세요.

- **CompileAsManaged**

   선택적 문자열 매개 변수입니다.

   애플리케이션 및 구성 요소가 CLR(공용 언어 런타임)의 기능을 사용할 수 있게 합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **false** -  *\<none>*

  - **true** -  **/clr**

  - **Pure** -  **/clr:pure**

  - **Safe** -  **/clr:safe**

  - **OldSyntax** -  **/clr:oldSyntax**

    자세한 내용은 [/clr(공용 언어 런타임 컴파일)](/cpp/build/reference/clr-common-language-runtime-compilation)을 참조하세요.

- **CreateHotpatchableImage**

   선택적 부울 매개 변수입니다.

   `true`인 경우 컴파일러가 *핫 패치*용 이미지를 준비하도록 합니다. 이 매개 변수는 각 함수의 첫 번째 명령이 2바이트가 되도록 합니다(핫 패치에 필요함).

   자세한 내용은 [/hotpatch(핫 패치 가능 이미지 만들기)](/cpp/build/reference/hotpatch-create-hotpatchable-image)를 참조하세요.

- **DebugInformationFormat**

   선택적 문자열 매개 변수입니다.

   프로그램용으로 생성되는 디버깅 정보 형식과 이 정보를 개체( *.obj*) 파일에 유지할지 아니면 프로그램 데이터베이스(PDB)에 유지할지를 선택합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **OldStyle** -  **/Z7**

  - **ProgramDatabase** -  **/Zi**

  - **EditAndContinue** -  **/ZI**

    자세한 내용은 [/Z7, /Zi, /ZI(디버그 정보 형식)](/cpp/build/reference/z7-zi-zi-debug-information-format)를 참조하세요.

- **DisableLanguageExtensions**

   선택적 부울 매개 변수입니다.

   **true**인 경우 컴파일러가 ANSI C 또는 ANSI C++와 호환되지 않는 언어 구문에 대한 오류를 내보내도록 합니다.

   자세한 내용은 [/Za, /Ze(언어 확장 사용 안 함)](/cpp/build/reference/za-ze-disable-language-extensions)의 **/Za** 옵션을 참조하세요.

- **DisableSpecificWarnings**

   선택적 String[] 매개 변수입니다.

   세미콜론으로 구분된 목록에 지정된 경고 번호를 사용하지 않도록 설정합니다.

   자세한 내용은 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX(경고 수준)](/cpp/build/reference/compiler-option-warning-level)의 `/wd` 옵션을 참조하세요.

- **EnableEnhancedInstructionSet**

   선택적 문자열 매개 변수입니다.

   SSE(스트리밍 SIMD 확장) 및 SSE2(스트리밍 SIMD 확장 2) 명령을 사용하는 코드 생성에 대한 아키텍처를 지정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **StreamingSIMDExtensions** -  **/arch:SSE**

  - **StreamingSIMDExtensions2** -  **/arch:SSE2**

    자세한 내용은 [/arch(x86)](/cpp/build/reference/arch-x86)를 참조하세요.

- **EnableFiberSafeOptimizations**

   선택적 부울 매개 변수입니다.

   `true`인 경우 정적 스레드 로컬 스토리지를 사용하여 할당한 데이터(즉, `__declspec(thread)`를 사용하여 할당한 데이터)의 파이버 안전을 지원합니다.

   자세한 내용은 [/GT(파이버 안전 스레드 로컬 스토리지 지원)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage)를 참조하세요.

- **EnablePREfast**

   선택적 부울 매개 변수입니다.

   `true`인 경우 코드 분석을 사용하도록 설정합니다.

   자세한 내용은 [/analyze(코드 분석)](/cpp/build/reference/analyze-code-analysis)를 참조하세요.

- **ErrorReporting**

   선택적 문자열 매개 변수입니다.

   ICE(내부 컴파일러 오류) 정보를 Microsoft에 직접 제공할 수 있도록 합니다. 기본적으로 IDE 빌드의 설정은 **프롬프트**이며, 명령줄 빌드의 설정은 **큐**입니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **None** -  **/errorReport:none**

  - **Prompt** -  **/errorReport:prompt**

  - **Queue** -  **/errorReport:queue**

  - **Send** -  **/errorReport:send**

    자세한 내용은 [/errorReport(내부 컴파일러 오류 보고)](/cpp/build/reference/errorreport-report-internal-compiler-errors)를 참조하세요.

- **ExceptionHandling**

   선택적 문자열 매개 변수입니다.

   컴파일러가 사용하는 예외 처리 모델을 지정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **false** -  *\<none>*

  - **Async** -  **/EHa**

  - **Sync** -  **/EHsc**

  - **SyncCThrow** -  **/EHs**

    자세한 내용은 [/EH(예외 처리 모델)](/cpp/build/reference/eh-exception-handling-model)를 참조하세요.

- **ExpandAttributedSource**

   선택적 부울 매개 변수입니다.

   `true`인 경우 소스 파일에 확장 특성을 삽입한 목록 파일을 만듭니다.

   자세한 내용은 [/Fx(삽입된 코드 병합)](/cpp/build/reference/fx-merge-injected-code)를 참조하세요.

- **FavorSizeOrSpeed**

   선택적 문자열 매개 변수입니다.

   코드 크기나 코드 속도 중 우선하는 것을 지정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Neither** -  *\<none>*

  - **Size** -  **/Os**

  - **Speed** -  **/Ot**

    자세한 내용은 [/Os, /Ot(코드 크기 우선, 코드 속도 우선)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code)를 참조하세요.

- **FloatingPointExceptions**

   선택적 부울 매개 변수입니다.

   `true`인 경우 안정적인 부동 소수점 예외 모델을 사용할 수 있습니다. 예외가 트리거되는 직후 발생합니다.

   자세한 내용은 [/fp(부동 소수점 동작 지정)](/cpp/build/reference/fp-specify-floating-point-behavior)의 /**fp:except** 옵션을 참조하세요.

- **FloatingPointModel**

   선택적 문자열 매개 변수입니다.

   부동 소수점 모델을 설정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Precise** -  **/fp:precise**

  - **Strict** -  **/fp:strict**

  - **Fast** -  **/fp:fast**

    자세한 내용은 [/fp(부동 소수점 동작 지정)](/cpp/build/reference/fp-specify-floating-point-behavior)를 참조하세요.

- **ForceConformanceInForLoopScope**

   선택적 부울 매개 변수입니다.

   `true`인 경우 Microsoft 확장([/Ze](/cpp/build/reference/za-ze-disable-language-extensions))을 사용하는 [for](/cpp/cpp/for-statement-cpp) 루프의 표준 C++ 동작을 구현합니다.

   자세한 내용은 [/Zc:forScope(for 루프 범위의 강제 규칙)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope)를 참조하세요.

- **ForcedIncludeFiles**

   선택적 `String[]` 매개 변수입니다.

   전처리기가 하나 이상의 지정된 헤더 파일을 처리하게 합니다.

   자세한 내용은 [/FI(강제 포함 파일 이름 지정)](/cpp/build/reference/fi-name-forced-include-file)를 참조하세요.

- **ForcedUsingFiles**

   선택적 **String[]** 매개 변수입니다.

   전처리기가 하나 이상의 지정된 **#using** 파일을 처리하게 합니다.

   자세한 내용은 [/FU(강제 #using 파일 이름 지정)](/cpp/build/reference/fu-name-forced-hash-using-file)를 참조하세요.

- **FunctionLevelLinking**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 컴파일러가 개별 함수를 패키지된 함수의 형태로 패키지할 수 있습니다(COMDAT).

   자세한 내용은 [/Gy(함수 수준 링크 사용)](/cpp/build/reference/gy-enable-function-level-linking)를 참조하세요.

- **GenerateXMLDocumentationFiles**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 컴파일러가 소스 코드 파일의 문서 주석을 처리하고 문서 주석이 포함된 각 소스 코드 파일에 대한 *.xdc* 파일을 만들도록 합니다.

   자세한 내용은 [/doc(문서 주석 처리) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp)를 참조하세요. 또한 이 표의 **XMLDocumentationFileName** 매개 변수도 참조하세요.

- **IgnoreStandardIncludePath**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 컴파일러가 PATH 및 INCLUDE 환경 변수에 지정된 디렉터리에서 포함 파일을 검색하지 않도록 합니다.

   자세한 내용은 [/X(표준 포함 경로 무시)](/cpp/build/reference/x-ignore-standard-include-paths)를 참조하세요.

- **InlineFunctionExpansion**

   선택적 **문자열** 매개 변수입니다.

   빌드에 대한 인라인 함수 확장 수준을 지정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Default** -  *\<none>*

  - **Disabled** -  **/Ob0**

  - **OnlyExplicitInline** -  **/Ob1**

  - **AnySuitable** -  **/Ob2**

    자세한 내용은 [/Ob(인라인 함수 확장)](/cpp/build/reference/ob-inline-function-expansion)를 참조하세요.

- **IntrinsicFunctions**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 애플리케이션을 더 빠르게 실행하는 데 도움이 되는 내장 함수 또는 다른 특별한 형태의 함수로 일부 함수 호출을 바꿉니다.

   자세한 내용은 [/Oi(내장 함수 만들기)](/cpp/build/reference/oi-generate-intrinsic-functions)를 참조하세요.

- **MinimalRebuild**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 변경된 C++ 클래스 정의(헤더 파일(.h)에 저장됨)가 포함된 C++ 소스 파일을 다시 컴파일해야 하는지 결정하는 최소 다시 빌드를 사용하도록 설정합니다.

   자세한 내용은 [/Gm(최소 다시 빌드 사용)](/cpp/build/reference/gm-enable-minimal-rebuild)을 참조하세요.

- **MultiProcessorCompilation**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 다중 프로세서를 사용하여 컴파일합니다. 이 매개 변수는 컴퓨터의 각 유효 프로세서에 대한 프로세스를 만듭니다.

   자세한 내용은 [/MP(여러 프로세스로 빌드)](/cpp/build/reference/mp-build-with-multiple-processes)를 참조하세요. 또한 이 표의 **ProcessorNumber** 매개 변수도 참조하세요.

- **ObjectFileName**

   선택적 **문자열** 매개 변수입니다.

   기본값 대신 사용할 개체(.obj) 파일 이름 또는 디렉터리를 지정합니다.

   자세한 내용은 [/Fo(개체 파일 이름)](/cpp/build/reference/fo-object-file-name)를 참조하세요.

- **ObjectFiles**

   선택적 **String[]** 매개 변수입니다.

   개체 파일의 목록입니다.

- **OmitDefaultLibName**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 개체( *.obj*) 파일에서 기본 C 런타임 라이브러리 이름을 생략합니다. 기본적으로 컴파일러는 올바른 라이브러리로 링커를 보내기 위해 라이브러리 이름을 *.obj* 파일에 넣습니다.

   자세한 내용은 [/Zl(기본 라이브러리 이름 생략)](/cpp/build/reference/zl-omit-default-library-name)를 참조하세요.

- **OmitFramePointers**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 호출 스택에서 프레임 포인터를 생성하지 않습니다.

   자세한 내용은 [/Oy(프레임 포인터 생략)](/cpp/build/reference/oy-frame-pointer-omission)를 참조하세요.

- **OpenMPSupport**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 컴파일러가 OpenMP 절 및 지시문을 처리하게 합니다.

   자세한 내용은 [/openmp(OpenMP 2.0 지원 활성화)](/cpp/build/reference/openmp-enable-openmp-2-0-support)를 참조하세요.

- **Optimization**

   선택적 **문자열** 매개 변수입니다.

   속도 및 크기에 대한 다양한 코드 최적화를 지정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Disabled** -  **/Od**

  - **MinSpace** -  **/O1**

  - **MaxSpeed** -  **/O2**

  - **Full** -  **/Ox**

    자세한 내용은 [/O 옵션(코드 최적화)](/cpp/build/reference/o-options-optimize-code)을 참조하세요.

- **PrecompiledHeader**

   선택적 **문자열** 매개 변수입니다.

   빌드 중 미리 컴파일된 헤더( *.pch*) 파일을 만들거나 사용합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **NotUsing** -  *\<none>*

  - **Create** -  **/Yc**

  - **Use** -  **/Yu**

    자세한 내용은 [/Yc(미리 컴파일된 헤더 파일 만들기)](/cpp/build/reference/yc-create-precompiled-header-file) 및 [/Yu(미리 컴파일된 헤더 파일 사용)](/cpp/build/reference/yu-use-precompiled-header-file)를 참조하세요. 또한 이 표의 **PrecompiledHeaderFile** 및 **PrecompiledHeaderOutputFile** 매개 변수도 참조하세요.

- **PrecompiledHeaderFile**

   선택적 **문자열** 매개 변수입니다.

   만들거나 사용할 미리 컴파일된 헤더 파일 이름을 지정합니다.

   자세한 내용은 [/Yc(미리 컴파일된 헤더 파일 만들기)](/cpp/build/reference/yc-create-precompiled-header-file) 및 [/Yu(미리 컴파일된 헤더 파일 사용)](/cpp/build/reference/yu-use-precompiled-header-file)를 참조하세요.

- **PrecompiledHeaderOutputFile**

   선택적 **문자열** 매개 변수입니다.

   기본 경로 이름을 사용하는 대신 미리 컴파일된 헤더의 경로 이름을 지정합니다.

   자세한 내용은 [/Fp(.pch 파일 이름 지정)](/cpp/build/reference/fp-name-dot-pch-file)를 참조하세요.

- **PreprocessKeepComments**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 전처리 중 주석을 유지합니다.

   자세한 내용은 [/C(전처리 중에 주석 유지)](/cpp/build/reference/c-preserve-comments-during-preprocessing)를 참조하세요.

- **PreprocessorDefinitions**

   선택적 `String[]` 매개 변수입니다.

   소스 파일에 대한 전처리 기호를 정의합니다.

   자세한 내용은 [/D(전처리가 정의)](/cpp/build/reference/d-preprocessor-definitions)를 참조하세요.

- **PreprocessOutput**

   선택적 `ITaskItem[]` 매개 변수입니다.

   작업에서 사용하고 내보낼 수 있는 전처리기 출력 항목의 배열을 정의합니다.

- **PreprocessOutputPath**

   선택적 `String` 매개 변수입니다.

   **PreprocessToFile** 매개 변수가 전처리된 출력을 작성할 출력 파일의 이름을 지정합니다.

   자세한 내용은 [/Fi(출력 파일 이름 전처리)](/cpp/build/reference/fi-preprocess-output-file-name)를 참조하세요.

- **PreprocessSuppressLineNumbers**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 C 및 C++소스 파일을 전처리하고, 표준 출력 디바이스에 전처리된 파일을 복사합니다.

   자세한 내용은 [/EP(#line 지시문 없이 stdout로 전처리)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives)를 참조하세요.

- **PreprocessToFile**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 C 및 C++ 소스 파일을 전처리하고, 전처리된 출력을 파일에 작성합니다.

   자세한 내용은 [/P(파일로 전처리)](/cpp/build/reference/p-preprocess-to-a-file)를 참조하세요.

- **ProcessorNumber**

   선택적 `Integer` 매개 변수입니다.

   다중 프로세서 컴파일에서 사용할 최대 프로세서 수를 지정합니다. 이 매개 변수는 **MultiProcessorCompilation** 매개 변수와 결합하여 사용합니다.

- **ProgramDataBaseFileName**

   선택적 `String` 매개 변수입니다.

   PDB(프로그램 데이터베이스) 파일에 대한 파일 이름을 지정합니다.

   자세한 내용은 [/Fd(프로그램 데이터베이스 파일 이름)](/cpp/build/reference/fd-program-database-file-name)를 참조하세요.

- **RuntimeLibrary**

   선택적 `String` 매개 변수입니다.

   다중 스레드 모듈이 DLL인지 나타내고, 런타임 라이브러리의 정품 버전 또는 디버그 버전을 선택합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **MultiThreaded** -  **/MT**

  - **MultiThreadedDebug** -  **/MTd**

  - **MultiThreadedDLL** -  **/MD**

  - **MultiThreadedDebugDLL** -  **/MDd**

    자세한 내용은 [/MD, /MT, /LD(런타임 라이브러리 사용)](/cpp/build/reference/md-mt-ld-use-run-time-library)를 참조하세요.

- **RuntimeTypeInfo**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 런타임에 C++ 개체의 형식(런타임 형식 정보)을 검사하는 코드를 추가합니다.

   자세한 내용은 [/GR(런타임 형식 정보 사용)](/cpp/build/reference/gr-enable-run-time-type-information)을 참조하세요.

- **ShowIncludes**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 컴파일러가 포함 파일의 목록을 출력하게 합니다.

   자세한 내용은 [/showIncludes(포함 파일 나열)](/cpp/build/reference/showincludes-list-include-files)를 참조하세요.

- **SmallerTypeCheck**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 값이 더 작은 데이터 형식에 할당되어 데이터 손실이 발생하면 런타임 오류를 보고합니다.

   자세한 내용은 [/RTC(런타임 오류 검사)](/cpp/build/reference/rtc-run-time-error-checks)의 **/RTCc** 옵션을 참조하세요.

- **Sources**

   필수 `ITaskItem[]` 매개 변수입니다.

   공백으로 구분된 소스 파일 목록을 지정합니다.

- **StringPooling**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 컴파일러가 프로그램 이미지에서 동일한 문자열의 복사본 하나를 만들 수 있습니다.

   자세한 내용은 [/GF(중복 문자열 제거)](/cpp/build/reference/gf-eliminate-duplicate-strings)를 참조하세요.

- **StructMemberAlignment**

   선택적 `String` 매개 변수입니다.

   구조체의 모든 멤버에 대해 바이트 맞춤을 지정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **Default** -  **/Zp1**

  - **1Byte** -  **/Zp1**

  - **2Bytes** -  **/Zp2**

  - **4Bytes** -  **/Zp4**

  - **8Bytes** -  **/Zp8**

  - **16Bytes** -  **/Zp16**

    자세한 내용은 [/Zp(구조체 멤버 맞춤)](/cpp/build/reference/zp-struct-member-alignment)를 참조하세요.

- **SuppressStartupBanner**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.

   자세한 내용은 [/nologo(시작 배너 표시 안 함) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp)를 참조하세요.

- **TrackerLogDirectory**

   선택적 `String` 매개 변수입니다.

   이 작업에 대한 추적 로그를 저장할 중간 디렉터리를 지정합니다.

   자세한 내용은 이 표의 **TLogReadFiles** 및 **TLogWriteFiles** 매개 변수를 참조하세요.

- **TreatSpecificWarningsAsErrors**

   선택적 **String[]** 매개 변수입니다.

   지정된 컴파일러 경고 목록을 오류로 처리합니다.

   자세한 내용은 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX(경고 수준)](/cpp/build/reference/compiler-option-warning-level)의 **/we**`n` 옵션을 참조하세요.

- **TreatWarningAsError**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 모든 컴파일러 경고를 오류로 처리합니다.

   자세한 내용은 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX(경고 수준)](/cpp/build/reference/compiler-option-warning-level)의 **/WX** 옵션을 참조하세요.

- **TreatWChar_tAsBuiltInType**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 `wchar_t` 형식을 네이티브 형식으로 처리합니다.

   자세한 내용은 [/Zc:wchar_t(wchar_t는 네이티브 형식임)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type)를 참조하세요.

- **UndefineAllPreprocessorDefinitions**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 컴파일러가 정의하는 Microsoft 관련 기호를 정의 해제합니다.

   자세한 내용은 [/U, /u(기호 정의 해제)](/cpp/build/reference/u-u-undefine-symbols)의 **/u** 옵션을 참조하세요.

- **UndefinePreprocessorDefinitions**

   선택적 `String[]` 매개 변수입니다.

   정의 해제할 하나 이상의 전처리기 기호 목록을 지정합니다.

   자세한 내용은 [/U, /u(기호 정의 해제)](/cpp/build/reference/u-u-undefine-symbols)의 **/U** 옵션을 참조하세요.

- **UseFullPaths**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 진단에서 컴파일러에 전달된 소스 코드 파일의 전체 경로를 표시합니다.

   자세한 내용은 [/FC(진단 소스 코드 파일의 전체 경로)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics)를 참조하세요.

- **UseUnicodeForAssemblerListing**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 출력 파일을 UTF-8 형식으로 만듭니다.

   자세한 내용은 [/FA, /Fa(목록 파일)](/cpp/build/reference/fa-fa-listing-file)의 **/FAu** 옵션을 참조하세요.

- **WarningLevel**

   선택적 `String` 매개 변수입니다.

   컴파일러에서 생성할 가장 높은 수준의 경고를 지정합니다.

   각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

  - **TurnOffAllWarnings** -  **/W0**

  - **Level1** -  **/W1**

  - **Level2** -  **/W2**

  - **Level3** -  **/W3**

  - **Level4** -  **/W4**

  - **EnableAllWarnings** -  **/Wall**

    자세한 내용은 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX(경고 수준)](/cpp/build/reference/compiler-option-warning-level)의 **/W**_n_ 옵션을 참조하세요.

- **WholeProgramOptimization**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 전체 프로그램 최적화를 사용합니다.

   자세한 내용은 [/GL(전체 프로그램 최적화)](/cpp/build/reference/gl-whole-program-optimization)을 참조하세요.

- **XMLDocumentationFileName**

   선택적 `String` 매개 변수입니다.

   생성된 XML 문서 파일의 이름을 지정합니다. 이 매개 변수는 파일 또는 디렉터리 이름일 수 있습니다.

   자세한 내용은 [/doc(문서 주석 처리) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp)의 `name` 인수를 참조하세요. 또한 이 표의 **GenerateXMLDocumentationFiles** 매개 변수도 참조하세요.

- **MinimalRebuildFromTracking**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 추적된 증분 빌드가 수행됩니다. `false`인 경우 다시 빌드가 수행됩니다.

- **TLogReadFiles**

   선택적 `ITaskItem[]` 매개 변수입니다.

   *읽기 파일 추적 로그*를 나타내는 항목의 배열을 지정합니다.

   읽기 파일 추적 로그( *.tlog*)에는 작업에서 읽은 입력 파일의 이름이 포함되어 있으며, 프로젝트 빌드 시스템에서 증분 빌드를 지원하는 데 이 로그를 사용합니다. 자세한 내용은 이 표의 **TrackerLogDirectory** 및 **TrackFileAccess** 매개 변수를 참조하세요.

- **TLogWriteFiles**

   선택적 `ITaskItem[]` 매개 변수입니다.

   *쓰기 파일 추적 로그*를 나타내는 항목의 배열을 지정합니다.

   쓰기 파일 추적 로그( *.tlog*)에는 작업에서 작성한 출력 파일의 이름이 포함되어 있으며, 프로젝트 빌드 시스템에서 증분 빌드를 지원하는 데 이 로그를 사용합니다. 자세한 내용은 이 표의 **TrackerLogDirectory** 및 **TrackFileAccess** 매개 변수를 참조하세요.

- **TrackFileAccess**

   선택적 `Boolean` 매개 변수입니다.

   `true`인 경우 파일 액세스 패턴을 추적합니다.

   자세한 내용은 이 표의 **TLogReadFiles** 및 **TLogWriteFiles** 매개 변수를 참조하세요.

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
