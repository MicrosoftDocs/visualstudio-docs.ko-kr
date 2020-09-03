---
title: '연습: VSTO 추가 기능 프로젝트의 복합 데이터 바인딩'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99caf87000ea9df9260e8926eee4c7136bc9b848
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985490"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>연습: VSTO 추가 기능 프로젝트의 복합 데이터 바인딩
  VSTO 추가 기능 프로젝트에서 호스트 컨트롤 및 Windows Forms 컨트롤에 데이터를 바인딩할 수 있습니다. 이 연습에서는 Microsoft Office Excel 워크시트에 컨트롤을 추가하고 런타임에 컨트롤을 데이터에 바인딩하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 런타임에 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 워크시트에 추가

- 컨트롤을 데이터 세트 인스턴스에 연결하는 <xref:System.Windows.Forms.BindingSource> 만들기.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- `AdventureWorksLT` 샘플 데이터베이스가 연결된 SQL Server 2005 또는 SQL Server 2005 Express의 실행 중인 인스턴스 액세스 권한 `AdventureWorksLT` [SQL Server 샘플 GitHub 리포지토리](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)에서 데이터베이스를 다운로드할 수 있습니다. 데이터베이스 연결에 대한 자세한 내용은 다음 항목을 참조하세요.

  - SQL Server Management Studio 또는 SQL Server Management Studio Express를 사용 하 여 데이터베이스를 연결 하려면 [방법: 데이터베이스 연결 (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database)을 참조 하세요.

  - 명령줄을 사용 하 여 데이터베이스를 연결 하려면 [방법: SQL Server Express에 데이터베이스 파일 연결](/previous-versions/sql/)을 참조 하세요.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 첫 번째 단계는 Excel VSTO 추가 기능 프로젝트를 만드는 것입니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. Visual Basic 또는 C#을 사용하여 **데이터베이스에서 워크시트 채우기**라는 이름으로 Excel VSTO 추가 기능 프로젝트를 만듭니다.

     자세한 내용은 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)을 참조하세요.

     Visual Studio에서 `ThisAddIn.vb` 또는 `ThisAddIn.cs` 파일을 열고 **데이터베이스에서 워크시트 채우기** 프로젝트를 **솔루션 탐색기**에 추가합니다.

## <a name="create-a-data-source"></a>데이터 소스 만들기
 **데이터 원본** 창을 사용하여 형식화된 데이터 세트를 프로젝트에 추가합니다.

### <a name="to-add-a-typed-dataset-to-the-project"></a>프로젝트에 형식화된 데이터 세트를 추가하려면

1. **데이터 소스** 창이 표시 되지 않는 경우 메뉴 모음에서 **View**  >  **다른 Windows**  >  **데이터 소스**보기를 선택 하 여 표시 합니다.

2. **새 데이터 소스 추가** 를 선택하여 **데이터 소스 구성 마법사**를 시작합니다.

3. **데이터베이스**를 클릭하고 **다음**을 클릭합니다.

4. `AdventureWorksLT` 데이터베이스에 대한 기존 연결이 있는 경우 이 연결을 선택하고 **다음**을 클릭합니다.

    그렇지 않은 경우 **새 연결**을 클릭하고 **연결 추가** 대화 상자를 사용하여 새 연결을 만듭니다. 자세한 내용은 [새 연결 추가](../data-tools/add-new-connections.md)를 참조 하세요.

5. **애플리케이션 구성 파일에 연결 문자열 저장** 페이지에서 **다음**을 클릭합니다.

6. **데이터베이스 개체 선택** 페이지에서 **테이블** 을 확장하고 **Address(SalesLT)** 를 선택합니다.

7. **마침**을 클릭합니다.

    *Adventureworksltdataset.xsd 파일이* 파일이 **솔루션 탐색기**에 추가 됩니다. 이 파일은 다음 항목을 정의합니다.

   - `AdventureWorksLTDataSet`라는 형식화된 데이터 세트. 이 데이터 세트는 AdventureWorksLT 데이터베이스의 **Address(SalesLT)** 테이블의 내용을 나타냅니다.

   - 라는 TableAdapter `AddressTableAdapter` 입니다. 이 TableAdapter를 사용 하 여에서 데이터를 읽고 쓸 수 있습니다 `AdventureWorksLTDataSet` . 자세한 내용은 [TableAdapter 개요](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)를 참조 하세요.

     이 연습 뒷부분에서는 이러한 두 개체를 모두 사용합니다.

## <a name="create-controls-and-bind-controls-to-data"></a>컨트롤 만들기 및 데이터에 컨트롤 바인딩
 이 연습에서 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤은 사용자가 통합 문서를 여는 즉시 선택한 테이블의 모든 데이터를 표시합니다. 목록 개체는 <xref:System.Windows.Forms.BindingSource> 를 사용하여 데이터베이스에 컨트롤을 연결합니다.

 컨트롤을 데이터에 바인딩하는 방법에 대 한 자세한 내용은 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)을 참조 하세요.

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>목록 개체, 데이터 세트 및 테이블 어댑터를 추가하려면

1. `ThisAddIn` 클래스에서 다음 컨트롤을 선언하여 `Address` 데이터 세트의 `AdventureWorksLTDataSet` 테이블을 표시합니다.

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. `ThisAddIn_Startup` 메서드에서 다음 코드를 추가하여 데이터 세트를 초기화하고 `AdventureWorksLTDataSet` 데이터 세트의 정보로 데이터 세트를 채웁니다.

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. `ThisAddIn_Startup` 메서드에 다음 코드를 추가합니다. 그러면 워크시트를 확장하는 호스트 항목이 생성됩니다. 자세한 내용은 [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조 하세요.

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. 범위를 만들고 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤을 추가합니다.

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. `AdventureWorksLTDataSet` 를 사용하여 목록 개체를 <xref:System.Windows.Forms.BindingSource>에 바인딩합니다. 목록 개체에 바인딩하려는 열의 이름을 전달합니다.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>추가 기능 테스트
 Excel을 열면 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 `Address` 데이터 세트의 `AdventureWorksLTDataSet` 테이블에 있는 데이터를 표시합니다.

### <a name="to-test-the-vsto-add-in"></a>VSTO 추가 기능을 테스트하려면

- **F5**키를 누릅니다.

     <xref:Microsoft.Office.Tools.Excel.ListObject> 라는 `addressListObject` 컨트롤이 워크시트에 만들어집니다. 동시에 `adventureWorksLTDataSet`라는 데이터 세트 개체와 <xref:System.Windows.Forms.BindingSource>라는 `addressBindingSource`가 프로젝트에 추가됩니다. <xref:Microsoft.Office.Tools.Excel.ListObject>가 <xref:System.Windows.Forms.BindingSource>에 바인딩되고 데이터 세트 개체에 바인딩됩니다.

## <a name="see-also"></a>추가 정보

- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [방법: 데이터베이스의 데이터로 워크시트 채우기](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [방법: 데이터베이스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [방법: 서비스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-services.md)
- [방법: 개체의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [방법: 워크시트에서 데이터베이스 레코드 스크롤](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [연습: 문서 수준 프로젝트의 단순 데이터 바인딩](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [연습: 문서 수준 프로젝트의 복합 데이터 바인딩](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Office 솔루션에서 로컬 데이터베이스 파일 사용 개요](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [새 데이터 원본 추가](../data-tools/add-new-data-sources.md)
- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Office 솔루션에서 로컬 데이터베이스 파일 사용 개요](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource 구성 요소 개요](/dotnet/framework/winforms/controls/bindingsource-component-overview)
