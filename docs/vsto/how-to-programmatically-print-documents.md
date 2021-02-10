---
title: '방법: 프로그래밍 방식으로 문서 인쇄'
description: 전체 Microsoft Word 문서 또는 문서의 일부를 기본 프린터에 인쇄 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c81e22bbf3af08c150f1e1156ee62f1666f59638
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956635"
---
# <a name="how-to-programmatically-print-documents"></a>방법: 프로그래밍 방식으로 문서 인쇄
  전체 Microsoft Office Word 문서 또는 일부 문서를 기본 프린터에 인쇄할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>문서 수준 사용자 지정의 일부인 문서 인쇄

### <a name="to-print-the-entire-document"></a>전체 문서를 인쇄하려면

1. 프로젝트의 <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> 클래스의 `ThisDocument` 메서드를 호출하여 전체 문서를 인쇄합니다. 이 예제를 사용하려면 `ThisDocument` 클래스에서 코드를 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]

### <a name="to-print-the-current-page-of-the-document"></a>문서의 현재 페이지를 인쇄하려면

1. 프로젝트의 <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> 클래스의 `ThisDocument` 메서드를 호출하고 현재 페이지의 복사본 하나를 인쇄하도록 지정합니다. 이 예제를 사용하려면 `ThisDocument` 클래스에서 코드를 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]

## <a name="print-a-document-by-using-a-vsto-add-in"></a>VSTO 추가 기능을 사용 하 여 문서 인쇄

### <a name="to-print-an-entire-document"></a>전체 문서를 인쇄하려면

1. 인쇄하려는 <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> 개체의 <xref:Microsoft.Office.Interop.Word.Document> 메서드를 호출합니다. 다음 코드 예제에서는 활성 문서를 인쇄합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 코드를 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]

### <a name="to-print-the-current-page-of-a-document"></a>문서의 현재 페이지를 인쇄하려면

1. 인쇄하려는 <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> 개체의 <xref:Microsoft.Office.Interop.Word.Document> 메서드를 호출하고 현재 페이지의 복사본 하나를 인쇄하도록 지정합니다. 다음 코드 예제에서는 활성 문서를 인쇄합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 코드를 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]

## <a name="see-also"></a>참고 항목
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
