---
title: 프로그래밍 방식으로 문서의 범위 또는 선택 영역 축소
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1575a130a525c169553598fd15acfa8ba8fc397a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546122"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>방법: 프로그래밍 방식으로 문서의 범위 또는 선택 영역 축소
  <xref:Microsoft.Office.Interop.Word.Range> 또는 <xref:Microsoft.Office.Interop.Word.Selection> 개체를 사용하여 작업하는 경우 기존 텍스트를 덮어쓰지 않도록 텍스트를 삽입하기 전에 삽입 지점으로 선택을 변경해야 할 수 있습니다. 및 개체에는 모두 <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> 열거형 값을 사용 하는 Collapse 메서드가 있습니다 <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> .

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> 는 선택 영역의 시작 부분으로 선택을 축소합니다. 열거형 값을 지정하지 않는 경우 이 값이 기본값입니다.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> 는 선택 영역의 끝 부분으로 선택을 축소합니다.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>범위를 축소하고 새 텍스트를 삽입하려면

1. 문서의 첫 번째 단락으로 구성된 <xref:Microsoft.Office.Interop.Word.Range> 개체를 만듭니다.

    다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다.

    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]

    다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 코드에서는 활성 문서를 사용합니다.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]

2. <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> 열거형 값을 사용하여 범위를 축소합니다.

    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]

3. 새 텍스트를 삽입합니다.

    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]

4. <xref:Microsoft.Office.Interop.Word.Range>를 선택합니다.

    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]

   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> 열거형 값을 사용하는 경우 다음 단락 시작 부분에 텍스트가 삽입됩니다.

   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]

   원래 범위에 단락 표식이 포함되어 있으므로 새 문장을 삽입할 때 단락 표식 앞에 삽입되지 않습니다. 자세한 내용은 [방법: 범위를 만들 때 프로그래밍 방식으로 단락 표시 제외](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)를 참조 하세요.

## <a name="document-level-customization-example"></a>문서 수준 사용자 지정 예제

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>문서 수준 사용자 지정의 범위를 축소하려면

1. 다음 예제에서는 문서 수준 사용자 지정의 전체 메서드를 보여 줍니다. 이 코드를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>VSTO 추가 기능에서 범위를 축소 하려면

1. 다음 예제에서는 VSTO 추가 기능의 전체 메서드를 보여 줍니다. 이 코드를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 Word 문서에 텍스트 삽입](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 범위의 시작 및 끝 문자 검색](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [방법: 프로그래밍 방식으로 범위를 만들 때 단락 표시 제외](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [방법: 프로그래밍 방식으로 문서의 범위 확장](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 Word 문서의 범위 다시 설정](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
