---
title: Word 문서 또는 Excel 통합 문서에 작업 창 추가
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2d24ec3a17c9e0824c6b7aaffeaaac02c1c4f76e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546226"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>방법: Word 문서 또는 Excel 통합 문서에 작업 창 추가
  Microsoft Office Word 문서 또는 Microsoft Excel 통합 문서에 작업 창을 추가 하려면 먼저 Windows Forms 사용자 정의 컨트롤을 만듭니다. 그런 다음 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` 프로젝트에서 필드 (Word) 또는 `ThisWorkbook.ActionsPane` 필드 (Excel)의 속성에 사용자 정의 컨트롤을 추가 합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="creating-the-user-control"></a>사용자 정의 컨트롤 만들기
 다음 절차에서는 Word 또는 Excel 프로젝트에서 사용자 정의 컨트롤을 만드는 방법을 보여 줍니다. 또한 클릭할 때 문서 또는 통합 문서에 텍스트를 기록 하는 단추를 사용자 정의 컨트롤에 추가 합니다.

#### <a name="to-create-the-user-control"></a>사용자 정의 컨트롤을 만들려면

1. Visual Studio에서 Word 또는 Excel 문서 수준 프로젝트를 엽니다.

2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

3. **새 항목 추가** 대화 상자에서 **작업 창 컨트롤**을 선택 하 고 이름을 **HelloControl**로 선택한 다음 **추가**를 클릭 합니다.

    > [!NOTE]
    > 또는 **사용자 정의 컨트롤** 항목을 프로젝트에 추가할 수 있습니다. **작업 창 컨트롤** 및 **사용자 정의 컨트롤** 항목에 의해 생성 된 클래스는 기능적으로 동일 합니다.

4. **도구 상자** 의 **Windows Forms** 탭에서 **Button** 컨트롤을 컨트롤로 끌어 옵니다.

    > [!NOTE]
    > 컨트롤이 디자이너에 표시 되지 않는 경우 **솔루션 탐색기**에서 **HelloControl** 를 두 번 클릭 합니다.

5. 단추의 이벤트 처리기에 코드를 추가 <xref:System.Windows.Forms.Control.Click> 합니다. 다음 예제에서는 Microsoft Office Word 문서에 대 한 코드를 보여 줍니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]

6. C #에서는 단추 클릭에 대 한 이벤트 처리기를 추가 해야 합니다. 호출 후 생성자에이 코드를 추가할 수 있습니다 `HelloControl` `InitializeComponent` .

     이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]

## <a name="add-the-user-control-to-the-actions-pane"></a>작업 창에 사용자 정의 컨트롤 추가
 작업 창을 표시 하려면 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` 필드 (Word) 또는 `ThisWorkbook.ActionsPane` 필드 (Excel)의 속성에 사용자 정의 컨트롤을 추가 합니다.

### <a name="to-add-the-user-control-to-the-actions-pane"></a>작업 창에 사용자 정의 컨트롤을 추가 하려면

1. `ThisDocument`클래스 수준 선언으로 또는 클래스에 다음 코드를 추가 `ThisWorkbook` 합니다 (메서드에이 코드를 추가 하지 않음).

     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]

2. 클래스의 `ThisDocument_Startup` 이벤트 처리기 `ThisDocument` 또는 `ThisWorkbook_Startup` 클래스의 이벤트 처리기에 다음 코드를 추가 `ThisWorkbook` 합니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]

## <a name="see-also"></a>참조
- [작업 창 개요](../vsto/actions-pane-overview.md)
- [연습: 작업 창에서 문서에 텍스트 삽입](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [방법: 작업 창에서 컨트롤 레이아웃 관리](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [연습: 작업 창에서 문서에 텍스트 삽입](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
