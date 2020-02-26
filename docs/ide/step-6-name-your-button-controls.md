---
title: '6단계: 단추 컨트롤 이름 지정'
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
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
ms.openlocfilehash: a5c23f48e803665e00155d1b546ace4e4ec7bc54
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579799"
---
# <a name="step-6-name-your-button-controls"></a>6단계: 단추 컨트롤 이름 지정

폼에 <xref:System.Windows.Forms.PictureBox> 하나만 있습니다. **pictureBox1**이라는 PictureBox와 이름이 **checkBox1**인 <xref:System.Windows.Forms.CheckBox> 하나만 있습니다. 이제 코드를 작성하면 그 코드는 CheckBox 및 PictureBox를 참조하게 됩니다. 이러한 컨트롤은 하나씩만 있기 때문에 코드에서 **pictureBox1** 또는 **checkBox1** 이 무엇을 의미하는지 알 수 있습니다.

> [!TIP]
> Visual Basic에서는 컨트롤 이름의 첫 글자가 기본적으로 대문자이어야 하기 때문에 **PictureBox1**, **CheckBox1**과 같은 식으로 이름이 지정됩니다.

그러나 단추의 경우 IDE에 의해 **button1**, **button2**, **button3**및 **button4**로 이름이 지정된 네 개가 폼에 있는데, 현재 이름만으로 어떤 단추가 **닫기** 단추이고 어떤 단추가 **그림 표시** 단추인지 알 수 없습니다. 따라서 보다 자세한 정보를 주는 단추 컨트롤의 이름을 지정하는 것이 좋습니다.

## <a name="to-name-your-button-controls"></a>단추 컨트롤의 이름을 지정하려면

1. 폼에서 **닫기** 단추를 선택합니다. 단추가 모두 선택되어 있는 경우 **Esc** 키를 눌러 선택을 취소합니다. **(Name)** 속성이 보일 때까지 **속성** 창을 스크롤합니다. 속성이 사전순으로 정렬되어 있는 경우 **(Name)** 속성은 목록의 위쪽에 있습니다. 다음 스크린샷과 같이 이름을 **closeButton**으로 바꿉니다.

    ![closeButton 이름이 있는 속성 창](../ide/media/express_setnameproperty.png)<br>***closeButton*** *이름*이 있는 ***속성*** *창*

    > [!NOTE]
    > 단추 이름을 “close”와 “Button” 사이에 공백이 있는 **close Button**으로 변경해 봅니다. 이렇게 하면 IDE에서 오류 메시지를 표시합니다. "속성 값이 잘못되었습니다." 공백을 비롯한 일부 문자는 컨트롤 이름에 사용할 수 없습니다.

1. 다른 세 단추의 이름을 **backgroundButton**, **clearButton**및 **showButton**으로 바꿉니다.
**속성** 창에서 컨트롤 선택기 드롭다운 목록을 선택하면 이름을 확인할 수 있습니다. 새 단추 이름이 표시됩니다.

1. 폼에서 **그림 표시** 단추를 두 번 클릭합니다. 대신 양식에서 **사진 표시** 단추를 선택한 다음 **Enter** 키를 눌러도 됩니다. 이렇게 하면 IDE의 주 창에 **Form1.cs**라는 추가 탭이 열립니다. Visual Basic을 사용하는 경우 탭의 이름이 **Form1.vb**로 지정됩니다.

   이 탭에서는 다음 스크린샷에 표시된 것처럼 양식 이면의 코드 파일을 표시합니다.

    ![Visual C&#35; 코드가 사용된 Form1.cs 탭](../ide/media/express_showbuttoncode.png)<br>
*C# 코드가 사용된* ***Form1.cs*** 탭

    > [!NOTE]
    > Form1.cs 또는 Form1.vb 탭에 **showButton**이 **ShowButton**으로 대신 표시될 수 있습니다.

1. 다음 코드 부분을 중점적으로 살펴봅니다.

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click

    End Sub
    ```

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   `showButton_Click()`(또는 `ShowButton_Click()`)이라는 코드를 확인하고 있습니다. IDE에서는 **showButton** 단추에 대한 코드 파일을 열면 이를 폼 코드에 추가합니다. 디자인 타임에 폼에서 컨트롤에 대한 코드 파일을 열면, 컨트롤에 대한 코드가 아직 없을 경우 이 코드가 생성됩니다. *메서드*라는 이 코드는 앱을 실행하고 컨트롤(이 경우 **사진 표시** 단추)을 선택할 때 실행됩니다.

1. **Windows Forms 디자이너** 탭을 다시 선택하고(**Form1.cs [디자인]** ) **그림 지우기** 단추용 코드 파일을 열어 양식 코드에 메서드를 만듭니다. 남은 두 단추에 대해 이 작업을 반복합니다. 매번 새 메서드가 폼의 코드 파일에 추가됩니다.

1. 둘 이상의 메서드를 추가하려면 IDE에서 `checkBox1_CheckedChanged()` 메서드가 추가되도록 **Windows Forms 디자이너**에서 **CheckBox** 컨트롤에 대한 코드 파일을 엽니다. 이 메서드는 사용자가 확인란을 선택하거나 선택 취소할 때마다 호출됩니다.

   > [!TIP]
   > 앱에서 작업할 때 코드 편집기와 **Windows Forms 디자이너** 사이를 이동하는 경우가 자주 있습니다. IDE를 사용하면 프로젝트 내에서 손쉽게 이동할 수 있습니다. **솔루션 탐색기**에서 *Form1.cs*(C#) 또는 *Form1.vb*(Visual Basic)를 두 번 클릭하여 **Windows Forms 디자이너**를 열거나 메뉴 모음에서 **보기** >  **디자이너**를 차례로 선택합니다.

    다음은 코드 편집기에 표시되는 새 코드입니다.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > 코드에 이벤트 처리기가 “camelCase” 문자로 표시되지 않을 수 있습니다.

    여기서 추가한 5개의 메서드는 사용자가 단추를 선택하거나 상자를 선택하는 등의 이벤트가 발생할 때마다 애플리케이션에 의해 호출되므로 *이벤트 처리기*라고 합니다.

    디자인 타임에 IDE에서 컨트롤에 대한 코드를 볼 때 컨트롤에 대한 이벤트 처리기 메서드가 없을 경우 메서드가 하나 추가됩니다. 예를 들어 IDE에서 단추를 두 번 클릭하면 사용자가 단추를 선택할 때마다 호출되는 <xref:System.Windows.Forms.Control.Click> 이벤트에 대한 이벤트 처리기가 추가되고, 확인란을 두 번 클릭하면 사용자가 상자를 선택하거나 선택 취소할 때마다 호출되는 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 이벤트에 대한 이벤트 처리기가 추가됩니다.

    컨트롤에 대한 이벤트 처리기를 추가한 후에는 언제든지 컨트롤을 두 번 클릭하거나 메뉴 모음에서 **보기** > **코드**를 선택하여 **Windows Forms 디자이너**에서 이벤트 처리기로 돌아갈 수 있습니다.

    프로그램을 빌드할 때는 이름이 중요하므로 이벤트 처리기를 비롯한 메서드에 원하는 이름을 지정할 수 있습니다. IDE를 사용하여 이벤트 처리기를 추가하면 컨트롤 이름과 처리 중인 이벤트를 기반으로 이름이 만들어집니다.

    예를 들어 **showButton**이라는 단추에 대한 Click 이벤트의 이름은 `showButton_Click()`(또는 `ShowButton_Click()`) 이벤트 처리기 메서드라고 합니다. 또한 일반적으로 메서드 이름 다음에는 메서드임을 나타내기 위해 여는 괄호와 닫는 괄호 `()`가 추가됩니다.

    코드 변수 이름을 변경하려고 결정한 경우 코드에서 변수를 마우스 오른쪽 단추로 클릭한 다음, **리팩터링** > **이름 바꾸기**를 선택합니다. 코드에서 해당 변수의 인스턴스 이름이 모두 바뀝니다. 자세한 내용은 [이름 바꾸기 리팩터링](../ide/reference/rename.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

* 다음 자습서 단계로 이동하려면 **[7단계: 양식에 대화 상자 구성 요소 추가](../ide/step-7-add-dialog-components-to-your-form.md)** 를 참조하세요.

* 이전 자습서 단계로 돌아가려면 [5단계: 양식에 컨트롤 추가](../ide/step-5-add-controls-to-your-form.md)를 참조하세요.

## <a name="see-also"></a>참조

* [자습서 2: 시간이 지정된 수학 퀴즈 만들기](tutorial-2-create-a-timed-math-quiz.md)
* [자습서 3: 맞추기 게임 만들기](tutorial-3-create-a-matching-game.md)
