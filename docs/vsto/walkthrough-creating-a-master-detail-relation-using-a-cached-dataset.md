---
title: 캐시 된 데이터 집합을 사용 하 여 마스터 세부 관계 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0acf84dd983a8c10f2af526ae0bb904eaa90a360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328362"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>연습: 캐시 된 데이터 집합을 사용 하 여 마스터 세부 관계 만들기
  이 연습에서는 워크시트에서 마스터/세부 관계를 만들고 오프 라인에서 솔루션을 사용할 수 있도록 데이터를 캐시 하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- 워크시트에 컨트롤을 추가 합니다.

- 워크시트에 캐시할 데이터 집합을 설정 합니다.

- 레코드를 스크롤할 수 있도록 코드를 추가 합니다.

- 프로젝트를 테스트 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- Northwind SQL Server 예제 데이터베이스에 액세스 합니다. 데이터베이스는 개발 컴퓨터 또는 서버에 있을 수 있습니다.

- SQL Server 데이터베이스에서 읽고 쓸 수 있는 권한입니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 이 단계에서는 Excel 통합 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. Visual Basic 또는 c #을 사용 하 여 이름 **내 마스터-세부 정보**를 사용 하 여 Excel 통합 문서 프로젝트를 만듭니다. **새 문서 만들기** 가 선택 되어 있는지 확인 합니다. 자세한 내용은 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)을 참조하세요.

   Visual Studio가 디자이너에서 새 Excel 통합 문서를 열고 **솔루션 탐색기**에 **마스터-세부 정보** 프로젝트를 추가 합니다.

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

8. **Orders** 테이블과 **Order Details** 테이블을 선택 합니다.

9. **마침**을 클릭합니다.

   마법사는 두 테이블을 **데이터 소스** 창에 추가 합니다. 또한 **솔루션 탐색기**에 표시 되는 형식화 된 데이터 집합을 프로젝트에 추가 합니다.

## <a name="add-controls-to-the-worksheet"></a>워크시트에 컨트롤 추가
 이 단계에서는 첫 번째 워크시트에 명명 된 범위, 목록 개체 및 두 개의 단추를 추가 합니다. 먼저 **데이터 소스 창에서** 명명 된 범위와 목록 개체를 추가 하 여 데이터 원본에 자동으로 바인딩합니다. 그런 다음 **도구 상자**에서 단추를 추가 합니다.

### <a name="to-add-a-named-range-and-a-list-object"></a>명명 된 범위와 목록 개체를 추가 하려면

1. **내 Master-Detail.xlsx** 통합 문서가 Visual Studio 디자이너에 열려 있고, **Sheet1** 이 표시 되어 있는지 확인 합니다.

2. **데이터 소스** 창을 열고 **Orders** 노드를 확장 합니다.

3. **OrderID** 열을 선택 하 고 표시 되는 드롭다운 화살표를 클릭 합니다.

4. 드롭다운 목록에서 **NamedRange** 를 클릭 한 다음 **OrderID** 열을 **A2**셀로 끕니다.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>이라는 컨트롤이 `OrderIDNamedRange` **A2**셀에 만들어집니다. 동시에 <xref:System.Windows.Forms.BindingSource> 명명 된 `OrdersBindingSource` , 테이블 어댑터 및 <xref:System.Data.DataSet> 인스턴스가 프로젝트에 추가 됩니다. 컨트롤이에 바인딩되고이는 <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> 인스턴스에 바인딩됩니다.

5. **Orders** 테이블 아래에 있는 열을 뒤로 스크롤합니다. 목록의 맨 아래에는 **주문 정보** 테이블이 있습니다. 이는 **Orders** 테이블의 자식 이기 때문에 여기에 있습니다. **Orders** 테이블과 같은 수준의 **Order Details** 테이블을 선택 하 고 표시 되는 드롭다운 화살표를 클릭 합니다.

6. 드롭다운 목록에서 **ListObject** 를 클릭 한 다음 **OrderDetails** 테이블을 **A6**셀로 끕니다.

7. <xref:Microsoft.Office.Tools.Excel.ListObject> **Order_DetailsListObject** 이라는 컨트롤이 **A6**셀에 만들어지고에 바인딩됩니다 <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>두 개의 단추를 추가 하려면

1. **도구 상자**의 **공용 컨트롤** 탭에서 <xref:System.Windows.Forms.Button> 워크시트의 **A3** 셀에 컨트롤을 추가 합니다.

    이 단추의 이름은 `Button1` 입니다.

2. <xref:System.Windows.Forms.Button>워크시트의 **B3** 셀에 다른 컨트롤을 추가 합니다.

    이 단추의 이름은 `Button2` 입니다.

   다음으로 문서에서 캐시 되도록 데이터 집합을 표시 합니다.

## <a name="cache-the-dataset"></a>데이터 집합 캐시
 데이터 집합을 공용으로 설정 하 고 **CacheInDocument** 속성을 설정 하 여 문서에서 캐시 되도록 데이터 집합을 표시 합니다.

### <a name="to-cache-the-dataset"></a>데이터 집합을 캐시 하려면

1. 구성 요소 트레이에서 **NorthwindDataSet** 를 선택 합니다.

2. **속성** 창에서 **Modifiers** 속성을 **Public**으로 변경 합니다.

    캐싱을 사용 하도록 설정 하기 전에 데이터 집합이 public 이어야 합니다.

3. **CacheInDocument** 속성을 **True**로 변경 합니다.

   다음 단계는 단추에 텍스트를 추가 하 고 c #에서는 이벤트 처리기를 연결 하는 코드를 추가 하는 것입니다.

## <a name="initialize-the-controls"></a>컨트롤 초기화
 이벤트 중에 단추 텍스트를 설정 하 고 이벤트 처리기를 추가 합니다 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> .

### <a name="to-initialize-the-data-and-the-controls"></a>데이터 및 컨트롤을 초기화 하려면

1. **솔루션 탐색기**에서 **Sheet1** 또는 **Sheet1.cs**를 마우스 오른쪽 단추로 클릭 한 다음 바로 가기 메뉴에서 **코드 보기** 를 클릭 합니다.

2. 메서드에 다음 코드를 추가 `Sheet1_Startup` 하 여 단추에 대 한 텍스트를 설정 합니다.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. C #의 경우에는 단추 클릭 이벤트에 대 한 이벤트 처리기를 `Sheet1_Startup` 메서드에 추가 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>레코드를 스크롤할 수 있도록 코드 추가
 <xref:System.Windows.Forms.Control.Click>각 단추의 이벤트 처리기에 코드를 추가 하 여 레코드를 이동 합니다.

### <a name="to-scroll-through-the-records"></a>레코드를 스크롤하려면

1. 의 이벤트에 대 한 이벤트 처리기를 추가 하 <xref:System.Windows.Forms.Control.Click> `Button1` 고 다음 코드를 추가 하 여 레코드를 뒤로 이동 합니다.

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. 의 이벤트에 대 한 이벤트 처리기를 추가 하 <xref:System.Windows.Forms.Control.Click> `Button2` 고 다음 코드를 추가 하 여 레코드를 이동 합니다.

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 통합 문서를 테스트 하 여 데이터가 예상 대로 표시 되는지 확인 하 고 오프 라인에서 솔루션을 사용할 수 있습니다.

### <a name="to-test-the-data-caching"></a>데이터 캐싱을 테스트 하려면

1. **F5**키를 누릅니다.

2. 명명 된 범위와 목록 개체가 데이터 원본의 데이터로 채워져 있는지 확인 합니다.

3. 단추를 클릭 하 여 일부 레코드를 스크롤합니다.

4. 통합 문서를 저장 한 다음 통합 문서와 Visual Studio를 닫습니다.

5. 데이터베이스에 대 한 연결을 사용 하지 않도록 설정 합니다. 데이터베이스가 서버에 있는 경우 컴퓨터에서 네트워크 케이블을 분리 하거나 데이터베이스가 개발 컴퓨터에 있는 경우 SQL Server 서비스를 중지 합니다.

6. Excel을 열고 *\bin* 디렉터리 (*\My Master-Detail\bin* in Visual Basic 또는 c #의 *\My Master-Detail\bin\debug* )에서 **Master-Detail.xlsx** 를 엽니다.

7. 일부 레코드를 스크롤하여 연결 해제 시 워크시트가 정상적으로 작동 하는지 확인 합니다.

8. 데이터베이스에 다시 연결 합니다. 데이터베이스가 서버에 있는 경우 컴퓨터를 네트워크에 다시 연결 하거나 데이터베이스가 개발 컴퓨터에 있는 경우 SQL Server 서비스를 시작 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 워크시트에서 마스터/세부 데이터 관계를 만들고 데이터 집합을 캐시 하는 기본 사항을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 솔루션을 배포합니다. 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md) 를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [데이터 캐시](../vsto/caching-data.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
