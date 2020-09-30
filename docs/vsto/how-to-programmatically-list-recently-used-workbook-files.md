---
title: '방법: 프로그래밍 방식으로 최근에 사용한 통합 문서 파일 나열'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e3d6b57251bb19cfb02849defb157c949f4ce35
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585160"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>방법: 프로그래밍 방식으로 최근에 사용한 통합 문서 파일 나열
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>속성은 Microsoft Office Excel에서 최근에 사용한 파일 목록에 표시 되는 모든 파일의 이름을 포함 하는 컬렉션을 반환 합니다. 목록의 길이는 사용자가 유지 하도록 선택한 파일 수에 따라 달라 집니다. 범위에 결과를 표시할 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>범위 개체에서 최근에 사용 된 통합 문서를 나열 하려면

1. 최근 파일 목록을 반복 하 고 개체를 기준으로 셀에 이름을 표시 합니다 <xref:Microsoft.Office.Interop.Excel.Range> .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>참고 항목
- [통합 문서 작업](../vsto/working-with-workbooks.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
