---
title: '7단계: 곱하기 및 나누기 문제 추가'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a1744b68ad043dcee21dcb5995fbd1908bd81b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579783"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>7단계: 곱하기 및 나누기 문제 추가

이 자습서의 7단계에서는 곱하기와 나누기 문제를 추가합니다. 하지만 먼저 이렇게 변경하는 방법을 살펴보겠습니다. 값을 저장하는 첫 단계를 알아야 합니다.

> [!NOTE]
> 이 항목은 기본 코딩 개념에 대해 설명하는 자습서 시리즈의 일부입니다. 자습서에 대한 개요는 [자습서 2: 시간이 지정된 수학 퀴즈 만들기](../ide/tutorial-2-create-a-timed-math-quiz.md)를 참조하세요.

## <a name="to-add-multiplication-and-division-problems"></a>곱하기 및 나누기 문제를 추가하려면

1. 정수 변수를 네 개 더 폼에 추가합니다.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. 이전과 마찬가지로 `StartTheQuiz()` 메서드를 수정하여 곱하기 및 나누기 문제를 난수로 채웁니다.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. 곱하기 및 나누기 문제에 대해서도 확인하도록 `CheckTheAnswer()` 메서드를 수정합니다.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     키보드를 사용하여 곱하기 기호(×)와 나누기 기호(÷)를 입력하기가 쉽지 않으므로 C# 및 Visual Basic에서는 별표(*)를 곱하기에, 슬래시(/)를 나누기에 각각 사용합니다.

4. 시간이 다 되면 자동으로 올바른 답을 채우도록 타이머의 <xref:System.Windows.Forms.Timer.Tick> 이벤트 처리기 마지막 부분을 변경합니다.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. 프로그램을 저장하고 실행합니다.

     다음 그림과 같이 퀴즈를 푸는 사람은 네 가지 문제에 대한 답을 입력하여 퀴즈를 완료해야 합니다.

     ![네 개의 문제가 있는 수학 퀴즈](../ide/media/express_finishedquiz.png)<br/>
*네 개의 문제가 있는* ***수학 퀴즈***

## <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동하려면 **[8단계: 퀴즈 사용자 지정](../ide/step-8-customize-the-quiz.md)** 을 참조하세요.

- 이전 자습서 단계로 돌아가려면 [6단계: 빼기 문제 추가](../ide/step-6-add-a-subtraction-problem.md)를 참조하세요.
