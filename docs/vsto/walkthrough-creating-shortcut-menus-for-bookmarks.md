---
title: '연습: 책갈피에 대 한 바로 가기 메뉴 만들기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b4b412d2e9456142c1be1af388e2803634d15c0
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91146911"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>연습: 책갈피에 대 한 바로 가기 메뉴 만들기
  이 연습에서는 <xref:Microsoft.Office.Tools.Word.Bookmark> Word 용 문서 수준 사용자 지정에서 컨트롤에 대 한 바로 가기 메뉴를 만드는 방법을 보여 줍니다. 사용자가 책갈피의 텍스트를 마우스 오른쪽 단추로 클릭 하면 바로 가기 메뉴가 나타나고 텍스트 서식을 지정 하는 데 사용할 수 있는 사용자 옵션이 제공 됩니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- [프로젝트를 만듭니다](#BKMK_CreateProject).

- [문서에 텍스트와 책갈피를 추가](#BKMK_addtextandbookmarks)합니다.

- [바로 가기 메뉴에 명령을 추가](#BKMK_AddCmndsShortMenu)합니다.

- [책갈피 텍스트의 서식을 지정](#BKMK_formattextbkmk)합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a><a name="BKMK_CreateProject"></a> 프로젝트 만들기
 첫 번째 단계는 Visual Studio에서 Word 문서 프로젝트를 만드는 것입니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

- 이름 **내 책갈피 바로 가기 메뉴**를 포함 하는 Word 문서 프로젝트를 만듭니다. 마법사에서 **새 문서 만들기**를 선택 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio에서 디자이너에 새 Word 문서가 열리고 **책갈피 바로 가기 메뉴** 프로젝트가 **솔루션 탐색기**에 추가 됩니다.

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> 문서에 텍스트 및 책갈피 추가
 문서에 텍스트를 추가 하 고 두 개의 겹치는 책갈피를 추가 합니다.

### <a name="to-add-text-to-your-document"></a>문서에 텍스트를 추가 하려면

- 프로젝트 디자이너에 표시 되는 문서에서 다음 텍스트를 입력 합니다.

     **책갈피에서 텍스트를 마우스 오른쪽 단추로 클릭 하면 바로 가기 메뉴를 만드는 예가 여기에 해당 합니다.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>문서에 책갈피 컨트롤을 추가 하려면

1. **도구 상자**의 **Word 컨트롤** 탭에서 컨트롤을 문서로 끌어 옵니다 <xref:Microsoft.Office.Tools.Word.Bookmark> .

    **책갈피 컨트롤 추가** 대화 상자가 나타납니다.

2. "텍스트를 마우스 오른쪽 단추로 클릭 하면 바로 가기 메뉴 만들기" 라는 단어를 선택한 다음 **확인**을 클릭 합니다.

    `bookmark1` 이 문서에 추가 됩니다.

3. <xref:Microsoft.Office.Tools.Word.Bookmark>"책갈피의 텍스트를 마우스 오른쪽 단추로 클릭 하십시오." 라는 단어에 다른 컨트롤을 추가 합니다.

    `bookmark2` 이 문서에 추가 됩니다.

   > [!NOTE]
   > "텍스트를 마우스 오른쪽 단추로 클릭 하십시오." 라는 단어는 및 둘 다에 있습니다 `bookmark1` `bookmark2` .

   디자인 타임에 문서에 책갈피를 추가 하면 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤이 생성 됩니다. 책갈피의 여러 이벤트에 대해 프로그래밍할 수 있습니다. <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>사용자가 책갈피의 텍스트를 마우스 오른쪽 단추로 클릭 하면 바로 가기 메뉴가 표시 되도록 책갈피의 이벤트에 코드를 작성할 수 있습니다.

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> 바로 가기 메뉴에 명령 추가
 문서를 마우스 오른쪽 단추로 클릭할 때 표시 되는 바로 가기 메뉴에 단추를 추가 합니다.

### <a name="to-add-commands-to-a-shortcut-menu"></a>바로 가기 메뉴에 명령을 추가 하려면

1. **리본 XML** 항목을 프로젝트에 추가 합니다. 자세한 내용은 [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)을 참조 하세요.

2. **솔루션 탐색기**에서 **ThisDocument.cs** 또는 **ThisDocument**를 선택 합니다.

3. 메뉴 모음에서 코드 **보기**를 선택  >  **Code**합니다.

     **ThisDocument** 클래스 파일이 코드 편집기에서 열립니다.

4. **ThisDocument** 클래스에 다음 코드를 추가 합니다. 이 코드는 CreateRibbonExtensibilityObject 메서드를 재정의 하 고 Office 응용 프로그램에 리본 XML 클래스를 반환 합니다.

     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]

5. **솔루션 탐색기**에서 리본 XML 파일을 선택합니다. 기본적으로 리본 XML 파일의 이름은 Ribbon1.xml입니다.

6. 메뉴 모음에서 코드 **보기**를 선택  >  **Code**합니다.

     코드 편집기에서 리본 xml 파일이 열립니다.

7. 코드 편집기에서 리본 XML 파일의 내용을 다음 코드로 바꿉니다.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="BoldButton" label="Bold" onAction="ButtonClick"
               getVisible="GetVisible" />
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"
              getVisible="GetVisible"/>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

     이 코드는 문서를 마우스 오른쪽 단추로 클릭할 때 나타나는 바로 가기 메뉴에 두 개의 단추를 추가 합니다.

8. **솔루션 탐색기**에서를 마우스 오른쪽 단추로 클릭 한 `ThisDocument` 다음 **코드 보기**를 클릭 합니다.

9. 클래스 수준에서 다음 변수 및 책갈피 변수를 선언 합니다.

     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]

10. **솔루션 탐색기**에서 리본 코드 파일을 선택 합니다. 기본적으로 리본 코드 파일의 이름은 **Ribbon1.cs** 또는 **ribbon1.xml**입니다.

11. 메뉴 모음에서 코드 **보기**를 선택  >  **Code**합니다.

     코드 편집기에서 리본 코드 파일이 열립니다.

12. 리본 코드 파일에서 다음 메서드를 추가 합니다. 문서의 바로 가기 메뉴에 추가한 두 단추에 대 한 콜백 메서드입니다. 이 메서드는 바로 가기 메뉴에 이러한 단추가 표시 되는지 여부를 결정 합니다. 굵게 및 기울임꼴 단추는 책갈피 안에서 텍스트를 마우스 오른쪽 단추로 클릭 하는 경우에만 표시 됩니다.

     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> 책갈피의 텍스트 서식 지정

### <a name="to-format-the-text-in-the-bookmark"></a>책갈피 텍스트의 서식을 지정 하려면

1. 리본 코드 파일에서 `ButtonClick` 책갈피에 형식을 적용 하는 이벤트 처리기를 추가 합니다.

     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]

2. **솔루션 탐색기** **ThisDocument.cs** 또는 **ThisDocument**를 선택 합니다.

3. 메뉴 모음에서 코드 **보기**를 선택  >  **Code**합니다.

     **ThisDocument** 클래스 파일이 코드 편집기에서 열립니다.

4. **ThisDocument** 클래스에 다음 코드를 추가 합니다.

     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]

    > [!NOTE]
    > 책갈피가 겹치는 경우를 처리 하는 코드를 작성 해야 합니다. 이렇게 하지 않으면 기본적으로 선택 영역의 모든 책갈피에 대해 코드가 호출 됩니다.

5. C #에서 책갈피 컨트롤에 대 한 이벤트 처리기를 이벤트에 추가 해야 합니다 <xref:Microsoft.Office.Tools.Word.Document.Startup> . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]

## <a name="test-the-application"></a>애플리케이션 테스트
 문서를 테스트 하 여 책갈피에서 텍스트를 마우스 오른쪽 단추로 클릭 하 고 텍스트의 형식이 올바르게 지정 된 경우 바로 가기 메뉴에 굵게 표시 및 기울임꼴 메뉴 항목이 표시 되는지 확인 합니다.

### <a name="to-test-your-document"></a>문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 첫 번째 책갈피를 마우스 오른쪽 단추로 클릭 한 다음 **굵게**를 클릭 합니다.

3. 의 모든 텍스트 `bookmark1` 형식이 굵게 설정 되어 있는지 확인 합니다.

4. 책갈피가 겹치는 텍스트를 마우스 오른쪽 단추로 클릭 한 다음 **기울임꼴**을 클릭 합니다.

5. 의 모든 텍스트가 기울임꼴 인지 확인 하 `bookmark2` 고 해당 부분의 텍스트 부분만 `bookmark1` `bookmark2` 기울임꼴입니다.

## <a name="next-steps"></a>다음 단계
 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- Excel에서 호스트 컨트롤의 이벤트에 응답 하는 코드를 작성 합니다. 자세한 내용은 [연습: NamedRange 컨트롤의 이벤트에 대 한 프로그래밍](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)을 참조 하세요.

- 확인란을 사용 하 여 책갈피의 서식을 변경할 수 있습니다. 자세한 내용은 [연습: CheckBox 컨트롤을 사용 하 여 문서 서식 변경](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Word를 사용한 연습](../vsto/walkthroughs-using-word.md)
- [Office UI 사용자 지정](../vsto/office-ui-customization.md)
- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)
- [책갈피 컨트롤](../vsto/bookmark-control.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
