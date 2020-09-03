---
title: '연습: Excel 작업 창의 컨트롤에 데이터 바인딩'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1543f872961d556674dd5ad6b3f5b8071d2d404b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253891"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>연습: Excel 작업 창의 컨트롤에 데이터 바인딩
  이 연습에서는 Microsoft Office Excel의 작업 창에서 컨트롤에 데이터를 바인딩하는 방법을 보여 줍니다. 컨트롤은 SQL Server 데이터베이스의 테이블 간 마스터/세부 관계를 보여 줍니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 워크시트에 컨트롤 추가

- 작업 창 컨트롤을 만듭니다.

- 작업 창 컨트롤에 데이터 바인딩된 Windows Forms 컨트롤 추가

- 응용 프로그램을 열 때 작업 창을 표시 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- Northwind SQL Server 예제 데이터베이스를 사용 하 여 서버에 액세스 합니다.

- SQL Server 데이터베이스에서 읽고 쓸 수 있는 권한입니다.

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 첫 번째 단계에서 Excel 통합 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. **내 Excel 작업 창**이름으로 Excel 통합 문서 프로젝트를 만듭니다. 마법사에서 **새 문서 만들기**를 선택 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio가 디자이너에서 새 Excel 통합 문서를 열고 **내 Excel 작업 창** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

## <a name="add-a-new-data-source-to-the-project"></a>프로젝트에 새 데이터 소스 추가

### <a name="to-add-a-new-data-source-to-the-project"></a>프로젝트에 새 데이터 원본을 추가 하려면

1. **데이터 소스** 창이 표시 되지 않으면 메뉴 모음에서 **View**  >  **다른 Windows**  >  **데이터 소스**보기를 선택 하 여 표시 합니다.

2. **새 데이터 소스 추가** 를 선택하여 **데이터 소스 구성 마법사**를 시작합니다.

3. **데이터베이스** 를 선택 하 고 **다음**을 클릭 합니다.

4. Northwind 샘플 SQL Server 데이터베이스에 대 한 데이터 연결을 선택 하거나 **새 연결** 단추를 사용 하 여 새 연결을 추가 합니다.

5. **다음**을 클릭합니다.

6. 선택 된 경우 연결을 저장 하는 옵션을 선택 취소 하 고 **다음**을 클릭 합니다.

7. **데이터베이스 개체** 창에서 **테이블** 노드를 확장 합니다.

8. **Suppliers** 테이블 옆의 확인란을 선택 합니다.

9. **Products** 테이블을 확장 하 고 **ProductName**, **공급자**, **QuantityPerUnit**및 **UnitPrice**를 선택 합니다.

10. **마침**을 클릭합니다.

    마법사에서 **Suppliers** 테이블 및 **Products** 테이블을 **데이터 소스** 창에 추가 합니다. 또한 **솔루션 탐색기**에 표시 되는 형식화 된 데이터 집합을 프로젝트에 추가 합니다.

## <a name="add-controls-to-the-worksheet"></a>워크시트에 컨트롤 추가
 그런 다음, <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> 첫 번째 워크시트에 컨트롤과 컨트롤을 추가 합니다.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>NamedRange 컨트롤 및 ListObject 컨트롤을 추가 하려면

1. Visual Studio 디자이너에서 **내 Excel 작업 Pane.xlsx** 통합 문서가 열려 있는지 확인 하 고 `Sheet1` 표시 합니다.

2. **데이터 소스** 창에서 **Suppliers** 테이블을 확장 합니다.

3. **회사 이름** 노드에서 드롭다운 화살표를 클릭 한 다음 **NamedRange**를 클릭 합니다.

4. **데이터 소스** 창에서 셀 **A2** 로 **회사 이름을** 끌어 옵니다 `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.NamedRange>이라는 컨트롤이 `CompanyNameNamedRange` 만들어지고 텍스트가 \<CompanyName> **A2**셀에 표시 됩니다. 동시에 <xref:System.Windows.Forms.BindingSource> 명명 된 `suppliersBindingSource` , 테이블 어댑터 및가 <xref:System.Data.DataSet> 프로젝트에 추가 됩니다. 컨트롤이에 바인딩되고이는 <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> 인스턴스에 바인딩됩니다.

5. **데이터 소스** 창에서 **Suppliers** 테이블 아래의 열을 뒤로 스크롤합니다. 목록의 맨 아래에 **Products** 테이블이 있습니다. **Suppliers** 테이블의 자식 이기 때문에 여기에 있습니다. **Suppliers** 테이블과 같은 수준의 **Products** 테이블을 선택 하 고 표시 되는 드롭다운 화살표를 클릭 합니다.

6. 드롭다운 목록에서 **ListObject** 를 클릭 한 다음 **Products** 테이블을에서 **A6** 셀로 끕니다 `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.ListObject>이라는 컨트롤이 `ProductNameListObject` **A6**셀에 만들어집니다. 동시에 <xref:System.Windows.Forms.BindingSource> 명명 된 `productsBindingSource` 와 테이블 어댑터가 프로젝트에 추가 됩니다. 컨트롤이에 바인딩되고이는 <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> 인스턴스에 바인딩됩니다.

7. C #의 경우에만 구성 요소 트레이에서 **suppliersBindingSource** 를 선택 하 고 **속성** 창에서 **Modifiers** 속성을 **Internal** 로 변경 합니다.

## <a name="add-controls-to-the-actions-pane"></a>작업 창에 컨트롤 추가
 다음에는 콤보 상자가 있는 작업 창 컨트롤이 필요 합니다.

### <a name="to-add-an-actions-pane-control"></a>작업 창 컨트롤을 추가 하려면

1. **솔루션 탐색기**에서 **내 Excel 작업 창** 프로젝트를 선택 합니다.

2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

3. **새 항목 추가** 대화 상자에서 **작업 창 컨트롤**을 선택 하 고 이름을 작업 **제어**로 선택한 다음 **추가**를 클릭 합니다.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>작업 창 컨트롤에 데이터 바인딩된 Windows Forms 컨트롤을 추가 하려면

1. **도구 상자**의 **공용 컨트롤** 탭에서 <xref:System.Windows.Forms.ComboBox> 컨트롤을 작업 창 컨트롤로 끌어 옵니다.

2. **Size** 속성을 **171, 21**로 변경 합니다.

3. 콤보 상자에 맞게 사용자 정의 컨트롤의 크기를 조정 합니다.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>작업 창의 컨트롤을 데이터에 바인딩
 이 섹션에서는의 데이터 원본을 <xref:System.Windows.Forms.ComboBox> 워크시트의 컨트롤과 동일한 데이터 원본으로 설정 합니다 <xref:Microsoft.Office.Tools.Excel.NamedRange> .

### <a name="to-set-data-binding-properties-of-the-control"></a>컨트롤의 데이터 바인딩 속성을 설정 하려면

1. 작업 창 컨트롤을 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

2. <xref:System.Windows.Forms.UserControl.Load>작업 창 컨트롤의 이벤트에 다음 코드를 추가 합니다.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. C #에서는에 대 한 이벤트 처리기를 만들어야 합니다 `ActionsControl` . 생성자에이 코드를 추가할 수 있습니다 `ActionsControl` . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>작업 창 표시
 런타임에 컨트롤을 추가할 때까지 작업 창이 표시 되지 않습니다.

#### <a name="to-show-the-actions-pane"></a>작업 창을 표시 하려면

1. **솔루션 탐색기**에서 *ThisWorkbook* 또는 *ThisWorkbook.cs*를 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

2. 클래스에 사용자 정의 컨트롤의 새 인스턴스를 만듭니다 `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>의 이벤트 처리기에서 `ThisWorkbook` 컨트롤을 작업 창에 추가 합니다.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 문서를 테스트 하 여 문서를 열 때 작업 창이 열리고 컨트롤에 마스터/세부 정보 관계가 있는지 확인할 수 있습니다.

### <a name="to-test-your-document"></a>문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 작업 창이 표시 되는지 확인 합니다.

3. 목록 상자에서 회사를 선택 합니다. 회사 이름이 컨트롤에 표시 되 <xref:Microsoft.Office.Tools.Excel.NamedRange> 고 제품 정보가 컨트롤에 나열 되는지 확인 합니다 <xref:Microsoft.Office.Tools.Excel.ListObject> .

4. 회사 이름 및 제품 세부 정보를 적절 하 게 변경 하려면 다양 한 회사를 선택 합니다.

## <a name="next-steps"></a>다음 단계
 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- Word의 컨트롤에 데이터 바인딩 자세한 내용은 [연습: Word 작업 창의 컨트롤에 데이터 바인딩](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)을 참조 하세요.

- 프로젝트를 배포 합니다. 자세한 내용은 [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [작업 창 개요](../vsto/actions-pane-overview.md)
- [방법: 작업 창에서 컨트롤 레이아웃 관리](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
