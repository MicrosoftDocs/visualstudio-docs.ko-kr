---
title: '방법: 프로그래밍 방식으로 통합 문서의 범위에 스타일 적용'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b8b511d195a40f42bf0b1224dd828b6c6d2b9671
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585355"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>방법: 프로그래밍 방식으로 통합 문서의 범위에 스타일 적용
  통합 문서의 영역에 명명된 스타일을 적용할 수 있습니다. Excel에서는 미리 정의된 다양한 스타일을 제공합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 **셀 서식** 대화 상자에는 셀의 서식을 지정하는 데 사용할 수 있는 모든 옵션이 표시되며, 코드에서 이러한 각 옵션을 사용할 수 있습니다. Excel에서 이 대화 상자를 표시하려면 **형식** 메뉴에서 **셀** 을 클릭합니다.

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 명명된 범위에 스타일을 적용하려면

1. 새 스타일을 만들고 해당 특성을 설정합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]

2. <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 만들고 텍스트를 할당한 다음 새 스타일을 적용합니다. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 명명된 범위에서 스타일을 지우려면

1. 범위에 표준 스타일을 적용합니다. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>VSTO 추가 기능에서 명명된 범위에 스타일을 적용하려면

1. 새 스타일을 만들고 해당 특성을 설정합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]

2. <xref:Microsoft.Office.Interop.Excel.Range>를 만들고 텍스트를 할당한 다음 새 스타일을 적용합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>VSTO 추가 기능에서 명명 된 범위에서 스타일을 지우려면

1. 범위에 표준 스타일을 적용합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]

## <a name="see-also"></a>참고 항목
- [범위 작업](../vsto/working-with-ranges.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
