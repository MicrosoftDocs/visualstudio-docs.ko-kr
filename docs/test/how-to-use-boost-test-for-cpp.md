---
title: Boost.Test for C++를 사용하는 방법
description: Boost.Test를 사용하여 Visual Studio에서 단위 테스트를 만듭니다.
ms.date: 01/29/2020
ms.topic: how-to
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 34c593469a586d1314c7ee52f3aeb3ab6faf334c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287274"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Visual Studio에서 Boost.Test for C++를 사용하는 방법

Visual Studio 2017 이상에서는 Boost.Test 테스트 어댑터가 Visual Studio IDE에 통합되어 있습니다. **C++를 사용한 데스크톱 개발** 워크로드의 구성 요소입니다.

![Test Adapter for Boost.Test](media/cpp-boost-component.png)

**C++를 사용한 데스크톱 개발** 워크로드가 설치되지 않은 경우 **Visual Studio 설치 관리자**를 엽니다. **C++를 사용한 데스크톱 개발** 워크로드를 선택한 다음 **수정** 단추를 선택합니다.

## <a name="install-boost"></a>Boost를 설치합니다.

Boost.Test에는 [Boost](https://www.boost.org/)가 필요합니다! Boost가 설치되어 있지 않으면 Vcpkg 패키지 관리자를 사용하는 것이 좋습니다.

1. [Vcpkg: Windows용 C ++ 패키지 관리자](/cpp/vcpkg)의 지침에 따라 vcpkg를 설치합니다(아직 설치하지 않은 경우).

1. Boost.Test 동적 또는 정적 라이브러리를 설치합니다.

    - `vcpkg install boost-test`를 실행하여 Boost.Test 동적 라이브러리를 설치합니다.

       -또는-

    - `vcpkg install boost-test:x86-windows-static`를 실행하여 Boost.Test 정적 라이브러리를 설치합니다.

1. `vcpkg integrate install`을 실행하여 Visual Studio를 라이브러리로 구성하고 Boost 헤더와 이진 파일 경로를 포함합니다.

Visual Studio의 솔루션 내에서 테스트를 구성하는 방법을 선택할 수 있습니다. 테스트 중인 프로젝트에 테스트 코드를 포함하거나 테스트를 위해 별도의 테스트 프로젝트를 만들 수 있습니다. 두 옵션 모두 장단점이 있습니다.

## <a name="add-tests-inside-your-project"></a>프로젝트 내에서 테스트 추가

Visual Studio 2017 버전 15.6 이상에서는 테스트할 항목 템플릿을 프로젝트에 추가할 수 있습니다. 테스트와 코드는 모두 동일한 프로젝트에 있습니다. 테스트 빌드를 생성하려면 별도의 빌드 구성을 만들어야 합니다. 그리고 테스트가 디버그 및 릴리스 빌드에 들어가지 못하도록 해야 합니다.

Visual Studio 2017 버전 15.5에서는 미리 구성된 테스트 프로젝트 또는 항목 템플릿을 Boost.Test에 사용할 수 없습니다. 지침을 사용하여 별도의 테스트 프로젝트를 만들고 구성합니다.

### <a name="create-a-boosttest-item"></a>Boost.Test 항목 만들기

1. 테스트를 위한 *.cpp* 파일을 만들려면 **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다.

1. **새 항목 추가** 대화 상자에서 **설치됨** > **Visual C++**  > **테스트**를 확장합니다. **Boost.Test**를 선택한 다음 **추가**를 선택하여 *Test.cpp*를 프로젝트에 추가합니다.

   ![Boost.Test 항목 템플릿](media/boost_test_item_template.png)

새 *Test.cpp* 파일에는 샘플 테스트 메서드가 포함되어 있습니다. 이 파일에서 사용자 고유의 헤더 파일을 포함하고 앱에 대한 테스트를 작성할 수 있습니다.

또한 테스트 파일은 매크로를 사용하여 테스트 구성에 대한 새 `main` 루틴을 정의합니다. 지금 프로젝트를 빌드하면 “_main이 이미 main.obj에 정의되어 있습니다.”와 같은 LNK2005 오류가 표시됩니다.

### <a name="create-and-update-build-configurations"></a>빌드 구성 만들기 및 업데이트

1. 테스트 구성을 만들려면 메뉴 모음에서 **빌드** > **구성 관리자**를 선택합니다. **구성 관리자** 대화 상자에서 **활성 솔루션 구성** 아래의 드롭다운을 열고 **새로 만들기**를 선택합니다. **새 솔루션 구성** 대화 상자에서 “Debug UnitTests”와 같은 이름을 입력합니다. **다음에서 설정 복사**에서 **디버그**를 선택한 다음 **확인**을 선택합니다.

1. 디버그 및 릴리스 구성에서 테스트 코드를 제외합니다. **솔루션 탐색기**에서 Test.cpp를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **속성 페이지** 대화 상자에서 **구성** 드롭다운에 있는 **모든 구성**을 선택합니다. **구성 속성** > **일반**을 선택하고 **빌드에서 제외** 속성의 드롭다운을 엽니다. **예**를 선택한 다음 **적용**을 선택하여 변경 내용을 저장합니다.

1. Debug UnitTests 구성의 테스트 코드를 포함하려면 **속성 페이지** 대화 상자에서 **구성** 대화 상자에 있는 **Debug UnitTests**를 선택합니다. **빌드에서 제외** 속성에서 **아니요**를 선택한 후 **확인**을 선택해 변경 내용을 저장합니다.

1. Debug UnitTests 구성에서 기본 코드를 제외합니다. **솔루션 탐색기**에서 `main` 함수를 포함하는 파일을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **속성 페이지** 대화 상자의 **구성** 드롭다운에서 **Debug UnitTests**를 선택합니다. **구성 속성** > **일반**을 선택하고 **빌드에서 제외** 속성의 드롭다운을 엽니다. **예**를 선택한 다음 **확인**을 선택하여 변경 내용을 저장합니다.

1. 솔루션 구성을 **Debug UnitTests**로 설정한 다음 프로젝트를 빌드하여 **테스트 탐색기**에서 메서드를 검색할 수 있도록 합니다.

만든 구성 이름이 “디버그” 또는 “릴리스”로 시작하는 경우 해당하는 Boost.Test 라이브러리가 자동으로 선택됩니다.

항목 템플릿은 Boost.Test의 단일 헤더 변형을 사용하지만 독립 실행형 라이브러리 변형을 사용하도록 #include 경로를 수정할 수 있습니다. 자세한 내용은 [include 지시문 추가](#add-include-directives)를 참조하세요.

## <a name="create-a-separate-test-project"></a>개별 테스트 프로젝트 추가

대부분의 경우 테스트에 별도의 프로젝트를 사용하는 편이 더 쉽습니다. 프로젝트에 대한 특별한 테스트 구성을 만들 필요는 없습니다. 또는 디버그 빌드와 릴리스 빌드에서 테스트 파일을 제외합니다.

### <a name="to-create-a-separate-test-project"></a>별도의 테스트 프로젝트를 만드는 방법

1. **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 차례로 선택합니다.

1. **새 프로젝트 추가** 대화 상자의 필터 드롭다운에서 **C++** , **Windows** 및 **콘솔**을 선택합니다. **콘솔 앱** 템플릿을 선택한 다음 **다음**을 선택합니다.

1. 프로젝트 이름을 지정하고 **만들기**를 선택합니다.

1. *.cpp* 파일에서 `main` 함수를 삭제합니다.

1. Boost.Test의 단일 헤더 또는 동적 라이브러리 버전을 사용하는 경우 [include 지시문 추가](#add-include-directives)로 이동합니다. 정적 라이브러리 버전을 사용하는 경우 일부 추가 구성을 수행해야 합니다.

   a. 프로젝트 파일을 편집하려면 먼저 언로드하세요. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드**를 선택합니다. 그런 다음 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **<name\>.vcxproj 편집**을 선택합니다.

   b. 다음과 같이 **Globals** 속성 그룹에 두 줄을 추가합니다.

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. *\*.vcxproj* 파일을 저장하고 닫은 다음, 프로젝트를 다시 로드합니다.

   d. **속성 페이지**를 열려면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

   e. **C/C++**  > **코드 생성**을 확장한 후 **런타임 라이브러리**를 선택합니다. 디버그 정적 런타임 라이브러리에 해당하는 **/MTd** 또는 릴리스 정적 런타임 라이브러리에 해당하는 **/MT**를 선택합니다.

   f. **링커** > **시스템**을 확장합니다. **하위 시스템**이 **콘솔**로 설정되었는지 확인합니다.

   g. **확인**을 선택하여 속성 페이지를 닫습니다.

## <a name="add-include-directives"></a>include 지시문 추가

1. *.cpp* 테스트 파일에서 필요한 `#include` 지시문을 추가하여 프로그램의 형식과 함수를 테스트 코드에 표시되게 합니다. 별도의 테스트 프로젝트를 사용하는 경우 일반적으로 프로그램은 폴더 계층 구조의 형제 수준에 있습니다. `#include "../"`를 입력하면 IntelliSense 창이 표시되어 헤더 파일에 대한 전체 경로를 선택할 수 있습니다.

   ![#include 지시문 추가](media/cpp-gtest-includes.png)

   다음과 함께 독립 실행형 라이브러리를 사용할 수 있습니다.

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   또는 다음과 함께 단일 헤더 버전을 사용할 수 있습니다.

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   그런 다음 `BOOST_TEST_MODULE`을 정의합니다.

다음 예제는 **테스트 탐색기**에서 테스트를 검색하는 데 충분합니다.

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>테스트 작성 및 실행

이제 Boost Test를 작성하고 실행할 준비가 되었습니다. 테스트 매크로에 대한 내용은 [Boost Test 라이브러리 설명서](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)를 참조하세요. **테스트 탐색기**를 사용한 테스트 검색, 실행 및 그룹화에 대한 내용은 [테스트 탐색기를 사용하여 단위 테스트 실행](run-unit-tests-with-test-explorer.md)을 참조하세요.

## <a name="see-also"></a>참조

- [C/C++에 대한 단위 테스트 작성](writing-unit-tests-for-c-cpp.md)
