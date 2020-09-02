---
title: 프로그래밍 방식으로 Word 표 셀에 텍스트 & 서식 추가
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: acd43c82c6dae32ef6595b2f63c06fe61f3c6168
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538049"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>방법: 프로그래밍 방식으로 Word 표의 셀에 텍스트 및 서식 추가
  각 테이블은 셀 컬렉션으로 이루어져 있습니다. 각 개별 <xref:Microsoft.Office.Interop.Word.Cell> 개체는 테이블의 한 셀을 나타냅니다. 테이블의 해당 위치로 각 셀을 참조합니다. 이 예제에서는 테이블의 첫 행과 첫 열에 있는 셀을 참조하고, 셀에 텍스트를 추가하고, 서식을 적용합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>셀에 텍스트 및 서식을 추가하려면

1. 테이블의 해당 위치에 따라 셀을 참조하고, 셀에 텍스트를 추가한 다음 서식을 적용합니다.

     다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다. 이 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]

     다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 예제에서는 활성 문서를 사용합니다. 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 Word 표 만들기](../vsto/how-to-programmatically-create-word-tables.md)
- [방법: 프로그래밍 방식으로 Word 표에 행 및 열 추가](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [방법: 프로그래밍 방식으로 문서 속성을 사용 하 여 Word 표 채우기](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
