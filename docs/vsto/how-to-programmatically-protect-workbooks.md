---
title: '방법: 프로그래밍 방식으로 통합 문서 보호'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee7444c63c2d774e9b22ea612049f09429729c79
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537633"
---
# <a name="how-to-programmatically-protect-workbooks"></a>방법: 프로그래밍 방식으로 통합 문서 보호
  사용자가 워크시트를 추가 하거나 삭제할 수 없으며 프로그래밍 방식으로 통합 문서의 보호를 해제할 수 있도록 Microsoft Office Excel 통합 문서를 보호할 수 있습니다. 선택적으로 암호를 지정 하 고, 구조를 보호할 지 여부를 표시 하 고 (사용자가 시트를 이동할 수 없도록) 통합 문서의 창을 보호할 지 여부를 지정할 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 통합 문서를 보호 해도 사용자가 셀을 편집 하는 것을 중지 하지 않습니다. 데이터를 보호 하려면 워크시트를 보호 해야 합니다. 자세한 내용은 [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)를 참조 하세요.

 다음 코드 예에서는 변수를 사용 하 여 사용자 로부터 받은 암호를 포함 합니다.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>문서 수준 사용자 지정의 일부인 통합 문서 보호

### <a name="to-protect-a-workbook"></a>통합 문서를 보호 하려면

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>통합 문서의 메서드를 호출 하 고 암호를 포함 합니다. 다음 코드 예제를 사용 하려면 `ThisWorkbook` 시트 클래스가 아닌 클래스에서 실행 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>통합 문서의 보호를 해제 하려면

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>필요한 경우 암호를 전달 하 여 메서드를 호출 합니다. 다음 코드 예제를 사용 하려면 `ThisWorkbook` 시트 클래스가 아닌 클래스에서 실행 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>응용 프로그램 수준 추가 기능을 사용 하 여 통합 문서 보호

### <a name="to-protect-a-workbook"></a>통합 문서를 보호 하려면

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A>통합 문서의 메서드를 호출 하 고 암호를 포함 합니다. 이 코드 예제에서는 활성 통합 문서를 사용 합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 코드를 실행합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>통합 문서의 보호를 해제 하려면

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A>필요한 경우 암호를 전달 하 여 활성 통합 문서의 메서드를 호출 합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 코드를 실행합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>참고 항목
- [통합 문서 작업](../vsto/working-with-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 숨기기](../vsto/how-to-programmatically-hide-worksheets.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
