---
title: Visual Studio에 대 한 글꼴 및 서식 Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd2e8a41ef4b9708df079e94bcac8b8c06189116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536112"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Visual Studio의 글꼴 및 서식 지정
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> 환경 글꼴
 사용자 지정을 위해 Visual Studio 내의 모든 글꼴을 사용자에 게 노출 해야 합니다. 이는 주로 **도구 > 옵션** 대화 상자의 **글꼴 및 색** 페이지를 통해 수행 됩니다. 글꼴 설정의 세 가지 주요 범주는 다음과 같습니다.

- **환경 글꼴** -대화 상자, 메뉴, 도구 창 및 문서 창을 포함 하 여 모든 인터페이스 요소에 사용 되는 IDE (통합 개발 환경)의 기본 글꼴입니다. 기본적으로 환경 글꼴은 현재 버전의 Windows에서 9 포인트 맑은 고딕로 표시 되는 시스템 글꼴에 연결 됩니다. 모든 인터페이스 요소에 대해 글꼴 하나를 사용 하면 IDE 전체에서 일관 된 글꼴 모양을 유지할 수 있습니다.

- **텍스트 편집기** -코드 및 기타 텍스트 기반 편집기에서 노출 하는 요소는 **도구 > 옵션**의 텍스트 편집기 페이지에서 사용자 지정할 수 있습니다.

- **특정 컬렉션** -해당 인터페이스 요소의 사용자 지정을 제공 하는 디자이너 창은 **도구 > 옵션**의 자체 설정 페이지에서 해당 디자인 화면에 특정 한 글꼴을 노출할 수 있습니다.

### <a name="editor-font-customization-and-resizing"></a>편집기 글꼴 사용자 지정 및 크기 조정
 사용자는 일반 사용자 인터페이스에 관계 없이 기본 설정에 따라 편집기에서 텍스트의 크기 및/또는 색을 확대 하거나 축소 하는 경우가 많습니다. 환경 글꼴은 편집기나 편집기/디자이너의 일부로 표시 될 수 있는 요소에 사용 되므로 이러한 글꼴 분류 중 하나가 변경 될 때 예상 되는 동작을 확인 하는 것이 중요 합니다.

 편집기에 표시 되지만 *콘텐츠의*일부가 아닌 UI 요소를 만드는 경우 요소를 예측 가능한 방식으로 크기 조정 하도록 텍스트 글꼴이 아니라 환경 글꼴을 사용 하는 것이 중요 합니다.

1. 편집기의 코드 텍스트에 대해 코드 텍스트 글꼴 설정으로 크기를 조정 하 고 편집기 텍스트의 확대/축소 수준에 응답 합니다.

2. 인터페이스의 다른 모든 요소는 환경 글꼴 설정에 연결 되 고 환경의 모든 전역 변경 내용에 응답 해야 합니다. 여기에는 다음이 포함되지만 이에 제한되지 않습니다.

    - 상황에 맞는 메뉴의 텍스트

    - 전구 메뉴 텍스트, 빠른 편집기 창 및 탐색 창 같은 편집기 장식의 텍스트

    - **파일에서 찾기** 또는 **리팩터링** 과 같은 대화 상자의 레이블 텍스트

### <a name="accessing-the-environment-font"></a>환경 글꼴 액세스
 네이티브 또는 WinForms 코드에서 `IUIHostLocale::GetDialogFont` 서비스의 인터페이스를 쿼리 한 후 메서드를 호출 하 여 환경 글꼴에 액세스할 수 있습니다 `SID_SUIHostLocale` .

 Windows Presentation Foundation (WPF)의 경우 `DialogWindow` wpf의 클래스 대신 셸 클래스에서 대화 상자 창 클래스를 파생 시킵니다 `Window` .

 XAML에서 코드는 다음과 같습니다.

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

코드 뒤:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (를 `Microsoft.VisualStudio.Shell.11.0` 현재 버전의 MPF dll로 대체 합니다.)

 대화 상자를 표시 하려면 `ShowModal()` 클래스에서 ""를 호출 `ShowDialog()` 합니다. `ShowModal()` 셸에서 올바른 모달 상태를 설정 하 고, 대화 상자가 부모 창에서 가운데 맞춤 되도록 합니다.

 코드는 다음과 같습니다.

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` bool을 반환 하나요? (nullable 부울)를 사용 하 여 `DialogResult` 필요한 경우 사용할 수 있습니다. 대화 상자가 **정상**으로 닫히면 반환 값은 true입니다.

 `HwndSource`팝업 창이 나 Win32/WinForms 부모 창의 wpf 자식 창과 같이, 대화 상자가 아닌 다른 WPF UI를 표시 해야 하는 경우에는 `FontFamily` `FontSize` wpf 요소의 루트 요소에서 및를 설정 해야 합니다. (셸은 주 창에서 속성을 설정 하지만 이전에는 상속 되지 않습니다 `HWND` .) Shell은 다음과 같이 속성을 바인딩할 수 있는 리소스를 제공 합니다.

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> 서식 지정 (배율/굵은 글꼴) 참조
 일부 대화 상자에서는 특정 텍스트를 굵게 하거나 환경 글꼴 이외의 크기를 설정 해야 합니다. 이전에는 환경 글꼴 보다 큰 글꼴이 " `environment font +2` " 또는 이와 유사 하 게 코딩 되었습니다. 제공 된 코드 조각을 사용 하 여 높은 DPI 모니터를 지원 하 고 표시 텍스트가 항상 올바른 크기와 무게 (예: 빛 또는 좋아요)로 표시 되는지 확인 합니다.

> [!NOTE]
> 서식 지정을 적용 하기 전에 [텍스트 스타일](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)에 있는 지침을 충족 하는지 확인 합니다. * *

 환경 글꼴의 크기를 조정 하려면 TextBlock 또는 Label의 스타일을 표시 된 대로 설정 합니다. 올바르게 사용 되는 이러한 각 코드 조각에서는 적절 한 크기와 가중치 변형을 포함 하 여 올바른 글꼴을 생성 합니다.

 여기서 " `vsui` "는 네임 스페이스에 대 한 참조입니다 `Microsoft.VisualStudio.Shell` .

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% 환경 글꼴 + 라이트

34 pt 맑은 고딕 Light **로 표시 됩니다.**

::: moniker range="vs-2017"

시작 페이지에서와 같이 **사용:** (드문) 고유한 브랜드 UI

::: moniker-end

::: moniker range=">=vs-2019"

**사용:** (드문) 고유한 브랜드 UI

::: moniker-end

**절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 TextBlock 이며 `label` 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** 표시 된 대로 TextBlock 또는 Label의 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% 환경 글꼴 + 라이트
 다음과 **같이 표시 됩니다** . 28 Pt 맑은 고딕 소량 **사용:** 큰 시그니처 대화 제목, 보고서의 주 제목

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 TextBlock 이며 `label` 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** 표시 된 대로 TextBlock 또는 Label의 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% 환경 글꼴 + 기타
 18 pt 맑은 고딕 사용 하는 경우 **:** 부제목, 작은 및 보통 대화 상자의 제목 **으로 표시 됩니다** .

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 TextBlock 이며 `label` 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% 환경 글꼴
 다음과 **같이 표시 됩니다** . 14 Pt 맑은 고딕 **사용:** 문서 웰 UI 또는 보고서의 섹션 제목

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 TextBlock 이며 `label` 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% 환경 글꼴
 다음 **으로 표시:** 12 Pt 맑은 고딕 **사용:** 서명 대화 상자와 문서 웰 UI의 작은 부제목

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 TextBlock 이며 `label` 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% 환경 글꼴
 **는** 11 Pt 맑은 고딕 사용: [서명 대화 상자, 트리 뷰의 최상위 노드, 세로 탭 탐색] **에 사용** 됩니다.

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 TextBlock 이며 `label` 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>환경 글꼴 + 굵게
 서명 대화 상자, 보고서 및 문서 웰 UI의 레이블 및 부제를 사용 하는 경우 굵게 표시 된 9 포인트 맑은 고딕 **에 사용** **됩니다.**

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 TextBlock 이며 `label` 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>지역화할 수 있는 스타일
 일부 경우에는 지역화 담당자가 동아시아 언어의 텍스트에서 굵은 글꼴을 제거 하는 등의 여러 로캘에 대 한 글꼴 스타일을 수정 해야 합니다. 글꼴 스타일의 지역화를 가능 하 게 하려면 해당 스타일이 .resx 파일 내에 있어야 합니다. Visual Studio 폼 디자이너에서이를 수행 하는 가장 좋은 방법은 디자인 타임에 글꼴 스타일을 명시적으로 설정 하는 것입니다. 이는 전체 글꼴 개체를 만들지만 부모 글꼴의 상속을 중단 하는 것 처럼 보일 수 있지만 글꼴을 설정 하는 데는 FontStyle 속성만 사용 됩니다.

 이 솔루션은 대화 상자의 이벤트를 연결 하는 것입니다 `FontChanged` . 이벤트에서 `FontChanged` 모든 컨트롤을 탐색 하 고 해당 글꼴이 설정 되었는지 확인 합니다. 설정 되어 있으면 폼의 글꼴 및 컨트롤의 이전 글꼴 스타일에 따라 새 글꼴로 변경 합니다. 코드의 예제는 다음과 같습니다.

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 이 코드를 사용 하면 폼의 글꼴이 업데이트 될 때 컨트롤의 글꼴도 업데이트 됩니다. 이 메서드는 폼의 생성자에서 호출 해야 합니다. 대화 상자에서의 인스턴스를 가져오지 못해 이벤트가 발생 하지 않을 수 있기 때문 `IUIService` `FontChanged` 입니다. `FontChanged`대화 상자가 이미 열려 있는 경우에는 후크를 통해 대화 상자에서 새 글꼴을 동적으로 선택할 수 있습니다.

### <a name="testing-the-environment-font"></a>환경 글꼴 테스트
 UI가 환경 글꼴을 사용 하 고 크기 설정에 맞는지 확인 하려면 **도구 > 옵션 > 환경 > 글꼴 및 색** 을 열고 "설정 표시:" 드롭다운 메뉴에서 "환경 글꼴"을 선택 합니다.

 ![도구 옵션 대화 상자의 글꼴 및 색 설정 &gt;](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />도구 옵션 대화 상자의 글꼴 및 색 설정 &gt;

 글꼴을 기본값과 다른 것으로 설정 합니다. 업데이트 되지 않는 UI를 명확 하 게 하려면 세리프 (예: "Times New Roman")을 사용 하 여 글꼴을 선택 하 고 매우 큰 크기를 설정 합니다. 그런 다음 UI를 테스트 하 여 환경을 작동 하는지 확인 합니다. 라이선스 대화 상자를 사용 하는 예제는 다음과 같습니다.

 ![환경 글꼴을 고려 하지 않는 UI 텍스트의 예](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />환경 글꼴을 고려 하지 않는 UI 텍스트의 예

 이 경우 "사용자 정보" 및 "제품 정보"는 글꼴을 사용할 수 없습니다. 경우에 따라 명시적인 디자인을 선택할 수 있지만 명시적 글꼴이 검토 사양의 일부로 지정 되지 않은 경우에는 버그가 될 수 있습니다.

 글꼴을 다시 설정 하려면 **도구 > 옵션 > 환경 > 글꼴 및 색**에서 "기본값 사용"을 클릭 합니다.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> 텍스트 스타일
 텍스트 스타일은 글꼴 크기, 무게 및 대/소문자를 나타냅니다. 구현 지침은 [환경 글꼴](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)을 참조 하세요.

### <a name="text-casing"></a>텍스트 대/소문자 구분

#### <a name="all-caps"></a>모든 대문자
 Visual Studio의 제목 또는 레이블에는 모두 대문자를 사용 하지 마세요.

#### <a name="all-lowercase"></a>모두 소문자
 Visual Studio에서 제목 또는 레이블에 대 한 모든 소문자를 사용 하지 마세요.

#### <a name="sentence-and-title-case"></a>문장 및 제목 대/소문자
 Visual Studio의 텍스트는 상황에 따라 제목 대/소문자 또는 문장의 대/소문자를 사용 해야 합니다.

|다음에 대 한 제목 사용 사례:|문장의 첫 글자를 사용 하는 경우:|
|-------------------------|----------------------------|
|대화 상자 제목|레이블|
|그룹 상자|확인란|
|메뉴 항목|라디오 단추|
|컨텍스트 메뉴 항목|목록 상자 항목|
|단추|상태 표시줄|
|테이블 레이블||
|열 머리글||
|도구 설명||

##### <a name="title-case"></a>단어의 첫 글자를 대문자로
 제목 대/소문자는 구에 포함 된 대부분 또는 모든 단어의 첫 글자를 대문자로 표기 하는 스타일입니다. Visual Studio에서 다음과 같은 여러 항목에 대 한 제목 사례가 사용 됩니다.

- **설명은.** 예: "선택한 항목 미리 보기"

- **열 머리글.** 예: "시스템 응답"

- **메뉴 항목입니다.** 예: "모두 저장"

  Title case를 사용 하는 경우 단어를 대문자로 하는 경우와 소문자를 그대로 두는 경우에 대 한 지침입니다.

|대문자|설명 및 예제|
|---------------|---------------------------|
|모든 명사||
|모든 동사|"Is" 및 다른 형태의 "to"를 포함 합니다.|
|모든 부사|"보다 큼" 및 "When" 포함|
|모든 형용사|"This" 및 "This"를 포함 합니다.|
|모든 대명사|Possessive "it" 및 "it"의 축약 대명사 "it", 동사 "is"를 포함 합니다.|
|음성 부분에 관계 없이 첫 번째 및 마지막 단어||
|동사 구의 일부인 전치사|"모든 Windows 종료" 또는 "시스템 종료"|
|머리글자어의 모든 문자|HTML, XML, URL, IDE, RGB|
|명사 또는 적절 한 형용사 인 경우 또는 단어의 가중치가 동일한 경우 복합 단어의 두 번째 단어|상호 참조, Microsoft 이전 소프트웨어, 읽기/쓰기 액세스, 런타임|

|소문자|예제|
|---------------|--------------|
|첫 번째 단어를 수정 하는 음성 또는 분사의 다른 부분인 복합 단어의 두 번째 단어|방법, 사용 안 함|
|문서 (제목에서 첫 번째 단어를 제외 하 고)|a, an, the|
|접속사 조정|및,의 경우, 또는|
|동사 구 외부에서 4 자 이하의 단어로 전치사|에서로,에서로, 그 위에|
|무한 구에 사용 되는 경우 "To"|"하드 디스크를 포맷 하는 방법"|

##### <a name="sentence-case"></a>문장 사례
 문장 사례는 문장의 첫 단어만 대문자 표시 되 고 적절 한 명사 및 대명사 "I"와 함께 사용 하는 표준 대문자 표시 메서드입니다. 일반적으로 대부분의 경우에는 컴퓨터에서 콘텐츠를 번역 하는 경우 전 세계 사용자가 쉽게 읽을 수 있습니다. 문장의 첫 글자를 사용 하는 경우:

1. **상태 표시줄 메시지입니다.** 이는 단순 하 고 간단한 상태 정보를 제공 합니다. 예: "프로젝트 파일 로드 중"

2. 레이블, 확인란, 라디오 단추 및 목록 상자 항목을 비롯 한 **다른 모든 UI 요소** 예: "목록에서 모든 항목 선택"

### <a name="text-formatting"></a>텍스트 서식 지정
 Visual Studio 2013의 기본 텍스트 서식은 [환경 글꼴](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)에 의해 제어 됩니다. 이 서비스를 사용 하면 IDE (통합 개발 환경) 전체에서 일관 된 글꼴 모양을 유지할 수 있으며 사용자에 게 일관 된 환경을 보장 하기 위해이 서비스를 사용 해야 합니다.

 Visual Studio 글꼴 서비스에서 사용 하는 기본 크기는 Windows에서 제공 되며, 9 포인트로 표시 됩니다.

 환경 글꼴에 서식을 적용할 수 있습니다. 이 항목에서는 스타일을 사용 하는 방법과 위치에 대해 설명 합니다. 구현 정보는 [환경 글꼴](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)을 참조 하세요.

#### <a name="bold-text"></a>굵은 텍스트
 굵은 텍스트는 Visual Studio에서 사용 되는 경우에만 사용 되며 다음을 위해 예약 되어야 합니다.

- 마법사의 질문 레이블

- 솔루션 탐색기에서 활성 프로젝트 지정

- 속성 도구 창의 재정의 된 값

- Visual Basic 편집기 드롭다운 목록의 특정 이벤트

- 웹 페이지에 대 한 문서 개요의 서버 생성 콘텐츠

- 복합 대화 상자 또는 디자이너 UI의 섹션 헤더

#### <a name="italics"></a>기울임꼴
 Visual Studio에서는 기울임꼴 또는 굵은 기울임꼴 텍스트를 사용 하지 않습니다.

#### <a name="color"></a>색상

- 파랑은 하이퍼링크 (탐색 및 명령) 용으로 예약 되어 있으며 방향에 사용 하면 안 됩니다.

- 더 큰 제목 (환경 글꼴 x 155% 이상)은 다음과 같은 목적으로 색을 지정할 수 있습니다.

  - Visual Studio UI 서명에 시각적 효과를 제공 하기 위해

  - 특정 영역에 주의를 걸려면

  - 표준 짙은 회색/검은색 환경 텍스트 색에서 릴리프를 제공 하려면

- 제목의 색은 기존 Visual Studio 브랜드 색 (주로 자주색, #FF68217A)을 활용 해야 합니다.

- 머리글에서 색을 사용 하는 경우에는 명암비와 기타 접근성 고려 사항을 포함 하 여 [Windows 색 지침](/windows/desktop/uxguide/vis-color)을 따라야 합니다.

### <a name="font-size"></a>글꼴 크기
 Visual Studio UI 디자인 기능을 사용 하면 더 많은 공백이 표시 됩니다. 가능 하면 chrome 및 제목 표시줄이 축소 되거나 제거 되었습니다. 정보 밀도는 Visual Studio에서 요구 되는 반면, 더 많은 줄 간격을 강조 하 고 글꼴 크기와 무게를 변형 하 여 입력 체계를 계속 중요 하 게 합니다.

 아래 표에서는 Visual Studio에서 사용 되는 디스플레이 글꼴의 디자인 세부 정보 및 시각적 예제를 제공 합니다. 일부 디스플레이 글꼴 변형에는 사용자 또는 조명 등의 크기와 가중치가 모두 표시 됩니다.

 모든 디스플레이 글꼴의 구현 코드 조각은 [서식 (배율/굵은 글꼴) 참조](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)에서 찾을 수 있습니다.

#### <a name="375-environment-font--light"></a>375% 환경 글꼴 + 라이트

|사용량|모양|
|-|-|
|**사용:** 하지만. 고유한 브랜드 UI만 해당 합니다.<br /><br /> **시겠습니까**<br /><br /> -문장 사례 사용<br />-항상 경량 가중치 사용<br /><br /> **안 함:**<br /><br /> -시작 페이지와 같은 서명 UI 이외의 UI 사용<br />-굵게, 기울임꼴 또는 굵은 기울임꼴<br />-본문 텍스트에 사용<br />-도구 창에서 사용|34 pt 맑은 고딕 Light **로 표시 됩니다.**<br /><br /> **시각적 예제:**<br /><br /> *현재 사용 되지 않습니다. Visual Studio 2017 시작 페이지에서 사용할 수 있습니다.*|

#### <a name="310-environment-font--light"></a>310% 환경 글꼴 + 라이트

::: moniker range="vs-2017"

|사용량|모양|
|-|-|
|**사용법:**<br /><br /> -서명 대화 상자에서 더 큰 제목<br />-주 보고서 머리글<br /><br /> **시겠습니까**<br /><br /> -문장 사례 사용<br />-항상 경량 가중치 사용<br /><br /> **안 함:**<br /><br /> -시작 페이지와 같은 서명 UI 이외의 UI 사용<br />-굵게, 기울임꼴 또는 굵은 기울임꼴<br />-본문 텍스트에 사용<br />-도구 창에서 사용|**다음과 같이 표시 됩니다.** 28pt 맑은 고딕 Light<br /><br /> **시각적 예제:**<br /><br /> ![310% 환경 글꼴 &#43; 밝은 제목의 예](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|사용량|모양|
|-|-|
|**사용법:**<br /><br /> -서명 대화 상자에서 더 큰 제목<br />-주 보고서 머리글<br /><br /> **시겠습니까**<br /><br /> -문장 사례 사용<br />-항상 경량 가중치 사용<br /><br /> **안 함:**<br /><br /> -서명 UI 이외의 UI를 사용 합니다.<br />-굵게, 기울임꼴 또는 굵은 기울임꼴<br />-본문 텍스트에 사용<br />-도구 창에서 사용|**다음과 같이 표시 됩니다.** 28pt 맑은 고딕 Light<br /><br /> **시각적 예제:**<br /><br /> ![310% 환경 글꼴 &#43; 밝은 제목의 예](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% 환경 글꼴 + 기타

|사용량|모양|
|-|-|
|**사용법:**<br /><br /> -부제목<br />-작은 및 보통 대화 상자의 제목<br /><br /> **시겠습니까**<br /><br /> -문장 사례 사용<br />-항상 사용 가중치를 사용 합니다.<br /><br /> **안 함:**<br /><br /> -굵게, 기울임꼴 또는 굵은 기울임꼴<br />-본문 텍스트에 사용<br />-도구 창에서 사용|18 pt 맑은 고딕 Semillight **로 표시 됩니다.**<br /><br /> **시각적 예제:**<br /><br /> ![200% 환경 글꼴 &#43;의 예](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% 환경 글꼴

|사용량|모양|
|-|-|
|**사용법:**<br /><br /> -문서 웰 UI의 섹션 제목<br />-보고서<br /><br /> **Do:** 문장 사례 사용<br /><br /> **안 함:**<br /><br /> -굵게, 기울임꼴 또는 굵은 기울임꼴<br />-본문 텍스트에 사용<br />-표준 Visual Studio 컨트롤에서 사용<br />-도구 창에서 사용|**다음과 같이 표시 됩니다.** 14 pt 맑은 고딕<br /><br /> **시각적 예제:**<br /><br /> ![155% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% 환경 글꼴

|사용량|모양|
|-|-|
|**사용법:**<br /><br /> -서명 대화 상자의 작은 부제목<br />-문서 웰 UI의 작은 부제목<br /><br /> **Do:** 문장 사례 사용<br /><br /> **안 함:**<br /><br /> -굵게, 기울임꼴 또는 굵은 기울임꼴<br />-본문 텍스트에 사용<br />-표준 Visual Studio 컨트롤에서 사용<br />-도구 창에서 사용|12 pt 맑은 고딕 **로 표시 됩니다.**<br /><br /> **시각적 예제:**<br /><br /> ![133% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% 환경 글꼴

|사용량|모양|
|-|-|
|**사용법:**<br /><br /> -서명 대화 상자의 섹션 제목<br />-트리 뷰의 최상위 노드<br />-세로 탭 탐색<br /><br /> **Do:** 문장 사례 사용<br /><br /> **안 함:**<br /><br /> -굵게, 기울임꼴 또는 굵은 기울임꼴<br />-본문 텍스트에 사용<br />-표준 Visual Studio 컨트롤에서 사용<br />-도구 창에서 사용|**다음과 같이 표시 됩니다.** 11pt 맑은 고딕<br /><br /> **시각적 예제:**<br /><br /> ![122% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>환경 글꼴 + 굵게

|사용량|모양|
|-|-|
|**사용법:**<br /><br /> -서명 대화 상자의 레이블 및 부제<br />-보고서의 레이블 및 부제<br />-문서 웰 UI의 레이블 및 부제<br /><br /> **시겠습니까**<br /><br /> -문장 사례 사용<br />-굵은 두께 사용<br /><br /> **안 함:**<br /><br /> -기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트에 사용<br />-표준 Visual Studio 컨트롤에서 사용<br />-도구 창에서 사용|굵게 **표시 되는** 9 pt 맑은 고딕<br /><br /> **시각적 예제:**<br /><br /> ![환경 글꼴 &#43; 굵은 제목 예](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>환경 글꼴

|사용량|모양|
|-|-|
|**사용:** 기타 모든 텍스트<br /><br /> **Do:** 문장 사례 사용<br /><br /> **안 함:** 기울임꼴 또는 굵게 기울임꼴|**다음과 같이 표시 됩니다.** 9 pt 맑은 고딕<br /><br /> **시각적 예제:**<br /><br /> ![환경 글꼴의 예](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>안쪽 여백 및 간격
 제목에는 적절 한 강조를 제공 하기 위해 주위의 공간이 필요 합니다. 이 공간은 포인트 크기 및 환경 글꼴의 가로 구분선 또는 텍스트 줄과 같이 머리글 근처의 다른 항목에 따라 달라 집니다.

- 제목의 이상적인 안쪽 여백은 대문자 문자 높이 공간의 90% 여야 합니다. 예를 들어 28 pt 맑은 고딕 밝은 제목에는 캡 높이가 26 pt이 고 안쪽 여백은 약 23 pt 또는 약 31 픽셀 이어야 합니다.

- 머리글 주위의 최소 공간은 대문자 높이의 50% 여야 합니다. 제목이 규칙이 나 기타 엄격한 맞춤 요소와 함께 제공 되는 경우 더 작은 공간을 사용할 수 있습니다.

- 굵게 표시 되는 환경 글꼴 텍스트는 기본 선 높이 간격과 안쪽 여백을 따라야 합니다.

## <a name="see-also"></a>추가 정보

- [글꼴 (Windows)](/windows/desktop/uxguide/vis-fonts)
- [사용자 인터페이스 텍스트 (Windows)](/windows/desktop/uxguide/text-ui)
