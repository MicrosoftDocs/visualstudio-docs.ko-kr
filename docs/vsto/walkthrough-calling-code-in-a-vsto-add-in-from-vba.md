---
title: '연습: VBA에서 VSTO 추가 기능의 코드 호출'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6fdbd2cf85086bac0aa7bb56c128a7ad6fe36f94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650780"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>연습: VBA에서 VSTO 추가 기능의 코드 호출
  이 연습에서는 VSTO 추가 기능의 개체를 VBA(Visual Basic for Applications) 및 COM VSTO 추가 기능을 비롯한 다른 Microsoft Office 솔루션에 노출하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 이 연습에서 Excel을 특정하게 사용하지는 않지만 여기에서 보여 주는 개념은 Visual Studio에서 제공하는 모든 VSTO 추가 기능 프로젝트 템플릿에 적용 가능합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 다른 Office 솔루션에 노출할 수 있는 클래스 정의

- 다른 Office 솔루션에 클래스 노출

- VBA 코드에서 클래스의 메서드 호출

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>VSTO 추가 기능 프로젝트 만들기
 첫 번째 단계는 Excel용 VSTO 추가 기능 프로젝트를 만드는 것입니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. Excel VSTO 추가 기능 프로젝트 템플릿을 사용하여 이름이 **ExcelImportData**인 Excel VSTO 추가 기능 프로젝트를 만듭니다. 자세한 내용은 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)을 참조하세요.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서는 **ThisAddIn.cs** 또는 **ThisAddIn.vb** 코드 파일을 열고 **ExcelImportData** 프로젝트를 **솔루션 탐색기**에 추가합니다.

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>다른 Office 솔루션에 노출할 수 있는 클래스 정의
 이 연습의 목적은 VBA 코드에서 VSTO 추가 기능에 있는 `ImportData` 클래스의 `AddInUtilities` 메서드를 호출하는 것입니다. 이 메서드는 현재 워크시트의 A1 셀에 문자열을 씁니다.

 `AddInUtilities` 클래스를 다른 Office 솔루션에 노출하려면 공용이고 COM에 표시되도록 클래스를 설정해야 합니다. 클래스에서 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 인터페이스도 노출해야 합니다. 다음 절차의 코드에서는 이러한 요구 사항을 충족하는 한 가지 방법을 보여 줍니다. 자세한 내용은 [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)을 참조하세요.

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>다른 Office 솔루션에 노출할 수 있는 클래스를 정의하려면

1. **프로젝트** 메뉴에서 **클래스 추가**를 클릭합니다.

2. **새 항목 추가** 대화 상자에서 새 클래스의 이름을 **AddInUtilities**로 변경하고 **추가**를 클릭합니다.

     **AddInUtilities.cs** 또는 **AddInUtilities.vb** 파일이 코드 편집기에서 열립니다.

3. 다음 지시문을 파일의 맨 위에 추가 합니다.

     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]

4. `AddInUtilities` 클래스를 다음 코드로 바꿉니다.

     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]

     이 코드에서는 `AddInUtilities` 클래스를 COM에 표시되도록 설정하고 `ImportData` 메서드를 클래스에 추가합니다. [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 인터페이스를 노출하기 위해 `AddInUtilities` 클래스는 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 특성도 갖고 있으며 COM에 표시되는 인터페이스를 구현합니다.

## <a name="expose-the-class-to-other-office-solutions"></a>클래스를 다른 Office 솔루션에 노출
 `AddInUtilities` 클래스를 다른 Office 솔루션에 노출하려면 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 클래스에서 `ThisAddIn` 메서드를 재정의합니다. 재정의에서 `AddInUtilities` 클래스의 인스턴스를 반환합니다.

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>AddInUtilities 클래스를 다른 Office 솔루션에 노출하려면

1. **솔루션 탐색기**에서 **Excel**을 확장합니다.

2. **ThisAddIn.cs** 또는 **ThisAddIn.vb**를 마우스 오른쪽 단추로 클릭한 다음 **코드 보기**를 클릭합니다.

3. `ThisAddIn` 클래스에 다음 코드를 추가합니다.

     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]

4. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

     솔루션이 오류 없이 빌드되는지 확인합니다.

## <a name="test-the-vsto-add-in"></a>VSTO 추가 기능 테스트
 몇 가지 유형의 Office 솔루션에서 `AddInUtilities` 클래스를 호출할 수 있습니다. 이 연습에서는 Excel 통합 문서에서 VBA 코드를 사용합니다. 사용할 수 있는 다른 유형의 Office 솔루션에 대 한 자세한 내용은 [다른 office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)을 참조 하세요.

### <a name="to-test-your-vsto-add-in"></a>VSTO 추가 기능을 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. Excel에서 현재 통합 문서를 Excel 매크로 사용 통합 문서(*.xlsm)로 저장합니다. 통합 문서를 바탕 화면과 같은 편리한 위치에 저장합니다.

3. 리본에서 **개발자** 탭을 클릭합니다.

    > [!NOTE]
    > **개발자** 탭이 표시되지 않는 경우 먼저 개발자 탭을 표시해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발자 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)를 참조 하세요.

4. **코드** 그룹에서 **Visual Basic**을 클릭합니다.

     Visual Basic Editor가 열립니다.

5. **프로젝트** 창에서 **ThisWorkbook**을 두 번 클릭합니다.

     `ThisWorkbook` 개체의 코드 파일이 열립니다.

6. 다음 VBA 코드를 코드 파일에 추가합니다. 이 코드는 먼저 **ExcelImportData** VSTO 추가 기능을 나타내는 COMAddIn 개체를 가져옵니다. 그런 다음 코드는 COMAddIn 개체의 개체 속성을 사용 하 여 메서드를 호출 합니다 `ImportData` .

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. **F5**키를 누릅니다.

8. 새로운 **Imported Data** 시트가 통합 문서에 추가되었는지 확인합니다. 또한 A1 셀에 **This is my data**문자열이 포함되어 있는지 확인합니다.

9. Excel을 종료합니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서 VSTO 추가 기능 프로그래밍에 대해 자세히 알아볼 수 있습니다.

- `ThisAddIn` 클래스를 사용하여 VSTO 추가 기능 프로젝트에서 호스트 애플리케이션을 자동화하고 다른 작업을 수행합니다. 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

- VSTO 추가 기능에서 사용자 지정 작업창을 만듭니다. 자세한 내용은 [사용자 지정 작업](../vsto/custom-task-panes.md) 창 및 [방법: 응용 프로그램에 사용자 지정 작업창 추가](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)를 참조 하세요.

- VSTO 추가 기능에서 리본을 사용자 지정 합니다. 자세한 내용은 [리본 개요](../vsto/ribbon-overview.md) 및 [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Office 솔루션 개발](../vsto/developing-office-solutions.md)
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [확장성 인터페이스를 사용 하 여 UI 기능 사용자 지정](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
