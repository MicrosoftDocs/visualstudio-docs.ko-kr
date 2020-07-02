---
title: '방법: 프로그래밍 방식으로 문서에서 찾은 항목 반복'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e200f910e002bb9380bd5a1b556dc6f1cab08810
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544744"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>방법: 프로그래밍 방식으로 문서에서 찾은 항목 반복
  클래스에는 <xref:Microsoft.Office.Interop.Word.Find> <xref:Microsoft.Office.Interop.Word.Find.Found%2A> 검색 된 항목을 찾을 때마다 **true** 를 반환 하는 속성이 있습니다. <xref:Microsoft.Office.Interop.Word.Range> 메서드를 사용하여 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 에서 찾은 모든 인스턴스를 순환 검색할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>찾은 항목을 순환 검색하려면

1. <xref:Microsoft.Office.Interop.Word.Range> 개체를 선언합니다.

    다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다.

    [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]

    다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 예제에서는 활성 문서를 사용합니다.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]

2. 루프에서 <xref:Microsoft.Office.Interop.Word.Find.Found%2A> 속성을 사용하여 문서의 문자열 항목을 모두 검색하고 문자열을 찾을 때마다 정수 변수를 1씩 증분합니다.

    [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
    [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]

3. 메시지 상자에는 문자열이 발견된 횟수가 표시됩니다.

    [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
    [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]

   다음 예제에서는 전체 메서드를 보여 줍니다.

## <a name="document-level-customization-example"></a>문서 수준 사용자 지정 예제

### <a name="to-loop-through-items-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 항목을 순환 검색하려면

1. 다음 예제에서는 문서 수준 사용자 지정의 전체 코드를 보여 줍니다. 이 코드를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>VSTO 추가 기능에서 항목을 반복 하려면

1. 다음 예제에서는 VSTO 추가 기능의 전체 코드를 보여 줍니다. 이 코드를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]

## <a name="see-also"></a>참고 항목
- [방법: 프로그래밍 방식으로 문서에서 uiresources.rext 검색 및 바꾸기](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [방법: 프로그래밍 방식으로 Word에서 검색 옵션 설정](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 검색 후 선택 영역 복원](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
