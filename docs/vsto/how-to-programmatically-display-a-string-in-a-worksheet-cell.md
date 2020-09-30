---
title: '방법: 프로그래밍 방식으로 워크시트 셀에 문자열 표시'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb3dbaec2efd95f63428e8494598720953f791e7
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585225"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>방법: 프로그래밍 방식으로 워크시트 셀에 문자열 표시
  이 예제에서는 프로그래밍 방식으로 셀에 텍스트를 표시 하는 방법을 보여 줍니다. 셀에 텍스트를 표시 하려면 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 나 네이티브 Excel 범위 개체를 사용 합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange 컨트롤 사용
 이 예제에서는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 이라는 컨트롤을 사용 `message` 합니다. 디자인 타임에 컨트롤을 문서 수준 사용자 지정에 추가 해야 합니다. 다음 코드는 클래스가 아니라 시트 클래스에 배치 해야 합니다 `ThisWorkbook` .

### <a name="to-display-text-in-a-namedrange-control"></a>NamedRange 컨트롤에 텍스트를 표시 하려면

1. 컨트롤의 값 <xref:Microsoft.Office.Tools.Excel.NamedRange> 을 **Hello World**설정 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>네이티브 Excel 범위 사용
 다음 코드는 프로그래밍 방식으로 새 범위를 만든 다음 여기에 값을 할당 합니다.

### <a name="to-display-text-in-an-excel-range"></a>Excel 범위에 텍스트를 표시 하려면

1. 의 **A1** 셀에서 범위를 검색 `Sheet1` 하 고 값을 **Hello World**로 설정 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>참고 항목
- [연습: Windows form을 사용 하 여 데이터 수집](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Office 솔루션 문제 해결](../vsto/troubleshooting-office-solutions.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
