---
title: '방법: 워크시트에 ListObject 컨트롤 추가'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c53d820170c359e568b0a7b0ab5711a632d9eba
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538322"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>방법: 워크시트에 ListObject 컨트롤 추가
  디자인 타임 및 런타임에 문서 수준 프로젝트에서 Microsoft Office Excel 워크시트에 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 추가할 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 런타임에 VSTO 추가 기능 프로젝트에서 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 추가할 수도 있습니다.

 이 항목에서는 다음 작업에 대해 설명합니다.

- [디자인 타임에 ListObject 컨트롤 추가](#designtime)

- [런타임에 문서 수준 프로젝트에서 ListObject 컨트롤 추가](#runtimedoclevel)

- [런타임에 VSTO 추가 기능 프로젝트에서 ListObject 컨트롤 추가](#runtimeaddin)

  컨트롤에 대 한 자세한 내용은 <xref:Microsoft.Office.Tools.Excel.ListObject> [ListObject 컨트롤](../vsto/listobject-control.md)을 참조 하세요.

## <a name="add-listobject-controls-at-design-time"></a><a name="designtime"></a>디자인 타임에 ListObject 컨트롤 추가
 디자인 타임에 문서 수준 프로젝트에서 워크시트에 컨트롤을 추가 하는 방법에는 여러 가지가 있습니다 <xref:Microsoft.Office.Tools.Excel.ListObject> . 즉, Excel, Visual Studio **도구 상자**및 **데이터 소스** 창에서 사용할 수 있습니다.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Excel에서 리본을 사용하려면

1. **삽입** 탭의 **테이블** 그룹에서 **테이블**을 클릭합니다.

2. 목록에 포함하려는 셀을 선택하고 **확인**을 클릭합니다.

#### <a name="to-use-the-toolbox"></a>도구 상자를 사용하려면

1. **도구 상자** 의 **Excel 컨트롤**탭에서 <xref:Microsoft.Office.Tools.Excel.ListObject> 를 워크시트로 끌어 옵니다.

     **ListObject 컨트롤 추가** 대화 상자가 나타납니다.

2. 목록에 포함하려는 셀을 선택하고 **확인**을 클릭합니다.

     기본 이름을 유지하지 않으려면 **속성** 창에서 이름을 변경할 수 있습니다.

#### <a name="to-use-the-data-sources-window"></a>데이터 원본 창을 사용하려면

1. **데이터 원본** 창을 열고 데이터베이스에서 데이터 원본을 만듭니다. 자세한 내용은 [새 연결 추가](../data-tools/add-new-connections.md)를 참조 하세요.

2. **데이터 원본** 창에서 테이블을 워크시트로 끌어 옵니다.

     데이터 바인딩된 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 워크시트에 추가됩니다. 자세한 내용은 [데이터 바인딩 및 Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)을 참조 하세요.

## <a name="add-listobject-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a>런타임에 문서 수준 프로젝트에서 ListObject 컨트롤 추가
 런타임에 동적으로 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 추가할 수 있습니다. 이를 통해 이벤트에 대한 응답으로 호스트 컨트롤을 만들 수 있습니다. 동적으로 생성된 리스트 개체는 워크시트를 닫을 때 워크시트에서 호스트 컨트롤로 유지되지 않습니다. 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)를 참조 하세요.

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>프로그래밍 방식으로 워크시트에 ListObject 컨트롤을 추가하려면

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 의 `Sheet1`이벤트 처리기에서 다음 코드를 삽입하여 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 **A1** - **A4**에 추가합니다.

     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]

## <a name="add-listobject-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>런타임에 VSTO 추가 기능 프로젝트에서 ListObject 컨트롤 추가
 VSTO 추가 기능 프로젝트에서 열려 있는 워크시트에 프로그래밍 방식으로 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 추가할 수 있습니다. 동적으로 생성된 리스트 개체는 워크시트를 저장한 다음 닫을 때 워크시트에서 호스트 컨트롤로 유지되지 않습니다. 자세한 내용은 [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조 하세요.

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>프로그래밍 방식으로 워크시트에 ListObject 컨트롤을 추가하려면

1. 다음 코드는 열려 있는 워크시트를 기반으로 하는 워크시트 호스트 항목을 생성하고 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 **A4** 셀을 통해 **A1**셀에 추가합니다.

     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]

## <a name="see-also"></a>참고 항목
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [ListObject 컨트롤](../vsto/listobject-control.md)
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [방법: ListObject 컨트롤 크기 조정](../vsto/how-to-resize-listobject-controls.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
