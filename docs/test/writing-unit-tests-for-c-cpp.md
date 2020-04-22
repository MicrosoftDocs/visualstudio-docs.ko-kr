---
title: C/C++에 대한 단위 테스트 작성
description: CTest, Boost.Test 및 Google Test를 비롯한 다양한 테스트 프레임워크를 사용하여 Visual Studio에서 C++ 유닛 테스트를 작성합니다.
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 0eaf41dc0bf3e21dfbf4018261844181d594f0d5
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649608"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Visual Studio에서 C/C++에 대한 단위 테스트 작성

**테스트 탐색기** 창을 사용하여 C++ 유닛 테스트를 작성하여 실행할 수 있으며, 다른 언어에서처럼 작동합니다. **테스트 탐색기**에 대한 자세한 내용은 [테스트 탐색기를 사용하여 단위 테스트 실행](run-unit-tests-with-test-explorer.md)을 참조하세요.

> [!NOTE]
> Live Unit Testing, Coded UI Tests 및 IntelliTest 등의 일부 기능은 C++에서 지원되지 않습니다.

Visual Studio에는 다음 C++ 테스트 기능이 포함되어 있으며 추가 다운로드가 필요하지 않습니다.

- C++에 대한 Microsoft 단위 테스트 프레임워크
- Google Test
- Boost.Test
- CTest

설치된 프레임워크를 사용할 뿐만 아니라 Visual Studio 내에서 사용하려는 모든 프레임워크에 대해 자체 테스트 어댑터를 작성할 수 있습니다. 테스트 어댑터는 **테스트 탐색기** 창에 단위 테스트를 통합할 수 있습니다. 몇 가지 타사 어댑터를 [Visual Studio Marketplace](https://marketplace.visualstudio.com)에서 제공하고 있습니다. 자세한 내용은 [타사 단위 테스트 프레임워크 설치](install-third-party-unit-test-frameworks.md)를 참조하세요.

**Visual Studio 2017 이상(Professional 및 Enterprise)**

C++ 단위 테스트 프로젝트는 [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)를 지원합니다.

**Visual Studio 2017 이상(모든 버전)**

- **Google Test 어댑터**는 **C++를 통한 데스크톱 개발** 워크로드의 기본 구성 요소로 포함되어 있습니다. 솔루션에 추가할 수 있는 프로젝트 템플릿이 있습니다. **솔루션 탐색기**의 솔루션 노드에서 **새 프로젝트 추가** 오른쪽 클릭 메뉴를 사용하여 추가합니다. **도구** > **옵션**을 통해 구성할 수 있는 옵션도 있습니다. 자세한 내용은 [방법: Visual Studio에서 Google Test 사용](how-to-use-google-test-for-cpp.md)을 참조하세요.

- **Boost.Test**는 **C++를 통한 데스크톱 개발** 워크로드의 기본 구성 요소로 포함되어 있습니다. **테스트 탐색기**와 통합되었지만 현재는 프로젝트 템플릿이 없습니다. 수동으로 구성해야 합니다. 자세한 내용은 [방법: Visual Studio에서 Boost.Test 사용](how-to-use-boost-test-for-cpp.md)을 참조하세요.

- **CTest** 지원은 **C++를 사용한 데스크톱 개발** 워크로드의 일부인 **C++ CMake 도구** 구성 요소에 포함되어 있습니다. 자세한 내용은 [방법: Visual Studio에서 CTest 사용](how-to-use-ctest-for-cpp.md)을 참조하세요.

**Visual Studio 2015 및 이전 버전**

Visual Studio Marketplace에서 Google Test 어댑터 및 Boost.Test 어댑터 확장을 다운로드할 수 있습니다. 이러한 확장은 [Test adapter for Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) 및 [Test adapter for Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)에 있습니다.

## <a name="basic-test-workflow"></a>기본 테스트 워크플로

다음 섹션에서는 C++ 단위 테스트를 시작하기 위한 기본 단계를 보여 줍니다. 기본 구성은 Microsoft 및 Google Test 프레임워크에서 유사합니다. Boost.Test에서는 수동으로 테스트 프로젝트를 만들어야 합니다.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Visual Studio 2019에서 테스트 프로젝트 만들기

하나 이상의 테스트 프로젝트 내에서 테스트를 정의하고 실행합니다. 테스트하려는 코드와 동일한 솔루션에 프로젝트를 만듭니다. 기존 솔루션에 새 테스트 프로젝트를 추가하려면 **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭합니다. 팝업 메뉴에서 **추가** > **새 프로젝트**를 선택합니다. **언어**를 C++로 설정하고 검색 상자에 "test"를 입력합니다. 다음 그림에서는 **C++를 사용한 데스크톱 개발** 및 **UWP 개발** 워크로드가 설치되었을 때 사용할 수 있는 테스트 프로젝트를 보여줍니다.

![Visual Studio 2019의 Excel C++ 테스트 프로젝트](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Visual Studio 2017에서 테스트 프로젝트 만들기

하나 이상의 테스트 프로젝트 내에서 테스트를 정의하고 실행합니다. 테스트하려는 코드와 동일한 솔루션에 프로젝트를 만듭니다. 새 테스트 프로젝트를 추가하려면 **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다. 왼쪽 창에서 **Visual C++ 테스트**를 선택합니다. 그런 다음, 가운데 창에서 프로젝트 형식 중 하나를 선택합니다. 다음 그림에서는 **C++를 통한 데스크톱 개발** 워크로드가 설치되었을 때 사용할 수 있는 테스트 프로젝트를 보여 줍니다.

![C++ 테스트 프로젝트](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>솔루션의 다른 프로젝트에 대한 참조 만들기

테스트 중인 프로젝트의 함수에 액세스할 수 있도록 하려면 테스트 프로젝트에서 프로젝트에 대한 참조를 추가합니다. **솔루션 탐색기**에서 테스트 프로젝트 노드를 마우스 오른쪽 단추로 클릭하여 팝업 메뉴를 표시합니다. **추가** > **참조**를 선택합니다. [참조 추가] 대화 상자에서 테스트할 프로젝트를 선택합니다.

![참조 추가](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>개체 또는 라이브러리 파일에 연결

테스트 코드가 테스트할 함수를 내보내지 않는 경우 .obj 또는 .lib 출력 파일을 테스트 프로젝트의 종속성에 추가할 수 있습니다. 자세한 내용은 [개체 또는 라이브러리 파일에 테스트를 연결하려면](how-to-use-microsoft-test-framework-for-cpp.md#object_files)을 참조하세요.

### <a name="add-include-directives-for-header-files"></a>헤더 파일에 대해 #include 지시문 추가

다음으로, 단위 테스트 *.cpp* 파일에서 테스트할 형식과 함수를 선언하는 모든 헤더 파일에 대해 `#include` 지시문을 추가합니다. `#include "`를 입력한 다음, IntelliSense가 선택할 수 있게 활성화됩니다. 다른 헤더에 대해 반복합니다.

![include 지시문 추가](media/cpp-add-includes-test-project.png)

원본 파일의 각 include 문에 전체 경로를 입력할 필요가 없도록 하려면 **프로젝트** > **속성** > **C/C++**  > **일반** > **추가 포함 디렉터리**에 필요한 폴더를 추가할 수 있습니다.

### <a name="write-test-methods"></a>테스트 메서드 작성

> [!NOTE]
> 이 섹션에서는 C/C++용 Microsoft 단위 테스트 프레임워크에 대한 구문을 보여 줍니다. 문서화된 내용은 다음과 같습니다. [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API 참조](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Google Test 설명서는 [Google Test 입문](https://github.com/google/googletest/blob/master/googletest/docs/primer.md)을 참조하세요. Boost.Test는 [Boost Test 라이브러리: 단위 테스트 프레임워크](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html)를 참조하세요.

테스트 프로젝트의 *.cpp* 파일에는 스텁 클래스와 메서드가 정의되어 있으며, 테스트 코드를 작성하는 방법에 대한 예제를 보여 줍니다. 시그니처는 **테스트 탐색기** 창에서 메서드를 검색 가능하게 하는 TEST_CLASS 및 TEST_METHOD 매크로를 사용합니다.

![include 지시문 추가](media/cpp-write-test-methods.png)

TEST_CLASS 및 TEST_METHOD는 [Microsoft Native Test Framework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)의 일부입니다. **테스트 탐색기**는 유사한 방식으로 다른 지원되는 프레임워크에서 테스트 메서드를 검색합니다.

TEST_METHOD는 void를 반환합니다. 테스트 결과를 내려면 `Assert` 클래스에서 고정 메서드를 사용하여 예상되는 항목에 대해 실제 결과를 테스트합니다. 다음 예제에서는 `MyClass`에 `std::string`을 취하는 생성자가 있다고 가정합니다. 생성자가 예상대로 클래스를 초기화하는지 테스트할 수 있습니다.

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

이전 예에서 `Assert::AreEqual` 호출의 결과가 테스트 통과 또는 실패 여부를 결정합니다. Assert 클래스에는 실제 결과와 예상 결과를 비교하는 여러 다른 메서드가 있습니다.

*특성*을 테스트 메서드에 추가하여 테스트 소유자, 우선 순위 및 기타 정보를 지정할 수 있습니다. 그런 다음 이 값을 사용하여 **테스트 탐색기**에서 테스트를 정렬하고 그룹화할 수 있습니다. 자세한 내용은 [테스트 탐색기를 사용하여 단위 테스트 실행](run-unit-tests-with-test-explorer.md)을 참조하세요.

### <a name="run-the-tests"></a>테스트 실행

1. **테스트** 메뉴에서 **Windows** > **테스트 탐색기**를 선택합니다. 다음 그림에서는 테스트를 아직 실행하지 않은 테스트 프로젝트를 보여 줍니다.

   ![테스트 실행 전 테스트 탐색기](media/cpp-test-explorer.png)

   > [!NOTE]
   > **테스트 탐색기**와의 CTest 통합은 아직 제공되지 않습니다. CMake 주 메뉴에서 CTest 테스트를 실행합니다.

1. 창에 일부 테스트가 표시되지 않는 경우 **솔루션 탐색기**에서 노드를 마우스 오른쪽 단추로 클릭하고 **빌드** 또는 **다시 빌드**를 선택하여 테스트 프로젝트를 빌드합니다.

1. **테스트 탐색기**에서 **모두 실행**을 선택하거나 실행하려는 특정 테스트를 선택합니다. 테스트를 마우스 오른쪽 단추로 클릭하면 중단점을 사용하는 디버그 모드에서 실행 등, 다른 옵션이 표시됩니다. 모든 테스트를 실행한 후에는 창에 어떤 테스트에 통과했고 어떤 테스트에 실패했는지 표시됩니다.

![테스트 실행 후 테스트 탐색기](media/cpp-test-explorer-passed.png)

실패한 테스트에 대해서는 원인 진단을 위해 상세 정보를 제공하는 메시지가 나타납니다. 실패한 테스트를 마우스 오른쪽 단추로 클릭하여 팝업 메뉴를 표시합니다. **선택한 테스트 디버그**를 선택하여 오류가 발생한 함수를 단계별로 실행합니다.

**테스트 탐색기**에 대한 자세한 내용은 [테스트 탐색기를 사용하여 단위 테스트 실행](run-unit-tests-with-test-explorer.md)을 참조하세요.

유닛 테스트와 관련된 자세한 내용은 [ 테스트 기본 사항](unit-test-basics.md)을 참조하세요.

## <a name="use-codelens"></a>CodeLens 사용

**Visual Studio 2017 이상(Professional 및 Enterprise 버전)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)를 사용하면 코드 편집기를 종료하지 않고도 유닛 테스트 상태를 신속하게 확인할 수 있습니다.

다음 방법 중 하나로 C++ 단위 테스트 프로젝트에 대한 CodeLens를 초기화할 수 있습니다.

- 테스트 프로젝트 또는 솔루션을 편집하고 빌드합니다.
- 프로젝트 또는 솔루션을 다시 빌드합니다.
- **테스트 탐색기** 창에서 테스트를 실행합니다.

CodeLens가 초기화되면 각 유닛 테스트 위에서 테스트 상태 아이콘을 확인할 수 있습니다.

![C++ CodeLens 아이콘](media/cpp-test-codelens-icons.png)

자세한 정보를 보거나 단위 테스트를 실행 또는 디버그하려면 아이콘을 클릭합니다.

![C++ CodeLens 실행 및 디버그](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>참조

- [코드 단위 테스트](unit-test-your-code.md)
