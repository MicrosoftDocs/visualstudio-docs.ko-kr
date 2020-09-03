---
title: '연습: 문서 수준 프로젝트의 복합 데이터 바인딩'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 026dc77573bbedce7882f9b3cceab049ef1066e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67692349"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>연습: 문서 수준 프로젝트의 복합 데이터 바인딩
  이 연습에서는 문서 수준 프로젝트에서 복합 데이터 바인딩의 기본 사항을 보여 줍니다. Microsoft Office Excel 워크시트의 여러 셀을 Northwind SQL Server 데이터베이스의 필드에 바인딩할 수 있습니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 통합 문서 프로젝트에 데이터 소스 추가

- 워크시트에 데이터 바인딩된 컨트롤을 추가 합니다.

- 데이터 변경 내용을 데이터베이스에 다시 저장 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- Northwind SQL Server 예제 데이터베이스를 사용 하 여 서버에 액세스 합니다.

- SQL Server 데이터베이스에서 읽고 쓸 수 있는 권한입니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 첫 번째 단계는 Excel 통합 문서 프로젝트를 만드는 것입니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름 **내 복합 데이터 바인딩**으로 Excel 통합 문서 프로젝트를 만듭니다. 마법사에서 **새 문서 만들기**를 선택 합니다.

     자세한 내용은 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)을 참조하세요.

     Visual Studio가 디자이너에서 새 Excel 통합 문서를 열고 **내 복합 데이터 바인딩** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

## <a name="create-the-data-source"></a>데이터 원본 만들기
 **데이터 원본** 창을 사용하여 형식화된 데이터 세트를 프로젝트에 추가합니다.

### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면

1. **데이터 소스** 창이 표시 되지 않는 경우 메뉴 모음에서 **View**  >  **다른 Windows**  >  **데이터 소스**보기를 선택 하 여 표시 합니다.

2. **새 데이터 소스 추가** 를 선택하여 **데이터 소스 구성 마법사**를 시작합니다.

3. **데이터베이스** 를 선택 하 고 **다음**을 클릭 합니다.

4. Northwind 샘플 SQL Server 데이터베이스에 대 한 데이터 연결을 선택 하거나 **새 연결** 단추를 사용 하 여 새 연결을 추가 합니다.

5. 연결을 선택 하거나 만든 후 **다음**을 클릭 합니다.

6. 선택 된 경우 연결을 저장 하는 옵션을 선택 취소 하 고 **다음**을 클릭 합니다.

7. **데이터베이스 개체** 창에서 **테이블** 노드를 확장 합니다.

8. **Employees** 테이블 옆의 확인란을 선택 합니다.

9. **마침**을 클릭합니다.

   이 마법사는 **Employees** 테이블을 **데이터 소스** 창에 추가 합니다. 또한 **솔루션 탐색기**에 표시 되는 형식화 된 데이터 집합을 프로젝트에 추가 합니다.

## <a name="add-controls-to-the-worksheet"></a>워크시트에 컨트롤 추가
 통합 문서를 열 때 워크시트에 **Employees** 테이블이 표시 됩니다. 사용자는 데이터를 변경한 다음 단추를 클릭 하 여 해당 변경 내용을 데이터베이스에 다시 저장할 수 있습니다.

 워크시트를 테이블에 자동으로 바인딩하려면 <xref:Microsoft.Office.Tools.Excel.ListObject> **데이터 소스** 창에서 워크시트에 컨트롤을 추가할 수 있습니다. 사용자에 게 변경 내용을 저장 하는 옵션을 제공 하려면 <xref:System.Windows.Forms.Button> **도구 상자**에서 컨트롤을 추가 합니다.

#### <a name="to-add-a-list-object"></a>목록 개체를 추가 하려면

1. Visual Studio 디자이너에서 **내 복합 데이터 Binding.xlsx** 통합 문서가 열려 있는지 확인 하 고 **sheet1"** 을 표시 합니다.

2. **데이터 소스** 창을 열고 **Employees** 노드를 선택 합니다.

3. 표시 되는 드롭다운 화살표를 클릭 합니다.

4. 드롭다운 목록에서 **ListObject** 를 선택 합니다.

5. **Employees** 테이블을 **A6**셀로 끕니다.

     <xref:Microsoft.Office.Tools.Excel.ListObject>이라는 컨트롤이 `EmployeesListObject` **A6**셀에 만들어집니다. 동시에 <xref:System.Windows.Forms.BindingSource> 명명 된 `EmployeesBindingSource` , 테이블 어댑터 및 <xref:System.Data.DataSet> 인스턴스가 프로젝트에 추가 됩니다. 컨트롤이에 바인딩되고이는 <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> 인스턴스에 바인딩됩니다.

### <a name="to-add-a-button"></a>단추를 추가 하려면

1. **도구 상자**의 **공용 컨트롤** 탭에서 <xref:System.Windows.Forms.Button> 워크시트의 **A4** 셀에 컨트롤을 추가 합니다.

   다음 단계는 워크시트를 열 때 단추에 텍스트를 추가 하는 것입니다.

## <a name="initialize-the-control"></a>컨트롤 초기화
 이벤트 처리기의 단추에 텍스트를 추가 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 합니다.

### <a name="to-initialize-the-control"></a>컨트롤을 초기화 하려면

1. **솔루션 탐색기**에서 **Sheet1** 또는 **Sheet1.cs**를 마우스 오른쪽 단추로 클릭 한 다음 바로 가기 메뉴에서 **코드 보기** 를 클릭 합니다.

2. 메서드에 다음 코드를 추가 `Sheet1_Startup` 하 여 b의 텍스트를 설정 합니다 `utton` .

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. C #의 경우에는 이벤트에 대 한 이벤트 처리기를 <xref:System.Windows.Forms.Control.Click> `Sheet1_Startup` 메서드에 추가 합니다.

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   이제 단추의 이벤트를 처리 하는 코드를 추가 <xref:System.Windows.Forms.Control.Click> 합니다.

## <a name="save-changes-to-the-database"></a>데이터베이스에 대 한 변경 내용 저장
 데이터에 대 한 변경 내용은 데이터베이스에 명시적으로 다시 저장 될 때까지 로컬 데이터 집합에만 존재 합니다.

### <a name="to-save-changes-to-the-database"></a>데이터베이스에 대 한 변경 내용을 저장 하려면

1. 의 이벤트에 대 한 이벤트 처리기를 추가 <xref:System.Windows.Forms.Control.Click> `button` 하 고 다음 코드를 추가 하 여 데이터 집합에 적용 된 모든 변경 내용을 데이터베이스에 다시 커밋합니다.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 통합 문서를 테스트 하 여 데이터가 예상 대로 표시 되 고 목록 개체의 데이터를 조작할 수 있는지 확인할 수 있습니다.

### <a name="to-test-the-data-binding"></a>데이터 바인딩을 테스트 하려면

- **F5**키를 누릅니다.

     통합 문서가 열리면 목록 개체가 **Employees** 테이블의 데이터로 채워져 있는지 확인 합니다.

### <a name="to-modify-data"></a>데이터를 수정 하려면

1. 이름을 **김소미**로 포함 하는 **B7**셀을 클릭 합니다.

2. **Anderson**이름을 입력 한 다음 **enter**키를 누릅니다.

### <a name="to-modify-a-column-header"></a>열 머리글을 수정 하려면

1. 열 머리글 **LastName**이 포함 된 셀을 클릭 합니다.

2. 두 단어 사이에 공백을 포함 하 여 **성을**입력 한 다음 **enter**키를 누릅니다.

### <a name="to-save-data"></a>데이터를 저장 하려면

1. 워크시트에서 **저장** 을 클릭 합니다.

2. Excel을 종료합니다. 변경한 내용을 저장할지 묻는 메시지가 표시 되 면 **아니요** 를 클릭 합니다.

3. **F5** 키를 눌러 프로젝트를 다시 실행 합니다.

     목록 개체는 **Employees** 테이블의 데이터로 채워집니다.

4. **B7** 셀의 이름은 여전히 **Anderson**입니다 .이 이름은 데이터베이스에 다시 저장 하 고 다시 저장 한 데이터 변경 내용입니다. 열 머리글이 데이터베이스에 바인딩되지 않고 워크시트에서 변경한 내용을 저장 하지 않았기 때문에 열 머리글 **LastName** 은 공간 없이 원래 형식으로 다시 변경 되었습니다.

### <a name="to-add-new-rows"></a>새 행을 추가 하려면

1. 목록 개체 내의 셀을 선택 합니다.

    새 행 **\*** 의 첫 번째 셀에 별표 ()가 포함 된 새 행이 목록의 맨 아래에 나타납니다.

2. 빈 행에 다음 정보를 추가 합니다.

   |EmployeeID|LastName|FirstName|제목|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|판매 관리자|

### <a name="to-delete-rows"></a>행 삭제

- 워크시트의 맨 왼쪽에 있는 숫자 16 (행 16)을 마우스 오른쪽 단추로 클릭 한 다음 **삭제**를 클릭 합니다.

### <a name="to-sort-the-rows-in-the-list"></a>목록의 행을 정렬 하려면

1. 목록 내에서 셀을 선택 합니다.

     화살표 단추는 각 열 머리글에 표시 됩니다.

2. **Last Name** 열 머리글에서 화살표 단추를 클릭 합니다.

3. **오름차순 정렬**을 클릭 합니다.

     행은 성을 기준으로 사전순으로 정렬 됩니다.

### <a name="to-filter-information"></a>정보를 필터링 하려면

1. 목록 내에서 셀을 선택 합니다.

2. **제목** 열 머리글에서 화살표 단추를 클릭 합니다.

3. **영업 담당자**를 클릭 합니다.

     이 목록에는 **Title** 열에 **Sales 담당자** 가 있는 행만 표시 됩니다.

4. **제목** 열 머리글에서 화살표 단추를 다시 클릭 합니다.

5. **(모두)** 를 클릭 합니다.

     필터링이 제거 되 고 모든 행이 표시 됩니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 데이터베이스의 테이블을 목록 개체에 바인딩하는 기본적인 방법을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 오프 라인에서 사용할 수 있도록 데이터를 캐시 합니다. 자세한 내용은 [방법: 오프 라인 이나 서버에서 사용할 데이터 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)를 참조 하세요.

- 솔루션을 배포합니다. 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)를 참조 하세요.

- 필드와 테이블 간에 마스터/세부 관계를 만듭니다. 자세한 내용은 [연습: 캐시 된 데이터 집합을 사용 하 여 마스터 세부 관계 만들기](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [연습: 문서 수준 프로젝트의 단순 데이터 바인딩](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
