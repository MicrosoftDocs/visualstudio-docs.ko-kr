---
title: '5단계: 폼에 컨트롤 추가 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6e66c8192b1fa409482bd33287cec04f74c1304
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851524"
---
# <a name="step-5-add-controls-to-your-form"></a>5단계: 폼에 컨트롤 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 단계에서는 `PictureBox` 컨트롤 및 `CheckBox` 컨트롤과 같은 컨트롤을 폼에 추가합니다. 그런 다음 폼에 단추를 추가합니다.

 ![비디오에 연결](../data-tools/media/playvideo.gif "링크 playvideo 보려면") 이 항목의 비디오 버전을 보려면 [자습서 1: Visual Basic에서 사진 뷰어 만들기-비디오 2](https://msdn.microsoft.com/vbasic/gg315945.aspx) 또는 [자습서 1: c #에서 사진 뷰어 만들기-비디오 2](https://msdn.microsoft.com/vcsharp/gg278410.aspx)를 참조 하세요. 이러한 비디오에서는 이전 버전의 Visual Studio를 사용하므로 일부 메뉴 명령과 기타 사용자 인터페이스 요소가 약간 다를 수 있습니다. 그러나 개념 및 절차는 Visual Studio의 현재 버전에서 비슷하게 작동합니다.

### <a name="to-add-controls-to-your-form"></a>폼에 컨트롤을 추가하려면

1. Visual Studio IDE 왼쪽에 있는 도구 상자 탭으로 이동하여 **공용 컨트롤** 그룹을 확장합니다. 이렇게 하면 폼에서 가장 일반적으로 사용되는 컨트롤이 표시됩니다.

2. 폼에서 TableLayoutPanel 컨트롤을 선택합니다. TableLayoutPanel이 선택되었는지 확인하려면 **속성** 창 맨 위에 있는 드롭다운 목록 상자에 이름이 표시되는지 확인합니다. **속성** 창 맨 위에 있는 드롭다운 목록 상자를 사용하여 폼 컨트롤을 선택할 수도 있습니다. 대개 이 방식으로 컨트롤을 선택하는 것이 마우스로 작은 컨트롤을 선택하는 것보다 더 간단할 수 있습니다.

3. **PictureBox** 항목을 두 번 클릭하여 PictureBox 컨트롤을 폼에 추가합니다. TableLayoutPanel은 도킹되어 폼을 채우므로 첫 번째 빈 셀(왼쪽 위 모퉁이)에 PictureBox 컨트롤이 추가됩니다.

4. 새 PictureBox 컨트롤을 클릭하여 선택한 다음 새 PictureBox 컨트롤의 검정색 삼각형을 선택하여 다음 그림과 같이 작업 목록을 표시합니다.

     ![PictureBox 작업](../ide/media/express-pictureboxtasks.png "Express_PictureBoxTasks") PictureBox 작업

    > [!NOTE]
    > TableLayoutPanel에 실수로 잘못된 컨트롤 형식을 추가한 경우 삭제할 수 있습니다. 컨트롤을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **삭제**를 선택합니다. 메뉴 모음을 사용하여 폼에서 컨트롤을 제거할 수도 있습니다. 메뉴 모음에서 **편집**, **실행 취소**를 선택하거나 **편집**, **삭제**를 선택합니다.

5. **부모 컨테이너에서 도킹** 링크를 선택합니다. 이렇게 하면 PictureBox **Dock** 속성이 자동으로 **채우기**로 설정됩니다. 이를 확인하려면 PictureBox 컨트롤을 클릭하여 선택하고 **속성** 창으로 이동하여 **Dock** 속성이 **채우기**로 설정되었는지 확인합니다.

6. **ColumnSpan** 속성을 변경하여 PictureBox가 두 열에 모두 걸치도록 합니다. PictureBox 컨트롤을 선택하고 **ColumnSpan** 속성을 **2**로 설정합니다. 또한 PictureBox가 비어 있는 경우 빈 프레임을 표시하려면 **BorderStyle** 속성을 **Fixed3D**로 설정합니다.

    > [!NOTE]
    > PictureBox의 **ColumnSpan** 속성이 표시되지 않는 경우 PictureBox가 TableLayoutPanel이 아닌 폼에 추가되었을 수 있습니다. 이 문제를 해결하려면 PictureBox를 선택해서 삭제하고, TableLayoutPanel을 선택한 후 새 PictureBox를 추가합니다.

7. 폼에서 TableLayoutPanel을 선택한 다음 **CheckBox** 컨트롤을 폼에 추가합니다. 도구 상자에서 **CheckBox** 항목을 두 번 클릭하여 새 CheckBox 컨트롤을 테이블의 사용 가능한 다음 셀에 추가합니다. PictureBox가 TableLayoutPanel의 처음 두 셀을 차지하므로 CheckBox 컨트롤은 왼쪽 아래 셀에 추가됩니다. 다음 그림과 같이 **Text** 속성을 선택하고 단어 **늘이기**를 입력합니다.

     ![Stretch 속성이 있는 TextBox 컨트롤](../ide/media/express-pictureviewercheckbox.png "Express_PictureViewerCheckbox") Stretch 속성이 있는 TextBox 컨트롤

8. 폼에서 TableLayoutPanel을 선택하고 도구 상자에서 TableLayoutPanel 컨트롤이 있는 **컨테이너** 그룹으로 이동한 다음, **FlowLayoutPanel** 항목을 두 번 클릭하여 PictureBox의 마지막 셀(오른쪽 맨 아래)에 새 컨트롤을 추가합니다. 그런 다음 FlowLayoutPanel의 검정색 삼각형 작업 목록에서 **부모 컨테이너에서 도킹**을 선택하거나 FlowLayoutPanel의 **Dock** 속성을 **채우기**로 설정하여 FlowLayoutPanel을 TableLayoutPanel에 도킹합니다.

    > [!NOTE]
    > FlowLayoutPanel은 다른 컨트롤을 줄 맞춰 순서대로 정렬하는 컨트롤입니다. FlowLayoutPanel의 크기를 조정하면 공간이 충분한 경우 하나의 행에 모든 컨트롤이 레이아웃됩니다. 그렇지 않은 경우 하나씩 쌓아올리는 방식으로 순서대로 정렬됩니다. FlowLayoutPanel을 사용하여 네 개의 단추를 수용합니다. 단추를 추가할 때 하나씩 쌓아올리는 방식으로 배열되는 경우 단추를 추가하기 전에 FlowLayoutPanel이 선택되었는지 확인하십시오. 위에서 각 셀에는 하나의 컨트롤만 있을 수 있다고 언급했지만 TableLayoutPanel의 오른쪽 아래 셀에는 네 개의 단추 컨트롤이 있습니다. 다른 컨트롤을 포함하는 컨트롤을 셀에 배치할 수 있기 때문입니다. 이러한 유형의 컨트롤을 컨테이너라고 하며, FlowLayoutPanel은 컨테이너입니다.

### <a name="to-add-buttons"></a>단추를 추가하려면

1. 추가한 새 FlowLayoutPanel을 선택합니다. 도구 상자의 **공용 컨트롤**로 이동한 다음 **Button** 항목을 두 번 클릭하여 **button1**이라는 단추 컨트롤을 FlowLayoutPanel에 추가합니다. 반복하여 다른 단추를 추가합니다. IDE는 **button1**이라는 단추가 이미 있음을 확인하고 다음 단추인 **button2**를 호출합니다.

2. 일반적으로 도구 상자를 사용하여 다른 단추를 추가하지만 이번에는 **button2**를 선택하고 메뉴 모음에서 **편집**, **복사**를 선택하거나 Ctrl+C를 누릅니다. 메뉴 모음에서 **편집**, **붙여넣기**를 선택하거나 Ctrl+V를 눌러 단추의 복사본을 붙여넣습니다. 다시 한 번 붙여넣습니다. 이제 IDE에서 FlowLayoutPanel에 **button3**과 **button4**를 추가했습니다.

    > [!NOTE]
    > 모든 컨트롤을 복사하여 붙여넣을 수 있습니다. IDE는 논리적인 방법으로 새 컨트롤의 이름을 지정하고 배치합니다. 컨테이너에 컨트롤을 붙여넣으면 IDE는 이 컨트롤을 배치할 논리적인 다음 공간을 선택합니다.

3. 첫 번째 단추를 선택하고 **Text** 속성을 **그림 표시**로 설정합니다. 그런 후 다음 세 단추의 **Text** 속성을 **그림 지우기**, **배경색 설정** 및 **닫기**로 설정합니다.

4. 다음 단계에서는 단추의 크기를 지정하고 패널의 오른쪽에 정렬되도록 배치합니다. FlowLayoutPanel을 선택하고 **FlowDirection** 속성을 확인합니다. 이 속성을 **RightToLeft**로 변경합니다. 속성을 이렇게 변경하면 즉시 단추가 셀의 오른쪽에 정렬되며 순서가 유지되어 **그림 표시** 단추가 오른쪽에 표시됩니다.

    > [!NOTE]
    > 단추의 순서가 잘못되어 있는 경우 FlowLayoutPanel에서 단추를 끌어서 원하는 순서대로 다시 배치할 수 있습니다. 단추를 선택하여 왼쪽 또는 오른쪽으로 끌어 놓을 수 있습니다.

5. **닫기** 단추를 클릭하여 선택합니다. Ctrl 키를 누른 채로 다른 세 개의 단추를 선택하여 모든 단추가 선택되도록 합니다. 모든 단추가 선택된 상태로 **속성** 창으로 이동하여 **AutoSize** 속성까지 위로 스크롤합니다. 이 속성은 단추의 모든 텍스트에 맞게 자동으로 단추 크기가 조정되도록 합니다. 이 속성을 **true**로 설정합니다. 이제 단추가 적절한 크기로 조정되고 올바른 순서로 정렬됩니다. 네 개의 단추가 모두 선택 되어 있는 동안에는 네 개의 **AutoSize** 속성을 동시에 변경할 수 있습니다. 다음 그림에서는 네 개의 단추를 보여 줍니다.

     ![단추가 네 개 있는 사진 뷰어](../ide/media/express-autosize.png "Express_AutoSize") 단추가 네 개 있는 사진 뷰어

6. 이제 프로그램을 다시 실행하여 새로 레이아웃된 폼을 확인합니다. 단추와 확인란을 선택해도 아직 아무런 동작이 수행되지 않지만 곧 동작하게 될 것입니다.

### <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동하려면 [6단계: 단추 컨트롤 이름 지정](../ide/step-6-name-your-button-controls.md)을 참조하세요.

- 이전 자습서 단계로 돌아가려면 [4단계: TableLayoutPanel 컨트롤을 사용하여 폼 레이아웃](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)을 참조하세요.
