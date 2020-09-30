---
title: 프로그래밍 방식으로 문서와 문서 부분 보호
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: beab8c2e1b18d56dc7b71688e0ff2ec5b74ac596
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584848"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>방법: 프로그래밍 방식으로 문서 및 문서 부분 보호
  Microsoft Office Word 문서에 보호를 추가하여 사용자의 문서 편집을 방지할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 또한 지정된 사용자가 문서에서 해당 영역만 편집할 수 있도록 특정 문서 영역을 예외로 표시할 수도 있습니다. 예를 들어 특정 책갈피를 제외한 전체 문서를 보호할 수 있습니다. 암호를 모를 경우 사용자가 문서 보호를 제거할 수 없도록 암호를 추가할 수도 있습니다.

> [!NOTE]
> 다음 예제에서는 암호 보호를 사용하지 않지만 문서 보호 추가 시 암호를 사용할 수 있습니다. 자세한 내용은 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)에서 문서 보호기 샘플을 참조 하세요.

 또한 콘텐츠 컨트롤을 사용하여 문서 부분을 보호할 수 있습니다. 자세한 내용은 [방법: 콘텐츠 컨트롤을 사용 하 여 문서 부분 보호](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)를 참조 하세요.

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>문서 수준 사용자 지정의 일부인 문서 보호

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>문서 수준 사용자 지정의 일부인 문서를 보호하려면

1. 프로젝트에서 <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> 클래스의 `ThisDocument` 메서드를 호출합니다.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>문서 보호에서 책갈피 컨트롤을 제외하려면

1. <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> 메서드를 사용하여 전체 문서를 보호합니다.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

2. 문서 보호에서 `Bookmark1` 을 제외합니다.

     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]

### <a name="compile-the-code"></a>코드 컴파일
 이러한 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다. 이러한 코드 예제에서는 이 코드가 나타나는 문서에 <xref:Microsoft.Office.Tools.Word.Bookmark> 이라는 기존 `Bookmark1` 컨트롤이 있다고 가정합니다.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>VSTO 추가 기능을 사용 하 여 문서 보호

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>애플리케이션 수준 VSTO 추가 기능을 사용하여 문서를 보호하려면

1. 보호하려는 <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> 의 <xref:Microsoft.Office.Interop.Word.Document> 메서드를 호출합니다.

     다음 코드 예제에서는 활성 문서를 보호합니다. 이 코드 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]

## <a name="see-also"></a>참고 항목
- [문서 수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)
- [Office 문서에 대 한 암호 보호](../vsto/password-protection-on-office-documents.md)
- [방법: 제한 된 권한으로 문서 뒤에 코드를 실행할 수 있도록 허용](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [방법: Word 문서에 책갈피 컨트롤 추가](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
