---
title: 기록 디버깅을 사용하여 앱 검사 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efabc8cd185daed4f018e3e4209e391b5bc39f44
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350448"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio-c-visual-basic-c"></a>Visual Studio에서 IntelliTrace 기록 디버깅을 사용하여 앱 검사(C#, Visual Basic, C++)

[기록 디버깅](../debugger/historical-debugging.md)을 사용하여 애플리케이션 실행 도중 앞이나 뒤로 이동하며 상태를 검사할 수 있습니다.

Visual Studio Enterprise 버전(Professional 또는 Community 버전 아님)에서 IntelliTrace를 사용할 수 있습니다.

## <a name="navigate-your-code-with-historical-debugging"></a>기록 디버깅을 사용하여 코드 탐색

버그가 있는 간단한 프로그램부터 살펴보겠습니다. C# 콘솔 애플리케이션에서 다음 코드를 추가합니다.

```csharp
static void Main(string[] args)
{
    int testInt = 0;
    int resultInt = AddAll(testInt);
    Console.WriteLine(resultInt);
}
private static int AddAll(int j)
{
    for (int i = 0; i < 20; i++)
    {
        j = AddInt(j);
    }
    return j;
}

private static int AddInt(int add)
{
    if (add == 10)
    {
        return add += 25;
    }
    return ++add;
}
```

`AddAll()`을 호출한 후 `resultInt`의 예상 값을 20으로 가정하겠습니다(`testInt`를 20배 증분한 결과). (또한 `AddInt()`에서 버그를 볼 수 없다고 가정하겠습니다.) 그러나 결과는 실제로 44입니다. `AddAll()`을 단계적으로 10회 실행하지 않고도 버그를 찾으려면 어떻게 할까요? 기록 디버깅을 사용하여 더 빠르고 쉽게 버그를 찾을 수 있습니다. 방법은 다음과 같습니다.

1. **도구 > 옵션 > IntelliTrace > 일반**에서 IntelliTrace가 사용하도록 설정되어 있는지 확인하고 **IntelliTrace 이벤트 및 호출 정보**를 선택합니다. 이 옵션을 선택하지 않으면 탐색 여백(아래 설명)을 볼 수 없습니다.

2. `Console.WriteLine(resultInt);` 줄에 중단점을 설정합니다.

3. 디버깅을 시작합니다. 코드가 중단점까지 실행됩니다. **로컬** 창에서 `resultInt`의 값이 44임을 확인할 수 있습니다.

4. **진단 도구** 창을 엽니다(**디버그 / 진단 도구 표시**). 코드 창이 다음과 같이 나타납니다.

    ![중단점의 코드 창](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")

5. 중단점 바로 위 왼쪽 여백 옆에 이중 화살표가 표시됩니다. 이 영역은 탐색 여백이라고 하며 기록 디버깅에 사용됩니다. 화살표를 클릭합니다.

    코드 창에서 위 코드 줄(`int resultInt = AddIterative(testInt);`)에 분홍색이 지정된 것을 확인할 수 있습니다. 창 위에는 현재 기록 디버깅 중임을 알리는 메시지가 표시됩니다.

    이제 코드 창의 모양은 다음과 같습니다.

    ![기록 디버깅 모드의 코드 창](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")

6. 이제 `AddAll()` 메서드를 단계별로 실행할 수 있습니다(**F11** 키 또는 탐색 여백의 **한 단계씩 코드 실행** 단추). 앞으로 이동합니다(**F10** 키 또는 탐색 여백의 **다음 호출로 이동**). 분홍색 줄이 `j = AddInt(j);` 줄에 표시됩니다. 이 경우에는 **F10** 키를 사용해도 다음 코드 줄로 진행되지 않습니다. 대신, 다음 함수 호출로 이동합니다. 기록 디버깅은 여러 호출을 탐색하며 함수 호출이 포함되지 않은 코드 줄을 건너뜁니다.

7. 이제 `AddInt()` 메서드를 한 단계씩 실행합니다. 이 코드의 버그가 즉시 표시됩니다.

## <a name="next-steps"></a>다음 단계

이 절차에서는 기록 디버깅으로 수행할 수 있는 작업의 기본적인 것만 살펴봤습니다.

- 디버깅 중에 스냅샷을 보려면 [IntelliTrace를 사용하여 이전 앱 상태 검사](../debugger/view-historical-application-state.md)를 참조하세요.
- 다양한 설정 및 탐색 여백에 있는 여러 단추의 효과에 대해 자세히 알아보려면 [IntelliTrace 기능](../debugger/intellitrace-features.md)을 참조하세요.
