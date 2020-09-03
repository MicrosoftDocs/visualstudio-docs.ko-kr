---
title: '방법: 프로그래밍 방식으로 워크시트 복사'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8226f337994c686d4d370e91831bc1262d3ef85e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546083"
---
# <a name="how-to-programmatically-copy-worksheets"></a>방법: 프로그래밍 방식으로 워크시트 복사
  워크시트의 복사본을 만들고 통합 문서의 기존 워크시트 앞이나 뒤에 해당 워크시트를 삽입할 수 있습니다. 워크시트를 삽입할 위치를 지정하지 않으면 새 워크시트를 포함할 새 통합 문서가 생성됩니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> 프로그래밍 방식으로 워크시트를 복사하든 또는 최종 사용자가 수동으로 워크시트를 복사하든 관계없이 새 워크시트에는 숨겨진 코드가 없으며 새 워크시트의 컨트롤이 작동하지 않습니다. 이는 새로 복사한 워크시트가 <xref:Microsoft.Office.Tools.Excel.Worksheet> 호스트 항목이 아니라 <xref:Microsoft.Office.Interop.Excel.Worksheet> 개체이기 때문입니다. Windows Forms 컨트롤 및 호스트 컨트롤은 호스트 항목에만 추가할 수 있습니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤의 프로그래밍](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)에 대 한 제한 사항을 참조 하세요.

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 통합 문서에 복사된 워크시트를 추가하려면

1. <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> 메서드를 사용하여 현재 통합 문서의 첫 번째 워크시트를 복사하고 세 번째 시트 뒤에 복사본을 배치합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>VSTO 추가 기능에서 통합 문서에 복사된 워크시트를 추가하려면

1. <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> 메서드를 사용하여 현재 통합 문서의 첫 번째 워크시트를 복사하고 세 번째 시트 뒤에 복사본을 배치합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]

## <a name="see-also"></a>추가 정보
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [방법: 프로그래밍 방식으로 통합 문서에 새 워크시트 추가](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서에서 워크시트 삭제](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 선택](../vsto/how-to-programmatically-select-worksheets.md)
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
