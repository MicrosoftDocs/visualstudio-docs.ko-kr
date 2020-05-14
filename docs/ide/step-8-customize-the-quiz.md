---
title: '8단계: 퀴즈 사용자 지정'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e568a9fa844802ddab934264cbc316d3514fe577
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579373"
---
# <a name="step-8-customize-the-quiz"></a>8단계: 퀴즈 사용자 지정

자습서의 마지막 부분에서는 퀴즈를 사용자 지정하고 이미 배운 내용을 확장하는 몇 가지 방법을 살펴보겠습니다. 예를 들어 프로그램에서 답이 분수가 아닌 난수 나누기 문제를 만드는 방법을 생각해 보세요. 자세히 알아보려면 `timeLabel` 컨트롤을 다른 색으로 바꾸고 퀴즈를 푸는 사람에게 힌트를 제공합니다.

> [!NOTE]
> 이 항목은 기본 코딩 개념에 대해 설명하는 자습서 시리즈의 일부입니다. 자습서에 대한 개요는 [자습서 2: 시간이 지정된 수학 퀴즈 만들기](../ide/tutorial-2-create-a-timed-math-quiz.md)를 참조하세요.

## <a name="to-customize-the-quiz"></a>퀴즈를 사용자 지정하려면

- 퀴즈에서 남은 시간이 5초뿐이라면 **BackColor** 속성을 설정하여 **timeLabel** 컨트롤을 빨간색으로 바꿉니다.

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  퀴즈가 끝나면 색을 초기화합니다.

- <xref:System.Windows.Forms.NumericUpDown> 컨트롤에 정답이 입력되면 소리를 재생하여 퀴즈를 푸는 사람에게 힌트를 제공합니다. 각 컨트롤의 <xref:System.Windows.Forms.NumericUpDown.ValueChanged> 이벤트에 대한 이벤트 처리기를 작성해야 합니다. 이 이벤트는 퀴즈를 푸는 사람이 컨트롤의 값을 변경할 때마다 발생합니다.

## <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서로 이동하려면 **[자습서 3: 맞추기 게임 만들기](../ide/tutorial-3-create-a-matching-game.md)** 를 참조하세요.

- 이전 자습서 단계로 돌아가려면 [7단계: 곱하기 및 나누기 문제 추가](../ide/step-7-add-multiplication-and-division-problems.md)를 참조하세요.
