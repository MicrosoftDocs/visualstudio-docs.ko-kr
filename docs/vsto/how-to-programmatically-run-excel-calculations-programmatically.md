---
title: '방법: 프로그래밍 방식으로 Excel 계산 실행'
description: Visual Studio를 사용 하 여 Microsoft Excel 통합 문서에서 프로그래밍 방식으로 계산을 실행 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9fdc9cbc1966ac0fd862b795d66c7004f5089499
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823966"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>방법: 프로그래밍 방식으로 Excel 계산 실행
  비슷한 프로세스를 사용 하 여 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 나 네이티브 Excel 범위 개체에서 계산을 실행 합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>NamedRange 컨트롤에서 계산 실행
 다음 예에서는 <xref:Microsoft.Office.Tools.Excel.NamedRange> A1 셀에를 만든 다음 셀을 계산 합니다. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

### <a name="to-run-calculations-in-a-namedrange-control"></a>NamedRange 컨트롤에서 계산을 실행 하려면

1. 명명 된 범위를 만듭니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet75":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet75":::

2. 지정 된 <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> 범위의 메서드를 호출 합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet76":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet76":::

## <a name="run-calculations-in-a-native-excel-range"></a>네이티브 Excel 범위에서 계산 실행

### <a name="to-run-calculations-in-a-native-excel-range"></a>네이티브 Excel 범위에서 계산을 실행 하려면

1. 명명 된 범위를 만듭니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet30":::

2. 지정 된 <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> 범위의 메서드를 호출 합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet31":::

## <a name="see-also"></a>참조
- [범위 작업](../vsto/working-with-ranges.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
