---
title: 프로그래밍 방식으로 문서에서 텍스트 찾기 및 바꾸기
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 18a50d6d4ef52a0c50be0b72b4cab5706da4e2db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547045"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>방법: 프로그래밍 방식으로 문서에서 텍스트 검색 및 바꾸기
  <xref:Microsoft.Office.Interop.Word.Find> 개체는 <xref:Microsoft.Office.Interop.Word.Selection> 및 <xref:Microsoft.Office.Interop.Word.Range> 개체 둘 다의 멤버이며, 둘 중 하나를 사용하여 Microsoft Office Word 문서에서 텍스트를 검색할 수 있습니다. 바꾸기 명령은 찾기 명령의 확장입니다.

 <xref:Microsoft.Office.Interop.Word.Find> 개체를 사용하여 Microsoft Office Word 문서를 반복하고 특정 텍스트, 서식 또는 스타일을 검색한 다음 <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> 속성을 사용하여 찾은 항목을 바꿉니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Selection 개체 사용
 <xref:Microsoft.Office.Interop.Word.Selection> 개체를 사용하여 텍스트를 찾는 경우 지정한 검색 조건은 현재 선택한 텍스트에 대해서만 적용됩니다. <xref:Microsoft.Office.Interop.Word.Selection>이 삽입 지점이면 문서가 검색됩니다. 검색 조건과 일치하는 항목이 발견되면 자동으로 선택됩니다.

 <xref:Microsoft.Office.Interop.Word.Find> 조건은 누적되며, 이는 조건이 이전 검색 조건에 추가됨을 의미합니다. 검색 전에 <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> 메서드를 사용하여 이전 검색의 서식을 지웁니다.

### <a name="to-find-text-using-a-selection-object"></a>Selection 개체를 사용하여 텍스트를 찾으려면

1. 변수에 검색 문자열을 할당합니다.

    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]

2. 이전 검색의 서식을 지웁니다.

    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]

3. 검색을 실행하고 결과가 포함된 메시지 상자를 표시합니다.

    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]

   다음 예제에서는 전체 메서드를 보여 줍니다.

   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]

## <a name="use-a-range-object"></a>Range 개체 사용
 <xref:Microsoft.Office.Interop.Word.Range> 개체를 사용하면 사용자 인터페이스에 아무것도 표시하지 않고 텍스트를 검색할 수 있습니다. <xref:Microsoft.Office.Interop.Word.Find>검색 조건과 일치 하는 텍스트를 찾은 경우 개체는 **True** 를 반환 하 고 그렇지 않으면 **False** 를 반환 합니다. 또한 텍스트가 발견되는 경우 검색 조건과 일치하도록 <xref:Microsoft.Office.Interop.Word.Range> 개체를 다시 정의합니다.

### <a name="to-find-text-using-a-range-object"></a>Range 개체를 사용하여 텍스트를 찾으려면

1. 문서의 두 번째 단락으로 구성된 <xref:Microsoft.Office.Interop.Word.Range> 개체를 정의합니다.

    다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다.

    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]

    다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 예제에서는 활성 문서를 사용합니다.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]

2. 개체의 속성을 사용 하 여 <xref:Microsoft.Office.Interop.Word.Range.Find%2A> <xref:Microsoft.Office.Interop.Word.Range> 먼저 기존 서식 지정 옵션을 지운 다음 문자열 **찾기**를 검색 합니다.

    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]

3. 메시지 상자에 검색 결과를 표시하고 <xref:Microsoft.Office.Interop.Word.Range>를 선택하여 표시되도록 합니다.

    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]

    검색에 실패하면 두 번째 단락이 선택됩니다. 성공하면 검색 조건이 표시됩니다.

   다음 예제에서는 문서 수준 사용자 지정의 전체 코드를 보여 줍니다. 이 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 코드를 실행합니다.

   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]

   다음 예제에서는 VSTO 추가 기능의 전체 코드를 보여 줍니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 코드를 실행합니다.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]

## <a name="search-for-and-replace-text-in-documents"></a>문서에서 텍스트 검색 및 바꾸기
 다음 코드는 현재 선택 영역을 검색 하 여 **찾은 문자열의** 모든 항목을 **찾은**문자열로 바꿉니다.

### <a name="to-search-for-and-replace-text-in-documents"></a>문서에서 텍스트를 검색하고 바꾸려면

1. 프로젝트의 `ThisDocument` 또는 `ThisAddIn` 클래스에 다음 예제 코드를 추가합니다.

     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]

     <xref:Microsoft.Office.Interop.Word.Find> 클래스에는 <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> 메서드가 있고 <xref:Microsoft.Office.Interop.Word.Replacement> 클래스에도 자체 <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> 메서드가 있습니다. 찾기 및 바꾸기 작업을 수행 하는 경우 두 개체의 ClearFormatting 지정 메서드를 사용 해야 합니다. <xref:Microsoft.Office.Interop.Word.Find> 개체에서만 사용하는 경우 대체 텍스트에서 예기치 않은 결과가 발생할 수 있습니다.

2. <xref:Microsoft.Office.Interop.Word.Find> 개체의 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 메서드를 사용하여 찾은 각 항목을 바꿉니다. 바꿀 항목을 지정 하려면 *replace* 매개 변수를 사용 합니다. 이 매개 변수는 다음 <xref:Microsoft.Office.Interop.Word.WdReplace> 값 중 하나일 수 있습니다.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll>은 찾은 항목을 모두 바꿉니다.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone>은 찾은 항목을 바꾸지 않습니다.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne>은 찾은 첫 번째 항목을 바꿉니다.

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 Word에서 검색 옵션 설정](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [방법: 프로그래밍 방식으로 문서에서 찾은 항목 반복](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 검색 후 선택 영역 복원](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
