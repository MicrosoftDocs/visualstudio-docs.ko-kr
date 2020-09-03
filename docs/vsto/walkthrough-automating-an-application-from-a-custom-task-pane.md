---
title: '연습: 사용자 지정 작업창에서 응용 프로그램 자동화'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5135e96125192d7ed125287aa47c839031824fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68871930"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>연습: 사용자 지정 작업창에서 응용 프로그램 자동화
  이 연습에서는 PowerPoint를 자동화하는 사용자 지정 작업창을 만드는 방법을 보여 줍니다. 사용자 지정 작업창은 사용자가 사용자 지정 작업창에 있는 <xref:System.Windows.Forms.MonthCalendar> 컨트롤을 클릭할 때 날짜를 슬라이드에 삽입합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 이 연습에서는 특별히 PowerPoint를 사용하지만 위에 나열된 애플리케이션에도 연습에서 설명하는 개념을 적용할 수 있습니다.

 이 연습에서는 다음 작업을 수행합니다.

- 사용자 지정 작업창의 사용자 인터페이스 디자인

- 사용자 지정 작업창에서 PowerPoint 자동화

- PowerPoint에서 사용자 지정 작업창 표시

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft PowerPoint 2010 또는 [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)]입니다.

## <a name="create-the-add-in-project"></a>추가 기능 프로젝트 만들기
 첫 번째 단계는 PowerPoint 용 VSTO 추가 기능 프로젝트를 만드는 것입니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. PowerPoint 추가 기능 프로젝트 템플릿을 사용하여 이름이 **MyAddIn**인 PowerPoint VSTO 추가 기능 프로젝트를 만듭니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서는 **ThisAddIn.cs** 또는 **ThisAddIn.vb** 코드 파일을 열고 **MyAddIn** 프로젝트를 **솔루션 탐색기**에 추가합니다.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>사용자 지정 작업창의 사용자 인터페이스 디자인
 사용자 지정 작업창을 위한 비주얼 디자이너는 없지만 원하는 레이아웃을 사용하여 사용자 정의 컨트롤을 디자인할 수 있습니다. 이 연습 뒷부분에서는 사용자 지정 작업창에 사용자 정의 컨트롤을 추가합니다.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>사용자 지정 작업창의 사용자 인터페이스를 디자인하려면

1. **프로젝트** 메뉴에서 **사용자 정의 컨트롤 추가**를 클릭합니다.

2. **새 항목 추가** 대화 상자에서 사용자 정의 컨트롤의 이름을 **MyUserControl**로 변경하고 **추가**를 클릭합니다.

     사용자 정의 컨트롤이 디자이너에서 열립니다.

3. **도구 상자** 의 **공용 컨트롤**탭에서 **MonthCalendar** 컨트롤을 사용자 정의 컨트롤로 끌어 놓습니다.

     **MonthCalendar** 컨트롤이 사용자 정의 컨트롤의 디자인 화면보다 큰 경우 사용자 정의 컨트롤의 크기를 조정하여 **MonthCalendar** 컨트롤에 맞춥니다.

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>사용자 지정 작업창에서 PowerPoint 자동화
 VSTO 추가 기능의 목적은 선택한 날짜를 활성 프레젠테이션의 첫 번째 슬라이드에 넣는 것입니다. 컨트롤의 <xref:System.Windows.Forms.MonthCalendar.DateChanged> 이벤트를 사용하여 변경될 때마다 선택한 날짜를 추가합니다.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>사용자 지정 작업창에서 PowerPoint를 자동화하려면

1. 디자이너에서 <xref:System.Windows.Forms.MonthCalendar> 컨트롤을 두 번 클릭합니다.

     **MyUserControl.cs** 또는 **MyUserControl.vb** 파일이 열리고 <xref:System.Windows.Forms.MonthCalendar.DateChanged> 이벤트에 대한 이벤트 처리기가 만들어집니다.

2. 파일 맨 위에 다음 코드를 추가합니다. 이 코드는 <xref:Microsoft.Office.Core> 및 [PowerPoint](/previous-versions/office/developer/office-2010/ff763170%28v%3doffice.14%29) 네임 스페이스에 대 한 별칭을 만듭니다.

     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]

3. `MyUserControl` 클래스에 다음 코드를 추가합니다. 이 코드는 [도형](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) 개체를의 멤버로 선언 `MyUserControl` 합니다. 다음 단계에서는이 [셰이프](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) 를 사용 하 여 활성 프레젠테이션의 슬라이드에 텍스트 상자를 추가 합니다.

     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]

4. `monthCalendar1_DateChanged` 이벤트 처리기를 다음 코드로 바꿉니다. 이 코드에서는 활성 프레젠테이션의 첫 번째 슬라이드에 텍스트 상자를 추가한 다음 현재 선택한 날짜를 텍스트 상자에 추가합니다. 이 코드는 `Globals.ThisAddIn` 개체를 사용하여 PowerPoint의 개체 모델에 액세스합니다.

     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]

5. **솔루션 탐색기**에서 **MyAddIn** 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **빌드**를 클릭합니다. 프로젝트가 오류 없이 빌드되는지 확인합니다.

## <a name="display-the-custom-task-pane"></a>사용자 지정 작업창 표시
 VSTO 추가 기능이 시작할 때 사용자 지정 작업창을 표시하려면 VSTO 추가 기능의 <xref:Microsoft.Office.Tools.AddIn.Startup> 이벤트 처리기에 있는 작업창에 사용자 정의 컨트롤을 추가합니다.

### <a name="to-display-the-custom-task-pane"></a>사용자 지정 작업창을 표시하려면

1. **솔루션 탐색기**에서 **PowerPoint**를 확장합니다.

2. **ThisAddIn.cs** 또는 **ThisAddIn.vb** 를 마우스 오른쪽 단추로 클릭하고 **코드 보기**를 클릭합니다.

3. `ThisAddIn` 클래스에 다음 코드를 추가합니다. 이 코드는 `MyUserControl` 및 <xref:Microsoft.Office.Tools.CustomTaskPane> 의 인스턴스를 `ThisAddIn` 클래스의 멤버로 선언합니다.

     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]

4. `ThisAddIn_Startup` 이벤트 처리기를 다음 코드로 바꿉니다. 이 코드는 <xref:Microsoft.Office.Tools.CustomTaskPane> 컬렉션에 `MyUserControl` 개체를 추가하여 새 `CustomTaskPanes` 을 만듭니다. 코드에서 작업창도 표시합니다.

     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]

## <a name="test-the-add-in"></a>추가 기능 테스트
 프로젝트를 실행하면 PowerPoint가 열리고 VSTO 추가 기능에서 사용자 지정 작업창을 표시합니다. <xref:System.Windows.Forms.MonthCalendar> 컨트롤을 클릭하여 코드를 테스트합니다.

### <a name="to-test-your-vsto-add-in"></a>VSTO 추가 기능을 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 사용자 지정 작업창이 표시되는지 확인합니다.

3. 작업창의 <xref:System.Windows.Forms.MonthCalendar> 컨트롤에서 날짜를 클릭합니다.

     날짜가 활성 프레젠테이션의 첫 번째 슬라이드에 삽입됩니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서는 사용자 지정 작업창을 만드는 방법에 대해 더 자세히 설명합니다.

- 다른 응용 프로그램에 대해 VSTO 추가 기능에서 사용자 지정 작업창을 만듭니다. 사용자 지정 작업창을 지 원하는 응용 프로그램에 대 한 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)을 참조 하세요.

- 사용자 지정 작업창을 숨기거나 표시하는 데 사용할 수 있는 리본 단추를 만듭니다. 자세한 내용은 [연습: 사용자 지정 작업창과 리본 단추 동기화](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)를 참조 하세요.

- Outlook에서 열린 모든 메일 메시지에 대해 사용자 지정 작업창을 만듭니다. 자세한 내용은 [연습: Outlook에서 전자 메일 메시지와 함께 사용자 지정 작업 창 표시](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [사용자 지정 작업 창](../vsto/custom-task-panes.md)
- [방법: 응용 프로그램에 사용자 지정 작업창 추가](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [연습: 사용자 지정 작업창과 리본 단추 동기화](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [연습: Outlook에서 전자 메일 메시지와 함께 사용자 지정 작업 창 표시](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
