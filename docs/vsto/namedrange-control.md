---
title: NamedRange 컨트롤
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e2b5b5d246e1033148bc199da6e7d2bdfb7aa9b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254724"
---
# <a name="namedrange-control"></a>NamedRange 컨트롤
  <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤은 고유 이름이 있고, 이벤트를 노출하고, 데이터에 바인딩될 수 있는 범위입니다. 자세한 내용은 [Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)를 참조 하세요.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>컨트롤 만들기
 디자인 타임 또는 런타임에 문서 수준 프로젝트에서 Microsoft Office Excel 워크시트에 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 추가할 수 있습니다.

 런타임에 VSTO 추가 기능에서 워크시트에 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 추가할 수 있습니다. 자세한 내용은 [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)를 참조 하세요.

> [!NOTE]
> 기본적으로 동적으로 만들어진 명명된 범위는 워크시트를 닫을 때 워크시트에서 호스트 컨트롤로 유지되지 않습니다. 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)를 참조 하세요.

 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤은 특정 시트 범위로만 구성될 수 있습니다. <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤은 모든 시트에 적용되는 상대적 이름을 가질 수 없으며 통합 문서에서 둘 이상의 워크시트를 포함하는 범위(3D 범위)로 구성될 수 없습니다.

## <a name="bind-data-to-the-control"></a>컨트롤에 데이터 바인딩
 명명된 범위에는 많은 셀을 포함할 수 있으므로 복잡한 데이터 바인딩이 가능해 보일 수 있습니다. 그러나 범위는 단지 데이터 세트의 특정 열에 쉽게 매핑할 수 없는 셀 모음일 뿐입니다. 따라서 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤은 단순 데이터 바인딩만 지원합니다. <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤은 복잡한 데이터 바인딩에 사용할 수 있습니다. 자세한 내용은 [ListObject 컨트롤](../vsto/listobject-control.md)을 참조 하세요.

 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤은 <xref:System.Windows.Forms.Control.DataBindings%2A> 속성을 사용하여 데이터 원본에 바인딩할 수 있습니다. <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤의 기본 데이터 바인딩 속성은 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>입니다.

 바인딩된 데이터 세트의 데이터가 임의 메커니즘을 통해 업데이트되면 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 변경 내용을 반영합니다.

## <a name="formatting"></a>서식 지정
 <xref:Microsoft.Office.Interop.Excel.Range> 에 적용할 수 있는 서식은 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤에 적용할 수 있습니다. 여기에는 테두리, 글꼴, 숫자 서식 및 스타일이 포함 됩니다.

## <a name="rename-the-control"></a>컨트롤 이름 바꾸기
 <xref:Microsoft.Office.Tools.Excel.NamedRange> 도구 상자 **에서**컨트롤을 워크시트에 추가할 때 Visual Studio에서 컨트롤 이름을 자동으로 생성합니다. **속성** 창을 사용하여 이 이름을 변경할 수 있습니다.

## <a name="events"></a>이벤트
 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤에 대해 다음 이벤트를 사용할 수 있습니다.

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>

## <a name="see-also"></a>참고 항목
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [방법: NamedRange 컨트롤 크기 조정](../vsto/how-to-resize-namedrange-controls.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [연습: NamedRange 컨트롤의 이벤트에 대 한 프로그래밍](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
