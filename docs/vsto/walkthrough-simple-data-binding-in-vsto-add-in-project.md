---
title: '연습: VSTO 추가 기능 프로젝트의 단순 데이터 바인딩'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 67264800fd2baa1ca685bcc578fb4d400e6538dd
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584913"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>연습: VSTO 추가 기능 프로젝트의 단순 데이터 바인딩

VSTO 추가 기능 프로젝트에서 호스트 컨트롤 및 Windows Forms 컨트롤에 데이터를 바인딩할 수 있습니다. 이 연습에서는 Microsoft Office Word 문서에 컨트롤을 추가하고 런타임에 데이터에 컨트롤을 바인딩하는 방법을 보여 줍니다.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

이 연습에서는 다음 작업을 수행합니다.

- 런타임에 문서에 <xref:Microsoft.Office.Tools.Word.ContentControl> 추가

- 컨트롤을 데이터 세트 인스턴스에 연결하는 <xref:System.Windows.Forms.BindingSource> 만들기.

- 사용자가 레코드를 스크롤하고 컨트롤에서 볼 수 있도록 설정

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

- `AdventureWorksLT` 샘플 데이터베이스가 연결된 SQL Server 2005 또는 SQL Server 2005 Express의 실행 중인 인스턴스 액세스 권한 `AdventureWorksLT` [SQL Server 샘플 GitHub 리포지토리](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)에서 데이터베이스를 다운로드할 수 있습니다. 데이터베이스 연결에 대한 자세한 내용은 다음 항목을 참조하세요.

  - SQL Server Management Studio 또는 SQL Server Management Studio Express를 사용 하 여 데이터베이스를 연결 하려면 [방법: 데이터베이스 연결 (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database)을 참조 하세요.

  - 명령줄을 사용 하 여 데이터베이스를 연결 하려면 [방법: SQL Server Express에 데이터베이스 파일 연결](/previous-versions/sql/)을 참조 하세요.

## <a name="create-a-new-project"></a>새 프로젝트 만들기

첫 번째 단계는 Word VSTO 추가 기능 프로젝트를 만드는 것입니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. Visual Basic 또는 C#을 사용하여 이름이 **데이터베이스에서 문서 채우기**인 Word VSTO 추가 기능 프로젝트를 만듭니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio에서 *ThisAddIn* 또는 *ThisAddIn.cs* 파일을 열고 **데이터베이스 프로젝트의 문서 채우기** 를 **솔루션 탐색기**에 추가 합니다.

2. 프로젝트가 또는를 대상으로 하는 경우 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* 어셈블리에 대 한 참조를 추가 합니다. 이 참조는 이 연습의 뒷부분에서 프로그래밍 방식으로 문서에 Windows Forms 컨트롤을 추가하는 데 필요합니다.

## <a name="create-a-data-source"></a>데이터 소스 만들기

**데이터 원본** 창을 사용하여 형식화된 데이터 세트를 프로젝트에 추가합니다.

### <a name="to-add-a-typed-dataset-to-the-project"></a>프로젝트에 형식화된 데이터 세트를 추가하려면

1. **데이터 소스** 창이 표시 되지 않는 경우 메뉴 모음에서 **View**  >  **다른 Windows**  >  **데이터 소스**보기를 선택 하 여 표시 합니다.

2. **새 데이터 소스 추가** 를 선택하여 **데이터 소스 구성 마법사**를 시작합니다.

3. **데이터베이스**를 클릭하고 **다음**을 클릭합니다.

4. `AdventureWorksLT` 데이터베이스에 대한 기존 연결이 있는 경우 이 연결을 선택하고 **다음**을 클릭합니다.

    그렇지 않은 경우 **새 연결**을 클릭하고 **연결 추가** 대화 상자를 사용하여 새 연결을 만듭니다. 자세한 내용은 [새 연결 추가](../data-tools/add-new-connections.md)를 참조 하세요.

5. **애플리케이션 구성 파일에 연결 문자열 저장** 페이지에서 **다음**을 클릭합니다.

6. **데이터베이스 개체 선택** 페이지에서 **테이블** 을 확장하고 **Customer(SalesLT)** 를 선택합니다.

7. **Finish**를 클릭합니다.

    *Adventureworksltdataset.xsd 파일이* 파일이 **솔루션 탐색기**에 추가 됩니다. 이 파일은 다음 항목을 정의합니다.

   - `AdventureWorksLTDataSet`라는 형식화된 데이터 세트. 이 데이터 세트는 AdventureWorksLT 데이터베이스의 **Customer(SalesLT)** 테이블 내용을 나타냅니다.

   - 라는 TableAdapter `CustomerTableAdapter` 입니다. 이 TableAdapter를 사용 하 여에서 데이터를 읽고 쓸 수 있습니다 `AdventureWorksLTDataSet` . 자세한 내용은 [TableAdapter 개요](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)를 참조 하세요.

     이 연습 뒷부분에서는 이러한 두 개체를 모두 사용합니다.

## <a name="create-controls-and-binding-controls-to-data"></a>컨트롤 만들기 및 데이터에 컨트롤 바인딩

이 연습에서 데이터베이스 레코드를 보기 위한 인터페이스는 기본 이며 문서 내에서 바로 만들어집니다. 하나의 <xref:Microsoft.Office.Tools.Word.ContentControl>은 한 번에 단일 데이터베이스 레코드를 표시하고 두 개의 <xref:Microsoft.Office.Tools.Word.Controls.Button> 컨트롤을 사용하면 레코드를 앞뒤로 스크롤할 수 있습니다. 콘텐츠 컨트롤은 <xref:System.Windows.Forms.BindingSource> 를 사용하여 데이터베이스에 연결합니다.

컨트롤을 데이터에 바인딩하는 방법에 대 한 자세한 내용은 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)을 참조 하세요.

### <a name="to-create-the-interface-in-the-document"></a>문서에서 인터페이스를 만들려면

1. `ThisAddIn` 클래스에서 다음 컨트롤을 선언하여 `Customer` 데이터베이스의 `AdventureWorksLTDataSet` 테이블을 표시 및 스크롤합니다.

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2. `ThisAddIn_Startup` 메서드에서 다음 코드를 추가하여 데이터 세트를 초기화하고, `AdventureWorksLTDataSet` 데이터베이스의 정보로 데이터 세트를 채웁니다.

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3. `ThisAddIn_Startup` 메서드에 다음 코드를 추가합니다. 이렇게 하면 문서를 확장하는 호스트 항목이 생성됩니다. 자세한 내용은 [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조 하세요.

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4. 문서의 시작 부분에서 여러 범위를 정의합니다. 이러한 범위는 텍스트를 삽입하고 컨트롤을 배치할 위치를 식별합니다.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5. 이전에 정의된 범위에 인터페이스 컨트롤을 추가합니다.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6. `AdventureWorksLTDataSet` 를 사용하여 콘텐츠 컨트롤을 <xref:System.Windows.Forms.BindingSource>에 바인딩합니다. C# 개발자의 경우 <xref:Microsoft.Office.Tools.Word.Controls.Button> 컨트롤에 대해 두 개의 이벤트 처리기를 추가합니다.

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7. 데이터베이스 레코드를 탐색하는 다음 코드를 추가합니다.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>추가 기능 테스트

Word를 열면 콘텐츠 컨트롤에 `AdventureWorksLTDataSet` 데이터 세트의 데이터가 표시됩니다. **다음** 및 **이전** 단추를 클릭하여 데이터베이스 레코드를 스크롤합니다.

### <a name="to-test-the-vsto-add-in"></a>VSTO 추가 기능을 테스트하려면

1. **F5**키를 누릅니다.

     이름이 `customerContentControl` 인 콘텐츠 컨트롤이 만들어지고 데이터로 채워집니다. 동시에 `adventureWorksLTDataSet`라는 데이터 세트 개체와 <xref:System.Windows.Forms.BindingSource>라는 `customerBindingSource`가 프로젝트에 추가됩니다. <xref:Microsoft.Office.Tools.Word.ContentControl>가 <xref:System.Windows.Forms.BindingSource>에 바인딩되고 데이터 세트 개체에 바인딩됩니다.

2. **다음** 및 **이전** 단추를 클릭하여 데이터베이스 레코드를 스크롤합니다.

## <a name="see-also"></a>참고 항목

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
- [Windows Forms 컨트롤을 Visual Studio의 데이터에 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [방법: 개체의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office 솔루션에서 로컬 데이터베이스 파일 사용 개요](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource 구성 요소 개요](/dotnet/framework/winforms/controls/bindingsource-component-overview)
