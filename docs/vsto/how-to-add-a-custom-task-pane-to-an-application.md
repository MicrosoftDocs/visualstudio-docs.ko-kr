---
title: '방법: 응용 프로그램에 사용자 지정 작업창 추가'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0df4d51795f01c98790f1d5b0525c45cc71899ab
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546213"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>방법: 응용 프로그램에 사용자 지정 작업창 추가
  VSTO 추가 기능을 사용하여 위에 나열된 애플리케이션에 사용자 지정 작업창을 추가할 수 있습니다. 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)을 참조 하세요.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="add-a-custom-task-pane-to-an-application"></a>응용 프로그램에 사용자 지정 작업창 추가

### <a name="to-add-a-custom-task-pane-to-an-application"></a>애플리케이션에 사용자 지정 작업창을 추가하려면

1. 위에 나열된 애플리케이션 중 하나에 대한 VSTO 추가 기능 프로젝트를 열거나 만듭니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

2. **프로젝트** 메뉴에서 **사용자 정의 컨트롤 추가**를 클릭합니다.

3. **새 항목 추가** 대화 상자에서 새 사용자 정의 컨트롤의 이름을 **MyUserControl**로 변경한 다음 **추가**를 클릭 합니다.

     사용자 정의 컨트롤이 디자이너에서 열립니다.

4. **도구 상자** 에서 사용자 정의 컨트롤에 하나 이상의 Windows Forms 컨트롤을 추가 합니다.

5. **ThisAddIn.cs** 또는 **ThisAddIn** 코드 파일을 엽니다.

6. `ThisAddIn` 클래스에 다음 코드를 추가합니다. 이 코드는 `MyUserControl` 및 <xref:Microsoft.Office.Tools.CustomTaskPane> 의 인스턴스를 `ThisAddIn` 클래스의 멤버로 선언합니다.

     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]

7. 다음 코드를 `ThisAddIn_Startup` 이벤트 처리기에 추가합니다. 이 코드는 <xref:Microsoft.Office.Tools.CustomTaskPane> 컬렉션에 `MyUserControl` 개체를 추가하여 새 `CustomTaskPanes` 을 만듭니다. 코드에서 작업창도 표시합니다.

     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

    > [!NOTE]
    > 이 코드는 애플리케이션의 활성 창과 사용자 지정 작업창을 연결합니다. 일부 애플리케이션의 경우 작업창이 애플리케이션의 다른 문서나 항목과 함께 표시되도록 이 코드를 수정하는 것이 좋습니다. 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Office UI 사용자 지정](../vsto/office-ui-customization.md)
- [사용자 지정 작업 창](../vsto/custom-task-panes.md)
- [연습: 사용자 지정 작업창에서 응용 프로그램 자동화](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
