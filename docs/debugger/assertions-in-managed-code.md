---
title: 관리 코드의 어설션 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 529c19753d09d6335e5c9fc5e839cdb7cd0c118c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745783"
---
# <a name="assertions-in-managed-code"></a>관리 코드의 어설션
어설션 또는 `Assert` 문은 `Assert` 문에 대한 인수로 지정하는 조건을 테스트합니다. 조건이 true로 평가되면 동작이 발생하지 않고, 조건이 false로 평가되면 어설션이 실패합니다. 디버그 빌드로 실행 중인 경우 프로그램 중단 모드가 시작됩니다.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 항목 내용
 [System.Diagnostics 네임스페이스의 어설션](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)

 [Debug.Assert 메서드](#BKMK_The_Debug_Assert_method)

 [Debug.Assert의 파생 작업](#BKMK_Side_effects_of_Debug_Assert)

 [Trace 및 Debug 요구 사항](#BKMK_Trace_and_Debug_Requirements)

 [어설션 인수](#BKMK_Assert_arguments)

 [어설션 동작 사용자 지정](#BKMK_Customizing_Assert_behavior)

 [구성 파일에서 어설션 설정](#BKMK_Setting_assertions_in_configuration_files)

## <a name="asserts-in-the-systemdiagnostics-namespace"></a><a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> System.Diagnostics 네임스페이스의 어설션
 Visual Basic 및 Visual C#에서는 `Assert` 네임스페이스에 있는 <xref:System.Diagnostics.Debug> 또는 <xref:System.Diagnostics.Trace>에서 <xref:System.Diagnostics> 메서드를 사용할 수 있습니다. <xref:System.Diagnostics.Debug> 클래스 메서드는 프로그램의 릴리스 버전에 포함되지 않으므로 릴리스 코드의 크기를 증가시키거나 속도를 떨어뜨리지 않습니다.

 C++는 <xref:System.Diagnostics.Debug> 클래스 메서드를 지원하지 않습니다. 조건부 컴파일(예: `#ifdef DEBUG`... `#endif`)에 <xref:System.Diagnostics.Trace> 클래스를 사용하면 동일한 결과를 얻을 수 있습니다.

 [항목 내용](#BKMK_In_this_topic)

## <a name="the-debugassert-method"></a><a name="BKMK_The_Debug_Assert_method"></a> Debug.Assert 메서드
 코드가 정확한 경우 true로 유지되어야 하는 조건을 테스트하려면 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 메서드를 사용합니다. 예를 들어 정수 나누기 함수를 작성한 경우, 수학의 규칙에 따라 0으로는 나눌 수 없습니다. 다음과 같이 어설션을 사용하여 이를 테스트할 수 있습니다.

```VB
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer
    Debug.Assert(divisor <> 0)
    Return CInt(dividend / divisor)
End Function
```

```csharp
int IntegerDivide ( int dividend , int divisor )
    { Debug.Assert ( divisor != 0 );
        return ( dividend / divisor ); }
```

 디버거에서 이 코드를 실행하면 어설션 문이 평가되지만, 릴리스 버전에서는 비교가 실행되지 않으므로 추가 오버헤드가 없습니다.

 또는 다음과 같은 예도 있습니다. 다음과 같이 당좌 예금 계좌를 구현하는 클래스가 있다고 가정합니다.

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Debug.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Debug.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 계좌에서 돈을 인출하기 전에 인출하려는 금액 이상의 잔액이 있는지 확인해야 합니다. 다음과 같은 어설션을 작성하여 잔액을 확인할 수 있습니다.

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Trace.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Trace.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 작성한 코드로 릴리스 버전을 만들면 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 메서드에 대한 호출이 사라집니다. 즉, 릴리스 버전에서는 잔액을 확인하는 호출이 사라집니다. 이 문제를 해결하려면 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 대신 릴리스 버전에서 사라지지 않는 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>를 사용해야 합니다.

 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 호출과 달리 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 호출은 릴리스 버전에 오버헤드를 추가합니다.

 [항목 내용](#BKMK_In_this_topic)

## <a name="side-effects-of-debugassert"></a><a name="BKMK_Side_effects_of_Debug_Assert"></a> Debug.Assert의 파생 작업
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>를 사용할 때는 `Assert`가 제거되어도 `Assert` 내의 코드에 의해 프로그램의 결과가 변경되지 않도록 해야 합니다. 프로그램 결과가 변경되면 릴리스 버전의 프로그램에만 나타나는 버그가 발생할 수 있습니다. 특히 다음 예와 같이 함수 또는 프로시저 호출이 포함된 Assert를 사용할 경우에 주의해야 합니다.

```VB
' unsafe code
Debug.Assert (meas(i) <> 0 )
```

```csharp
// unsafe code
Debug.Assert (meas(i) != 0 );
```

 이러한 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>의 사용이 안전해 보일 수도 있지만 meas 함수가 호출될 때마다 카운터를 업데이트한다고 가정해 보십시오. 릴리스 버전을 빌드할 때 이 meas에 대한 호출이 제거되므로 카운터는 업데이트되지 않습니다. 이는 파생 작업이 있는 함수의 예입니다. 파생 작업이 있는 함수에 대한 호출을 제거하면 릴리스 버전에서만 나타나는 버그가 발생할 수 있습니다. 이러한 문제를 방지하려면 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 문에 함수 호출을 배치하는 대신 다음과 같이 임시 변수를 사용합니다.

```VB
temp = meas( i )
Debug.Assert (temp <> 0)
```

```csharp
temp = meas( i );
Debug.Assert ( temp != 0 );
```

 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>를 사용하는 경우에도 `Assert` 문 내에 함수 호출을 배치하지 않으려고 할 수 있습니다. <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 문은 릴리스 빌드에서 제거되지 않기 때문에 이러한 호출이 위험하지는 않습니다. 그러나 습관적으로 이러한 구문을 사용하지 않는 경우 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>를 사용할 때 실수를 줄일 수 있습니다.

 [항목 내용](#BKMK_In_this_topic)

## <a name="trace-and-debug-requirements"></a><a name="BKMK_Trace_and_Debug_Requirements">Trace 및 Debug 요구 사항</a>
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 마법사를 사용하여 프로젝트를 만드는 경우 릴리스 구성과 디버그 구성 모두에서 기본적으로 TRACE 기호가 정의됩니다. 디버그 기호는 기본적으로 디버그 빌드에서만 정의됩니다.

 그 밖의 경우에 <xref:System.Diagnostics.Trace> 메서드가 작동하려면 프로그램의 소스 파일 맨 위에 다음 중 하나가 있어야 합니다.

- Visual Basic에서는 `#Const TRACE = True`

- Visual C# 및 C++에서는 `#define TRACE`

  또는 다음과 같은 TRACE 옵션을 사용하여 프로그램을 빌드해야 합니다.

- Visual Basic에서는 `/d:TRACE=True`

- Visual C# 및 C++에서는 `/d:TRACE`

  C# 또는 Visual Basic 릴리스 빌드에서 Debug 메서드를 사용해야 하는 경우 릴리스 구성에서 디버그 기호를 정의해야 합니다.

  C++는 <xref:System.Diagnostics.Debug> 클래스 메서드를 지원하지 않습니다. 조건부 컴파일(예: `#ifdef DEBUG`... `#endif`)에 <xref:System.Diagnostics.Trace> 클래스를 사용하면 동일한 결과를 얻을 수 있습니다. 이러한 기호는 **\<Project> 속성 페이지** 대화 상자에서 정의할 수 있습니다. 자세한 내용은 [Visual Basic 디버그 구성에 대한 프로젝트 설정 변경](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) 또는 [C 또는 C++ 디버그 구성에 대한 프로젝트 설정 변경](../debugger/project-settings-for-a-cpp-debug-configuration.md)을 참조하세요.

## <a name="assert-arguments"></a><a name="BKMK_Assert_arguments"></a> 어설션 인수
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 및 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>에는 세 가지 인수가 사용됩니다. 첫 번째 인수는 확인할 조건으로, 필수 인수입니다. 인수를 하나만 지정하여 <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> 또는 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName>를 호출하는 경우 `Assert` 메서드는 조건을 확인하여 결과가 false인 경우에 호출 스택의 내용을 **출력** 창에 출력합니다. 다음 예제에서는 <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> 및 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName>를 보여 줍니다.

```VB
Debug.Assert(stacksize > 0)
Trace.Assert(stacksize > 0)
```

```csharp
Debug.Assert ( stacksize > 0 );
Trace.Assert ( stacksize > 0 );
```

 두 번째 및 세 번째 인수는 선택적으로 지정되는 문자열입니다. 인수를 두 개나 세 개 사용하여 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 또는 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>를 호출하는 경우 첫 번째 인수는 조건입니다. 메서드는 조건을 확인하고 그 결과가 false인 경우 두 번째 문자열과 세 번째 문자열을 출력합니다. 다음 예제에서는 인수 두 개를 사용하는 <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> 및 <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName>를 보여 줍니다.

```VB
Debug.Assert(stacksize > 0, "Out of stack space")
Trace.Assert(stacksize > 0, "Out of stack space")
```

```csharp
Debug.Assert ( stacksize > 0, "Out of stack space" );
Trace.Assert ( stacksize > 0, "Out of stack space" );
```

 다음 예제에서는 <xref:System.Diagnostics.Debug.Assert%2A> 및 <xref:System.Diagnostics.Trace.Assert%2A>를 보여 줍니다.

```VB
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )
```

```csharp
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );
```

 [항목 내용](#BKMK_In_this_topic)

## <a name="customizing-assert-behavior"></a><a name="BKMK_Customizing_Assert_behavior"></a> 어설션 동작 사용자 지정
 사용자 인터페이스 모드로 애플리케이션을 실행하는 경우 조건이 실패하면 `Assert` 메서드에서 **어설션 실패** 대화 상자를 표시합니다. 어설션이 실패할 경우에 발생하는 동작은 <xref:System.Diagnostics.Debug.Listeners%2A> 또는 <xref:System.Diagnostics.Trace.Listeners%2A> 속성으로 제어됩니다.

 <xref:System.Diagnostics.TraceListener> 개체를 `Listeners` 컬렉션에 추가하거나, <xref:System.Diagnostics.TraceListener>를 `Listeners` 컬렉션에서 제거하거나, 기존 <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName>의 `TraceListener` 메서드를 다르게 동작하도록 재정의하는 방법으로 출력 동작을 사용자 지정할 수 있습니다.

 예를 들어 **어설션 실패** 대화 상자를 표시하는 대신 이벤트 로그에 쓰도록 <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> 메서드를 재정의할 수 있습니다.

 이러한 방법으로 출력을 사용자 지정하려면 프로그램에 수신기가 있어야 하고 사용자가 <xref:System.Diagnostics.TraceListener>에서 상속하여 <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> 메서드를 재정의해야 합니다.

 자세한 내용은 [추적 수신기](/dotnet/framework/debug-trace-profile/trace-listeners)를 참조하세요.

 [항목 내용](#BKMK_In_this_topic)

## <a name="setting-assertions-in-configuration-files"></a><a name="BKMK_Setting_assertions_in_configuration_files"></a> 구성 파일에서 어설션 설정
 코드뿐만 아니라 프로그램 구성 파일에서도 어설션을 설정할 수 있습니다. 자세한 내용은 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 또는 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>를 참조하세요.

## <a name="see-also"></a>참조

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>
- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>
- [디버거 보안](../debugger/debugger-security.md)
- [애플리케이션 추적 및 조율](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [방법: 추적 및 디버그를 사용한 조건부 컴파일](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)
- [C#, F#, and Visual Basic Project Types](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)(C#, F# 및 Visual Basic 프로젝트 형식)
- [관리 코드 디버그](../debugger/debugging-managed-code.md)