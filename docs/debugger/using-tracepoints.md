---
title: 추적점을 사용하여 정보 기록 | Microsoft Docs
ms.date: 10/28/2019
ms.topic: conceptual
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: fcc9f01315d3783af1a1f124785cd74fafb215bf
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187305"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>Visual Studio에서 추적점을 사용하여 출력 창에 정보 기록

추적점을 사용하면 코드를 수정하거나 중지하지 않고 구성 가능한 조건에서 출력 창에 정보를 기록할 수 있습니다. 이 기능은 관리되는 언어(C#, Visual Basic, F#) 및 네이티브 코드 뿐 아니라 JavaScript 및 Python과 같은 언어에 대해서도 지원됩니다.

## <a name="let39s-take-an-example"></a>예를 들어 보겠습니다.

다음 예제 프로그램은 루프에서 다른 반복을 실행할 때마다 1씩 늘리는 카운터 변수를 사용하는 간단한 `for` 루프입니다.

![카운터 예제](../debugger/media/counterexample.png "카운터 예제")

## <a name="set-tracepoints-in-source-code"></a>소스 코드에서 추적점 설정

**중단점 설정** 창의 **작업** 확인란 아래에 출력 문자열을 지정하여 추적점을 설정할 수 있습니다.

1. 추적점을 초기화하려면 먼저 추적점을 설정하려는 줄 번호의 왼쪽 여백을 클릭합니다.

   ![중단점 초기화](../debugger/media/breakpointinitialization.png "중단점 초기화")

2. 빨간색 원을 마우스로 가리킨 다음 기어 아이콘을 클릭합니다.
3. **중단점 설정** 창이 열립니다.

   ![중단점 창](../debugger/media/breakpointwindow.png "중단점 창")

4. **작업** 확인란을 선택합니다.

   ![선택된 작업 상자](../debugger/media/checkedactionsbox.png "선택된 작업 상자")

   빨간색 원이 다이아몬드로 변경되어 중단점에서 추적점으로 전환되었음을 알 수 있습니다.

5. **출력 창에 메시지 표시** 텍스트 상자에 로그인할 메시지를 입력합니다(자세한 내용은 이 문서의 뒷부분에 나오는 섹션 참조).

   이제 추적점이 설정됩니다. 출력 창에 정보를 기록하는 것으로 작업이 완료된 경우 &quot;닫기&quot; 단추를 누릅니다.

6. 메시지가 표시되는지 여부를 결정하는 조건을 추가하려면 **조건** 확인란을 선택합니다.

   ![선택된 조건 상자](../debugger/media/checkedconditionsbox.png "선택된 조건 상자")

   조건에 대한 세 가지 선택 사항이 있습니다. **조건 식**, **필터** 및 **적중 횟수**입니다.

## <a name="actions-menu"></a>작업 메뉴

이 메뉴를 사용하여 출력 창에 메시지를 기록할 수 있습니다. 메시지 상자에 출력하려는 문자열을 입력합니다(따옴표 필요 없음). 변수의 값을 표시 하려면 중괄호 안에 포함해야 합니다.

예를 들어 출력 콘솔에서 `counter` 변수의 값을 표시하려면 메시지 텍스트 상자에 {counter}를 입력합니다.

![카운터 출력 메시지](../debugger/media/counteroutputmessage.png "카운터 출력 메시지")

**닫기**를 클릭한 다음 프로그램을 디버그하면(**F5**), 출력 창에 다음 출력이 표시됩니다.

![출력 창의 작업 메시지](../debugger/media/actionsmessageinoutputwindow.png "출력 창의 작업 메시지")

특수 키워드를 사용하여 보다 구체적인 정보를 표시할 수도 있습니다. 아래 표시된 대로 키워드를 정확하게 입력합니다. 각 키워드 앞에 "$"를 사용하고 키워드 자체에 대해 모든 대문자를 사용합니다.

| 키워드 | 표시되는 내용 |
| --- | --- |
| $ADDRESS | 현재 명령 |
| $CALLER | 호출 함수 이름 |
| $CALLSTACK | 호출 스택 |
| $FUNCTION | 현재 함수 이름 |
| $PID | 프로세스 ID |
| $PNAME | 프로세스 이름 |
| $TID | 스레드 ID |
| $TNAME   | 스레드 이름 |
| $TICK | 틱 수(Windows GetTickCount) |

## <a name="conditions-menu"></a>조건 메뉴

조건을 사용하여 출력 메시지를 필터링할 수 있으므로 특정 시나리오에만 표시됩니다. 사용할 수 있는 세 가지 종류의 조건이 있습니다.

### <a name="conditional-expression"></a>조건 식
조건 식의 경우 출력 메시지는 특정 조건이 충족될 때만 표시됩니다.

조건 식의 경우 특정 조건이 true이거나 변경된 경우에 메시지를 출력하도록 추적점을 설정할 수 있습니다. 예를 들어 `for` 루프의 짝수 반복을 수행하는 동안 카운터 값만 표시하려는 경우 **Is true** 옵션을 선택한 다음 메시지 텍스트 상자에 `i%2 == 0`를 입력합니다.

![조건 식이 True임](../debugger/media/conditionalexpressionistrue.png "조건 식이 True임")

`for` 루프의 반복이 변경될 때 카운터 값을 인쇄하려면 **변경 시** 옵션을 선택하고 메시지 텍스트 상자에 `i`를 입력합니다.

![변경 시 조건 식](../debugger/media/conditionalexpressionwhenchanged.png "변경 시 조건 식")

**변경 시** 옵션의 동작은 프로그래밍 언어마다 다릅니다.

- 네이티브 코드의 경우 디버거는 조건의 첫 번째 계산을 변경으로 간주하지 않으므로 첫 번째 계산에서는 추적점이 적중되지 않습니다.
- 관리 코드의 경우 **변경 시**를 선택하면 디버거가 첫 번째 계산에서 추적점에 도달합니다.

조건을 설정하는 동안 사용할 수 있는 유효한 식에 대한 자세한 내용은 [디버거에서 식](expressions-in-the-debugger.md)을 참조하세요.

### <a name="hit-count"></a>적중 횟수
적중 횟수 조건을 통해 추적점이 설정된 코드 줄이 지정된 횟수 만큼 실행된 후에만 출력을 보낼 수 있습니다.

적중 횟수의 경우 추적점이 설정된 코드 줄이 지정된 적중 횟수 값과 같거나, 지정된 적중 횟수 값의 배수이거나, 지정된 적중 횟수 값 보다 크거나 같은 경우 메시지를 출력하도록 선택할 수 있습니다. 요구 사항에 가장 적합한 옵션을 선택하고 해당 반복을 나타내는 정수 값을 필드에 입력합니다(예: 5).

![조건 식 적중 횟수](../debugger/media/conditionalexpressionhitcount.png "조건 식 적중 횟수")

### <a name="filter"></a>필터
필터 조건에 대해 표시되는 디바이스, 프로세스 또는 스레드 출력을 지정합니다.

![조건 식 필터](../debugger/media/conditionalexpressionfilter.png "조건 식 필터")

필터 식 목록:

- MachineName = "이름"
- ProcessId = 값
- ProcessName = "이름"
- ThreadId = 값
- ThreadName = "이름"

문자열(예: 이름)을 큰따옴표로 묶습니다. 따옴표 없이 값을 입력할 수 있습니다. `&`(`AND`), `||` (`OR`0), `!` (`NOT`) 및 괄호를 사용하여 절을 결합할 수 있습니다.

## <a name="considerations"></a>고려 사항

추적점은 더 깔끔하고 부드러운 환경을 디버그하기 위한 것이지만, 사용할 때 알아야 할 몇 가지 고려 사항이 있습니다.

경우에 따라 개체의 속성이나 특성을 검사하면 해당 값이 변경될 수 있습니다. 검사 중에 값이 변경되면 추적점 기능 자체에 의해 발생하는 버그가 아닙니다. 그러나 추적점을 사용하여 개체를 검사해도 이러한 실수로 수정되는 것은 방지되지 않습니다.

**작업** 메시지 상자에서 식이 계산되는 방식은 현재 개발에 사용하고 있는 언어와 다를 수 있습니다. 예를 들어 문자열을 출력하기 위해 일반적으로 `Debug.WriteLine()` 또는 `console.log()`를 사용하는 경우에도 따옴표로 메시지를 묶을 필요가 없습니다. 또한 식 출력에 대한 중괄호 구문(`{ }`)은 개발 언어에서 값을 출력하는 규칙과 다를 수 있습니다. 그러나 중괄호(`{ }`) 내의 콘텐츠는 개발 언어의 구문을 사용하여 계속 작성해야 합니다.

라이브 애플리케이션을 디버그하고 유사한 기능을 찾으려면 스냅샷 디버거의 logpoint 기능을 확인하세요. 스냅샷 디버거는 프로덕션 애플리케이션의 문제를 조사하는 데 사용되는 도구입니다. Logpoint를 사용하면 소스 코드를 수정하지 않고도 출력 창에 메시지를 보낼 수 있으며 실행 중인 애플리케이션에 영향을 주지 않습니다. 자세한 내용은 [라이브 Azure 애플리케이션 디버그](../debugger/debug-live-azure-applications.md)를 참조하세요.

## <a name="see-also"></a>참조

- [디버깅이란?](../debugger/what-is-debugging.md)
- [Visual Studio를 사용하여 더 나은 C# 코드 작성](../debugger/write-better-code-with-visual-studio.md)
- [먼저 디버깅 살펴보기](../debugger/debugger-feature-tour.md)
- [디버거의 식](expressions-in-the-debugger.md)
- [중단점 사용](../debugger/using-breakpoints.md)
- [라이브 Azure 애플리케이션 디버그](../debugger/debug-live-azure-applications.md)
