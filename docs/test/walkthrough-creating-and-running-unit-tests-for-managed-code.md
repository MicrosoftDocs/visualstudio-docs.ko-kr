---
title: C# 단위 테스트 자습서
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 4d5878e2c5950e45f65f8d56efdf53cd7b2e89ea
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094673"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>연습: 관리 코드에 대한 단위 테스트 만들기 및 실행

이 문서에서는 관리 코드에 대한 Microsoft 단위 테스트 프레임워크 및 Visual Studio **테스트 탐색기**를 사용하여 일련의 단위 테스트를 생성, 실행 및 사용자 지정하는 방법을 안내합니다. 개발 중인 C# 프로젝트로 시작하여 해당 코드를 실행해 보는 테스트를 만들어 테스트를 실행하고 결과를 검사합니다. 그런 다음, 프로젝트 코드를 변경하고 테스트를 다시 실행합니다.



## <a name="create-a-project-to-test"></a>테스트할 프로젝트 만들기

::: moniker range="vs-2017"

1. Visual Studio를 엽니다.

2. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택합니다.

   **새 프로젝트** 대화 상자가 나타납니다.

3. **Visual C#** > **.NET Core** 카테고리에서 **콘솔 앱(.NET Core)** 프로젝트 템플릿을 선택합니다.

4. 프로젝트의 이름을 **Bank**로 지정한 다음, **확인**을 클릭합니다.

   Bank 프로젝트가 만들어져 **솔루션 탐색기**에 표시되고 코드 편집기에 *Program.cs* 파일이 열립니다.

   > [!NOTE]
   > *Program.cs*가 편집기에 열리지 않으면 *솔루션 탐색기*에서 **Program.cs** 파일을 두 번 클릭하여 엽니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio를 엽니다.

2. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

3. C# **콘솔 앱(.NET Core)** 프로젝트 템플릿을 검색하여 선택한 후, **다음**을 클릭합니다.

4. 프로젝트의 이름을 **Bank**로 지정한 다음, **만들기**를 클릭합니다.

   Bank 프로젝트가 만들어져 **솔루션 탐색기**에 표시되고 코드 편집기에 *Program.cs* 파일이 열립니다.

   > [!NOTE]
   > *Program.cs*가 편집기에 열리지 않으면 *솔루션 탐색기*에서 **Program.cs** 파일을 두 번 클릭하여 엽니다.

::: moniker-end

5. *Program.cs*의 내용을 *BankAccount* 클래스를 정의하는 다음 C# 코드로 바꿉니다.

   ```csharp
   using System;

   namespace BankAccountNS
   {
       /// <summary>
       /// Bank account demo class.
       /// </summary>
       public class BankAccount
       {
           private readonly string m_customerName;
           private double m_balance;

           private BankAccount() { }

           public BankAccount(string customerName, double balance)
           {
               m_customerName = customerName;
               m_balance = balance;
           }

           public string CustomerName
           {
               get { return m_customerName; }
           }

           public double Balance
           {
               get { return m_balance; }
           }

           public void Debit(double amount)
           {
               if (amount > m_balance)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount; // intentionally incorrect code
           }

           public void Credit(double amount)
           {
               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount;
           }

           public static void Main()
           {
               BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

               ba.Credit(5.77);
               ba.Debit(11.22);
               Console.WriteLine("Current balance is ${0}", ba.Balance);
           }
       }
   }
   ```

6. *솔루션 탐색기*에서 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택하여 파일의 이름을 **BankAccount.cs**로 바꿉니다.

7. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

이제 테스트할 수 있는 메서드를 포함한 프로젝트가 준비되었습니다. 이 문서에서는 `Debit` 메서드 테스트에 집중합니다. `Debit` 메서드는 계좌에서 돈을 인출할 때 호출됩니다.

## <a name="create-a-unit-test-project"></a>단위 테스트 프로젝트 만들기

1. **파일** 메뉴에서 **추가** > **새 프로젝트**를 선택합니다.

   > [!TIP]
   > **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택할 수도 있습니다.

::: moniker range="vs-2017"

2. **새 프로젝트** 대화 상자에서 **설치됨** 및 **Visual C#** 을 확장한 다음, **테스트**를 선택합니다.

3. 템플릿 목록에서 **MSTest 테스트 프로젝트(.NET Core)** 를 선택합니다.

4. **이름** 상자에 `BankTests`를 입력한 다음, **확인**을 선택합니다.

   **BankTests** 프로젝트가 **Bank** 솔루션에 추가됩니다.

::: moniker-end

::: moniker range=">=vs-2019"

2. C# **MSTest 테스트 프로젝트(.NET Core)** 프로젝트 템플릿을 검색하여 선택한 후, **다음**을 클릭합니다.

3. 프로젝트 이름을 **BankTests**로 지정합니다.

4. **만들기**를 클릭합니다.

   **BankTests** 프로젝트가 **Bank** 솔루션에 추가됩니다.

::: moniker-end

5. **BankTests** 프로젝트에서 **Bank** 프로젝트에 대한 참조를 추가합니다.

   **솔루션 탐색기**에서 **BankTests** 프로젝트 아래의 **종속성**을 선택한 다음, 오른쪽 클릭 메뉴에서 **참조 추가**를 선택합니다.

6. **참조 관리자** 대화 상자에서 **프로젝트**를 확장하고 **솔루션**을 선택한 다음, **Bank** 항목을 선택합니다.

7. **확인**을 선택합니다.

## <a name="create-the-test-class"></a>테스트 클래스 만들기

`BankAccount` 클래스를 확인하기 위한 테스트 클래스를 만듭니다. 프로젝트 템플릿에서 생성된 *UnitTest1.cs* 파일을 사용할 수 있지만 파일 및 클래스에 설명이 포함된 이름을 제공할 수 있습니다.

### <a name="rename-a-file-and-class"></a>파일 및 클래스 이름 바꾸기

1. 파일의 이름을 바꾸려면 **솔루션 탐색기**에서 BankTests 프로젝트의 *UnitTest1.cs* 파일을 선택합니다. 오른쪽 클릭 메뉴에서 **이름 바꾸기**를 선택한 다음, 파일 이름을 *BankAccountTests.cs*로 바꿉니다.

::: moniker range="vs-2017"

2. 클래스 이름을 변경하려면 팝업되어 코드 요소에 대한 참조 이름도 변경할지 묻는 대화 상자에서 **예**를 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

2. 클래스의 이름을 바꾸려면 코드 편집기에서 커서를 `UnitTest1`에 두고 **이름 바꾸기**를 선택합니다. **BankAccountTests**를 입력한 다음, **Enter**를 누릅니다.

::: moniker-end

*BankAccountTests.cs* 파일에는 이제 다음 코드가 들어 있습니다.

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

### <a name="add-a-using-statement"></a>using 문 추가

[`using` 문](/dotnet/csharp/language-reference/keywords/using-statement)을 테스트 클래스에 추가하여 정규화된 이름을 사용하지 않고 테스트 중인 프로젝트를 호출할 수 있습니다. 클래스 파일의 맨 위에 다음을 추가합니다.

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>테스트 클래스 요구 사항

테스트 클래스의 최소 요구 사항은 다음과 같습니다.

- `[TestClass]` 특성은 테스트 탐색기에서 실행하려는 단위 테스트 메서드가 포함된 모든 클래스에 필요합니다.

- 테스트 탐색기에서 인식하려는 각 테스트 메서드에는 `[TestMethod]` 특성이 있어야 합니다.

`[TestClass]` 특성이 없는 단위 테스트 프로젝트에 다른 클래스를 사용하거나 `[TestMethod]` 특성이 없는 테스트 클래스에 다른 메서드를 사용할 수 있습니다. 테스트 메서드에서 해당 다른 클래스 및 메서드를 호출할 수 있습니다.

## <a name="create-the-first-test-method"></a>첫 번째 테스트 메서드 만들기

이 절차에서는 단위 테스트 메서드를 작성하여 `Debit` 클래스의 `BankAccount` 메서드 동작을 확인합니다.

확인해야 하는 동작이 3개 이상 있습니다.

- 이 메서드는 대변 금액이 잔액보다 큰 경우 <xref:System.ArgumentOutOfRangeException> 을 발생시킵니다.

- 이 메서드는 차변 금액이 0보다 작을 경우 <xref:System.ArgumentOutOfRangeException>을 throw합니다.

- 대변 금액이 유효한 경우 이 메서드는 잔고에서 차변 금액을 뺍니다.

> [!TIP]
> 이 연습에서 사용하지 않으므로 기본 `TestMethod1` 메서드를 삭제할 수 있습니다.

### <a name="to-create-a-test-method"></a>테스트 메서드를 만들려면

첫 번째 테스트에서는 유효 금액(잔고보다 작고 0보다 큰 값)이 계좌로부터 올바른 금액을 인출하는지 확인합니다. 다음 메서드를 `BankAccountTests` 클래스에 추가합니다.

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

메서드가 간단함: 기초 잔액으로 새 `BankAccount` 개체를 설정한 다음, 유효한 금액을 인출합니다. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> 메서드를 사용하여 최종 잔액이 기대한 것과 같은지 확인합니다.

### <a name="test-method-requirements"></a>테스트 메서드 요구 사항

테스트 메서드는 다음 요구 사항을 충족해야 합니다.

- `[TestMethod]` 특성으로 데코레이트됩니다.

- `void`를 반환합니다.

- 매개 변수를 사용할 수 없습니다.

## <a name="build-and-run-the-test"></a>테스트 빌드 및 실행

1. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

2. **테스트 탐색기**가 열리지 않은 경우 상단 메뉴 모음에서 **테스트** > **Windows** > **테스트 탐색기**를 선택하여 엽니다.

3. **모두 실행** 을 선택하여 테스트를 실행합니다.

   테스트가 실행되는 동안 **테스트 탐색기** 창 맨 위의 상태 표시줄에 애니메이션이 사용됩니다. 테스트 실행이 끝날 때 테스트 메서드가 통과했으면 녹색이 되고 테스트가 실패하면 빨간색이 됩니다.

   이러한 경우 테스트가 실패합니다.

4. 창 하단에서 세부 정보를 보려면 **테스트 탐색기**에서 메서드를 선택합니다.

## <a name="fix-your-code-and-rerun-your-tests"></a>코드를 수정하고 테스트 다시 실행

테스트 결과에 실패를 설명하는 메시지가 포함됩니다. `AreEqual` 메서드의 메시지는 예상 내용과 실제로 수신된 내용을 표시합니다. 잔액이 감소할 것으로 예상했지만 인출금만큼 증가했습니다.

단위 테스트에서 버그 발견됨: *차감*해야 할 경우 잔고에 인출금이 *추가*됩니다.

### <a name="correct-the-bug"></a>버그 수정

오류를 수정하려면 *BankAccount.cs* 파일에서 아래 줄을

```csharp
m_balance += amount;
```

다음 구문으로 바꿉니다.

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>테스트 다시 실행

**테스트 탐색기**에서 **모두 실행**을 선택하여 테스트를 다시 실행합니다. 빨강/녹색 막대가 테스트를 통과했음을 나타내는 녹색으로 바뀝니다.

![통과한 테스트를 보여주는 Visual Studio 2019의 텍스트 탐색기](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>단위 테스트를 사용하여 코드 개선

이 섹션에서는 반복적인 분석 프로세스, 단위 테스트 개발 및 리팩터링을 통해 프로덕션 코드를 보다 강력하고 효과적으로 만드는 방법을 설명합니다.

### <a name="analyze-the-issues"></a>문제 분석

유효한 금액이 `Debit` 메서드에서 제대로 공제되었는지 확인하기 위한 테스트 메서드를 만들었습니다. 이제 차변 금액이 다음 중 하나인 경우 메서드가 <xref:System.ArgumentOutOfRangeException>을 throw하는지 확인합니다.

- 잔고보다 크거나
- 0보다 작음

### <a name="create-and-run-new-test-methods"></a>새 메서드를 만들고 실행합니다.

차변 금액이 0보다 작은 경우 올바른 동작을 확인하기 위해 테스트 메서드를 만듭니다.

```csharp
[TestMethod]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act and assert
    Assert.ThrowsException<System.ArgumentOutOfRangeException>(() => account.Debit(debitAmount));
}
```

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> 메서드를 사용하여 올바른 예외가 throw되었음을 어설션합니다. <xref:System.ArgumentOutOfRangeException>을 throw되는 경우가 아니면 이 메서드로 인해 테스트에 실패합니다. 차변 금액이 0보다 작을 때, 보다 일반적인 <xref:System.ApplicationException>을 throw하기 위해 테스트 중인 메서드를 일시적으로 수정하면 테스트가 올바르게 작동합니다&mdash;즉, 실패합니다.

인출한 금액이 잔고보다 많을 경우를 테스트하려면 다음 단계를 수행합니다.

1. `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`라는 새 테스트 메서드를 만듭니다.

2. `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` 의 메서드 본문을 새 메서드로 복사합니다.

3. `debitAmount` 를 잔액보다 큰 값으로 설정합니다.

두 개의 테스트를 실행하고 통과하는지 확인합니다.

### <a name="continue-the-analysis"></a>분석 계속 수행

테스트 중인 메서드를 추가로 개선할 수 있습니다. 현재 구현에서는 어떤 조건(`amount > m_balance` 또는 `amount < 0`)으로 인해서 테스트 중에 예외가 throw되는지 알 수 있는 방법이 없습니다. `ArgumentOutOfRangeException`이 메서드의 어떤 지점에서 throw되었다는 사실만 알고 있습니다. `BankAccount.Debit`에서 어떤 조건으로 인해 예외가 throw되었는지 알 수 있다면 더 나을 것이므로(`amount > m_balance` 또는 `amount < 0`) 인수에 대한 온전성 검사를 정확히 수행하는 메서드임을 확인할 수 있습니다.

테스트 중인 메서드(`BankAccount.Debit`)를 다시 살펴보면 인수 이름을 매개 변수로 받는 `ArgumentOutOfRangeException` 생성자가 두 조건문 모두에 사용된다는 사실을 알 수 있습니다.

```csharp
throw new ArgumentOutOfRangeException("amount");
```

훨씬 많은 정보를 보고하는 데 사용할 수 있는 생성자가 있음: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)>에는 인수 이름, 인수 값 및 사용자 정의 메시지가 포함됩니다. 이 생성자를 사용하도록 테스트 중인 메서드를 리팩터링할 수 있습니다. 더 좋은 점은 공개적으로 사용할 수 있는 형식 멤버를 사용하여 오류를 지정할 수 있다는 점입니다.

### <a name="refactor-the-code-under-test"></a>테스트 중인 코드 리팩터링

먼저 클래스 범위에서 오류 메시지에 대한 두 개 상수를 정의합니다. 다음을 테스트 중인 클래스에 배치합니다(`BankAccount`).

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

그런 다음, `Debit` 메서드에서 두 조건문을 수정합니다.

```csharp
if (amount > m_balance)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
}

if (amount < 0)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
}
```

### <a name="refactor-the-test-methods"></a>테스트 메서드 리팩터링

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>에 대한 호출을 제거하여 테스트 메서드를 리팩터링합니다. `Debit()` 블록에서 `try/catch`에 대한 호출을 래핑하고 예상되는 특정 예외를 catch한 다음, 연결된 메시지를 확인합니다. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> 메서드는 두 문자열을 비교하는 기능을 제공합니다.

이제 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`는 다음과 같습니다.

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>재테스트, 재작성 및 재분석

테스트 중인 메서드에 버그가 있는데 `Debit` 메서드에서 <xref:System.ArgumentOutOfRangeException>을 throw하지 않는 경우라도 올바른 메시지가 예외와 함께 출력될 수 있습니다. 현재는 테스트 메서드가 이러한 사례를 처리하지 않습니다. `debitAmount` 값이 유효하면(즉, 잔액보다 작고 0보다 큼) 예외가 catch되지 않으므로 어설션이 절대로 시작되지 않습니다. 그런데도 테스트 메서드를 통과합니다. 예외가 throw되지 않는 경우에도 테스트 메서드가 실패하지 않아야 하므로 이 방법은 좋지 않습니다.

이것은 테스트 메서드의 버그입니다. 문제를 해결하려면 테스트 메서드 끝에 예외가 throw되지 않은 경우를 처리하도록 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> 어설션을 추가합니다.

테스트를 다시 실행하여 올바른 예외가 catch되면 테스트가 *실패*한다는 점이 확인되었습니다. `catch` 블록은 예외를 catch하지만 메서드가 계속 실행되고 새로운 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> 어설션에서 실패합니다. 이 문제를 해결하려면 `return` 블록에서 `StringAssert` 다음에 `catch`문을 추가합니다. 테스트를 다시 실행하여 이 문제가 수정되었는지 확인합니다. `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`의 최종 버전은 다음과 같습니다.

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

### <a name="conclusion"></a>결론

테스트 코드가 개선되어 보다 강력하고 유익한 테스트 메서드가 제공됩니다. 하지만 무엇보다도 중요한 것은 테스트 중인 코드 역시 향상되었다는 점입니다.

> [!TIP]
> 이 연습에서는 관리 코드에 Microsoft 단위 테스트 프레임워크를 사용합니다. **테스트 탐색기**에서는 **테스트 탐색기**용 어댑터가 포함된 타사 단위 테스트 프레임워크의 테스트도 실행할 수 있습니다. 자세한 내용은 [타사 단위 테스트 프레임워크 설치](../test/install-third-party-unit-test-frameworks.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

명령줄에서 테스트를 실행하는 방법에 대한 자세한 내용은 [VSTest.Console.exe command-line 옵션](vstest-console-options.md)을 참조하세요.
