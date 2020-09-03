---
title: '방법: NamedRange 컨트롤 크기 조정'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7762e67b1676f72030cae8d958bef19c501660c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545823"
---
# <a name="how-to-resize-namedrange-controls"></a>방법: NamedRange 컨트롤 크기 조정
  Microsoft Office Excel 문서에 추가할 때 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤의 크기를 설정할 수 있지만 나중에 크기를 조정할 수도 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 문서 수준 프로젝트에서 디자인 타임 또는 런타임에 명명된 범위의 크기를 조정할 수 있습니다. 또한 애플리케이션 수준 VSTO 추가 기능에서 런타임에 명명된 범위의 크기를 조정할 수도 있습니다.

 이 항목에서는 다음 작업에 대해 설명합니다.

- [디자인 타임에 NamedRange 컨트롤 크기 조정](#designtime)

- [런타임에 문서 수준 프로젝트에서 NamedRange 컨트롤 크기 조정](#runtimedoclevel)

- [런타임에 VSTO 추가 기능 프로젝트에서 NamedRange 컨트롤 크기 조정](#runtimeaddin)

## <a name="resize-namedrange-controls-at-design-time"></a><a name="designtime"></a> 디자인 타임에 NamedRange 컨트롤 크기 조정
 명명된 범위의 크기를 **이름 정의** 대화 상자에서 다시 정의하여 크기를 조정할 수 있습니다.

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>이름 정의 대화 상자를 사용하여 명명된 범위의 크기를 조정하려면

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 마우스 오른쪽 단추로 클릭합니다.

2. 바로 가기 메뉴에서 **명명된 범위 관리** 를 클릭합니다.

     **이름 정의** 대화 상자가 나타납니다.

3. 크기를 조정하려는 명명된 범위를 선택합니다.

4. **참조 대상** 상자를 지웁니다.

5. 명명된 범위의 크기를 정의하는 데 사용하려는 셀을 선택합니다.

6. **확인**을 클릭합니다.

## <a name="resize-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> 런타임에 문서 수준 프로젝트에서 NamedRange 컨트롤 크기 조정
 <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> 속성을 사용하여 프로그래밍 방식으로 명명된 범위의 크기를 조정할 수 있습니다.

> [!NOTE]
> **속성** 창에서 <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> 속성은 읽기 전용으로 표시됩니다.

### <a name="to-resize-a-named-range-programmatically"></a>프로그래밍 방식으로 명명된 범위의 크기를 조정하려면

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> 의 **A1** 셀에서 `Sheet1`컨트롤을 만듭니다.

     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]

2. 명명된 범위의 크기를 조정하여 **B1**셀을 포함합니다.

     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> 런타임에 VSTO 추가 기능 프로젝트에서 NamedRange 컨트롤 크기 조정
 런타임에 열려 있는 워크시트에서 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤의 크기를 조정할 수 있습니다. VSTO 추가 기능을 사용 하 여 워크시트에 컨트롤을 추가 하는 방법에 대 한 자세한 내용은 <xref:Microsoft.Office.Tools.Excel.NamedRange> [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)를 참조 하세요.

### <a name="to-resize-a-named-range-programmatically"></a>프로그래밍 방식으로 명명된 범위의 크기를 조정하려면

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> 의 **A1** 셀에서 `Sheet1`컨트롤을 만듭니다.

     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]

2. 명명된 범위의 크기를 조정하여 **B1**셀을 포함합니다.

     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]

## <a name="see-also"></a>추가 정보
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [방법: 책갈피 컨트롤 크기 조정](../vsto/how-to-resize-bookmark-controls.md)
- [방법: ListObject 컨트롤 크기 조정](../vsto/how-to-resize-listobject-controls.md)
