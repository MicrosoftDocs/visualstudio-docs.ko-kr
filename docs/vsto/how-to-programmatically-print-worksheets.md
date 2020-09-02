---
title: '방법: 프로그래밍 방식으로 워크시트 인쇄'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b0affdd34ad1cb302beacdc1abc9d02275878afd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537893"
---
# <a name="how-to-programmatically-print-worksheets"></a>방법: 프로그래밍 방식으로 워크시트 인쇄

통합 문서의 모든 워크시트를 인쇄할 수 있습니다.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 워크시트 인쇄

### <a name="to-print-a-worksheet"></a>워크시트를 인쇄하려면

1. `Sheet1`의 `PrintOut` 메서드를 호출하고, 두 복사본을 요청하고, 인쇄 전에 문서를 미리 봅니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>메서드를 사용 하면 **인쇄 미리 보기** 창에 지정 된 개체를 표시할 수 있습니다. 다음 코드에서는 `Sheet1`이라는 <xref:Microsoft.Office.Tools.Excel.Worksheet> 호스트 항목이 있다고 가정합니다.

### <a name="to-preview-a-page-before-printing"></a>인쇄 전에 페이지를 미리 보려면

1. 워크시트의 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> 메서드를 호출합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>VSTO 추가 기능에서 워크시트 인쇄

### <a name="to-print-a-worksheet"></a>워크시트를 인쇄하려면

1. 활성 워크시트의 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> 메서드를 호출하고, 두 복사본을 요청하고, 인쇄 전에 문서를 미리 봅니다.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>메서드를 사용 하면 **인쇄 미리 보기** 창에 지정 된 개체를 표시할 수 있습니다.

### <a name="to-preview-a-page-before-printing"></a>인쇄 전에 페이지를 미리 보려면

1. 활성 워크시트의 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> 메서드를 호출합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>추가 정보

- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트에서 맞춤법 검사](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [워크시트 호스트 항목](../vsto/worksheet-host-item.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
