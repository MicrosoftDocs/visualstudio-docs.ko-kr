---
title: '방법: 프로그래밍 방식으로 문서에 머리글 및 바닥글 추가'
description: 섹션의 Headers 속성 및 바닥글 속성을 사용 하 여 문서의 머리글 및 바닥글에 텍스트를 추가 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 73844d19ef6bb85c623706ab0d359836e42a3b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828748"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>방법: 프로그래밍 방식으로 문서에 머리글 및 바닥글 추가
  <xref:Microsoft.Office.Interop.Word.Section>의 <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> 속성 및 <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> 속성을 사용하여 문서의 머리글 및 바닥글에 텍스트를 추가할 수 있습니다. 문서의 각 섹션에는 다음 세 개의 머리글과 바닥글이 포함됩니다.

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  문서 수준 사용자 지정 및 VSTO 추가 기능에 대한 절차가 서로 다릅니다.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>문서 수준 사용자 지정
 다음 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

### <a name="to-add-text-to-footers-in-the-document"></a>문서의 바닥글에 텍스트를 추가하려면

1. 다음 코드 예제에서는 문서의 각 섹션에 대한 기본 바닥글에 삽입할 텍스트의 글꼴을 설정하고 바닥글에 텍스트를 삽입합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>문서의 머리글에 텍스트를 추가하려면

1. 다음 코드 예제에서는 문서의 각 머리글에 페이지 번호를 표시할 필드를 추가하고 텍스트가 머리글 오른쪽에 정렬되도록 단락 맞춤을 설정합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet116":::

## <a name="vsto-add-ins"></a>VSTO 추가 기능
 다음 코드 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

### <a name="to-add-text-to-footers-in-a-document"></a>문서의 바닥글에 텍스트를 추가하려면

1. 다음 코드 예제에서는 문서의 각 섹션에 대한 기본 바닥글에 삽입할 텍스트의 글꼴을 설정하고 바닥글에 텍스트를 삽입합니다. 이 코드 예제에서는 활성 문서를 사용합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>문서의 머리글에 텍스트를 추가하려면

1. 다음 코드 예제에서는 문서의 각 머리글에 페이지 번호를 표시할 필드를 추가하고 텍스트가 머리글 오른쪽에 정렬되도록 단락 맞춤을 설정합니다. 이 코드 예제에서는 활성 문서를 사용합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet116":::

## <a name="see-also"></a>참조
- [방법: 프로그래밍 방식으로 새 문서 만들기](../vsto/how-to-programmatically-create-new-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 확장](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 문서에서 찾은 항목 반복](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
