---
title: C++ Core Guidelines 사용
ms.date: 08/14/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
dev_langs:
- CPP
ms.openlocfilehash: 762ba639c1443bb737087233d04c9e3753f2f455
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807078"
---
# <a name="use-the-c-core-guidelines-checkers"></a>C++ Core Guidelines 검사기 사용

C++ 핵심 지침은 C++ C++ 전문가와 디자이너가 만든 코딩에 대 한 지침, 규칙 및 모범 사례 집합입니다. Visual Studio는 현재에 대 한 C++코드 분석 도구의 일부로 이러한 규칙의 하위 집합을 지원 합니다. 핵심 지침 체커는 visual Studio 2017 및 Visual Studio 2019에 기본적으로 설치 되며, [Visual studio 2015 용 NuGet 패키지로 제공](#vs2015_corecheck)됩니다.

## <a name="the-c-core-guidelines-project"></a>C++ 핵심 지침 프로젝트

Bjarne Stroustrup 및 기타 사용자가 만든 C++ 핵심 지침은 최신 C++ 안전 하 고 효과적으로 사용 하는 방법에 대 한 지침입니다. 지침은 정적 형식 안전성 및 리소스 안전성을 강조 합니다. 이는 언어에서 가장 오류가 발생 하기 쉬운 부분을 제거 하거나 최소화 하는 방법을 파악 하 고 안정적인 방식으로 코드를 더 간단 하 고 더 효율적으로 만드는 방법을 제안 합니다. 이러한 지침은 Standard C++ Foundation에서 유지 관리 됩니다. 자세히 알아보려면 [GitHub](https://github.com/isocpp/CppCoreGuidelines)에서 설명서, [ C++ 핵심 지침](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)및 C++ 핵심 지침 문서 프로젝트 파일에 액세스를 참조 하세요.

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>코드 분석 C++ 에서 핵심 검사 지침 사용
프로젝트에 대 한 **속성 페이지** 대화 상자의 **코드 분석** 섹션에서 **빌드 시 코드 분석 사용** 확인란을 선택 하 여 프로젝트에 대해 코드 분석을 사용 하도록 설정할 수 있습니다.

![코드 분석 일반 설정의 속성 페이지](media/cppcorecheck_codeanalysis_general.png)

핵심 검사 규칙 C++ 의 하위 집합은 코드 분석을 사용 하도록 설정한 경우 기본적으로 실행 되는 Microsoft Native 권장 규칙 집합에 포함 되어 있습니다. 추가 핵심 검사 규칙을 사용 하도록 설정 하려면 드롭다운을 클릭 하 고 포함 하려는 규칙 집합을 선택 합니다.

![추가 C++ 핵심 검사 규칙 집합 드롭다운](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>예제
핵심 검사 규칙에서 C++ 찾을 수 있는 몇 가지 문제의 예는 다음과 같습니다.

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

이 예제에서는 핵심 검사 규칙에서 C++ 찾을 수 있는 몇 가지 경고를 보여 줍니다.

- C26494은 규칙 유형입니다. 5: 항상 개체를 초기화 합니다.

- C26485는 규칙 범위입니다. 3: 배열-포인터 감소 하지 않습니다.

- C26481는 규칙 범위입니다. 1: 포인터 산술 연산을 사용 하지 않습니다. 대신 `span` 를 사용하세요.

이 코드 C++ 를 컴파일할 때 핵심 검사 코드 분석 규칙 집합을 설치 하 고 사용 하도록 설정 하는 경우 처음 두 경고는 출력 되지만 세 번째 경고는 표시 되지 않습니다. 예제 코드의 빌드 출력은 다음과 같습니다.

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ 핵심 지침은 더 안전 하 고 더 안전 하 게 코드를 작성 하는 데 도움이 됩니다. 그러나 규칙이 나 프로필을 적용 하지 않아야 하는 인스턴스가 있는 경우 코드에서 직접 표시 하지 않는 것이 쉽습니다. @No__t_0 특성을 사용 하 여 다음 코드 C++ 블록에서 규칙 위반을 검색 하 고 보고 하지 않도록 핵심 검사를 유지할 수 있습니다. 개별 문을 표시 하 여 특정 규칙을 표시 하지 않을 수 있습니다. 특정 규칙 번호를 포함 하지 않고 `[[gsl::suppress(bounds)]]`을 작성 하 여 전체 범위 프로필을 표시 하지 않을 수도 있습니다.

## <a name="supported-rule-sets"></a>지원 되는 규칙 집합
C++ 핵심 지침 검사기에 새 규칙을 추가 하면 기존 코드에 대해 생성 되는 경고 수가 늘어날 수 있습니다. 미리 정의 된 규칙 집합을 사용 하 여 사용할 규칙의 종류를 필터링 할 수 있습니다.
대부분의 규칙에 대 한 참조 항목은 [Visual Studio C++ Core 검사 참조](code-analysis-for-cpp-corecheck.md)에 있습니다.

Visual Studio 2017 버전 15.3에서 지원 되는 규칙 집합은 다음과 같습니다.
- **소유자 포인터 규칙** [은 C++ 핵심 지침에서 소유자 \<T > 관련 된 리소스 관리 검사를](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)적용 합니다.

- **Const 규칙** [은 C++ 핵심 지침에서 const 관련 검사를](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)적용 합니다.

- **원시 포인터 규칙** [은 C++ 핵심 지침에서 원시 포인터 관련 리소스 관리 검사를](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)적용 합니다.

- **고유 포인터 규칙** [은 C++ 핵심 지침의 고유 포인터 의미 체계를 사용 하 여 형식과 관련 된 리소스 관리 검사를](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)적용 합니다.

- **범위 규칙** 은 [ C++ 핵심 지침의 범위 프로필](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)을 적용 합니다.

- **형식 규칙** 은 [ C++ 핵심 지침의 형식 프로필](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)을 적용 합니다.

**Visual Studio 2017 버전 15.5**:

- **클래스 규칙** 특수 멤버 함수 및 가상 사양의 적절 한 사용에 초점을 맞춘 몇 가지 규칙입니다. [클래스 및 클래스 계층 구조](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class)에 권장 되는 검사의 하위 집합입니다.
- **동시성 규칙** 잘못 선언 된 가드 개체를 catch 하는 단일 규칙 자세한 내용은 [concurrency와 관련 된 지침](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency)을 참조 하세요.
- **선언 규칙** [인터페이스 지침](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) 의 몇 가지 규칙은 전역 변수를 선언 하는 방법에 중점을 둡니다.
- **함수 규칙** @No__t_1 지정자를 도입 하는 데 도움이 되는 두 가지 검사입니다. 이는 [clear 함수 디자인 및 구현](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions)에 대 한 지침의 일부입니다.
- **공유 포인터 규칙** [리소스 관리](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) 지침 적용의 일부로 공유 포인터가 함수로 전달 되거나 로컬로 사용 되는 방법과 관련 된 몇 가지 규칙을 추가 했습니다.
- **스타일 규칙** 차단을를 사용 하는 [것은 간단](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto)하지만 중요 한 검사입니다. 이는에서 C++코딩 스타일을 개선 하 고 식과 문을 사용 하는 첫 번째 단계입니다.

**Visual Studio 2017 버전 15.6**:

- **산술 규칙** 산술 [오버플로](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [부호 없는 서명 된 작업](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) 및 [비트 조작을](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative)검색 하는 규칙입니다.

경고를 하나 또는 몇 개의 그룹 으로만 제한 하도록 선택할 수 있습니다. **기본 최소** 및 **기본 권장** 규칙 집합에는 C++ 다른 PREfast 검사 외에도 핵심 검사 규칙이 포함 됩니다. 사용 가능한 규칙 집합을 보려면 프로젝트 속성 대화 상자를 열고 **코드 Analysis\General**를 선택한 다음 **규칙 집합** 콤보 상자에서 드롭다운을 열고 **여러 규칙 집합 선택**을 선택 합니다. Visual Studio에서 규칙 집합을 사용 하는 방법에 대 한 자세한 내용은 [규칙 집합을 사용 하 여 코드 분석 규칙 그룹화](using-rule-sets-to-group-code-analysis-rules.md)를 참조 하세요.

## <a name="macros"></a>매크로

핵심 C++ 지침 검사기는 코드에서 전체 경고 범주를 더 쉽게 표시 하지 않도록 하는 매크로를 정의 하는 헤더 파일을 제공 합니다.

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

이러한 매크로는 규칙 집합에 해당 하며 공백으로 구분 된 경고 번호 목록으로 확장 됩니다. 적절 한 pragma 구문을 사용 하 여 프로젝트 또는 코드 섹션에 대 한 유용한 규칙 집합을 구성할 수 있습니다. 다음 예제에서 코드 분석은 누락 된 상수 한정자에 대해서만 경고를 표시 합니다.

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>특성

Microsoft C++ 컴파일러는 gsl 표시 안 함 특성을 제한적으로 지원 합니다. 이를 사용 하 여 함수 내에서 식 및 블록 문에 대 한 경고를 표시 하지 않을 수 있습니다.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>명령줄 옵션을 사용 하 여 분석 표시 안 함

#Pragmas 대신 파일의 속성 페이지에서 명령줄 옵션을 사용 하 여 프로젝트 또는 단일 파일에 대 한 경고를 표시 하지 않을 수 있습니다. 예를 들어 파일에 대해 26400 경고를 사용 하지 않도록 설정 하려면 다음을 수행 합니다.

1. 에서 파일을 마우스 오른쪽 단추로 클릭 **솔루션 탐색기**

2. **속성 선택 | C/C++| 명령줄**

3. **추가 옵션** 창에서 `/wd26400`을 추가 합니다.

명령줄 옵션을 사용 하 여 `/analyze-`를 지정 하 여 파일에 대 한 모든 코드 분석을 일시적으로 사용 하지 않도록 설정할 수 있습니다. 이렇게 하면 ' */analyze '를 '/analyze-'로 재정의*하는 경고 D9025 생성 되며 나중에 코드 분석을 다시 사용 하도록 설정 하는 것을 알려 줍니다.

## <a name="corecheck_per_file"></a>특정 프로젝트 C++ 파일에서 핵심 지침 검사기 사용

때로는 포커스가 있는 코드 분석을 수행 하 고 여전히 Visual Studio IDE를 사용 하는 것이 유용할 수 있습니다. 다음 샘플 시나리오를 사용 하 여 빌드 시간을 절약 하 고 결과를 보다 쉽게 필터링 할 수 있습니다.

1. 명령 셸에서 `esp.extension` 및 `esp.annotationbuildlevel` 환경 변수를 설정 합니다.
2. 이러한 변수를 상속 하려면 명령 셸에서 Visual Studio를 엽니다.
3. 프로젝트를 로드 하 고 해당 속성을 엽니다.
4. 코드 분석을 사용 하도록 설정 하 고, 적절 한 규칙 집합을 선택 하지만 코드 분석 확장을 사용 하지 않습니다.
5. C++ 핵심 지침 검사기를 사용 하 여 분석 하려는 파일로 이동 하 여 해당 속성을 엽니다.
6. **C/C++\ 명령줄 옵션** 을 선택 하 고 `/analyze:plugin EspXEngine.dll` 추가
7. 미리 컴파일된 헤더 (**C/C++\ 미리 컴파일된 헤더**)를 사용 하지 않도록 설정 합니다. 확장 엔진이 미리 컴파일된 헤더 (PCH)에서 내부 정보를 읽으려고 할 수 있으므로이 작업이 필요 합니다. PCH가 기본 프로젝트 옵션으로 컴파일된 경우에는 호환 되지 않습니다.
8. 프로젝트를 다시 빌드합니다. 모든 파일에서 일반적인 PREFast 검사를 실행 해야 합니다. 핵심 지침 C++ 검사기는 기본적으로 사용 하도록 설정 되어 있지 않으므로이를 사용 하도록 구성 된 파일 에서만 실행 해야 합니다.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Visual Studio 외부에서 C++ 핵심 지침 검사기를 사용 하는 방법

자동화 된 빌드에서 핵심 C++ 지침 검사를 사용할 수 있습니다.

### <a name="msbuild"></a>MSBuild
네이티브 코드 분석 검사기 (PREfast)는 사용자 지정 대상 파일을 통해 MSBuild 환경에 통합 됩니다. 프로젝트 속성을 사용 하 여 사용 하도록 설정 하 고 PREfast C++ 을 기반으로 하는 핵심 지침 검사기를 추가할 수 있습니다.

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Microsoft .Cpp .targets 파일을 가져오기 전에 이러한 속성을 추가 해야 합니다. 특정 규칙 집합을 선택 하거나 사용자 지정 규칙 집합을 만들거나 다른 PREfast 검사를 포함 하는 기본 규칙 집합을 사용할 수 있습니다.

[앞서 설명한](#corecheck_per_file)것과 C++ 동일한 방법으로 MSBuild 파일을 사용 하 여 지정 된 파일 에서만 코어 검사기를 실행할 수 있습니다. 환경 변수는 `BuildMacro` 항목을 사용 하 여 설정할 수 있습니다.

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

프로젝트 파일을 수정 하지 않으려는 경우 명령줄에서 속성을 전달할 수 있습니다.

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>비 MSBuild 프로젝트

MSBuild를 사용 하지 않는 빌드 시스템을 사용 하는 경우 검사기를 계속 실행할 수 있지만 코드 분석 엔진 구성의 내부에 대해 잘 알고 있어야 합니다. 이러한 내부는 나중에 지원 되지 않을 수도 있습니다.

몇 가지 환경 변수를 설정 하 고 컴파일러에 대 한 적절 한 명령줄 옵션을 사용 해야 합니다. 컴파일러에 대 한 특정 경로, 포함 디렉터리 등을 검색할 필요가 없도록 "네이티브 도구 명령 프롬프트" 환경에서 작업 하는 것이 좋습니다.

1. **환경 변수**
   - 이를 `set esp.extensions=cppcorecheck.dll` 하 여 엔진에서 C++ 핵심 지침 모듈을 로드 하도록 지시 합니다.
   - `set esp.annotationbuildlevel=ignore` SAL 주석을 처리 하는 논리를 사용 하지 않도록 설정 합니다. 주석은 C++ 핵심 지침 검사기의 코드 분석에는 영향을 주지 않지만 처리에는 시간이 오래 걸릴 수도 있습니다. 이 설정은 선택 사항 이지만 매우 권장 됩니다.
   - `set caexcludepath=%include%` 표준 헤더에서 발생 하는 경고를 사용 하지 않도록 설정 하는 것이 좋습니다. 여기에 경로를 더 추가할 수 있습니다. 예를 들어 프로젝트의 공용 헤더에 대 한 경로를 추가할 수 있습니다.
2. **명령줄 옵션**
   - `/analyze` 코드 분석을 활성화 합니다 (/analyze: only 및/analyze: quiet를 사용 하는 경우에도 사용).
   - `/analyze:plugin EspXEngine.dll`이 옵션은 PREfast 코드 분석 확장 엔진을 로드 합니다. 이 엔진은 C++ 핵심 지침 검사기를 차례로 로드 합니다.

## <a name="use-the-guideline-support-library"></a>지침 지원 라이브러리 사용
지침 지원 라이브러리는 핵심 지침을 따르는 데 도움이 되도록 설계 되었습니다. GSL에는 오류가 발생 하기 쉬운 구문을 보다 안전한 대체 항목으로 바꿀 수 있는 정의가 포함 되어 있습니다. 예를 들어 `T*, length` 매개 변수 쌍을 `span<T>` 형식으로 바꿀 수 있습니다. GSL은 [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl)에서 사용할 수 있습니다. 라이브러리는 오픈 소스 이므로 소스를 보거나 의견을 올리거나 참가할 수 있습니다. 프로젝트는 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)에서 찾을 수 있습니다.

## <a name="vs2015_corecheck"></a>Visual Studio C++ 2015 프로젝트의 핵심 검사 지침 사용

Visual Studio 2015을 사용 하는 경우 C++ 핵심 검사 코드 분석 규칙 집합은 기본적으로 설치 되지 않습니다. Visual Studio 2015에서 핵심 검사 코드 분석 도구를 C++ 사용 하려면 몇 가지 추가 단계를 수행 해야 합니다. Microsoft에서는 Nuget 패키지를 사용 하 여 Visual Studio 2015 프로젝트에 대 한 지원을 제공 합니다. 패키지 이름은 CppCoreCheck입니다 .이 패키지는 [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck)에서 사용할 수 있습니다. 이 패키지에는 Visual Studio 2015 이상 업데이트 1이 설치 되어 있어야 합니다.

또한 패키지는 다른 패키지를 종속성으로 설치 합니다 .이는 헤더 전용의 GSL (지침 지원 라이브러리)입니다. GSL는 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)의 GitHub 에서도 사용할 수 있습니다.

코드 분석 규칙이 로드 되는 방식으로 인해 Visual Studio 2015 내에서 확인 하려는 각 C++ 프로젝트에 CppCoreCheck NuGet 패키지를 설치 해야 합니다.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Visual Studio 2015에서 프로젝트에 CppCoreCheck 패키지를 추가 하려면

1. **솔루션 탐색기**에서 패키지를 추가 하려는 솔루션의 프로젝트에 대 한 상황에 맞는 메뉴를 마우스 오른쪽 단추로 클릭 하 여 엽니다. Nuget 패키지 **관리** 를 선택 하 여 **nuget 패키지 관리자**를 엽니다.

2. **NuGet 패키지 관리자** 창에서 CppCoreCheck를 검색 합니다.

    ![Nuget 패키지 관리자 창에 CppCoreCheck 패키지 표시](../code-quality/media/cppcorecheck_nuget_window.png)

3. CppCoreCheck 패키지를 선택한 후 **설치** 단추를 선택 하 여 프로젝트에 규칙을 추가 합니다.

   NuGet 패키지는 프로젝트에 대해 코드 분석을 사용 하도록 설정할 때 호출 되는 프로젝트에 다른 Msbuild.exe *.targets* 파일을 추가 합니다. 이 *.targets* 파일은 Visual Studio C++ code 분석 도구에 대 한 추가 확장으로 핵심 검사 규칙을 추가 합니다. 패키지가 설치 될 때 속성 페이지 대화 상자를 사용 하 여 해제 된 및 실험적 규칙을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

## <a name="see-also"></a>참조

- [Visual Studio C++ Core 검사 참조](code-analysis-for-cpp-corecheck.md)
