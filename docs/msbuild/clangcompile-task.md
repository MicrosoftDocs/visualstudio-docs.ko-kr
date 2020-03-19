---
title: ClangCompile 작업 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ClangCompile task
- ClangCompile task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: c1526fbd3c2c0822781f0e011999ddcb9c679170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275468"
---
# <a name="clangcompile-task"></a>ClangCompile 작업

Microsoft C++ 컴파일러 도구 clang.exe를 래핑합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **ClangCompile** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|선택적 **string[]** 매개 변수입니다.<br/><br/>포함 경로에 추가할 디렉터리를 하나 이상 지정합니다. 항목이 여러 개일 때에는 세미콜론으로 구분합니다.<br/><br/>대신 `-I[path]`를|
|**AdditionalOptions**|선택적 **string** 매개 변수입니다.|
|**BufferSecurityCheck**|선택적 **string** 매개 변수입니다.<br/><br/>보안 검사를 통해 스택 버퍼 오버런, 프로그램의 보안에 대해 일반적으로 시도되는 공격을 검색할 수 있습니다. <br/><br/>대신 `fstack-protector`를|
|**BuildingInIde**|선택적 **bool** 매개 변수입니다.|
|**CLanguageStandard**|선택적 **string** 매개 변수입니다.<br/><br/>C 언어 표준을 결정합니다.<br/><br/>값이 `std=[value]`c89 **,** c99 **,** c11 **,** gnu99**또는**gnu11**인** 를 사용합니다.|
|**ClangVersion**|선택적 **string** 매개 변수입니다.|
|**CompileAs**|선택적 **string** 매개 변수입니다.<br/><br/>.c 및 .cpp 파일에 대한 컴파일 언어 옵션을 선택합니다. 기본값은 .c 또는 .cpp 확장명에 따라 감지됩니다.<br/><br/>`-x c`, `-x c++`를 사용합니다.|
|**CppLanguageStandard**|선택적 **string** 매개 변수입니다.<br/><br/>C++ 언어 표준을 결정합니다.<br/><br/>값이 `std=[value]`c++98 **,** c++11 **,** c++1y **,** gnu++98 **,** gnu++11**또는**gnu++1y**인** 를 사용합니다.|
|**DataLevelLinking**|선택적 **bool** 매개 변수입니다.<br/><br/>링커 최적화를 사용하면 별도 섹션에서 각 데이터 항목을 내보내 사용하지 않은 데이터를 제거할 수 있습니다.|
|**DebugInformationFormat**|선택적 **string** 매개 변수입니다.<br/><br/>컴파일러에서 생성되는 디버깅 정보 형식을 지정합니다.<br/><br/>**None** - 디버깅 정보를 생성하지 않으므로 컴파일이 더 빨라질 수 있습니다(`g0` 사용).<br/>**FullDebug** - DWARF2 디버그 정보를 생성합니다(`g2 -gdwarf-2` 사용).<br/>**LineNumber** - 줄 번호 정보만 생성합니다(`gline-tables-only` 사용).|
|**EnableNeonCodegen**|선택적 **bool** 매개 변수입니다.<br/><br/>NEON 부동 소수점 하드웨어에 대한 코드 생성을 사용하도록 설정합니다. 이는 arm 아키텍처에만 적용됩니다.|
|**ExceptionHandling**|선택적 **string** 매개 변수입니다.<br/><br/>컴파일러가 사용하는 예외 처리 모델을 지정합니다.<br/><br/>**Disabled** - 예외 처리를 사용하지 않도록 설정합니다(`fno-exceptions` 사용).<br/>**Enabled** - 예외 처리를 사용하도록 설정합니다(`fexceptions` 사용).<br/>**UnwindTables** - 필요한 정적 데이터를 생성하지만 생성된 코드에는 영향을 주지 않습니다(`funwind-tables` 사용).|
|**FloatABI**|선택적 **string** 매개 변수입니다.<br/><br/>부동 소수점 ABI를 선택할 수 있는 선택 옵션입니다.<br/><br/>**soft** - 컴파일러가 부동 소수점 연산에 대한 라이브러리 호출이 포함된 출력을 생성하도록 합니다(`mfloat-abi=soft` 사용).<br/>**softfp** - 하드웨어 부동 소수점 명령을 사용하는 코드 생성을 허용하지만 계속해서 soft-float 호출 규칙을 사용합니다(`mfloat-abi=softfp` 사용).<br/>**hard** - 부동 소수점 명령의 생성을 허용하고 FPU 관련 호출 규칙을 사용합니다(`mfloat-abi=hard` 사용).|
|**ForcedIncludeFiles**|선택적 **string[]** 매개 변수입니다.<br/><br/>하나 이상의 강제 포함 파일입니다.<br/><br/>대신 `-include [name]`를|
|**FunctionLevelLinking**|선택적 **bool** 매개 변수입니다.<br/><br/>컴파일러가 개별 함수를 패키지된 함수(COMDAT)의 형태로 패키지할 수 있게 합니다. 편집에 필요하며 계속 작동합니다.<br/><br/>대신 `ffunction-sections`를|
|**GccToolChain**|선택적 **string** 매개 변수입니다.<br/><br/>Gcc 도구 체인에 대한 폴더 경로입니다.|
|**GNUMode**|선택적 **bool** 매개 변수입니다.<br/><br/>|
|**MSCompatibility**|선택적 **bool** 매개 변수입니다.<br/><br/>완전한 Microsoft C++ 호환성을 사용합니다.|
|**MSCompatibilityVersion**|선택적 **string** 매개 변수입니다.<br/><br/>_MSC_VER에서 보고할 Microsoft 컴파일러 버전 번호를 나타내는 점으로 구분된 값입니다(0 = 정의하지 않음(기본값)).|
|**MSExtensions**|선택적 **bool** 매개 변수입니다.<br/><br/>Microsoft 컴파일러에서 지원하는 일부 비표준 구문을 허용합니다.|
|**MSCompilerVersion**|선택적 **string** 매개 변수입니다.<br/><br/>_MSC_VER에서 보고할 Microsoft 컴파일러 버전 번호입니다(0 = 정의하지 않음(기본값)).|
|**MSVCErrorReport**|선택적 **bool** 매개 변수입니다.<br/><br/>Visual Studio에서 파일 및 줄 정보의 구문 분석에 사용할 수 있는 오류를 보고합니다.|
|**ObjectFileName**|선택적 **string** 매개 변수입니다.<br/><br/>기본 개체 파일 이름을 재정의할 이름을 지정합니다. 파일 또는 디렉터리 이름일 수 있습니다.<br/><br/>대신 `/Fo[name]`를|
|**OmitFramePointers**|선택적 **bool** 매개 변수입니다.<br/><br/>호출 스택에서 프레임 포인터를 생성하지 않습니다.|
|**Optimization**|선택적 **string** 매개 변수입니다.<br/><br/>애플리케이션의 최적화 수준을 지정합니다.<br/><br/>**Custom** - 사용자 지정 최적화입니다.<br/>**Disabled** - 최적화를 사용하지 않도록 설정합니다(`O0` 사용).<br/>**MinSize** - 크기에 맞게 최적화합니다(`Os` 사용).<br/>**MaxSpeed** - 속도에 맞게 최적화합니다(`O2` 사용).<br/>**Full** - 고가의 최적화입니다(`O3` 사용).|
|**PositionIndependentCode**|선택적 **bool** 매개 변수입니다.<br/><br/>공유 라이브러리에서 사용할 PIC(위치 독립적 코드)를 생성합니다.|
|**PrecompiledHeader**|선택적 **string** 매개 변수입니다.<br/><br/>빌드하는 동안 미리 컴파일된 헤더를 만들거나 사용하도록 설정합니다.|
|**PrecompiledHeaderFile**|선택적 **string** 매개 변수입니다.<br/><br/>미리 컴파일된 헤더 파일에 사용할 헤더 파일 이름을 지정합니다. 이 파일은 빌드 중에 **강제 포함 파일**에도 추가됩니다.|
|**PrecompiledHeaderOutputFileDirectory**|선택적 **string** 매개 변수입니다.<br/><br/>생성된 미리 컴파일된 헤더에 대한 디렉터리를 지정합니다. 이 디렉터리는 빌드 중에 **추가 포함 디렉터리**에도 추가됩니다.|
|**PrecompiledHeaderCompileAs**|선택적 **string** 매개 변수입니다.<br/><br/>미리 컴파일된 헤더 파일에 대한 컴파일 언어 옵션을 선택합니다.<br/><br/>`-x c-header`, `-x c++-header`를 사용합니다.|
|**PreprocessorDefinitions**|선택적 **string[]** 매개 변수입니다.<br/><br/>소스 파일에 대한 전처리 기호를 정의합니다.<br/><br/>대신 `-D`를|
|**RuntimeLibrary**|선택적 **string** 매개 변수입니다.<br/><br/>링크할 런타임 라이브러리를 지정합니다.<br/><br/>`MSVC /MT`, `/MTd`, `/MD`, `/MDd` 스위치를 사용합니다.<br/><br/>**MultiThreaded** - 애플리케이션에서 런타임 라이브러리의 다중 스레드 정적 버전을 사용하게 됩니다.<br/>**MultiThreadedDebug** - _DEBUG 및 _MT를 정의합니다. 또한, 이 옵션은 컴파일러가 .obj 파일에 라이브러리 이름 LIBCMTD.lib를 배치하여 링커가 LIBCMTD.lib를 사용하여 외부 기호를 확인하도록 만듭니다.<br/>**MultiThreadedDLL** - 애플리케이션에서 런타임 라이브러리의 다중 스레드별 및 DLL별 버전을 사용하게 됩니다. _MT 및 _DLL을 정의하고 컴파일러가 라이브러리 이름 MSVCRT.lib를 .obj 파일에 배치하게 만듭니다.<br/>**MultiThreadedDebugDLL** - _DEBUG, _MT 및 _DLL을 정의하고 애플리케이션에서 런타임 라이브러리의 디버그 다중 스레드별 및 DLL별 버전을 사용하게 됩니다. 또한 컴파일러가 라이브러리 이름 MSVCRTD.lib를 .obj 파일에 배치하게 만듭니다.|
|**RuntimeTypeInfo**|선택적 **bool** 매개 변수입니다.<br/><br/>런타임에 C++ 개체의 형식(런타임 형식 정보)을 검사하는 코드를 추가합니다.<br/><br/>`frtti`, `fno-rtti`를 사용합니다.|
|**ShowIncludes**|선택적 **bool** 매개 변수입니다.<br/><br/>컴파일러 출력으로 포함 파일 목록을 생성합니다.<br/><br/>대신 `-H`를|
|**Sources**|필수 **ITaskItem[]** 매개 변수입니다.|
|**StrictAliasing**|선택적 **bool** 매개 변수입니다.<br/><br/>가장 엄격한 앨리어싱 규칙을 가정합니다. 한 형식의 개체는 다른 형식의 개체와 동일한 주소에 있을 수 없는 것으로 간주됩니다.|
|**Sysroot**|선택적 **string** 매개 변수입니다.<br/><br/>헤더 및 라이브러리의 루트 디렉터리에 대한 폴더 경로입니다.|
|**TargetArch**|선택적 **string** 매개 변수입니다.<br/><br/>대상 아키텍처입니다.|
|**ThumbMode**|선택적 **string** 매개 변수입니다.<br/><br/>Thumb 마이크로 아키텍처용으로 실행되는 코드를 생성합니다. 이는 arm 아키텍처에만 적용됩니다.<br/><br/>**Thumb** - Thumb 코드를 생성합니다(`mthumb` 사용).<br/>**ARM** - Arm 코드를 생성합니다(`marm` 사용).<br/>**Disabled** - 선택한 플랫폼에 적용되지 않는 옵션입니다.|
|**TrackerLogDirectory**|선택적 **string** 매개 변수입니다.<br/><br/>추적기 로그 디렉터리입니다.|
|**TreatWarningAsError**|선택적 **bool** 매개 변수입니다.<br/><br/>모든 컴파일러 경고를 오류로 처리합니다.<br/><br/>새 프로젝트인 경우 모든 컴파일에서 `/WX`를 사용하는 것이 좋습니다. 모든 경고를 해결하면 찾기 어려운 코드 오류를 최소화할 수 있습니다.|
|**UndefinePreprocessorDefinitions**|선택적 **string[]** 매개 변수입니다.<br/><br/>전처리기 정의 해제를 하나 이상 지정합니다.<br/><br/>대신 `-U [macro]`를|
|**UndefineAllPreprocessorDefinitions**|선택적 **bool** 매개 변수입니다.<br/><br/>이전에 정의한 모든 전처리기 값을 정의 해제합니다.<br/><br/>대신 `-undef`를|
|**UseMultiToolTask**|선택적 **bool** 매개 변수입니다.<br/><br/>다중 프로세서 컴파일입니다.|
|**UseShortEnums**|선택적 **bool** 매개 변수입니다.<br/><br/>열거형 형식은 가능한 값의 입력 집합에 필요한 만큼의 바이트만 사용합니다.|
|**자세한 정보**|선택적 **bool** 매개 변수입니다.<br/><br/>실행할 명령을 표시하고 자세한 정보 표시 출력을 사용합니다.|
|**WarningLevel**|선택적 **string** 매개 변수입니다.<br/><br/>컴파일러가 코드 오류를 처리하는 수준을 선택합니다. 다른 플래그는 **추가 옵션**에 직접 추가해야 합니다(`/w`, `/Weverything` 참조).<br/><br/>**TurnOffAllWarnings** - 모든 컴파일러 경고를 사용하지 않도록 설정합니다(`w` 사용).<br/>**EnableAllWarnings** - 기본적으로 사용하지 않도록 설정된 경고를 포함한 모든 경고를 사용하도록 설정합니다(`Wall` 사용).|

## <a name="see-also"></a>참고 항목

[작업 참조](../msbuild/msbuild-task-reference.md)