---
title: '10단계: 추가 단추 및 확인란에 대한 코드 작성'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0dc7281b51d0efe0d19020df6a154e332ad9bb0
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579429"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>10단계: 추가 단추 및 확인란에 대한 코드 작성

이제 다른 네 메서드를 완료할 준비가 되었습니다. 지금 이 코드를 복사하여 붙여넣을 수도 있지만 이 자습서의 내용을 최대한 학습하려면 이 코드를 입력하고 IntelliSense를 사용합니다.

이 코드는 앞서 추가한 단추에 기능을 추가합니다. 이 코드가 없으면 단추로 어떤 작업도 수행되지 않습니다. 단추에서는 <xref:System.Windows.Forms.Control.Click> 이벤트의 코드를 사용하고 확인란에서는 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 이벤트를 사용하여 컨트롤을 활성화했을 때 서로 다른 작업을 수행합니다. 예를 들어 **그림 지우기** 단추를 선택하면 활성화되는 `clearButton_Click`(또는 `ClearButton_Click`) 이벤트는 해당 **이미지** 속성을 **null**(또는 **nothing**)으로 설정하여 현재 이미지를 지웁니다. 코드의 각 이벤트에는 코드의 기능에 대해 설명하는 주석이 포함되어 있습니다.

> [!TIP]
> 모범 사례: 항상 코드를 주석으로 처리합니다. 주석은 코드를 읽는 사용자의 이해를 돕기 위한 것으로, 앱에서는 주석 줄에 있는 모든 내용을 무시합니다. C#에서는 두 개의 슬래시(//)로 주석 줄을 시작하고, Visual Basic에서는 작은따옴표(‘)로 주석 줄을 시작합니다.

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>추가 단추 및 확인란에 대한 코드를 작성하는 방법

다음 코드를 **Form1** 코드 파일(*Form1.cs* 또는 *Form1.vb*)에 추가합니다.

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> 코드에 “camelCase” 문자가 표시되지 않을 수 있습니다.

## <a name="next-steps"></a>다음 단계

* 다음 자습서 단계로 이동하려면 **[11단계: 앱 실행 및 기타 ](../ide/step-11-run-your-program-and-try-other-features.md)** 을 참조하세요.

* 이전 자습서 단계로 돌아가려면 [9단계: 코드 검토, 주석 처리 및 테스트](../ide/step-9-review-comment-and-test-your-code.md)를 참조하세요.

## <a name="see-also"></a>참조

* [자습서 2: 시간이 지정된 수학 퀴즈 만들기](tutorial-2-create-a-timed-math-quiz.md)
* [자습서 3: 맞추기 게임 만들기](tutorial-3-create-a-matching-game.md)
