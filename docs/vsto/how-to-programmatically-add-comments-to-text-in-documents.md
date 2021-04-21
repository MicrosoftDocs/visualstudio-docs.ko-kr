---
title: '방법: 프로그래밍 방식으로 문서의 텍스트에 메모 추가'
description: 프로그래밍 방식으로 문서의 텍스트에 주석을 추가 합니다. 문서 클래스의 Comments 속성은 Microsoft Word 문서에서 텍스트 범위에 주석을 추가 합니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4e03f189f2236131308b8f9ea5d90c52ffa3147d
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825825"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>방법: 프로그래밍 방식으로 문서의 텍스트에 메모 추가
  문서 클래스의 Comments 속성은 Microsoft Office Word 문서에서 텍스트 범위에 주석을 추가 합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 다음 예제에서는 문서의 첫 번째 단락에 메모를 추가합니다.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 텍스트에 새 메모를 추가하려면

1. <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 속성의 <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> 메서드를 호출하고 범위 및 메모 텍스트를 제공합니다. 다음 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet118":::

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>VSTO 추가 기능에서 텍스트에 새 메모를 추가 하려면

1. <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 속성의 <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> 메서드를 호출하고 범위 및 메모 텍스트를 제공합니다.

     다음 코드 예제에서는 활성 문서에 메모를 추가합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet118":::

## <a name="robust-programming"></a>강력한 프로그래밍
 Word에서 메모에 추가하는 사용자 이니셜을 변경하려면 <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> 속성을 사용합니다.

## <a name="see-also"></a>참조
- [방법: 프로그래밍 방식으로 문서에서 모든 메모 제거](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [문서 호스트 항목](../vsto/document-host-item.md)
