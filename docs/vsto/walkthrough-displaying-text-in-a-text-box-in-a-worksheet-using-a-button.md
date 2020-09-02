---
title: 단추를 사용 하 여 워크시트의 텍스트 상자에 텍스트 표시
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b30eea0152b75cdd0869ececac674ee5aeee7933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328715"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>연습: 워크시트에서 단추를 사용 하 여 텍스트 상자에 텍스트 표시
  이 연습에서는 Microsoft Office Excel 워크시트에서 단추 및 텍스트 상자를 사용 하는 방법 및 Visual Studio에서 Office 개발 도구를 사용 하 여 Excel 프로젝트를 만드는 방법에 대 한 기본 사항을 보여 줍니다. 결과를 완료 된 샘플로 보려면 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)에서 Excel 컨트롤 샘플을 참조 하세요.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- 워크시트에 컨트롤을 추가 합니다.

- 단추를 클릭할 때 텍스트 상자를 채웁니다.

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

1. 이름 **내 Excel 단추**를 사용 하 여 Excel 통합 문서 프로젝트를 만듭니다. **새 문서 만들기** 가 선택 되어 있는지 확인 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio가 디자이너에서 새 Excel 통합 문서를 열고 **내 Excel 단추** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

## <a name="add-controls-to-the-worksheet"></a>워크시트에 컨트롤 추가
 이 연습에서는 첫 번째 워크시트에 단추와 텍스트 상자가 필요 합니다.

### <a name="to-add-a-button-and-a-text-box"></a>단추 및 텍스트 상자를 추가하려면

1. Visual Studio 디자이너에서 **내 Excel Button.xlsx** 통합 문서가 열려 있는지 확인 `Sheet1` 합니다.

2. 도구 상자의 **공용 컨트롤** 탭에서를로 끌어 옵니다 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> `Sheet1` .

3. **보기** 메뉴에서 **속성 창**을 선택 합니다.

4. **TextBox1** 이 **속성** 창 드롭다운 상자에 표시 되는지, 텍스트 상자의 **Name** 속성을 **인 displaytext**로 변경 해야 합니다.

5. **Button** 컨트롤을로 끌어 오고 `Sheet1` 다음 속성을 변경 합니다.

   |속성|값|
   |--------------|-----------|
   |**이름**|**insertText**|
   |**Text**|**텍스트 삽입**|

   이제 단추를 클릭할 때 실행할 코드를 작성 합니다.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>단추를 클릭할 때 텍스트 상자 채우기
 사용자가 단추를 클릭할 때마다 **Hello World!** 가 텍스트 상자에 추가 됩니다.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>단추를 클릭할 때 텍스트 상자에 쓰려면

1. **솔루션 탐색기**에서 **Sheet1**을 마우스 오른쪽 단추로 클릭 한 다음 바로 가기 메뉴에서 **코드 보기** 를 클릭 합니다.

2. 단추의 이벤트 처리기에 다음 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. C #에서 다음과 같이 이벤트 처리기를 이벤트에 추가 해야 합니다 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 통합 문서를 테스트 하 여 메시지 Hello World 수 있는지 확인할 수 있습니다 **.** 단추를 클릭 하면 텍스트 상자에 나타납니다.

### <a name="to-test-your-workbook"></a>통합 문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 이 단추를 클릭합니다.

3. Hello World 되었는지 확인 **하세요.** 텍스트 상자에 나타납니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 Excel 워크시트에서 단추 및 텍스트 상자를 사용 하는 기본 사항을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 프로젝트를 배포 합니다. 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)를 참조 하세요.

- 확인란을 사용 하 여 서식 변경 자세한 내용은 [연습: CheckBox 컨트롤을 사용 하 여 워크시트 서식 변경](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Excel을 사용한 연습](../vsto/walkthroughs-using-excel.md)
- [Office 문서에서 Windows Forms 컨트롤의 제한 사항](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
