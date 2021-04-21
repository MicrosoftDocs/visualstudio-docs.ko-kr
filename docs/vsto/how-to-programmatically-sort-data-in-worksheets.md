---
title: '방법: 프로그래밍 방식으로 워크시트의 데이터 정렬'
description: Visual Studio를 사용 하 여 런타임에 워크시트 범위 및 목록에 포함 된 데이터를 프로그래밍 방식으로 정렬 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 024bf53b7fc7f3a6e32e10b7107c9a62d8c40cee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825019"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>방법: 프로그래밍 방식으로 워크시트의 데이터 정렬
  런타임에 워크시트 범위와 목록에 포함된 데이터를 정렬할 수 있습니다. 다음 코드에서는 첫 번째 열의 데이터와 두 번째 열의 데이터를 기준으로 차례로 `Fruits`라는 다중 열 범위를 정렬합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 데이터 정렬

### <a name="to-sort-data-in-a-namedrange-control"></a>NamedRange 컨트롤의 데이터를 정렬하려면

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤의 <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> 메서드를 호출합니다. 다음 예제에서는 워크시트에 `Fruits`라는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 필요합니다. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet78":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet78":::

   컨트롤의 데이터를 정렬 하려면 다음 코드를 *sheet1* 또는 *sheet1. cs* 에 추가 합니다. <xref:Microsoft.Office.Tools.Excel.ListObject> 코드에서는 `Sheet1` 워크시트에 `fruitList`라는 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 있다고 가정합니다.

### <a name="to-sort-data-in-a-listobject-control"></a>ListObject 컨트롤의 데이터를 정렬하려면

1. <xref:Microsoft.Office.Tools.Excel.ListObject> 호스트 컨트롤에서 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 속성의 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 메서드를 호출합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet79":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet79":::

## <a name="sort-data-in-a-vsto-add-in"></a>VSTO 추가 기능에서 데이터 정렬

### <a name="to-sort-data-in-a-native-range"></a>기본 범위의 데이터를 정렬하려면

1. 네이티브 Excel <xref:Microsoft.Office.Interop.Excel.Range> 컨트롤의 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 메서드를 호출합니다. 다음 예제에서는 워크시트에 `Fruits`라는 네이티브 Excel 컨트롤이 필요합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet23":::

### <a name="to-sort-data-in-a-listobject-control"></a>ListObject 컨트롤의 데이터를 정렬하려면

1. 네이티브 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 컨트롤에서 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 속성의 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 메서드를 호출합니다. 다음 예제에서는 활성 워크시트에 `fruitList`라는 네이티브 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 컨트롤이 있다고 가정합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet24":::

## <a name="see-also"></a>참조
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 증분 변경 데이터로 범위 채우기](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [방법: 프로그래밍 방식으로 통합 문서의 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [ListObject 컨트롤](../vsto/listobject-control.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
