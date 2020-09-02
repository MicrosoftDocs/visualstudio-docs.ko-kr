---
title: 디버거를 사용한 예외 관리 | Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: how-to
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff28944a36d338230a17cd533a4832452e42885b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348459"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Visual Studio에서 디버거를 사용한 예외 관리

예외는 프로그램이 실행되는 동안 발생하는 오류 상태를 나타냅니다. 중단할 예외 또는 예외 세트를 디버거에 알리고 디버거를 중단할 지점(즉, 디버거에서 일시 중지)을 지정할 수 있습니다. 디버거가 중단되면 예외가 throw된 위치가 표시됩니다. 예외를 추가하거나 삭제할 수도 있습니다. Visual Studio에서 솔루션을 연 상태로 **디버그 > Windows > 예외 설정**을 사용하여 **예외 설정** 창을 엽니다.

가장 중요한 예외에 응답하는 처리기를 제공합니다. 예외에 대한 처리기를 추가하는 방법을 알아야 하는 경우 [더 나은 C# 코드를 작성하여 버그 수정](../debugger/write-better-code-with-visual-studio.md)을 참조하세요. 또한 일부 예외에 대해 항상 실행을 중단하도록 디버거를 구성하는 방법에 대해 알아봅니다.

예외가 발생하면 디버거가 **출력** 창에 예외 메시지를 씁니다. 다음과 같은 경우에 실행이 중단될 수 있습니다.

- 처리되지 않은 예외가 throw됩니다.
- 디버거는 처리기가 호출되기 전에 실행을 중단하도록 구성되어 있습니다.
- [내 코드만](../debugger/just-my-code.md)을 설정했으며, 사용자 코드에서 처리되지 않은 예외가 중단되도록 디버거가 구성되어 있습니다.

> [!NOTE]
> ASP.NET에는 브라우저에 오류 페이지를 표시하는 최상위 예외 처리기가 있습니다. **내 코드만**이 설정되지 않은 경우에는 실행이 중단되지 않습니다. 예제를 보려면 아래의 [사용자가 처리하지 않은 예외를 계속하도록 디버거에 지시](#BKMK_UserUnhandled)를 참조하세요.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Visual Basic 애플리케이션에서 디버거는 모든 오류를 예외로 관리합니다. 이는 On Error 스타일의 오류 처리기를 사용하는 경우에도 마찬가지입니다.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>예외가 throw되면 중단하도록 디버거에게 지시합니다.

디버거는 예외가 throw된 지점에서 실행을 중단할 수 있으므로 처리기가 호출되기 전에 예외를 검사할 수 있습니다.

**예외 설정** 창(**디버그 > Windows > 예외 설정**)에서 **공용 언어 런타임 예외**와 같은 예외 범주에 대한 노드를 확장합니다. 그런 다음, **System.AccessViolationException**과 같은 해당 범주 내의 특정 예외에 대한 확인란을 선택합니다. 전체 예외 범주를 선택할 수도 있습니다.

![확인된 AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> **예외 설정** 도구 모음에 있는 **검색** 창을 사용하여 특정 예외를 찾거나 검색을 사용하여 특정 네임스페이스(예: **System.IO**)를 필터링할 수 있습니다.

**예외 설정** 창에서 예외를 선택하면 처리 여부에 관계없이 예외가 throw될 때마다 디버거 실행이 중단됩니다. 이제 이 예외를 첫 번째 예외라고 합니다. 예를 들어 다음은 몇 가지 시나리오입니다.

- 다음 C# 콘솔 애플리케이션에서 Main 메서드는 `try/catch` 블록 내부에서 **AccessViolationException**을 발생시킵니다.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  **예외 설정**에서 **AccessViolationException**을 선택한 경우 이 코드를 디버거에서 실행하면 `throw` 줄에서 실행이 중단됩니다. 그런 다음 실행을 계속할 수 있습니다. 콘솔에 다음 두 줄이 모두 표시됩니다.

  ```cmd
  caught exception
  goodbye
  ```

  그러나 `here` 줄은 표시되지 않습니다.

- C# 콘솔 애플리케이션은 두 개의 메서드가 있는 클래스를 사용하여 클래스 라이브러리를 참조합니다. 한 메서드는 예외를 throw하고 처리하지만, 두 번째 메서드는 동일한 예외를 throw하지만 처리하지는 않습니다.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  콘솔 애플리케이션의 Main() 메서드는 다음과 같습니다.

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  **예외 설정**에서 **AccessViolationException**을 선택한 경우 이 코드를 디버거에서 실행하면 **ThrowHandledException()** 및 **ThrowUnhandledException()** 의 `throw` 줄에서 실행이 중단됩니다.

예외 설정을 기본값으로 복원하려면 **기본 설정으로 목록 복원** 단추를 선택합니다.

![예외 설정에서 기본값 복원](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>사용자가 처리하지 않은 예외에 대해 계속하도록 디버거에 지시

[내 코드만](../debugger/just-my-code.md)을 사용하여 .NET 또는 JavaScript 코드를 디버깅하는 경우 사용자 코드에서 처리되지 않았지만 다른 위치에서는 처리되는 예외가 중단하지 않도록 디버거에 지시할 수 있습니다.

1. **예외 설정** 창에서 열 레이블을 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 연 다음, **열 >추가 작업 표시**를 선택합니다. (**내 코드만**을 해제한 경우에는 이 명령이 표시되지 않습니다.) **추가 작업**이라는 세 번째 열이 표시됩니다.

   ![추가 작업 열](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   이 열에서 **사용자 코드에서 처리되지 않은 경우 계속**을 표시하는 예외의 경우 해당 예외가 사용자 코드에서 처리되지 않고 외부에서 치리되면 디버거는 계속됩니다.

2. 특정 예외에 대한 이 설정을 변경하려면 예외를 선택하고, 마우스 오른쪽 단추를 클릭하여 바로 가기 메뉴를 표시하고, **사용자 코드에서 처리되지 않은 경우 계속**을 선택합니다. 전체 공용 언어 런타임 예외와 같은 전체 예외 범주에 대한 설정을 변경할 수도 있습니다).

   ![**사용자 코드에서 처리되지 않은 경우 계속** 설정](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

예를 들어 ASP.NET 웹 애플리케이션은 예외를 HTTP 500 상태 코드([ASP.NET Web API의 예외 처리](/aspnet/web-api/overview/error-handling/exception-handling))로 변환하여 예외를 처리하므로 예외의 소스를 확인하는 데 도움이 되지 않을 수도 있습니다. 아래 예제에서는 사용자 코드가 `String.Format()` 을 발생시키는 <xref:System.FormatException>을 호출합니다. 다음과 같이 실행이 중단됩니다.

![사용자가 처리하지 않은 예외 중단](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>예외 추가 및 삭제

예외를 추가하거나 삭제할 수 있습니다. 범주에서 예외 유형을 삭제하려면 예외를 선택하고 **예외 설정** 도구 모음에서 **선택한 예외를 목록에서 삭제** 단추(빼기 기호)를 선택합니다. 또는 예외를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **삭제**를 선택할 수 있습니다. 예외를 삭제하는 것은 예외를 선택 취소하는 것과 같은 효과를 가집니다. 즉, 해당 예외가 throw될 때 디버거가 중단되지 않습니다.

예외를 추가하려면 다음을 수행합니다.

1. **예외 설정** 창에서 예외 범주 중 하나(예: **공용 언어 런타임**)를 선택합니다.

2. **선택한 범주에 예외 추가** 단추(더하기 기호)를 선택합니다.

   ![**선택한 범주에 예외 추가** 단추](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. 예외 이름을 입력합니다(예: **System.UriTemplateMatchException**).

   ![예외 이름 입력](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   예외가 목록에 추가(사전순으로)되고 자동으로 확인됩니다.

GPU 메모리 액세스 예외, JavaScript 런타임 예외 또는 Win32 예외 범주에 예외를 추가하려면 오류 코드 및 설명을 포함합니다.

> [!TIP]
> 맞춤법 검사를 수행합니다. **예외 설정** 창에서는 추가된 예외가 있는지 검사하지 않습니다. 따라서 **Sytem.UriTemplateMatchException**을 입력하면 해당 예외에 대한 항목( **System.UriTemplateMatchException**에 대한 항목이 아님)을 얻게 됩니다.

예외 설정은 솔루션의 .suo파일에 유지되므로 특정 솔루션에 적용됩니다. 특정 예외 설정을 여러 솔루션에서 다시 사용할 수 없습니다. 이제 추가된 예외만 유지되고, 삭제된 예외는 유지되지 않습니다. 예외를 추가하고 솔루션을 닫았다가 다시 열면 예외가 그대로 유지됩니다. 그러나 예외를 삭제한 후 솔루션을 닫았다가 다시 열면 예외가 다시 나타나지 않습니다.

**예외 설정** 창은 C#의 일반적인 예외 형식을 지원하지만 Visual Basic의 일반 예외 형식은 지원하지 않습니다. `MyNamespace.GenericException<T>`와 같은 예외에서 실행을 중단하려면 **MyNamespace.GenericException`1**과 같은 예외를 추가해야 합니다. 즉, 다음 코드와 같은 예외를 만든 경우:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

이전 절차를 사용하여 **예외 설정**에 다음과 같은 예외를 추가할 수 있습니다.

![일반 예외 추가](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>예외에 조건 추가

**예외 설정** 창을 사용하여 예외에 대한 조건을 설정합니다. 현재 지원되는 조건에는 예외에 포함하거나 제외할 모듈 이름이 포함됩니다. 모듈 이름을 조건으로 설정하여 특정 코드 모듈에서만 예외를 중단하도록 선택할 수 있습니다. 특정 모듈을 중단하지 않도록 선택할 수도 있습니다.

> [!NOTE]
> [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]부터 예외에 조건을 추가할 수 있습니다.

조건부 예외를 추가하려면 다음을 수행합니다.

1. 예외 설정 창에서 **조건 편집** 단추를 선택하거나 예외를 마우스 오른쪽 단추로 클릭하고 **조건 편집**을 선택합니다.

   ![예외에 대한 조건](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. 예외에 필요한 조건을 더 추가하려면 각 새 조건마다 **조건 추가**를 선택합니다. 추가 조건 줄이 표시됩니다.

   ![예외에 대한 추가 조건](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. 각 조건 줄에 대해 모듈의 이름을 입력하고 비교 연산자 목록을 **같음** 또는 **같지 않음**으로 변경합니다. 이름에 와일드카드( **\\\*** )를 지정하여 둘 이상의 모듈을 지정할 수 있습니다.

4. 조건을 삭제해야 하는 경우 조건 줄 끝에 있는 **X**를 선택합니다.

## <a name="see-also"></a>참조

- [예외 후 실행 계속](../debugger/continuing-execution-after-an-exception.md)<br/>
- [방법: 예외 발생 후 시스템 코드 검사](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [방법: 네이티브 런타임 검사 사용](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [C 런타임 라이브러리 없이 런타임 검사 사용](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [디버거 소개](../debugger/debugger-feature-tour.md)
