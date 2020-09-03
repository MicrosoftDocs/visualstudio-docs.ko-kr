---
title: 런타임에 VSTO 추가 기능의 문서에 컨트롤 추가
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e8cde57ece3774e94f923387e1a8f7ca71cf797
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254168"
---
# <a name="walkthrough-add-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>연습: 런타임에 VSTO 추가 기능의 문서에 컨트롤 추가
  VSTO 추가 기능을 사용 하 여 열려 있는 Microsoft Office Word 문서에 컨트롤을 추가할 수 있습니다. 이 연습에서는 리본을 사용 하 여 사용자가 또는을 문서에 추가할 수 있도록 하는 방법을 보여 줍니다 <xref:Microsoft.Office.Tools.Word.Controls.Button> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> .

 **적용 대상:** 이 항목의 정보는 Word 2010의 VSTO 추가 기능 프로젝트에 적용됩니다. 자세한 내용은 [Office 애플리케이션 및 프로젝트 형식에 따라 사용 가능한 기능](../vsto/features-available-by-office-application-and-project-type.md)을 참조하세요.

 이 연습에서는 다음 작업을 수행합니다.

- 새 Word VSTO 추가 기능 프로젝트 만들기

- 문서에 컨트롤을 추가하는 UI(사용자 인터페이스) 제공

- 런타임에 문서에 컨트롤 추가

- 문서에서 컨트롤 제거

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-a-new-word-add-in-project"></a>새 Word 추가 기능 프로젝트 만들기
 Word VSTO 추가 기능 프로젝트를 만드는 작업부터 시작합니다.

### <a name="to-create-a-new-word-vsto-add-in-project"></a>새 Word VSTO 추가 기능 프로젝트를 만들려면

1. 이름이 **Worddynamiccontrols**인 WORD 용 VSTO 추가 기능 프로젝트를 만듭니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

2. **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** 어셈블리에 대한 참조를 추가합니다. 이 참조는 이 연습의 뒷부분에서 프로그래밍 방식으로 문서에 Windows Forms 컨트롤을 추가하는 데 필요합니다.

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>문서에 컨트롤을 추가 하는 UI 제공
 Word에서 리본에 사용자 지정 탭을 추가합니다. 사용자는 탭에서 확인란을 선택하여 문서에 컨트롤을 추가할 수 있습니다.

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>문서에 컨트롤을 추가하는 UI를 제공하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

2. **새 항목 추가** 대화 상자에서 **리본(비주얼 디자이너)** 을 선택합니다.

3. 새 리본 메뉴의 이름을 **MyRibbon**으로 변경하고 **추가**를 클릭합니다.

    **MyRibbon.cs** 또는 **MyRibbon.vb** 파일이 리본 디자이너에서 열리고 기본 탭 및 그룹이 표시됩니다.

4. 리본 디자이너에서 **group1** 그룹을 클릭합니다.

5. **속성** 창에서 **레이블** 속성을 **group1** 에서 **컨트롤 추가**로 변경합니다.

6. **도구 상자** 의 **Office 리본 컨트롤**탭에서 **CheckBox** 컨트롤을 **group1**로 끌어옵니다.

7. **CheckBox1** 을 클릭하여 선택합니다.

8. **속성** 창에서 다음 속성을 변경합니다.

   | 속성 | 값 |
   |-----------|-----------------------|
   | **이름** | **addButtonCheckBox** |
   | **레이블** | **단추 추가** |

9. **group1**에 두 번째 확인란을 추가하고 다음 속성을 변경합니다.

   | 속성 | 값 |
   |-----------|---------------------------|
   | **이름** | **addRichTextCheckBox** |
   | **레이블** | **서식 있는 텍스트 컨트롤 추가** |

10. 리본 디자이너에서 **단추 추가**를 두 번 클릭합니다.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 단추 추가 **확인란의** 이벤트 처리기가 코드 편집기에서 열립니다.

11. 리본 디자이너로 돌아와서 **서식 있는 텍스트 컨트롤 추가**를 두 번 클릭합니다.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 서식 있는 텍스트 컨트롤 추가 **확인란의** 이벤트 처리기가 코드 편집기에서 열립니다.

    이 연습의 뒷부분에서는 이러한 이벤트 처리기에 코드를 추가하여 활성 문서에서 컨트롤을 추가 및 제거합니다.

## <a name="add-and-remove-controls-on-the-active-document"></a>활성 문서에서 컨트롤 추가 및 제거
 VSTO 추가 기능 코드에서 컨트롤을 추가하려면 먼저 활성 문서를 <xref:Microsoft.Office.Tools.Word.Document>*호스트 항목* 으로 변환해야 합니다. Office 솔루션에서 관리되는 컨트롤은 컨트롤에 대한 컨테이너 역할을 하는 호스트 항목에만 추가할 수 있습니다. VSTO 추가 기능 프로젝트에서는 런타임에 메서드를 사용 하 여 호스트 항목을 만들 수 있습니다 `GetVstoObject` .

 활성 문서에서 `ThisAddIn` 또는 <xref:Microsoft.Office.Tools.Word.Controls.Button> 를 추가 또는 제거하기 위해 호출할 수 있는 메서드를 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 클래스에 추가합니다. 이 연습 뒷부분에서는 리본에 있는 확인란의 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 이벤트 처리기에서 이러한 메서드를 호출합니다.

### <a name="to-add-and-remove-controls-on-the-active-document"></a>활성 문서에서 컨트롤을 추가 및 제거하려면

1. **솔루션 탐색기**에서 *ThisAddIn.cs* 또는 *ThisAddIn* 을 두 번 클릭 하 여 코드 편집기에서 파일을 엽니다.

2. `ThisAddIn` 클래스에 다음 코드를 추가합니다. 이 코드에서는 문서에 추가할 컨트롤을 나타내는 <xref:Microsoft.Office.Tools.Word.Controls.Button> 및 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 개체를 선언합니다.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]

3. `ThisAddIn` 클래스에 다음 메서드를 추가합니다. 사용자가 리본의 **단추 추가** 확인란을 클릭하면 확인란이 선택된 경우 이 메서드가 문서의 현재 선택 영역에 <xref:Microsoft.Office.Tools.Word.Controls.Button> 을 추가하고, 확인란 선택이 취소된 경우 <xref:Microsoft.Office.Tools.Word.Controls.Button> 을 제거합니다.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]

4. `ThisAddIn` 클래스에 다음 메서드를 추가합니다. 사용자가 리본의 **서식 있는 텍스트 컨트롤 추가** 확인란을 클릭하면 확인란이 선택된 경우 이 메서드가 문서의 현재 선택 영역에 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 을 추가하고, 확인란 선택이 취소된 경우 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 을 제거합니다.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]

## <a name="remove-the-button-control-when-the-document-is-saved"></a>문서 저장 시 단추 컨트롤 제거
 문서를 저장하고 닫으면 Windows Forms 컨트롤이 유지되지 않습니다. 그러나 각 컨트롤의 ActiveX 래퍼는 문서에 유지되므로 문서가 다시 열릴 때 이 래퍼의 테두리가 최종 사용자에게 표시됩니다. VSTO 추가 기능에서 동적으로 생성 된 Windows Forms 컨트롤을 정리 하는 방법에는 여러 가지가 있습니다. 이 연습에서는 문서를 저장할 때 프로그래밍 방식으로 컨트롤을 제거 <xref:Microsoft.Office.Tools.Word.Controls.Button> 합니다.

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>문서 저장 시 단추 컨트롤을 제거하려면

1. *ThisAddIn.cs* 또는 *ThisAddIn* 코드 파일에서 다음 메서드를 클래스에 추가 `ThisAddIn` 합니다. 이 메서드는 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 이벤트의 기본 이벤트 처리기입니다. 저장된 문서에 연결된 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목이 있는 경우 이벤트 처리기에서 해당 호스트 항목을 가져오고 <xref:Microsoft.Office.Tools.Word.Controls.Button> 컨트롤이 있는 경우 이를 제거합니다.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]

2. C#에서 다음 코드를 `ThisAddIn_Startup` 이벤트 처리기에 추가합니다. 이 코드는 C#에서 `Application_DocumentBeforeSave` 이벤트 처리기를 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 이벤트와 연결하는 데 필요합니다.

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>사용자가 리본의 확인란을 클릭할 때 컨트롤 추가 및 제거
 마지막으로 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 리본에 추가한 확인란의 이벤트 처리기를 수정 하 여 문서에 컨트롤을 추가 하거나 제거 합니다.

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>사용자가 리본의 확인란을 클릭할 때 컨트롤을 추가 하거나 제거 하려면

1. *MyRibbon.cs* 또는 *myribbon.vb* 코드 파일에서 생성 된 `addButtonCheckBox_Click` 및 `addRichTextCheckBox_Click` 이벤트 처리기를 다음 코드로 바꿉니다. 이 코드는 이 연습의 앞부분에서 `ToggleButtonOnDocument` 클래스에 추가한 `ToggleRichTextControlOnDocument` 및 `ThisAddIn` 메서드를 호출하도록 이벤트 처리기를 다시 정의합니다.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]

## <a name="test-the-solution"></a>솔루션 테스트
 리본의 사용자 지정 탭에서 선택하여 문서에 컨트롤을 추가합니다. 문서를 저장하면 <xref:Microsoft.Office.Tools.Word.Controls.Button> 컨트롤이 제거됩니다.

### <a name="to-test-the-solution"></a>솔루션을 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 활성 문서에서 **enter** 키를 여러 번 눌러 문서에 비어 있는 새 단락을 추가 합니다.

3. 첫 번째 단락을 선택합니다.

4. **추가 기능** 탭을 클릭합니다.

5. **컨트롤 추가** 그룹에서 **단추 추가**를 클릭합니다.

     첫 번째 단락에 단추가 나타납니다.

6. 마지막 단락을 선택합니다.

7. **컨트롤 추가** 그룹에서 **서식 있는 텍스트 컨트롤 추가**를 클릭합니다.

     서식 있는 텍스트 콘텐츠 컨트롤이 마지막 단락에 추가됩니다.

8. 문서를 저장합니다.

     문서에서 단추가 제거됩니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서 VSTO 추가 기능의 컨트롤에 대해 자세히 알아볼 수 있습니다.

- 런타임에 다양 한 형식의 컨트롤을 문서에 추가 하 고 문서를 다시 열 때 컨트롤을 다시 만드는 방법을 보여 주는 샘플은 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)에서 Word 추가 기능 동적 컨트롤 샘플을 참조 하세요.

- Excel 용 VSTO 추가 기능을 사용 하 여 워크시트에 컨트롤을 추가 하는 방법을 보여 주는 연습은 [연습: 런타임에 vsto 추가 기능 프로젝트에서 워크시트에 컨트롤 추가](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Word 솔루션](../vsto/word-solutions.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office 문서에서 동적 컨트롤 유지](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [방법: Word 문서에 콘텐츠 컨트롤 추가](../vsto/how-to-add-content-controls-to-word-documents.md)
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
