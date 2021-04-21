---
title: '방법: 프로그래밍 방식으로 통합 문서 내에서 워크시트 이동'
description: Microsoft Excel 통합 문서의 다른 워크시트를 기준으로 워크시트의 위치를 프로그래밍 방식으로 변경할 수 있는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd05dcb39c295d4d1ebb39d933c643f61c6d921c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827294"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>방법: 프로그래밍 방식으로 통합 문서 내에서 워크시트 이동
  통합 문서의 다른 워크시트를 기준으로 워크시트의 위치를 프로그래밍 방식으로 변경할 수 있습니다. 이동한 시트의 위치를 지정하지 않으면 Excel에서 이 시트가 포함된 새 통합 문서를 만듭니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 워크시트를 이동하려면

1. 통합 문서에 있는 총 시트 수를 변수에 할당하고 첫 번째 워크시트가 마지막 워크시트가 되도록 이동합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet24":::

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>VSTO 추가 기능에서 워크시트를 이동 하려면

1. 통합 문서에 있는 총 시트 수를 변수에 할당하고 첫 번째 워크시트가 마지막 워크시트가 되도록 이동합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet16":::

## <a name="see-also"></a>참조
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 숨기기](../vsto/how-to-programmatically-hide-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에서 워크시트 삭제](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
