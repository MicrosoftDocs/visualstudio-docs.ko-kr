---
title: '방법: 프로그래밍 방식으로 워크시트에서 행 그룹화'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 759ba8c6e0796b25a87e8bf0b08795aed5bade05
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537880"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>방법: 프로그래밍 방식으로 워크시트에서 행 그룹화
  하나 이상의 전체 행을 그룹화 할 수 있습니다. 워크시트에 그룹을 만들려면 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 나 네이티브 Excel 범위 개체를 사용 합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange 컨트롤 사용
 <xref:Microsoft.Office.Tools.Excel.NamedRange>디자인 타임에 문서 수준 프로젝트에 컨트롤을 추가 하는 경우 컨트롤을 사용 하 여 프로그래밍 방식으로 그룹을 만들 수 있습니다. 다음 예제에서는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 동일한 워크시트에 `data2001` , `data2002` 및의 세 가지 컨트롤이 있다고 가정 `dataAll` 합니다. 각 명명 된 범위는 워크시트의 전체 행을 참조 합니다.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>워크시트에 NamedRange 컨트롤 그룹을 만들려면

1. 각 범위의 메서드를 호출 하 여 세 개의 명명 된 범위를 그룹화 <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> 합니다. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > 행의 그룹을 해제 하려면 <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> 메서드를 호출 합니다.

## <a name="use-native-excel-ranges"></a>네이티브 Excel 범위 사용
 이 코드에서는 `data2001` 워크시트에서, 및 라는 세 개의 Excel 범위를 가정 합니다 `data2002` `dataAll` .

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>워크시트에 Excel 범위 그룹을 만들려면

1. 각 범위의 메서드를 호출 하 여 세 개의 명명 된 범위를 그룹화 <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> 합니다. 다음 예에서는 <xref:Microsoft.Office.Interop.Excel.Range> `data2001` `data2002` 동일한 워크시트에, 및 라는 세 개의 컨트롤이 있다고 가정 합니다 `dataAll` . 각 명명 된 범위는 워크시트의 전체 행을 참조 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > 행의 그룹을 해제 하려면 <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
