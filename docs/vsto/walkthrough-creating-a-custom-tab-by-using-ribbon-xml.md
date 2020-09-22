---
title: '연습: 리본 XML을 사용 하 여 사용자 지정 탭 만들기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e05bd9173b83ec3303a058dcf61ea48a7ef7675c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841447"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>연습: 리본 XML을 사용 하 여 사용자 지정 탭 만들기
  이 연습에서는 **리본 (XML)** 항목을 사용 하 여 사용자 지정 리본 탭을 만드는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- **추가 기능** 탭에 단추를 추가 합니다. **추가 기능** 탭은 리본 XML 파일에 정의 된 기본 탭입니다.

- **추가 기능** 탭의 단추를 사용 하 여 Word Microsoft Office 자동화

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>프로젝트 만들기
 첫 번째 단계는 Word VSTO 추가 기능 프로젝트를 만드는 것입니다. 나중에이 문서의 **추가 기능** 탭을 사용자 지정 합니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름이 **My리본** **추가 인 Word 추가 기능** 프로젝트를 만듭니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ThisAddIn.cs** 또는 **ThisAddIn** 코드 파일을 열고 **my리본 기능** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

## <a name="create-the-vsto-add-ins-tab"></a>VSTO 추가 기능 탭 만들기
 **추가 기능** 탭을 만들려면 프로젝트에 **리본 (XML)** 항목을 추가 합니다. 이 연습의 뒷부분에서는 이 탭에 일부 단추를 추가합니다.

### <a name="to-create-the-add-ins-tab"></a>추가 기능 탭을 만들려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

2. **새 항목 추가** 대화 상자에서 **리본 (XML)** 을 선택 합니다.

3. 새 리본 메뉴의 이름을 **MyRibbon**으로 변경하고 **추가**를 클릭합니다.

     **MyRibbon.cs** 또는 **myribbon.vb** 파일이 디자이너에서 열립니다. **MyRibbon.xml** 라는 XML 파일도 프로젝트에 추가 됩니다.

4. **솔루션 탐색기**에서 **ThisAddin.cs** 또는 **ThisAddin**을 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

5. **ThisAddin** 클래스에 다음 코드를 추가합니다. 이 코드는 `CreateRibbonExtensibilityObject` 메서드를 재정의하고 Office 애플리케이션에 리본 XML 클래스를 반환합니다.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. **솔루션 탐색기**에서 **my리본 추가 기능** 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **빌드**를 클릭 합니다. 프로젝트가 오류 없이 빌드되는지 확인합니다.

## <a name="add-buttons-to-the-add-ins-tab"></a>추가 기능 탭에 단추 추가
 이 VSTO 추가 기능은 활성 문서에 상용구 텍스트 및 특정 표를 추가하는 방법을 사용자에게 제공하기 위한 것입니다. 사용자 인터페이스를 제공 하려면 리본 XML 파일을 수정 하 여 **추가 기능** 탭에 두 개의 단추를 추가 합니다. 이 연습의 뒷부분에서 단추에 대한 콜백 메서드를 정의합니다. 리본 XML 파일에 대 한 자세한 내용은 [리본 xml](../vsto/ribbon-xml.md)을 참조 하세요.

### <a name="to-add-buttons-to-the-add-ins-tab"></a>추가 기능 탭에 단추를 추가 하려면

1. **솔루션 탐색기**에서 **MyRibbon.xml** 를 마우스 오른쪽 단추로 클릭 한 다음 **열기**를 클릭 합니다.

2. **Tab** 요소의 내용을 다음 XML로 바꿉니다. 이 XML은 기본 컨트롤 그룹의 레이블을 **내용**으로 변경 하 고 레이블이 **Insert Text** 및 **insert Table**인 두 개의 새 단추를 추가 합니다.

    ```xml
    <tab idMso="TabAddIns">
        <group id="ContentGroup" label="Content">
            <button id="textButton" label="Insert Text"
                 screentip="Text" onAction="OnTextButton"
                 supertip="Inserts text at the cursor location."/>
            <button id="tableButton" label="Insert Table"
                 screentip="Table" onAction="OnTableButton"
                 supertip="Inserts a table at the cursor location."/>
        </group>
    </tab>
    ```

## <a name="automate-the-document-by-using-the-buttons"></a>단추를 사용 하 여 문서 자동화
 `onAction`사용자가 클릭 하는 경우 작업을 수행 하려면 **텍스트 삽입** 및 **테이블 삽입** 단추에 대 한 콜백 메서드를 추가 해야 합니다. 리본 컨트롤의 콜백 메서드에 대 한 자세한 내용은 [리본 XML](../vsto/ribbon-xml.md)을 참조 하세요.

### <a name="to-add-callback-methods-for-the-buttons"></a>단추에 대한 콜백 메서드를 추가하려면

1. **솔루션 탐색기**에서 **MyRibbon.cs** 또는 **myribbon.vb**를 마우스 오른쪽 단추로 클릭 한 다음 **열기**를 클릭 합니다.

2. **MyRibbon.cs** 또는 **myribbon.vb** 파일 맨 위에 다음 코드를 추가 합니다. 이 코드는 <xref:Microsoft.Office.Interop.Word> 네임스페이스에 대한 별칭을 만듭니다.

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. `MyRibbon` 클래스에 다음 메서드를 추가합니다. 커서의 현재 위치에 있는 활성 문서에 문자열을 추가 하는 **텍스트 삽입** 단추에 대 한 콜백 메서드입니다.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. `MyRibbon` 클래스에 다음 메서드를 추가합니다. 커서의 현재 위치에 있는 활성 문서에 테이블을 추가 하는 **테이블 삽입** 단추에 대 한 콜백 메서드입니다.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>VSTO 추가 기능 테스트
 프로젝트를 실행 하면 Word가 열리고 리본 메뉴에 **추가 기능** 이라는 탭이 표시 됩니다. **추가 기능** 탭에서 **텍스트 삽입** 및 **표 삽입** 단추를 클릭 하 여 코드를 테스트 합니다.

### <a name="to-test-your-vsto-add-in"></a>VSTO 추가 기능을 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. **추가 기능** 탭이 리본 메뉴에 표시 되는지 확인 합니다.

3. **추가 기능** 탭을 클릭합니다.

4. **콘텐츠** 그룹이 리본 메뉴에 표시 되는지 확인 합니다.

5. **콘텐츠** 그룹에서 **텍스트 삽입** 단추를 클릭 합니다.

     문서에서 커서의 현재 위치에 문자열이 추가됩니다.

6. **콘텐츠** 그룹에서 **테이블 삽입** 단추를 클릭 합니다.

     문서에서 커서의 현재 위치에 표가 추가됩니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서는 Office UI를 사용자 지정하는 방법에 대해 더 자세히 설명합니다.

- 다른 Office 응용 프로그램의 리본을 사용자 지정 합니다. 리본 메뉴 사용자 지정을 지 원하는 응용 프로그램에 대 한 자세한 내용은 [리본 개요](../vsto/ribbon-overview.md)를 참조 하세요.

- 리본 디자이너를 사용 하 여 Office 응용 프로그램의 리본을 사용자 지정 합니다. 자세한 내용은 [Ribbon Designer](../vsto/ribbon-designer.md)을 참조하십시오.

- 사용자 지정 작업 창을 만듭니다. 자세한 내용은 [작업 창 개요](../vsto/actions-pane-overview.md)를 참조 하세요.

- Outlook 양식 영역을 사용하여 Microsoft Office Outlook의 UI를 사용자 지정합니다. 자세한 내용은 [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [리본 개요](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
