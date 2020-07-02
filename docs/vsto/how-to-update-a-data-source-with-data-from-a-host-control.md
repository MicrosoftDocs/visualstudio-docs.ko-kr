---
title: '방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8384b35583517a832763f5229d2b526ca10190ad
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541247"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트
  호스트 컨트롤을 데이터 원본에 바인딩하고 해당 데이터 원본을 컨트롤에 있는 데이터의 변경 내용으로 업데이트할 수 있습니다. 이 프로세스는 크게 다음과 같은 두 가지 단계로 구성되어 있습니다.

1. 컨트롤에 있는 수정된 데이터로 메모리 내 데이터 원본을 업데이트합니다. 일반적으로 메모리 내 데이터 원본은 <xref:System.Data.DataSet>, <xref:System.Data.DataTable>또는 일부 다른 데이터 개체입니다.

2. 데이터베이스를 메모리 내 데이터 원본의 변경된 데이터로 업데이트합니다. 이 작업은 데이터 원본이 SQL Server 또는 Microsoft Office Access 데이터베이스와 같이 백 엔드 데이터베이스에 연결된 경우에만 가능합니다.

   호스트 컨트롤 및 데이터 바인딩에 대 한 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md) 및 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)을 참조 하세요.

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>메모리 내 데이터 원본 업데이트
 기본적으로 단순 데이터 바인딩(Word 문서의 콘텐츠 컨트롤 또는 Excel 워크시트의 명명된 범위 컨트롤 등)을 사용하도록 설정된 호스트 컨트롤은 데이터 변경 내용을 메모리 내 데이터 원본에 저장하지 않습니다. 즉, 최종 사용자가 호스트 컨트롤에서 값을 변경한 다음 컨트롤에서 벗어나면 컨트롤의 새 값이 데이터 원본에 자동으로 저장되지 않습니다.

 데이터 원본에 데이터를 저장하려면 런타임에 특정 이벤트에 대한 응답으로 데이터 원본을 업데이트하는 코드를 작성하거나, 컨트롤의 값이 변경되면 자동으로 데이터를 업데이트하도록 컨트롤을 구성하면 됩니다.

 <xref:Microsoft.Office.Tools.Excel.ListObject> 변경 내용을 메모리 내 데이터 원본에 저장할 필요가 없습니다. <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 데이터에 바인딩하면 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤은 추가 코드를 요구하지 않고 자동으로 변경 내용을 메모리 내 데이터 원본에 저장합니다.

### <a name="to-update-the-in-memory-data-source-at-run-time"></a>런타임에 메모리 내 데이터 원본을 업데이트하려면

- 컨트롤을 데이터 원본에 바인딩하는 <xref:System.Windows.Forms.Binding.WriteValue%2A> 개체의 <xref:System.Windows.Forms.Binding> 메서드를 호출합니다.

     다음 예제에서는 Excel 워크시트의 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤의 변경 내용을 데이터 원본에 저장합니다. 이 예제에서는 해당 <xref:Microsoft.Office.Tools.Excel.NamedRange> 속성이 데이터 원본의 필드에 바인딩된 `namedRange1` 이라는 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 컨트롤이 있다고 가정합니다.

     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]

### <a name="automatically-update-the-in-memory-data-source"></a>자동으로 메모리 내 데이터 원본 업데이트
 또한 메모리 내 데이터 원본을 자동으로 업데이트하도록 컨트롤을 구성할 수도 있습니다. 문서 수준 프로젝트에서는 코드 또는 디자이너를 사용하여 이 작업을 수행할 수 있습니다. VSTO 추가 기능 프로젝트에서는 코드를 사용 해야 합니다.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>코드를 사용하여 메모리 내 데이터 원본을 자동으로 업데이트하도록 컨트롤을 설정하려면

1. <xref:System.Windows.Forms.Binding>컨트롤을 데이터 소스에 바인딩하는 개체의 OnPropertyChanged 모드를 사용 합니다. 다음 두 가지 옵션으로 데이터 원본을 업데이트할 수 있습니다.

   - 컨트롤의 유효성을 검사할 때 데이터 원본을 업데이트 하려면이 속성을 DataSourceUpdateMode로 설정 합니다.

   - 컨트롤의 데이터 바인딩된 속성 값이 변경 될 때 데이터 원본을 업데이트 하려면이 속성을 OnPropertyChanged로 설정 합니다. DataSourceUpdateMode.

     > [!NOTE]
     > Word는 문서 변경 또는 컨트롤 변경 알림을 제공 하지 않기 때문에 DataSourceUpdateMode OnPropertyChanged 옵션은 Word 호스트 컨트롤에는 적용 되지 않습니다. 그러나 Word 문서의 Windows Forms 컨트롤에 대해서는 이 옵션을 사용할 수 있습니다.

     다음 예제에서는 컨트롤의 값이 변경될 때 자동으로 데이터 원본을 업데이트하기 위해 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 구성합니다. 이 예제에서는 해당 <xref:Microsoft.Office.Tools.Excel.NamedRange> 속성이 데이터 원본의 필드에 바인딩된 `namedRange1` 이라는 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 컨트롤이 있다고 가정합니다.

     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>디자이너를 사용하여 자동으로 메모리 내 데이터 원본을 업데이트하도록 컨트롤을 설정하려면

1. Visual Studio의 디자이너에서 Word 문서 또는 Excel 통합 문서를 엽니다.

2. 데이터 원본을 자동으로 업데이트하려는 컨트롤을 클릭합니다.

3. **속성** 창에서 **(DataBindings)** 속성을 확장합니다.

4. **(고급)** 속성 옆에 있는 줄임표 단추 (![VisualStudioEllipsesButton 스크린 샷](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton 스크린 샷"))를 클릭 합니다.

5. **서식 지정 및 고급 바인딩** 대화 상자에서 **데이터 원본 업데이트 모드** 드롭다운 목록을 클릭하고 다음 값 중 하나를 선택합니다.

    - 컨트롤의 유효성을 검사할 때 데이터 원본을 업데이트하려면 **OnValidation**을 선택합니다.

    - 컨트롤의 데이터 바인딩된 속성 값이 변경될 때 데이터 원본을 업데이트하려면 **OnPropertyChanged**를 선택합니다.

        > [!NOTE]
        > **OnPropertyChanged** 옵션은 Word 호스트 컨트롤에는 적용되지 않습니다. Word가 문서 변경 또는 컨트롤 변경 알림을 제공하지 않기 때문입니다. 그러나 Word 문서의 Windows Forms 컨트롤에 대해서는 이 옵션을 사용할 수 있습니다.

6. **서식 지정 및 고급 바인딩** 대화 상자를 닫습니다.

## <a name="update-the-database"></a>데이터베이스 업데이트
 메모리 내 데이터 원본이 데이터베이스와 연결된 경우 데이터베이스를 데이터 원본에 대한 변경 내용으로 업데이트해야 합니다. 데이터베이스를 업데이트 하는 방법에 대 한 자세한 내용은 [데이터를 데이터베이스에 다시 저장](../data-tools/save-data-back-to-the-database.md) 하 고 [TableAdapter를 사용 하 여 데이터 업데이트](../data-tools/update-data-by-using-a-tableadapter.md) 를 참조 하세요.

### <a name="to-update-the-database"></a>데이터베이스를 업데이트하려면

1. 컨트롤에 대한 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 의 <xref:System.Windows.Forms.BindingSource> 메서드를 호출합니다.

     디자인 타임에 데이터 바인딩된 컨트롤을 문서나 통합 문서에 추가하면 <xref:System.Windows.Forms.BindingSource> 가 자동으로 생성됩니다. <xref:System.Windows.Forms.BindingSource>는 해당 컨트롤을 프로젝트의 형식화된 데이터 세트에 연결합니다. 자세한 내용은 [BindingSource 구성 요소 개요](/dotnet/framework/winforms/controls/bindingsource-component-overview)를 참조 하세요.

     다음 코드 예제에서는 프로젝트가 <xref:System.Windows.Forms.BindingSource> 라는 `customersBindingSource`를 포함하고 있다고 가정합니다.

     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]

2. `Update`프로젝트에서 생성 된 TableAdapter의 메서드를 호출 합니다.

     TableAdapter는 디자인 타임에 데이터 바인딩된 컨트롤을 문서 또는 통합 문서에 추가할 때 자동으로 생성 됩니다. TableAdapter는 프로젝트의 형식화 된 데이터 집합을 데이터베이스에 연결 합니다. 자세한 내용은 [TableAdapter 개요](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)를 참조 하세요.

     다음 코드 예에서는 Northwind 데이터베이스의 Customers 테이블에 대 한 연결이 있고 프로젝트에 이름이 인 TableAdapter와 이라는 형식화 된 데이터 집합이 포함 되어 있다고 가정 합니다 `customersTableAdapter` `northwindDataSet` .

     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]

## <a name="see-also"></a>참고 항목
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
- [TableAdapter를 사용하여 데이터 업데이트](../data-tools/update-data-by-using-a-tableadapter.md)
- [방법: 워크시트에서 데이터베이스 레코드 스크롤](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [방법: 데이터베이스의 데이터로 워크시트 채우기](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [방법: 개체의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [방법: 데이터베이스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [방법: 서비스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-services.md)
