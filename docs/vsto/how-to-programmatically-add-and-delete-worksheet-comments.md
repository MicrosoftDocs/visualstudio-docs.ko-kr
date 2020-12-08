---
title: '방법: 프로그래밍 방식으로 워크시트 메모 추가 및 삭제'
description: Microsoft Office Excel 워크시트에서 프로그래밍 방식으로 주석을 추가 하 고 삭제 하는 방법에 대해 알아봅니다. 다중 셀 범위가 아닌 단일 셀에만 주석을 추가할 수 있습니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f845197de6664728a812e2795e51605ed962c575
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844610"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>방법: 프로그래밍 방식으로 워크시트 메모 추가 및 삭제
  프로그래밍 방식으로 Microsoft Office Excel 워크시트에서 메모를 추가하거나 삭제할 수 있습니다. 메모는 다중 셀 범위가 아닌 단일 셀에만 추가할 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>문서 수준 프로젝트에서 메모 추가 및 삭제
 다음 예제에서는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 라는 단일 셀 `dateComment` 컨트롤이 `Sheet1`이라는 워크시트에 있다고 가정합니다.

### <a name="to-add-a-new-comment-to-a-named-range"></a>명명된 범위에 새 메모를 추가하려면

1. <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> 컨트롤의 <xref:Microsoft.Office.Tools.Excel.NamedRange> 메서드를 호출하고 메모 텍스트를 제공합니다. 이 코드는 `Sheet1` 클래스에 배치해야 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]

#### <a name="to-delete-a-comment-from-a-named-range"></a>명명된 범위에서 메모를 삭제하려면

1. 메모가 해당 범위에 있는지 확인하고 삭제합니다. 이 코드는 `Sheet1` 클래스에 배치해야 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>VSTO 추가 기능 프로젝트에서 메모 추가 및 삭제
 다음 예제에서는 <xref:Microsoft.Office.Interop.Excel.Range> 라는 단일 셀 `dateComment` 가 활성 워크시트에 있다고 가정합니다.

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Excel 범위에 새 메모를 추가하려면

1. <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> 의 <xref:Microsoft.Office.Interop.Excel.Range> 메서드를 호출하여 메모 텍스트를 제공합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]

### <a name="to-delete-a-comment-from-an-excel-range"></a>Excel 범위에서 메모를 삭제하려면

1. 메모가 해당 범위에 있는지 확인하고 삭제합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]

## <a name="see-also"></a>참고 항목
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 메모 표시](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
