---
title: '방법: 프로그래밍 방식으로 검색 후 선택 영역 복원'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 30daa81c33070db3f9418b45b84b4acc6e243dc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547097"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>방법: 프로그래밍 방식으로 검색 후 선택 영역 복원
  문서에서 텍스트를 찾아 바꾸는 경우 검색이 완료 된 후 사용자의 원래 선택 영역을 복원 하는 것이 좋습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 샘플 프로시저의 코드에서는 두 개의 개체를 사용 <xref:Microsoft.Office.Interop.Word.Range> 합니다. 하나는 현재를 저장 하 <xref:Microsoft.Office.Interop.Word.Selection> 고, 하나는 검색 범위로 사용할 전체 문서를 설정 합니다.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>검색 후 사용자의 원래 선택 영역을 복원 하려면

1. <xref:Microsoft.Office.Interop.Word.Range>문서와 현재 선택 항목에 대 한 개체를 만듭니다.

    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]

2. 검색 및 바꾸기 작업을 수행 합니다.

    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]

3. 사용자의 원래 선택 영역을 복원 하려면 시작 범위를 선택 합니다.

    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]

   다음 예제에서는 전체 메서드를 보여 줍니다.

## <a name="example"></a>예제
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]

## <a name="see-also"></a>참고 항목
- [방법: 프로그래밍 방식으로 문서에서 텍스트 검색 및 바꾸기](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [방법: 프로그래밍 방식으로 Word에서 검색 옵션 설정](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [방법: 프로그래밍 방식으로 문서에서 찾은 항목 반복](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
