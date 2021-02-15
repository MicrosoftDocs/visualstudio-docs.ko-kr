---
title: 단위 테스트 시작
description: Visual Studio를 사용하여 단위 테스트를 정의 및 실행하여 코드 상태를 유지 관리하고, 고객이 찾기 전에 오류와 결함을 찾습니다.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c83b13b852b9ae53bd2218a62b6681478369df1b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970519"
---
# <a name="get-started-with-unit-testing"></a>유닛 테스트 시작

Visual Studio를 사용하여 단위 테스트를 정의하고 실행하여 코드 상태를 유지 관리하고, 코드 적용 범위를 확인하고 , 고객이 찾기 전에 오류와 결함을 찾을 수 있습니다. 단위 테스트를 수시로 실행하여 코드가 올바르게 작동하는지 확인합니다.

이 문서의 코드 및 그림에서는 C#을 사용하지만 개념 및 기능은 .NET 언어, C++, Python, JavaScript 및 TypeScript에 적용됩니다.

## <a name="create-unit-tests"></a>단위 테스트 만들기

이 섹션에서는 단위 테스트 프로젝트를 만드는 방법을 설명합니다.

1. Visual Studio에서 테스트할 프로젝트를 엽니다.

   예제 단위 테스트를 보여 주기 위해 이 문서에서는 **HelloWorldCore** 라는 간단한 “Hello World” C# 프로젝트를 테스트합니다. 이러한 프로젝트의 샘플 코드는 다음과 같습니다.

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. **솔루션 탐색기** 에서 솔루션 노드를 선택합니다. 그런 다음, 상단 메뉴 모음에서 **파일** > **추가** > **새 프로젝트** 를 선택합니다.

1. 새 프로젝트 대화 상자에서 MSTest와 같이 사용할 테스트 프레임워크에 대한 단위 테스트 프로젝트 템플릿을 찾아 선택합니다.

   Visual Studio 2017 버전 14.8부터 .NET 언어에는 NUnit 및 xUnit의 기본 제공 템플릿이 포함됩니다. C++의 경우 해당 언어에서 지원되는 테스트 프레임워크를 선택해야 합니다. Python의 경우 테스트 프로젝트를 설정하려면 [Python 코드에서 유닛 테스트 설정](../python/unit-testing-python-in-visual-studio.md)을 참조하세요.

   > [!TIP]
   > C#의 경우 더 빠른 메서드를 사용하여 코드에서 단위 테스트 프로젝트를 만들 수 있습니다. 자세한 내용은 [단위 테스트 프로젝트 및 테스트 메서드 만들기](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods)를 참조하세요. .NET Core 또는 .NET Standard에서 이 메서드를 사용하려면 Visual Studio 2019가 필요합니다.

   다음 그림은 .NET에서 지원되는 MSTest 단위 테스트를 보여 줍니다.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019의 단위 테스트 프로젝트 템플릿](media/vs-2019/add-new-test-project.png)

   **다음** 을 클릭하여 테스트 프로젝트의 이름을 선택한 다음, **만들기** 를 클릭합니다.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Visual Studio 2019의 단위 테스트 프로젝트 템플릿](media/mstest-test-project-template.png)

   테스트 프로젝트의 이름(예: HelloWorldTests)을 선택하고 **확인** 을 클릭합니다.

   ::: moniker-end

   프로젝트가 솔루션에 추가됩니다.

   ![솔루션 탐색기의 단위 테스트 프로젝트](media/vs-2019/solution-explorer.png)

1. 단위 테스트 프로젝트에서 **참조** 또는 **종속성** 을 마우스 오른쪽 단추로 클릭한 다음, **참조 추가** 를 선택하여 테스트하려는 프로젝트에 대한 참조를 추가합니다.

1. 테스트할 코드가 포함된 프로젝트를 선택하고 **확인** 을 클릭합니다.

   ![Visual Studio에서 프로젝트 참조 추가](media/vs-2019/reference-manager.png)

1. 단위 테스트 메서드에 코드를 추가합니다.

   예를 들어 MSTest, NUnit 또는 xUnit(.NET에서만 지원)과 같은 테스트 프레임워크와 일치하는 올바른 설명서 탭을 선택하여 다음 코드를 사용할 수 있습니다.

   # <a name="mstest"></a>[MSTest](#tab/mstest)

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   # <a name="nunit"></a>[NUnit](#tab/nunit)

   ```csharp
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

    # <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

## <a name="run-unit-tests"></a>단위 테스트 실행

1. [테스트 탐색기](../test/run-unit-tests-with-test-explorer.md)를 엽니다.

   ::: moniker range=">=vs-2019"
   테스트 탐색기를 열려면 상단 메뉴 모음에서 **테스트** > **테스트 탐색기** 를 선택하거나 **Ctrl**+**E**, **T** 를 누릅니다.
   ::: moniker-end
   ::: moniker range="vs-2017"
   테스트 탐색기를 열려면 상단 메뉴 모음에서 **테스트** > **Windows** > **테스트 탐색기** 를 선택합니다.
   ::: moniker-end

1. **모두 실행** 을 클릭하여 단위 테스트를 실행하거나 **Ctrl** + **R**, **V** 를 누릅니다.

   ![테스트 탐색기에서 단위 테스트 실행](media/vs-2019/test-explorer-run-all.png)

   테스트가 완료된 후 녹색 확인 표시는 테스트가 통과되었음을 나타냅니다. 빨간색 "x" 아이콘은 테스트가 실패했음을 나타냅니다.

   ![테스트 탐색기에서 단위 테스트 결과 검토](media/vs-2019/unit-test-passed.png)

> [!TIP]
> [테스트 탐색기](../test/run-unit-tests-with-test-explorer.md)를 사용하여 기본 제공 테스트 프레임워크(MSTest) 또는 타사 테스트 프레임워크에서 단위 테스트를 실행할 수 있습니다. 테스트를 범주로 그룹화하고 테스트 목록을 필터링하고 테스트 재생 목록 생성, 저장 및 실행할 수 있습니다. 테스트를 디버그하고 테스트 성능 및 코드 검사를 분석할 수도 있습니다.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>라이브 단위 테스트 결과 보기(Visual Studio Enterprise)

Visual Studio 2017 이상에서 MSTest, xUnit 또는 NUnit 테스트 프레임워크를 사용하고 있다면 단위 테스트의 라이브 결과를 볼 수 있습니다.

> [!NOTE]
> 다음 단계를 수행하려면 Visual Studio Enterprise가 필요합니다.

1. **테스트** > **Live Unit Testing** > **시작** 을 선택하여 **테스트** 메뉴에서 라이브 단위 테스트를 켭니다.

   ::: moniker range="vs-2017"

   ![Live Unit Testing 설정](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019에서 라이브 단위 테스트 시작](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. 코드를 작성하고 편집할 때 코드 편집기 창에 테스트 결과가 표시됩니다.

   ![테스트 결과 보기](media/vs-2019/live-unit-testing-results.png)

1. 해당 메서드에 적용된 테스트의 이름과 같은 자세한 정보를 보려면 테스트 결과 표시기를 클릭합니다.

   ![테스트 결과 표시기 선택](media/vs-2019/live-unit-testing-details.png)

라이브 단위 테스트에 대한 자세한 내용은 [라이브 단위 테스트](../test/live-unit-testing-intro.md)를 참조하세요.

## <a name="use-a-third-party-test-framework"></a>타사 테스트 프레임워크 사용

프로그래밍 언어에 따라 Boost, Google, NUnit 등의 타사 테스트 프레임워크를 사용하여 Visual Studio에서 단위 테스트를 실행할 수 있습니다. 타사 프레임워크를 사용하려면 다음을 수행합니다.

- **NuGet 패키지 관리자** 를 사용하여 선택한 프레임워크에 대한 NuGet 패키지를 설치합니다.

- (.NET) Visual Studio 2017 버전 14.6부터 Visual Studio에는 NUnit 및 xUnit 테스트 프레임워크에 대해 미리 구성된 테스트 프로젝트 템플릿이 포함됩니다. 템플릿에는 지원을 사용하는 데 필요한 NuGet 패키지도 포함되어 있습니다.

- (C++) Visual Studio 2017 이상 버전에는 Boost와 같은 일부 프레임워크가 이미 포함되어 있습니다. 자세한 내용은 [Visual Studio에서 C/C++에 대한 단위 테스트 작성](../test/writing-unit-tests-for-c-cpp.md)을 참조하세요.

단위 테스트 프로젝트를 추가하려면 다음을 수행합니다.

1. 테스트할 코드가 포함된 솔루션을 엽니다.

2. **솔루션 탐색기** 에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트** 를 선택합니다.

3. 단위 테스트 프로젝트 템플릿을 선택합니다.

   이 예제에서는 [NUnit](https://nunit.org/)을 선택합니다.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019의 NUnit 테스트 프로젝트 템플릿](media/vs-2019/nunit-test-project-template.png)

   **다음** 을 클릭하여 프로젝트 이름을 지정한 다음, **만들기** 를 클릭합니다.

   ::: moniker-end

   ::: moniker range="vs-2017"

   프로젝트의 이름을 지정한 다음, **확인** 을 클릭하여 만듭니다.

   ::: moniker-end

   프로젝트 템플릿에는 NUnit 및 NUnit3TestAdapter에 대한 NuGet 참조가 포함됩니다.

   ![솔루션 탐색기의 NUnit NuGet 종속성](media/vs-2019/nunit-nuget-dependencies.png)

4. 테스트할 코드가 포함된 프로젝트에 테스트 프로젝트의 참조를 추가합니다.

   **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, **추가** > **참조** 를 선택합니다. **참조** 또는 **종속성** 노드의 오른쪽 클릭 메뉴에서 참조를 추가할 수도 있습니다.

5. 테스트 메서드에 코드를 추가합니다.

   ![단위 테스트 코드 파일에 코드 추가](media/vs-2019/unit-test-method.png)

6. **테스트 탐색기** 에서 테스트를 실행하거나, 테스트 코드를 마우스 오른쪽 단추로 클릭하고 **테스트 실행** 을 선택하여 테스트를 실행하거나, **Ctrl** + **R**, **T** 를 누릅니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [단위 테스트 기본 사항](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [관리 코드에 대한 단위 테스트 만들기 및 실행](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
