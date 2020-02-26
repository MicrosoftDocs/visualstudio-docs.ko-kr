---
title: '6단계: 타이머 추가'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23d050df688d4d1efec75245e6f48d748464170c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579318"
---
# <a name="step-6-add-a-timer"></a>6단계: 타이머 추가
다음에는 일치 게임에 <xref:System.Windows.Forms.Timer> 컨트롤을 추가합니다. 타이머는 지정한 시간(밀리초)을 대기한 뒤 *틱*이라고 하는 이벤트를 발생시킵니다. 이 방법은 작업을 시작하거나 작업을 정기적으로 반복하는 데 유용합니다. 이 경우 타이머를 사용하여 플레이어가 두 개의 아이콘을 선택할 수 있도록 하고 아이콘이 서로 일치하지 않을 경우 잠시 후 다시 두 개의 아이콘을 숨깁니다.

## <a name="to-add-a-timer"></a>타이머를 추가하려면

1. **Windows Forms 디자이너**의 도구 상자에서 **구성 요소** 범주의 **Timer**를 선택한 다음, **Enter** 키를 선택하거나 타이머를 두 번 클릭하여 타이머 컨트롤을 폼에 추가합니다. **Timer1**이라고 하는 타이머의 아이콘이 다음 이미지와 같이 폼 아래 공간에 나타납니다.

     ![Timer](../ide/media/express_timer.png)<br/>
***Timer***

    > [!NOTE]
    > 도구 상자가 비어 있는 경우 도구 상자를 열기 전에 폼 뒤쪽의 코드가 아닌 폼 디자이너를 선택했는지 확인하십시오.

2. **Timer1** 아이콘을 선택하여 타이머를 선택합니다. **속성** 창에서 이벤트 보기에서 속성 보기로 전환합니다. 그런 다음 타이머의 **Interval** 속성은 **750**으로 설정하고 **Enabled** 속성은 **False**로 설정합니다. **Interval** 속성은 타이머의 *틱* 간 대기 시간이나 <xref:System.Windows.Forms.Timer.Tick> 이벤트를 트리거하는 시점을 나타냅니다. 750이라는 값은 Tick 이벤트를 발생시키기 전에 타이머가 3/4초, 즉 750 밀리초를 대기함을 의미합니다. <xref:System.Windows.Forms.Timer.Start> 메서드를 호출하여 플레이어가 두 번째 레이블을 선택한 후에만 타이머가 시작되도록 합니다.

3. **Windows Forms 디자이너**에서 타이머 컨트롤 아이콘을 선택한 다음, **Enter** 키를 선택하거나, 타이머를 두 번 클릭하여 빈 Tick 이벤트 처리기를 추가합니다. 또는 코드를 다음 코드로 바꾸거나 이벤트 처리기에 다음 코드를 수동으로 입력합니다.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > 이 페이지의 오른쪽 위에 있는 프로그래밍 언어 컨트롤을 사용하여 C# 코드 조각 또는 Visual Basic 코드 조각을 볼 수 있습니다.<br><br>![Docs.Microsoft.com에 대한 프로그래밍 언어 컨트롤](../ide/media/docs-programming-language-control.png)

     틱 이벤트 처리기는 다음 세 가지 작업을 수행합니다. 첫 번째로 타이머는 <xref:System.Windows.Forms.Timer.Stop> 메서드를 호출하면 실행이 중지됩니다. 그런 다음 `firstClicked`와 `secondClicked`라는 두 개의 참조 변수를 사용하여 플레이어가 선택한 두 레이블의 아이콘이 다시 보이지 않도록 합니다. 마지막으로 `firstClicked` 및 `secondClicked` 참조 변수를 `null`(C#의 경우)과 `Nothing`(Visual Basic의 경우)으로 다시 설정합니다. 이 단계는 프로그램 자체를 다시 설정하는 방식이기 때문에 중요합니다. 이제 <xref:System.Windows.Forms.Label> 컨트롤이 추적되고 있지 않으며 플레이어는 레이블을 다시 선택할 수 있습니다.

    > [!NOTE]
    > Timer 개체에는 타이머를 시작하는 `Start()` 메서드와 타이머를 중지하는 `Stop()` 메서드가 있습니다. **속성** 창에서 타이머의 **Enabled** 속성을 **True**로 설정하면 프로그램이 시작되는 즉시 타이머에서 틱이 시작됩니다. 그러나 이 속성을 **False**로 설정하면 `Start()` 메서드가 호출될 때까지 틱을 시작하지 않습니다. 일반적으로 타이머는 틱 사이의 밀리초를 결정하는 **Interval** 속성을 사용하여 Tick 이벤트를 반복적으로 발생시킵니다. 이 경우에 Tick 이벤트 내에서 타이머의 `Stop()` 메서드가 호출되는 방식을 살펴보면 타이머가 *일회 모드*로 설정되고, 그에 따라 `Start()` 메서드가 호출되면 지정한 간격만큼 기다렸다가 단일 Tick 이벤트를 트리거한 뒤 중지됩니다.

4. 새 타이머의 동작을 보려면 코드 편집기로 이동하여 다음 코드를 `label_Click()` 이벤트 처리기 메서드의 위쪽과 아래쪽에 추가합니다. `if` 문을 위쪽에 추가하고 세 개의 문을 아래쪽에 추가하며 메서드의 나머지 부분은 그대로 유지됩니다.

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     메서드 위쪽의 코드는 **Enabled** 속성 값을 검사하여 타이머가 시작되었는지 여부를 확인합니다. 그러면 플레이어가 첫 번째 및 두 번째 Label 컨트롤을 선택하고 타이머가 시작되는 경우 세 번째 레이블을 선택해도 아무것도 수행되지 않습니다.

     메서드 아래쪽의 코드는 플레이어가 선택한 두 번째 Label 컨트롤을 추적하도록 `secondClicked` 참조 변수를 설정한 다음, 레이블의 아이콘 색을 검정으로 설정하여 표시합니다. 그런 다음 750밀리초 동안 기다린 후 단일 Tick 이벤트를 발생시키도록 일회 모드에서 타이머를 시작합니다. 그러면 타이머의 Tick 이벤트 처리기는 두 아이콘을 숨기고 `firstClicked` 및 `secondClicked` 참조 변수를 다시 설정하므로 폼에서 플레이어가 다른 아이콘 쌍을 선택할 수 있습니다.

5. 프로그램을 저장하고 실행합니다. 아이콘을 선택하면 표시됩니다.

6. 다른 아이콘을 선택합니다. 그러면 해당 아이콘이 잠깐 나타났다가 두 아이콘이 모두 사라집니다. 이 작업을 여러 번 반복하십시오. 이제 폼에서 사용자가 선택하는 첫 번째 아이콘과 두 번째 아이콘을 추적하고, 아이콘이 사라지기 전에 타이머를 사용하여 일시 중지시킵니다.

## <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동하려면 **[7단계: 쌍 표시](../ide/step-7-keep-pairs-visible.md)** 를 참조하세요.

- 이전 자습서 단계로 돌아가려면 [5단계: 레이블 참조 추가](../ide/step-5-add-label-references.md)를 참조하세요.
