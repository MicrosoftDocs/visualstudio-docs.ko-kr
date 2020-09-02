---
title: '7단계: 곱하기 및 나누기 문제 추가 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7f7efb0acf6611346abe67a7a94e5c221919665
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646968"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>7단계: 곱하기 및 나누기 문제 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 자습서의 7단계에서는 곱하기와 나누기 문제를 추가합니다. 하지만 먼저 이렇게 변경하는 방법을 살펴보겠습니다. 값을 저장하는 첫 단계를 알아야 합니다.

### <a name="to-add-multiplication-and-division-problems"></a>곱하기 및 나누기 문제를 추가하려면

1. 정수 변수를 네 개 더 폼에 추가합니다.

     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]

2. 이전과 마찬가지로 `StartTheQuiz()` 메서드를 수정하여 곱하기 및 나누기 문제를 난수로 채웁니다.

     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]

3. 곱하기 및 나누기 문제에 대해서도 확인하도록 `CheckTheAnswer()` 메서드를 수정합니다.

     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]

     키보드를 사용하여 곱하기 기호(×)와 나누기 기호(÷)를 입력하기가 쉽지 않으므로 Visual C# 및 Visual Basic에서는 별표(*)를 곱하기에, 슬래시(/)를 나누기에 각각 사용합니다.

4. 시간이 다 되면 자동으로 올바른 답을 채우도록 타이머의 Tick 이벤트 처리기 마지막 부분을 변경합니다.

     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]

5. 프로그램을 저장하고 실행합니다.

     다음 그림과 같이 퀴즈를 푸는 사람은 네 가지 문제에 대한 답을 입력하여 퀴즈를 완료해야 합니다.

     ![네 가지 문제가 있는 수학 퀴즈](../ide/media/express-finishedquiz.png "Express_FinishedQuiz") 네 가지 문제가 있는 수학 퀴즈

### <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동 하려면 [8 단계: 퀴즈 사용자 지정](../ide/step-8-customize-the-quiz.md)을 참조 하세요.

- 이전 자습서 단계로 돌아가려면 [6 단계: 빼기 문제 추가](../ide/step-6-add-a-subtraction-problem.md)를 참조 하세요.
