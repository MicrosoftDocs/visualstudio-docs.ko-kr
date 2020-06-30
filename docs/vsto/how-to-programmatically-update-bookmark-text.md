---
title: '방법: 프로그래밍 방식으로 책갈피 텍스트 업데이트'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b76c239606a4bf0d6da203bd4eea45a11162706
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546954"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>방법: 프로그래밍 방식으로 책갈피 텍스트 업데이트
  나중에 텍스트를 검색할 수 있도록 또는 책갈피의 텍스트를 바꾸기 위해 Microsoft Office Word 문서의 자리 표시자 책갈피에 텍스트를 삽입할 수 있습니다. 문서 수준 사용자 지정을 개발하는 경우 데이터에 바인딩된 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤의 텍스트를 업데이트할 수도 있습니다. 자세한 내용은 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)을 참조 하세요.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 책갈피 개체는 다음 두 형식 중 하나일 수 있습니다.

- <xref:Microsoft.Office.Tools.Word.Bookmark> 호스트 컨트롤.

   <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤은 데이터 바인딩을 사용하도록 설정하고 이벤트를 노출하여 네이티브 <xref:Microsoft.Office.Interop.Word.Bookmark> 개체를 확장합니다. 호스트 컨트롤에 대 한 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

- 네이티브 <xref:Microsoft.Office.Interop.Word.Bookmark> 개체입니다.

   <xref:Microsoft.Office.Interop.Word.Bookmark> 개체에는 이벤트 또는 데이터 바인딩 기능이 없습니다.

  책갈피에 텍스트를 할당하는 경우 <xref:Microsoft.Office.Interop.Word.Bookmark> 및 <xref:Microsoft.Office.Tools.Word.Bookmark> 간에 동작이 다릅니다. 자세한 내용은 [책갈피 컨트롤](../vsto/bookmark-control.md)을 참조 하세요.

## <a name="use-host-controls"></a>호스트 컨트롤 사용

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>책갈피 컨트롤을 사용하여 책갈피 내용을 업데이트하려면

1. 책갈피 이름에 대해 `bookmark` 인수를 사용하고 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 속성에 할당할 문자열에 대해 `newText` 인수를 사용하는 프로시저를 만듭니다.

    > [!NOTE]
    > <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤의 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 또는 <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> 속성에 텍스트를 할당하면 책갈피가 삭제되지 않습니다.

     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]

2. *NewText* 문자열을의 속성에 할당 합니다 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> .

     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]

## <a name="use-word-objects"></a>Word 개체 사용

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Word 책갈피 개체를 사용하여 책갈피 내용을 업데이트하려면

1. <xref:Microsoft.Office.Interop.Word.Bookmark>의 이름에 대해 `bookmark` 인수를 사용하고 책갈피의 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 속성에 할당할 문자열에 대해 `newText` 인수를 사용하는 프로시저를 만듭니다.

    > [!NOTE]
    > 네이티브 Word <xref:Microsoft.Office.Interop.Word.Bookmark> 개체에 텍스트를 할당하면 책갈피가 삭제됩니다.

     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]

2. 책갈피를 *newText* <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 자동으로 삭제 하는 책갈피의 속성에 newText 문자열을 할당 합니다. 그런 후 <xref:Microsoft.Office.Interop.Word.Bookmarks> 컬렉션에 책갈피를 다시 추가합니다.

     다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다.

     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]

     다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 예제에서는 활성 문서를 사용합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]

## <a name="see-also"></a>참고 항목
- [방법: 프로그래밍 방식으로 Word 문서에 텍스트 삽입](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Word 개체 모델 개요](../vsto/word-object-model-overview.md)
- [책갈피 컨트롤](../vsto/bookmark-control.md)
