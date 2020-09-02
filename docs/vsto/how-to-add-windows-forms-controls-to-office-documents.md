---
title: '방법: Office 문서에 Windows forms 컨트롤 추가'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b12d51ffe3a2e647a067b95d320e8beb70cac384
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547539"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>방법: Office 문서에 Windows Forms 컨트롤 추가
  디자인 타임에 문서 수준 프로젝트에서 Microsoft Office Excel 및 Microsoft Office Word 문서에 Windows Forms 컨트롤을 추가할 수 있습니다. 런타임에 문서 수준 사용자 지정 및 VSTO 추가 기능에서 컨트롤을 추가할 수 있습니다. 예를 들어 <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> 사용자가 옵션 목록에서 선택할 수 있도록 워크시트에 컨트롤을 추가할 수 있습니다.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 이 항목에서는 다음 작업에 대해 설명합니다.

- [디자인 타임에 컨트롤 추가](#designtime)

- [런타임에 문서 수준 프로젝트에서 컨트롤 추가](#runtimedoclevel)

- [런타임에 VSTO 추가 기능에서 컨트롤 추가](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> 디자인 타임에 컨트롤 추가
 디자인 타임에 문서 수준 프로젝트의 문서에 Windows Forms 컨트롤을 추가하는 여러 가지 방법이 있습니다.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Windows Forms 컨트롤을 문서로 끌어오려면

1. 문서가 디자이너에 표시되도록 Visual Studio에서 Excel 통합 문서 프로젝트 또는 Word 문서 프로젝트를 만들거나 엽니다. 프로젝트 만들기에 대 한 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

2. **도구 상자**의 **공용 컨트롤** 탭에서 추가할 컨트롤을 클릭 하 여 문서로 끌어 옵니다.

    > [!NOTE]
    > Excel에서 컨트롤을 선택하는 경우 **수식 입력줄** 에 **=EMBED("WinForms.Control.Host","")** 가 표시됩니다. 이 텍스트는 필요하며 삭제하면 안 됩니다.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>문서에서 Windows Forms 컨트롤을 그리려면

1. 문서가 디자이너에 표시되도록 Visual Studio에서 Excel 통합 문서 프로젝트 또는 Word 문서 프로젝트를 만들거나 엽니다. 프로젝트 만들기에 대 한 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

2. **도구 상자**의 **공용 컨트롤** 탭에서 추가 하려는 컨트롤을 클릭 합니다.

3. 문서에서 컨트롤의 왼쪽 위를 배치할 위치를 클릭한 다음 컨트롤의 오른쪽 아래를 배치할 위치로 끕니다.

     지정된 위치와 크기를 사용하여 컨트롤이 문서에 추가됩니다.

    > [!NOTE]
    > Excel에서 컨트롤을 선택 하는 경우 **수식 입력줄**에 **= EMBED ("WinForms", "")** 가 표시 됩니다. 이 텍스트는 필요하며 삭제하면 안 됩니다.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>컨트롤을 한 번 클릭하여 문서에 Windows Forms 컨트롤을 추가하려면

1. 문서가 디자이너에 표시되도록 Visual Studio에서 Excel 통합 문서 프로젝트 또는 Word 문서 프로젝트를 만들거나 엽니다. 프로젝트 만들기에 대 한 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

2. **도구 상자**의 **공용 컨트롤** 탭에서 추가 하려는 컨트롤을 클릭 합니다.

3. 문서에서 컨트롤을 추가할 위치를 클릭합니다.

     기본 크기를 사용하여 컨트롤이 문서에 추가됩니다.

    > [!NOTE]
    > Excel에서 컨트롤을 선택하는 경우 **수식 입력줄** 에 **=EMBED("WinForms.Control.Host","")** 가 표시됩니다. 이 텍스트는 필요하며 삭제하면 안 됩니다.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>컨트롤을 두 번 클릭하여 문서에 Windows Forms 컨트롤을 추가하려면

1. 문서가 디자이너에 표시되도록 Visual Studio에서 Excel 통합 문서 프로젝트 또는 Word 문서 프로젝트를 만들거나 엽니다. 프로젝트 만들기에 대 한 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

2. **도구 상자**의 **공용 컨트롤** 탭에서 추가 하려는 컨트롤을 두 번 클릭 합니다.

     컨트롤의 문서 또는 활성 창의 가운데에 추가됩니다.

    > [!NOTE]
    > Excel에서 컨트롤을 선택하는 경우 **수식 입력줄** 에 **=EMBED("WinForms.Control.Host","")** 가 표시됩니다. 이 텍스트는 필요하며 삭제하면 안 됩니다.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Enter 키를 눌러 문서에 Windows Forms 컨트롤을 추가 하려면

1. 문서가 디자이너에 표시되도록 Visual Studio에서 Excel 통합 문서 프로젝트 또는 Word 문서 프로젝트를 만들거나 엽니다. 프로젝트 만들기에 대 한 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

2. **도구 상자**의 **공용 컨트롤** 탭에서 추가할 컨트롤을 클릭 하 고 **enter** 키를 누릅니다.

     컨트롤의 문서 또는 활성 창의 가운데에 추가됩니다.

    > [!NOTE]
    > Excel에서 컨트롤을 선택하는 경우 **수식 입력줄** 에 **=EMBED("WinForms.Control.Host","")** 가 표시됩니다. 이 텍스트는 필요하며 삭제하면 안 됩니다.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> 런타임에 문서 수준 프로젝트에서 컨트롤 추가
 프로그래밍 방식으로 런타임에 Windows Forms 컨트롤을 문서에 추가할 수 있습니다. Word에서 `ThisDocument` 클래스의 <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> 속성 메서드를 사용합니다. Excel에서는 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> n 클래스의 속성 메서드를 사용 `Sheet` *n* 합니다. 각 메서드에는 다양한 방법으로 컨트롤의 위치를 지정할 수 있는 여러 오버로드가 있습니다.

 런타임에 Windows Forms 컨트롤을 문서에 추가할 경우 문서를 닫으면 컨트롤이 문서에 유지되지 않습니다. 다음에 문서를 열 때 컨트롤을 다시 만들 수 있습니다. 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)를 참조 하세요.

### <a name="to-add-a-windows-forms-control-at-run-time"></a>런타임에 Windows Forms 컨트롤을 추가하려면

1. 이름 Add가 있는 메서드를 사용 \<*control class*> 합니다. 여기서 *컨트롤 클래스* 는 추가 하려는 Windows Forms 컨트롤의 클래스 이름입니다 (예: <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

     다음 코드 예제에서는 <xref:Microsoft.Office.Tools.Excel.Controls.Button> **C5** `Sheet1` Excel 용 문서 수준 프로젝트에서의 셀 C5에를 추가 하는 방법을 보여 줍니다.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a> 런타임에 VSTO 추가 기능에서 컨트롤 추가
 프로그래밍 방식으로 런타임에 열려 있는 문서에 Windows Forms 컨트롤을 추가할 수 있습니다. 먼저, 열려 있는 문서 또는 워크시트의 기반이 되는 호스트 항목을 생성합니다. 그런 다음 Word에서 새 호스트 항목의 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 속성 메서드를 사용합니다. Excel에서 새 호스트 항목의 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 속성 메서드를 사용합니다. 각 메서드에는 다양한 방법으로 컨트롤의 위치를 지정할 수 있는 여러 오버로드가 있습니다.

 런타임에 Windows Forms 컨트롤을 문서에 추가할 경우 문서를 닫으면 컨트롤이 문서에 유지되지 않습니다. 다음에 문서를 열 때 컨트롤을 다시 만들 수 있습니다. 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)를 참조 하세요.

 VSTO 추가 기능 프로젝트에서 호스트 항목을 생성 하는 방법에 대 한 자세한 내용은 [런타임에 Vsto 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조 하세요.

### <a name="to-add-a-windows-forms-control-at-run-time"></a>런타임에 Windows Forms 컨트롤을 추가하려면

1. 이름 Add가 있는 메서드를 사용 \<*control class*> 합니다. 여기서 *컨트롤 클래스* 는 추가 하려는 Windows Forms 컨트롤의 클래스 이름입니다 (예: <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

    > [!NOTE]
    > 이상을 대상으로 하는 VSTO 추가 기능 프로젝트에서 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 추가 메서드에 액세스 하려면 먼저 *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* 또는 *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* 어셈블리에 대 한 참조를 추가 해야 합니다 \<*control class*> .

     다음 코드 예제에서는 Word VSTO 추가 기능을 사용하여 활성 문서의 첫 번째 단락에 <xref:Microsoft.Office.Tools.Word.Controls.Button>을 추가하는 방법을 보여 줍니다.

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>참조
- [Office 문서에 대 한 Windows Forms 컨트롤 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [방법: 워크시트 셀에서 컨트롤 크기 조정](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
