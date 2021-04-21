---
title: 프로그래밍 방식으로 Excel 범위에서 날짜 값을 저장 & 검색
description: Visual Studio를 사용 하 여 프로그래밍 방식으로 Microsoft Excel 범위에서 날짜 값을 저장 하 고 검색 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e3115e00147a5dff850f6e0c051ffc3b6733218
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826241"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>방법: 프로그래밍 방식으로 Excel 범위에서 날짜 값 저장 및 검색
  <xref:Microsoft.Office.Tools.Excel.NamedRange>컨트롤 또는 네이티브 Excel 범위 개체에서 값을 저장 하 고 검색할 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Visual Studio의 Office 개발 도구를 사용 하 여 범위에서 1/1/1900 이후의 날짜 값을 저장 하는 경우에는 OA (OLE Automation) 형식으로 저장 됩니다. 메서드를 사용 <xref:System.DateTime.FromOADate%2A> 하 여 OA (OLE Automation) 날짜의 값을 검색 해야 합니다. 날짜가 1/1/1900 이전인 경우 문자열로 저장 됩니다.

> [!NOTE]
> Excel 날짜는 처음 두 달 1900에 대 한 OLE 자동화 날짜와 다릅니다. **1904 date 시스템** 옵션을 선택 하는 경우에도 차이점이 있습니다. 아래 코드 예제에서는 이러한 차이를 해결 하지 않습니다.

## <a name="use-a-namedrange-control"></a>NamedRange 컨트롤 사용

- 이 예제는 문서 수준 사용자 지정을 위한 것입니다. 다음 코드는 클래스가 아니라 시트 클래스에 배치 해야 합니다 `ThisWorkbook` .

### <a name="to-store-a-date-value-in-a-named-range"></a>명명 된 범위에 날짜 값을 저장 하려면

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** 셀에 컨트롤을 만듭니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. 오늘 날짜를의 값으로 설정 `NamedRange1` 합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>명명 된 범위에서 날짜 값을 검색 하려면

1. 에서 날짜 값을 검색 `NamedRange1` 합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>네이티브 Excel 범위 사용

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>네이티브 Excel 범위 개체에 날짜 값을 저장 하려면

1. <xref:Microsoft.Office.Interop.Excel.Range> **A1** 셀을 나타내는을 만듭니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. 오늘 날짜를의 값으로 설정 `rng` 합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>네이티브 Excel 범위 개체에서 날짜 값을 검색 하려면

1. 에서 날짜 값을 검색 `rng` 합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>참조
- [범위 작업](../vsto/working-with-ranges.md)
- [Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
