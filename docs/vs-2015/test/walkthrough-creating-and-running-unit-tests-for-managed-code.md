---
title: '연습: 관리 코드에 대한 단위 테스트 만들기 및 실행 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.assetid: 2b018b18-b412-4e0e-b0ee-b580a2f3ba9c
caps.latest.revision: 85
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 631a180789f5fff373799b78222c25a50ab32912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657097"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>연습: 관리 코드에 대한 단위 테스트 만들기 및 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 관리 코드에 대한 Microsoft 단위 테스트 프레임워크 및 Visual Studio 테스트 탐색기를 사용하여 일련의 단위 테스트를 생성, 실행 및 사용자 지정하는 방법을 안내합니다. 개발 중인 C# 프로젝트로 시작하여 해당 코드를 실행해 보는 테스트를 만들어 테스트를 실행하고 결과를 검사합니다. 그런 다음 프로젝트 코드를 변경하고 테스트를 다시 실행할 수 있습니다.

 이 항목에는 다음과 같은 섹션이 포함되어 있습니다.

 [연습 준비](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)

 [단위 테스트 프로젝트 만들기](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)

 [테스트 클래스 만들기](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)

- [테스트 클래스 요구 사항](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)

  [첫 번째 테스트 메서드 만들기](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)

- [테스트 메서드 요구 사항](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)

  [테스트 빌드 및 실행](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)

  [코드를 수정하고 테스트 다시 실행](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)

  [단위 테스트를 사용하여 코드 개선](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)

> [!NOTE]
> 이 연습에서는 관리 코드에 Microsoft 단위 테스트 프레임워크를 사용합니다. 테스트 탐색기에서는 테스트 탐색기용 어댑터가 포함된 타사 단위 테스트 프레임워크의 테스트도 실행할 수 있습니다. 자세한 내용은 [타사 단위 테스트 프레임 워크 설치](../test/install-third-party-unit-test-frameworks.md) 를 참조 하세요.

> [!NOTE]
> 명령줄에서 테스트를 실행하는 방법에 대한 자세한 내용은 [연습: 명령줄 테스트 유틸리티 사용](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)을 참조하세요.

## <a name="prerequisites"></a>사전 요구 사항

- Bank 프로젝트. [단위 테스트를 만들기 위한 샘플 프로젝트를](../test/sample-project-for-creating-unit-tests.md)참조 하세요.

## <a name="prepare-the-walkthrough"></a><a name="BKMK_Prepare_the_walkthrough"></a> 연습 준비

1. Visual Studio를 엽니다.

2. **파일** 메뉴에서 **새로 만들기** 를 가리킨 다음 **프로젝트**를 클릭합니다.

    **새 프로젝트** 대화 상자가 나타납니다.

3. **설치된 템플릿**에서 **Visual C#** 을 클릭합니다.

4. 애플리케이션 형식 목록에서 **클래스 라이브러리**를 클릭합니다.

5. In the **이름** 상자에 `Bank` 를 가리킨 다음 **확인**을 참조하세요.

   > [!NOTE]
   > "Bank"라는 이름이 이미 사용되고 있으면 프로젝트에 대해 다른 이름을 선택합니다.

    새 Bank 프로젝트가 만들어져 솔루션 탐색기에 표시되고 코드 편집기에 Class1.cs 파일이 열립니다.

   > [!NOTE]
   > Class1.cs 파일이 코드 편집기에서 열리지 않으면 솔루션 탐색기에서 Class1.cs 파일을 두 번 클릭하여 엽니다.

6. [단위 테스트를 만들기 위한 샘플 프로젝트](../test/sample-project-for-creating-unit-tests.md)에서 소스 코드를 복사합니다.

7. Class1.cs의 원래 내용을 [단위 테스트를 만들기 위한 샘플 프로젝트](../test/sample-project-for-creating-unit-tests.md)의 코드로 바꿉니다.

8. 파일을 BankAccount.cs로 저장합니다.

9. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

   이제 Bank라는 프로젝트가 준비되었습니다. 이 프로젝트에는 테스트할 소스 코드와 테스트에 사용할 도구가 들어 있습니다. Bank에 대한 네임스페이스 **BankAccountNS**에는 다음 절차에서 테스트할 메서드가 포함된 공용 클래스인 **BankAccount**가 있습니다.

   신속한 시작으로 사용자는 `Debit` 메서드에 집중합니다. 현금 인출 시 Debit 메서드가 호출되며 다음 코드가 포함됩니다.

```csharp
// method under test
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}

```

## <a name="create-a-unit-test-project"></a><a name="BKMK_Create_a_unit_test_project"></a> 단위 테스트 프로젝트 만들기
 **필수 조건**: [Prepare the walkthrough](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)절차의 단계를 따릅니다.

#### <a name="to-create-a-unit-test-project"></a>단위 테스트 프로젝트를 만들려면

1. **파일** 메뉴에서 **추가**를 선택한 다음 **새 프로젝트...** 를 선택합니다.

2. 새 프로젝트 대화 상자에서 **설치됨** 및 **Visual C#** 을 확장한 다음, **테스트**를 선택합니다.

3. 템플릿 목록에서 **단위 테스트 프로젝트**를 선택합니다.

4. **이름** 상자에 BankTest를 입력한 다음 **확인**을 선택합니다.

     **BankTests** 프로젝트가 **Bank** 솔루션에 추가됩니다.

5. **BankTests** 프로젝트에서 **Bank** 솔루션에 대한 참조를 추가합니다.

     솔루션 탐색기에서 **BankTests** 프로젝트의 **참조** 를 선택 하 고 상황에 맞는 메뉴에서 **참조 추가** ...를 선택 합니다.

6. 참조 관리자 대화 상자에서 **솔루션**을 확장한 다음, **Bank** 항목을 선택합니다.

## <a name="create-the-test-class"></a><a name="BKMK_Create_the_test_class"></a> 테스트 클래스 만들기
 `BankAccount` 클래스를 확인하려면 테스트 클래스가 필요합니다. 프로젝트 템플릿에서 생성된 UnitTest1.cs를 사용할 수 있지만 파일 및 클래스에 설명이 포함된 이름을 제공해야 합니다. 솔루션 탐색기에서 파일 이름을 바꾸면 한 번에 수행할 수 있습니다.

 **클래스 파일 이름 변경**

 솔루션 탐색기에서 BankTests 프로젝트의 UnitTest1.cs 파일을 선택합니다. 상황에 맞는 메뉴에서 **이름 바꾸기**를 선택한 다음 파일 이름을 BankAccountTests.cs로 바꿉니다. 프로젝트의 모든 참조 이름을 코드 요소 'UnitTest1'로 바꿀지 묻는 대화 상자에서 **예** 를 선택합니다. 이 단계에서는 클래스 이름을 `BankAccountTest`로 변경합니다.

 BankAccountTests.cs 파일에는 이제 다음 코드가 들어 있습니다.

```csharp
// unit test code
using System;
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

 **테스트에서 프로젝트에 using 문 추가**

 using 문을 클래스에 추가하여 정규화된 이름을 사용하지 않고 테스트 중인 프로젝트를 호출할 수 있습니다. 클래스 파일의 맨 위에 다음을 추가합니다.

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a><a name="BKMK_Test_class_requirements"></a> 테스트 클래스 요구 사항
 테스트 클래스의 최소 요구 사항은 다음과 같습니다.

- `[TestClass]` 특성은 테스트 탐색기에서 실행하려는 단위 테스트 메서드가 포함된 모든 클래스의 관리 코드에 대한 Microsoft 단위 테스트 프레임워크에 필요합니다.

- 테스트 탐색기에서 실행하려는 각 테스트 메서드에는 `[TestMethod]`특성이 있어야 합니다.

  `[TestClass]` 특성이 없는 단위 테스트 프로젝트에 다른 클래스를 사용하거나 `[TestMethod]` 특성이 없는 테스트 클래스에 다른 메서드를 사용할 수 있습니다. 테스트 메서드에서 이러한 다른 클래스와 메서드를 사용할 수 있습니다.

## <a name="create-the-first-test-method"></a><a name="BKMK_Create_the_first_test_method"></a> 첫 번째 테스트 메서드 만들기
 이 절차에서는 단위 테스트 메서드를 작성하여 `Debit` 클래스의 `BankAccount` 메서드 동작을 확인합니다. 이 메서드가 위에 나열되어 있습니다.

 테스트 중인 메서드를 분석한 결과, 세 가지 이상의 동작을 확인하기로 결정했습니다.

1. 메서드는 [ArgumentOutOfRangeException] (<!-- TODO: review code entity reference <xref:assetId:///ArgumentOutOfRangeException?qualifyHint=False&amp;autoUpgrade=True>  -->)가 잔액 보다 큰 경우

2. 또한 대변 금액이 0보다 작을 경우에도 `ArgumentOutOfRangeException` 을 발생시킵니다.

3. 1)과 2)의 검사가 충족될 경우 이 메서드는 계정 잔액에서 금액을 뺍니다.

   첫 번째 테스트에서는 유효 금액(계정 잔액보다 작고 0보다 큰 값)이 계정으로부터 올바른 금액을 인출하는지 확인합니다.

#### <a name="to-create-a-test-method"></a>테스트 메서드를 만들려면

1. using `BankAccountNS;` 문을 BankAccountTests.cs 파일에 추가합니다.

2. 다음 메서드를 `BankAccountTests` 클래스에 추가합니다.

   ```csharp
   // unit test code
   [TestMethod]
   public void Debit_WithValidAmount_UpdatesBalance()
   {
       // arrange
       double beginningBalance = 11.99;
       double debitAmount = 4.55;
       double expected = 7.44;
       BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

       // act
       account.Debit(debitAmount);

       // assert
       double actual = account.Balance;
       Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
   }
   ```

   이 메서드는 상당히 간단합니다. 기초 잔액으로 새 `BankAccount` 개체를 만든 다음 유효한 금액을 인출합니다. 관리 코드 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> 메서드에 Microsoft 단위 테스트 프레임워크를 사용하여 마감 잔액이 기대한 것과 같은지 확인합니다.

### <a name="test-method-requirements"></a><a name="BKMK_Test_method_requirements"></a> 테스트 메서드 요구 사항
 테스트 메서드는 다음 요구 사항을 충족해야 합니다.

- 이 메서드를 `[TestMethod]` 특성으로 데코레이팅해야 합니다.

- 이 메서드는 `void`를 반환해야 합니다.

- 메서드에 매개 변수를 사용할 수 없습니다.

## <a name="build-and-run-the-test"></a><a name="BKMK_Build_and_run_the_test"></a> 테스트 빌드 및 실행

#### <a name="to-build-and-run-the-test"></a>테스트를 빌드 및 실행하려면

1. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

     오류가 없는 경우 **실행하지 않은 테스트** 그룹에 나열된 **Debit_WithValidAmount_UpdatesBalance** 와 함께 UnitTestExplorer 창이 나타납니다. 빌드에 성공한 후 테스트 탐색기가 나타나지 않는 경우 메뉴에서 **테스트** 를 선택하고, **창**을 선택한 다음  **테스트 탐색기**를 선택합니다.

2. **모두 실행** 을 선택하여 테스트를 실행합니다. 테스트가 실행되는 동안 창 맨 위의 상태 표시줄에 애니메이션이 사용됩니다. 테스트 실행이 끝날 때 테스트 메서드가 통과했으면 녹색이 되고 테스트가 실패하면 빨간색이 됩니다.

3. 이러한 경우 테스트가 실패할 수 있습니다. 테스트 메서드가 **실패한 테스트**그룹으로 와 함께 UnitTestExplorer 창이 나타납니다. 창 하단에서 세부 정보를 보려면 테스트 탐색기에서 메서드를 선택합니다.

## <a name="fix-your-code-and-rerun-your-tests"></a><a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> 코드를 수정 하 고 테스트 다시 실행
 **테스트 결과 분석**

 테스트 결과에 실패를 설명하는 메시지가 포함됩니다. 메서드의 경우 `AreEquals` 메시지에 예상 된 항목 (<strong> \<*XXX*> 예상</strong>매개 변수)과 실제 수신 된 항목 ( **실제 \<*YYY*> ** 매개 변수)이 표시 됩니다. 기초 잔액보다 줄어든 잔액을 예상했지만, 인출액만큼 늘어났습니다.

 다시 검사한 Debit 코드에 단위 테스트를 통해 버그를 찾는 데 성공한 것으로 나타납니다. 차감해야 할 경우 계정 잔액에 인출금이 추가됩니다.

 **버그 수정**

 오류를 수정하려면 다음 줄

```csharp
m_balance += amount;
```

 다음과 같이 바꿉니다.

```csharp
m_balance -= amount;
```

 **테스트 다시 실행**

 테스트 탐색기에서 **모두 실행** 을 선택 하 여 테스트를 다시 실행 합니다. 빨강/녹색 막대가 녹색으로 바뀌고 테스트는 **통과한 테스트** 그룹으로 이동합니다.

## <a name="use-unit-tests-to-improve-your-code"></a><a name="BKMK_Use_unit_tests_to_improve_your_code"></a> 단위 테스트를 사용 하 여 코드 개선
 이 섹션에서는 반복적인 분석 프로세스, 단위 테스트 개발 및 리팩터링을 통해 프로덕션 코드를 보다 강력하고 효과적으로 만드는 방법을 설명합니다.

 **문제 분석**

 테스트 메서드를 만들어 `Debit` 메서드에서 유효한 금액이 정확하게 차감된 것을 확인한 후에는 원래 분석의 나머지 사례를 살펴볼 수 있습니다.

1. 이 메서드는 대변 금액이 잔액보다 큰 경우 `ArgumentOutOfRangeException` 을 발생시킵니다.

2. 또한 대변 금액이 0보다 작을 경우에도 `ArgumentOutOfRangeException` 을 발생시킵니다.

   **테스트 메서드 만들기**

   테스트 메서드를 만들어 이러한 문제를 해결하려는 첫 번째 시도가 성공할 가능성이 높습니다.

```csharp
//unit test method
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    account.Debit(debitAmount);

    // assert is handled by ExpectedException
}

```

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> 특성을 사용하여 올바른 예외가 throw되었음을 어설션합니다. `ArgumentOutOfRangeException` 을 throw되는 경우가 아니면 이 특성으로 인해 테스트에 실패합니다. 양수 및 음수 `debitAmount` 값을 모두 사용하여 테스트를 실행한 후 금액이 0보다 작은 경우 제네릭 <xref:System.ApplicationException> 을 throw하는 테스트를 위해 메서드를 일시적으로 수정하면 테스트가 올바르게 작동함을 알 수 있습니다. 인출한 금액이 잔액보다 많을 경우를 테스트하려면 다음을 수행해야 합니다.

1. `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`라는 새 테스트 메서드를 만듭니다.

2. `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` 의 메서드 본문을 새 메서드로 복사합니다.

3. `debitAmount` 를 잔액보다 큰 값으로 설정합니다.

   **테스트 실행**

   `debitAmount` 에 대한 값이 서로 다른 두 메서드를 실행하여 테스트에서 나머지 경우가 적절히 처리되는지 확인할 수 있습니다. 세 테스트를 모두 실행하면 원래 분석의 모든 경우가 올바르게 검사되는지 확인할 수 있습니다.

   **분석 계속 수행**

   하지만 마지막 두 테스트 메서드는 다소 문제가 있습니다. 각 테스트를 실행할 때 테스트 중인 코드의 어떤 조건이 throw되는지 확실히 알 수 없습니다. 두 조건을 구분하는 몇 가지 방법이 유용합니다. 즉, 위반한 조건을 확실히 알면 테스트에 대한 자신감이 증가합니다. 이 정보는 테스트 중인 메서드에 의해 throw되는 예외를 처리하는 프로덕션 메커니즘에도 유용할 것입니다. 메서드가 throw할 때 자세한 정보가 생성되면 관련된 모든 문제에 도움이 되지만 `ExpectedException` 특성은 이 정보를 제공할 수 없습니다.

   테스트 중인 메서드를 살펴보면 인수 이름을 매개 변수로 받는 `ArgumentOutOfRangeException` 생성자가 두 조건문 모두에 사용된다는 사실을 알 수 있습니다.

```csharp
throw new ArgumentOutOfRangeException("amount");
```

 MSDN 라이브러리를 검색하면 많은 정보를 제공하는 생성자가 있음을 알 수 있습니다. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` 에는 인수 이름, 인수 값 및 사용자 정의 메시지가 포함됩니다. 이 생성자를 사용하도록 테스트 중인 메서드를 리팩터링할 수 있습니다. 더 좋은 점은 공개적으로 사용할 수 있는 형식 멤버를 사용하여 오류를 지정할 수 있다는 점입니다.

 **테스트 중인 코드 리팩터링**

 먼저 클래스 범위에서 오류 메시지에 대한 두 개 상수를 정의합니다.

```csharp
// class under test
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";
```

 그런 다음 `Debit` 메서드에서 두 조건문을 수정합니다.

```csharp
// method under test
// ...
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
// ...
```

 **테스트 메서드 리팩터링**

 테스트 메서드에서 먼저 `ExpectedException` 특성을 제거합니다. 해당 위치에서 throw된 예외를 catch하고 올바른 조건 문에서 throw되었는지 확인합니다. 그러나 두 옵션 중 하나를 결정하여 나머지 조건을 확인해야 합니다. 예를 들어, `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` 메서드에서 다음 중 한 가지 작업을 수행할 수 있습니다.

- 예외의 `ActualValue` 속성( `ArgumentOutOfRangeException` 생성자의 두 번째 매개 변수)이 기초 잔액보다 크다고 어셜션합니다. 이 옵션을 사용하려면 테스트 메서드의 `ActualValue` 변수에 대해 예외의 `beginningBalance` 속성을 테스트해야 하고, `ActualValue` 가 0보다 큰지도 확인해야 합니다.

- 메시지(생성자의 세 번째 매개 변수)에 `DebitAmountExceedsBalanceMessage` 가 `BankAccount` 클래스에 정의되어 있음을 어셜션합니다.

  Microsoft 단위 테스트 프레임워크에서 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> 메서드를 사용하면 첫 번째 옵션에서 필요한 계산 없이도 두 번째 옵션을 확인할 수 있습니다.

  `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` 를 수정하는 두 번째 시도의 예를 들면 다음과 같습니다.

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
    }
}
```

 **재테스트, 재작성 및 재분석**

 테스트 메서드를 다른 값으로 다시 테스트하면 다음과 같은 사실이 발생합니다.

1. `debitAmount` 가 잔액보다 큰 어설션을 사용하여 올바른 오류를 catch하는 경우 `Contains` 어설션이 통과하고, 예외가 무시되어 테스트 메서드를 통과하게 됩니다. 이것이 바로 우리가 원하는 동작입니다.

2. 0보다 작은 `debitAmount` 를 사용할 경우 잘못된 오류 메시지가 반환되어 어설션이 실패합니다. 테스트 코드 경로 아래 메서드의 다른 지점에서 임시 `ArgumentOutOfRange` 예외를 유도하는 경우에도 어설션이 실패합니다. 이 점 역시 좋습니다.

3. `debitAmount` 값이 유효하면(예: 잔액보다 작지만 0보다 큼) 예외가 catch되지 않으므로 어설션이 절대로 catch되지 않습니다. 테스트 메서드를 통과합니다. 예외가 throw되지 않는 경우에도 테스트 메서드가 실패하지 않아야 하므로 이 방법은 좋지 않습니다.

   세 번째 사실은 테스트 메서드의 버그입니다. 여기서는 문제를 해결하기 위해 테스트 메서드 끝에 예외가 throw되지 않은 경우를 처리하도록 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> 어설션을 추가합니다.

   하지만 재테스트를 통해 올바른 예외가 catch되면 테스트가 실패한다는 점이 확인되었습니다. catch 문이 예외를 다시 설정하고 메서드가 계속 실행되어 새 어설션에서 실패합니다. 새 문제를 해결하기 위해 `return` 다음에 `StringAssert`문을 추가합니다. 재테스트를 통해 문제를 해결한 것을 확인합니다. `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` 의 최종 버전은 다음과 같습니다.

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
        return;
    }
    Assert.Fail("No exception was thrown.");
}

```

 이 최종 단원에서는 테스트 코드 개선 작업으로 테스트 메서드가 더욱 더 견고하고 유용해졌습니다. 하지만 더 중요한 것은 추가 분석을 통해 테스트 중인 프로젝트의 코드가 향상되었다는 점입니다.
