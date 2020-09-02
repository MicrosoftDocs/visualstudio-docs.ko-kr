---
title: CheckBox 컨트롤을 사용 하 여 워크시트 서식 변경
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 42d2c46f6fd61d74476933cfda3dea8c62b00c95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328697"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>연습: CheckBox 컨트롤을 사용 하 여 워크시트 서식 변경
  이 연습에서는 Microsoft Office Excel 워크시트에서 확인란을 사용 하 여 서식을 변경 하는 기본적인 방법을 보여 줍니다. Visual Studio에서 Office 개발 도구를 사용 하 여 프로젝트에 코드를 만들고 추가 합니다. 결과를 완료 된 샘플로 보려면 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)에서 Excel 컨트롤 샘플을 참조 하세요.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- 워크시트에 텍스트 및 컨트롤을 추가 합니다.

- 옵션이 선택 된 경우 텍스트의 서식을 지정 합니다.

- 프로젝트를 테스트 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 이 단계에서는 Visual Studio를 사용 하 여 Excel 통합 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. **내 Excel 서식 지정**을 사용 하 여 Excel 통합 문서 프로젝트를 만듭니다. **새 문서 만들기** 가 선택 되어 있는지 확인 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio가 디자이너에서 새 Excel 통합 문서를 열고 **Excel 서식 지정** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

## <a name="add-text-and-controls-to-the-worksheet"></a>워크시트에 텍스트 및 컨트롤 추가
 이 연습에서는 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 컨트롤에 세 개의 컨트롤과 일부 텍스트가 필요 <xref:Microsoft.Office.Tools.Excel.NamedRange> 합니다.

### <a name="to-add-three-check-boxes"></a>확인란 세 개를 추가 하려면

1. 통합 문서가 Visual Studio 디자이너에 열려 있고 열려 있는지 확인 `Sheet1` 합니다.

2. **도구 상자**의 **공용 컨트롤** 탭에서 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 컨트롤을 **Sheet1**의 **B2** 셀로 끌어 옵니다.

3. **보기** 메뉴에서 **속성** 창을 선택 합니다.

4. **Checkbox1** 이 **속성** 창의 개체 이름 목록 상자에 표시 되는지 여부를 표시 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyBoldFont**|
    |**Text**|**굵게**|

5. **B4** 셀에서 두 번째 확인란을 끌거나 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyItalicFont**|
    |**Text**|**기울임꼴**|

6. 세 번째 확인란을 셀 **B6** 또는 옆으로 끌고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyUnderlineFont**|
    |**Text**|**바뀝니다**|

7. **Ctrl** 키를 누른 상태에서 세 개의 확인란 컨트롤을 모두 선택 합니다.

8. Excel의 서식 탭 정렬 그룹에서 **맞춤**을 클릭 한 다음 **왼쪽 맞춤**을 클릭 합니다.

     세 개의 확인란 컨트롤은 선택한 첫 번째 컨트롤의 위치에서 왼쪽에 정렬 됩니다.

     그런 다음 컨트롤을 워크시트로 끌어 옵니다 <xref:Microsoft.Office.Tools.Excel.NamedRange> .

    > [!NOTE]
    > <xref:Microsoft.Office.Tools.Excel.NamedRange> **이름** 상자에 **textfont** 를 입력 하 여 컨트롤을 추가할 수도 있습니다.

#### <a name="to-add-text-to-a-namedrange-control"></a>NamedRange 컨트롤에 텍스트를 추가 하려면

1. 도구 상자의 **Excel 컨트롤** 탭에서 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 **B9**셀로 끌어 옵니다.

2. **$B $9** 이 편집 가능 텍스트 상자에 표시 되 고 **B9** 셀이 선택 되어 있는지 확인 합니다. 그렇지 않으면 **B9** 셀을 클릭 하 여 선택 합니다.

3. **확인**을 클릭합니다.

4. **B9** 셀은 이름이 인 범위가 됩니다 `NamedRange1` .

    워크시트에는 표시 되지 않지만 `NamedRange1` **B9** 셀을 선택한 경우에는 **이름 상자** 에 표시 됩니다 (왼쪽 워크시트 바로 위).

5. **NamedRange1** 이 **속성** 창의 개체 이름 목록 상자에 표시 되는지 여부를 표시 하 고 다음 속성을 변경 합니다.

   |속성|값|
   |--------------|-----------|
   |**이름**|**textFont**|
   |**Value2**|**이 텍스트의 서식을 변경 하려면 확인란을 클릭 합니다.**|

   그런 다음 옵션을 선택할 때 텍스트의 서식을 지정 하는 코드를 작성 합니다.

## <a name="format-the-text-when-an-option-is-selected"></a>옵션이 선택 된 경우 텍스트 서식 지정
 이 섹션에서는 사용자가 서식 옵션을 선택할 때 워크시트의 텍스트 형식이 변경 되도록 코드를 작성 합니다.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>확인란을 선택 하는 경우 서식을 변경 하려면

1. **Sheet1**을 마우스 오른쪽 단추로 클릭 한 다음 바로 가기 메뉴에서 **코드 보기** 를 클릭 합니다.

2. <xref:System.Windows.Forms.Control.Click>확인란의 이벤트 처리기에 다음 코드를 추가 합니다 `applyBoldFont` .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. <xref:System.Windows.Forms.Control.Click>확인란의 이벤트 처리기에 다음 코드를 추가 합니다 `applyItalicFont` .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. <xref:System.Windows.Forms.Control.Click>확인란의 이벤트 처리기에 다음 코드를 추가 합니다 `applyUnderlineFont` .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. C #에서는 아래와 같이 이벤트에 확인란에 대 한 이벤트 처리기를 추가 해야 합니다 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 확인란을 선택 하거나 선택 취소 하면 통합 문서를 테스트 하 여 텍스트의 서식이 올바르게 지정 되었는지 확인할 수 있습니다.

### <a name="to-test-your-workbook"></a>통합 문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 확인란을 선택하거나 선택을 취소합니다.

3. 텍스트의 형식이 올바르게 지정 되었는지 확인 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 Excel 워크시트에서 확인란 및 텍스트 서식 지정을 사용 하는 기본 사항을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 프로젝트를 배포 합니다. 자세한 내용은 [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)를 참조 하세요.
- 단추를 사용하여 텍스트 상자를 채웁니다. 자세한 내용은 [연습: 워크시트에서 단추를 사용 하 여 텍스트 상자에 텍스트 표시](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Excel을 사용한 연습](../vsto/walkthroughs-using-excel.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 문서에서 Windows Forms 컨트롤의 제한 사항](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
