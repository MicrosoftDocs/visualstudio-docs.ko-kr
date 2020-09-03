---
title: 확장 된 개체를 사용 하 여 Excel 자동화
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65734f5397bae8c35fb8e312041d0600b8fa84e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254339"
---
# <a name="automate-excel-by-using-extended-objects"></a>확장 된 개체를 사용 하 여 Excel 자동화
  Visual Studio에서 Excel 솔루션을 개발하는 경우 솔루션에서 *호스트 항목* 및 *호스트 컨트롤*을 사용할 수 있습니다. Excel 개체 모델, 즉 Excel용 주 interop 어셈블리가 노출하는 개체 모델에서 일반적으로 사용되는 특정 개체(예: <xref:Microsoft.Office.Interop.Excel.Worksheet> 및 <xref:Microsoft.Office.Interop.Excel.Range> )를 확장하는 개체입니다. 확장된 개체는 기반이 되는 Excel 개체처럼 동작하지만 개체에 새 이벤트 및 데이터 바인딩 기능 등을 더 추가합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 사용할 수 있는 컨텍스트는 각 솔루션 형식마다 다를 수 있지만 호스트 항목과 호스트 컨트롤은 VSTO 추가 기능과 문서 수준 사용자 지정 둘 다에서 사용할 수 있습니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

## <a name="excel-host-items"></a>Excel 호스트 항목
 Excel 프로젝트는 여러 호스트 항목에 대한 액세스를 제공합니다.

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. 이 호스트 항목은 프로젝트의 워크시트를 포함 하 고 나타냅니다. 또한 호스트 컨트롤 및 Windows Forms 컨트롤을 포함하여 관리되는 컨트롤에 대한 컨테이너 역할을 하고 해당 화면에 컨트롤에 대한 정보를 유지 관리합니다. 자세한 내용은 [워크시트 호스트 항목](../vsto/worksheet-host-item.md)을 참조 하세요.

- <xref:Microsoft.Office.Tools.Excel.Workbook>. 이 호스트 항목은 프로젝트의 통합 문서를 나타내며 통합 문서의 모든 워크시트에서 공유하는 구성 요소에 대한 컨테이너 역할을 합니다. 자세한 내용은 [통합 문서 호스트 항목](../vsto/workbook-host-item.md)을 참조 하세요.

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. 이 호스트 항목은 차트만 포함하고 이벤트를 노출하는 Excel의 워크시트를 나타냅니다.

     Microsoft Office Excel 문서 수준 사용자 지정 프로젝트에서 디자인 타임에 차트 시트를 새 시트로 추가하면 Visual Studio에서 자동으로 <xref:Microsoft.Office.Tools.Excel.ChartSheet> 호스트 항목을 만듭니다.

     <xref:Microsoft.Office.Tools.Excel.ChartSheet> 호스트 항목은 Excel의 워크시트이지만 차트 시트에 컨트롤을 추가할 수 없습니다. 차트가 있는 워크시트에 다른 컨트롤을 포함하려는 경우 차트 시트를 사용하지 마세요. 대신, <xref:Microsoft.Office.Tools.Excel.Chart> 호스트 컨트롤을 사용하여 워크시트에 포함 개체로 차트를 배치할 수 있습니다. 자세한 내용은 [차트 컨트롤](../vsto/chart-control.md)을 참조 하세요.

## <a name="excel-host-controls"></a>Excel 호스트 컨트롤
 통합 문서와 워크시트를 만들고 구성 및 자동화하는 데 도움이 되는 여러 Excel용 호스트 컨트롤이 있습니다. 이러한 호스트 컨트롤은 네이티브 Excel 개체 모델의 해당 항목에 없는 이벤트 및 데이터 바인딩 기능을 제공합니다.

 Excel 프로젝트에서 사용할 수 있는 호스트 컨트롤에 대한 자세한 내용은 다음 항목을 참조하세요.

- [차트 컨트롤](../vsto/chart-control.md)

- [ListObject 컨트롤](../vsto/listobject-control.md)

- [NamedRange 컨트롤](../vsto/namedrange-control.md)

- [XmlMappedRange 컨트롤](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>참고 항목
- [방법: ListObject 컨트롤을 데이터로 채우기](../vsto/how-to-fill-listobject-controls-with-data.md)
- [방법: 워크시트에 차트 컨트롤 추가](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [방법: 워크시트에 ListObject 컨트롤 추가](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [방법: 워크시트에 XMLMappedRange 컨트롤 추가](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [방법: NamedRange 컨트롤 크기 조정](../vsto/how-to-resize-namedrange-controls.md)
- [방법: ListObject 컨트롤 크기 조정](../vsto/how-to-resize-listobject-controls.md)
- [방법: ListObject 컨트롤에 새 행을 추가할 때 데이터 유효성 검사](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [방법: 데이터에 ListObject 열 매핑](../vsto/how-to-map-listobject-columns-to-data.md)
- [연습: NamedRange 컨트롤의 이벤트에 대 한 프로그래밍](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
