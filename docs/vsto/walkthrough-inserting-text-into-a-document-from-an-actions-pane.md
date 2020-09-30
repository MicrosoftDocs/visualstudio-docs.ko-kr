---
title: '연습: 작업 창에서 문서에 텍스트 삽입'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5c65027d7670c4d6789f32eb4d9080df061d904a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584965"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>연습: 작업 창에서 문서에 텍스트 삽입
  이 연습에서는 Microsoft Office Word 문서에서 작업 창을 만드는 방법을 보여 줍니다. 작업 창에는 입력을 수집한 다음 텍스트를 문서에 보내는 두 개의 컨트롤이 포함 되어 있습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 작업 창 컨트롤에서 Windows Forms 컨트롤을 사용 하 여 인터페이스를 디자인 합니다.

- 응용 프로그램을 열 때 작업 창을 표시 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트 만들기
 첫 번째 단계에서는 Word 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. **내 기본 작업 창**이라는 이름으로 Word 문서 프로젝트를 만듭니다. 마법사에서 **새 문서 만들기**를 선택 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio가 디자이너에서 새 Word 문서를 열고 **솔루션 탐색기**에 **내 기본 작업 창** 프로젝트를 추가 합니다.

## <a name="add-text-and-bookmarks-to-the-document"></a>문서에 텍스트 및 책갈피 추가
 작업 창이 문서에서 책갈피에 텍스트를 보냅니다. 문서를 디자인 하려면 일부 텍스트를 입력 하 여 기본 양식을 만듭니다.

### <a name="to-add-text-to-your-document"></a>문서에 텍스트를 추가 하려면

1. Word 문서에 다음 텍스트를 입력 합니다.

    **3 월 21 일, 2008**

    **이름**

    **주소**

    **Word의 기본 작업 창에 대 한 예입니다.**

   <xref:Microsoft.Office.Tools.Word.Bookmark>Visual Studio의 **도구 상자** 에서 끌거나 Word의 **책갈피** 대화 상자를 사용 하 여 컨트롤을 문서에 추가할 수 있습니다.

### <a name="to-add-a-bookmark-control-to-your-document"></a>문서에 책갈피 컨트롤을 추가 하려면

1. **도구 상자**의 **Word 컨트롤** 탭에서 컨트롤을 문서로 끌어 옵니다 <xref:Microsoft.Office.Tools.Word.Bookmark> .

     **책갈피 컨트롤 추가** 대화 상자가 나타납니다.

2. 단락 표시를 선택 하지 않고 단어 **이름을**선택 하 고 **확인**을 클릭 합니다.

    > [!NOTE]
    > 단락 표시는 책갈피의 외부에 있어야 합니다. 문서에 단락 표시가 표시 되지 않는 경우 **도구** 메뉴를 클릭 하 **Microsoft Office Word 도구** 를 가리킨 다음 **옵션**을 클릭 합니다. **보기** 탭을 클릭 하 고 **옵션** 대화 상자의 **서식 표시** 섹션에서 **단락 표시** 확인란을 선택 합니다.

3. **속성** 창에서 **않고 책갈피 2** 의 **Name** 속성을 **showname**으로 변경 합니다.

4. 단락 표시를 선택 하지 않고 **주소**를 선택 합니다.

5. 리본의 **삽입** 탭에 있는 **링크** 그룹에서 **책갈피**를 클릭 합니다.

6. **책갈피** 대화 상자에서 **책갈피 이름** 상자에 **showaddress** 를 입력 하 고 **추가**를 클릭 합니다.

## <a name="add-controls-to-the-actions-pane"></a>작업 창에 컨트롤 추가
 작업 창 인터페이스를 디자인 하려면 프로젝트에 작업 창 컨트롤을 추가한 다음 작업 창 컨트롤에 Windows Forms 컨트롤을 추가 합니다.

### <a name="to-add-an-actions-pane-control"></a>작업 창 컨트롤을 추가 하려면

1. **솔루션 탐색기**에서 **내 기본 작업 창** 프로젝트를 선택 합니다.

2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

3. **새 항목 추가** 대화 상자에서 **작업 창 컨트롤**을 클릭 하 고 컨트롤의 이름을 **InsertTextControl으로** 선택한 다음 **추가**를 클릭 합니다.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>작업 창 컨트롤에 Windows Form 컨트롤을 추가 하려면

1. 작업 창 컨트롤이 디자이너에 표시 되지 않는 경우 **InsertTextControl**를 두 번 클릭 합니다.

2. **도구 상자**의 **공용 컨트롤** 탭에서 **Label** 컨트롤을 작업 창 컨트롤로 끌어 옵니다.

3. 레이블 컨트롤의 **Text** 속성을 **Name**으로 변경 합니다.

4. 작업 창 컨트롤에 **Textbox** 컨트롤을 추가 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**getName**|
    |**크기**|**130, 20**|

5. 작업 창 컨트롤에 두 번째 **Label** 컨트롤을 추가 하 고 **Text** 속성을 **Address**로 변경 합니다.

6. 작업 창 컨트롤에 두 번째 **Textbox** 컨트롤을 추가 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**getAddress**|
    |**반환 허용**|**True**|
    |**여러 줄**|**True**|
    |**크기**|**130, 40**|

7. 작업 창 컨트롤에 **Button** 컨트롤을 추가 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**addText**|
    |**Text**|**삽입**|

## <a name="add-code-to-insert-text-into-the-document"></a>문서에 텍스트를 삽입 하는 코드 추가
 작업 창에서 텍스트 상자의 텍스트를 문서의 적절 한 컨트롤에 삽입 하는 코드를 작성 <xref:Microsoft.Office.Tools.Word.Bookmark> 합니다. 클래스를 사용 `Globals` 하 여 작업 창의 컨트롤에서 문서의 컨트롤에 액세스할 수 있습니다. 자세한 내용은 [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)를 참조 하세요.

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>작업 창에서 문서의 책갈피에 텍스트를 삽입 하려면

1. <xref:System.Windows.Forms.Control.Click> **Addtext** 단추의 이벤트 처리기에 다음 코드를 추가 합니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]

2. C #에서는 단추 클릭에 대 한 이벤트 처리기를 추가 해야 합니다. 호출 후 생성자에이 코드를 추가할 수 있습니다 `InsertTextControl` `InitializeComponent` . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]

## <a name="add-code-to-show-the-actions-pane"></a>작업 창을 표시 하는 코드 추가
 작업 창을 표시 하려면 만든 컨트롤을 컨트롤 컬렉션에 추가 합니다.

### <a name="to-show-the-actions-pane"></a>작업 창을 표시 하려면

1. 클래스에서 작업 창 컨트롤의 새 인스턴스를 만듭니다 `ThisDocument` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]

2. 의 이벤트 처리기에 다음 코드를 추가 <xref:Microsoft.Office.Tools.Word.Document.Startup> `ThisDocument` 합니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]

## <a name="test-the-application"></a>애플리케이션 테스트
 문서를 테스트 하 여 문서를 열 때 작업 창이 열리고 단추를 클릭할 때 텍스트 상자에 입력 된 텍스트가 책갈피에 삽입 되는지 확인 합니다.

### <a name="to-test-your-document"></a>문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 작업 창이 표시 되는지 확인 합니다.

3. 작업 창의 텍스트 상자에 이름과 주소를 입력 하 고 **삽입**을 클릭 합니다.

## <a name="next-steps"></a>다음 단계
 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- Excel에서 작업 창을 만듭니다. 자세한 내용은 [방법: Excel 통합 문서에 작업 창 추가](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))를 참조 하세요.

- 작업 창의 컨트롤에 데이터를 바인딩합니다. 자세한 내용은 [연습: Word 작업 창의 컨트롤에 데이터 바인딩](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [작업 창 개요](../vsto/actions-pane-overview.md)
- [방법: Word 문서 또는 Excel 통합 문서에 작업 창 추가](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [방법: Excel 통합 문서에 작업 창 추가](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [방법: 작업 창에서 컨트롤 레이아웃 관리](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [책갈피 컨트롤](../vsto/bookmark-control.md)
