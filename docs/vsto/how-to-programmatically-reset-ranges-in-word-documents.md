---
title: '방법: 프로그래밍 방식으로 Word 문서의 범위 다시 설정'
description: Visual Studio를 사용 하 여 Microsoft Word 문서에서 프로그래밍 방식으로 기존 범위의 크기를 조정 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ae3b8f92231b77d81c1ef68e0929ccd000653b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824148"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>방법: 프로그래밍 방식으로 Word 문서의 범위 다시 설정
  <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> 메서드를 사용하여 Microsoft Office Word 문서에서 기존의 범위의 크기를 조정합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>기존 범위를 다시 설정하려면

1. 문서의 처음 7자로 시작하는 초기 범위를 설정합니다.

     다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet43":::

     다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 코드에서는 활성 문서를 사용합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet43":::

2. <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> 를 사용하여 두 번째 문장에서 범위를 시작하고 다섯 번째 문장 끝에서 종료합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet44":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet44":::

## <a name="document-level-customization-example"></a>문서 수준 사용자 지정 예제

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 기존 범위를 다시 설정하려면

1. 다음 예제에서는 문서 수준 사용자 지정의 전체 예를 보여 줍니다. 이 코드를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet42":::

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>VSTO 추가 기능에서 기존 범위를 다시 설정 하려면

1. 다음 예제에서는 VSTO 추가 기능의 전체 예를 보여 줍니다. 이 코드를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet42":::

## <a name="see-also"></a>참조
- [방법: 프로그래밍 방식으로 문서의 범위 확장](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 범위의 시작 및 끝 문자 검색](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [방법: 프로그래밍 방식으로 문서의 범위 또는 선택 영역 축소](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
