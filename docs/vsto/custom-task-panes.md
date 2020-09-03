---
title: 사용자 지정 작업창
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 804fbf7e6d9069f6d0fb406e2a5191dcbafbbcee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254388"
---
# <a name="custom-task-panes"></a>사용자 지정 작업창
  작업창은 일반적으로 Microsoft Office 애플리케이션에서 창의 한쪽에 도킹된 사용자 인터페이스 패널입니다. 사용자 지정 작업창을 사용하면 사용자 고유의 작업창을 만들고 사용자에게 솔루션 기능에 액세스하기 위한 친숙한 인터페이스를 제공할 수 있습니다. 예를 들어 인터페이스에는 문서를 수정하거나 데이터 소스의 데이터를 표시하는 코드를 실행하는 컨트롤이 포함될 수 있습니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> 사용자 지정 작업창은 작업 창과 다릅니다. 작업 창은 Microsoft Office Word 및 Microsoft Office Excel용 문서 수준 사용자 지정의 일부입니다. 자세한 내용은 [작업 창 개요](../vsto/actions-pane-overview.md)를 참조 하세요.

## <a name="benefits-of-custom-task-panes"></a>사용자 지정 작업창의 이점
 사용자 지정 작업창을 사용하면 친숙한 사용자 인터페이스에 기능을 통합할 수 있습니다. Visual Studio 도구를 사용하여 사용자 지정 작업창을 신속하게 만들 수 있습니다.

### <a name="familiar-user-interface"></a>친숙 한 사용자 인터페이스
 Microsoft Office 시스템의 응용 프로그램 사용자는 이미 Word의 **스타일 및 서식** 작업창과 같은 작업창 사용에 대해 잘 알고 있습니다. 사용자 지정 작업창은 Microsoft Office System의 다른 작업창처럼 동작합니다. 사용자는 애플리케이션 창의 원하는 쪽에 사용자 지정 작업창을 도킹하거나 창에서 임의의 위치로 사용자 지정 작업창을 끌 수 있습니다. 동시에 여러 사용자 지정 작업창을 표시하는 VSTO 추가 기능을 만들 수 있으며 사용자가 각 작업창을 개별적으로 제어할 수 있습니다.

### <a name="windows-forms-support"></a>Windows forms 지원
 Visual Studio에서 Office 개발 도구를 사용하여 만든 사용자 지정 작업창의 사용자 인터페이스는 Windows Forms 컨트롤을 기반으로 합니다. 친숙한 Windows Forms 디자이너를 사용하여 사용자 지정 작업창에 대한 사용자 인터페이스를 디자인할 수 있습니다. Windows Forms의 데이터 바인딩 지원을 사용하여 데이터 소스를 작업창의 컨트롤에 바인딩할 수도 있습니다.

## <a name="create-a-custom-task-pane"></a>사용자 지정 작업창 만들기
 다음 두 단계를 통해 기본 사용자 지정 작업창을 만들 수 있습니다.

1. <xref:System.Windows.Forms.UserControl> 개체에 Windows Forms 컨트롤을 추가하여 사용자 지정 작업창에 대한 사용자 인터페이스를 만듭니다.

2. VSTO 추가 기능의 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> 개체에 사용자 정의 컨트롤을 전달하여 사용자 지정 작업창을 인스턴스화합니다. 이 컬렉션은 작업창의 모양을 수정하고 사용자 이벤트에 응답하는 데 사용할 수 있는 새로운 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체를 반환합니다.

   자세한 내용은 [방법: 응용 프로그램에 사용자 지정 작업창 추가](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)를 참조 하세요.

### <a name="create-the-user-interface"></a>사용자 인터페이스 만들기
 Visual Studio의 Office 개발 도구를 사용하여 만든 모든 사용자 지정 작업창에는 <xref:System.Windows.Forms.UserControl> 개체가 포함됩니다. 이 사용자 정의 컨트롤은 사용자 지정 작업창의 사용자 인터페이스를 제공합니다. 디자인 타임 또는 런타임에 사용자 정의 컨트롤을 만들 수 있습니다. 디자인 타임에 사용자 정의 컨트롤을 만드는 경우 Windows Forms 디자이너를 사용하여 작업창의 사용자 인터페이스를 생성할 수 있습니다.

### <a name="instantiate-the-custom-task-pane"></a>사용자 지정 작업창 인스턴스화
 사용자 지정 작업창의 사용자 인터페이스를 포함하는 사용자 정의 컨트롤을 만든 후 <xref:Microsoft.Office.Tools.CustomTaskPane>을 인스턴스화해야 합니다. 이렇게 하려면 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 메서드 중 하나를 호출하여 VSTO 추가 기능의 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection>에 사용자 정의 컨트롤을 전달합니다. 이 컬렉션은 `ThisAddIn` 클래스의 `CustomTaskPanes` 필드로 노출됩니다. 다음 코드 예제는 `ThisAddIn` 클래스에서 실행해야 합니다.

 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 메서드는 새로운 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체를 반환합니다. 이 개체를 사용하여 작업창의 모양을 수정하고 사용자 이벤트에 응답할 수 있습니다.

### <a name="control-the-task-pane-in-multiple-windows"></a>여러 창에서 작업 창 제어
 사용자 지정 작업창은 사용자에게 문서 또는 항목의 뷰를 제공하는 문서 프레임 창에 연결됩니다. 작업창은 연결된 창이 표시되는 경우에만 표시됩니다.

 사용자 지정 작업창을 표시하는 창을 확인하려면 작업창을 만들 때 적절한 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 메서드 오버로드를 사용합니다.

- 작업창을 활성 창에 연결하려면 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 메서드를 사용합니다.

- 작업창을 지정된 창에 호스트된 문서와 연결하려면 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 메서드를 사용합니다.

  일부 Office 애플리케이션에는 둘 이상의 창이 열려 있을 때 작업창을 만들거나 표시하는 시기에 대한 명시적 지침이 필요합니다. 따라서 작업창이 애플리케이션에서 적절한 문서 또는 항목과 함께 표시되도록 코드에서 사용자 지정 작업창을 인스턴스화할 위치를 고려하는 것이 중요합니다. 자세한 내용은 [응용 프로그램 창에서 사용자 지정 작업창 관리](#Managing)를 참조 하세요.

## <a name="access-the-application-from-the-task-pane"></a>작업 창에서 응용 프로그램에 액세스
 사용자 정의 컨트롤에서 애플리케이션을 자동화하려는 경우 코드에서 `Globals.ThisAddIn.Application`을 사용하여 개체 모델에 직접 액세스할 수 있습니다. 정적 `Globals` 클래스는 `ThisAddIn` 개체에 대한 액세스를 제공합니다. 이 개체의 `Application` 필드는 애플리케이션의 개체 모델에 대한 진입점입니다.

 개체의 필드에 대 한 자세한 내용은 `Application` `ThisAddIn` [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요. 사용자 지정 작업창에서 응용 프로그램을 자동화 하는 방법을 보여 주는 연습은 [연습: 사용자 지정 작업창에서 응용 프로그램 자동 적용](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)을 참조 하세요. 클래스에 대 한 자세한 내용은 `Globals` [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)를 참조 하세요.

## <a name="manage-the-user-interface-of-the-task-pane"></a>작업 창의 사용자 인터페이스 관리
 작업창을 만든 후 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체의 속성 및 이벤트를 사용하여 작업창의 사용자 인터페이스를 제어하고 사용자가 작업창을 변경할 때 응답할 수 있습니다.

### <a name="make-the-custom-task-pane-visible"></a>사용자 지정 작업창 표시
 기본적으로 작업창은 표시되지 않습니다. 작업 창이 표시 되도록 하려면 속성을 true로 설정 해야 합니다 <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> . **true**

 사용자는 작업창의 모퉁이에 있는 **닫기** 단추 (X)를 클릭 하 여 언제 든 지 작업 창을 닫을 수 있습니다. 그러나 사용자가 사용자 지정 작업창을 다시 열 수 있는 기본 방법은 없습니다. 표시할 방법을 제공하지 않는 한 사용자 지정 작업창을 닫은 사용자는 사용자 지정 작업창을 다시 볼 수 없습니다.

 VSTO 추가 기능에서 사용자 지정 작업창을 만드는 경우 사용자가 사용자 지정 작업창을 표시하거나 숨기기 위해 클릭할 수 있는 UI 요소(예: 단추)도 만들어야 합니다. Microsoft Office 애플리케이션에서 리본 메뉴 사용자 지정을 지원하는 사용자 지정 작업창을 만드는 경우 사용자 지정 작업창을 표시하거나 숨기는 단추를 사용하여 리본 메뉴에 컨트롤 그룹을 추가할 수 있습니다. 이 작업을 수행 하는 방법을 보여 주는 연습은 [연습: 사용자 지정 작업창과 리본 단추 동기화](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)를 참조 하세요.

 Microsoft Office 애플리케이션에서 리본 메뉴 사용자 지정을 지원하지 않는 사용자 지정 작업창을 만드는 경우 사용자 지정 작업창을 표시하거나 숨기는 <xref:Microsoft.Office.Core.CommandBarButton>을 추가할 수 있습니다.

### <a name="modify-the-appearance-of-the-task-pane"></a>작업창의 모양 수정
 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체의 속성을 사용하여 사용자 지정 작업창의 크기와 위치를 제어할 수 있습니다. 사용자 지정 작업창에 포함된 <xref:System.Windows.Forms.UserControl> 개체의 속성을 사용하여 사용자 지정 작업창의 모양에 대해 다른 여러 변경을 수행할 수 있습니다. 예를 들어 사용자 정의 컨트롤의 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 속성을 사용하여 사용자 지정 작업창에 대한 배경 이미지를 지정할 수 있습니다.

 다음 표에서는 <xref:Microsoft.Office.Tools.CustomTaskPane> 속성을 사용하여 사용자 지정 작업창에 대해 수행할 수 있는 변경 내용을 보여 줍니다.

|Task|속성|
|----------|--------------|
|작업창의 크기를 변경하려면|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|
|작업창의 위치를 변경하려면|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|
|작업창을 숨기거나 표시되도록 설정하려면|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|
|사용자가 작업창의 위치를 변경할 수 없도록 하려면|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|

### <a name="program-custom-task-pane-events"></a>프로그램 사용자 지정 작업창 이벤트
 사용자가 사용자 지정 작업창을 수정할 때 VSTO 추가 기능에서 응답하도록 할 수도 있습니다. 예를 들어 사용자가 창의 방향을 세로에서 가로로 변경하는 경우 컨트롤의 위치를 변경하는 것이 좋습니다.

 다음 표에서는 사용자 지정 작업창에 대한 사용자 변경 내용에 응답하기 위해 처리할 수 있는 이벤트를 보여 줍니다.

|Task|이벤트|
|----------|-----------|
|사용자가 작업창의 위치를 변경할 때 응답|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|사용자 작업창을 숨기거나 표시되도록 설정할 때 응답|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>작업 창에서 사용 하는 리소스 정리
 사용자 지정 작업창을 만든 후 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체는 VSTO 추가 기능이 실행되는 한 메모리에 유지됩니다. 사용자가 작업창의 모퉁이에 있는 **닫기** 단추 (X)를 클릭 한 후에도 개체가 메모리에 유지 됩니다.

 VSTO 추가 기능이 계속 실행되는 동안 작업창에서 사용하는 리소스를 정리하려면 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> 또는 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> 메서드를 사용합니다. 이러한 메서드는 `CustomTaskPanes` 컬렉션에서 지정된 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체를 제거하고 개체의 <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> 메서드를 호출합니다.

 VSTO 추가 기능이 언로드되면 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]에서 사용자 지정 작업창이 사용하는 리소스를 자동으로 정리합니다. <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> 프로젝트의 이벤트 처리기에서 또는 메서드를 호출 하지 마십시오 `ThisAddIn_Shutdown` . `ThisAddIn_Shutdown`이 호출되기 전에 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]에서 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체가 사용하는 리소스를 정리하기 때문에 이러한 메서드에서 <xref:System.ObjectDisposedException>이 발생합니다. 에 대 한 자세한 내용은 `ThisAddIn_Shutdown` [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.

## <a name="manage-custom-task-panes-in-multiple-application-windows"></a><a name="Managing"></a> 여러 응용 프로그램 창에서 사용자 지정 작업창 관리
 애플리케이션에서 여러 창을 사용하여 문서 및 기타 항목을 표시하는 사용자 지정 작업창을 만드는 경우 사용자가 예상하는 시기에 작업창이 표시되도록 추가 단계를 수행해야 합니다.

 모든 애플리케이션의 사용자 지정 작업창은 사용자에게 문서 또는 항목의 뷰를 제공하는 문서 프레임 창에 연결됩니다. 작업창은 연결된 창이 표시되는 경우에만 표시됩니다. 그러나 일부 애플리케이션은 문서 프레임 창을 동일한 방식으로 사용합니다.

 다음 애플리케이션 그룹에는 다양한 개발 요구 사항이 있습니다.

- [Outlook](#Outlook)

- [Word, InfoPath 및 PowerPoint](#WordAndInfoPath)

## <a name="outlook"></a><a name="Outlook"></a> 했습니다
 Outlook에 대한 사용자 지정 작업창을 만드는 경우 사용자 지정 작업창이 특정 탐색기 또는 검사기 창에 연결됩니다. 탐색기는 폴더의 내용을 표시 하는 창이 며, 검사기는 전자 메일 메시지 또는 작업과 같은 항목을 표시 하는 창입니다.

 여러 탐색기 또는 검사기 창이 포함된 사용자 지정 작업창을 표시하려는 경우 탐색기 또는 검사기 창이 열릴 때 사용자 지정 작업창의 새 인스턴스를 만들어야 합니다. 이렇게 하려면 탐색기 또는 검사기 창을 만들 때 발생하는 이벤트를 처리한 다음 이벤트 처리기에서 작업창을 만듭니다. 표시되는 창에 따라 탐색기 및 검사기 이벤트를 처리하여 작업창을 숨기거나 표시할 수도 있습니다.

 작업 창을 특정 탐색기 또는 검사기와 연결 하려면 메서드를 사용 하 여 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 작업창을 만들고 <xref:Microsoft.Office.Interop.Outlook.Explorer> 또는 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체를 *window* 매개 변수에 전달 합니다. 사용자 지정 작업창을 만드는 방법에 대 한 자세한 내용은 [사용자 지정 작업창 개요](../vsto/custom-task-panes.md)를 참조 하세요.

- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>

  검사기 창의 상태를 모니터링하기 위해 검사기와 관련된 다음 이벤트를 처리할 수 있습니다.

- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Outlook에서 사용자 지정 작업창의 여러 인스턴스 방지
 Outlook 창에 사용자 지정 작업창의 여러 인스턴스가 표시되지 않도록 하려면 각 창을 닫을 때 `ThisAddIn` 클래스의 `CustomTaskPanes` 컬렉션에서 사용자 지정 작업창을 명시적으로 제거합니다. 창을 닫을 때 발생하는 이벤트(예: <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> 또는 <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>)에서 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> 메서드를 호출합니다.

 사용자 지정 작업창을 명시적으로 제거하지 않는 경우 Outlook 창에 사용자 지정 작업창의 여러 인스턴스가 표시될 수도 있습니다. 경우에 따라 Outlook에서 창을 재활용하며, 재활용된 창은 연결된 사용자 지정 작업창에 대한 참조를 유지합니다.

## <a name="word-infopath-and-powerpoint"></a><a name="WordAndInfoPath"></a> Word, InfoPath 및 PowerPoint
 Word, InfoPath 및 PowerPoint는 각 문서를 서로 다른 문서 프레임 창에서 표시합니다. 이러한 애플리케이션에 대한 사용자 지정 작업창을 만드는 경우 사용자 지정 작업창이 특정 문서에만 연결됩니다. 사용자가 다른 문서를 여는 경우 이전 문서가 다시 표시될 때까지 사용자 지정 작업창이 숨겨집니다.

 여러 문서가 포함된 사용자 지정 작업창을 표시하려는 경우 사용자가 새 문서를 만들거나 기존 문서를 열 때 사용자 지정 작업창의 새 인스턴스를 만듭니다. 이렇게 하려면 문서를 만들거나 열 때 발생하는 이벤트를 처리한 다음 이벤트 처리기에서 작업창을 만듭니다. 표시되는 문서에 따라 문서 이벤트를 처리하여 작업창을 숨기거나 표시할 수도 있습니다.

 작업창을 특정 문서 창에 연결 하려면 메서드를 사용 하 여 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 작업창을 만들고 (Word의 경우) <xref:Microsoft.Office.Interop.Word.Window>  <xref:Microsoft.Office.Interop.InfoPath.WindowObject> 또는 [documentwindow](/previous-versions/office/developer/office-2010/ff762047(v=office.14)) (PowerPoint의 경우)를 *window* 매개 변수에 전달 합니다.

### <a name="word-events"></a>Word 이벤트
 Word에서 문서 창의 상태를 모니터링하기 위해 다음 이벤트를 처리할 수 있습니다.

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>

### <a name="infopath-events"></a>InfoPath 이벤트
 InfoPath에서 문서 창의 상태를 모니터링하기 위해 다음 이벤트를 처리할 수 있습니다.

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>

### <a name="powerpoint-events"></a>PowerPoint 이벤트
 PowerPoint에서 문서 창의 상태를 모니터링하기 위해 다음 이벤트를 처리할 수 있습니다.

- [Microsoft. EApplication_Event. n e t. n e w 프레젠테이션](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

- [AfterPresentationOpen를 EApplication_Event 합니다.](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

- [Microsoft. EApplication_Event 프레젠테이션을 표시 합니다.](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

- [PresentationOpen를 EApplication_Event 합니다.](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

- [Microsoft EApplication_Event를 활성화 합니다.](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

- [Microsoft EApplication_Event를 비활성화 합니다.](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>참고 항목
- [방법: 응용 프로그램에 사용자 지정 작업창 추가](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [연습: 사용자 지정 작업창에서 응용 프로그램 자동화](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [연습: 사용자 지정 작업창과 리본 단추 동기화](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [연습: Outlook에서 전자 메일 메시지와 함께 사용자 지정 작업 창 표시](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
