---
title: '방법: 프로그래밍 방식으로 워크시트에서 맞춤법 검사'
description: Microsoft Excel 워크시트에서 프로그래밍 방식으로 단어의 맞춤법을 검사할 수 있는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1bf35e225def686ae2424a89b7e5d6b77207ccee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826059"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>방법: 프로그래밍 방식으로 워크시트에서 맞춤법 검사
  프로그래밍 방식으로 워크시트에 있는 단어의 맞춤법을 검사할 수 있습니다. 워크시트에 맞춤법이 잘못된 단어가 있으면 **맞춤법 검사** 대화 상자가 자동으로 나타납니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 워크시트의 맞춤법을 검사하려면

1. 워크시트의 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 메서드를 호출합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet45":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet45":::

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>VSTO 추가 기능에서 워크시트의 맞춤법을 검사 하려면

1. 활성 워크시트의 <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> 메서드를 호출합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet22":::

## <a name="see-also"></a>참조
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 Excel 계산 실행](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
