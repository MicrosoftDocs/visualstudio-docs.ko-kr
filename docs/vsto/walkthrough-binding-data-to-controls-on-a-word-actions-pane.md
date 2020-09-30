---
title: '연습: Word 작업 창의 컨트롤에 데이터 바인딩'
titleSuffix: ''
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
ms.openlocfilehash: 05df38bf6056b392c0b991617316ba2c1c657306
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585069"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>연습: Word 작업 창의 컨트롤에 데이터 바인딩
  이 연습에서는 Word의 작업 창에서 컨트롤에 데이터를 바인딩하는 방법을 보여 줍니다. 컨트롤은 SQL Server 데이터베이스의 테이블 간 마스터/세부 관계를 보여 줍니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 데이터에 바인딩된 Windows Forms 컨트롤을 사용 하 여 작업 창 만들기

- 마스터/세부 관계를 사용 하 여 컨트롤의 데이터를 표시 합니다.

- 응용 프로그램을 열 때 작업 창을 표시 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

- Northwind SQL Server 예제 데이터베이스를 사용 하 여 서버에 액세스 합니다.

- SQL Server 데이터베이스에서 읽고 쓸 수 있는 권한입니다.

## <a name="create-the-project"></a>프로젝트 만들기
 첫 번째 단계에서는 Word 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. **내 Word 작업 창**이라는 이름으로 word 문서 프로젝트를 만듭니다. 마법사에서 **새 문서 만들기**를 선택 합니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio가 디자이너에서 새 Word 문서를 열고 **솔루션 탐색기** **내 word 작업 창** 프로젝트를 추가 합니다.

## <a name="add-controls-to-the-actions-pane"></a>작업 창에 컨트롤 추가
 이 연습에서는 데이터 바인딩된 Windows Forms 컨트롤을 포함 하는 작업 창 컨트롤이 필요 합니다. 프로젝트에 데이터 소스를 추가한 다음 **데이터** 소스 창에서 작업 창 컨트롤로 컨트롤을 끌어 옵니다.

### <a name="to-add-an-actions-pane-control"></a>작업 창 컨트롤을 추가 하려면

1. **솔루션 탐색기**에서 **내 Word 작업 창** 프로젝트를 선택 합니다.

2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

3. **새 항목 추가** 대화 상자에서 **작업 창 컨트롤**을 선택 하 고 이름을 작업 **제어**로 지정한 다음 **추가**를 클릭 합니다.

### <a name="to-add-a-data-source-to-the-project"></a>프로젝트에 데이터 소스를 추가 하려면

1. **데이터 소스** 창이 표시 되지 않는 경우 메뉴 모음에서 **View**  >  **다른 Windows**  >  **데이터 소스**보기를 선택 하 여 표시 합니다.

   > [!NOTE]
   > **데이터 원본 표시** 를 사용할 수 없는 경우 Word 문서를 클릭 한 다음 다시 확인 합니다.

2. **새 데이터 소스 추가** 를 클릭 하 여 **데이터 소스 구성 마법사**를 시작 합니다.

3. **데이터베이스** 를 선택 하 고 **다음**을 클릭 합니다.

4. Northwind 샘플 SQL Server 데이터베이스에 대 한 데이터 연결을 선택 하거나 **새 연결** 단추를 사용 하 여 새 연결을 추가 합니다.

5. **다음**을 클릭합니다.

6. 선택 된 경우 연결을 저장 하는 옵션을 선택 취소 하 고 **다음**을 클릭 합니다.

7. **데이터베이스 개체** 창에서 **테이블** 노드를 확장 합니다.

8. **Suppliers** 및 **Products** 테이블 옆의 확인란을 선택 합니다.

9. **Finish**를 클릭합니다.

   마법사에서 **Suppliers** 테이블 및 **Products** 테이블을 **데이터 소스** 창에 추가 합니다. 또한 **솔루션 탐색기**에 표시 되는 형식화 된 데이터 집합을 프로젝트에 추가 합니다.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>작업 창 컨트롤에 데이터 바인딩된 Windows Forms 컨트롤을 추가 하려면

1. **데이터 소스** 창에서 **Suppliers** 테이블을 확장 합니다.

2. **회사 이름** 노드에서 드롭다운 화살표를 클릭 하 고 **ComboBox**를 선택 합니다.

3. **CompanyName** 을 **데이터 소스** 창에서 작업 창 컨트롤로 끌어 옵니다.

     <xref:System.Windows.Forms.ComboBox>컨트롤은 작업 창 컨트롤에 생성 됩니다. 동시에 <xref:System.Windows.Forms.BindingSource> 명명 된 `SuppliersBindingSource` , 테이블 어댑터 및가 <xref:System.Data.DataSet> 구성 요소 트레이의 프로젝트에 추가 됩니다.

4. `SuppliersBindingNavigator` **구성 요소** 트레이에서를 선택 하 고 **delete**키를 누릅니다. 이 연습에서는를 사용 하지 않습니다 `SuppliersBindingNavigator` .

    > [!NOTE]
    > 을 삭제 `SuppliersBindingNavigator` 해도 해당에 대해 생성 된 코드는 모두 제거 되지 않습니다. 이 코드를 제거할 수 있습니다.

5. 레이블 아래에 있도록 콤보 상자를 이동 하 고 **Size** 속성을 **171, 21**로 변경 합니다.

6. **데이터 소스** 창에서 **Suppliers** 테이블의 자식인 **Products** 테이블을 확장 합니다.

7. **ProductName** 노드에서 드롭다운 화살표를 클릭 하 고 **ListBox**를 선택 합니다.

8. **ProductName** 을 작업 창 컨트롤로 끌어옵니다.

     <xref:System.Windows.Forms.ListBox>컨트롤은 작업 창 컨트롤에 생성 됩니다. 이와 동시에 <xref:System.Windows.Forms.BindingSource> 명명 된 `ProductBindingSource` 및 테이블 어댑터는 구성 요소 트레이에서 프로젝트에 추가 됩니다.

9. 레이블 아래에 있는 목록 상자를 이동 하 고 **Size** 속성을 **171, 95**로 변경 합니다.

10. <xref:System.Windows.Forms.Button> **도구 상자** 에서 작업 창 컨트롤로를 끌어 목록 상자 아래에 놓습니다.

11. 를 마우스 오른쪽 단추로 클릭 하 <xref:System.Windows.Forms.Button> 고 바로 가기 메뉴에서 **속성** 을 클릭 한 후 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**삽입**|
    |**Text**|**삽입**|

12. 컨트롤에 맞게 사용자 정의 컨트롤의 크기를 조정 합니다.

## <a name="set-up-the-data-source"></a>데이터 원본 설정
 데이터 소스를 설정 하려면 <xref:System.Windows.Forms.UserControl.Load> 작업 창 컨트롤의 이벤트에 코드를 추가 하 여 컨트롤을의 데이터로 채우고 <xref:System.Data.DataTable> <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> 각 컨트롤에 대해 및 속성을 설정 합니다.

### <a name="to-load-the-control-with-data"></a>데이터를 사용 하 여 컨트롤을 로드 하려면

1. <xref:System.Windows.Forms.UserControl.Load>클래스의 이벤트 처리기에서 `ActionsControl` 다음 코드를 추가 합니다.

     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]

2. C #에서는 이벤트 처리기를 이벤트에 연결 해야 합니다 <xref:System.Windows.Forms.UserControl.Load> . 호출 후 생성자에이 코드를 추가할 수 있습니다 `ActionsControl` `InitializeComponent` . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]

### <a name="to-set-data-binding-properties-of-the-controls"></a>컨트롤의 데이터 바인딩 속성을 설정 하려면

1. `CompanyNameComboBox` 컨트롤을 선택합니다.

2. **속성** 창에서 **DataSource** 속성의 오른쪽에 있는 단추를 클릭 하 고 **suppliersBindingSource**를 선택 합니다.

3. **Displaymember** 속성의 오른쪽에 있는 단추를 클릭 하 고 **CompanyName**을 선택 합니다.

4. **데이터 바인딩** 속성을 확장 하 고 **텍스트** 속성의 오른쪽에 있는 단추를 클릭 한 다음 **없음**을 선택 합니다.

5. `ProductNameListBox` 컨트롤을 선택합니다.

6. **속성** 창에서 **DataSource** 속성의 오른쪽에 있는 단추를 클릭 하 고 **productsBindingSource**를 선택 합니다.

7. **Displaymember** 속성의 오른쪽에 있는 단추를 클릭 하 고 **ProductName**을 선택 합니다.

8. **데이터 바인딩** 속성을 확장 하 고 **SelectedValue** 속성의 오른쪽에 있는 단추를 클릭 한 다음 **없음**을 선택 합니다.

## <a name="add-a-method-to-insert-data-into-a-table"></a>테이블에 데이터를 삽입 하는 메서드 추가
 다음 작업은 바인딩된 컨트롤에서 데이터를 읽고 Word 문서에서 테이블을 채우는 것입니다. 먼저 테이블의 머리글 서식을 지정 하는 프로시저를 만든 다음 메서드를 추가 하 여 `AddData` Word 테이블을 만들고 서식을 지정 합니다.

### <a name="to-format-the-table-headings"></a>표 머리글의 서식을 지정 하려면

1. 클래스에서 `ActionsControl` 테이블 머리글의 형식을 지정 하는 메서드를 만듭니다.

     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]

### <a name="to-create-the-table"></a>테이블을 만들려면

1. 클래스에서 `ActionsControl` 테이블이 없는 경우 테이블을 만드는 메서드를 작성 하 고 작업 창의 데이터를 테이블에 추가 합니다.

     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]

### <a name="to-insert-text-into-a-word-table"></a>Word 표에 텍스트를 삽입 하려면

1. <xref:System.Windows.Forms.Control.Click> **삽입** 단추의 이벤트 처리기에 다음 코드를 추가 합니다.

     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]

2. C #에서는 단추의 이벤트에 대 한 이벤트 처리기를 만들어야 합니다 <xref:System.Windows.Forms.Control.Click> .  <xref:System.Windows.Forms.UserControl.Load>클래스의 이벤트 처리기에이 코드를 추가할 수 있습니다 `ActionsControl` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]

## <a name="show-the-actions-pane"></a>작업 창 표시
 컨트롤이 컨트롤에 추가 되 면 작업 창이 표시 됩니다.

### <a name="to-show-the-actions-pane"></a>작업 창을 표시 하려면

1. **솔루션 탐색기**에서 **ThisDocument** 또는 **ThisDocument.cs**를 마우스 오른쪽 단추로 클릭 한 다음 바로 가기 메뉴에서 **코드 보기** 를 클릭 합니다.

2. 다음 예제와 같이 클래스의 맨 위에 컨트롤의 새 인스턴스를 만듭니다 `ThisDocument` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]

3. <xref:Microsoft.Office.Tools.Word.Document.Startup>다음 예제와 같이의 이벤트 처리기에 코드를 추가 `ThisDocument` 합니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 문서를 테스트 하 여 문서를 열 때 작업 창이 표시 되는지 확인할 수 있습니다. 작업 창의 컨트롤에서 마스터/세부 관계를 테스트 하 고 **삽입** 단추를 클릭할 때 Word 테이블에서 데이터가 채워지는지 확인 합니다.

### <a name="to-test-your-document"></a>문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 작업 창이 표시 되는지 확인 합니다.

3. 콤보 상자에서 회사를 선택 하 고 **제품** 목록 상자의 항목이 변경 되었는지 확인 합니다.

4. 제품을 선택 하 고 작업 창에서 **삽입** 을 클릭 한 다음 제품 정보가 Word의 테이블에 추가 되었는지 확인 합니다.

5. 다양 한 회사의 추가 제품을 삽입 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 Word의 작업 창에서 컨트롤에 데이터를 바인딩하는 기본적인 방법을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- Excel의 컨트롤에 데이터 바인딩 자세한 내용은 [연습: Excel 작업 창의 컨트롤에 데이터 바인딩](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)을 참조 하세요.

- 프로젝트를 배포 합니다. 자세한 내용은 [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [작업 창 개요](../vsto/actions-pane-overview.md)
- [방법: Word 문서 또는 Excel 통합 문서에 작업 창 추가](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
