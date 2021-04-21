---
title: '방법: 프로그래밍 방식으로 문서의 텍스트 서식 지정'
description: Range 개체를 사용 하 여 프로그래밍 방식으로 Microsoft Word 문서에서 텍스트의 서식을 지정 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b91486c193b7b3fdba3b4c5cbbe86f58ffa7f06c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827879"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>방법: 프로그래밍 방식으로 문서의 텍스트 서식 지정
  <xref:Microsoft.Office.Interop.Word.Range> 개체를 사용하여 Microsoft Office Word 문서의 텍스트에 서식을 지정할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 다음 예제에서는 문서의 첫 번째 단락을 선택하고 글꼴 크기, 글꼴 이름 및 맞춤을 변경합니다. 그런 다음 범위를 선택하고 메시지 상자를 표시하여 코드의 다음 섹션을 실행하기 전에 일시 중지합니다. 다음 섹션에서는 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목 (문서 수준 사용자 지정의 경우) 또는 <xref:Microsoft.Office.Interop.Word.Document> 클래스 (VSTO 추가 기능의 경우)의 Undo 메서드를 세 번 호출 합니다. 표준 들여쓰기 스타일을 적용하고 메시지 상자를 표시하여 코드를 일시 중지합니다. 그런 다음 코드에서 <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> 메서드를 한 번 호출하고 메시지 상자를 표시합니다.

## <a name="document-level-customization-example"></a>문서 수준 사용자 지정 예제

### <a name="to-format-text-using-a-document-level-customization"></a>문서 수준 사용자 지정을 사용하여 텍스트의 서식을 지정하려면

1. 다음 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다. 이 코드를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet62":::

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="to-format-text-using-a-vsto-add-in"></a>VSTO 추가 기능을 사용하여 텍스트의 서식을 지정하려면

1. 다음 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 예제에서는 활성 문서를 사용합니다. 이 코드를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet62":::

## <a name="see-also"></a>참조
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 Word 문서에 텍스트 삽입](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [방법: 프로그래밍 방식으로 문서에서 텍스트 검색 및 바꾸기](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
