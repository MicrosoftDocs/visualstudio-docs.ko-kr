---
title: '방법: 프로그래밍 방식으로 문서에서 텍스트 숨기기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dae19d196f830e5187fa395473c0a5482cb1d03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543314"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>방법: 프로그래밍 방식으로 문서에서 텍스트 숨기기
  텍스트의 특정 범위에 대해 <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> 의 <xref:Microsoft.Office.Interop.Word.Range.Font%2A> 속성을 설정하여 문서에서 텍스트를 숨길 수 있습니다.

 예를 들어 문서 <xref:Microsoft.Office.Tools.Word.Bookmark> 를 프린터로 보내기 전에 (문서 수준 사용자 지정) 또는 <xref:Microsoft.Office.Interop.Word.Bookmark> (VSTO 추가 기능) 내의 텍스트를 일시적으로 숨길 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>문서를 인쇄하는 동안 책갈피 컨트롤에서 텍스트를 숨기려면

1. 지정된 범위에 있는 모든 텍스트를 숨기는 프로시저를 만듭니다.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. 지정된 범위에 있는 모든 텍스트를 표시하는 프로시저를 만듭니다.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. 책갈피의 범위를 `HideText` 메서드로 전달하고, 문서를 인쇄한 다음 동일한 범위를 `UnhideText` 메서드로 전달합니다.

     다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다. 이 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 예제에서는 활성 문서를 사용합니다. 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>코드 컴파일
 이 코드 예제에서는 문서에 <xref:Microsoft.Office.Tools.Word.Bookmark> 이라는 컨트롤 (문서 수준 사용자 지정) 또는 <xref:Microsoft.Office.Interop.Word.Bookmark> 컨트롤 (VSTO 추가 기능)이 포함 되어 있다고 가정 `bookmark1` 합니다.

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 문서 인쇄](../vsto/how-to-programmatically-print-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 Word 문서의 범위 다시 설정](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [방법: 프로그래밍 방식으로 책갈피 텍스트 업데이트](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
