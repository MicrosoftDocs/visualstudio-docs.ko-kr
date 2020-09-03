---
title: '방법: 프로그래밍 방식으로 Excel 범위에 색 적용'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d4a99e2e71e6a87b304ceea45a3cd595f911ff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543457"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>방법: 프로그래밍 방식으로 Excel 범위에 색 적용
  셀 범위 내의 텍스트에 색을 적용 하려면 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 나 네이티브 Excel 범위 개체를 사용 합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange 컨트롤 사용
 이 예제는 문서 수준 사용자 지정을 위한 것입니다.

### <a name="to-apply-color-to-a-namedrange-control"></a>NamedRange 컨트롤에 색을 적용 하려면

1. <xref:Microsoft.Office.Tools.Excel.NamedRange>A1 셀에 컨트롤을 만듭니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. 컨트롤의 텍스트 색을 설정 합니다 <xref:Microsoft.Office.Tools.Excel.NamedRange> .

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>네이티브 Excel 범위 사용

### <a name="to-apply-color-to-a-native-excel-range-object"></a>네이티브 Excel 범위 개체에 색을 적용 하려면

1. A1 셀에 범위를 만든 다음 텍스트 색을 설정 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>추가 정보
- [범위 작업](../vsto/working-with-ranges.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [방법: 프로그래밍 방식으로 통합 문서의 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
