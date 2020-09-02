---
title: '방법: 프로그래밍 방식으로 워크시트 범위에서 텍스트 검색'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d35d24f9132a9b279316b53fbb13e3bfa094994
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547032"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>방법: 프로그래밍 방식으로 워크시트 범위에서 텍스트 검색
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>개체의 메서드를 <xref:Microsoft.Office.Interop.Excel.Range> 사용 하 여 범위 내에서 텍스트를 검색할 수 있습니다. 이 텍스트는 또는와 같은 워크시트 셀에 나타날 수 있는 오류 문자열 일 수도 있습니다 `#NULL!` `#VALUE!` . 오류 문자열에 대 한 자세한 내용은 [셀 오류 값](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values)을 참조 하세요.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 다음 예에서는 라는 범위를 검색 `Fruits` 하 고 "사과" 라는 단어를 포함 하는 셀의 글꼴을 수정 합니다. 또한이 절차에서는 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 이전에 설정한 검색 설정을 사용 하 여 검색을 반복 하는 메서드를 사용 합니다. 검색 하기 전에 셀을 지정 하면 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 메서드는 나머지를 처리 합니다.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>메서드의 검색은 범위의 끝에 도달한 후 검색 범위의 시작 부분으로 다시 래핑됩니다. 코드가 무한 루프에서 검색 되지 않는지 확인 해야 합니다. 예제 절차에서는 속성을 사용 하 여이를 처리 하는 한 가지 방법을 보여 줍니다 <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> .

## <a name="to-search-for-text-in-a-worksheet-range"></a>워크시트 범위에서 텍스트를 검색 하려면

1. 전체 범위, 첫 번째 찾은 범위 및 현재 발견 된 범위를 추적 하기 위한 변수를 선언 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. 첫 번째 일치 항목을 검색 하 여 이후에 검색할 셀을 제외한 모든 매개 변수를 지정 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. 일치가 있으면 계속 검색 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. 첫 번째 찾은 범위 ( `firstFind` )를 **Nothing**과 비교 합니다. `firstFind`에 값이 없으면 코드는 찾은 범위 ()를 저장 합니다 `currentFind` .

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. 찾은 범위의 주소가 첫 번째 찾은 범위의 주소와 일치 하는 경우 루프를 종료 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. 찾은 범위의 모양을 설정 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. 다른 검색을 수행 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   다음 예제에서는 전체 메서드를 보여 줍니다.

## <a name="example"></a>예제
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>참고 항목
- [범위 작업](../vsto/working-with-ranges.md)
- [방법: 프로그래밍 방식으로 통합 문서의 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
