---
title: '3단계: 카운트다운 타이머 추가 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bae5b4a81864cc591491c21218a5d8253dfc61bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671842"
---
# <a name="step-3-add-a-countdown-timer"></a>3단계: 카운트다운 타이머 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 자습서의 3단계에서는 퀴즈를 푸는 사람이 퀴즈를 마칠 때까지 남은 시간(초)을 추적하도록 카운트다운 타이머를 추가합니다.

> [!NOTE]
> 이 항목은 기본 코딩 개념에 대해 설명하는 자습서 시리즈의 일부입니다. 자습서에 대 한 개요는 [자습서 2: 시간이 지정 된 수학 퀴즈 만들기](../ide/tutorial-2-create-a-timed-math-quiz.md)를 참조 하세요.

### <a name="to-add-a-countdown-timer"></a>카운트다운 타이머를 추가하려면

1. 이전 절차에서와 같이 **timeLeft**라는 정수 변수를 추가합니다. 이 코드는 다음과 같습니다.

     [!code-csharp[VbExpressTutorial3Step3#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial3Step3#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#5)]

     이제 타이머와 같이 실제로 초를 세는 메서드가 있어야 합니다. 이 메서드는 지정된 시간이 지나면 이벤트를 발생시킵니다.

2. 디자인 창에서 도구 상자의 **구성 요소** 범주에 있는 `Timer` 컨트롤을 폼으로 이동합니다.

     그러면 디자인 창의 맨 아래에 있는 회색 영역에 이 컨트롤이 표시됩니다.

3. 폼에서 방금 추가한 **timer1** 아이콘을 선택하고 **Interval** 속성을 **1000**으로 설정합니다.

     간격 값은 밀리초 단위이므로 값으로 1000을 지정하면 Tick 이벤트가 1초 간격으로 발생합니다.

4. 폼에서 Timer 컨트롤을 두 번 클릭하거나, 이 컨트롤을 선택한 다음 Enter 키를 선택합니다.

     코드 편집기가 나타나고 방금 추가한 Tick 이벤트 처리기에 대한 메서드가 표시됩니다.

5. 새 이벤트 처리기 메서드에 다음 문을 추가합니다.

     [!code-csharp[VbExpressTutorial3Step3#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial3Step3#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#6)]

     추가한 문을 기반으로 타이머는 1초 간격으로 **timeLeft** 정수 변수가 0보다 큰지 확인하여 시간이 다 되었는지 여부를 확인합니다. 이 값이 0보다 크면 시간이 남은 것입니다. 타이머는 먼저 timeLeft에서 1을 뺀 다음 퀴즈를 푸는 사람에게 남은 시간(초)을 표시하도록 `timeLabel` 컨트롤의 **Text** 속성을 업데이트합니다.

     남은 시간이 없으면 타이머가 중지되고 `timeLabel` 컨트롤의 텍스트가 **Time's up!** 으로 변경되어 표시됩니다. 퀴즈가 끝났다는 메시지 상자가 나타나고 답(이 경우, addend1과 addend2를 더한 값)이 표시됩니다. 퀴즈를 푸는 사람이 다른 퀴즈를 시작할 수 있도록 `startButton` 컨트롤의 **Enabled** 속성이 `true`로 설정됩니다.

     이제 프로그램에서 결정을 내리도록 지시하는 방법인 `if else` 문을 추가했습니다. `if else` 문은 다음과 같습니다.

    > [!NOTE]
    > 다음 예제는 이해를 돕기 위한 것일 뿐입니다. 프로젝트에 추가하지 마십시오.

    ```vb
    If (something that your program will check) Then
        ' One or more statements that will run
        ' if what the program checked is true.
    Else
        ' One or more statements that will run
        ' if what the program checked is false.
    End If
    ```

    ```csharp
    if (something that your program will check)
    {
        // One or more statements that will run
        // if what the program checked is true.
    }
    else
    {
        // One or more statements that will run
        // if what the program checked is false.
    }
    ```

     더하기 문제의 답을 표시하기 위해 `else` 블록에 추가한 문을 자세히 살펴봅니다.

     [!code-csharp[VbExpressTutorial3Step3#24](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#24)]
     [!code-vb[VbExpressTutorial3Step3#24](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#24)]

     `addend1 + addend2` 문은 두 변수의 값을 서로 더합니다. 첫 번째 부분(`sum.Value`)은 sum `NumericUpDown` 컨트롤의 **Value** 속성을 사용하여 올바른 답을 표시합니다. 이 속성은 나중에 퀴즈의 답을 확인할 때도 사용됩니다.

     퀴즈를 푸는 사람은 `NumericUpDown` 컨트롤을 사용하여 숫자를 더 쉽게 입력할 수 있습니다. 수학 문제의 답을 입력하는 데 이 컨트롤이 사용되는 이유입니다. 가능한 모든 답은 0에서 100 사이의 정수이므로 **Minimum**, **Maximum** 및 **DecimalPlaces** 속성의 값을 기본값으로 유지하면 퀴즈를 푸는 사람이 소수, 음수 또는 100을 초과하는 숫자를 입력할 수 없습니다. 퀴즈를 푸는 사람이 3.141은 입력할 수 있고 3.1415는 입력할 수 없도록 하려면 **DecimalPlaces** 속성을 3으로 설정하면 됩니다.

6. 다음과 같이 `StartTheQuiz()` 메서드에 세 개의 줄을 추가합니다.

     [!code-csharp[VbExpressTutorial3Step3#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial3Step3#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#7)]

     이제 퀴즈를 시작하면 **timeLeft** 변수가 30으로 설정되고 `timeLabel` 컨트롤의 **Text** 속성이 30초로 설정됩니다. 그런 다음 `Timer` 컨트롤의 `Start()` 메서드가 카운트다운을 시작합니다. 이때 답을 확인하지는 않습니다. 답 확인은 나중에 수행됩니다.

7. 프로그램을 저장하고 실행한 후 폼에서 **시작** 단추를 선택합니다.

     타이머가 카운트다운을 시작합니다. 시간이 다 되면 퀴즈가 종료되고 답이 표시됩니다. 다음 그림에서는 진행 중인 퀴즈를 보여 줍니다.

     ![진행 중인 수학 퀴즈](../ide/media/express-addcountdown.png "Express_AddCountdown") 진행 중인 수학 퀴즈

### <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동하려면 [4단계: CheckTheAnswer() 메서드 추가](../ide/step-4-add-the-checktheanswer-parens-method.md)를 참조하세요.

- 이전 자습서 단계로 돌아가려면 [2단계: 난수 더하기 문제 만들기](../ide/step-2-create-a-random-addition-problem.md)를 참조하세요.
