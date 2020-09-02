---
title: Office 솔루션의 컨트롤에 데이터 바인딩
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93e2d5abb9c8fda9d4a1300a9bb0958ac9266499
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986167"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Office 솔루션의 컨트롤에 데이터 바인딩
  컨트롤이 자동으로 데이터를 표시할 수 있도록 Windows Forms 컨트롤 및 Microsoft Office Word 문서 또는 Microsoft Office Excel 워크시트의 *호스트 컨트롤* 을 데이터 원본에 바인딩할 수 있습니다. 애플리케이션 수준과 문서 수준 프로젝트 둘 다 데이터를 컨트롤에 바인딩할 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 호스트 컨트롤은 Word의 콘텐츠 컨트롤 및 Excel의 명명된 범위와 같이 Word 및 Excel 개체 모델에 있는 개체를 확장합니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

 Windows Forms와 호스트 컨트롤 모두 데이터 세트 및 데이터 테이블 같은 데이터 원본에 대해 *단순 데이터 바인딩*과 *복합 데이터 바인딩*을 둘 다 지원하는 Windows Forms 데이터 바인딩 모델을 사용합니다. Windows Forms의 데이터 바인딩 모델에 대 한 자세한 내용은 [데이터 바인딩 및 Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)를 참조 하세요.

## <a name="simple-data-binding"></a>단순 데이터 바인딩
 단순 데이터 바인딩은 컨트롤 속성이 데이터 테이블의 값 등 단일 데이터 요소에 바인딩될 때 존재합니다. 예를 들어 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤은 데이터 세트의 필드로 바인딩될 수 있는 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 속성을 가집니다. 데이터 세트의 필드가 변경되면 명명된 범위의 값도 변경됩니다. <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤을 제외한 모든 호스트 컨트롤은 단일 데이터 바인딩을 지원합니다. <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤은 컬렉션이므로 데이터 바인딩을 지원하지 않습니다.

 호스트 컨트롤에 대한 단순 데이터 바인딩을 수행하려면 <xref:System.Windows.Forms.Binding>을 해당 컨트롤의 `DataBindings` 속성에 추가합니다. <xref:System.Windows.Forms.Binding> 개체는 컨트롤의 속성 값과 데이터 요소 값 사이의 단순 바인딩을 나타냅니다.

 다음 예제에서는 문서 수준 프로젝트에서 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 속성을 데이터 요소에 바인딩하는 방법에 대해 설명합니다.

 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]

 간단한 데이터 바인딩을 보여 주는 연습은 연습: 문서 수준 프로젝트에 대 한 [문서 수준 프로젝트의 단순 데이터 바인딩](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) 및 연습: vsto 추가 기능 프로젝트에 대 한 [vsto 추가 기능 프로젝트의 단순 데이터 바인딩](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) 을 참조 하세요.

## <a name="complex-data-binding"></a>복합 데이터 바인딩
 복합 데이터 바인딩은 컨트롤 속성이 데이터 테이블의 여러 열과 같이 둘 이상의 데이터 요소에 바인딩될 때 존재합니다. Excel용 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤은 복합 데이터 바인딩을 지원하는 유일한 호스트 컨트롤입니다. 또한 <xref:System.Windows.Forms.DataGridView> 컨트롤 같이 복합 데이터 바인딩을 지원하는 많은 Windows Forms 컨트롤이 있을 수 있습니다.

 복합 데이터 바인딩을 수행하려면 컨트롤의 `DataSource` 속성을 복합 데이터 바인딩에서 지원되는 데이터 원본 개체로 설정합니다. 예를 들어 <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> 컨트롤의 <xref:Microsoft.Office.Tools.Excel.ListObject> 속성은 데이터 테이블의 여러 열에 바인딩될 수 있습니다. 데이터 테이블의 모든 데이터는 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤에 나타나며 데이터 테이블의 데이터가 변경되면 <xref:Microsoft.Office.Tools.Excel.ListObject> 역시 변경됩니다. 복합 데이터 바인딩에 사용할 수 있는 데이터 원본 목록은 [Windows Forms에서 지 원하는 데이터 원본](/dotnet/framework/winforms/data-sources-supported-by-windows-forms)을 참조 하세요.

 다음 코드 예제는 두 개의 <xref:System.Data.DataSet> 개체를 사용하여 <xref:System.Data.DataTable> 를 만들고 테이블 중 하나를 데이터로 채웁니다. 그런 다음 코드가 <xref:Microsoft.Office.Tools.Excel.ListObject> 를 데이터가 포함된 테이블에 바인딩합니다. 이 예제는 Excel 문서 수준 프로젝트에 대한 것입니다.

 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]

 복합 데이터 바인딩을 보여 주는 연습은 연습: 문서 수준 프로젝트에 대 한 [문서 수준 프로젝트의 복합 데이터 바인딩](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) 및 연습: vsto 추가 기능 프로젝트에 대 한 [vsto 추가 기능 프로젝트의 복합 데이터 바인딩](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) 을 참조 하세요.

## <a name="display-data-in-documents-and-workbooks"></a>문서 및 통합 문서에 데이터 표시
 문서 수준 프로젝트에서 **데이터 원본** 창을 사용하여 데이터 바인딩된 컨트롤을 문서 또는 통합 문서에 쉽게 추가할 수 있으며 같은 방식으로 Windows Forms에도 사용할 수 있습니다. **데이터 소스** 창을 사용 하는 방법에 대 한 자세한 내용은 [Visual Studio에서 데이터에 컨트롤 Windows Forms 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) 및 [새 데이터 소스 추가](../data-tools/add-new-data-sources.md)를 참조 하세요.

### <a name="drag-controls-from-the-data-sources-window"></a>데이터 소스 창에서 컨트롤 끌기
 개체를 **데이터 원본** 창에서 끌어 문서에 놓으면 컨트롤이 만들어집니다. 만들어진 컨트롤의 유형은 데이터의 단일 열 또는 여러 열을 바인딩하는지 여부에 따라 달라집니다.

 Excel의 경우 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 각 개별 필드의 워크시트에서 만들어지며 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 여러 열과 행을 포함하는 각 데이터 범위에 대해 만들어집니다. **데이터 원본** 창에서 테이블 또는 필드를 선택한 다음 드롭다운 목록에서 다른 컨트롤을 선택하여 이 기본값을 변경할 수 있습니다.

 <xref:Microsoft.Office.Tools.Word.ContentControl> 컨트롤이 문서에 추가됩니다. 콘텐츠 컨트롤의 형식은 선택한 필드의 데이터 형식에 따라 달라집니다.

### <a name="bind-data-in-document-level-projects-at-design-time"></a>디자인 타임에 문서 수준 프로젝트에서 데이터 바인딩
 다음 항목은 디자인 타임에 데이터를 바인딩하는 예제를 보여 줍니다.

- [방법: 데이터베이스의 데이터로 워크시트 채우기](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [방법: 데이터베이스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [방법: 개체의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [방법: 서비스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-services.md)

- [방법: 워크시트에서 데이터베이스 레코드 스크롤](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)

### <a name="bind-data-in-vsto-add-in-projects"></a>VSTO 추가 기능 프로젝트에서 데이터 바인딩
 VSTO 추가 기능 프로젝트에서는 런타임에만 컨트롤을 추가할 수 있습니다. 다음 항목에서 런타임에 데이터를 바인딩하는 예제를 보여 줍니다.

- [연습: VSTO 추가 기능 프로젝트의 단순 데이터 바인딩](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)

- [연습: VSTO 추가 기능 프로젝트의 복합 데이터 바인딩](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="update-data-that-is-bound-to-host-controls"></a>호스트 컨트롤에 바인딩되는 데이터 업데이트
 데이터 원본과 호스트 컨트롤 간의 데이터 바인딩은 양방향 데이터 업데이트를 포함합니다. 단순 데이터 바인딩에서 데이터 원본을 변경하면 호스트 컨트롤에 자동으로 반영되지만 호스트 컨트롤을 변경하면 데이터 원본을 업데이트하기 위해 명시적 호출이 필요합니다. 그 이유는 다른 데이터 바인딩 필드가 함께 변경되지 않으면 한 데이터 바인딩 필드의 변경 내용이 적용되지 않는 경우가 있기 때문입니다. 예를 들어 한 필드는 기간이고 다른 한 필드는 경험한 햇수를 나타내는 두 개의 필드가 있을 수 있습니다. 경험은 기간을 초과할 수 없습니다. 사용자가 기간을 50에서 25로 업데이트하고 경험을 30에서 10으로 업데이트하려면 이 두 필드를 동시에 변경해야 합니다. 이 문제를 해결하기 위해, 코드로 업데이트를 명시적으로 보내야만 단일 데이터 바인딩을 사용하는 필드가 업데이트됩니다.

 솔루션이 다음 중 하나를 사용하는 경우, 단순 데이터 바인딩을 사용하는 호스트 컨트롤에서 데이터 원본을 업데이트하려면 메모리 내 데이터 원본( <xref:System.Data.DataSet> 또는 <xref:System.Data.DataTable>) 및 백 엔드 데이터베이스로 업데이트를 보내야 합니다.

 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 사용해 복합 데이터 바인딩을 수행하는 경우는 메모리 내 데이터 원본을 명시적으로 업데이트 할 필요가 없습니다. 이 경우 추가 코드 없이 변경 내용을 자동으로 메모리 내 데이터 원본으로 보냅니다.

 자세한 내용은 [방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [데이터 바인딩 및 Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [방법: Windows Form에 단순 바인딩된 컨트롤 만들기](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
- [TableAdapter를 사용하여 데이터 업데이트](../data-tools/update-data-by-using-a-tableadapter.md)
- [데이터 캐시](../vsto/caching-data.md)
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
