---
title: '방법: 프로그래밍 방식으로 Word 문서에 텍스트 삽입'
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aef597099964333771fd488e0541b4ea4daf4553
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541507"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>방법: 프로그래밍 방식으로 Word 문서에 텍스트 삽입
  Microsoft Office Word 문서에 텍스트를 삽입하는 기본 방법에는 다음 세 가지가 있습니다.

- 범위에 텍스트를 삽입합니다.

- 범위의 텍스트를 새 텍스트로 바꿉니다.

- <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 개체의 <xref:Microsoft.Office.Interop.Word.Selection> 메서드를 사용하여 커서 또는 선택 영역에 텍스트를 삽입합니다.

> [!NOTE]
> 콘텐츠 컨트롤 및 책갈피에 텍스트를 삽입할 수도 있습니다. 자세한 내용은 [콘텐츠 컨트롤](../vsto/content-controls.md) 및 [책갈피 컨트롤](../vsto/bookmark-control.md)을 참조 하세요.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>범위에 텍스트 삽입
 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 개체의 <xref:Microsoft.Office.Interop.Word.Range> 속성을 사용하여 문서에 텍스트를 삽입합니다.

### <a name="to-insert-text-in-a-range"></a>범위에 텍스트를 삽입하려면

1. 문서의 시작 부분에 범위를 지정하고 **New Text**텍스트를 삽입합니다.

     다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다.

     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]

     다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 코드에서는 활성 문서를 사용합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]

2. 1자에서 삽입된 텍스트의 길이까지 확장된 <xref:Microsoft.Office.Interop.Word.Range> 개체를 선택합니다.

     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]

## <a name="replace-text-in-a-range"></a>범위에서 텍스트 바꾸기
 지정된 범위에 텍스트가 포함되어 있는 경우 범위에 있는 모든 텍스트가 삽입된 텍스트로 바뀝니다.

### <a name="to-replace-text-in-a-range"></a>범위의 텍스트를 바꾸려면

1. 문서의 처음 12자로 구성된 <xref:Microsoft.Office.Interop.Word.Range> 개체를 만듭니다.

     다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다.

     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]

     다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 코드에서는 활성 문서를 사용합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]

2. 이러한 문자를 **New Text**문자열로 바꿉니다.

     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]

3. 범위를 선택합니다.

     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]

## <a name="insert-text-using-typetext"></a>TypeText를 사용 하 여 텍스트 삽입
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 메서드는 선택 영역에 텍스트를 삽입합니다. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 는 사용자 컴퓨터에 설정된 옵션에 따라 다르게 동작합니다. 다음 프로시저의 코드에서는 <xref:Microsoft.Office.Interop.Word.Selection> 개체 변수를 선언하고 **Overtype** 옵션이 설정된 경우 해제합니다. **Overtype** 옵션이 활성화된 경우 커서 옆에 있는 텍스트를 모두 덮어씁니다.

### <a name="to-insert-text-using-the-typetext-method"></a>TypeText 메서드를 사용하여 텍스트를 삽입하려면

1. <xref:Microsoft.Office.Interop.Word.Selection> 개체 변수를 선언합니다.

    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]

2. **Overtype** 옵션이 설정된 경우 해제합니다.

    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]

3. 현재 선택 영역이 삽입 지점인지 테스트합니다.

    삽입 지점이면 코드가 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>를 사용하여 문장을 삽입하고 <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> 메서드를 사용하여 단락 표시를 삽입합니다.

    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]

4. **ElseIf** 블록의 코드에서는 선택이 일반 선택인지 테스트합니다. 일반 선택이면 다른 **If** 블록에서 **ReplaceSelection** 옵션이 설정되었는지 테스트합니다. 일반 선택이면 코드에서 선택 영역의 <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> 메서드를 사용하여 선택 영역을 선택한 텍스트 블록의 시작 부분에 있는 삽입 지점으로 축소합니다. 텍스트와 단락 표시를 삽입합니다.

    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]

5. 선택 영역이 삽입 지점 또는 선택한 텍스트 블록이 아니면 **Else** 블록의 코드에서 아무 작업도 수행하지 않습니다.

    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]

   <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> <xref:Microsoft.Office.Interop.Word.Selection> 키보드의 **백스페이스** 키 기능을 모방 하는 개체의 메서드를 사용할 수도 있습니다. 그러나 텍스트 삽입 및 조작의 경우 <xref:Microsoft.Office.Interop.Word.Range> 개체가 더 많은 제어를 제공합니다.

   다음 예제에서는 전체 코드를 보여 줍니다. 이 예제를 사용하려면 프로젝트의 `ThisDocument` 또는 `ThisAddIn` 클래스에서 코드를 실행합니다.

   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 문서의 텍스트 서식 지정](../vsto/how-to-programmatically-format-text-in-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 확장](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
