---
title: ListObject 컨트롤
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b5286a4bddff2b529abd0a565bb4dbeef7ffaf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71251860"
---
# <a name="listobject-control"></a>ListObject 컨트롤
  <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤은 이벤트를 노출하고, 데이터에 바인딩될 수 있는 목록입니다. 워크시트에 목록을 추가하면 Visual Studio에서 Microsoft Office Excel 개체 모델을 트래버스하지 않고 직접 프로그래밍할 수 있는 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 만듭니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>컨트롤 만들기
 문서 수준 프로젝트에서는 디자인 타임 또는 런타임에 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 워크시트에 추가할 수 있습니다. VSTO 추가 기능 프로젝트에서는 런타임에만 워크시트에 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 추가할 수 있습니다. 자세한 내용은 [방법: 워크시트에 ListObject 컨트롤 추가](../vsto/how-to-add-listobject-controls-to-worksheets.md)를 참조 하세요.

> [!NOTE]
> 기본적으로 동적으로 생성된 목록 개체는 워크시트를 닫을 때 워크시트에서 호스트 컨트롤로 유지되지 않습니다. 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)를 참조 하세요.

## <a name="bind-data-to-the-control"></a>컨트롤에 데이터 바인딩
 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤은 간단한 데이터 바인딩 및 복잡한 데이터 바인딩을 지원합니다. <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤은 디자인 타임에 <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> 및 <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> 속성을 사용하거나 런타임에 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 메서드를 사용하여 데이터 원본에 바인딩되어야 합니다.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.ListObject> 는 <xref:System.Data.DataTable>등 데이터 변경 시 이벤트가 발생하는 데이터 원본에 바인딩될 때 자동으로 업데이트됩니다. 데이터 변경 시 이벤트가 발생하지 않는 데이터 원본에 <xref:Microsoft.Office.Tools.Excel.ListObject> 를 바인딩할 경우 <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> 또는 <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> 메서드를 호출하여 <xref:Microsoft.Office.Tools.Excel.ListObject>를 업데이트해야 합니다.

 반복 스키마 요소를 해당 셀에 매핑하여 <xref:Microsoft.Office.Tools.Excel.ListObject>를 워크시트 셀에 추가할 때 Visual Studio에서 <xref:Microsoft.Office.Tools.Excel.ListObject>를 생성된 데이터 세트에 자동으로 매핑합니다. 그러나 <xref:Microsoft.Office.Tools.Excel.ListObject> 는 자동으로 데이터에 바인딩되지 않습니다. 디자인 타임 또는 런타임에 문서 수준 프로젝트에서 <xref:Microsoft.Office.Tools.Excel.ListObject>를 데이터 세트에 바인딩할 수 있습니다. <xref:Microsoft.Office.Tools.Excel.ListObject>런타임에 VSTO 추가 기능에서를 데이터 집합에 프로그래밍 방식으로 바인딩할 수 있습니다.

 데이터는 <xref:Microsoft.Office.Tools.Excel.ListObject>와 별개이므로 <xref:Microsoft.Office.Tools.Excel.ListObject>를 통해 직접 수행하지 않고 바인딩된 데이터 세트를 통해 데이터를 추가 및 제거해야 합니다. 바인딩된 데이터 세트의 데이터가 임의 메커니즘을 통해 업데이트되면 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 자동으로 변경 내용을 반영합니다. 자세한 내용은 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)을 참조 하세요.

 <xref:Microsoft.Office.Tools.Excel.ListObject> 를 데이터 원본에 바인딩하여 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 신속하게 채울 수 있습니다. 데이터 바인딩된 <xref:Microsoft.Office.Tools.Excel.ListObject>에서 데이터를 편집하는 경우 데이터 원본에서도 자동으로 변경됩니다. <xref:Microsoft.Office.Tools.Excel.ListObject> 를 채운 다음 데이터 원본을 수정하지 않고 사용자가 <xref:Microsoft.Office.Tools.Excel.ListObject> 의 데이터를 변경할 수 있게 하려면 <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> 메서드를 사용하여 <xref:Microsoft.Office.Tools.Excel.ListObject> 를 데이터 원본에서 분리합니다. 자세한 내용은 [방법: ListObject 컨트롤을 데이터로 채우기](../vsto/how-to-fill-listobject-controls-with-data.md)를 참조 하세요.

> [!NOTE]
> 겹치는 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤에서는 데이터 바인딩이 지원되지 않습니다.

### <a name="improve-performance-in-listobject-controls"></a>ListObject 컨트롤의 성능 향상
 컨트롤을 먼저 바인딩한 다음, <xref:Microsoft.Office.Tools.Excel.ListObject> 을 호출하여 데이터 세트를 채우면 XML 파일을 데이터 바인딩된 <xref:System.Data.DataSet.ReadXml%2A> 컨트롤로 읽어들이는 속도가 느려집니다. 성능을 개선하려면 컨트롤에 바인딩하기 전에 <xref:System.Data.DataSet.ReadXml%2A> 을 호출합니다.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>데이터 원본에서 ListObject 컨트롤 연결 끊기
 데이터 원본에 바인딩하여 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 데이터로 채운 다음 연결을 끊어 목록 개체의 데이터를 수정해도 데이터 원본에 영향을 주지 않도록 할 수 있습니다. 자세한 내용은 [방법: ListObject 컨트롤을 데이터로 채우기](../vsto/how-to-fill-listobject-controls-with-data.md)를 참조 하세요.

### <a name="restore-column-and-row-order"></a>열 및 행 순서 복원
 디자인 타임에 문서에 추가된 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤에 데이터를 바인딩하면 통합 문서를 저장할 때마다 Visual Studio에서 열 및 행 순서를 추적합니다. 런타임 중 사용자가 <xref:Microsoft.Office.Tools.Excel.ListObject> 열 또는 행을 이동하면 다음에 통합 문서가 열릴 때 새 순서가 유지되고 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 데이터 원본에 다시 바인딩됩니다.

 <xref:Microsoft.Office.Tools.Excel.ListObject> 를 원래 열 및 행 순서로 복원하려는 경우 <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> 메서드를 호출할 수 있습니다. 이 메서드는 지정된 <xref:Microsoft.Office.Tools.Excel.ListObject>의 열 및 행 순서와 관련된 사용자 지정 문서 속성을 제거합니다. <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> 의 열 및 행 순서를 유지하지 않으려는 경우 통합 문서의 <xref:Microsoft.Office.Tools.Excel.ListObject>이벤트에서 이 메서드를 호출합니다.

## <a name="format"></a>서식
 <xref:Microsoft.Office.Interop.Excel.ListObject> 에 적용할 수 있는 서식은 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤에 적용할 수 있습니다. 여기에는 테두리, 글꼴, 숫자 서식 및 스타일이 포함됩니다. 최종 사용자는 데이터 바인딩된의 열을 다시 정렬할 수 <xref:Microsoft.Office.Tools.Excel.ListObject> 있으며, <xref:Microsoft.Office.Tools.Excel.ListObject> 가 디자인 타임에 문서에 추가 된 경우 이러한 변경 내용은 문서와 함께 유지 됩니다. 다음에 문서를 열면 목록 개체가 동일한 데이터 원본에 바인딩되지만 열 순서에 사용자가 변경한 내용이 반영됩니다.

## <a name="add-and-remove-columns-at-run-time"></a>런타임에 열 추가 및 제거
 런타임에 데이터 바인딩된 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤에서 수동으로 열을 추가 또는 제거할 수 없습니다. 최종 사용자가 열을 삭제 하려고 하면 즉시 복원 되 고 추가 된 열이 제거 됩니다. 그러므로 사용자에게 데이터에 바인딩된 <xref:Microsoft.Office.Tools.Excel.ListObject> 에서 이러한 작업을 수행할 수 없는 이유를 설명하는 코드를 작성하는 것이 중요합니다. Visual Studio는 데이터 바인딩과 관련된 <xref:Microsoft.Office.Tools.Excel.ListObject> 에 여러 가지 이벤트를 제공합니다. 예를 들어 <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> 이벤트를 사용하여 삭제하려는 데이터를 삭제할 수 없으며 복원되었다는 것을 사용자에게 경고할 수 있습니다.

## <a name="add-and-remove-rows-at-run-time"></a>런타임에 행 추가 및 제거
 데이터 원본에서 새 행 추가를 허용하고 읽기 전용이 아닌 경우 데이터 바인딩된 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤에서 수동으로 행을 추가 및 제거할 수 있습니다. <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> 등의 이벤트에 대해 코드를 작성하여 데이터 유효성을 검사할 수 있습니다. 자세한 내용은 [방법: ListObject 컨트롤에 새 행을 추가할 때 데이터 유효성 검사](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)를 참조 하세요.

 경우에 따라 목록 개체와 데이터 원본의 관계로 인해 일상적인 오류가 발생할 수 있습니다. 예를 들어 <xref:Microsoft.Office.Tools.Excel.ListObject>에 표시하려는 열을 매핑하여, null 값을 사용할 수 없는 필드 등 제한 사항이 있는 열이 누락된 경우 행을 만들 때마다 오류가 발생하도록 할 수 있습니다. <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> 이벤트에 대한 이벤트 처리기에서 누락된 값을 추가하도록 코드를 작성할 수 있습니다.

## <a name="rename-listobject-controls-in-excel"></a>Excel에서 ListObject 컨트롤 이름 바꾸기
 Excel에서는 **디자인** 탭을 사용 하 여 사용자가 런타임에 excel 테이블의 이름을 변경할 수 있습니다. 그러나 컨트롤은 <xref:Microsoft.Office.Tools.Excel.ListObject> 이 기능을 지원 하지 않습니다. 사용자가 <xref:Microsoft.Office.Tools.Excel.ListObject>에 해당하는 Excel 표의 이름을 변경하려고 하면 통합 문서가 저장될 때 Excel 테이블의 이름이 자동으로 원래 이름으로 되돌려집니다.

## <a name="events"></a>이벤트
 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤에 대해 다음 이벤트를 사용할 수 있습니다.

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Change>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>

## <a name="see-also"></a>추가 정보
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [방법: 워크시트에 ListObject 컨트롤 추가](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [방법: ListObject 컨트롤 크기 조정](../vsto/how-to-resize-listobject-controls.md)
- [방법: ListObject 컨트롤에 새 행을 추가할 때 데이터 유효성 검사](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [방법: 데이터에 ListObject 열 매핑](../vsto/how-to-map-listobject-columns-to-data.md)
- [방법: ListObject 컨트롤을 데이터로 채우기](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [방법: 데이터베이스의 데이터로 워크시트 채우기](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
