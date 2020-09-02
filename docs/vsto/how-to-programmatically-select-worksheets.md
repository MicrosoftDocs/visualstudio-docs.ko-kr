---
title: '방법: 프로그래밍 방식으로 워크시트 선택'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6134b23e7b398794529ee43a428ee8b8962ccf38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547006"
---
# <a name="how-to-programmatically-select-worksheets"></a>방법: 프로그래밍 방식으로 워크시트 선택
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> 메서드는 사용자의 선택 영역을 새 개체로 이동하는 지정된 개체를 선택합니다. 사용자의 선택 영역을 변경하지 않고 포커스를 개체로 가져오려는 경우 <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> 메서드를 사용합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 VSTO 추가 기능에서 기존 워크시트를 선택 하거나 런타임에 문서 수준 사용자 지정에서 워크시트를 만든 경우 excel 통합 문서의 Excel 컬렉션을 사용 하 여 액세스 해야 합니다 <xref:Microsoft.Office.Interop.Excel.Sheets> . 그렇지 않으면 호스트 항목에 직접 액세스할 수 있습니다 <xref:Microsoft.Office.Tools.Excel.Worksheet> .

## <a name="use-the-worksheet-host-item"></a>워크시트 호스트 항목 사용
 문서 수준 사용자 지정에서 다음 코드를 *Sheet1 .vb* 또는 *Sheet1.cs*에 추가 합니다.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>호스트 항목을 사용하여 통합 문서의 첫 번째 워크시트를 선택하려면

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> 의 `Sheet1`메서드를 호출합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel 통합 문서의 시트 컬렉션 사용
 Excel <xref:Microsoft.Office.Interop.Excel.Sheets> 컬렉션을 사용하여 워크시트에 액세스합니다.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Excel 통합 문서의 시트 컬렉션을 사용하여 통합 문서의 첫 번째 워크시트를 선택하려면

1. <xref:Microsoft.Office.Interop.Excel.Sheets> 컬렉션의 <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> 메서드를 호출하여 활성 통합 문서의 첫 번째 워크시트를 선택합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>추가 정보
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 인쇄](../vsto/how-to-programmatically-print-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에서 워크시트 삭제](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 숨기기](../vsto/how-to-programmatically-hide-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)
- [워크시트 호스트 항목](../vsto/worksheet-host-item.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
