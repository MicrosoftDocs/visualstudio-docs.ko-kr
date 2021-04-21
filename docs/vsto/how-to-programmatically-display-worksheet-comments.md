---
title: '방법: 프로그래밍 방식으로 워크시트 메모 표시'
description: Microsoft Excel 워크시트의 문서 수준 또는 응용 프로그램 수준에서 프로그래밍 방식으로 메모를 표시 하 고 숨길 수 있는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af327a6756189c73f80f624205451274abf19264
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828672"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>방법: 프로그래밍 방식으로 워크시트 메모 표시
  Microsoft Office Excel 워크시트에서 프로그래밍 방식으로 메모를 표시하고 숨길 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 워크시트에 모든 메모를 표시하려면

1. 메모를 표시하려는 경우 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 속성을 **true** 로 설정하고 그렇지 않은 경우 **false** 로 설정합니다. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet31":::

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>애플리케이션 수준 VSTO의 추가 기능에서 워크시트에 모든 메모를 표시하려면

1. 메모를 표시하려는 경우 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 속성을 **true** 로 설정하고 그렇지 않은 경우 **false** 로 설정합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet21":::

## <a name="see-also"></a>참조
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 메모 추가 및 삭제](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
