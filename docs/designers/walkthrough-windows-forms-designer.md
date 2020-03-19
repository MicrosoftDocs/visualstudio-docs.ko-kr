---
title: Windows Forms 디자이너 자습서
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 07526637f2d8083f37f55aa3da36bb01479db087
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589840"
---
# <a name="walkthrough-get-started-with-windows-forms-designer"></a>연습: Windows Forms 디자이너 시작

Windows Forms 디자이너는 Windows Forms 애플리케이션 빌드를 위한 다양한 도구를 제공합니다. 이 문서에서는 다음 작업을 포함하여 디자이너에서 제공하는 다양한 도구를 사용하여 앱을 빌드하는 방법을 보여 줍니다.

- 맞춤선을 사용하여 컨트롤을 정렬합니다.
- 스마트 태그를 사용하여 디자이너 작업을 수행합니다.
- 컨트롤의 여백 및 안쪽 여백을 설정합니다.
- <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤을 사용하여 컨트롤을 정렬합니다.
- <xref:System.Windows.Forms.SplitContainer> 컨트롤을 사용하여 컨트롤의 레이아웃을 분할합니다.
- 문서 개요 창을 사용하여 레이아웃을 살펴봅니다.
- 크기 및 위치 정보를 표시하여 컨트롤을 배치합니다.
- 속성 창을 사용하여 속성 값을 설정합니다.

완료되면 Windows Forms 디자이너에서 사용할 수 있는 여러 레이아웃 기능을 사용하여 어셈블된 사용자 지정 컨트롤이 표시됩니다. 이 컨트롤은 간단한 계산기의 UI(사용자 인터페이스)를 구현합니다. 다음 이미지는 계산기 컨트롤의 일반적인 레이아웃을 보여 줍니다.

![둘러보기 계산기 UI](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>사용자 지정 컨트롤 프로젝트 만들기

첫 번째 단계는 DemoCalculator 컨트롤 프로젝트를 만드는 것입니다.

1. Visual Studio를 열고 새 **Windows Forms 컨트롤 라이브러리** 프로젝트를 만듭니다. 프로젝트 이름을 **DemoCalculatorLib**로 지정합니다.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019의 Windows Forms 컨트롤 라이브러리 템플릿](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. 파일의 이름을 바꾸려면 **솔루션 탐색기**에서 **UserControl1.vb** 또는 **UserControl1.cs**를 마우스 오른쪽 단추로 선택하고 **이름 바꾸기**를 선택한 후 파일 이름을 DemoCalculator.vb 또는 DemoCalculator.cs로 변경합니다. 코드 요소 “UserControl1”에 대한 모든 참조 이름을 변경할지 묻는 메시지가 표시되면 **예**를 선택합니다.

Windows Forms 디자이너는 DemoCalculator 컨트롤에 대한 디자이너 화면을 표시합니다. 이 뷰에서는 도구 상자에서 컨트롤 및 구성 요소를 선택하고 디자이너 화면에 배치하여 컨트롤의 모양을 그래픽으로 디자인할 수 있습니다. 사용자 지정 컨트롤에 대한 자세한 내용은 [사용자 지정 컨트롤의 종류](/dotnet/framework/winforms/controls/varieties-of-custom-controls)를 참조하세요.

## <a name="design-the-control-layout"></a>컨트롤 레이아웃 디자인

DemoCalculator 컨트롤에는 여러 Windows Forms 컨트롤이 포함되어 있습니다. 이 절차에서는 Windows Forms 디자이너를 사용하여 컨트롤을 정렬합니다.

1. Windows Forms 디자이너에서 오른쪽 아래 모서리에 있는 크기 조정 핸들을 선택하고 오른쪽 아래로 끌어서 DemoCalculator 컨트롤을 더 큰 크기로 변경합니다. Visual Studio의 오른쪽 아래 모서리에서 컨트롤의 크기 및 위치 정보를 찾습니다. 컨트롤 크기를 조정할 때 크기 정보를 확인하여 컨트롤의 크기를 너비 500 및 높이 400으로 설정합니다.

2. **도구 상자**에서 **컨테이너** 노드를 선택하여 엽니다. **SplitContainer** 컨트롤을 선택하고 디자이너 화면으로 끌어옵니다.

   `SplitContainer`가 DemoCalculator 컨트롤의 디자이너 화면에 배치됩니다.

    > [!TIP]
    > `SplitContainer` 컨트롤 크기가 DemoCalculator 컨트롤의 크기에 맞게 자동으로 조정됩니다. **속성** 창에서 `SplitContainer` 컨트롤에 대한 속성 설정을 확인합니다. <xref:System.Windows.Forms.SplitContainer.Dock%2A> 속성을 찾습니다. 해당 값은 `SplitContainer` 컨트롤이 항상 DemoCalculator 컨트롤의 경계에 맞게 크기가 조정되도록 하는 [DockStyle.Fill](xref:System.Windows.Forms.DockStyle.Fill)입니다. 이 동작을 확인하려면 DemoCalculator 컨트롤의 크기를 조정합니다.

3. **속성** 창에서 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 속성의 값을 `None`로 변경합니다.

    `SplitContainer` 컨트롤은 기본 크기로 축소되고 더 이상 DemoCalculator 컨트롤의 크기를 따르지 않습니다.

4. `SplitContainer` 컨트롤의 오른쪽 위 모서리에 있는 스마트 태그 문자 모양(![스마트 태그 문자 모양](media/smart-tag-glyph.gif))을 선택합니다. **부모 컨테이너에서 도킹**을 선택하여 `Dock` 속성을 `Fill`로 설정합니다.

    `SplitContainer` 컨트롤이 DemoCalculator 컨트롤의 경계에 도킹합니다.

    > [!NOTE]
    > 일부 컨트롤은 편리한 디자인을 위한 스마트 태그를 제공합니다. 자세한 내용은 [연습: Windows Forms 컨트롤에서 스마트 태그를 사용하여 일반 작업 수행](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls)을 참조하세요.

5. 패널 사이의 세로 테두리를 선택하고 오른쪽으로 끌어 왼쪽 패널에 공간 대부분이 오도록 합니다.

    `SplitContainer`는 DemoCalculator 컨트롤을 구분하는 이동 가능한 테두리를 사용하여 두 패널로 나눕니다. 왼쪽 패널은 계산기 단추와 표시를 포함하고 오른쪽 패널은 사용자가 수행하는 산술 연산 기록을 표시합니다.

6. **속성** 창에서 `BorderStyle` 속성의 값을 `Fixed3D`으로 변경합니다.

7. **도구 상자**에서 **공용 컨트롤** 노드를 선택하여 엽니다. `ListView` 컨트롤을 선택하고 `SplitContainer` 컨트롤의 오른쪽 패널로 끕니다.

8. `ListView` 컨트롤의 스마트 태그 문자 모양을 선택합니다. 스마트 태그 패널에서 `View` 설정을 `Details`로 변경합니다.

9. 스마트 태그 패널에서 **열 편집**을 선택합니다.

   **ColumnHeader 컬렉션 편집기** 대화 상자가 열립니다.

10. **ColumnHeader 컬렉션 편집기** 대화 상자에서 **추가**를 선택하여 `ListView` 컨트롤에 열을 추가합니다. 열의 `Text` 속성 값을 **History**로 변경합니다. **확인**을 선택하여 열을 만듭니다.

11. 스마트 태그 패널에서 **부모 컨테이너에서 도킹**을 선택한 후 스마트 태그 문자 모양을 선택하여 스마트 태그 패널을 닫습니다.

12. **컨테이너** 노드 **도구 상자**에서 `TableLayoutPanel` 컨트롤을 `SplitContainer` 컨트롤의 왼쪽 패널로 끕니다.

    `TableLayoutPanel` 컨트롤은 스마트 태그 패널이 열린 상태로 디자이너 화면에 표시됩니다. `TableLayoutPanel` 컨트롤은 자식 컨트롤을 표로 정렬합니다. `TableLayoutPanel` 컨트롤에는 DemoCalculator 컨트롤의 표시 및 단추가 포함됩니다. 자세한 내용은 [연습: TableLayoutPanel을 사용하여 컨트롤 정렬](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel)을 참조하세요.

13. 스마트 태그 패널에서 **행 및 열 편집**을 선택합니다.

    **열 및 행 스타일** 대화 상자가 열립니다.

14. 5개의 열이 표시될 때까지 **추가** 단추를 선택합니다. 5개의 열을 모두 선택하고 **크기 유형** 상자에서 **백분율**을 선택합니다. **백분율** 값을 **20**으로 설정합니다. 이렇게 하면 각 열이 같은 너비로 설정됩니다.

15. **표시**에서 **행**을 선택합니다.

16. 5개의 행이 표시될 때까지 **추가**를 선택합니다. 5개의 행을 모두 선택하고 **크기 유형** 상자에서 **백분율**을 선택합니다. **백분율** 값을 **20**으로 설정합니다. 이렇게 하면 각 행의 높이가 동일하게 설정됩니다.

17. **확인**을 선택하여 변경 내용을 적용한 다음, 스마트 태그 문자 모양을 선택하여 스마트 태그 패널을 닫습니다.

18. **속성** 창에서 `Dock` 속성의 값을 `Fill`로 변경합니다.

## <a name="populate-the-control"></a>컨트롤 채우기

이제 컨트롤의 레이아웃을 설정했으므로 단추와 표시로 DemoCalculator 컨트롤을 채울 수 있습니다.

1. **도구 상자**에서 `TextBox` 컨트롤 아이콘을 두 번 클릭합니다.

   `TextBox` 컨트롤이 `TableLayoutPanel` 컨트롤의 첫 번째 셀에 배치됩니다.

2. **속성** 창에서 `TextBox` 컨트롤의 ColumnSpan 속성을 **5**로 변경합니다.

   `TextBox` 컨트롤이 행의 가운데 위치로 이동합니다.

3. `TextBox` 컨트롤의 `Anchor` 속성 값을 `Left`, `Right`로 변경합니다.

   `TextBox` 컨트롤이 가로 방향으로 확장되어 5개의 열에 걸쳐 있습니다.

4. `TextBox` 컨트롤의 `TextAlign` 속성 값을 `Right`로 변경합니다.

5. **속성** 창에서 `Font` 속성 노드를 확장합니다. `TextBox` 컨트롤에 대해 `Size`를 **14**로, `Bold`를 **true**로 설정합니다.

6. `TableLayoutPanel` 컨트롤을 선택합니다.

7. **도구 상자**에서 `Button` 아이콘을 두 번 클릭합니다.

   `Button` 컨트롤이 `TableLayoutPanel` 컨트롤의 열린 다음 셀에 배치됩니다.

8. **도구 상자**에서 `Button` 아이콘을 네 번 더 두 번 클릭하여 `TableLayoutPanel` 컨트롤의 두 번째 행을 채웁니다.

9. **Shift** 키를 `Button` 컨트롤을 선택하여 5개의 컨트롤을 모두 선택합니다. **Ctrl**+**C**를 눌러 `Button` 컨트롤을 클립보드로 복사합니다.

10. **Ctrl**+**V**를 세 번 눌러 `Button` 컨트롤의 복사본을 `TableLayoutPanel` 컨트롤의 나머지 행에 붙여넣습니다.

11. **Shift** 키를 `Button` 컨트롤을 선택하여 20개의 컨트롤을 모두 선택합니다.

12. **속성** 창에서 `Dock` 속성의 값을 `Fill`로 변경합니다.

    모든 `Button` 컨트롤이 도킹되고 포함하는 셀을 모두 채웁니다.

13. **속성** 창에서 `Margin` 속성 노드를 확장합니다. `All` 값을 **5**로 설정합니다.

    사이에 더 큰 여백을 만들기 위해 모든 `Button` 컨트롤의 크기가 더 작아집니다.

14. **button10** 및 **button20**을 선택한 후 **삭제**를 눌러 레이아웃에서 제거합니다.

15. **button5** 및 **button15**를 선택한 후 해당 `RowSpan` 속성 값을 **2**로 변경합니다. 이러한 속성은 DemoCalculator 컨트롤의 **Clear** 및 **=** 단추가 됩니다.

## <a name="use-the-document-outline-window"></a>문서 개요 창 사용

컨트롤이나 폼이 여러 컨트롤로 채워지면 문서 개요 창을 사용하여 레이아웃을 보다 쉽게 이동할 수 있습니다.

1. 메뉴 모음에서 **보기** > **다른 창** > **문서 개요**를 선택합니다.

   문서 개요 창에는 DemoCalculator 컨트롤 및 해당 구성 요소 컨트롤의 트리 보기가 표시됩니다. `SplitContainer`와 같은 컨테이너 컨트롤은 트리에 자식 컨트롤을 하위 노드로 표시합니다. 문서 개요 창을 사용하여 표시된 컨트롤의 이름을 바꿀 수도 있습니다.

2. **문서 개요** 창에서 **button1**을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다. 이름을 sevenButton으로 변경합니다.

3. **문서 개요** 창을 사용하여 다음 목록에 따라 `Button` 컨트롤의 이름을 디자이너에서 생성한 이름에서 프로덕션 이름으로 바꿉니다.

   - button1에서 **sevenButton**으로

   - button2에서 **eightButton**으로

   - button3에서 **nineButton**으로

   - button4에서 **divisionButton**으로

   - button5에서 **clearButton**으로

   - button6에서 **fourButton**으로

   - button7에서 **fivebutton**으로

   - button8에서 **sixButton**으로

   - button9에서 **multiplicationButton**으로

   - button11에서 **onebutton**으로

   - button12에서 **twoButton**으로

   - button13에서 **threeButton**으로

   - button14에서 **subtractionButton**으로

   - button15에서 **equalsButton**으로

   - button16에서 **zeroButton**으로

   - button17에서 **changeSignButton**으로

   - button18에서 **decimalButton**으로

   - button19에서 **additionButton**으로

4. **문서 개요** 및 **속성** 창을 사용하여 다음 목록에 따라 각 `Button` 컨트롤의 `Text` 속성 값을 변경합니다.

   - sevenButton 컨트롤 텍스트 속성을 **7**로 변경

   - eightButton 컨트롤 텍스트 속성을 **8**로 변경

   - nineButton 컨트롤 텍스트 속성을 **9**로 변경

   - divisionButton 컨트롤 텍스트 속성을 **/** (정방향 슬래시)로 변경

   - clearButton 컨트롤 텍스트 속성을 **Clear**로 변경

   - fourButton 컨트롤 텍스트 속성을 **4**로 변경

   - fiveButton 컨트롤 텍스트 속성을 **5**로 변경

   - sixButton 컨트롤 텍스트 속성을 **6**으로 변경

   - multiplicationButton 컨트롤 텍스트 속성을 **\*** (별표)로 변경

   - oneButton 컨트롤 텍스트 속성을 **1**로 변경

   - twoButton 컨트롤 텍스트 속성을 **2**로 변경

   - threeButton 컨트롤 텍스트 속성을 **3**으로 변경

   - subtractionButton 컨트롤 텍스트 속성을 **-** (하이픈)으로 변경

   - equalsButton 컨트롤 텍스트 속성을 **=** (같음 기호)로 변경

   - zeroButton 컨트롤 텍스트 속성을 **0**으로 변경

   - changeSignButton 컨트롤 텍스트 속성을 **+/-** 로 변경

   - decimalButton 컨트롤 텍스트 속성을 **.** (마침표)로 변경

   - additionButton 컨트롤 텍스트 속성을 **+** (더하기 기호)으로 변경

5. 디자이너 화면에서 **Shift** 키를 누른 채 `Button` 컨트롤을 선택하여 모든 컨트롤을 선택합니다.

6. **속성** 창에서 `Font` 속성 노드를 확장합니다. 모든 `Button` 컨트롤에 대해 `Size`를 **14**로, `Bold`를 **true**로 설정합니다.

이렇게 하면 DemoCalculator 컨트롤의 디자인이 완료됩니다. 이제 계산기 논리를 제공하기만 하면 됩니다.

## <a name="implement-event-handlers"></a>이벤트 처리기 구현

DemoCalculator 컨트롤의 단추에는 대부분의 계산기 논리를 구현하는 데 사용할 수 있는 이벤트 처리기가 있습니다. Windows Forms 디자이너를 사용하여 더블 클릭 한 번으로 모든 단추의 모든 이벤트 처리기 스텁을 구현할 수 있습니다.

1. 디자이너 화면에서 **Shift** 키를 누른 채 `Button` 컨트롤을 선택하여 모든 컨트롤을 선택합니다.

2. `Button` 컨트롤 중 하나를 두 번 클릭합니다.

   디자이너에서 생성된 이벤트 처리기에 대해 코드 편집기가 열립니다.

## <a name="test-the-control"></a>컨트롤 테스트

DemoCalculator 컨트롤은 <xref:System.Windows.Forms.UserControl> 클래스에서 상속되므로 **UserControl 테스트 컨테이너**를 사용하여 해당 동작을 테스트할 수 있습니다. 자세한 내용은 [방법: UserControl의 런타임 동작 테스트](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol)를 참조하세요.

1. **F5** 키를 눌러 **UserControl 테스트 컨테이너**에서 DemoCalculator 컨트롤을 빌드하고 실행합니다.

2. `SplitContainer` 패널 사이의 테두리를 선택하고 왼쪽 및 오른쪽으로 끕니다. `TableLayoutPanel` 및 모든 자식 컨트롤은 사용 가능한 공간에 맞게 자체적으로 크기가 조정됩니다.

3. 컨트롤 테스트를 마쳤으면 **닫기**를 선택합니다.

## <a name="use-the-control-on-a-form"></a>폼에서 컨트롤 사용

DemoCalculator 컨트롤은 다른 복합 컨트롤이나 폼에서 사용할 수 있습니다. 다음 절차에서는 사용 방법을 설명합니다.

### <a name="create-the-project"></a>프로젝트를 만듭니다.

첫 번째 단계에서는 애플리케이션 프로젝트를 만듭니다. 이 프로젝트를 사용하여 사용자 지정 컨트롤을 표시하는 애플리케이션을 빌드합니다.

1. 새 **Windows Forms 애플리케이션** 프로젝트를 만들고 이름을 **DemoCalculatorTest**로 지정합니다.

2. **솔루션 탐색기**에서 **DemoCalculatorTest** 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, **참조 추가**를 선택하여 **참조 추가** 대화 상자를 엽니다.

3. **프로젝트** 탭을 선택하고 DemoCalculatorLib 프로젝트를 두 번 클릭하여 테스트 프로젝트에 참조를 추가합니다.

4. **솔루션 탐색기**에서 **DemoCalculatorTest**를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.

5. Windows Forms 디자이너에서 폼의 크기를 약 **700 x 500**으로 늘립니다.

### <a name="use-the-control-in-the-forms-layout"></a>폼의 레이아웃에서 컨트롤 사용

애플리케이션에서 DemoCalculator 컨트롤을 사용하려면 폼에 배치해야 합니다.

1. **도구 상자**에서 **DemoCalculatorLib 구성 요소** 노드를 확장합니다.

2. **DemoCalculator** 컨트롤을 **도구 상자**에서 폼으로 끌어옵니다. 컨트롤을 폼의 왼쪽 위 모서리로 이동합니다. 컨트롤이 폼의 테두리에 가까워지면 *맞춤선*이 표시됩니다. 맞춤선은 폼의 `Padding` 속성 및 컨트롤의 `Margin` 속성에 대한 거리를 나타냅니다. 맞춤선이 나타내는 위치에 컨트롤을 배치합니다.

   자세한 내용은 [연습: 맞춤선을 사용하여 컨트롤 정렬](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines)을 참조하세요.

3. **도구 상자**에서 `Button` 컨트롤을 끌어 폼에 놓습니다.

4. `Button` 컨트롤을 DemoCalculator 컨트롤 주위로 이동하고 맞춤선이 나타나는 위치를 확인합니다. 이 기능을 사용하여 컨트롤을 정확하고 쉽게 정렬할 수 있습니다. 완료되면 `Button` 컨트롤을 삭제합니다.

5. DemoCalculator 컨트롤을 마우스 오른쪽 단추로 선택하고 **속성**을 선택합니다.

6. `Dock` 속성의 값을 `Fill`로 변경합니다.

7. 폼을 선택한 다음, `Padding` 속성 노드를 확장합니다. **모두** 값을 **20**으로 변경합니다.

   DemoCalculator 컨트롤의 크기가 폼의 새 `Padding` 값에 맞도록 줄어듭니다.

8. 다양한 크기 조정 핸들을 다른 위치로 끌어 폼의 크기를 조정합니다. DemoCalculator 컨트롤의 크기가 조정되는 방법을 확인합니다.

## <a name="next-steps"></a>다음 단계

이 문서에서는 간단한 계산기의 사용자 인터페이스를 구성하는 방법을 살펴보았습니다. 계속하려면 계산기 논리를 구현하여 해당 기능을 확장한 다음, [ClickOnce를 사용하여 앱을 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)할 수 있습니다. 또는 [Windows Forms를 사용하여 사진 뷰어를 만드는](../ide/tutorial-1-create-a-picture-viewer.md) 다른 자습서를 계속 진행합니다.

## <a name="see-also"></a>참조

- [Windows Forms 컨트롤](/dotnet/framework/winforms/controls/)
- [Windows Forms 컨트롤의 접근성](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [ClickOnce를 사용하여 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
