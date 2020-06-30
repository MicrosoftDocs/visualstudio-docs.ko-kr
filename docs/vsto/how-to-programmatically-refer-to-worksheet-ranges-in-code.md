---
title: '방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93673fcc270ce2f1ac43804cb1d794281f28c702
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547396"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조
  유사한 프로세스를 사용 하 여 컨트롤의 내용이 <xref:Microsoft.Office.Tools.Excel.NamedRange> 나 네이티브 Excel 범위 개체를 참조 합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange 컨트롤 사용
 다음 예에서는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 워크시트에를 추가한 다음 범위의 셀에 텍스트를 추가 합니다.

### <a name="to-refer-to-a-namedrange-control"></a>NamedRange 컨트롤을 참조 하려면

1. 컨트롤의 속성에 문자열을 할당 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> 합니다. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>네이티브 Excel 범위 사용
 다음 예에서는 워크시트에 네이티브 Excel 범위를 추가한 다음 범위에 있는 셀에 텍스트를 추가 합니다.

### <a name="to-refer-to-a-native-range-object"></a>네이티브 범위 개체를 참조 하려면

1. 범위의 속성에 문자열을 할당 <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>참고 항목
- [범위 작업](../vsto/working-with-ranges.md)
- [방법: 프로그래밍 방식으로 워크시트에서 맞춤법 검사](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서의 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [방법: 프로그래밍 방식으로 증분 변경 데이터로 범위 채우기](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [방법: 프로그래밍 방식으로 워크시트 범위에서 텍스트 검색](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
