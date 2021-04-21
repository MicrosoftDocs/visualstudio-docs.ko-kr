---
title: '방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택'
description: Range 개체를 사용 하 여 Microsoft Word 문서에서 프로그래밍 방식으로 범위를 정의 하 고 선택 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3a5dc0c7fb9f3e9a2b4a15447f81239db973c215
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825955"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택
  <xref:Microsoft.Office.Interop.Word.Range> 개체를 사용하여 Microsoft Office Word 문서의 범위를 정의할 수 있습니다. 예를 들어 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 개체의 메서드를 사용 <xref:Microsoft.Office.Interop.Word.Range> 하거나 <xref:Microsoft.Office.Tools.Word.Document> 클래스 (문서 수준 사용자 지정) 또는 <xref:Microsoft.Office.Interop.Word.Document> 클래스 (VSTO 추가 기능)의 Content 속성을 사용 하 여 여러 가지 방법으로 전체 문서를 선택할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>범위 정의
 다음 예제에서는 인쇄할 수 없는 문자를 비롯하여 활성 문서의 처음 7자를 포함하는 새로운 <xref:Microsoft.Office.Interop.Word.Range> 개체를 만드는 방법을 보여 줍니다. 그런 다음 범위 내의 텍스트를 선택합니다.

### <a name="to-define-a-range-in-a-document-level-customization"></a>문서 수준 사용자 지정의 범위를 정의하려면

1. <xref:Microsoft.Office.Tools.Word.Document> 클래스의 <xref:Microsoft.Office.Tools.Word.Document.Range%2A> 메서드에 시작 및 끝 문자를 전달하여 문서에 범위를 추가합니다. 이 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet18":::

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>VSTO 추가 기능을 사용하여 범위를 정의하려면

1. <xref:Microsoft.Office.Interop.Word.Document> 클래스의 <xref:Microsoft.Office.Interop.Word._Document.Range%2A> 메서드에 시작 및 끝 문자를 전달하여 문서에 범위를 추가합니다. 다음 코드 예제에서는 활성 문서에 범위를 추가합니다. 이 코드 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet18":::

## <a name="select-a-range-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 범위를 선택 합니다.
 다음 예제에서는 <xref:Microsoft.Office.Interop.Word.Range> 개체의 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 메서드를 사용하거나 <xref:Microsoft.Office.Tools.Word.Document> 클래스의 <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 속성을 사용하여 전체 문서를 선택하는 방법을 보여 줍니다.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Select 메서드를 사용하여 전체 문서를 범위로 선택하려면

1. 전체 문서를 포함하는 <xref:Microsoft.Office.Interop.Word.Range>의 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 메서드를 사용합니다. 다음 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>콘텐츠 속성을 사용하여 전체 문서를 범위로 선택하려면

1. <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 속성을 사용하여 전체 문서를 포함하는 범위를 정의합니다.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet20":::

   다른 개체의 메서드와 속성을 사용하여 범위를 정의할 수도 있습니다.

### <a name="to-select-a-sentence-in-the-active-document"></a>활성 문서에서 문장을 선택하려면

1. <xref:Microsoft.Office.Interop.Word.Sentences> 컬렉션을 사용하여 범위를 설정합니다. 선택하려는 문장의 인덱스를 사용합니다.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet21":::

   문장을 선택하는 다른 방법은 범위의 시작 및 끝 값을 수동으로 설정하는 것입니다.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>시작 및 끝 값을 수동으로 설정하여 문장을 선택하려면

1. 범위 변수를 만듭니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet23":::

2. 문서에 두 개 이상의 문장이 있는지 확인 하 고 범위의 *시작* 및 *끝* 인수를 설정한 다음 범위를 선택 합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet24":::

## <a name="select-a-range-by-using-a-vsto-add-in"></a>VSTO 추가 기능을 사용 하 여 범위 선택
 다음 예제에서는 <xref:Microsoft.Office.Interop.Word.Range> 개체의 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 메서드를 사용하거나 <xref:Microsoft.Office.Interop.Word.Document> 클래스의 <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 속성을 사용하여 전체 문서를 선택하는 방법을 보여 줍니다.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Select 메서드를 사용하여 전체 문서를 범위로 선택하려면

1. 전체 문서를 포함하는 <xref:Microsoft.Office.Interop.Word.Range>의 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 메서드를 사용합니다. 다음 코드 예제에서는 활성 문서의 내용을 선택합니다. 이 코드 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>콘텐츠 속성을 사용하여 전체 문서를 범위로 선택하려면

1. <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 속성을 사용하여 전체 문서를 포함하는 범위를 정의합니다.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet20":::

   다른 개체의 메서드와 속성을 사용하여 범위를 정의할 수도 있습니다.

### <a name="to-select-a-sentence-in-the-active-document"></a>활성 문서에서 문장을 선택하려면

1. <xref:Microsoft.Office.Interop.Word.Sentences> 컬렉션을 사용하여 범위를 설정합니다. 선택하려는 문장의 인덱스를 사용합니다.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet21":::

   문장을 선택하는 다른 방법은 범위의 시작 및 끝 값을 수동으로 설정하는 것입니다.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>시작 및 끝 값을 수동으로 설정하여 문장을 선택하려면

1. 범위 변수를 만듭니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet23":::

2. 문서에 두 개 이상의 문장이 있는지 확인 하 고 범위의 *시작* 및 *끝* 인수를 설정한 다음 범위를 선택 합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet24":::

## <a name="see-also"></a>참조
- [Word 개체 모델 개요](../vsto/word-object-model-overview.md)
- [방법: 프로그래밍 방식으로 문서의 범위 확장](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 범위의 시작 및 끝 문자 검색](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [방법: 프로그래밍 방식으로 문서의 범위 확장](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 Word 문서의 범위 다시 설정](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 또는 선택 영역 축소](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [방법: 프로그래밍 방식으로 범위를 만들 때 단락 표시 제외](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
