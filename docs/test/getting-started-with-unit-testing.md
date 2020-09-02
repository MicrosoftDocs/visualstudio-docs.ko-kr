---
title: 단위 테스트 시작
ms.date: 04/07/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c167e98f9419842876aed713e008b8746064669a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82153042"
---
# <a name="get-started-with-unit-testing"></a>단위 테스트 시작

Visual Studio를 사용하여 단위 테스트를 정의하고 실행하여 코드 상태를 유지 관리하고, 코드 적용 범위를 확인하고 , 고객이 찾기 전에 오류와 결함을 찾을 수 있습니다. 단위 테스트를 수시로 실행하여 코드가 올바르게 작동하는지 확인합니다.

## <a name="create-unit-tests"></a>단위 테스트 만들기

이 섹션에서는 단위 테스트 프로젝트를 만드는 방법을 설명합니다.

1. Visual Studio에서 테스트할 프로젝트를 엽니다.

   예제 단위 테스트를 보여 주기 위해 이 문서에서는 **HelloWorldCore**라는 간단한 “Hello World” 프로젝트를 테스트합니다. 이러한 프로젝트의 샘플 코드는 다음과 같습니다.

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

1. **솔루션 탐색기**에서 솔루션 노드를 선택합니다. 그런 다음, 상단 메뉴 모음에서 **파일** > **추가** > **새 프로젝트**를 선택합니다.

1. 새 프로젝트 대화 상자에서 사용할 테스트 프레임워크에 대한 단위 테스트 프로젝트 템플릿을 찾아 선택합니다.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019의 단위 테스트 프로젝트 템플릿](media/vs-2019/add-new-test-project.png)

   **다음**을 클릭하여 테스트 프로젝트의 이름을 선택한 다음, **만들기**를 클릭합니다.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Visual Studio 2019의 단위 테스트 프로젝트 템플릿](media/mstest-test-project-template.png)

   테스트 프로젝트의 이름을 선택한 다음, **확인**을 클릭합니다.

   ::: moniker-end

   프로젝트가 솔루션에 추가됩니다.

   ![솔루션 탐색기의 단위 테스트 프로젝트](media/vs-2019/solution-explorer.png)

1. 단위 테스트 프로젝트에서 **참조** 또는 **종속성**을 마우스 오른쪽 단추로 클릭한 다음, **참조 추가**를 선택하여 테스트하려는 프로젝트에 대한 참조를 추가합니다.

1. 테스트할 코드가 포함된 프로젝트를 선택하고 **확인**을 클릭합니다.

   ![Visual Studio에서 프로젝트 참조 추가](media/vs-2019/reference-manager.png)

1. 단위 테스트 메서드에 코드를 추가합니다.

   예를 들어 MSTest 테스트 프로젝트의 경우 다음 코드를 사용할 수 있고

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

   NUnit 테스트 프로젝트의 경우에는 다음 코드를 사용할 수 있습니다.

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

> [!TIP]
> 단위 테스트 만들기에 대한 자세한 내용은 [관리 코드에 대한 단위 테스트 만들기 및 실행](walkthrough-creating-and-running-unit-tests-for-managed-code.md)을 참조하세요.

## <a name="run-unit-tests"></a>단위 테스트 실행

1. [테스트 탐색기](../test/run-unit-tests-with-test-explorer.md)를 엽니다.

   ::: moniker range=">=vs-2019"
   테스트 탐색기를 열려면 상단 메뉴 모음에서 **테스트** > **테스트 탐색기**를 선택합니다.
   ::: moniker-end
   ::: moniker range="vs-2017"
   테스트 탐색기를 열려면 상단 메뉴 모음에서 **테스트** > **Windows** > **테스트 탐색기**를 선택합니다.
   ::: moniker-end

1. **모두 실행**을 클릭하여 단위 테스트를 실행합니다.

   ![테스트 탐색기에서 단위 테스트 실행](media/vs-2019/test-explorer-run-all.png)

   테스트가 완료된 후 녹색 확인 표시는 테스트가 통과되었음을 나타냅니다. 빨간색 "x" 아이콘은 테스트가 실패했음을 나타냅니다.

   ![테스트 탐색기에서 단위 테스트 결과 검토](media/vs-2019/unit-test-passed.png)

> [!TIP]
> [테스트 탐색기](../test/run-unit-tests-with-test-explorer.md)를 사용하여 기본 제공 테스트 프레임워크(MSTest) 또는 타사 테스트 프레임워크에서 단위 테스트를 실행할 수 있습니다. 테스트를 범주로 그룹화하고 테스트 목록을 필터링하고 테스트 재생 목록 생성, 저장 및 실행할 수 있습니다. 테스트를 디버그하고 테스트 성능 및 코드 검사를 분석할 수도 있습니다.

## <a name="view-live-unit-test-results"></a>라이브 단위 테스트 결과 보기

Visual Studio 2017 이상에서 MSTest, xUnit 또는 NUnit 테스트 프레임워크를 사용하고 있다면 단위 테스트의 라이브 결과를 볼 수 있습니다.

> [!NOTE]
> 라이브 단위 테스트는 Enterprise 버전에서만 사용 가능합니다.

1. **테스트** > **Live Unit Testing** > **시작**을 선택하여 **테스트** 메뉴에서 라이브 단위 테스트를 켭니다.

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

## <a name="generate-unit-tests-with-intellitest"></a>IntelliTest를 사용하여 단위 테스트 생성

IntelliTest를 실행하면 오류가 발생하는 테스트를 확인하고 필요한 코드를 추가하여 수정할 수 있습니다. 생성된 테스트 중에서 재발 테스트 모음을 제공하기 위해 테스트 프로젝트에 저장할 테스트를 선택할 수 있습니다. 코드를 변경하면 IntelliTest를 다시 실행하여 생성된 테스트를 코드 변경 내용과 동기화합니다. 방법을 알아보려면 [IntelliTest를 사용하여 코드에 대한 단위 테스트 생성](../test/generate-unit-tests-for-your-code-with-intellitest.md)을 참조하세요.

> [!TIP]
> IntelliTest는 .NET Framework를 대상으로 하는 관리 코드에만 사용할 수 있습니다.

![IntelliTest를 사용하여 단위 테스트 생성](media/intellitest.png)

## <a name="analyze-code-coverage"></a>코드 검사 분석

프로젝트의 코드 중 단위 테스트와 같은 코딩된 테스트를 사용하여 실제로 테스트할 부분을 결정하려면 Visual Studio의 코드 검사 기능을 사용합니다. 버그로부터 효과적으로 보호하려면 코드의 상당한 부분을 실행해야 합니다. 방법을 알아보려면 [코드 검사를 사용하여 테스트할 코드 범위 결정](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)을 참조하세요.

## <a name="use-a-third-party-test-framework"></a>타사 테스트 프레임워크 사용

Boost, Google, NUnit 등의 타사 테스트 프레임워크를 사용하여 Visual Studio에서 단위 테스트를 실행할 수 있습니다. **NuGet 패키지 관리자**를 사용하여 선택한 프레임워크에 대한 NuGet 패키지를 설치합니다. 또는 NUnit 및 xUnit 테스트 프레임워크의 경우 Visual Studio에는 필요한 NuGet 패키지를 포함하는 미리 구성된 테스트 프로젝트 템플릿이 포함되어 있습니다.

[NUnit](https://nunit.org/)을 사용하는 단위 테스트를 만들려면 다음을 수행합니다.

1. 테스트할 코드가 포함된 솔루션을 엽니다.

2. **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

3. **NUnit Test Project** 프로젝트 템플릿을 선택합니다.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019의 NUnit 테스트 프로젝트 템플릿](media/vs-2019/nunit-test-project-template.png)

   **다음**을 클릭하여 프로젝트 이름을 지정한 다음, **만들기**를 클릭합니다.

   ::: moniker-end

   ::: moniker range="vs-2017"

   프로젝트의 이름을 지정한 다음, **확인**을 클릭하여 만듭니다.

   ::: moniker-end

   프로젝트 템플릿에는 NUnit 및 NUnit3TestAdapter에 대한 NuGet 참조가 포함됩니다.

   ![솔루션 탐색기의 NUnit NuGet 종속성](media/vs-2019/nunit-nuget-dependencies.png)

4. 테스트할 코드가 포함된 프로젝트에 테스트 프로젝트의 참조를 추가합니다.

   **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, **추가** > **참조**를 선택합니다. **참조** 또는 **종속성** 노드의 오른쪽 클릭 메뉴에서 참조를 추가할 수도 있습니다.

5. 테스트 메서드에 코드를 추가합니다.

   ![단위 테스트 코드 파일에 코드 추가](media/vs-2019/unit-test-method.png)

6. **테스트 탐색기**에서 테스트를 실행하거나 테스트 코드를 마우스 오른쪽 단추로 클릭하고 **테스트 실행**을 선택하여 테스트를 실행합니다.

## <a name="see-also"></a>참조

* [연습: 관리 코드에 대한 단위 테스트 만들기 및 실행](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [단위 테스트 만들기 명령](create-unit-tests-menu.md)
* [IntelliTest를 사용하여 테스트 생성](generate-unit-tests-for-your-code-with-intellitest.md)
* [테스트 탐색기를 사용하여 테스트 실행](run-unit-tests-with-test-explorer.md)
* [코드 검사 분석](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
