---
title: '방법: 프로그래밍 방식으로 통합 문서 내에서 워크시트 이동'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4594395eb887a950c9ff0ba41cd8d3c625d35dc3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519828"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>방법: 프로그래밍 방식으로 통합 문서 내에서 워크시트 이동
  통합 문서의 다른 워크시트를 기준으로 워크시트의 위치를 프로그래밍 방식으로 변경할 수 있습니다. 이동한 시트의 위치를 지정하지 않으면 Excel에서 이 시트가 포함된 새 통합 문서를 만듭니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 워크시트를 이동하려면

1. 통합 문서에 있는 총 시트 수를 변수에 할당하고 첫 번째 워크시트가 마지막 워크시트가 되도록 이동합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>VSTO 추가 기능에서 워크시트를 이동 하려면

1. 통합 문서에 있는 총 시트 수를 변수에 할당하고 첫 번째 워크시트가 마지막 워크시트가 되도록 이동합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>추가 정보
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 숨기기](../vsto/how-to-programmatically-hide-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에서 워크시트 삭제](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
