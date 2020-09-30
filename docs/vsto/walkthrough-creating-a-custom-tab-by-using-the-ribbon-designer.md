---
title: '연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f311f35ba4a8c443f47941a905ee4cf4d3ebfb2
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585017"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기
  리본 디자이너를 사용하여 사용자 지정 탭을 만들고 이 탭에 컨트롤을 추가 및 배치할 수 있습니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- [작업 창을 만듭니다](#BKMK_CreateActionsPanes).

- [사용자 지정 탭을 만듭니다](#BKMK_CreateCustomTab).

- [사용자 지정 탭의 단추를 사용 하 여 작업 창을 숨기 거 나 표시](#BKMK_HideShowActionsPane)합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Excel 통합 문서 프로젝트 만들기
 리본 디자이너를 사용하는 단계는 모든 Office 애플리케이션에서 거의 동일합니다. 이 예제에서는 Excel 통합 문서를 사용합니다.

### <a name="to-create-an-excel-workbook-project"></a>Excel 통합 문서 프로젝트를 만들려면

- 이름이 **Myexcelribbon**인 Excel 통합 문서 프로젝트를 만듭니다. 자세한 내용은 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)을 참조하세요.

     Visual Studio가 디자이너에서 새 통합 문서를 열고 **Myexcelribbon** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> 작업 창 만들기
 프로젝트에 두 개의 사용자 지정 작업 창을 추가합니다. 나중에 이러한 작업 창을 표시하거나 숨기는 단추를 사용자 지정 탭에 추가합니다.

### <a name="to-create-actions-panes"></a>작업 창을 만들려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

2. **새 항목 추가** 대화 상자에서 **ActionsPaneControl**을 선택 하 고 **추가**를 선택 합니다.

     **ActionsPaneControl1.cs** 또는 **actionspanecontrol1.vb 파일이** 파일이 디자이너에서 열립니다.

3. **도구 상자**의 **공용 컨트롤** 탭에서 디자이너 화면에 레이블을 추가 합니다.

4. **속성** 창에서 Label1의 **Text** 속성을 **Actions Pane 1**로 설정 합니다.

5. 1-5단계를 반복하여 두 번째 작업 창 및 레이블을 만듭니다. 두 번째 레이블의 **Text** 속성을 **Actions Pane 2**로 설정 합니다.

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> 사용자 지정 탭 만들기
 Office 애플리케이션의 디자인 지침 중 하나는 사용자가 항상 Office 애플리케이션 UI를 제어할 수 있어야 한다는 것입니다. 작업 창에 대해 이 기능을 추가하려면 리본 메뉴의 사용자 지정 탭에서 각 작업 창을 표시하거나 숨기는 단추를 추가합니다. 사용자 지정 탭을 만들려면 프로젝트에 **리본 (비주얼 디자이너)** 항목을 추가 합니다. 이 디자이너는 컨트롤을 추가 및 배치하고, 컨트롤 속성을 설정하고, 컨트롤 이벤트를 처리하는 데 유용합니다.

### <a name="to-create-a-custom-tab"></a>사용자 지정 탭을 만들려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

2. **새 항목 추가** 대화 상자에서 **리본(비주얼 디자이너)** 을 선택합니다.

3. 새 리본의 이름을 **myribbon.vb**로 변경 하 고 **추가**를 선택 합니다.

     **MyRibbon.cs** 또는 **MyRibbon.vb** 파일이 리본 디자이너에서 열리고 기본 탭 및 그룹이 표시됩니다.

4. 리본 디자이너에서 기본 탭을 선택합니다.

5. **속성** 창에서 **ControlId** 속성을 확장 한 다음 **고 controlidtype** 속성을 **Custom**으로 설정 합니다.

6. **레이블** 속성을 **My Custom Tab**으로 설정 합니다.

7. 리본 디자이너에서 **group1**을 선택 합니다.

8. **속성** 창에서 **Label** 을 **Actions Pane Manager**로 설정 합니다.

9. **도구 상자**의 **Office 리본 컨트롤** 탭에서 단추를 **group1**로 끌어 옵니다.

10. **Button1**을 선택 합니다.

11. **속성** 창에서 **Label** 을 **Show Actions Pane 1**로 설정 합니다.

12. **Group1**에 두 번째 단추를 추가 하 고 **Label** 속성을 **Show Actions Pane 2**로 설정 합니다.

13. **도구 상자**의 **Office 리본 컨트롤** 탭에서 **ToggleButton** 컨트롤을 **group1**로 끌어 옵니다.

14. **Label** 속성을 **Hide Actions Pane**으로 설정 합니다.

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> 사용자 지정 탭의 단추를 사용 하 여 작업 창 숨기기 및 표시
 마지막 단계는 사용자에게 응답하는 코드를 추가하는 것입니다. 두 단추의 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> 이벤트와 설정/해제 단추의 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 이벤트에 대한 이벤트 처리기를 추가합니다. 이러한 이벤트 처리기에 작업 창을 숨기거나 표시할 수 있는 코드를 추가합니다.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>사용자 지정 탭의 단추를 사용하여 작업 창을 숨기거나 표시하려면

1. **솔루션 탐색기**에서 *MyRibbon.cs* 또는 *myribbon.vb*에 대 한 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다.

2. 다음 코드를 `MyRibbon` 클래스의 맨 위에 추가합니다. 이 코드는 두 개의 작업 창 개체를 만듭니다.

     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]

3. `MyRibbon_Load` 메서드를 다음 코드로 바꿉니다. 이 코드는 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> 컬렉션에 작업 창 개체를 추가하고 뷰에서 해당 개체를 숨깁니다. 또한 Visual C# 코드는 여러 리본 컨트롤 이벤트에 대리자를 연결합니다.

     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]

4. `MyRibbon` 클래스에 다음 세 개의 이벤트 처리기 메서드를 추가합니다. 이러한 메서드는 두 단추의 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> 이벤트와 설정/해제 단추의 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 이벤트를 처리합니다. button1 및 button2에 대한 이벤트 처리기는 대체 작업 창을 표시합니다. toggleButton1에 대한 이벤트 처리기는 활성 작업 창을 표시하거나 숨깁니다.

     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]

## <a name="test-the-custom-tab"></a>사용자 지정 탭 테스트
 프로젝트를 실행 하면 Excel이 시작 되 고 리본 메뉴에 **My Custom tab** 탭이 나타납니다. **내 사용자 지정 탭** 의 단추를 선택 하 여 작업 창을 표시 하거나 숨깁니다.

### <a name="to-test-the-custom-tab"></a>사용자 지정 탭을 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. **My Custom tab** 탭을 선택 합니다.

3. **사용자 지정 작업 창 관리자** 그룹에서 **Show Actions pane 1**을 선택 합니다.

     작업 창이 나타나고 레이블 **작업 창 1**이 표시 됩니다.

4. **Show Actions Pane 2**를 선택 합니다.

     작업 창이 나타나고 레이블 **작업 창 2**가 표시 됩니다.

5. **작업 창 숨기기**를 선택 합니다.

     작업 창이 더 이상 표시되지 않습니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서는 Office UI를 사용자 지정하는 방법에 대해 더 자세히 설명합니다.

- 문서 수준 사용자 지정에 컨텍스트 기반 UI를 추가합니다. 자세한 내용은 [작업 창 개요](../vsto/actions-pane-overview.md)를 참조 하세요.

- 표준 또는 사용자 지정 Microsoft Office Outlook 양식을 확장합니다. 자세한 내용은 [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [런타임에 리본 메뉴에 액세스](../vsto/accessing-the-ribbon-at-run-time.md)
- [리본 개요](../vsto/ribbon-overview.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [Outlook에 대 한 리본 사용자 지정](../vsto/customizing-a-ribbon-for-outlook.md)
- [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [방법: 리본의 탭 위치 변경](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [방법: 기본 제공 탭 사용자 지정](../vsto/how-to-customize-a-built-in-tab.md)
- [방법: backstage 보기에 컨트롤 추가](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [리본 개체 모델 개요](../vsto/ribbon-object-model-overview.md)
