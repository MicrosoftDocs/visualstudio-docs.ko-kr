---
title: 단추를 사용 하 여 문서의 텍스트 상자에 텍스트 표시
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f3c467abcee8fb4faafd2da06ba261e7f3039fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328749"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>연습: 문서에서 단추를 사용 하 여 텍스트 상자에 텍스트 표시
  이 연습에서는 Microsoft Office Word에 대한 문서 수준 사용자 지정에서 단추 및 텍스트 상자를 사용하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 디자인 타임에 문서 수준 프로젝트의 Word 문서에 컨트롤 추가

- 단추를 클릭할 때 텍스트 상자 채우기

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 첫 번째 단계에서는 Word 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름 **내 Word 단추**를 사용 하 여 word 문서 프로젝트를 만듭니다. 마법사에서 **새 문서 만들기**를 선택 합니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

     Visual Studio가 디자이너에서 새 Word 문서를 열고 **솔루션 탐색기**에 **word 단추** 프로젝트를 추가 합니다.

## <a name="add-controls-to-the-word-document"></a>Word 문서에 컨트롤 추가
 Word 문서의 사용자 인터페이스 컨트롤은 단추와 텍스트 상자로 구성됩니다.

### <a name="to-add-a-button-and-a-text-box"></a>단추 및 텍스트 상자를 추가하려면

1. Visual Studio 디자이너에서 문서가 열려 있는지 확인합니다.

2. **도구 상자**의 **공용 컨트롤** 탭에서 컨트롤을 문서로 끌어 옵니다 <xref:Microsoft.Office.Tools.Word.Controls.TextBox> .

   > [!NOTE]
   > Word에서는 기본적으로 컨트롤이 텍스트와 인라인으로 놓입니다. Word의 **옵션** 대화 상자에 있는 **편집** 탭에서 기본값을 변경 하 여 컨트롤 및 모양 개체를 삽입 하는 방법을 수정할 수 있습니다.

3. **보기** 메뉴에서 **속성 창**을 클릭합니다.

4. **속성** 창 드롭다운 상자에서 **TextBox1** 을 찾아 텍스트 상자의 **이름** 속성을 **인 displaytext**로 변경 합니다.

5. **단추** 컨트롤을 문서로 끌고 다음 속성을 변경 합니다.

   |속성|값|
   |--------------|-----------|
   |**이름**|**insertText**|
   |**Text**|**텍스트 삽입**|

   이제 단추를 클릭할 때 실행되는 코드를 작성할 수 있습니다.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>단추를 클릭할 때 텍스트 상자 채우기
 사용자가 단추를 클릭할 때마다 **Hello World!** 가 텍스트 상자에 추가 됩니다.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>단추를 클릭할 때 텍스트 상자에 쓰려면

1. **솔루션 탐색기**에서 **ThisDocument**를 마우스 오른쪽 단추로 클릭 한 다음 바로 가기 메뉴에서 **코드 보기** 를 클릭 합니다.

2. 단추의 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기에 다음 코드를 추가합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. C#에서는 단추에 대한 이벤트 처리기를 <xref:Microsoft.Office.Tools.Word.Document.Startup> 이벤트에 추가해야 합니다. 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)를 참조 하세요.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 문서를 테스트 하 여 메시지 Hello World 수 있는지 확인할 수 있습니다 **.** 단추를 클릭 하면 텍스트 상자에 나타납니다.

### <a name="to-test-your-document"></a>문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. 이 단추를 클릭합니다.

3. Hello World 되었는지 확인 **하세요.** 텍스트 상자에 나타납니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 Word 문서에서 단추 및 텍스트 상자를 사용하는 기본 사항을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 콤보 상자를 사용하여 서식 변경. 자세한 내용은 [연습: CheckBox 컨트롤을 사용 하 여 문서 서식 변경](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)을 참조 하세요.

- 라디오 단추를 사용하여 차트 스타일 선택. 자세한 내용은 [연습: 문서에서 라디오 단추를 사용 하 여 차트 업데이트](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Office 문서에 대 한 Windows Forms 컨트롤 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Word를 사용한 연습](../vsto/walkthroughs-using-word.md)
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)
- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
