---
title: '방법: 프로그래밍 방식으로 워크시트 숨기기'
description: 워크시트 호스트 항목을 사용 하 여 Microsoft Excel 통합 문서에서 프로그래밍 방식으로 워크시트를 표시 하거나 숨길 수 있는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b859ea468db86d57347553f9fd10b44fea99026b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826475"
---
# <a name="how-to-programmatically-hide-worksheets"></a>방법: 프로그래밍 방식으로 워크시트 숨기기
  통합 문서의 모든 워크시트를 표시하거나 숨길 수 있습니다. 워크시트를 숨기려면 워크시트 호스트 항목을 사용하거나 통합 문서의 시트 컬렉션을 통해 워크시트에 액세스합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>워크시트 호스트 항목 사용
 문서 수준 사용자 지정에서 디자인 타임에 워크시트가 추가된 경우 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 속성을 사용하여 지정된 워크시트를 숨깁니다.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>워크시트 호스트 항목을 사용하여 워크시트를 숨기려면

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 호스트 항목의 `Sheet1` 속성을 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 열거형 값으로 설정합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet25":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel 통합 문서의 시트 컬렉션 사용
 다음과 같은 경우 Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> 컬렉션을 통해 워크시트에 액세스합니다.

- VSTO 추가 기능에서 워크시트를 숨기려고 합니다.

- 숨기려는 워크시트는 문서 수준 사용자 지정에서 런타임에 생성되었습니다.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Excel 통합 문서의 시트 컬렉션을 사용하여 워크시트를 숨기려면

1. 워크시트의 <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> 속성을 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 열거형 값으로 설정합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet26":::

## <a name="see-also"></a>참조
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에서 워크시트 삭제](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 내에서 워크시트 이동](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
