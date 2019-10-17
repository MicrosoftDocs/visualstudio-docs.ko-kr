---
title: 'CA2007: 작업을 직접 대기하지 마세요.'
ms.date: 03/08/2019
ms.topic: reference
f1_keywords:
- CA2007
- DoNotDirectlyAwaitATaskAnalyzer
helpviewer_keywords:
- CA2007
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: cf07c997f933e6aacf3eff29ae204ecd0bedb036
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233069"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: 작업을 직접 대기하지 마세요.

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|범주|Microsoft.Reliability|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

비동기 메서드는 <xref:System.Threading.Tasks.Task>를 직접 [기다립니다.](/dotnet/csharp/language-reference/keywords/await)

## <a name="rule-description"></a>규칙 설명

비동기 메서드가 <xref:System.Threading.Tasks.Task> 직접 기다립니다 작업을 만든 스레드와 동일한 스레드에서 연속 작업을 수행 합니다. 이 동작은 성능 측면에서 비용이 많이 들 수 있으며 UI 스레드에 교착 상태가 발생할 수 있습니다. 을 호출 <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> 하 여 연속 작업을 위한 신호를 보내는 것이 좋습니다.

이 규칙은 [fxcop 분석기](install-fxcop-analyzers.md) 에서 도입 되었으며 레거시 fxcop 분석에는 존재 하지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

위반 문제를 해결 하려면 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> 대기 <xref:System.Threading.Tasks.Task>에서를 호출 합니다. 매개 변수에 대해 `true` 또는 `false` 를 전달할 수 있습니다. `continueOnCapturedContext`

- 작업 `ConfigureAwait(true)` 에 대해를 호출 하는 것은 명시적으로를 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>호출 하지 않는 동작과 동일 합니다. 이 메서드를 명시적으로 호출 하 여 판독기에서 의도적으로 원래 동기화 컨텍스트에서 연속 작업을 수행 하려고 한다는 것을 알 수 있습니다.

- 작업 `ConfigureAwait(false)` 에 대해를 호출 하 여 스레드 풀에 연속 작업을 예약 하 여 UI 스레드에서 교착 상태를 방지 합니다. 전달은 `false` 앱 독립적인 라이브러리에 대해 좋은 옵션입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

소비자가 GUI (그래픽 사용자 인터페이스) 앱이 아니거나 소비자 <xref:System.Threading.SynchronizationContext>에가 없는 경우이 경고를 표시 하지 않을 수 있습니다.

## <a name="example"></a>예제

다음 코드 조각에서는 경고를 생성 합니다.

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

위반 문제를 해결 하려면 대기 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> <xref:System.Threading.Tasks.Task>에서를 호출 합니다.

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="configurability"></a>구성이

이 규칙에서 값을 반환 하지 않는 비동기 메서드를 제외할지 여부를 구성할 수 있습니다. 이러한 종류의 메서드를 제외 하려면 프로젝트의 editorconfig 파일에 다음 키-값 쌍을 추가 합니다.

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

이 규칙을 적용할 출력 어셈블리 종류를 구성할 수도 있습니다. 예를 들어 콘솔 응용 프로그램 또는 동적으로 연결 된 라이브러리 (즉, UI 앱이 아님)를 생성 하는 코드에만이 규칙을 적용 하려면 프로젝트의 editorconfig 파일에 다음 키-값 쌍을 추가 합니다.

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

자세한 내용은 [FxCop 분석기 구성](configure-fxcop-analyzers.md)을 참조 하세요.

## <a name="see-also"></a>참고자료

- [System.threading.tasks.task.configureawait (false)로 작업을 대기 해야 하나요?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Visual Studio에서 FxCop 분석기 설치](install-fxcop-analyzers.md)