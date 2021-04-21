---
title: '방법: 프로그래밍 방식으로 워크시트에서 보호 제거'
description: Visual Studio를 사용 하 여 Microsoft Excel 워크시트에서 프로그래밍 방식으로 보호를 제거 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c392ee3434edf9211a4a3061e7a83a8621960430
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824161"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>방법: 프로그래밍 방식으로 워크시트에서 보호 제거
  Microsoft Office Excel 워크시트에서 프로그래밍 방식으로 보호를 제거할 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 다음 예제에서는 사용자에게서 가져온 암호가 들어 있는 `getPasswordFromUser`변수를 사용합니다.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 워크시트를 보호 해제하려면

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A>워크시트의 메서드를 호출 하 고 필요한 경우 암호를 전달 합니다. 이 예제에서는 `Sheet1`이라는 워크시트를 사용한다고 가정합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet28":::

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>VSTO 추가 기능에서 워크시트의 보호를 해제 하려면

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A>활성 워크시트의 메서드를 호출 하 고 필요한 경우 암호를 전달 합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet18":::

## <a name="see-also"></a>참조
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서 보호](../vsto/how-to-programmatically-protect-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 숨기기](../vsto/how-to-programmatically-hide-worksheets.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
