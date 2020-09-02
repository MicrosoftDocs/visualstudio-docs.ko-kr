---
title: 프로그래밍 방식으로 증분 변경 데이터 범위 자동 채우기
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 076381c93d11c2d13bdd89ea5c36c0039e15ef71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547474"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>방법: 프로그래밍 방식으로 증분 변경 데이터로 범위 채우기
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>개체의 메서드를 <xref:Microsoft.Office.Interop.Excel.Range> 사용 하면 값을 사용 하 여 워크시트의 범위를 자동으로 채울 수 있습니다. 가장 자주 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 사용 되는 메서드는 증분 방식으로 증가 하거나 감소 하는 범위에 값을 저장 하는 데 사용 됩니다. 열거형에서 선택적 상수를 제공 하 여 동작을 지정할 수 있습니다 <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 다음을 사용할 때 두 범위를 지정 해야 합니다 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> .

- <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>채우기의 시작 지점을 지정 하 고 초기 값을 포함 하는 메서드를 호출 하는 범위입니다.

- 채우려는 범위 이며, 메서드에 매개 변수로 전달 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 됩니다. 이 대상 범위는 초기 값을 포함 하는 범위를 포함 해야 합니다.

    > [!NOTE]
    > 대신 컨트롤을 전달할 수 없습니다 <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Interop.Excel.Range> . 자세한 내용은 [호스트 항목 및 호스트 컨트롤의 프로그래밍](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)에 대 한 제한 사항을 참조 하세요.

## <a name="example"></a>예
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>코드 컴파일
 채우려는 범위의 첫 번째 셀에는 초기 값이 포함 되어야 합니다.

 이 예에서는 다음과 같은 세 개의 지역을 채워야 합니다.

- 열 B는 평일 5 개를 포함 합니다. 초기 값에 대해 B1 셀에 **월요일** 을 입력 합니다.

- 열 C는 5 개월을 포함 합니다. 초기 값에 대해 셀 C1에 **1 월** 을 입력 합니다.

- 열 D는 각 행에 대해 2 씩 증가 하는 일련의 숫자를 포함 하는 것입니다. 초기 값에 대해 D1 셀에 **4** 를 입력 하 고 D2 셀에 **6** 을 입력 합니다.

## <a name="see-also"></a>추가 정보
- [범위 작업](../vsto/working-with-ranges.md)
- [방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [방법: 프로그래밍 방식으로 통합 문서의 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [방법: 프로그래밍 방식으로 Excel 계산 실행](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
