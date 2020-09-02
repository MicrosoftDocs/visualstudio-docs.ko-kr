---
title: '방법: 프로그래밍 방식으로 통합 문서 닫기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3d3fe0f929632bd7021def9f6597182aa8fea87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547500"
---
# <a name="how-to-programmatically-close-workbooks"></a>방법: 프로그래밍 방식으로 통합 문서 닫기
  활성 통합 문서를 닫거나 닫을 통합 문서를 지정할 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>활성 통합 문서 닫기
 활성 통합 문서를 닫는 절차에는 문서 수준 사용자 지정 및 VSTO 추가 기능에 대해 각각 하나씩, 두 가지가 있습니다.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 활성 통합 문서를 닫으려면

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> 메서드를 호출하여 사용자 지정과 연결된 통합 문서를 닫습니다. 다음 코드 예제를 사용하려면 Excel용 문서 수준 프로젝트의 `Sheet1` 클래스에서 실행합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>VSTO 추가 기능에서 활성 통합 문서를 닫으려면

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> 메서드를 호출하여 활성 통합 문서를 닫습니다. 다음 코드 예제를 사용하려면 Excel용 VSTO 추가 기능 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]

## <a name="close-a-workbook-that-you-specify-by-name"></a>이름으로 지정한 통합 문서를 닫습니다.
 이름으로 지정한 통합 문서를 닫는 방법은 VSTO 추가 기능과 문서 수준 사용자 지정에서 동일합니다.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>이름으로 지정한 통합 문서를 닫으려면

1. <xref:Microsoft.Office.Interop.Excel.Workbooks> 컬렉션에 대한 인수로 통합 문서 이름을 지정합니다. 다음 코드 예제에서는 **NewWorkbook** 이라는 통합 문서가 Excel에서 열려 있다고 가정합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]

## <a name="see-also"></a>추가 정보
- [통합 문서 작업](../vsto/working-with-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 저장](../vsto/how-to-programmatically-save-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 열기](../vsto/how-to-programmatically-open-workbooks.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
