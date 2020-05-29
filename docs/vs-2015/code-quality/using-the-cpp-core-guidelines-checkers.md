---
title: C++ Core Guidelines 체커 사용 | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: fffa4cec6a2bd7a340b90776ac20dc486f28045b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173573"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ Core Guidelines 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Core Guidelines은 c + + 전문가 및 디자이너에서 만든 c + +의 코딩에 대 한 지침, 규칙 및 모범 사례 집합입니다.  이제 Visual Studio에서 코드 분석 도구에 대 한 추가 규칙을 만들어 C++ Core Guidelines 준수 여부를 확인 하 고 향상 된 기능을 제안 하는 추가 기능 패키지를 지원 합니다.  
  
## <a name="the-c-core-guidelines-project"></a>C++ Core Guidelines 프로젝트  
 Bjarne Stroustrup 및 기타 사용자가 만든 C++ Core Guidelines은 최신 c + +를 안전 하 고 효과적으로 사용 하는 방법에 대 한 지침입니다. 지침은 정적 형식 안전성 및 리소스 안전성을 강조 합니다. 이는 언어에서 가장 오류가 발생 하기 쉬운 부분을 제거 하거나 최소화 하는 방법을 파악 하 고 안정적인 방식으로 코드를 더 간단 하 고 더 효율적으로 만드는 방법을 제안 합니다. 이러한 지침은 표준 c + + Foundation에 의해 유지 관리 됩니다. 자세한 내용은 [GitHub](https://github.com/isocpp/CppCoreGuidelines)에서 설명서, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)및 C++ Core Guidelines 설명서 프로젝트 파일 액세스를 참조 하세요.  
  
 Microsoft에서는 Nuget 패키지를 사용 하 여 프로젝트에 추가할 수 있는 C++ Core Check 코드 분석 규칙 집합을 만들어 C++ Core Guidelines 작업을 지원 합니다. 패키지 이름은 CppCoreCheck입니다 .이 패키지는에서 사용할 수 있습니다 [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . 이 패키지에는 Visual Studio 2015 이상 업데이트 1이 설치 되어 있어야 합니다.  
  
 또한 패키지는 다른 패키지를 종속성으로 설치 합니다 .이는 헤더 전용의 GSL (지침 지원 라이브러리)입니다. GSL는 GitHub 에서도 사용할 수 있습니다 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>코드 분석에서 C++ Core Check 지침 사용  
 C++ Core Check 코드 분석 도구를 사용 하려면 Visual Studio 내에서 확인 하려는 각 c + + 프로젝트에 CppCoreCheck NuGet 패키지를 설치 합니다.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>CppCoreCheck 패키지를 프로젝트에 추가 하려면  
  
1. **솔루션 탐색기**에서 패키지를 추가 하려는 솔루션의 프로젝트에 대 한 상황에 맞는 메뉴를 마우스 오른쪽 단추로 클릭 하 여 엽니다. Nuget 패키지 **관리** 를 선택 하 여 **nuget 패키지 관리자**를 엽니다.  
  
2. **NuGet 패키지 관리자** 창에서 CppCoreCheck를 검색 합니다.  
  
    ![Nuget 패키지 관리자 창에 CppCoreCheck 패키지 표시](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. CppCoreCheck 패키지를 선택한 후 **설치** 단추를 선택 하 여 프로젝트에 규칙을 추가 합니다.  
  
   NuGet 패키지는 프로젝트에 대해 코드 분석을 사용 하도록 설정할 때 호출 되는 프로젝트에 다른 Msbuild.exe .targets 파일을 추가 합니다. 이 .targets 파일은 Visual Studio code analysis tool의 추가 확장으로 C++ Core Check 규칙을 추가 합니다.  
  
   프로젝트에 대 한 **속성 페이지** 대화 상자의 **코드 분석** 섹션에서 **빌드 시 코드 분석 사용** 확인란을 선택 하 여 프로젝트에 대해 코드 분석을 사용 하도록 설정할 수 있습니다.  
  
   ![코드 분석 일반 설정의 속성 페이지](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ Core Check 규칙은 코드 분석을 사용 하도록 설정할 때 실행 되는 기본 규칙 집합의 일부가 됩니다. C++ Core Check 규칙은 개발 중 이므로 일부 규칙은 모든 코드에서 사용할 준비가 되지 않을 수도 있지만 개발 중에 정보를 받을 수 있습니다. 이러한 규칙은 실험적으로 릴리스됩니다. 프로젝트에 대 한 속성에서 릴리스된 또는 실험적 규칙을 실행할지 여부를 선택할 수 있습니다.  
  
   ![코드 분석 확장 프로그램 설정에 대 한 속성 페이지](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   C++ Core Check 규칙 집합을 사용 하거나 사용 하지 않도록 설정 하려면 프로젝트의 **속성 페이지** 대화 상자를 엽니다. **구성 속성**아래에서 **코드 분석**, **확장**을 확장 합니다. **C++ Core Check (릴리스) 사용** 또는 **C++ Core Check 사용 (실험적)** 옆의 드롭다운 컨트롤에서 **예** 또는 **아니요**를 선택 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.  
  
## <a name="check-types-bounds-and-lifetimes"></a>유형, 범위 및 수명 확인  
 현재 C++ Core Check 패키지에는 [형식 안전성](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [범위 안전성](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)및 [수명 안전성](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) 프로필에 대 한 체커가 포함 되어 있습니다.  
  
 C++ Core Check 규칙에서 찾을 수 있는 문제 종류의 예는 다음과 같습니다.  
  
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
  
 이 예제에서는 C++ Core Check 규칙에서 찾을 수 있는 몇 가지 경고를 보여 줍니다.  
  
- C26494은 규칙 유형입니다. 5: 항상 개체를 초기화 합니다.  
  
- C26485는 규칙 범위입니다. 3: 배열-포인터 감소 하지 않습니다.  
  
- C26481는 규칙 범위입니다. 1: 포인터 산술 연산을 사용 하지 않습니다. 대신 `span`를 사용하세요.  
  
  이 코드를 컴파일할 때 C++ Core Check 코드 분석 규칙 집합을 설치 하 고 사용 하도록 설정 하는 경우 처음 두 경고는 출력 되지만 세 번째는 표시 되지 않습니다. 예제 코드의 빌드 출력은 다음과 같습니다.  
  
**1>------빌드 시작: 프로젝트: CoreCheckExample, 구성: 디버그 Win32--**  
**----**  
**1> CoreCheckExample**  
**1> CoreCheckExample-> C:\Users\username\documents\visual studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1> CoreCheckExample-> C:\Users\username\documents\visual studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (전체 PDB)**  
**c:\users\username\documents\visual studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): warning C26494: ' arr ' 변수는 uninitializ입니다.**  
**ed. 항상 개체를 초기화 합니다. (형식. 5: https: \/ /go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): warning C26485: 식 ' arr ': 배열 없음**  
**포인터가 감소 합니다. (경계. 3: https: \/ /go.microsoft.com/fwlink/p/?LinkID=620415)**  
**========== 빌드: 성공 1, 실패 0, 최신 0, 생략 0 ==========** 

C++ Core Guidelines는 더 빠르고 안전한 코드를 작성 하는 데 도움이 됩니다. 그러나 규칙이 나 프로필을 적용 하지 않아야 하는 인스턴스가 있는 경우 코드에서 직접 표시 하지 않는 것이 쉽습니다. 특성을 사용 `gsl::suppress` 하 여 다음 코드 블록에서 규칙 위반을 검색 하 고 보고할 수 C++ Core Check 유지할 수 있습니다. 개별 문을 표시 하 여 특정 규칙을 표시 하지 않을 수 있습니다. `[[gsl::suppress(bounds)]]`특정 규칙 번호를 포함 하지 않고 작성 하 여 전체 범위 프로필을 표시 하지 않을 수도 있습니다.  
  
## <a name="use-the-guideline-support-library"></a>지침 지원 라이브러리 사용  
 CppCoreCheck NuGet 패키지는 Microsoft의 GSL (지침 지원 라이브러리) 구현이 포함 된 패키지도 설치 합니다. GSL는 독립 실행형 형식으로도 사용할 수 있습니다 [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . 이 라이브러리는 핵심 지침을 따라야 하는 경우에 유용 합니다. GSL에는 오류가 발생 하기 쉬운 구문을 보다 안전한 대체 항목으로 바꿀 수 있는 정의가 포함 되어 있습니다. 예를 들어 `T*, length` 매개 변수 쌍을 형식으로 바꿀 수 있습니다 `span<T>` . GSL는 오픈 소스 이므로 라이브러리 소스, 주석 또는 기여를 확인 하려는 경우에는에서 프로젝트를 찾을 수 있습니다 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .
