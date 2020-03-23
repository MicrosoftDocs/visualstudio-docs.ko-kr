---
title: 디버거로 예외 관리 | 마이크로 소프트 문서
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: conceptual
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
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301124"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Visual Studio의 디버거를 통해 예외 관리

예외는 프로그램이 실행되는 동안 발생하는 오류 상태를 나타냅니다. 디버거에게 중단할 예외 또는 예외 집합과 디버거가 중단되도록 할 때(즉, 디버거에서 일시 중지) 알려줄 수 있습니다. 디버거가 중단되면 예외가 throw된 위치를 표시합니다. 예외를 추가하거나 삭제할 수도 있습니다. Visual Studio에서 솔루션을 열려 있는 경우 **Windows > 예외 설정에서 > 디버그를** 사용하여 **예외 설정** 창을 엽니다.

가장 중요한 예외에 응답하는 처리기를 제공합니다. 예외에 대한 처리기를 추가하는 방법을 알아야 하는 경우 [더 나은 C# 코드를 작성하여 버그 수정을](../debugger/write-better-code-with-visual-studio.md)참조하십시오. 또한 일부 예외에 대해 항상 실행을 중단하도록 디버거를 구성하는 방법에 대해알아봅니다.

예외가 발생하면 디버거는 **출력** 창에 예외 메시지를 씁니다. 다음과 같은 경우 실행이 중단될 수 있습니다.

- 처리되지 않은 예외가 throw됩니다.
- 디버거는 처리기가 호출되기 전에 실행을 중단하도록 구성됩니다.
- [내 코드만](../debugger/just-my-code.md)설정했으며 디버거는 사용자 코드에서 처리되지 않는 예외를 중단하도록 구성됩니다.

> [!NOTE]
> ASP.NET에는 브라우저에 오류 페이지를 표시하는 최상위 예외 처리기가 있습니다. **내 코드만** 켜져 있지 않으면 실행이 중단되지 않습니다. 예를 들어 [아래의 사용자가 처리하지 않은 예외를 계속 진행하도록 디버거에 알릴 것을 참조하세요.](#BKMK_UserUnhandled)

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Visual Basic 애플리케이션에서 디버거는 모든 오류를 예외로 관리합니다. 이는 On Error 스타일의 오류 처리기를 사용하는 경우에도 마찬가지입니다.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>예외가 throw될 때 디버거에게 중단하라고 지시합니다.

디버거는 예외가 throw된 지점에서 실행을 중단할 수 있으므로 처리기가 호출되기 전에 예외를 검사할 수 있습니다.

예외 **설정** 창(Windows > 예외 설정 >**디버그)에서**공통 언어 런타임 예외와 같은 예외 범주에 대한 **노드를 확장합니다.** 그런 다음 **System.Access위반예외와**같은 해당 범주 내의 특정 예외에 대한 확인란을 선택합니다. 전체 예외 범주를 선택할 수도 있습니다.

![확인된 AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "예외설정체크액세스")

> [!TIP]
> **예외 설정** 도구 모음에서 **검색** 창을 사용하여 특정 예외를 찾거나 검색을 사용하여 특정 네임스페이스(예: **System.IO)를**필터링할 수 있습니다.

**예외 설정** 창에서 예외를 선택하면 예외가 throw될 때마다 디버거 실행이 중단됩니다. 이제 예외를 첫 번째 기회 예외라고 합니다. 예를 들어 다음은 몇 가지 시나리오입니다.

- 다음 C# 콘솔 응용 프로그램에서 Main 메서드는 블록 내부에 `try/catch` **Access위반예외를** throw합니다.

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

  **예외 설정에서** **Access위반Exception을** 체크 인한 경우 `throw` 디버거에서 이 코드를 실행할 때 실행이 중단됩니다. 그런 다음 실행을 계속할 수 있습니다. 콘솔에 다음 두 줄이 모두 표시됩니다.

  ```cmd
  caught exception
  goodbye
  ```

  그러나 `here` 선이 표시되지 않습니다.

- C# 콘솔 응용 프로그램은 두 가지 메서드가 있는 클래스 라이브러리를 참조합니다. 한 메서드는 예외를 throw 하 고 처리 하는 동안 두 번째 메서드는 동일한 예외를 throw 하지만 처리 하지 않습니다.

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

  **예외 설정에서** `throw` **Access위반예외가** 체크인 경우 디버거에서 이 코드를 실행할 때 **throwHandledException()** 및 **ThrowUnhandledException()의** 줄에서 실행이 중단됩니다.

예외 설정을 기본값으로 복원하려면 **목록 복원을 기본 설정 단추로** 선택합니다.

![예외 설정에서 기본값 복원](../debugger/media/restoredefaultexceptions.png "복원기본예외")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>디버거에게 사용자가 처리되지 않은 예외를 계속하도록 지시

[내 코드로](../debugger/just-my-code.md).NET 또는 JavaScript 코드를 디버깅하는 경우 디버거에게 사용자 코드에서 처리되지 않지만 다른 곳에서 처리되는 예외를 위반하지 않도록 지시할 수 있습니다.

1. 예외 **설정** 창에서 열 레이블을 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 연 다음 **추가 작업 > 열 표시를**선택합니다. 내 **코드만**끄면 이 명령이 표시되지 않습니다. **추가 작업이라는** 세 번째 열이 나타납니다.

   ![추가 작업 열](../debugger/media/additionalactionscolumn.png "추가작업열")

   이 열의 **사용자 코드에서 처리되지 않은 경우 Continue를** 표시하는 예외의 경우 해당 예외가 사용자 코드에서 처리되지 않고 외부에서 처리되는 경우 디버거가 계속됩니다.

2. 특정 예외에 대해 이 설정을 변경하려면 예외를 선택하고 바로 가기 메뉴를 표시하려면 마우스 오른쪽 단추를 클릭하고 **사용자 코드에서 처리되지 않은 경우 계속을 선택합니다.** 전체 공통 언어 런타임 예외와 같은 전체 예외 범주에 대한 설정을 변경할 수도 있습니다.

   ![** 사용자 코드 ** 설정에서 처리되지 않은 경우 계속](../debugger/media/continuewhenunhandledinusercodesetting.png "계속처리되지 않은 사용자 코드 설정")

예를 들어 ASP.NET 웹 응용 프로그램은 예외의 출처를 확인하는 데 도움이 되지 않을 수 있는 HTTP 500 상태[코드(ASP.NET 웹 API의 예외 처리)로](/aspnet/web-api/overview/error-handling/exception-handling)변환하여 예외를 처리합니다. 아래 예제에서는 사용자 코드가 `String.Format()` 을 발생시키는 <xref:System.FormatException>을 호출합니다. 다음과 같이 실행이 중단됩니다.

![처리되지 않은 예외를&#45;사용자 에 대한 중단](../debugger/media/exceptionunhandledbyuser.png "예외처리되지 않은사용자")

## <a name="add-and-delete-exceptions"></a>예외 추가 및 삭제

예외를 추가하거나 삭제할 수 있습니다. 범주에서 예외 유형을 삭제하려면 예외를 선택하고 **예외 설정** 도구 모음의 목록 단추(빼기 **기호)에서 선택한 예외 삭제를** 선택합니다. 또는 예외를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **삭제를** 선택할 수 있습니다. 예외를 삭제하면 예외를 선택 취소하지 않는 것과 같은 효과가 있으며, 이는 디버거가 throw될 때 중단되지 않습니다.

예외를 추가하려면 다음을 수행하십시오.

1. 예외 **설정** 창에서 예외 범주 중 하나를 선택합니다(예: **공통 언어 런타임).**

2. 선택한 범주 단추(더하기 **기호)에 예외 추가를** 선택합니다.

   ![** 선택한 범주 ** 버튼에 예외 추가](../debugger/media/addanexceptiontotheselectedcategorybutton.png "추가예외To선택된범주")

3. 예외의 이름을 입력합니다(예: **System.UriTemplateMatchException).**

   ![예외 이름 입력](../debugger/media/typetheexceptionname.png "TypeThe예외 이름")

   예외는 목록에 (알파벳 순서로) 추가되고 자동으로 선택됩니다.

GPU 메모리 액세스 예외, 자바스크립트 런타임 예외 또는 Win32 예외 범주에 예외를 추가하려면 오류 코드와 설명을 포함합니다.

> [!TIP]
> 맞춤법 검사를 수행합니다. **예외 설정** 창은 추가된 예외가 있는지 확인하지 않습니다. 따라서 **Sytem.UriTemplateMatchException을**입력하면 해당 예외에 대한 항목이 **표시됩니다(System.UriTemplateMatchException)에**대한 항목이 표시됩니다.

예외 설정은 솔루션의 .suo파일에 유지되므로 특정 솔루션에 적용됩니다. 특정 예외 설정을 여러 솔루션에서 다시 사용할 수 없습니다. 이제 추가된 예외만 유지됩니다. 삭제된 예외는 그렇지 않습니다. 예외를 추가하고 솔루션을 닫고 다시 열 수 있으며 예외는 여전히 존재합니다. 그러나 예외를 삭제한 후 솔루션을 닫았다가 다시 열면 예외가 다시 나타나지 않습니다.

**예외 설정** 창은 C#의 일반적인 예외 형식을 지원하지만 Visual Basic의 일반 예외 형식은 지원하지 않습니다. `MyNamespace.GenericException<T>`와 같은 예외에서 실행을 중단하려면 **MyNamespace.GenericException`1**과 같은 예외를 추가해야 합니다. 즉, 이 코드와 같은 예외를 만든 경우:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

이전 프로시저를 사용하여 **예외를 예외 설정에** 추가할 수 있습니다.

![일반 예외 추가](../debugger/media/addgenericexception.png "추가 제네릭예외")

## <a name="add-conditions-to-an-exception"></a>예외에 조건 추가

예외 **설정** 창을 사용하여 예외에 대한 조건을 설정합니다. 현재 지원되는 조건에는 예외를 포함하거나 제외할 모듈 이름이 포함됩니다. 모듈 이름을 조건으로 설정하면 특정 코드 모듈에서만 예외에 대해 중단하도록 선택할 수 있습니다. 특정 모듈이 파손되지 않도록 선택할 수도 있습니다.

> [!NOTE]
> 예외에 조건을 추가하는 것은 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]에서부터 지원됩니다.

조건부 예외를 추가하려면 다음을 수행하십시오.

1. 예외 설정 창에서 **조건 편집** 단추를 선택하거나 예외를 마우스 오른쪽 단추로 클릭하고 **조건 편집을**선택합니다.

   ![예외 조건](../debugger/media/dbg-conditional-exception.png "Dbg조건예외")

2. 예외에 필요한 조건을 추가하려면 각 새 조건에 대해 **조건 추가를** 선택합니다. 추가 조건선이 나타납니다.

   ![예외에 대한 추가 조건](../debugger/media/extraconditionsforanexception.png "추가 조건예외")

3. 각 조건 줄에 대해 모듈 이름을 입력하고 비교 연산자 목록을 **같음** 또는 **같지 않음으로 변경합니다.** 이름에 와일드카드()**\\**를 지정하여 두 개 이상의 모듈을 지정할 수 있습니다.

4. 조건을 삭제해야 하는 경우 조건선의 끝에 있는 **X를** 선택합니다.

## <a name="see-also"></a>참고 항목

- [예외 후 실행 계속](../debugger/continuing-execution-after-an-exception.md)<br/>
- [방법: 예외 발생 후 시스템 코드 검사](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [방법: 네이티브 런타임 검사 기능 사용](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [C 런타임 라이브러리 없이 런타임 검사 사용](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [디버거 소개](../debugger/debugger-feature-tour.md)
