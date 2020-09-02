---
title: '방법: 프로그래밍 방식으로 Word에서 검색 옵션 설정'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 434dfc85ed6c4e03c7c610a497bd063ce1826c62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546993"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>방법: 프로그래밍 방식으로 Word에서 검색 옵션 설정
  Microsoft Office Word 문서에서 선택 항목에 대 한 검색 옵션을 설정 하는 방법에는 두 가지가 있습니다.

- 개체의 개별 속성을 설정 <xref:Microsoft.Office.Interop.Word.Find> 합니다.

- <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>개체의 메서드 인수를 사용 <xref:Microsoft.Office.Interop.Word.Find> 합니다.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Find 개체의 속성 사용
 다음 코드는 개체의 속성 <xref:Microsoft.Office.Interop.Word.Find> 을 설정 하 여 현재 선택 영역 내에서 텍스트를 검색 합니다. 검색 하는 검색 조건 (예: 전달 검색, 줄 바꿈 및 검색할 텍스트)은 개체의 속성입니다 <xref:Microsoft.Office.Interop.Word.Find> .

 <xref:Microsoft.Office.Interop.Word.Find>메서드의 매개 변수와 동일한 속성을 지정 해야 하므로 c # 코드를 작성 하는 경우에는 개체의 각 속성을 설정 하는 것이 유용 하지 않습니다 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> . 따라서이 예제는 Visual Basic 코드만 포함 합니다.

### <a name="to-set-search-options-using-a-find-object"></a>Find 개체를 사용 하 여 검색 옵션을 설정 하려면

1. 개체의 속성을 설정 <xref:Microsoft.Office.Interop.Word.Find> 하 여 텍스트에 대 한 선택 항목을 앞 **find me**으로 검색 합니다.

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Execute 메서드 인수 사용
 다음 코드에서는 개체의 메서드를 사용 하 여 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> <xref:Microsoft.Office.Interop.Word.Find> 현재 선택 영역 내에서 텍스트를 검색 합니다. 검색 조건 (예: 전달 검색, 래핑 및 검색할 텍스트)은 메서드의 매개 변수로 전달 됩니다 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .

### <a name="to-set-search-options-using-execute-method-arguments"></a>Execute 메서드 인수를 사용 하 여 검색 옵션을 설정 하려면

1. 검색 조건을 메서드의 매개 변수로 전달 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 하 여 선택한 텍스트에 대해 앞으로 검색 합니다. **find me**

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 문서에서 텍스트 검색 및 바꾸기](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [방법: 프로그래밍 방식으로 문서에서 찾은 항목 반복](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [방법: 프로그래밍 방식으로 검색 후 선택 영역 복원](../vsto/how-to-programmatically-restore-selections-after-searches.md)
