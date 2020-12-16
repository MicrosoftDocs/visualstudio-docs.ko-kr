---
title: '방법: 프로그래밍 방식으로 통합 문서의 모든 워크시트 나열'
description: Visual Studio를 사용 하 여 Microsoft Excel 통합 문서의 모든 워크시트를 프로그래밍 방식으로 나열 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74ff02d6458e643e9a143a8132ad16f10899ec74
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525657"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>방법: 프로그래밍 방식으로 통합 문서의 모든 워크시트 나열
  <xref:Microsoft.Office.Interop.Excel.Workbook> 클래스는 <xref:Microsoft.Office.Interop.Excel.Worksheets> 개체를 제공합니다. 이 개체에는 통합 문서에 있는 모든 <xref:Microsoft.Office.Interop.Excel.Worksheet> 개체의 컬렉션이 들어 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>문서 수준 사용자 지정의 통합 문서에 있는 기존 워크시트를 모두 나열하려면

1. <xref:Microsoft.Office.Interop.Excel.Worksheets> 컬렉션을 순환하면서 각 시트의 이름을 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤에서 오프셋된 셀에 전달합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>VSTO 추가 기능의 통합 문서에 있는 기존 워크시트를 모두 나열하려면

1. <xref:Microsoft.Office.Interop.Excel.Worksheets> 컬렉션을 반복하면서 각 시트의 이름을 <xref:Microsoft.Office.Interop.Excel.Range> 개체에서 오프셋된 셀에 전달합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>참고 항목
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에 새 워크시트 추가](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 내에서 워크시트 이동](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
