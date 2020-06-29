---
title: C++에 대한 Microsoft 단위 테스트 프레임워크 사용
description: C++에 대한 Microsoft 유닛 테스트 프레임워크를 사용하여 C++ 코드에 대한 유닛 테스트를 작성합니다.
ms.date: 01/08/2020
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a9393fd248f4e6520c261d405bc624a75d8cf69f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287118"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Visual Studio에서 Microsoft Unit Testing Framework for C++ 사용

Microsoft Unit Testing Framework for C++는 **C++를 통한 데스크톱 개발** 워크로드에 기본적으로 포함됩니다.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a>별도 프로젝트에서 단위 테스트를 작성하려면

일반적으로 테스트하려는 코드와 동일한 솔루션에 있는 자체 프로젝트에서 테스트 코드를 실행합니다. 새 테스트 프로젝트를 설정 및 구성하려면 [C/C++용 단위 테스트 작성](writing-unit-tests-for-c-cpp.md)을 참조하세요.

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a> 같은 프로젝트에서 단위 테스트를 작성하려면

DLL에서 내보내지 않은 함수 테스트 등, 일부 경우에는 테스트하는 프로그램과 동일한 프로젝트에서 테스트를 만들어야 합니다. 같은 프로젝트에서 단위 테스트를 작성하려면

1. 단위 테스트에 필요한 헤더 및 라이브러리 파일을 포함하도록 프로젝트 속성을 수정합니다.

   1. 솔루션 탐색기의 테스트 중인 프로젝트 바로 가기 메뉴에서 **속성**을 선택합니다. 프로젝트 속성 창이 열립니다.

   1. [속성 페이지] 대화 상자에서 **구성 속성** > **VC++ 디렉터리**를 선택합니다.

   1. 다음 행에서 아래쪽 화살표를 클릭하고 **\<Edit>** 를 선택합니다. 이 경로를 추가합니다.

      | 디렉터리 | 속성 |
      |-| - |
      | **포함 디렉터리** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **라이브러리 디렉터리** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. C++ 단위 테스트 파일 추가:

   - **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목** > **C++ 파일(.cpp)** 을 선택합니다.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> 개체 또는 라이브러리 파일에 테스트를 연결하려면

테스트 중인 코드에서 테스트할 함수를 내보내지 않는 경우 **.obj** 또는 **.lib** 출력 파일을 테스트 프로젝트의 종속성에 추가할 수 있습니다. 유닛 테스트에 필요한 헤더 및 라이브러리 또는 개체 파일을 포함하도록 테스트 프로젝트의 속성을 수정합니다.

1. 솔루션 탐색기의 테스트 프로젝트 바로 가기 메뉴에서 **속성**을 선택합니다. 프로젝트 속성 창이 열립니다.

1. **구성 속성** > **링커** > **입력** 페이지를 선택한 다음, **추가 종속성**을 선택합니다.

   **편집**을 선택하고 **.obj** 또는 **.lib** 파일의 이름을 추가합니다. 전체 경로 이름을 사용하지 마세요.

1. **구성 속성** > **링커** > **일반** 페이지를 선택한 다음, **추가 라이브러리 디렉터리**를 선택합니다.

   **편집**을 선택하고 **.obj** 또는 **.lib** 파일의 디렉터리 경로를 추가합니다. 일반적으로 이 경로는 테스트 중인 프로젝트의 빌드 폴더에 있습니다.

1. **구성 속성** > **VC++ 디렉터리** 페이지를 선택하고 **포함 디렉터리**를 선택합니다.

   **편집**을 선택하고 테스트 중인 프로젝트의 헤더 디렉터리를 추가합니다.

## <a name="write-the-tests"></a>테스트 작성

테스트 클래스가 있는 모든 *.cpp* 파일에는 "CppUnitTest.h" 및 `using namespace Microsoft::VisualStudio::CppUnitTestFramework`에 대한 using 문이 포함되어야 합니다. 테스트 프로젝트는 이미 구성되어 있습니다. 네임스페이스 정의와, 시작을 위한 TEST_METHOD를 포함한 TEST_CLASS도 들어 있습니다. 클래스 및 메서드 매크로에서 괄호 안의 이름과 네임스페이스 이름을 수정할 수 있습니다.

테스트 프레임워크는 테스트 모듈, 클래스 및 메서드를 초기화하고 테스트가 완료된 후 리소스를 정리하기 위한 특수 매크로를 정의합니다. 이러한 매크로는 클래스나 메서드에 처음 액세스하기 전과 마지막 테스트를 실행한 후에 실행되는 코드를 생성합니다. 자세한 내용은 [초기화 및 정리](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup)를 참조하세요.

[Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) 클래스에서 고정 메서드를 사용하여 테스트 조건을 정의합니다. [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) 클래스를 사용하여 **출력 창**에 메시지를 작성합니다. 테스트 메서드에 특성 추가

## <a name="run-the-tests"></a>테스트 실행

1. **테스트** 메뉴에서 **Windows** > **테스트 탐색기**를 선택합니다.

1. 창에 일부 테스트가 표시되지 않는 경우 **솔루션 탐색기**에서 노드를 마우스 오른쪽 단추로 클릭하고 **빌드** 또는 **다시 빌드**를 선택하여 테스트 프로젝트를 빌드합니다.

1. **테스트 탐색기**에서 **모두 실행**을 선택하거나 실행하려는 특정 테스트를 선택합니다. 테스트를 마우스 오른쪽 단추로 클릭하면 중단점을 사용하는 디버그 모드에서 실행 등, 다른 옵션이 표시됩니다.

1. **출력 창**의 드롭다운에서 **테스트**를 선택하여 `Logger` 클래스가 작성한 메시지를 확인합니다.

   ![테스트 메시지를 표시하는 C++ 출력 창](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>그룹화를 사용하도록 설정하는 특성 정의

**테스트 탐색기**에서 테스트를 분류하고 그룹화할 수 있도록 하는 특성을 테스트 메서드에 정의할 수 있습니다. 특성(trait)을 정의하려면 `TEST_METHOD_ATTRIBUTE` 매크로를 사용합니다. 예를 들어 `TEST_MY_TRAIT`라는 특성(trait)을 정의하는 경우 다음과 같습니다.

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

단위 테스트에서 정의된 특성(trait)을 사용하려면 다음과 같습니다.

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>C++ 성분 특성 매크로

`CppUnitTest.h`에는 다음의 미리 정의된 특성이 있습니다. 자세한 내용은 [Microsoft Unit Testing Framework for C++ API 참조](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)를 참조하세요.

|매크로|설명|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|TEST_METHOD_ATTRIBUTE 매크로를 사용하여 특성(trait)을 정의합니다.|
|`TEST_OWNER(ownerAlias)`|미리 정의된 소유자 특성(trait)을 사용하여 테스트 메서드의 소유자를 지정합니다.|
|`TEST_PRIORITY(priority)`|미리 정의된 우선순위 특성(trait)을 사용하여 테스트 메서드에 상대적 우선순위를 할당합니다.|

## <a name="see-also"></a>참조

- [빠른 시작: 테스트 탐색기를 사용한 테스트 기반 개발](../test/quick-start-test-driven-development-with-test-explorer.md)
