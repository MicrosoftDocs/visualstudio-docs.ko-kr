---
title: Visual C# 코드 유닛 테스트
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590867"
---
# <a name="unit-test-c-code"></a>C# 코드 단위 테스트

이 문서에서는 UWP 앱에서 C# 클래스에 대한 단위 테스트를 만드는 한 가지 방법에 대해 설명합니다.

테스트 중인 클래스인 **Rooter** 클래스는 지정된 숫자의 예상 제곱근을 계산하는 함수를 구현합니다.

이 문서에서는 *테스트 기반 개발*을 보여 줍니다. 이 방법에서는 먼저 테스트하고 있는 시스템에서 특정 동작을 확인하는 테스트를 작성한 다음 테스트를 통과하는 코드를 작성합니다.

## <a name="create-the-solution-and-the-unit-test-project"></a>솔루션 및 단위 테스트 프로젝트 만들기

1. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다.

2. **빈 앱(유니버설 Windows)** 프로젝트 템플릿을 검색하여 선택합니다.

3. 프로젝트 이름을 **Maths**로 지정합니다.

4. **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 차례로 선택합니다.

5. **단위 테스트 앱(유니버설 Windows)** 프로젝트 템플릿을 검색하여 선택합니다.

6. 테스트 프로젝트 이름을 **RooterTests**로 지정합니다.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>테스트가 테스트 탐색기에서 실행되는지 확인

1. *UnitTest.cs* 파일의 **TestMethod1**에 테스트 코드를 삽입합니다.

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 클래스는 테스트 메서드의 결과를 확인하는 데 사용할 수 있는 몇 가지 정적 메서드를 제공합니다.

::: moniker range="vs-2017"

2. **테스트** 메뉴에서 **실행** > **모든 테스트**를 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

2. **테스트** 메뉴에서 **모든 테스트 실행**을 선택합니다.

::: moniker-end

   테스트 프로젝트가 빌드되고 실행됩니다. 다소 시간이 걸릴 수 있으므로 잠시 기다립니다. **테스트 탐색기** 창이 나타나고 테스트가 **통과한 테스트** 아래에 나열됩니다. 창의 아래쪽에 있는 **요약** 창은 선택된 테스트에 대한 추가 정보를 제공합니다.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Maths 프로젝트에 Rooter 클래스 추가

1. **솔루션 탐색기**에서 **Maths** 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **추가** > **클래스**를 선택합니다.

2. 클래스 파일의 이름을 *Rooter.cs*로 지정합니다.

3. 다음 코드를 **Rooter** 클래스 *Rooter.cs* 파일에 추가합니다.

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   **Rooter** 클래스는 생성자와 **SquareRoot** 평가자 메서드를 선언합니다. **SquareRoot** 메서드는 테스트 설정의 기본 구조를 테스트할 정도의 최소 구현일 뿐입니다.

4. `public` 키워드를 **Rooter** 클래스 선언에 추가하여 테스트 코드에서 액세스할 수 있도록 합니다.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>프로젝트 참조 추가

1. RooterTests 프로젝트에서 Maths 앱에 대한 참조를 추가합니다.

    1. **솔루션 탐색기**에서 **RooterTests** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **참조**를 선택합니다.

    2. **참조 추가 - RooterTests** 대화 상자에서 **솔루션**을 확장하고 **프로젝트**를 선택한 다음, **Maths** 프로젝트를 선택합니다.

        ![Maths 프로젝트에 참조 추가](../test/media/ute_cs_windows_addreference.png)

2. *UnitTest.cs* 파일에 `using` 문을 추가합니다.

    1. *UnitTest.cs*를 엽니다.

    2. `using Microsoft.VisualStudio.TestTools.UnitTesting;` 줄 아래에 다음 코드를 추가합니다.

       ```csharp
       using Maths;
       ```

3. **Rooter** 함수를 사용하는 테스트를 추가합니다. *UnitTest.cs*에 다음 코드를 추가합니다.

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

   새 테스트가 **테스트 탐색기**의 **실행하지 않은 테스트** 노드에 표시됩니다.

4. "페이로드에 대상 경로가 같은 파일이 둘 이상 있습니다" 오류를 방지 하려면 **솔루션 탐색기**에서 **Maths** 프로젝트 아래의 **속성** 노드를 확장한 다음 *Default.rd.xml* 파일을 삭제합니다.

::: moniker range="vs-2017"

6. **테스트 탐색기**에서 **모두 실행**을 선택합니다.

   솔루션이 빌드되고 테스트가 실행되며 통과합니다.

   ![테스트 탐색기에서 통과된 BasicTest](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. **테스트 탐색기**에서 **모든 테스트 실행**을 선택합니다.

   솔루션이 빌드되고 테스트가 실행되며 통과합니다.

   ![테스트 탐색기에서 통과된 기본 테스트](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

테스트 및 앱 프로젝트를 설정하고 앱 프로젝트에서 함수를 호출하는 테스트를 실행할 수 있는지 확인했습니다. 이제 실제 테스트 및 코드 작성을 시작할 수 있습니다.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>반복적으로 테스트를 확장하고 통과하도록 만들기

1. **RangeTest**라는 새 테스트를 추가합니다.

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > 통과된 테스트는 변경하지 않는 것이 좋습니다. 새 테스트를 대신 추가합니다.

2. **RangeTest** 테스트를 실행하고 실패하는지 확인합니다.

   ![RangeTest 실패](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > 테스트를 작성한 후 즉시 실행하여 실패하는지 확인합니다. 이렇게 하면 결코 실패하지 않는 테스트를 작성하게 되는 간단한 실수를 방지하는 데 도움이 됩니다.

3. 새 테스트가 통과하도록 테스트 중인 코드를 개선합니다. *Rooter.cs*에서 **SquareRoot** 함수를 다음과 같이 변경합니다.

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

::: moniker range="vs-2017"

4. **테스트 탐색기**에서 **모두 실행**을 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. **테스트 탐색기**에서 **모든 테스트 실행**을 선택합니다.

::: moniker-end

   이제 세 테스트가 모두 통과합니다.

> [!TIP]
> 한 번에 하나씩 테스트를 추가하여 코드를 개발합니다. 각 반복 후 모든 테스트가 통과하는지 확인합니다.

## <a name="refactor-the-code"></a>코드 리팩터링

이 섹션에서는 앱과 테스트 코드를 모두 리팩터링하고 테스트를 다시 실행하여 계속 통과하는지 확인합니다.

### <a name="simplify-the-square-root-estimation"></a>제곱근 추정 단순화

1. 다음과 같이 코드 줄 하나를 변경하여 **SquareRoot** 함수에서 중앙 계산을 단순화합니다.

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. 모든 테스트를 실행하여 회귀를 도입하지 않았는지 확인합니다. 모두 통과되어야 합니다.

> [!TIP]
> 훌륭한 단위 테스트의 안정적인 집합은 코드를 변경할 때 버그를 만들지 않았다는 확신을 줍니다.

### <a name="eliminate-duplicated-code"></a>중복 코드 제거

**RangeTest** 메서드는 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 메서드에서 통과되는 *허용* 오차 변수의 분모를 하드 코드로 작성합니다. 동일한 허용 오차 계산을 사용하는 추가 테스트를 추가할 계획인 경우 여러 위치에서 하드 코드된 값을 사용하면 코드를 유지하기가 더 어려워집니다.

1. 허용 오차 값을 계산하기 위해 비공개 도우미 메서드를 **UnitTest1** 클래스에 추가한 다음, **RangeTest**에서 메서드를 호출합니다.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // Old code
        // double tolerance = expected/1000;

        // New code
        double tolerance = ToleranceHelper(expected);
    }
    ...
    ```

2. **RangeTest**를 실행하여 계속 통과하는지 확인합니다.

> [!TIP]
> **테스트 탐색기**에 표시하지 않으려는 도우미 메서드를 테스트 클래스에 추가하는 경우, 이 메서드에 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 특성을 추가하지 마세요.

## <a name="see-also"></a>참조

- [연습: 테스트 탐색기를 사용한 테스트 기반 개발](quick-start-test-driven-development-with-test-explorer.md)
