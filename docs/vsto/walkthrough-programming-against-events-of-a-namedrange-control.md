---
title: '연습: NamedRange 컨트롤의 이벤트에 대 한 프로그래밍'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e5ce12e2de8274afd2c27d4ece36529563a6386
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584939"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>연습: NamedRange 컨트롤의 이벤트에 대 한 프로그래밍
  이 연습에서는 <xref:Microsoft.Office.Tools.Excel.NamedRange> Visual Studio에서 Office 개발 도구를 사용 하 여 Microsoft Office Excel 워크시트 및 프로그램에 컨트롤을 추가 하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- <xref:Microsoft.Office.Tools.Excel.NamedRange>워크시트에 컨트롤을 추가 합니다.

- 제어 이벤트에 대 한 프로그램 <xref:Microsoft.Office.Tools.Excel.NamedRange> 입니다.

- 프로젝트를 테스트 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트 만들기
 이 단계에서는 Visual Studio를 사용 하 여 Excel 통합 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름이 **My 명명 된 범위 이벤트**인 Excel 통합 문서 프로젝트를 만듭니다. **새 문서 만들기** 가 선택 되어 있는지 확인 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio가 디자이너에서 새 Excel 통합 문서를 열고 **솔루션 탐색기** **내 명명 된 범위 이벤트** 프로젝트를 추가 합니다.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>워크시트에 텍스트 및 명명 된 범위 추가
 호스트 컨트롤이 확장 된 Office 개체 이기 때문에 네이티브 개체를 추가 하는 것과 동일한 방식으로 문서에 추가할 수 있습니다. 예를 들어 <xref:Microsoft.Office.Tools.Excel.NamedRange> **삽입** 메뉴를 열고 **이름**을 가리킨 다음 **정의**를 선택 하 여 Excel 컨트롤을 워크시트에 추가할 수 있습니다. <xref:Microsoft.Office.Tools.Excel.NamedRange> **도구 상자** 에서 워크시트로 끌어와 서 컨트롤을 추가할 수도 있습니다.

 이 단계에서는 **도구 상자**를 사용 하 여 워크시트에 두 개의 명명 된 범위 컨트롤을 추가한 다음 워크시트에 텍스트를 추가 합니다.

### <a name="to-add-a-range-to-your-worksheet"></a>워크시트에 범위를 추가 하려면

1. 표시 된 상태로 *My 명명 된 범위 Events.xlsx* 통합 문서가 Visual Studio 디자이너에 열려 있는지 확인 `Sheet1` 합니다.

2. 도구 상자의 **Excel 컨트롤** 탭에서 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을의 **A1** 셀로 끌어 옵니다 `Sheet1` .

     **NamedRange 컨트롤 추가** 대화 상자가 나타납니다.

3. **$A $1** 이 편집 가능 텍스트 상자에 표시 되 고 **A1** 셀이 선택 되어 있는지 확인 합니다. 그렇지 않으면 **A1** 셀을 클릭 하 여 선택 합니다.

4. **확인**을 클릭합니다.

     **A1** 셀은 이름이 인 범위가 됩니다 `namedRange1` . 워크시트에는 표시 되지 않지만 `namedRange1` **A1** 셀을 선택 하면 **이름** 상자에 표시 됩니다 (왼쪽에 워크시트 바로 위에 있음).

5. <xref:Microsoft.Office.Tools.Excel.NamedRange> **B3**셀에 다른 컨트롤을 추가 합니다.

6. **$B $3** 이 편집 가능 텍스트 상자에 표시 되 고 **B3** 셀이 선택 되어 있는지 확인 합니다. 그렇지 않으면 **B3** 셀을 클릭 하 여 선택 합니다.

7. **확인**을 클릭합니다.

     **B3** 셀은 이름이 인 범위가 됩니다 `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>워크시트에 텍스트를 추가 하려면

1. **A1**셀에 다음 텍스트를 입력 합니다.

    **이는 NamedRange 컨트롤의 예입니다.**

2. 왼쪽 **A3** 셀에서 `namedRange2` 다음 텍스트를 입력 합니다.

    **이벤트**

   다음 섹션에서는 `namedRange2` `namedRange2` <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 의, 및 이벤트에 대 한 응답으로 컨트롤의 속성 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 을 삽입 하 고 수정 하는 코드를 작성 합니다 `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>BeforeDoubleClick 이벤트에 응답 하는 코드를 추가 합니다.

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>BeforeDoubleClick 이벤트를 기반으로 NamedRange2에 텍스트를 삽입 하려면

1. **솔루션 탐색기**에서 **Sheet1** 또는 **Sheet1.cs** 를 마우스 오른쪽 단추로 클릭 하 고 **코드 보기**를 선택 합니다.

2. 이벤트 처리기가 다음과 같이 표시 되도록 코드를 추가 합니다 `namedRange1_BeforeDoubleClick` .

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3. C #에서는 아래 이벤트에 표시 된 것 처럼 명명 된 범위에 대 한 이벤트 처리기를 추가 해야 합니다 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>변경 이벤트에 응답 하는 코드를 추가 합니다.

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Change 이벤트를 기준으로 namedRange2에 텍스트를 삽입 하려면

1. 이벤트 처리기가 다음과 같이 표시 되도록 코드를 추가 합니다 `NamedRange1_Change` .

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    > Excel 범위에서 셀을 두 번 클릭 하면 편집 모드로 전환 되므로 <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 텍스트에 대 한 변경 내용이 없는 경우에도 선택 영역이 범위 밖으로 이동 하면 이벤트가 발생 합니다.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>SelectionChange 이벤트에 응답 하는 코드를 추가 합니다.

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>SelectionChange 이벤트를 기반으로 namedRange2에 텍스트를 삽입 하려면

1. **NamedRange1_SelectionChange** 이벤트 처리기가 다음과 같이 표시 되도록 코드를 추가 합니다.

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    > Excel 범위에서 셀을 두 번 클릭 하면 선택 영역이 범위로 이동 하기 때문에 이벤트가 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 발생 하기 전에 이벤트가 발생 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> 합니다.

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 통합 문서를 테스트 하 여 이벤트가 발생할 때 컨트롤의 이벤트를 설명 하는 텍스트가 <xref:Microsoft.Office.Tools.Excel.NamedRange> 다른 명명 된 범위에 삽입 되는지 확인할 수 있습니다.

### <a name="to-test-your-document"></a>문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 에 커서를 놓고 `namedRange1` 이벤트와 관련 된 텍스트가 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 삽입 되는지와 주석이 워크시트에 삽입 되는지 확인 합니다.

3. 안쪽을 두 번 클릭 `namedRange1` 하 고 이벤트에 대 한 텍스트가 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> 에 빨간색 기울임꼴 텍스트로 삽입 되는지 확인 `namedRange2` 합니다.

4. 외부를 클릭 하 `namedRange1` 고 텍스트를 변경 하지 않아도 편집 모드를 종료할 때 변경 이벤트가 발생 하는지 확인 합니다.

5. 에서 텍스트를 변경 `namedRange1` 합니다.

6. 외부를 클릭 하 `namedRange1` 고 이벤트 관련 텍스트가 <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 파란색 텍스트를 사용 하 여 삽입 되는지 확인 `namedRange2` 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 컨트롤의 이벤트에 대 한 프로그래밍의 기본 사항을 보여 줍니다 <xref:Microsoft.Office.Tools.Excel.NamedRange> . 다음에 나올 수 있는 작업은 다음과 같습니다.

- 프로젝트를 배포 합니다. 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [방법: NamedRange 컨트롤 크기 조정](../vsto/how-to-resize-namedrange-controls.md)
- [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)
