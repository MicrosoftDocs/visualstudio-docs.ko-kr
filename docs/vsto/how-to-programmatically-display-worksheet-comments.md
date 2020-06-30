---
title: '방법: 프로그래밍 방식으로 워크시트 메모 표시'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0fc84e2726cd7a70b8fc59b0f1ac2b3377f9c4af
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543366"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>방법: 프로그래밍 방식으로 워크시트 메모 표시
  Microsoft Office Excel 워크시트에서 프로그래밍 방식으로 메모를 표시하고 숨길 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 워크시트에 모든 메모를 표시하려면

1. 메모를 표시하려는 경우 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 속성을 **true** 로 설정하고 그렇지 않은 경우 **false**로 설정합니다. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>애플리케이션 수준 VSTO의 추가 기능에서 워크시트에 모든 메모를 표시하려면

1. 메모를 표시하려는 경우 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 속성을 **true** 로 설정하고 그렇지 않은 경우 **false**로 설정합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]

## <a name="see-also"></a>참고 항목
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 메모 추가 및 삭제](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
