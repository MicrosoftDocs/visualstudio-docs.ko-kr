---
title: '연습: Windows Form을 사용 하 여 데이터 수집'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 893418ca5eb82e9466ea13a12088b38fd496e695
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841515"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>연습: Windows Form을 사용 하 여 데이터 수집
  이 연습에서는 Microsoft Office Excel용 문서 수준 사용자 지정에서 Windows Form을 열고 사용자로부터 정보를 수집하고 워크시트 셀에 해당 정보를 기록하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 이 연습에서는 Excel용 문서 수준 프로젝트를 사용하지만 연습에서 설명하는 개념을 다른 Office 프로젝트에 적용할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 첫 번째 단계에서 Excel 통합 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. **WinFormInput**이라는 이름의 Excel 통합 문서 프로젝트를 만들고 마법사에서 **새 문서 만들기** 를 선택합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio의 디자이너에 새 Excel 통합 문서가 열리고 **WinFormInput** 프로젝트가 **솔루션 탐색기**에 추가됩니다.

## <a name="add-a-namedrange-control-to-the-worksheet"></a>워크시트에 NamedRange 컨트롤 추가

### <a name="to-add-a-named-range-to-sheet1"></a>Sheet1에 명명된 범위를 추가하려면

1. **에서** A1 `Sheet1`셀을 선택합니다.

2. **이름** 상자에 **formInput**를 입력합니다.

     **이름** 상자는 워크시트의 **A** 열 바로 위에 수식 입력줄의 왼쪽에 있습니다.

3. **Enter** 키를 누릅니다.

     <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 **A1**셀에 추가됩니다. 워크시트에 볼 수 있는 표시가 없지만 **A1** 셀을 선택하면 **formInput** 이 **이름** 상자(왼쪽에 워크시트 바로 위) 및 **속성** 창에 나타납니다.

## <a name="add-a-windows-form-to-the-project"></a>프로젝트에 Windows Form 추가
 사용자에게 정보 확인 메시지를 표시하는 Windows Form을 만듭니다.

### <a name="to-add-a-windows-form"></a>Windows Form을 추가하려면

1. **솔루션 탐색기** 에서 **WinFormInput**프로젝트를 선택합니다.

2. **프로젝트** 메뉴에서 **새 Windows Form 추가**를 클릭합니다.

3. 양식을 **GetInputString.vb** 또는 **GetInputString.cs**로 명명한 다음 **추가**를 클릭합니다.

    새 양식이 디자이너에서 열립니다.

4. 폼에 <xref:System.Windows.Forms.TextBox> 및 <xref:System.Windows.Forms.Button> 를 추가합니다.

5. 단추를 선택하고 **속성** 창에서 **Text** 속성을 찾은 다음 텍스트를 **확인**으로 변경합니다.

   그런 다음 코드를 `ThisWorkbook.vb` 또는 `ThisWorkbook.cs` 에 추가하여 사용자의 정보를 수집합니다.

## <a name="display-the-windows-form-and-collecting-information"></a>Windows Form 표시 및 정보 수집
 `GetInputString` Windows Form의 인스턴스를 만들어 표시한 다음 사용자의 정보를 워크시트의 임의 셀에 기록합니다.

#### <a name="to-display-the-form-and-collect-information"></a>양식을 표시하고 정보를 수집하려면

1. **솔루션 탐색기** 에서 **ThisWorkbook.vb** 또는 **ThisWorkbook.cs**를 마우스 오른쪽 단추로 클릭한 다음 **코드 보기**를 클릭합니다.

2. <xref:Microsoft.Office.Tools.Excel.Workbook.Open> 의 `ThisWorkbook`이벤트 처리기에서 다음 코드를 추가하여 `GetInputString` 양식에 대한 변수를 선언한 다음 양식을 표시합니다.

   > [!NOTE]
   > C#에서는 아래 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 이벤트에 표시된 것처럼 이벤트 처리기를 추가해야 합니다. 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]

3. 명명된 범위에 텍스트를 쓰는 `WriteStringToCell` 이라는 메서드를 만듭니다. 이 메서드가 양식에서 호출되고 사용자의 입력이 <xref:Microsoft.Office.Tools.Excel.NamedRange> A1 `formInput`셀의 **컨트롤인**에 전달됩니다.

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]

   그런 다음 양식에 코드를 추가하여 단추의 클릭 이벤트를 처리합니다.

## <a name="send-information-to-the-worksheet"></a>워크시트에 정보 보내기

### <a name="to-send-information-to-the-worksheet"></a>워크시트에 정보를 보내려면

1. **솔루션 탐색기** 에서 **GetInputString**을 마우스 오른쪽으로 클릭한 다음 **뷰 디자이너**를 클릭합니다.

2. 해당 단추를 두 번 클릭하여 단추의 추가된 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기로 코드 파일을 엽니다.

3. 코드를 이벤트 처리기에 추가하여 텍스트 상자에서 받은 입력을 `WriteStringToCell`함수로 보낸 다음 양식을 닫습니다.

     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]

## <a name="test"></a>테스트
 이제 프로젝트를 실행할 수 있습니다. Windows Form이 나타나고 사용자 입력이 워크시트에 표시됩니다.

### <a name="to-test-your-workbook"></a>통합 문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. Windows Form이 나타나는지 확인합니다.

3. 텍스트 상자에 **Hello World** 를 입력한 다음 **확인**을 클릭합니다.

4. **Hello World** 가 워크시트의 **A1** 셀에 나타나는지 확인합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 Windows Form을 표시하고 데이터를 워크시트에 전달하는 기본 사항을 보여 줍니다. 수행할 수 있는 다른 작업은 다음과 같습니다.

- Excel 통합 문서 또는 Word 문서에서 Windows Forms 컨트롤 사용. 자세한 내용은 [Windows Forms 컨트롤의 Office 문서 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)를 참조 하세요.

- 문서 수준 사용자 지정 또는 VSTO 추가 기능에서 Microsoft Office 응용 프로그램의 사용자 인터페이스를 수정 합니다. 자세한 내용은 [OFFICE UI 사용자 지정](../vsto/office-ui-customization.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Office 솔루션 개발](../vsto/developing-office-solutions.md)
- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [문서 수준 사용자 지정 프로그램](../vsto/programming-document-level-customizations.md)
- [Word를 사용한 연습](../vsto/walkthroughs-using-word.md)
- [Excel을 사용한 연습](../vsto/walkthroughs-using-excel.md)
