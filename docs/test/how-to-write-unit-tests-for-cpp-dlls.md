---
title: C++ DLL의 단위 테스트 작성
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 856bc21fdee8945ddcd97e3978f46af0008af616
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279277"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Visual Studio에서 C++ DLL에 대한 단위 테스트 작성

테스트할 함수를 내보낼지 여부에 따라 DLL 코드를 테스트하는 방법에는 여러 가지가 있습니다. 다음 방법 중 하나를 선택합니다.

**단위 테스트가 DLL에서 내보낸 함수만 호출:** [C/C++에 대한 단위 테스트 작성](writing-unit-tests-for-c-cpp.md)에서 설명한 대로 별도의 테스트 프로젝트를 추가합니다. 테스트 프로젝트에서 DLL 프로젝트에 대한 참조를 추가합니다.

[DLL 프로젝트에서 내보낸 함수를 참조하려면](#projectRef) 절차로 이동합니다.

**DLL이 .exe 파일로 빌드:** 개별 테스트 프로젝트를 추가합니다. 출력 개체 파일에 연결합니다.

[개체 또는 라이브러리 파일에 테스트를 연결하려면](#objectRef) 절차로 이동합니다.

**단위 테스트가 DLL에서 내보내지 않은 비 멤버 함수를 호출하며 DLL를 정적 라이브러리 형태로 빌드할 수 있음:** *.lib* 파일로 컴파일되도록 DLL 프로젝트를 변경합니다. 테스트 중인 프로젝트를 참조하는 개별 테스트 프로젝트를 추가합니다.

이 접근 방법은 테스트에서 내보내지 않은 멤버를 사용할 수 있다는 이점이 있지만, 테스트를 여전히 별도 프로젝트로 유지해야 합니다.

[DLL을 정적 라이브러리로 변경하려면](#staticLink) 절차로 이동합니다.

**단위 테스트가 내보내지 않은 비 멤버 함수를 호출해야 하고 코드는 동적 링크 라이브러리(DLL) 형태로 빌드되어야 함:** 제품 코드와 동일한 프로젝트에 단위 테스트를 추가합니다.

[동일한 프로젝트에 단위 테스트를 추가하려면](#sameProject) 절차로 이동합니다.

## <a name="create-the-tests"></a>테스트 만들기

### <a name="staticLink"></a>DLL을 정적 라이브러리로 변경하려면

- 테스트가 DLL 프로젝트에서 내보내지 않은 멤버를 사용해야 하며 테스트 중인 프로젝트가 동적 라이브러리로 빌드되는 경우에는 정적 라이브러리로 변환하는 것을 고려해 보세요.

  1. **솔루션 탐색기**의 테스트 중인 프로젝트 바로 가기 메뉴에서 **속성**을 선택합니다. 프로젝트 **속성** 창이 열립니다.

  2. **구성 속성** > **일반**을 선택합니다.

  3. **구성 형식**을 **정적 라이브러리(.lib)** 로 설정합니다.

  [개체 또는 라이브러리 파일에 테스트를 연결하려면](#objectRef) 절차를 계속 진행합니다.

### <a name="projectRef"></a> 테스트 프로젝트에서 내보낸 DLL 함수를 참조하려면

- DLL 프로젝트에서 테스트할 함수를 내보내는 경우 테스트 프로젝트에서 코드 프로젝트에 대한 참조를 추가할 수 있습니다.

  1. 기본 단위 테스트 프로젝트를 만듭니다.

      ::: moniker range="vs-2019"

      1. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다. **새 프로젝트 추가** 대화 상자에서 **언어**를 C++로 설정하고 검색 상자에 "test"를 입력합니다. 그런 다음, **네이티브 단위 테스트 프로젝트**를 선택합니다.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. **파일** 메뉴에서 **새로 만들기** > **프로젝트** > **Visual C++** > **테스트** > **C++ 단위 테스트 프로젝트**를 차례로 선택합니다.

      ::: moniker-end

  1. **솔루션 탐색기**에서 테스트 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **참조**를 선택합니다.

  1. **프로젝트**를 선택하고 테스트할 프로젝트를 선택합니다.

       **추가** 단추를 선택합니다.

  1. 테스트 프로젝트에 대한 속성에서 테스트 중인 프로젝트의 위치를 포함 디렉터리에 추가합니다.

       **구성 속성** > **VC++ 디렉터리** > **포함 디렉터리**를 차례로 선택합니다.

       **편집**을 선택하고 테스트 중인 프로젝트의 헤더 디렉터리를 추가합니다.

  [단위 테스트 작성](#addTests)으로 이동합니다.

### <a name="objectRef"></a> 개체 또는 라이브러리 파일에 테스트를 연결하려면

- DLL이 테스트할 함수를 내보내지 않는 경우 *.obj* 또는 *.lib* 출력 파일을 테스트 프로젝트의 종속성에 추가할 수 있습니다.

  1. 기본 단위 테스트 프로젝트를 만듭니다.

      ::: moniker range="vs-2019"

      1. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다. **새 프로젝트 추가** 대화 상자에서 **언어**를 C++로 설정하고 검색 상자에 "test"를 입력합니다. 그런 다음, **네이티브 단위 테스트 프로젝트**를 선택합니다.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. **파일** 메뉴에서 **새로 만들기** > **프로젝트** > **Visual C++** > **테스트** > **C++ 단위 테스트 프로젝트**를 차례로 선택합니다.

      ::: moniker-end

  2. **솔루션 탐색기**의 테스트 프로젝트 바로 가기 메뉴에서 **속성**을 선택합니다.

  3. **구성 속성** > **링커** > **입력** > **추가 종속성**을 차례로 선택합니다.

       **편집**을 선택하고 **.obj** 또는 **.lib** 파일의 이름을 추가합니다. 전체 경로 이름을 사용하지 마세요.

  4. **구성 속성** > **링커** > **일반** > **추가 라이브러리 디렉터리**를 차례로 선택합니다.

       **편집**을 선택하고 **.obj** 또는 **.lib** 파일의 디렉터리 경로를 추가합니다. 일반적으로 이 경로는 테스트 중인 프로젝트의 빌드 폴더에 있습니다.

  5. **구성 속성** > **VC++ 디렉터리** > **포함 디렉터리**를 차례로 선택합니다.

       **편집**을 선택하고 테스트 중인 프로젝트의 헤더 디렉터리를 추가합니다.

  [단위 테스트 작성](#addTests)으로 이동합니다.

### <a name="sameProject"></a> 동일 프로젝트에 단위 테스트를 추가하려면

1. 유닛 테스트에 필요한 헤더 및 라이브러리 파일을 포함하도록 제품 코드 프로젝트 속성을 수정합니다.

   1. **솔루션 탐색기**의 테스트 중인 프로젝트의 바로 가기 메뉴에서 **속성**을 선택합니다. 프로젝트 **속성** 창이 열립니다.

   2. **구성 속성** > **VC++ 디렉터리**를 선택합니다.

   3. 포함 및 라이브러리 디렉터리를 편집합니다.

       |디렉터리|속성|
       |-|-|
       |**포함 디렉터리** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**라이브러리 디렉터리** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. C++ 단위 테스트 파일 추가:

   - **솔루션 탐색기**의 프로젝트 바로 가기 메뉴에서 **추가** > **새 항목** > **C++ 단위 테스트**를 차례로 선택합니다.

   [단위 테스트 작성](#addTests)으로 이동합니다.

## <a name="addTests"></a>단위 테스트 작성

1. 각 단위 테스트 코드 파일에서 테스트 중인 프로젝트의 헤더에 대해 `#include` 문을 추가합니다.

2. 테스트 클래스와 메서드를 단위 테스트 코드 파일에 추가합니다. 예를 들어:

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>테스트 실행

1. **테스트** 메뉴에서 **Windows** > **테스트 탐색기**를 선택합니다.

1. 창에 일부 테스트가 표시되지 않는 경우 **솔루션 탐색기**에서 노드를 마우스 오른쪽 단추로 클릭하고 **빌드** 또는 **다시 빌드**를 선택하여 테스트 프로젝트를 빌드합니다.

1. **테스트 탐색기**에서 **모두 실행**을 선택하거나 실행하려는 특정 테스트를 선택합니다. 테스트를 마우스 오른쪽 단추로 클릭하면 중단점을 사용하는 디버그 모드에서 실행 등, 다른 옵션이 표시됩니다.

## <a name="see-also"></a>참조

- [C/C++에 대한 단위 테스트 작성](writing-unit-tests-for-c-cpp.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API 참조](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
- [연습: 동적 연결 라이브러리 만들기 및 사용(C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [가져오기 및 내보내기](/cpp/build/importing-and-exporting)
- [빠른 시작: 테스트 탐색기를 사용한 테스트 기반 개발](../test/quick-start-test-driven-development-with-test-explorer.md)
