---
title: C++ 핵심 지침 검사기 사용 | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 946b46bfb5101154832e10b61cd861b0c104dc14
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275294"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ Core Guidelines 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Core Guidelines는 이식 가능한 집합 지침, 규칙 및 C++ 전문가가 및 디자이너에서 생성하는 C++에서 코딩 하는 방법에 대 한 모범 사례입니다.  이제 Visual Studio에서 코드 분석 도구에 대 한 추가 규칙을 만들어 C++ 핵심 지침을 준수 하는지 확인 하 고 향상 된 기능을 제안 하는 추가 기능 패키지를 지원 합니다.  
  
## <a name="the-c-core-guidelines-project"></a>C++ Core Guidelines 프로젝트  
 C++ Core Guidelines를 안전 하 게 하 고 효과적으로 최신 C++를 사용 하는 데는 Bjarne Stroustrup 등에서 생성 합니다. 지침은 정적 형식 안전성 및 리소스 안전성을 강조 합니다. 이는 언어에서 가장 오류가 발생 하기 쉬운 부분을 제거 하거나 최소화 하는 방법을 파악 하 고 안정적인 방식으로 코드를 더 간단 하 고 더 효율적으로 만드는 방법을 제안 합니다. 이러한 지침 표준 C++ Foundation에서 유지 됩니다. 자세히 알아보려면 [GitHub](https://github.com/isocpp/CppCoreGuidelines)에서 설명서, [ C++ 핵심 지침](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)및 C++ 핵심 지침 문서 프로젝트 파일에 액세스를 참조 하세요.  
  
 Microsoft는 Nuget C++ 패키지를 사용 하 여 C++ 프로젝트에 추가할 수 있는 핵심 검사 코드 분석 규칙 집합을 만들어 핵심 지침 활동을 지원 합니다. 패키지 이름은 CppCoreCheck입니다 .이 패키지는 [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck)에서 사용할 수 있습니다. 이 패키지에는 Visual Studio 2015 이상 업데이트 1이 설치 되어 있어야 합니다.  
  
 또한 패키지는 다른 패키지를 종속성으로 설치 합니다 .이는 헤더 전용의 GSL (지침 지원 라이브러리)입니다. GSL는 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)의 GitHub 에서도 사용할 수 있습니다.  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>코드 분석에서 C++ Core Check 지침을 사용 하도록 설정  
 C++ 핵심 검사 코드 분석 도구를 사용 하려면 Visual Studio 내에서 확인 하려는 각 C++ 프로젝트에 CppCoreCheck NuGet 패키지를 설치 합니다.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>CppCoreCheck 패키지를 프로젝트에 추가 하려면  
  
1. **솔루션 탐색기**에서 패키지를 추가 하려는 솔루션의 프로젝트에 대 한 상황에 맞는 메뉴를 마우스 오른쪽 단추로 클릭 하 여 엽니다. Nuget 패키지 **관리** 를 선택 하 여 **nuget 패키지 관리자**를 엽니다.  
  
2. **NuGet 패키지 관리자** 창에서 CppCoreCheck를 검색 합니다.  
  
    ![Nuget 패키지 관리자 창에 CppCoreCheck 패키지 표시](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. CppCoreCheck 패키지를 선택한 후 **설치** 단추를 선택 하 여 프로젝트에 규칙을 추가 합니다.  
  
   NuGet 패키지는 프로젝트에 대해 코드 분석을 사용 하도록 설정할 때 호출 되는 프로젝트에 다른 Msbuild.exe .targets 파일을 추가 합니다. 이 .targets 파일은 Visual Studio C++ code 분석 도구에 대 한 추가 확장으로 핵심 검사 규칙을 추가 합니다.  
  
   프로젝트에 대 한 **속성 페이지** 대화 상자의 **코드 분석** 섹션에서 **빌드 시 코드 분석 사용** 확인란을 선택 하 여 프로젝트에 대해 코드 분석을 사용 하도록 설정할 수 있습니다.  
  
   ![코드 분석 일반 설정의 속성 페이지](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   핵심 C++ 검사 규칙은 코드 분석을 사용 하도록 설정할 때 실행 되는 기본 규칙 집합의 일부가 됩니다. 핵심 검사 C++ 규칙은 개발 중 이므로 일부 규칙은 모든 코드에서 사용할 준비가 되지 않았을 수 있지만 개발 중에 정보를 받을 수 있습니다. 이러한 규칙은 실험적으로 릴리스됩니다. 프로젝트에 대 한 속성에서 릴리스된 또는 실험적 규칙을 실행할지 여부를 선택할 수 있습니다.  
  
   ![코드 분석 확장 프로그램 설정에 대 한 속성 페이지](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   C++ 핵심 검사 규칙 집합을 사용 하거나 사용 하지 않도록 설정 하려면 프로젝트의 **속성 페이지** 대화 상자를 엽니다. **구성 속성**아래에서 **코드 분석**, **확장**을 확장 합니다. **핵심 C++ 검사 사용 (릴리스)** 또는 **핵심 검사 사용 C++ (실험적)** 옆의 드롭다운 컨트롤에서 **예** 또는 **아니요**를 선택 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.  
  
## <a name="check-types-bounds-and-lifetimes"></a>유형, 범위 및 수명 확인  
 C++ 핵심 검사 패키지에는 현재 [형식 안전성](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [범위 안전성](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)및 [수명 안전성](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) 프로필에 대 한 체커가 포함 되어 있습니다.  
  
 핵심 검사 규칙에서 C++ 찾을 수 있는 문제의 종류에 대 한 예는 다음과 같습니다.  
  
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
  
 이 예제에서는 C++ Core Check 규칙을 찾을 수 있는 경고의 일부를 보여 줍니다.  
  
- C26494은 규칙 유형입니다. 5: 항상 개체를 초기화 합니다.  
  
- C26485는 규칙 범위입니다. 3: 배열-포인터 감소 하지 않습니다.  
  
- C26481는 규칙 범위입니다. 1: 포인터 산술 연산을 사용 하지 않습니다. 대신 `span`를 사용하세요.  
  
  C++ Core Check 코드 분석 규칙 집합은를 설치 하 고이 코드를 컴파일할 때 사용 하도록 설정 하는 경우 처음 두 개의 경고를 출력 하지만 세 번째 표시 되지 않습니다. 예제 코드의 빌드 출력은 다음과 같습니다.  
  
**1 >------빌드 시작: 프로젝트: CoreCheckExample, 구성: 디버그 Win32--**  
**----**  
**1 > CoreCheckExample**  
**1 > CoreCheckExample-> C:\Users\username\documents\visual studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample-> C:\Users\username\documents\visual studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (전체 PDB)**  
**c:\users\username\documents\visual studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): warning C26494: ' arr ' 변수는 uninitializ입니다.**  
**ed. 항상 개체를 초기화 합니다. (5를 입력 합니다. https://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): warning C26485: 식 ' arr ': 배열 없음**  
**포인터가 감소 합니다. (범위. 3: https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
= = = = = = = = = **빌드: 1 개 성공, 0 개 최신** , 0 개 건너뜀 = = = = = = = = = = C++ 핵심 지침은 더 안전 하 고 더 안전 하 게 코드를 작성 하는 데 도움이 됩니다. 그러나 규칙이 나 프로필을 적용 하지 않아야 하는 인스턴스가 있는 경우 코드에서 직접 표시 하지 않는 것이 쉽습니다. `gsl::suppress` 특성을 사용 하 여 다음 코드 C++ 블록에서 규칙 위반을 검색 하 고 보고 하지 않도록 핵심 검사를 유지할 수 있습니다. 개별 문을 표시 하 여 특정 규칙을 표시 하지 않을 수 있습니다. 특정 규칙 번호를 포함 하지 않고 `[[gsl::suppress(bounds)]]`을 작성 하 여 전체 범위 프로필을 표시 하지 않을 수도 있습니다.  
  
## <a name="use-the-guideline-support-library"></a>지침 지원 라이브러리 사용  
 CppCoreCheck NuGet 패키지는 Microsoft의 GSL (지침 지원 라이브러리) 구현이 포함 된 패키지도 설치 합니다. GSL은 [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl)에서 독립 실행형 형식으로도 사용할 수 있습니다. 이 라이브러리는 핵심 지침을 따라야 하는 경우에 유용 합니다. GSL에는 오류가 발생 하기 쉬운 구문을 보다 안전한 대체 항목으로 바꿀 수 있는 정의가 포함 되어 있습니다. 예를 들어 `T*, length` 매개 변수 쌍을 `span<T>` 형식으로 바꿀 수 있습니다. GSL는 오픈 소스 이므로 라이브러리 소스, 주석 또는 기여를 확인 하려는 경우 프로젝트를 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)에서 찾을 수 있습니다.
