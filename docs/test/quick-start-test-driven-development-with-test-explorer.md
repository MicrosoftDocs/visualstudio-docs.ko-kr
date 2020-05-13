---
title: 테스트 기반 개발 연습
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a264975014fea88126bbca0589fe037e629dae10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566282"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>연습: 테스트 탐색기를 사용한 테스트 기반 개발

증분 코드 변경을 통해 코드가 제대로 작동하도록 하는 단위 테스트를 만듭니다. 타사에서 개발된 것을 비롯하여 단위 테스트를 작성하는 데 사용할 수 있는 프레임워크에는 여러 가지가 있습니다. 일부 테스트 프레임워크는 다른 언어 또는 플랫폼의 테스트를 위해 전문화되어 있습니다. 테스트 탐색기는 이러한 프레임워크 중 하나에서 단위 테스트를 위한 단일 인터페이스를 제공합니다. **테스트 탐색기**에 대한 자세한 내용은 [테스트 탐색기를 사용하여 단위 테스트 실행](run-unit-tests-with-test-explorer.md) 및 [테스트 탐색기 FAQ](test-explorer-faq.md)를 참조하세요.

이 연습에서는 Microsoft 테스트 프레임워크(MSTest)를 사용하여 C#에서 테스트 메서드를 개발하는 방법을 보여 줍니다. 다른 언어 또는 NUnit과 같은 다른 테스트 프레임워크에 맞도록 쉽게 조정할 수 있습니다. 자세한 내용은 [타사 단위 테스트 프레임워크 설치](install-third-party-unit-test-frameworks.md)를 참조하세요.

## <a name="create-a-test-and-generate-code"></a>테스트 만들기 및 코드 생성

1. C# **클래스 라이브러리(.NET Standard)** 프로젝트를 만듭니다. 이 프로젝트에는 테스트할 코드가 포함됩니다. 프로젝트 이름을 **MyMath**로 지정합니다.

2. 동일한 솔루션에서 새 **MSTest 테스트 프로젝트(.NET Core)** 프로젝트를 추가합니다. 테스트 프로젝트 이름을 **MathTests**로 지정합니다.

   ![새 코드 및 테스트 프로젝트](../test/media/test-driven-development-ide.png)

3. 특정 입력에 대해 얻은 결과를 확인하는 간단한 테스트 메서드를 작성합니다. `UnitTest1` 클래스에 다음 코드를 추가합니다.

   ```csharp
   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. 테스트 코드에서 형식을 생성합니다.

   1. 커서를 `Rooter`에 놓고 전구 메뉴에서 **‘Rooter’ 형식 생성** > **새 형식 생성**을 선택합니다.

      ![새 형식 빠른 작업 생성](media/test-driven-development-generate-new-type.png)

   2. **형식 생성** 대화 상자에서 **프로젝트**를 클래스 라이브러리 프로젝트인 **MyMath**로 설정한 다음 **확인**을 선택합니다.

      ![Visual Studio 2019의 형식 생성 대화 상자](media/test-driven-development-generate-type-dialog.png)

5. 테스트 코드에서 메서드를 생성합니다. 커서를 `SquareRoot`에 놓고 전구 메뉴에서 **‘Rooter.SquareRoot’ 메서드 생성**을 선택합니다.

6. 단위 테스트를 실행합니다.

   1. **테스트 탐색기**를 열려면 **테스트** 메뉴에서 **Windows** > **테스트 탐색기**를 선택합니다.

   2. **테스트 탐색기**에서 **모두 실행** 단추를 선택하여 테스트를 실행합니다.

   솔루션이 빌드되고 테스트가 실행되며 실패합니다.

7. 테스트의 이름을 선택합니다.

   테스트 세부 정보가 **테스트 세부 정보 요약** 창에 표시됩니다.

   ![테스트 탐색기의 테스트 세부 정보 요약](media/test-driven-development-test-detail-summary.png)

8. **스택 추적**에서 상위 링크를 선택하여 테스트가 실패한 위치로 이동합니다.

이제 테스트를 만들었으며 테스트를 통과하도록 수정할 스텁을 만들었습니다.

## <a name="verify-a-code-change"></a>코드 변경 확인

1. *Class1.cs* 파일에서 `SquareRoot`의 코드를 개선합니다.

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. **테스트 탐색기**에서 **모두 실행**을 선택합니다.

   솔루션이 빌드되고 테스트가 실행되며 통과합니다.

   ![통과한 테스트를 보여 주는 테스트 탐색기](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>입력 범위 확장

코드가 모든 경우에 작동한다는 확신을 높이기 위해 더욱 광범위한 입력 값 범위를 시도하는 테스트를 추가합니다.

> [!TIP]
> 통과한 기존 테스트를 변경하지 마십시오. 대신에 새 테스트를 추가합니다. 사용자 요구 사항이 변경될 때만 기존 테스트를 변경합니다. 이 정책을 적용하면 코드를 확장할 때 기존 기능이 손실되지 않습니다.

1. 테스트 클래스에서 입력 값 범위를 시도하는 다음 테스트를 추가합니다.

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. **테스트 탐색기**에서 **모두 실행**을 선택합니다.

   첫 번째 테스트는 여전히 통과하지만 새 테스트는 실패합니다. 실패 지점을 찾으려면 실패한 테스트를 선택한 다음 **테스트 세부 정보 요약** 창에서 세부 정보를 확인합니다.

3. 테스트 아래 메서드를 검사하여 잘못된 부분이 무엇인지 알아봅니다. 다음과 같이 `SquareRoot` 코드를 변경합니다.

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4. **테스트 탐색기**에서 **모두 실행**을 선택합니다.

   이제 두 테스트를 모두 통과합니다.

## <a name="add-tests-for-exceptional-cases"></a>예외 경우에 대한 테스트 추가

1. 음수 입력에 대한 새 테스트를 추가합니다.

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. **테스트 탐색기**에서 **모두 실행**을 선택합니다.

   테스트 아래 메서드가 반복적으로 실행되므로 수동으로 취소해야 합니다.

3. **테스트 탐색기**의 도구 모음에서 **취소**를 선택합니다.

   테스트 실행이 중지됩니다.

4. 메서드의 시작 부분에 다음 `if` 문을 추가하여 `SquareRoot` 코드를 수정합니다.

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. **테스트 탐색기**에서 **모두 실행**을 선택합니다.

   모든 테스트를 통과합니다.

## <a name="refactor-the-code-under-test"></a>테스트 중인 코드 리팩터링

코드를 리팩터링하되 테스트를 변경하지 마세요.

> [!TIP]
> *리팩터링* 은 코드가 더 잘 수행되도록 하거나 코드를 좀 더 쉽게 이해할 수 있도록 하기 위한 변경입니다. 코드의 동작을 변경하기 위한 것이 아니므로 테스트는 변경되지 않습니다.
>
> 기능을 확장하는 단계와 별도로 리팩터링 단계를 수행하는 것이 좋습니다. 테스트를 변경되지 않은 상태로 유지하면 리팩터링 중에 실수로 버그가 발생되지 않았다는 확신을 가질 수 있습니다.

1. `SquareRoot` 메서드에서 `result`를 계산하는 줄을 다음과 같이 변경합니다.

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }

        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
            previousResult = result;
            result = (result + input / result) / 2;
            //was: result = result - (result * result - input) / (2*result);
        }
        return result;
    }
    ```

2. **모두 실행**을 선택하고 모든 테스트가 계속 통과하는지 확인합니다.

   ![통과한 테스트 3개를 보여 주는 테스트 탐색기](../test/media/test-driven-development-three-passed-tests.png)
