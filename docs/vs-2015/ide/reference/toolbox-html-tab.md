---
title: 도구 상자, HTML 탭 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4474f2a0823b5599da30706daedff6e5cd1fc0f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851656"
---
# <a name="toolbox-html-tab"></a>도구 상자, HTML 탭
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

도구 상자의 **HTML** 탭에서는 웹 페이지와 Web Forms에서 유용한 구성 요소를 제공합니다. 이 탭을 보려면 먼저 HTML 디자이너에서 편집할 문서를 엽니다. **보기** 메뉴에서 **도구 상자**를 클릭하고 도구 상자의 **HTML** 탭을 클릭합니다.

 **HTML** 탭에서 도구 인스턴스를 만들려면 도구를 두 번 클릭하여 현재 삽입 지점에 있는 문서에 추가하거나 도구를 선택하고 편집 화면의 원하는 위치로 끌어다 놓습니다.

## <a name="tasks"></a>작업

- [방법: 도구 상자 창 관리](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)

- [방법: 도구 상자 탭 조작](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)

## <a name="ui-elements"></a>UI 요소
 다음 도구는 [HTML] 탭에서 기본적으로 사용할 수 있습니다.

 **포인터** ![ASP.NET 모바일 디자이너 HTMLpage 포인터](../../ide/reference/media/vxpointer.gif "vxPointer")

 [도구 상자] 탭이 열리면 이 도구가 기본적으로 선택됩니다. 이 도구는 삭제할 수 없습니다. 포인터를 사용하여 개체를 디자인 보기 화면에 끌어다 놓고, 크기를 조정하고, 페이지 또는 양식에서 위치를 변경합니다. 자세한 내용은 [방법: 도구 상자 창 관리](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) 및 [방법: 도구 상자 탭 조작](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)을 참조하세요.

 **입력 (단추)** ![HTML 웹 페이지 단추](../../ide/reference/media/vxbutton.gif "vxButton")

 `type="button"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Button1"`은 첫 번째 단추로 삽입되고, `id="Button2"`는 두 번째 단추로 삽입되는 식으로 항목이 삽입됩니다.

 **Input (Button)** 를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<input id="Button1" type="button" value="Button" name="Button1">
```

 자세한 내용은 [HTML Input 컨트롤](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputButton 서버 컨트롤 선언 구문](https://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: How to: Create Scripts and Edit Event Handlers](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d)(NIB: 방법: 스크립트 만들기 및 이벤트 처리기 편집), [Button Web Server Controls Content Map](https://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf)(Button 웹 서버 컨트롤 콘텐츠 맵), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> 및 <xref:System.Web.UI.WebControls.Button>을 참조하세요.

 **입력 (다시 설정)** ![htmlpageresetbutton 스크린 샷](../../ide/reference/media/vxreset.gif "vxReset")

 `type="reset"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Reset1"`은 첫 번째 다시 설정 단추로 삽입되고, `id="Reset2"`는 두 번째 다시 설정 단추로 삽입되는 식으로 항목이 삽입됩니다.

 **Input (Reset)** 를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

 자세한 내용은 [HTML Input 컨트롤](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputReset 서버 컨트롤 선언 구문](https://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> 및 <xref:System.Web.UI.WebControls.Button>을 참조하세요.

 **입력 (제출)** ![htmlpagetool바 submitbutton 스크린 샷](../../ide/reference/media/vxsubmit.gif "vxSubmit")

 `type="submit"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Submit1"`은 첫 번째 제출 단추로 삽입되고, `id="Submit2"`는 두 번째 제출 단추로 삽입되는 식으로 항목이 삽입됩니다.

 **Input (Submit)** 를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

 자세한 내용은 [HTML Input 컨트롤](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputSubmit 서버 컨트롤 선언 구문](https://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> 및 <xref:System.Web.UI.WebControls.Button>을 참조하세요.

 **입력 (텍스트)** ![HTMLpageToolbarTextField 스크린 샷](../../ide/reference/media/vxtextfield.gif "vxTextfield")

 `type="text"`의 `input` 요소를 문서에 삽입합니다. 표시되는 기본 텍스트를 변경하려면 `value` 특성을 편집합니다. 기본적으로 `id="Text1"`은 첫 번째 텍스트 필드로 삽입되고, `id="Text2"`는 두 번째 텍스트 필드로 삽입되는 식으로 항목이 삽입됩니다.

 **Input (Text)** 를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

 자세한 내용은 [HTML Input 컨트롤](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputText 서버 컨트롤 선언 구문](https://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [TextBox 웹 서버 컨트롤 개요](https://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText> 및 <xref:System.Web.UI.WebControls.TextBox>을 참조하세요.

> [!IMPORTANT]
> 모든 사용자 입력의 유효성을 검사하는 것이 좋습니다. 자세한 내용은 [ASP.NET 웹 페이지에서 사용자 입력 유효성 검사](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)를 참조하세요.

 **입력 (파일)** ![HTML 페이지 파일 필드](../../ide/reference/media/vxfilefield.gif "vxFilefield")

 `type="file"`의 `input` 요소를 문서에 삽입합니다. 기본적으로 `id="File1"`은 첫 번째 파일 필드로 삽입되고, `id="File2"`는 두 번째 파일 필드로 삽입되는 식으로 항목이 삽입됩니다.

 **Input (File)** 를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<input id="File1" type="file" name="File1">
```

 자세한 내용은 [HTML Input 컨트롤](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputFile 서버 컨트롤 선언 구문](https://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6) 및 <xref:System.Web.UI.HtmlControls.HtmlInputFile>을 참조하세요.

> [!IMPORTANT]
> 모든 사용자 입력의 유효성을 검사하는 것이 좋습니다. 자세한 내용은 [ASP.NET 웹 페이지에서 사용자 입력 유효성 검사](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)를 참조하세요.

 **입력 (암호)** ![Visual Studio 암호 필드](../../ide/reference/media/vxpassword.gif "vxPassword")

 `type="password"`의 `input` 요소를 삽입합니다. 기본적으로 `id="Password1"`은 첫 번째 암호 필드로 삽입되고, `id="Password2"`는 두 번째 암호 필드로 삽입되는 식으로 항목이 삽입됩니다.

 **Input (Password)** 를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<input id="Password1" type="password" name="Password1">
```

 자세한 내용은 [HTML Input 컨트롤](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputPassword 서버 컨트롤 선언 구문](https://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [방법: 암호 입력란으로 TextBox 웹 서버 컨트롤 설정](https://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310) 및 [연습: Web Forms 페이지에서 사용자 입력 유효성 검사](https://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436)를 참조하세요.

> [!IMPORTANT]
> 애플리케이션에서 사용자 이름과 암호를 전송할 경우 SSL(Secure Sockets Layer)을 사용하여 전송을 암호화하도록 웹 사이트를 구성해야 합니다. 자세한 내용은 [IIS Operations Guide](https://technet.microsoft.com/library/cc732976(v=WS.10).aspx)(IIS 작업 가이드)에서 "Securing Connections with SSL(SSL을 사용하여 연결 보호)"을 참조하세요. 또한 모든 사용자 입력의 유효성을 검사하는 것이 좋습니다. 자세한 내용은 [ASP.NET 웹 페이지에서 사용자 입력 유효성 검사](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)를 참조하세요.

 **입력 (확인란)** ![HTML 웹 페이지 도구 상자 확인란 옵션](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")

 `type="checkbox"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Checkbox1"`은 첫 번째 확인란으로 삽입되고, `id="Checkbox2"`는 두 번째 확인란으로 삽입되는 식으로 항목이 삽입됩니다.

 **Input (Check box)** 를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

 자세한 내용은 [HTML Input 컨트롤](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputCheckBox 서버 컨트롤 선언 구문](https://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [CheckBox 및 CheckBoxList 웹 서버 컨트롤 개요](https://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> 및 <xref:System.Web.UI.WebControls.CheckBox>를 참조하세요.

 **입력 (라디오)** ![VisualStudioHTMLpageRadioButton 스크린 샷](../../ide/reference/media/vxradio.gif "vxRadio")

 `type="radio"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Radio1"`은 첫 번째 라디오 단추로 삽입되고, `id="Radio2"`는 두 번째 라디오 단추로 삽입되는 식으로 항목이 삽입됩니다.

 **Input (Radio)** 를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<input id="Radio1" type="radio" name="Radio1">
```

 자세한 내용은 [HTML Input 컨트롤](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputRadioButton 서버 컨트롤 선언 구문](https://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton 및 RadioButtonList 웹 서버 컨트롤 개요](https://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> 및 <xref:System.Web.UI.WebControls.RadioButton>을 참조하세요.

 **입력 (숨김)** ![HTML 페이지 숨겨진 항목](../../ide/reference/media/vxhidden.gif "vxhidden")

 `type="hidden"`의 `input` 요소를 삽입합니다. 기본적으로 `id="Hidden1"`은 첫 번째 숨겨진 필드로 삽입되고, `id="Hidden2"`는 두 번째 숨겨진 필드로 삽입되는 식으로 항목이 삽입됩니다.

 **Input (Hidden)** 를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<input id="Hidden1" type="hidden" name="Hidden1">
```

 자세한 내용은 [HTML Input 컨트롤](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputHidden 서버 컨트롤 선언 구문](https://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) 및 <xref:System.Web.UI.HtmlControls.HtmlInputHidden>을 참조하세요.

 **Textarea** ![HTMLpage 도구 모음 텍스트 영역](../../ide/reference/media/vxtextarea.gif "vxTextarea")

 `textarea` 요소를 삽입합니다. 텍스트 영역의 크기를 조정하거나, 스크롤 막대를 사용하여 표시 영역을 벗어나는 텍스트를 볼 수 있습니다. 표시되는 기본 텍스트를 변경하려면 `value` 특성을 편집합니다. 기본적으로 `id="textarea1"`은 첫 번째 텍스트 영역으로 삽입되고, `id=" textarea 2"`는 두 번째 텍스트 영역으로 삽입되는 식으로 항목이 삽입됩니다.

 **Textarea**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

 자세한 내용은 [Htmltextarea 서버 컨트롤 선언 구문](https://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), 및을 참조 하세요 <xref:System.Web.UI.HtmlControls.HtmlTextArea> <xref:System.Web.UI.WebControls.TextBox> .

> [!IMPORTANT]
> 모든 사용자 입력의 유효성을 검사하는 것이 좋습니다. 자세한 내용은 [ASP.NET 웹 페이지에서 사용자 입력 유효성 검사](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)를 참조하세요.

 **테이블** ![htmlpagetool바 표 스크린샷](../../ide/reference/media/vxtable.gif "vxTable")

 `table` 요소를 삽입합니다.

 **Table**을 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

 자세한 내용은 [HtmlTable 서버 컨트롤 선언 구문](https://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Table, TableRow 및 TableCell 웹 서버 컨트롤 개요](https://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable> 및 <xref:System.Web.UI.WebControls.Table>을 참조하세요.

 **이미지** ![HTML 페이지 이미지 항목](../../ide/reference/media/vximage.gif "vxImage")

 `img` 요소를 삽입합니다. 이 요소를 편집하여 해당 `src` 및 `alt` 텍스트를 지정합니다.

 **Image**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<img alt="" src="">
```

 자세한 내용은 [HtmlImage 서버 컨트롤 선언 구문](https://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [이미지 웹 서버 컨트롤 개요](https://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9),, 및를 참조 하세요 <xref:System.Web.UI.HtmlControls.HtmlImage> <xref:System.Web.UI.HtmlControls.HtmlInputImage> <xref:System.Web.UI.WebControls.Image> .

 **Select** ![HTML 페이지 도구 상자 드롭다운](../../ide/reference/media/vxdropdown.gif "vxDropdown") 선택

 `select` 요소를 삽입합니다(`size` 특성 없음). 기본적으로 `id="select1"`은 첫 번째 목록 상자로 삽입되고, `id="select2"`는 두 번째 목록 상자로 삽입되는 식으로 항목이 삽입됩니다.

 **Select**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<select id="select1" name="select1"><option selected></option></select>
```

 size 속성 값을 늘려 여러 줄 `select` 요소를 만들 수 있습니다.

 자세한 내용은 [HtmlSelect 서버 컨트롤 선언 구문](https://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: How to: Create Scripts and Edit Event Handlers](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d)(NIB: 방법: 스크립트 만들기 및 이벤트 처리기 편집), [DropDownList Web Server Control Overview](https://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608)(DropDownList 웹 서버 컨트롤 개요), [ListBox Web Server Control Overview](https://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97)(ListBox 웹 서버 컨트롤 개요), <xref:System.Web.UI.HtmlControls.HtmlSelect> 및 <xref:System.Web.UI.WebControls.DropDownList>를 참조하세요.

 **수평선** ![HTML 페이지 수평선 규칙 항목](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")

 `hr` 요소를 삽입합니다. 줄 두께를 늘리려면 `size` 특성을 편집합니다.

 **Horizontal Rule**을 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<hr width="100%" size=1>
```

 자세한 내용은 [HTML Horizontal Rule 컨트롤](https://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f)을 참조하세요.

 **Div** ![HTML 페이지 레이블](../../ide/reference/media/vxlabel.gif "vxLabel")

 `ms_positioning="FlowLayout"` 특성을 포함하는 `div` 요소를 삽입합니다. 너비 및 높이를 제외하고 이 항목은 선형 레이아웃 패널과 동일합니다. `div` 요소 내에 포함된 텍스트의 서식을 지정하려면 `class="stylename"` 특성을 여는 태그에 추가합니다.

 **Div**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.

```
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

 자세한 내용은 [HTML Div 컨트롤](https://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Label 웹 서버 컨트롤 개요](https://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac) 및 <xref:System.Web.UI.WebControls.Label>을 참조하세요.

## <a name="see-also"></a>관련 항목
 [도구 상자](../../ide/reference/toolbox.md) [표준 탭, 도구 상자](https://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870) [HTML 컨트롤](https://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)
