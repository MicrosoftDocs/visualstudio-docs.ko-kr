---
title: '방법: 프로그래밍 방식으로 문서의 문자 수 세기'
description: 문자 컬렉션의 Count 속성을 사용 하 여 문서에 있는 문자 수를 확인 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68ddc86183eacd7f76e39bb06e47968c0129849c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824007"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>방법: 프로그래밍 방식으로 문서의 문자 수 세기
  문서에서 첫 번째 문자는 문자 위치 0에 있는 문자이며 삽입 지점을 나타냅니다. 마지막 문자 위치는 문서에 있는 총 문자 수와 같습니다. <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> 컬렉션의 <xref:Microsoft.Office.Interop.Word.Characters> 속성을 사용하여 문서에 있는 문자 수를 확인할 수 있습니다.

 공백, 단락 표시 및 일반적으로 숨겨져 있는 다른 문자를 포함하여 문서에 있는 모든 문자 수가 계산됩니다. 단락 표시도 포함되므로 새로 만든 빈 문서도 한 개의 문자 수를 반환합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 문자 수를 표시하려면

1. 전체 문서를 선택합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet98":::

2. 메시지 상자에 문서의 문자 수를 표시합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet99":::

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>VSTO 추가 기능의 문자 수를 표시 하려면

1. 전체 문서를 선택합니다. 다음 예제에서는 활성 문서를 선택합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet98":::

2. 메시지 상자에 문서의 문자 수를 표시합니다.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet99":::

## <a name="see-also"></a>참조
- [방법: 프로그래밍 방식으로 범위의 시작 및 끝 문자 검색](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
