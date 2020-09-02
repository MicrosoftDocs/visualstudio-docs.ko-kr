---
title: 라디오 단추를 사용 하 여 워크시트의 차트 업데이트
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e63d7d09a09fe4c051d8137428fdae90490cbae5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238818"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>연습: 워크시트에서 라디오 단추를 사용하여 차트 업데이트
  이 연습에서는 Microsoft Office Excel 워크시트에서 라디오 단추를 사용 하 여 사용자에 게 옵션 간을 빠르게 전환할 수 있는 방법을 제공 하는 기본 사항을 보여 줍니다. 이 경우 옵션은 차트의 스타일을 변경 합니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 결과를 완료 된 샘플로 보려면 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)에서 Excel 컨트롤 샘플을 참조 하세요.

 이 연습에서는 다음 작업을 수행합니다.

- 워크시트에 라디오 단추 그룹 추가

- 옵션을 선택할 때 차트 스타일을 변경합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

## <a name="add-a-chart-to-a-worksheet"></a>워크시트에 차트 추가
 기존 통합 문서를 사용자 지정 하는 Excel 통합 문서 프로젝트를 만들 수 있습니다. 이 연습에서는 통합 문서에 차트를 추가한 다음 새 Excel 솔루션에서이 통합 문서를 사용 합니다. 이 연습의 데이터 원본은 **차트의 data**라는 워크시트입니다.

### <a name="to-add-the-data"></a>데이터를 추가 하려면

1. Microsoft Excel을 엽니다.

2. **Sheet3** 탭을 마우스 오른쪽 단추로 클릭 한 다음 바로 가기 메뉴에서 **이름 바꾸기** 를 클릭 합니다.

3. **차트에 대 한**시트의 이름을 데이터로 바꿉니다.

4. A4 셀의 왼쪽 위 모퉁이가 있는 **차트의 데이터** 에 다음 데이터를 추가 하 고 오른쪽 아래 모서리를 E8.

   |지역/사분기|Q1|Q2|Q3|Q4|
   |-|--------|--------|--------|--------|
   |West|500|550|550|600|
   |East|600|625|675|700|
   |North|450|470|490|510|
   |South|800|750|775|790|

   다음으로 첫 번째 워크시트에 차트를 추가 하 여 데이터를 표시 합니다.

### <a name="to-add-a-chart-in-excel"></a>Excel에서 차트를 추가 하려면

1. **삽입** 탭의 **차트** 그룹에서 **열**을 클릭 한 다음 **모든 차트 종류**를 클릭 합니다.

2. **차트 삽입** 대화 상자에서 **확인**을 클릭 합니다.

3. **디자인** 탭의 **데이터** 그룹에서 **데이터 선택**을 클릭 합니다.

4. **데이터 원본 선택** 대화 상자에서 **chartdata 범위** 상자를 클릭 하 고 기본 선택 항목을 선택 취소 합니다.

5. **차트의 데이터** 시트에서 숫자가 포함 된 셀 블록을 선택 합니다. 여기에는 왼쪽 위 모서리의 A4와 오른쪽 아래 모서리의 E8가 포함 됩니다.

6. **데이터 소스 선택** 대화 상자에서 **확인**을 클릭 합니다.

7. 오른쪽 위 모퉁이가 **E2**셀과 정렬 되도록 차트의 위치를 변경 합니다.

8. C 드라이브에 파일을 저장 하 고 이름을 **ExcelChart.xlsx**로 합니다.

9. Excel을 종료합니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 이 단계에서는 Excel 통합 문서를 기반으로 **하는 Excel** 통합 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름이 **My Excel Chart**인 Excel 통합 문서 프로젝트를 만듭니다. 마법사에서 **기존 문서 복사**를 선택 합니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

2. **찾아보기** 단추를 클릭 하 여이 연습의 앞부분에서 만든 통합 문서를 찾습니다.

3. **확인**을 클릭합니다.

     Visual Studio에서 새 Excel 통합 문서를 디자이너에서 열고 **Excel 차트** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

## <a name="set-properties-of-the-chart"></a>차트의 속성 설정
 기존 통합 문서를 사용 하는 새 Excel 통합 문서 프로젝트를 만드는 경우 통합 문서의 모든 명명 된 범위, 목록 개체 및 차트에 대해 호스트 컨트롤이 자동으로 만들어집니다. <xref:Microsoft.Office.Tools.Excel.Chart> **속성** 창을 사용 하 여 컨트롤의 이름을 변경할 수 있습니다.

### <a name="to-change-the-name-of-the-chart-control"></a>차트 컨트롤의 이름을 변경 하려면

1. <xref:Microsoft.Office.Tools.Excel.Chart>디자이너에서 컨트롤을 선택 하 고 **속성** 창에서 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**dataChart**|
    |**HasLegend**|**false**|

## <a name="add-controls"></a>컨트롤 추가
 이 워크시트는 라디오 단추를 사용 하 여 차트 스타일을 신속 하 게 변경할 수 있는 방법을 사용자에 게 제공 합니다. 그러나 라디오 단추를 단독으로 사용할 수 있어야 합니다. 한 단추를 선택 하면 그룹의 다른 단추를 동시에 선택할 수 없습니다. 이 동작은 워크시트에 몇 가지 라디오 단추를 추가할 때 기본적으로 발생 하지 않습니다.

 이 동작을 추가 하는 한 가지 방법은 사용자 컨트롤의 라디오 단추를 그룹화 하 고 사용자 컨트롤 뒤에 코드를 작성 한 다음 사용자 정의 컨트롤을 워크시트에 추가 하는 것입니다.

### <a name="to-add-a-user-control"></a>사용자 컨트롤을 추가하려면

1. **솔루션 탐색기**에서 **내 Excel 차트** 프로젝트를 선택 합니다.

2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

3. **새 항목 추가** 대화 상자에서 **사용자 정의 컨트롤**을 클릭 하 고 컨트롤 이름을 **ChartOptions로** 선택한 다음 **추가**를 클릭 합니다.

### <a name="to-add-radio-buttons-to-the-user-control"></a>사용자 정의 컨트롤에 라디오 단추를 추가 하려면

1. 사용자 정의 컨트롤이 디자이너에 표시 되지 않는 경우 **솔루션 탐색기**에서 **ChartOptions** 를 두 번 클릭 합니다.

2. **도구 상자**의 **공용 컨트롤** 탭에서 **라디오 단추** 컨트롤을 사용자 정의 컨트롤로 끌고 다음 속성을 변경 합니다.

   | 속성 | 값 |
   |----------|------------------|
   | **이름** | **columnChart** |
   | **Text** | **세로 막대형 차트** |

3. 사용자 정의 컨트롤에 두 번째 라디오 단추를 추가 하 고 다음 속성을 변경 합니다.

   | 속성 | 값 |
   |----------|---------------|
   | **이름** | **barChart** |
   | **Text** | **가로 막대형 차트** |

4. 세 번째 라디오 단추를 사용자 정의 컨트롤에 추가 하 고 다음 속성을 변경 합니다.

   | 속성 | 값 |
   |----------|----------------|
   | **이름** | **lineChart** |
   | **Text** | **꺾은선형 차트** |

5. 네 번째 라디오 단추를 사용자 정의 컨트롤에 추가 하 고 다음 속성을 변경 합니다.

   |속성|값|
   |--------------|-----------|
   |**이름**|**areaBlockChart**|
   |**Text**|**영역 블록 차트**|

   다음으로 라디오 단추를 클릭 하면 차트를 업데이트 하는 코드를 작성 합니다.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>라디오 단추가 선택 된 경우 차트 스타일 변경
 이제 차트 스타일을 변경 하는 코드를 추가할 수 있습니다. 이렇게 하려면 사용자 정의 컨트롤에서 공용 이벤트를 만들고, 선택 유형을 설정 하는 속성을 추가 하 고, `CheckedChanged` 각 라디오 단추의 이벤트에 대 한 이벤트 처리기를 만듭니다.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>사용자 컨트롤에서 이벤트와 속성을 만들려면

1. **솔루션 탐색기**에서 사용자 정의 컨트롤을 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

2. 클래스에 코드를 추가 `ChartOptions` 하 여 `SelectionChanged` 이벤트 및 속성을 만듭니다 `Selection` .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>라디오 단추의 CheckedChanged 이벤트를 처리 하려면

1. `CheckedChanged` 라디오 단추의 `areaBlockChart` 이벤트 처리기에서 차트 종류를 설정한 다음 이벤트를 발생시킵니다.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]

2. `CheckedChanged` 라디오 단추의 `barChart` 이벤트 처리기에서 차트 종류를 설정합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]

3. `CheckedChanged` 라디오 단추의 `columnChart` 이벤트 처리기에서 차트 종류를 설정합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]

4. `CheckedChanged` 라디오 단추의 `lineChart` 이벤트 처리기에서 차트 종류를 설정합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]

5. C#에서는 라디오 단추에 대해 이벤트 처리기를 추가해야 합니다. `ChartOptions` 생성자의 `InitializeComponent` 호출 아래에 코드를 추가할 수 있습니다. 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]

## <a name="add-the-user-control-to-the-worksheet"></a>워크시트에 사용자 정의 컨트롤 추가
 솔루션을 빌드하면 새 사용자 정의 컨트롤이 **도구 상자**에 자동으로 추가 됩니다. 그런 다음 컨트롤을 **도구 상자** 에서 워크시트로 끌어 올 수 있습니다.

### <a name="to-add-the-user-control-your-worksheet"></a>워크시트에 사용자 정의 컨트롤을 추가 하려면

1. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

     **ChartOptions** 사용자 정의 컨트롤이 **도구 상자**에 추가 됩니다.

2. **솔루션 탐색기**에서 **Sheet1** 또는 **Sheet1.cs**를 마우스 오른쪽 단추로 클릭 한 다음 **뷰 디자이너**를 클릭 합니다.

3. **ChartOptions** 컨트롤을 **도구 상자** 에서 워크시트로 끌어 옵니다.

     이라는 새 컨트롤이 `my_Excel_Chart_ChartOptions1` 프로젝트에 추가 됩니다.

4. 컨트롤의 이름을 **ChartOptions1**로 변경 합니다.

## <a name="change-the-chart-type"></a>차트 종류 변경
 차트 종류를 변경 하려면 사용자 정의 컨트롤에서 선택한 옵션에 따라 스타일을 설정 하는 이벤트 처리기를 만듭니다.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>워크시트에 표시 되는 차트의 형식을 변경 하려면

1. `Sheet1` 클래스에 다음 이벤트 처리기를 추가합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]

2. C #에서는 아래와 같이 사용자 정의 컨트롤에 대 한 이벤트 처리기를 이벤트에 추가 해야 합니다 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 통합 문서를 테스트 하 여 라디오 단추를 선택할 때 차트의 스타일이 올바르게 지정 되었는지 확인할 수 있습니다.

### <a name="to-test-your-workbook"></a>통합 문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 여러 라디오 단추를 선택합니다.

3. 선택 항목과 일치하도록 차트 스타일이 변경되는지 확인합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 워크시트에서 라디오 단추 및 차트 스타일을 사용 하는 기본 사항을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 프로젝트를 배포 합니다. 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)를 참조 하세요.

- 단추를 사용하여 텍스트 상자를 채웁니다. 자세한 내용은 [연습: 워크시트에서 단추를 사용 하 여 텍스트 상자에 텍스트 표시](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)를 참조 하세요.

- 확인란을 사용 하 여 워크시트의 서식을 변경 합니다. 자세한 내용은 [연습: CheckBox 컨트롤을 사용 하 여 워크시트 서식 변경](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)을 참조 하세요.

## <a name="see-also"></a>참조
- [Excel을 사용한 연습](../vsto/walkthroughs-using-excel.md)
