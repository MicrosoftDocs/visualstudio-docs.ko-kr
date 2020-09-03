---
title: '연습: 서버의 통합 문서에 데이터 삽입'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
- workbooks [Office development in Visual Studio], inserting data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d9dcd22ca124ee5ea4002277f91071727a3e9e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985427"
---
# <a name="walkthrough-insert-data-into-a-workbook-on-a-server"></a>연습: 서버의 통합 문서에 데이터 삽입
  이 연습에서는 클래스를 사용 하 여 Excel을 시작 하지 않고 Microsoft Office Excel 통합 문서에 캐시 되는 데이터 집합에 데이터를 삽입 하는 방법을 보여 줍니다 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> .

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- AdventureWorksLT 데이터베이스의 데이터를 포함 하는 데이터 집합 정의

- Excel 통합 문서 프로젝트 및 콘솔 응용 프로그램 프로젝트에서 데이터 집합의 인스턴스를 만듭니다.

- <xref:Microsoft.Office.Tools.Excel.ListObject>통합 문서의 데이터 집합에 바인딩된를 만듭니다.

- 통합 문서의 데이터 집합을 데이터 캐시에 추가 합니다.

- Excel을 시작 하지 않고 콘솔 응용 프로그램에서 코드를 실행 하 여 캐시 된 데이터 집합에 데이터를 삽입 합니다.

  이 연습에서는 개발 컴퓨터에서 코드를 실행 하는 것으로 가정 하지만 Excel이 설치 되어 있지 않은 서버에서는이 연습에서 보여 주는 코드를 사용할 수 있습니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- AdventureWorksLT 샘플 데이터베이스가 연결 된 Microsoft SQL Server 또는 Microsoft SQL Server Express의 실행 중인 인스턴스에 대 한 액세스. [CodePlex 웹 사이트](https://archive.codeplex.com/?p=SqlServerSamples)에서 AdventureWorksLT 데이터베이스를 다운로드할 수 있습니다. 데이터베이스 연결에 대한 자세한 내용은 다음 항목을 참조하세요.

  - SQL Server Management Studio 또는 SQL Server Management Studio Express를 사용 하 여 데이터베이스를 연결 하려면 [방법: 데이터베이스 연결 (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database)을 참조 하세요.

  - 명령줄을 사용 하 여 데이터베이스를 연결 하려면 [방법: SQL Server Express에 데이터베이스 파일 연결](/previous-versions/sql/)을 참조 하세요.

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>데이터 집합을 정의 하는 클래스 라이브러리 프로젝트 만들기
 Excel 통합 문서 프로젝트와 콘솔 응용 프로그램에서 동일한 데이터 집합을 사용 하려면 두 프로젝트 모두에서 참조 되는 별도의 어셈블리에 데이터 집합을 정의 해야 합니다. 이 연습에서는 클래스 라이브러리 프로젝트에서 데이터 집합을 정의 합니다.

### <a name="to-create-the-class-library-project"></a>클래스 라이브러리 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

3. 템플릿 창에서 **Visual c #** 또는 **Visual Basic**을 확장 한 다음 **Windows**를 클릭 합니다.

4. 프로젝트 템플릿 목록에서 **클래스 라이브러리**를 선택 합니다.

5. **이름** 상자에 **AdventureWorksDataSet**을 입력 합니다.

6. **찾아보기**를 클릭 하 고 *%UserProfile%\My 문서* (windows XP 및 이전 버전의 경우) 또는 *%UserProfile%\Documents* (windows Vista) 폴더로 이동한 다음 **폴더 선택**을 클릭 합니다.

7. **새 프로젝트** 대화 상자에서 **솔루션용 디렉터리 만들기** 확인란을 선택 하지 않았는지 확인 합니다.

8. **확인**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**솔루션 탐색기** 에 **AdventureWorksDataSet** 프로젝트를 추가 하 고 **Class1.cs** 또는 **Class1** 코드 파일을 엽니다.

9. **솔루션 탐색기**에서 **Class1.cs** 또는 **Class1 .vb**를 마우스 오른쪽 단추로 클릭 한 다음 **삭제**를 클릭 합니다. 이 연습에서는이 파일이 필요 하지 않습니다.

## <a name="define-a-dataset-in-the-class-library-project"></a>클래스 라이브러리 프로젝트에서 데이터 집합 정의
 SQL Server 2005에 대 한 AdventureWorksLT 데이터베이스의 데이터를 포함 하는 형식화 된 데이터 집합을 정의 합니다. 이 연습의 뒷부분에서는 Excel 통합 문서 프로젝트와 콘솔 응용 프로그램 프로젝트에서이 데이터 집합을 참조 합니다.

 데이터 집합은 AdventureWorksLT 데이터베이스의 Product 테이블에 있는 데이터를 나타내는 *형식화 된 데이터 집합* 입니다. 형식화 된 데이터 집합에 대 한 자세한 내용은 [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)를 참조 하세요.

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>클래스 라이브러리 프로젝트에서 형식화 된 데이터 집합을 정의 하려면

1. **솔루션 탐색기**에서 **AdventureWorksDataSet** 프로젝트를 클릭 합니다.

2. **데이터 소스** 창이 표시 되지 않는 경우 메뉴 모음에서 **View**  >  **다른 Windows**  >  **데이터 소스**보기를 선택 하 여 표시 합니다.

3. **새 데이터 소스 추가** 를 선택하여 **데이터 소스 구성 마법사**를 시작합니다.

4. **데이터베이스**를 클릭하고 **다음**을 클릭합니다.

5. AdventureWorksLT 데이터베이스에 대 한 기존 연결이 있는 경우이 연결을 선택 하 고 **다음**을 클릭 합니다.

    그렇지 않은 경우 **새 연결**을 클릭하고 **연결 추가** 대화 상자를 사용하여 새 연결을 만듭니다. 자세한 내용은 [방법: 데이터베이스의 데이터에 연결](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)을 참조 하세요.

6. **애플리케이션 구성 파일에 연결 문자열 저장** 페이지에서 **다음**을 클릭합니다.

7. **데이터베이스 개체 선택** 페이지에서 **테이블** 을 확장 하 고 **Product (saleslt)** 를 선택 합니다.

8. **마침**을 클릭합니다.

    *Adventureworksltdataset.xsd 파일이* 파일이 **AdventureWorksDataSet** 프로젝트에 추가 됩니다. 이 파일은 다음 항목을 정의합니다.

   - `AdventureWorksLTDataSet`라는 형식화된 데이터 세트. 이 데이터 집합은 AdventureWorksLT 데이터베이스에 있는 Product 테이블의 내용을 나타냅니다.

   - 라는 TableAdapter `ProductTableAdapter` 입니다. 이 TableAdapter를 사용 하 여에서 데이터를 읽고 쓸 수 있습니다 `AdventureWorksLTDataSet` . 자세한 내용은 [TableAdapter 개요](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)를 참조 하세요.

     이 연습 뒷부분에서는 이러한 두 개체를 모두 사용합니다.

9. **솔루션 탐색기**에서 **AdventureWorksDataSet** 을 마우스 오른쪽 단추로 클릭 하 고 **빌드**를 클릭 합니다.

     프로젝트가 오류 없이 빌드되는지 확인합니다.

## <a name="create-an-excel-workbook-project"></a>Excel 통합 문서 프로젝트 만들기
 데이터의 인터페이스에 대 한 Excel 통합 문서 프로젝트를 만듭니다. 이 연습 뒷부분에서는 <xref:Microsoft.Office.Tools.Excel.ListObject> 데이터를 표시 하는을 만들고 통합 문서의 데이터 캐시에 데이터 집합의 인스턴스를 추가 합니다.

### <a name="to-create-the-excel-workbook-project"></a>Excel 통합 문서 프로젝트를 만들려면

1. **솔루션 탐색기**에서 **AdventureWorksDataSet** 솔루션을 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 프로젝트**를 클릭 합니다.

2. 템플릿 창에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **Office/SharePoint**를 확장합니다.

3. 확장된 **Office/SharePoint** 노드 아래에서 **Office 추가 기능** 노드를 선택합니다.

4. 프로젝트 템플릿 목록에서 **Excel 2010 통합 문서** 또는 **Excel 2013 통합 문서** 프로젝트를 선택합니다.

5. **이름** 상자에 **AdventureWorksReport**을 입력 합니다. 위치를 수정 하지 마세요.

6. **확인**을 클릭합니다.

     **Visual Studio Tools for Office 프로젝트 마법사** 가 열립니다.

7. **새 문서 만들기** 가 선택 되어 있는지 확인 하 고 **확인**을 클릭 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]디자이너에서 **AdventureWorksReport** 통합 문서를 열고 **솔루션 탐색기**에 **AdventureWorksReport** 프로젝트를 추가 합니다.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Excel 통합 문서 프로젝트에서 데이터 원본에 데이터 집합 추가
 Excel 통합 문서에 데이터 집합을 표시 하려면 먼저 Excel 통합 문서 프로젝트에서 데이터 원본에 데이터 집합을 추가 해야 합니다.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Excel 통합 문서 프로젝트의 데이터 원본에 데이터 집합을 추가 하려면

1. **솔루션 탐색기**에서 **AdventureWorksReport** 프로젝트 아래의 **Sheet1.cs** 또는 **sheet1"** 을 두 번 클릭 합니다.

     통합 문서가 디자이너에서 열립니다.

2. **데이터** 메뉴에서 **새 데이터 소스 추가**를 클릭합니다.

     **데이터 원본 구성** 마법사가 열립니다.

3. **개체**를 클릭 하 고 **다음**을 클릭 합니다.

4. **바인딩할 개체 선택** 페이지에서 **참조 추가**를 클릭 합니다.

5. **프로젝트** 탭에서 **AdventureWorksDataSet** 를 클릭 한 다음 **확인**을 클릭 합니다.

6. **AdventureWorksDataSet** 어셈블리의 **AdventureWorksDataSet** 네임 스페이스에서 **Adventureworksltdataset.xsd 파일이** 를 클릭 한 다음 **마침**을 클릭 합니다.

     **데이터 소스** 창이 열리고 **adventureworksltdataset.xsd 파일이** 이 데이터 원본 목록에 추가 됩니다.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>데이터 집합의 인스턴스에 바인딩된 ListObject 만들기
 통합 문서에 데이터 집합을 표시 하려면 <xref:Microsoft.Office.Tools.Excel.ListObject> 데이터 집합의 인스턴스에 바인딩된를 만듭니다. 컨트롤을 데이터에 바인딩하는 방법에 대 한 자세한 내용은 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)을 참조 하세요.

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>데이터 집합의 인스턴스에 바인딩된 ListObject를 만들려면

1. **데이터 소스** 창의 **AdventureWorksDataSet**아래에서 **adventureworksltdataset.xsd 파일이** 노드를 확장 합니다.

2. **Product** 노드를 선택 하 고 표시 되는 드롭다운 화살표를 클릭 한 다음 드롭다운 목록에서 **ListObject** 를 선택 합니다.

     드롭다운 화살표가 나타나지 않으면 디자이너에서 통합 문서가 열려 있는지 확인 합니다.

3. **Product** 테이블을 A1 셀로 끕니다.

     <xref:Microsoft.Office.Tools.Excel.ListObject>이라는 컨트롤 `productListObject` 은 A1 셀에서 시작 하 여 워크시트에 만들어집니다. 동시에 `adventureWorksLTDataSet`라는 데이터 세트 개체와 <xref:System.Windows.Forms.BindingSource>라는 `productBindingSource`가 프로젝트에 추가됩니다. <xref:Microsoft.Office.Tools.Excel.ListObject>가 <xref:System.Windows.Forms.BindingSource>에 바인딩되고 데이터 세트 개체에 바인딩됩니다.

## <a name="add-the-dataset-to-the-data-cache"></a>데이터 캐시에 데이터 집합 추가
 Excel 통합 문서 프로젝트 외부의 코드를 사용 하 여 통합 문서의 데이터 집합에 액세스 하려면 데이터 집합을 데이터 캐시에 추가 해야 합니다. 데이터 캐시에 대 한 자세한 내용은 [문서 수준 사용자 지정의 캐시 된 데이터](../vsto/cached-data-in-document-level-customizations.md) 및 [캐시 데이터](../vsto/caching-data.md)를 참조 하세요.

### <a name="to-add-the-dataset-to-the-data-cache"></a>데이터 캐시에 데이터 집합을 추가 하려면

1. 디자이너에서 **adventureworksltdataset.xsd 파일이**를 클릭 합니다.

2. **속성** 창에서 **Modifiers** 속성을 **Public**으로 설정 합니다.

3. **CacheInDocument** 속성을 **True**로 설정 합니다.

## <a name="checkpoint"></a>검사점
 Excel 통합 문서 프로젝트를 빌드하고 실행 하 여 오류 없이 컴파일되고 실행 되는지 확인 합니다.

### <a name="to-build-and-run-the-project"></a>프로젝트를 빌드하여 실행하려면

1. **솔루션 탐색기**에서 **AdventureWorksReport** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **디버그**를 선택한 다음 **새 인스턴스 시작**을 클릭 합니다.

     프로젝트가 빌드되고 통합 문서가 Excel에서 열립니다. <xref:Microsoft.Office.Tools.Excel.ListObject>데이터 캐시의 개체에 아직 데이터가 없으므로 **Sheet1** 의이 비어 있습니다 `adventureWorksLTDataSet` . 다음 섹션에서는 콘솔 응용 프로그램을 사용 하 여 개체를 데이터로 채웁니다 `adventureWorksLTDataSet` .

2. Excel을 닫습니다. 변경 내용을 저장 하지 않습니다.

## <a name="create-a-console-application-project"></a>콘솔 응용 프로그램 프로젝트 만들기
 통합 문서의 캐시 된 데이터 집합에 데이터를 삽입 하는 데 사용할 콘솔 응용 프로그램 프로젝트를 만듭니다.

### <a name="to-create-the-console-application-project"></a>콘솔 응용 프로그램 프로젝트를 만들려면

1. **솔루션 탐색기**에서 **AdventureWorksDataSet** 솔루션을 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 프로젝트**를 클릭 합니다.

2. **프로젝트 형식** 창에서 **Visual c #** 또는 **Visual Basic**을 확장 한 다음 **Windows**를 클릭 합니다.

3. **템플릿** 창에서 **콘솔 응용 프로그램**을 선택합니다.

4. **이름** 상자에 **datawriter 여부**을 입력 합니다. 위치를 수정 하지 마세요.

5. **확인**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**솔루션 탐색기** 에 **datawriter 여부** 프로젝트를 추가 하 고 **Program.cs** 또는 코드 파일을 **엽니다.**

## <a name="add-data-to-the-cached-dataset-by-using-the-console-application"></a>콘솔 응용 프로그램을 사용 하 여 캐시 된 데이터 집합에 데이터 추가
 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>콘솔 응용 프로그램에서 클래스를 사용 하 여 통합 문서의 캐시 된 데이터 집합을 데이터로 채웁니다.

### <a name="to-add-data-to-the-cached-dataset"></a>캐시 된 데이터 집합에 데이터를 추가 하려면

1. **솔루션 탐색기**에서 **datawriter 여부** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **참조 추가**를 클릭 합니다.

2. **.Net** 탭에서 **VisualStudio. ServerDocument**를 선택 합니다.

3. **확인**을 클릭합니다.

4. **솔루션 탐색기**에서 **datawriter 여부** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **참조 추가**를 클릭 합니다.

5. **프로젝트** 탭에서 **AdventureWorksDataSet**를 선택 하 고 **확인**을 클릭 합니다.

6. 코드 편집기에서 *Program.cs* 또는 module1.vb 파일을 *엽니다.*

7. 다음을 **사용 하 여** (c #의 경우) 또는 **Imports** (Visual Basic의 경우) 문을 코드 파일의 맨 위에 추가 합니다.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. `Main` 메서드에 다음 코드를 추가합니다. 이 코드는 다음 개체를 선언 합니다.

   - `AdventureWorksLTDataSet` `ProductTableAdapter` **AdventureWorksDataSet** 프로젝트에 정의 된 및 형식의 인스턴스입니다.

   - **AdventureWorksReport** 프로젝트의 build 폴더에 있는 AdventureWorksReport 통합 문서에 대 한 경로입니다.

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>통합 문서의 데이터 캐시에 액세스 하는 데 사용할 개체입니다.

     > [!NOTE]
     > 다음 코드에서는 파일 확장명이 *.xlsx* 인 통합 문서를 사용 하 고 있다고 가정 합니다. 프로젝트의 통합 문서에 다른 파일 확장명이 있는 경우 필요에 따라 경로를 수정 합니다.

     [!code-csharp[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#3)]

9. `Main`이전 단계에서 추가한 코드 뒤에 다음 코드를 메서드에 추가 합니다. 이 코드는 다음 작업을 수행합니다.

   - 테이블 어댑터를 사용 하 여 형식화 된 데이터 집합 개체를 채웁니다.

   - 이 클래스는 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 클래스의 속성을 사용 하 여 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 통합 문서의 캐시 된 데이터 집합에 액세스 합니다.

   - 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 캐시 된 데이터 집합을 로컬 형식화 된 데이터 집합의 데이터로 채웁니다.

     [!code-csharp[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#4)]

10. **솔루션 탐색기**에서 **datawriter 여부** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **디버그**를 가리킨 다음 **새 인스턴스 시작**을 클릭 합니다.

     프로젝트가 빌드되고 콘솔 응용 프로그램은 로컬 데이터 집합이 채워지고 응용 프로그램이 데이터를 통합 문서의 캐시 된 데이터 집합에 저장할 때 몇 가지 상태 메시지를 표시 합니다. **Enter** 키를 눌러 애플리케이션을 닫습니다.

## <a name="test-the-workbook"></a>통합 문서 테스트
 통합 문서를 열면에서 <xref:Microsoft.Office.Tools.Excel.ListObject> 콘솔 응용 프로그램을 사용 하 여 캐시 된 데이터 집합에 추가 된 데이터를 표시 합니다.

### <a name="to-test-the-workbook"></a>통합 문서를 테스트 하려면

1. 아직 열려 있는 경우 Visual Studio 디자이너에서 AdventureWorksReport 통합 문서를 닫습니다.

2. 파일 탐색기에서 **AdventureWorksReport** 프로젝트의 빌드 폴더에 있는 AdventureWorksReport 통합 문서를 엽니다. 기본적으로 빌드 폴더는 다음 위치 중 하나에 있습니다.

    - *%UserProfile%\My Documents\AdventureWorksReport\bin\Debug* (Windows XP 및 이전 버전)

    - *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* (Windows Vista의 경우)

3. <xref:Microsoft.Office.Tools.Excel.ListObject>통합 문서를 연 후가 데이터로 채워져 있는지 확인 합니다.

## <a name="next-steps"></a>다음 단계

다음 항목에서 캐시 된 데이터로 작업 하는 방법에 대해 자세히 알아볼 수 있습니다.

- Excel을 시작 하지 않고 캐시 된 데이터 집합의 데이터 변경 자세한 내용은 [연습: 서버의 통합 문서에서 캐시 된 데이터 변경](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [연습: 서버의 통합 문서에서 캐시 된 데이터 변경](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
