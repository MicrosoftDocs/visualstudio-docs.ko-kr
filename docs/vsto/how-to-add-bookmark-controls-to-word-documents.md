---
title: '방법: Word 문서에 책갈피 컨트롤 추가'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de5868674790239b8374ef9796308280588ae96e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547253"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>방법: Word 문서에 책갈피 컨트롤 추가
  문서 수준 프로젝트에서 디자인 타임 또는 런타임에 프로젝트의 문서에 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 추가할 수 있습니다. VSTO 추가 기능 프로젝트에서는 런타임에 열려 있는 임의 문서에 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 추가할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 이 항목에서는 다음 작업에 대해 설명합니다.

- [디자인 타임에 책갈피 컨트롤 추가](#designtime)

- [런타임에 문서 수준 프로젝트에 책갈피 컨트롤 추가](#runtimedoclevel)

- [런타임에 VSTO 추가 기능 프로젝트에서 책갈피 컨트롤 추가](#runtimeaddin)

  컨트롤에 대 한 자세한 내용은 <xref:Microsoft.Office.Tools.Word.Bookmark> [책갈피 컨트롤](../vsto/bookmark-control.md)을 참조 하세요.

## <a name="add-bookmark-controls-at-design-time"></a><a name="designtime"></a>디자인 타임에 책갈피 컨트롤 추가
 디자인 타임에 문서 수준 프로젝트의 문서에 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 추가하는 여러 가지 방법이 있습니다.

- Visual Studio **도구 상자**에서.

   <xref:Microsoft.Office.Tools.Word.Bookmark> 도구 상자 **에서 문서로** 컨트롤을 끌어올 수 있습니다. 이미 **도구 상자** 를 사용하여 Windows Forms 컨트롤을 문서에 추가 중인 경우 이 방법을 선택하는 것이 좋습니다.

- Word 내에서.

   네이티브 책갈피를 추가하는 것과 동일한 방식으로 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 문서에 추가할 수 있습니다. 이런 방식으로 추가하는 경우 컨트롤을 만들 때 이름을 지정할 수 있다는 이점이 있습니다.

- **데이터 소스** 창에서.

   <xref:Microsoft.Office.Tools.Word.Bookmark> 데이터 소스 **창에서** 컨트롤을 문서로 끌어올 수 있습니다. 이 기능은 동시에 컨트롤을 데이터에 바인딩하려는 경우에 유용합니다. **데이터 소스** 창에서 Windows Form 컨트롤을 추가하는 것과 동일한 방법으로 호스트 컨트롤을 추가할 수 있습니다. 자세한 내용은 [데이터 바인딩 및 Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)을 참조 하세요.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>도구 상자에서 문서에 책갈피 컨트롤을 추가하려면

1. **도구 상자** 를 열고 **Word 컨트롤** 탭을 클릭합니다.

2. <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 문서로 끌어옵니다.

     **책갈피 추가** 대화 상자가 나타납니다.

3. 책갈피에 포함하려는 텍스트 또는 기타 항목을 선택합니다.

4. **확인**을 클릭합니다.

     기본 책갈피 이름을 유지하지 않으려면 **속성** 창에서 이름을 변경할 수 있습니다.

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Word에서 문서에 책갈피 컨트롤을 추가하려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디자이너에 호스트된 문서에서 책갈피를 추가하려는 위치에 커서를 놓거나 책갈피로 묶으려는 텍스트를 선택합니다.

2. 리본 메뉴의 **삽입** 탭에 있는 **링크** 그룹에서 **책갈피** 단추를 클릭합니다.

3. **책갈피** 대화 상자에서 새 책갈피의 이름을 입력하고 **추가**를 클릭합니다.

## <a name="add-bookmark-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a>런타임에 문서 수준 프로젝트에 책갈피 컨트롤 추가
 프로젝트에서 <xref:Microsoft.Office.Tools.Word.Bookmark> 클래스의 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 속성 메서드를 사용하여 프로그래밍 방식으로 런타임에 문서에 `ThisDocument` 컨트롤을 추가할 수 있습니다. 다음과 같은 방법으로 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 추가하는 데 사용할 수 있는 두 개의 메서드 오버로드가 있습니다.

- 지정된 범위에 <xref:Microsoft.Office.Tools.Word.Bookmark> 를 추가합니다.

- 문서의 네이티브 책갈피(즉, <xref:Microsoft.Office.Tools.Word.Bookmark> )를 기반으로 하는 <xref:Microsoft.Office.Interop.Word.Bookmark>를 추가합니다.

  동적으로 생성된 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤은 문서를 닫을 때 문서에 유지되지 않습니다. 그러나 네이티브 <xref:Microsoft.Office.Interop.Word.Bookmark> 는 문서에 남아 있습니다. 다음에 문서를 열 때 네이티브 책갈피를 기반으로 하는 <xref:Microsoft.Office.Tools.Word.Bookmark> 를 다시 만들 수 있습니다. 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)를 참조 하세요.

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>프로그래밍 방식으로 문서에 책갈피 컨트롤을 추가하려면

1. 프로젝트의 `ThisDocument_Startup` 이벤트 처리기에서 다음 코드를 삽입하여 문서의 첫 번째 단락에 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 추가합니다.

     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]

    > [!NOTE]
    > 기존 <xref:Microsoft.Office.Tools.Word.Bookmark> 에서 <xref:Microsoft.Office.Interop.Word.Bookmark>컨트롤을 만들려는 경우 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 메서드를 사용하고 기존 <xref:Microsoft.Office.Interop.Word.Bookmark>를 전달합니다.

## <a name="add-bookmark-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>런타임에 VSTO 추가 기능 프로젝트에서 책갈피 컨트롤 추가
 VSTO 추가 기능을 사용하여 프로그래밍 방식으로 런타임에 열려 있는 문서에 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 추가할 수 있습니다. 이렇게 하려면 열려 있는 문서를 기반으로 하는 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목을 생성한 다음 이 호스트 항목의 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 속성 메서드를 사용합니다. 다음과 같은 방법으로 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 추가하는 데 사용할 수 있는 두 개의 메서드 오버로드가 있습니다.

- 지정된 범위에 <xref:Microsoft.Office.Tools.Word.Bookmark> 를 추가합니다.

- 문서의 네이티브 책갈피(즉, <xref:Microsoft.Office.Tools.Word.Bookmark> )를 기반으로 하는 <xref:Microsoft.Office.Interop.Word.Bookmark>를 추가합니다.

  동적으로 생성된 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤은 문서를 닫을 때 문서에 유지되지 않습니다. 그러나 네이티브 <xref:Microsoft.Office.Interop.Word.Bookmark> 는 문서에 남아 있습니다. 다음에 문서를 열 때 네이티브 책갈피를 기반으로 하는 <xref:Microsoft.Office.Tools.Word.Bookmark> 를 다시 만들 수 있습니다. 자세한 내용은 [Office 문서에서 동적 컨트롤 유지](../vsto/persisting-dynamic-controls-in-office-documents.md)를 참조 하세요.

  VSTO 추가 기능 프로젝트에서 호스트 항목을 생성 하는 방법에 대 한 자세한 내용은 [런타임에 Vsto 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조 하세요.

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>지정된 범위에 책갈피 컨트롤을 추가하려면

1. <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 메서드를 사용하고 <xref:Microsoft.Office.Interop.Word.Range> 를 추가하려는 <xref:Microsoft.Office.Tools.Word.Bookmark>를 전달합니다.

     다음 코드 예제에서는 활성 문서의 시작 부분에 새 <xref:Microsoft.Office.Tools.Word.Bookmark> 를 추가합니다. 이 예제를 사용하려면 Word VSTO 추가 기능 프로젝트의 `ThisAddIn_Startup` 이벤트 처리기에서 코드를 실행합니다.

     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>네이티브 책갈피 컨트롤을 기반으로 하는 책갈피 컨트롤을 추가하려면

1. <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 메서드를 사용하고 새 <xref:Microsoft.Office.Interop.Word.Bookmark> 의 기초로 사용할 기존 <xref:Microsoft.Office.Tools.Word.Bookmark>를 전달합니다.

     다음 코드 예제에서는 활성 문서의 첫 번째 <xref:Microsoft.Office.Tools.Word.Bookmark> 를 기반으로 하는 새 <xref:Microsoft.Office.Interop.Word.Bookmark> 를 만듭니다. 이 예제를 사용하려면 Word VSTO 추가 기능 프로젝트의 `ThisAddIn_Startup` 이벤트 처리기에서 코드를 실행합니다.

     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]

## <a name="see-also"></a>참고 항목
- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [문서 수준 사용자 지정 프로그램](../vsto/programming-document-level-customizations.md)
- [방법: 책갈피 컨트롤 크기 조정](../vsto/how-to-resize-bookmark-controls.md)
