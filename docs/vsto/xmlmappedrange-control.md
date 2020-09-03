---
title: XmlMappedRange 컨트롤
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01417d9c08491edc882f7f758bb36e6184500e52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985368"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange 컨트롤
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>컨트롤은 반복 되지 않는 스키마 요소가 Excel Microsoft Office의 셀에 매핑될 때만 생성 되는 범위입니다. 예를 들어 `maxOccurs` schema 요소의 특성은 1과 같습니다. Visual Studio에서 XML 매핑된 범위를 만든 후에는 Excel 개체 모델을 트래버스 하지 않고 직접 프로그래밍할 수 있습니다. <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>요소 매핑이 제거 될 때에만 Excel 내에서 컨트롤을 삭제할 수 있습니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>컨트롤에 데이터 바인딩
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>컨트롤은 단일 데이터 필드에 대 한 바인딩을 지원 합니다 (단순 데이터 바인딩). <xref:Microsoft.Office.Tools.Excel.ListObject>컨트롤은 복합 데이터 바인딩을 지원할 수 있으며 반복 스키마 요소가 셀에 매핑될 때 자동으로 생성 됩니다. 자세한 내용은 [ListObject 컨트롤](../vsto/listobject-control.md)을 참조 하세요.

 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>컨트롤은 속성을 사용 하 여 데이터 소스에 바인딩됩니다 <xref:System.Windows.Forms.Control.DataBindings%2A> . <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>워크시트 셀에를 추가 하면 Visual Studio는 매핑된 셀의 데이터에서 데이터 집합을 자동으로 생성 하 고 컨트롤을 해당 데이터 집합에 바인딩합니다. 의 기본 데이터 바인딩 속성은 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> 입니다.

 바인딩된 데이터 집합의 데이터가 임의 메커니즘을 통해 업데이트 되 면 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 컨트롤이 변경 내용을 반영 합니다.

## <a name="formatting"></a>서식 지정
 에 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 적용할 수 있는 것과 동일한 서식을 컨트롤에 적용할 수 있습니다 <xref:Microsoft.Office.Interop.Excel.Range> . 여기에는 테두리, 글꼴, 숫자 서식 및 스타일이 포함됩니다.

## <a name="events"></a>이벤트
 컨트롤에 사용할 수 있는 이벤트는 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 다음과 같습니다.

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>참고 항목
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [방법: 워크시트에 XMLMappedRange 컨트롤 추가](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [방법: Visual Studio 내에서 워크시트에 스키마 매핑](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
