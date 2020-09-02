---
title: 리본 단추를 사용 하 여 사용자 지정 작업창 동기화
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ad910f94c6b6a4345f6973e84e02c85d4fe1f0e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328331"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>연습: 사용자 지정 작업창과 리본 단추 동기화
  이 연습에서는 사용자가 리본의 토글 단추를 클릭 하 여 숨기 거 나 표시할 수 있는 사용자 지정 작업창을 만드는 방법을 보여 줍니다. Microsoft Office 애플리케이션에서는 사용자가 사용자 지정 작업창을 표시하거나 숨기는 기본 방법을 제공하지 않으므로 사용자가 클릭하여 사용자 지정 작업창을 표시하거나 숨길 수 있도록 단추와 같은 UI(사용자 인터페이스) 요소를 항상 만들어야 합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 이 연습에서는 Excel을 사용하지만 위에 나열된 애플리케이션에도 연습에서 설명하는 개념을 적용할 수 있습니다.

 이 연습에서는 다음 작업을 수행합니다.

- 사용자 지정 작업창의 UI 디자인

- 토글 단추를 리본에 추가

- 토글 단추를 사용자 지정 작업창과 동기화

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel 또는 Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)]

## <a name="create-the-add-in-project"></a>추가 기능 프로젝트 만들기
 이 단계에서는 Excel 용 VSTO 추가 기능 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. Excel 추가 기능 프로젝트 템플릿을 사용하여 **SynchronizeTaskPaneAndRibbon**이라는 이름의 Excel 추가 기능 프로젝트를 만듭니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ThisAddIn.cs** 또는 **ThisAddIn** 코드 파일을 열고 **솔루션 탐색기**에 **열고 synchronizetaskpaneandribbon** 프로젝트를 추가 합니다.

## <a name="add-a-toggle-button-to-the-ribbon"></a>토글 단추를 리본에 추가
 Office 애플리케이션의 디자인 지침 중 하나는 사용자가 항상 Office 애플리케이션 UI를 제어할 수 있어야 한다는 것입니다. 사용자가 사용자 지정 작업창을 제어할 수 있도록 작업창을 표시하고 숨기는 리본 토글 단추를 추가할 수 있습니다. 토글 단추를 만들려면 프로젝트에 **리본(비주얼 디자이너)** 항목을 추가합니다. 이 디자이너는 컨트롤을 추가 및 배치하고, 컨트롤 속성을 설정하고, 컨트롤 이벤트를 처리하는 데 유용합니다. 자세한 내용은 [리본 디자이너](../vsto/ribbon-designer.md)를 참조 하세요.

### <a name="to-add-a-toggle-button-to-the-ribbon"></a>토글 단추를 리본에 추가 하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

2. **새 항목 추가** 대화 상자에서 **리본(비주얼 디자이너)** 을 선택합니다.

3. 새 리본의 이름을 **ManageTaskPaneRibbon**으로 변경하고 **추가**를 클릭합니다.

     **ManageTaskPaneRibbon.cs** 또는 **ManageTaskPaneRibbon.vb** 파일이 리본 디자이너에서 열리고 기본 탭 및 그룹이 표시됩니다.

4. 리본 디자이너에서 **group1**을 클릭합니다.

5. **속성** 창에서 **Label** 속성을 **작업창 관리자**로 설정합니다.

6. **도구 상자** 의 **Office 리본 컨트롤**탭에서 **ToggleButton** 을 **작업창 관리자** 그룹으로 끌어 놓습니다.

7. **toggleButton1**을 클릭합니다.

8. **속성** 창에서 **Label** 속성을 **작업창 표시**로 설정합니다.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>사용자 지정 작업창의 사용자 인터페이스 디자인
 사용자 지정 작업창을 위한 비주얼 디자이너는 없지만 원하는 레이아웃을 사용하여 사용자 정의 컨트롤을 디자인할 수 있습니다. 이 연습 뒷부분에서는 사용자 지정 작업창에 사용자 정의 컨트롤을 추가합니다.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>사용자 지정 작업창의 사용자 인터페이스를 디자인하려면

1. **프로젝트** 메뉴에서 **사용자 정의 컨트롤 추가**를 클릭합니다.

2. **새 항목 추가** 대화 상자에서 새 사용자 정의 컨트롤의 이름을 **TaskPaneControl**로 변경하고 **추가**를 클릭합니다.

     사용자 정의 컨트롤이 디자이너에서 열립니다.

3. **도구 상자** 의 **공용 컨트롤**탭에서 **TextBox** 컨트롤을 사용자 정의 컨트롤로 끌어 놓습니다.

## <a name="create-the-custom-task-pane"></a>사용자 지정 작업창 만들기
 VSTO 추가 기능이 시작될 때 사용자 지정 작업창을 만들려면 사용자 정의 컨트롤을 VSTO 추가 기능의 <xref:Microsoft.Office.Tools.AddIn.Startup> 이벤트 처리기 작업창에 추가합니다. 기본적으로 사용자 지정 작업창은 표시되지 않습니다. 이 연습 뒷부분에서는 사용자가 리본에 추가한 토글 단추를 클릭할 때 작업창을 표시 하거나 숨기는 코드를 추가 합니다.

### <a name="to-create-the-custom-task-pane"></a>사용자 지정 작업창을 만들려면

1. **솔루션 탐색기**에서 **Excel**을 확장합니다.

2. **ThisAddIn.cs** 또는 **ThisAddIn.vb** 를 마우스 오른쪽 단추로 클릭하고 **코드 보기**를 클릭합니다.

3. `ThisAddIn` 클래스에 다음 코드를 추가합니다. 이 코드에서는 `TaskPaneControl` 의 인스턴스를 `ThisAddIn`의 구성원으로 선언합니다.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]

4. `ThisAddIn_Startup` 이벤트 처리기를 다음 코드로 바꿉니다. 이 코드에서는 `TaskPaneControl` 개체를 `CustomTaskPanes` 필드에 추가하지만 사용자 지정 작업창을 표시하지 않습니다. 기본적으로 <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> 클래스의 <xref:Microsoft.Office.Tools.CustomTaskPane> 속성은 **false**입니다. Visual C# 코드는 이벤트 처리기를 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 이벤트에도 연결합니다.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]

5. `ThisAddIn` 클래스에 다음 메서드를 추가합니다. 이 메서드가 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 이벤트를 처리합니다. 사용자가 **닫기** 단추(X)를 클릭하여 작업창을 닫으면 이 메서드가 리본의 토글 단추 상태를 업데이트합니다.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]

6. 다음 속성을 `ThisAddIn` 클래스에 추가합니다. 이 속성은 전용 `myCustomTaskPane1` 개체를 다른 클래스에 노출합니다. 이 연습의 뒷부분에서는 코드를 이 속성을 사용하는 `MyRibbon` 클래스에 추가합니다.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]

## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>설정/해제 단추를 사용 하 여 사용자 지정 작업창 숨기기 및 표시
 마지막 단계는 사용자가 리본의 토글 단추를 클릭할 때 사용자 지정 작업창을 표시하거나 숨기는 코드를 추가하는 것입니다.

### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>토글 단추를 사용하여 사용자 지정 작업창을 표시하거나 숨기려면

1. 리본 디자이너에서 **작업창 표시** 토글 단추를 두 번 클릭합니다.

     Visual Studio에서 이 토글 단추의 `toggleButton1_Click`이벤트를 처리하는 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 이라는 이벤트 처리기가 자동으로 생성됩니다. 또한 *MyRibbon.cs* 또는 *MyRibbon.vb* 파일이 코드 편집기에서 열립니다.

2. `toggleButton1_Click` 이벤트 처리기를 다음 코드로 바꿉니다. 사용자가 토글 단추를 클릭하면 이 코드에서는 토글 단추를 눌렀는지 안 눌렀는지에 따라 사용자 지정 작업창을 표시하거나 숨깁니다.

     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]

## <a name="test-the-add-in"></a>추가 기능 테스트
 프로젝트를 실행하면 사용자 지정 작업창을 표시하지 않고 Excel이 열립니다. 리본에서 설정/해제 단추를 클릭 하 여 코드를 테스트 합니다.

### <a name="to-test-your-vsto-add-in"></a>VSTO 추가 기능을 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

     Excel이 열리고 **추가 기능** 탭이 리본 메뉴에 표시 되는지 확인 합니다.

2. 리본에서 **추가 기능** 탭을 클릭 합니다.

3. **작업창 관리자** 그룹에서 **작업창 표시** 토글 단추를 클릭합니다.

     토글 단추를 클릭할 때 작업창이 번갈아 표시되고 숨겨지는지 확인합니다.

4. 작업창이 표시되면 작업창의 모퉁이에 있는 **닫기** 단추(X)를 클릭합니다.

     토글 단추가 눌러지지 않은 상태로 나타나는지 확인합니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서는 사용자 지정 작업창을 만드는 방법에 대해 더 자세히 설명합니다.

- 다른 응용 프로그램에 대해 VSTO 추가 기능에서 사용자 지정 작업창을 만듭니다. 사용자 지정 작업창을 지 원하는 응용 프로그램에 대 한 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)을 참조 하세요.

- 사용자 지정 작업창에서 애플리케이션을 자동화합니다. 자세한 내용은 [연습: 사용자 지정 작업창에서 응용 프로그램 자동화](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)를 참조 하세요.

- Outlook에서 열린 모든 메일 메시지에 대해 사용자 지정 작업창을 만듭니다. 자세한 내용은 [연습: Outlook에서 전자 메일 메시지와 함께 사용자 지정 작업 창 표시](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [사용자 지정 작업 창](../vsto/custom-task-panes.md)
- [방법: 응용 프로그램에 사용자 지정 작업창 추가](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [연습: 사용자 지정 작업창에서 응용 프로그램 자동화](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [연습: Outlook에서 전자 메일 메시지와 함께 사용자 지정 작업 창 표시](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
- [리본 개요](../vsto/ribbon-overview.md)
