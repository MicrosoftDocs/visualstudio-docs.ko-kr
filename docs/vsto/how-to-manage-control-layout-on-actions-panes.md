---
title: '방법: 작업 창에서 컨트롤 레이아웃 관리'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6df90847000560299b8b1a6f259ffa6e7df0729
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520149"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>방법: 작업 창에서 컨트롤 레이아웃 관리
  작업 창은 기본적으로 문서 또는 워크시트의 오른쪽에 도킹 됩니다. 그러나 왼쪽, 위쪽 또는 아래쪽에 도킹할 수 있습니다. 여러 사용자 정의 컨트롤을 사용 하는 경우 작업 창에서 사용자 정의 컨트롤을 제대로 스택 하는 코드를 작성할 수 있습니다. 자세한 내용은 [작업 창 개요](../vsto/actions-pane-overview.md)를 참조 하세요.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 컨트롤의 스택 순서는 작업 창이 세로 또는 가로로 도킹 되는지에 따라 달라 집니다.

> [!NOTE]
> 런타임에 작업 창의 크기를 조정 하는 경우 작업 창에서 크기를 조정 하도록 컨트롤을 설정할 수 있습니다. Windows Forms 컨트롤의 <xref:System.Windows.Forms.Control.Anchor%2A> 속성을 사용하여 작업 창에 컨트롤을 고정할 수 있습니다. 자세한 내용은 [How to: Anchor controls on Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)를 참조 하세요.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>작업 창 컨트롤의 스택 순서를 설정 하려면

1. 여러 사용자 컨트롤이 나 중첩 된 작업 창 컨트롤을 포함 하는 작업 창이 포함 된 Microsoft Office Word 용 문서 수준 프로젝트를 엽니다. 자세한 내용은 [방법: Word 문서 또는 Excel 통합 문서에 작업 창 추가](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)를 참조 하세요.

2. **솔루션 탐색기** 에서 **ThisDocument.cs** 또는 **ThisDocument** 를 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

3. <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>작업 창의 이벤트 처리기에서 작업 창의 방향이 가로 인지 확인 합니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. 방향이 가로 이면 왼쪽에서 작업 창 컨트롤을 스택 합니다. 그렇지 않으면 위쪽에서 스택 합니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. C #에서는 이벤트 처리기에에 대 한 이벤트 처리기를 추가 해야 합니다 `ActionsPane` <xref:Microsoft.Office.Tools.Word.Document.Startup> . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. 프로젝트를 실행 하 고 작업 창이 문서 맨 위에 도킹 될 때 작업 창 컨트롤이 왼쪽에서 오른쪽으로 누적 되는지 확인 하 고, 작업 창이 문서 오른쪽에 도킹 되 면 컨트롤이 위쪽에서 아래쪽으로 누적 되는지 확인 합니다.

## <a name="example"></a>예제
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 사항이 필요합니다.

- 여러 사용자 컨트롤이 나 중첩 된 작업 창 컨트롤을 포함 하는 작업 창을 포함 하는 Word 문서 수준 프로젝트입니다.

## <a name="see-also"></a>참고 항목
- [작업 창 개요](../vsto/actions-pane-overview.md)
- [방법: Word 문서 또는 Excel 통합 문서에 작업 창 추가](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [방법: Word 문서 또는 Excel 통합 문서에 작업 창 추가](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [연습: 작업 창에서 문서에 텍스트 삽입](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [연습: 작업 창에서 문서에 텍스트 삽입](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
