---
title: '연습: 문서 수준 프로젝트의 단순 데이터 바인딩'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0c22947e572a29c2b49a5ce9bb808c3cf2fe2902
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584926"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>연습: 문서 수준 프로젝트의 단순 데이터 바인딩
  이 연습에서는 문서 수준 프로젝트의 데이터 바인딩에 대 한 기본 사항을 보여 줍니다. SQL Server 데이터베이스의 단일 데이터 필드는 Microsoft Office Excel에서 명명 된 범위에 바인딩됩니다. 또한이 연습에서는 테이블의 모든 레코드를 스크롤할 수 있도록 하는 컨트롤을 추가 하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- Excel 프로젝트에 대 한 데이터 원본 만들기

- 워크시트에 컨트롤 추가

- 데이터베이스 레코드를 통해 스크롤

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- Northwind SQL Server 예제 데이터베이스를 사용 하 여 서버에 액세스 합니다.

- SQL Server 데이터베이스에서 읽고 쓸 수 있는 권한입니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 이 단계에서는 Excel 통합 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. Visual Basic 또는 c #을 사용 하 여 **내 단순 데이터 바인딩**이름으로 Excel 통합 문서 프로젝트를 만듭니다. **새 문서 만들기** 가 선택 되어 있는지 확인 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

   Visual Studio가 디자이너에서 새 Excel 통합 문서를 열고 **단순 데이터 바인딩** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

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

8. **Customers** 테이블 옆의 확인란을 선택 합니다.

9. **Finish**를 클릭합니다.

   마법사가 **데이터 소스** 창에 **Customers** 테이블을 추가 합니다. 또한 **솔루션 탐색기**에 표시 되는 형식화 된 데이터 집합을 프로젝트에 추가 합니다.

## <a name="add-controls-to-the-worksheet"></a>워크시트에 컨트롤 추가
 이 연습에서는 두 개의 명명 된 범위와 4 개의 단추가 첫 번째 워크시트에 필요 합니다. 먼저 **데이터 소스 창에서** 두 개의 명명 된 범위를 추가 하 여 데이터 원본에 자동으로 바인딩합니다. 그런 다음 **도구 상자**에서 단추를 추가 합니다.

### <a name="to-add-two-named-ranges"></a>두 개의 명명 된 범위를 추가 하려면

1. *내 단순 데이터 Binding.xlsx* 통합 문서가 Visual Studio 디자이너에서 열려 있고, **Sheet1** 이 표시 되는지 확인 합니다.

2. **데이터 소스** 창을 열고 **Customers** 노드를 확장 합니다.

3. **CompanyName** 열을 선택 하 고 표시 되는 드롭다운 화살표를 클릭 합니다.

4. 드롭다운 목록에서 **NamedRange** 를 선택 하 고 **CompanyName** 열을 **A1**셀로 끕니다.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>이라는 컨트롤이 `companyNameNamedRange` **A1**셀에 만들어집니다. 동시에 <xref:System.Windows.Forms.BindingSource> 명명 된 `customersBindingSource` , 테이블 어댑터 및 <xref:System.Data.DataSet> 인스턴스가 프로젝트에 추가 됩니다. 컨트롤이에 바인딩되고이는 <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> 인스턴스에 바인딩됩니다.

5. **데이터 소스** 창에서 **CustomerID** 열을 선택 하 고 표시 되는 드롭다운 화살표를 클릭 합니다.

6. 드롭다운 목록에서 **NamedRange** 를 클릭 한 다음 **CustomerID** 열을 셀 **B1**로 끕니다.

7. <xref:Microsoft.Office.Tools.Excel.NamedRange>이라는 다른 컨트롤 `customerIDNamedRange` 은 **B1**셀에 만들어지고에 바인딩됩니다 <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>단추 4 개를 추가 하려면

1. **도구 상자**의 **공용 컨트롤** 탭에서 <xref:System.Windows.Forms.Button> 워크시트의 **A3** 셀에 컨트롤을 추가 합니다.

    이 단추의 이름은 `Button1` 입니다.

2. 다음 셀에 세 개의 단추를 더 추가 하 여 이름이 표시 되도록 합니다.

   |셀|(이름)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   다음 단계는 단추에 텍스트를 추가 하 고 c #에서는 이벤트 처리기를 추가 하는 것입니다.

## <a name="initialize-the-controls"></a>컨트롤 초기화
 이벤트 중에 단추 텍스트를 설정 하 고 이벤트 처리기를 추가 합니다 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> .

### <a name="to-initialize-the-controls"></a>컨트롤을 초기화 하려면

1. **솔루션 탐색기**에서 **Sheet1** 또는 **Sheet1.cs**를 마우스 오른쪽 단추로 클릭 한 다음 바로 가기 메뉴에서 **코드 보기** 를 클릭 합니다.

2. 메서드에 다음 코드를 추가 `Sheet1_Startup` 하 여 각 단추에 대 한 텍스트를 설정 합니다.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. C #의 경우에는 단추 클릭 이벤트에 대 한 이벤트 처리기를 `Sheet1_Startup` 메서드에 추가 합니다.

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   이제 <xref:System.Windows.Forms.Control.Click> 사용자가 레코드를 탐색할 수 있도록 단추의 이벤트를 처리 하는 코드를 추가 합니다.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>레코드를 스크롤할 수 있도록 코드 추가
 <xref:System.Windows.Forms.Control.Click>각 단추의 이벤트 처리기에 코드를 추가 하 여 레코드를 이동 합니다.

### <a name="to-move-to-the-first-record"></a>첫 번째 레코드로 이동 하려면

1. 단추의 이벤트에 대 한 이벤트 처리기를 추가 하 <xref:System.Windows.Forms.Control.Click> `Button1` 고 다음 코드를 추가 하 여 첫 번째 레코드로 이동 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>이전 레코드로 이동 하려면

1. 단추의 이벤트에 대 한 이벤트 처리기를 추가 하 <xref:System.Windows.Forms.Control.Click> `Button2` 고 다음 코드를 추가 하 여 위치를 다시 1로 이동 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>다음 레코드로 이동 하려면

1. 단추의 이벤트에 대 한 이벤트 처리기를 추가 하 <xref:System.Windows.Forms.Control.Click> `Button3` 고 다음 코드를 추가 하 여 위치를 1로 이동 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>마지막 레코드로 이동 하려면

1. 단추의 이벤트에 대 한 이벤트 처리기를 추가 하 <xref:System.Windows.Forms.Control.Click> `Button4` 고 다음 코드를 추가 하 여 마지막 레코드로 이동 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 통합 문서를 테스트 하 여 데이터베이스의 레코드를 탐색할 수 있는지 확인할 수 있습니다.

### <a name="to-test-your-workbook"></a>통합 문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 첫 번째 레코드가 **A1** 및 **B1**셀에 표시 되는지 확인 합니다.

3. **>**( `Button3` ) 단추를 클릭 하 고 다음 레코드가 **A1** 및 **B1**셀에 표시 되는지 확인 합니다.

4. 다른 스크롤 단추를 클릭 하 여 레코드가 예상 대로 변경 되는지 확인 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 명명 된 범위를 데이터베이스의 필드에 바인딩하는 기본적인 방법을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 오프 라인에서 사용할 수 있도록 데이터를 캐시 합니다. 자세한 내용은 [방법: 오프 라인 이나 서버에서 사용할 데이터 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)를 참조 하세요.

- 한 필드가 아닌 테이블의 여러 열에 셀을 바인딩합니다. 자세한 내용은 [연습: 문서 수준 프로젝트의 복합 데이터 바인딩](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)을 참조 하세요.

- 컨트롤을 사용 <xref:System.Windows.Forms.BindingNavigator> 하 여 레코드를 스크롤합니다. 자세한 내용은 [방법: Windows Forms BindingNavigator 컨트롤을 사용 하 여 데이터 탐색](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [연습: 문서 수준 프로젝트의 복합 데이터 바인딩](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
