---
title: 엑셀 오브젝트 모델 개요
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a823692a5cc0f154c514edff4fe9398de0efd212
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649420"
---
# <a name="excel-object-model-overview"></a>엑셀 개체 모델 개요
  Microsoft Office Excel을 사용하는 솔루션을 개발하려면 Excel 개체 모델에서 제공하는 개체와 상호 작용할 수 있습니다. 이 항목에서는 가장 중요한 개체를 소개합니다.

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  개체 모델은 사용자 인터페이스와 매우 유사합니다. <xref:Microsoft.Office.Interop.Excel.Application> 개체는 전체 애플리케이션을 나타내고, 각 <xref:Microsoft.Office.Interop.Excel.Workbook> 개체에는 `Worksheet` 개체의 컬렉션이 포함됩니다. 여기에서 셀을 나타내는 주요 추상화는 <xref:Microsoft.Office.Interop.Excel.Range> 개체이며, 이 개체를 통해 개별 셀 또는 셀 그룹에서 작업할 수 있습니다.

  Excel 개체 모델 외에도 Visual Studio의 Office 프로젝트는 Excel 개체 모델의 일부 개체를 확장하는 *호스트 항목* 및 *호스트 컨트롤을* 제공합니다. 호스트 항목 및 호스트 컨트롤은 확장되는 Excel 개체처럼 동작하지만 데이터 바인딩 기능과 같은 추가 기능 및 추가 이벤트도 제공합니다. 자세한 내용은 확장 개체 및 [호스트 항목 및 호스트 컨트롤 개요를](../vsto/host-items-and-host-controls-overview.md)사용하여 Excel [자동화를](../vsto/automating-excel-by-using-extended-objects.md) 참조하세요.

  이 항목에서는 Excel 개체 모델에 대한 간략한 개요를 제공합니다. 전체 Excel 개체 모델에 대해 자세히 알아볼 수 있는 리소스의 경우 [Excel 개체 모델 설명서 사용을](#ExcelOMDocumentation)참조하십시오.

## <a name="access-objects-in-an-excel-project"></a>Excel 프로젝트의 개체 액세스
 Excel용 새 VSTO 추가 기능 프로젝트를 만들면 Visual Studio에서 *ThisAddIn.vb* 또는 *ThisAddIn.cs* 코드 파일을 자동으로 만듭니다. `Me.Application` 또는 `this.Application`을 사용하여 애플리케이션 개체에 액세스할 수 있습니다.

 Excel에 대한 새 문서 수준 프로젝트를 만들면 새 Excel 통합 문서 또는 Excel 서식 파일 프로젝트를 만들 수 있습니다. Visual Studio는 통합 문서 및 서식 파일 프로젝트에 대한 새 Excel 프로젝트에서 다음과 같은 코드 파일을 자동으로 만듭니다.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sheet1.vb|Sheet1.cs|
|Sheet2.vb|Sheet2.cs|
|Sheet3.vb|Sheet3.cs|

 프로젝트에서 `Globals` 클래스를 사용하여 해당 클래스 외부에서 `ThisWorkbook`, `Sheet1`, `Sheet2` 또는 `Sheet3`에 액세스할 수 있습니다. 자세한 내용은 [Office 프로젝트의 개체에 대한 전역 액세스를](../vsto/global-access-to-objects-in-office-projects.md)참조하십시오. 다음 예제에서는 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> 코드가 `Sheet1` n 클래스 중 하나에 배치되는지 `Sheet`또는 *클래스* `ThisWorkbook` 중 하나에 배치되는지 여부에 관계없이 메서드를 호출합니다.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Excel 문서의 데이터는 구조화 수준이 높기 때문에 개체 모델이 계층적이고 간단합니다. Excel은 상호 작용할 수 있는 수백 개의 개체를 제공하지만 사용 가능한 개체의 작은 하위 집합에 집중하여 개체 모델에서 좋은 시작을 얻을 수 있습니다. 이러한 개체에는 다음 네 가지가 있습니다.

- 애플리케이션

- 통합 문서

- 워크시트

- 범위

  Excel에서 수행되는 대부분의 작업은 이 네 가지 개체와 해당 멤버를 중심으로 합니다.

### <a name="application-object"></a>애플리케이션 개체
 Excel <xref:Microsoft.Office.Interop.Excel.Application> 개체는 Excel 애플리케이션 자체를 나타냅니다. <xref:Microsoft.Office.Interop.Excel.Application> 개체는 실행 중인 애플리케이션, 해당 인스턴스에 적용된 옵션 및 인스턴스 내에서 열려 있는 현재 사용자 개체에 대한 많은 정보를 표시합니다.

> [!NOTE]
> Excel에서 <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> 개체의 <xref:Microsoft.Office.Interop.Excel.Application> 속성을 **false**라는 Word 또는 Excel 개체 모델에 고유하게 존재하는 개체를 확장합니다. 이 속성을 false로 설정하면 Excel에서 호스트 컨트롤의 이벤트를 비롯한 모든 이벤트를 발생시킬 수 없습니다.

### <a name="workbook-object"></a>통합 문서 개체
 <xref:Microsoft.Office.Interop.Excel.Workbook> 개체는 Excel 애플리케이션 내에서 단일 통합 문서를 나타냅니다.

 Visual Studio의 Office 개발 도구는 <xref:Microsoft.Office.Interop.Excel.Workbook> 형식을 제공하여 <xref:Microsoft.Office.Tools.Excel.Workbook> 개체를 확장합니다. 이 형식은 <xref:Microsoft.Office.Interop.Excel.Workbook> 개체의 모든 기능에 액세스할 수 있습니다. 자세한 내용은 [통합 문서 호스트 항목을](../vsto/workbook-host-item.md)참조하십시오.

### <a name="worksheet-object"></a>Worksheet 개체
 <xref:Microsoft.Office.Interop.Excel.Worksheet> 개체는 <xref:Microsoft.Office.Interop.Excel.Worksheets> 컬렉션의 멤버입니다. <xref:Microsoft.Office.Interop.Excel.Worksheet>의 속성, 메서드 및 이벤트 대부분은 <xref:Microsoft.Office.Interop.Excel.Application> 또는 <xref:Microsoft.Office.Interop.Excel.Workbook> 개체에서 제공하는 멤버와 동일하거나 유사합니다.

 Excel에서는 <xref:Microsoft.Office.Interop.Excel.Sheets> 컬렉션을 <xref:Microsoft.Office.Interop.Excel.Workbook> 개체의 속성으로 제공합니다. <xref:Microsoft.Office.Interop.Excel.Sheets> 컬렉션의 각 멤버는 <xref:Microsoft.Office.Interop.Excel.Worksheet> 또는 <xref:Microsoft.Office.Interop.Excel.Chart> 개체입니다.

 Visual Studio의 Office 개발 도구는 <xref:Microsoft.Office.Interop.Excel.Worksheet> 형식을 제공하여 <xref:Microsoft.Office.Tools.Excel.Worksheet> 개체를 확장합니다. 이 형식은 <xref:Microsoft.Office.Interop.Excel.Worksheet> 개체의 모든 기능뿐만 아니라 관리되는 컨트롤을 호스트하고 새 이벤트를 처리하는 기능과 같은 새 기능에 액세스할 수 있습니다. 자세한 내용은 [워크시트 호스트 항목을](../vsto/worksheet-host-item.md)참조하십시오.

### <a name="range-object"></a>Range 개체
 <xref:Microsoft.Office.Interop.Excel.Range> 개체는 Excel 애플리케이션 내에서 가장 많이 사용되는 개체입니다. Excel 내에서 영역을 조작하려면 먼저 <xref:Microsoft.Office.Interop.Excel.Range> 개체로 표현하고 해당 범위의 메서드 및 속성을 사용해야 합니다. <xref:Microsoft.Office.Interop.Excel.Range> 개체는 셀, 행, 열, 하나 이상의 셀 블록을 포함하는 셀 선택 영역(인접하거나 인접하지 않을 수 있음) 또는 여러 시트에 있는 셀 그룹을 나타냅니다.

 Visual Studio는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 및 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 형식을 제공하여 <xref:Microsoft.Office.Interop.Excel.Range> 개체를 확장합니다. 이러한 형식은 <xref:Microsoft.Office.Interop.Excel.Range> 개체와 동일한 기능을 사용할 뿐만 아니라 데이터 바인딩 기능과 같은 새로운 기능 및 새로운 이벤트로 제공합니다. 자세한 내용은 [NamedRange 컨트롤](../vsto/namedrange-control.md) 및 [XmlMappedRange 컨트롤을](../vsto/xmlmappedrange-control.md)참조하십시오.

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a>Excel 개체 모델 설명서 사용
 Excel 개체 모델에 대한 자세한 내용은 Excel PIA(주 interop 어셈블리) 참조 및 VBA 개체 모델 참조를 참조할 수 있습니다.

### <a name="primary-interop-assembly-reference"></a>기본 인터옵 어셈블리 참조
 Excel PIA 참조 설명서에서는 Excel에 대한 주 interop 어셈블리의 형식에 대해 설명합니다. 이 설명서는 다음과 같은 위치에서 사용할 수 있습니다: [Excel 2010 기본 interop 어셈블리 참조.](office-primary-interop-assemblies.md)

 PIA의 클래스와 인터페이스 간의 차이점 및 PIA의 이벤트가 구현되는 방법과 같은 Excel PIA 디자인에 대한 자세한 내용은 [Office 기본 interop 어셈블리의 클래스 및 인터페이스 개요를](/previous-versions/office/office-12/ms247299(v=office.12))참조하십시오.

### <a name="vba-object-model-reference"></a>VBA 개체 모델 참조
 VBA 개체 모델 참조에서는 VBA(Visual Basic for Applications) 코드로 표시되는 Excel 개체 모델에 대해 설명합니다. 자세한 내용은 [Excel 2010 개체 모델 참조를](/office/vba/api/overview/Excel/object-model)참조하십시오.

 VBA 개체 모델 참조의 모든 개체 및 멤버는 Excel PIA의 형식 및 멤버에 해당합니다. 예를 들어 VBA 개체 모델 참조의 워크시트 개체는 Excel PIA의 <xref:Microsoft.Office.Interop.Excel.Worksheet> 개체에 해당합니다. VBA 개체 모델 참조에서는 대부분의 속성, 메서드 및 이벤트에 대한 코드 예제를 제공하지만 Visual Studio를 사용하여 만든 Excel 프로젝트에서 사용하려면 이 참조의 VBA 코드를 Visual Basic 또는 Visual C#으로 변환해야 합니다.

### <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[엑셀 솔루션](../vsto/excel-solutions.md)|Microsoft Office Excel용 문서 수준 사용자 지정 및 VSTO 추가 기능을 만드는 방법에 대해 설명합니다.|
|[범위로 작업](../vsto/working-with-ranges.md)|범위와 관련된 일반적인 작업을 수행하는 방법을 보여 주는 예제를 제공합니다.|
|[워크시트 작업](../vsto/working-with-worksheets.md)|워크시트와 관련된 일반적인 작업을 수행하는 방법을 보여 주는 예제를 제공합니다.|
|[통합 문서 작업](../vsto/working-with-workbooks.md)|통합 문서와 관련된 일반적인 작업을 수행하는 방법을 보여 주는 예제를 제공합니다.|
