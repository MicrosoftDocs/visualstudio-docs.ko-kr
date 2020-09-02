---
title: CheckBox 컨트롤을 사용 하 여 문서 서식 변경
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24c3cb8d76551bb477f9c13cc56c313519f3b617
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328720"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>연습: CheckBox 컨트롤을 사용 하 여 문서 서식 변경
  이 연습에서는 Microsoft Office Word에 대 한 문서 수준 사용자 지정에서 Windows Forms 컨트롤을 사용 하 여 텍스트 서식을 변경 하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 디자인 타임에 문서 수준 프로젝트의 문서에 텍스트 및 컨트롤 추가

- 옵션을 선택 하는 경우 텍스트의 서식을 지정 합니다.

  결과를 완료 된 샘플로 보려면 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)에서 Word 컨트롤 샘플을 참조 하세요.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 첫 번째 단계에서는 Word 문서 프로젝트를 만듭니다.

### <a name="create-a-new-project"></a>새 프로젝트 만들기

1. Word **서식**이라는 이름의 word 문서 프로젝트를 만듭니다. 마법사에서 **새 문서 만들기**를 선택 합니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio가 디자이너에서 새 Word 문서를 열고 **내 Word 서식 지정** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

## <a name="add-text-and-controls-to-the-word-document"></a>Word 문서에 텍스트 및 컨트롤 추가
 이 연습에서는 컨트롤의 세 가지 확인란 및 일부 텍스트를 <xref:Microsoft.Office.Tools.Word.Bookmark> Word 문서에 추가 합니다. 확인란은 텍스트의 서식을 지정 하는 옵션을 사용자에 게 제공 합니다.

### <a name="add-three-check-boxes"></a>확인란 세 개 추가

1. Visual Studio 디자이너에서 문서가 열려 있는지 확인합니다.

2. **도구 상자**의 **공용 컨트롤** 탭에서 첫 번째 컨트롤을 문서로 끌어 옵니다 <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> .

3. **속성** 창에서 다음 속성을 변경합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyBoldFont**|
    |**Text**|**굵게**|

4. **Enter** 키를 눌러 삽입 지점을 첫 번째 확인란 아래로 이동 합니다.

5. 확인란 아래의 문서에 두 번째 확인란을 추가 하 `ApplyBoldFont` 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyItalicFont**|
    |**Text**|**기울임꼴**|

6. **Enter** 키를 눌러 삽입 지점을 두 번째 확인란 아래로 이동 합니다.

7. 문서에서 확인란 아래의 세 번째 확인란을 추가 하 `ApplyItalicFont` 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyUnderlineFont**|
    |**Text**|**바뀝니다**|

### <a name="add-text-and-a-bookmark-control"></a>텍스트 및 책갈피 컨트롤 추가

1. 확인란 컨트롤 아래로 삽입 지점을 이동 하 고 다음 텍스트를 입력 합니다.

    **이 텍스트의 서식을 변경 하려면 확인란을 클릭 합니다.**

2. **도구 상자**의 **Word 컨트롤** 탭에서 컨트롤을 문서로 끌어 옵니다 <xref:Microsoft.Office.Tools.Word.Bookmark> .

    **책갈피 컨트롤 추가** 대화 상자가 나타납니다.

3. 문서에 추가한 텍스트를 선택 하 고 **확인**을 클릭 합니다.

    <xref:Microsoft.Office.Tools.Word.Bookmark> **않고 책갈피 2** 라는 컨트롤이 문서의 선택한 텍스트에 추가 됩니다.

4. **속성** 창에서 **(이름)** 속성의 값을 **글꼴 텍스트** 로 변경 합니다.

   그런 다음 확인란을 선택 하거나 선택 취소 하는 경우 텍스트의 서식을 지정 하는 코드를 작성 합니다.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>확인란을 선택 하거나 선택 취소 하는 경우 텍스트 서식 지정
 사용자가 서식 옵션을 선택 하는 경우 문서에서 텍스트의 형식을 변경 합니다.

### <a name="change-formatting-when-a-check-box-is-selected"></a>확인란이 선택 된 경우 서식 변경

1. 솔루션 탐색기를 마우스 오른쪽 단추로 클릭 한 `ThisDocument` 다음 바로 가기 메뉴에서 **코드 보기** 를 클릭 합니다. **Solution Explorer**

2. C #의 경우 **ThisDocument** 클래스에 다음 상수를 추가 합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. 확인란의 이벤트 처리기에 다음 코드를 추가 <xref:System.Windows.Forms.Control.Click> `applyBoldFont` 합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. 확인란의 이벤트 처리기에 다음 코드를 추가 <xref:System.Windows.Forms.Control.Click> `applyItalicFont` 합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. 확인란의 이벤트 처리기에 다음 코드를 추가 <xref:System.Windows.Forms.Control.Click> `applyUnderlineFont` 합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. C #에서는 텍스트 상자에 대 한 이벤트 처리기를 이벤트에 추가 해야 합니다 <xref:Microsoft.Office.Tools.Word.Document.Startup> . 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 확인란을 선택 하거나 선택 취소 하면 문서를 테스트 하 여 텍스트 형식이 올바르게 지정 되었는지 확인할 수 있습니다.

### <a name="test-your-document"></a>문서 테스트

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 확인란을 선택하거나 선택을 취소합니다.

3. 텍스트의 형식이 올바르게 지정 되었는지 확인 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 Word 문서에서 확인란을 사용 하 고 프로그래밍 방식으로 텍스트 서식을 변경 하는 기본적인 방법을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 단추를 사용 하 여 텍스트 상자를 채웁니다. 자세한 내용은 [연습: 문서에서 단추를 사용 하 여 텍스트 상자에 텍스트 표시](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)를 참조 하세요.

- 라디오 단추를 사용하여 차트 스타일 선택. 자세한 내용은 [연습: 문서에서 라디오 단추를 사용 하 여 차트 업데이트](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Word를 사용한 연습](../vsto/walkthroughs-using-word.md)
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 문서에서 Windows Forms 컨트롤의 제한 사항](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
