---
title: Visual Studio | 글꼴 및 서식 지정 Microsoft Docs
description: 환경 글꼴을 사용하는 방법을 포함하여 Visual Studio 위해 디자인하는 새로운 기능의 글꼴 및 서식 지정에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e6e26b18c838fc240d7fab398f8626890eed0d31
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901684"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Visual Studio의 글꼴 및 서식 지정
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> 환경 글꼴
 사용자 지정을 위해 Visual Studio 내의 모든 글꼴을 사용자에게 노출해야 합니다. 이 작업은 주로 도구 > 옵션 대화 상자의 **글꼴 및 색** 페이지를 통해 **수행됩니다.** 글꼴 설정의 세 가지 주요 범주는 다음과 같습니다.

- **환경 글꼴** - 대화 상자, 메뉴, 도구 창 및 문서 창을 비롯한 모든 인터페이스 요소에 사용되는 IDE(통합 개발 환경)의 기본 글꼴입니다. 기본적으로 환경 글꼴은 현재 버전의 Windows에서 9pt 맑은 고딕 표시되는 시스템 글꼴에 연결됩니다. 모든 인터페이스 요소에 대해 하나의 글꼴을 사용하면 IDE 전체에서 일관된 글꼴 모양을 유지할 수 있습니다.

- **텍스트 편집기** - 코드 및 기타 텍스트 기반 편집기에서 표면화되는 요소는 도구 > 옵션 의 텍스트 편집기 페이지에서 사용자 지정할 수 **있습니다.**

- **특정 컬렉션** - 인터페이스 요소의 사용자 지정을 제공하는 디자이너 창은 도구 > 옵션 의 자체 설정 페이지에서 디자인 표면과 특정한 글꼴을 노출할 수 **있습니다.**

### <a name="editor-font-customization-and-resizing"></a>편집기 글꼴 사용자 지정 및 크기 조정
 사용자는 일반 사용자 인터페이스와 관계없이 기본 설정에 따라 편집기에서 텍스트의 크기 및/또는 색을 확대하거나 확대/축소하는 경우가 많습니다. 환경 글꼴은 편집기/디자이너 내에서 또는 편집기의 일부로 나타날 수 있는 요소에 사용되므로 이러한 글꼴 분류 중 하나가 변경될 때 예상되는 동작에 유의해야 합니다.

 편집기에서 표시되지만 *콘텐츠의* 일부가 아닌 UI 요소를 만들 때는 요소의 크기를 예측 가능한 방식으로 조정하도록 텍스트 글꼴이 아닌 환경 글꼴을 사용하는 것이 중요합니다.

1. 편집기에서 코드 텍스트의 경우 코드 텍스트 글꼴 설정으로 크기를 조정하고 편집기 텍스트의 확대/축소 수준에 응답합니다.

2. 인터페이스의 다른 모든 요소는 환경 글꼴 설정에 연결되고 환경의 전역 변경에 응답해야 합니다. 여기에는 다음이 포함되지만 이에 제한되지 않습니다.

    - 상황에 맞는 메뉴의 텍스트

    - 전구 메뉴 텍스트, 빠른 찾기 편집기 창과 같은 편집기 장식의 텍스트 및 창으로 이동

    - **파일에서 찾기** 또는 **리팩터링과** 같은 대화 상자의 레이블 텍스트

### <a name="accessing-the-environment-font"></a>환경 글꼴 액세스
 네이티브 또는 WinForms 코드에서는 `IUIHostLocale::GetDialogFont` 서비스에서 인터페이스를 쿼리한 후 메서드를 호출하여 환경 글꼴에 액세스할 수 `SID_SUIHostLocale` 있습니다.

 WPF(Windows Presentation Foundation)의 경우 WPF의 클래스 대신 셸의 클래스에서 대화 상자 창 `DialogWindow` `Window` 클래스를 파생합니다.

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

코드 숨기기:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (를 `Microsoft.VisualStudio.Shell.11.0` MPF dll의 현재 버전으로 바꿉다.)

 대화 상자를 표시하려면 `ShowModal()` 를 통해 클래스에서 ""를 `ShowDialog()` 호출합니다. `ShowModal()` 는 셸에서 올바른 모달 상태를 설정하고 대화 상자가 부모 창의 가운데에 배치되도록 하는 등의 방식으로 설정합니다.

 코드는 다음과 같습니다.

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` 는 부울을 반환합니까? (nullable 부울)를 사용하는 `DialogResult` 이며, 필요한 경우 사용할 수 있습니다. 대화 상자가 **OK** 로 닫힌 경우 반환 값은 true입니다.

 대화 상자가 아니고 자체 에서 호스트되는 일부 WPF `HwndSource` UI(예: Win32/WinForms 부모 창의 WPF 자식 창)를 표시해야 하는 경우 `FontFamily` WPF 요소의 루트 요소에 및 를 설정해야 `FontSize` 합니다. (셸은 주 창에서 속성을 설정하지만 을 지나서 상속되지는 `HWND` 않습니다.) 셸은 다음과 같이 속성을 바인딩할 수 있는 리소스를 제공합니다.

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> 서식 지정(크기 조정/굵게 표시) 참조
 일부 대화 상자에서는 특정 텍스트가 굵게 표시되거나 환경 글꼴 이외의 크기여야 합니다. 이전에는 환경 글꼴보다 큰 글꼴이 " `environment font +2` " 또는 이와 유사하게 코딩되었습니다. 제공된 코드 조각을 사용하면 높은 DPI 모니터를 지원하고 표시 텍스트가 항상 올바른 크기 및 가중치(예: Light 또는 Semilight)로 표시되는지 확인합니다.

> [!NOTE]
> 서식을 적용하기 전에 [텍스트 스타일에](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)있는 지침을 따르고 있는지 확인합니다.**

 환경 글꼴의 크기를 조정하려면 TextBlock 또는 레이블의 스타일을 표시된 대로 설정합니다. 올바르게 사용되는 이러한 각 코드 조각은 적절한 크기 및 가중치 변형을 포함하여 올바른 글꼴을 생성합니다.

 여기서 " `vsui` "은 네임스페이스 에 대한 참조입니다. `Microsoft.VisualStudio.Shell`

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% 환경 글꼴 + 밝게

**다음과 같이 표시됩니다.** 34pt 맑은 고딕 Light

::: moniker range="vs-2017"

**사용:** (드문) 고유한 브랜드 UI(예: 시작 페이지)

::: moniker-end

::: moniker range=">=vs-2019"

**사용:** (드문) 고유한 브랜드 UI

::: moniker-end

**절차 코드:** 여기서 `textBlock` 는 이전에 정의된 TextBlock이고 는 이전에 정의된 `label` 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** 표시된 대로 TextBlock 또는 Label의 스타일을 설정합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% 환경 글꼴 + 밝게
 **다음과 같이 표시됩니다.** 28pt 맑은 고딕 Light **Use:** 큰 서명 대화 상자 제목, 보고서의 주 제목

 **절차 코드:** 여기서 `textBlock` 는 이전에 정의된 TextBlock이고 는 이전에 정의된 `label` 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** 표시된 대로 TextBlock 또는 Label의 스타일을 설정합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% 환경 글꼴 + Semilight
 **다음과 같이 표시됩니다.** 18pt 맑은 고딕 Semilight **Use for:** subheadings, titles in small and medium dialogs

 **절차 코드:** 여기서 `textBlock` 는 이전에 정의된 TextBlock이고 는 이전에 정의된 `label` 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% 환경 글꼴
 **다음과 같이 표시됩니다.** 14pt 맑은 고딕 **사용:** 문서 웰 UI 또는 보고서의 섹션 제목

 **절차 코드:** 여기서 `textBlock` 는 이전에 정의된 TextBlock이고 는 이전에 정의된 `label` 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% 환경 글꼴
 **다음과 같이 표시됩니다.** 12pt 맑은 고딕 **사용:** 서명 대화 상자 및 문서 웰 UI에서 더 작은 하위 헤더

 **절차 코드:** 여기서 `textBlock` 는 이전에 정의된 TextBlock이고 는 이전에 정의된 `label` 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% 환경 글꼴
 **다음과 같이 표시됩니다.** 11pt 맑은 고딕 **사용:** 서명 대화 상자의 섹션 제목, 트리 뷰의 상위 노드, 세로 탭 탐색

 **절차 코드:** 여기서 `textBlock` 는 이전에 정의된 TextBlock이고 는 이전에 정의된 `label` 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>환경 글꼴 + 굵게
 **다음과 같이 표시됩니다.** 굵게 표시된 9pt 맑은 고딕 **사용:** 서명 대화 상자, 보고서 및 문서 웰 UI의 레이블 및 하위 머리

 **절차 코드:** 여기서 `textBlock` 는 이전에 정의된 TextBlock이고 는 이전에 정의된 `label` 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** 다음과 같이 TextBlock 또는 Label의 스타일을 설정합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>지역화 가능한 스타일
 경우에 따라 지역화 도우미는 동아시아 언어에 대한 텍스트에서 굵게 표시를 제거하는 등 다양한 로케일의 글꼴 스타일을 수정해야 합니다. 글꼴 스타일의 지역화를 가능하게 하려면 해당 스타일이 .resx 파일 내에 있어야 합니다. 이렇게 하고 Visual Studio 폼 디자이너에서 글꼴 스타일을 편집하는 가장 좋은 방법은 디자인 타임에 글꼴 스타일을 명시적으로 설정하는 것입니다. 전체 글꼴 개체를 만들고 부모 글꼴의 상속을 끊는 것처럼 보일 수 있지만 FontStyle 속성만 글꼴을 설정하는 데 사용됩니다.

 해결 방법은 대화 폼의 이벤트를 후크하는 `FontChanged` 것입니다. 이벤트에서 `FontChanged` 모든 컨트롤을 안내하고 해당 글꼴이 설정되어 있는지 확인합니다. 설정된 경우 폼의 글꼴 및 컨트롤의 이전 글꼴 스타일에 따라 새 글꼴로 변경합니다. 코드에서 이에 대한 예는 다음과 같습니다.

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

 이 코드를 사용하면 폼의 글꼴이 업데이트될 때 컨트롤의 글꼴도 업데이트됩니다. 이 메서드는 폼의 생성자에서도 호출해야 합니다. 대화 상자가 인스턴스를 얻지 못할 수 `IUIService` 있고 이벤트가 발생하지 않기 `FontChanged` 때문입니다. 후크하면 대화 상자가 이미 열려 있는 `FontChanged` 경우에도 대화 상자에서 새 글꼴을 동적으로 선택할 수 있습니다.

### <a name="testing-the-environment-font"></a>환경 글꼴 테스트
 UI가 환경 글꼴을 사용하고 크기 설정을 준수하도록 하려면 **도구 > 옵션 > 환경 > 글꼴 및 색을** 열고 "설정 표시: " 드롭다운 메뉴에서 "환경 글꼴"을 선택합니다.

 ![도구 옵션 대화 상자의 글꼴 및 색 설정 &gt;](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />도구 옵션 대화 상자의 글꼴 및 색 설정 &gt;

 글꼴을 기본값과 매우 다른 글꼴로 설정합니다. 어떤 UI가 업데이트되지 않는지 확인하려면 세리프가 있는 글꼴(예: "Times New Roman")을 선택하고 매우 큰 크기를 설정합니다. 그런 다음, UI를 테스트하여 환경을 준수하는지 확인합니다. 라이선스 대화 상자를 사용하는 예제는 다음과 같습니다.

 ![환경 글꼴을 지원하지 않는 UI 텍스트의 예](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />환경 글꼴을 지원하지 않는 UI 텍스트의 예

 이 경우 "사용자 정보" 및 "제품 정보"는 글꼴을 준수하지 않습니다. 경우에 따라 이는 명시적 디자인 선택일 수 있지만 명시적 글꼴이 빨간색 선 사양의 일부로 지정되지 않은 경우 버그일 수 있습니다.

 글꼴을 다시 설정하려면 **도구 > 옵션 > 환경 > 글꼴 및 색** 에서 "기본값 사용"을 클릭합니다.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> 텍스트 스타일
 텍스트 스타일은 글꼴 크기, 두께 및 대/소문자를 나타냅니다. 구현 [지침은 환경 글꼴 을](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)참조하세요.

### <a name="text-casing"></a>텍스트 대/소문자 구분

#### <a name="all-caps"></a>모든 대문자
 Visual Studio 제목 또는 레이블에 대한 모든 대문자를 사용하지 마십시오.

#### <a name="all-lowercase"></a>모두 소문자
 Visual Studio 제목 또는 레이블에 소문자를 모두 사용하지 마십시오.

#### <a name="sentence-and-title-case"></a>문장 및 제목 대/소문자
 Visual Studio 텍스트는 상황에 따라 제목 대/소문자 또는 문장 대/소문자 중 하나를 사용해야 합니다.

|다음의 경우 제목 사례를 사용합니다.|다음의 경우 문장 대/소문자 사용:|
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
 제목 대/소문자는 구에 있는 단어의 대부분 또는 모든 첫 글자가 대문자로 표현되는 스타일입니다. Visual Studio 제목 대/소문자 는 다음을 비롯한 많은 항목에 사용됩니다.

- **툴팁.** 예: "선택한 항목 미리 보기"

- **열 머리글입니다.** 예: "시스템 응답"

- **메뉴 항목.** 예: "모두 저장"

  제목 대/소문자를 사용할 때는 단어를 대문자로 시작하고 소문자로 두는 경우에 대한 지침은 다음과 같습니다.

|대문자|주석 및 예제|
|---------------|---------------------------|
|모든 명사||
|모든 동사|"Is" 및 "to be"의 다른 형식 포함|
|모든 부사|"Than" 및 "When" 포함|
|모든 형용사|"This" 및 "That" 포함|
|모든 발음|소유형 "Its"와 "It's"를 포함하는 것은 "it" 및 동사 "is"의 축약입니다.|
|음성 부분에 관계없이 첫 번째 단어와 마지막 단어||
|동사 구의 일부인 전치사|"모든 창 닫기" 또는 "시스템 종료"|
|머리글자어의 모든 문자|HTML, XML, URL, IDE, RGB|
|명사 또는 적절한 형용사인 경우 복합 단어의 두 번째 단어이거나, 단어의 가중치가 같으면 입니다.|상호 참조, Microsoft 소프트웨어 이전, 읽기/쓰기 액세스, Run-Time|

|소문자|예|
|---------------|--------------|
|음성의 또 다른 부분인 경우 복합 단어의 두 번째 단어 또는 첫 번째 단어를 수정하는 부분|방법, 해제|
|제목에서 첫 번째 단어가 아닌 경우 아티클|a, an, the|
|좌표 결합|and, but, for, nor, or|
|동사 구 외부에 4개 이하의 문자가 있는 전치사|into, on, as as for, out, on of|
|무한 구에 사용되는 경우 "To"|"하드 디스크를 포맷하는 방법"|

##### <a name="sentence-case"></a>문장 대/소문자
 문장 대/소문자 는 문장의 첫 번째 단어만 적절한 명사 및 "I"와 함께 대문자로 표시되는 표준 대문자 표시 메서드입니다. 일반적으로 문장 사례는 특히 컴퓨터에서 콘텐츠를 번역할 때 전 세계 대상을 더 쉽게 읽을 수 있습니다. 다음의 경우 문장 대/소문자 사용:

1. **상태 표시줄 메시지.** 단순하고 짧으며 상태 정보만 제공합니다. 예: "프로젝트 파일 로드"

2. 레이블, 확인란, 라디오 단추 및 목록 상자 항목을 포함한 **다른 모든 UI 요소.** 예: "목록의 항목 Select all"

### <a name="text-formatting"></a>텍스트 서식 지정
 Visual Studio 2013 기본 텍스트 서식은 [환경 글꼴](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)로 제어됩니다. 이 서비스는 IDE(통합 개발 환경) 전체에서 일관된 글꼴 모양을 보장하는 데 도움이 되며, 사용자에게 일관된 환경을 보장하는 데 사용해야 합니다.

 Visual Studio 글꼴 서비스에서 사용하는 기본 크기는 Windows에서 제공되며 9pt로 표시됩니다.

 환경 글꼴에 서식을 적용할 수 있습니다. 이 항목에서는 스타일을 사용하는 방법 및 위치에 대해 다룹니다. 구현 정보는 환경 [글꼴](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)을 참조하세요.

#### <a name="bold-text"></a>굵은 텍스트
 굵은 텍스트는 Visual Studio 드물게 사용되며 다음을 위해 예약되어야 합니다.

- 마법사의 질문 레이블

- 솔루션 탐색기 활성 프로젝트 지정

- 속성 도구 창의 재정의된 값

- Visual Basic 편집기 드롭다운 목록의 특정 이벤트

- 웹 페이지에 대한 문서 개요의 서버 생성 콘텐츠

- 복잡한 대화 상자 또는 디자이너 UI의 섹션 헤더

#### <a name="italics"></a>기울임꼴
 Visual Studio 굵게 표시되거나 굵게 표시한 텍스트는 사용하지 않습니다.

#### <a name="color"></a>Color

- Blue는 하이퍼링크(탐색 및 명령)용으로 예약되며 방향에 사용하면 안 됩니다.

- 큰 제목(환경 글꼴 x 155% 이상)은 다음과 같은 용도로 색을 지정할 수 있습니다.

  - 시그니처 Visual Studio UI에 시각적 개체를 제공하려면

  - 특정 영역에 주의를 기울이려면

  - 표준 진한 회색/검은색 환경 텍스트 색에서 완화를 제공하려면

- 머리글의 색은 주로 주 자주색 #FF68217A 기존 Visual Studio 브랜드 색을 활용해야 합니다.

- 머리글에서 색을 사용하는 경우 대비 비율 및 기타 접근성 고려 사항을 포함하여 [Windows 색 지침을](/windows/desktop/uxguide/vis-color)따라야 합니다.

### <a name="font-size"></a>글꼴 크기
 Visual Studio UI 디자인은 더 많은 공백이 있는 밝은 모양을 제공합니다. 가능한 경우 크롬 및 제목 표시줄이 축소되거나 제거되었습니다. 정보 밀도는 Visual Studio 요구 사항이지만 보다 개방적인 줄 간격과 글꼴 크기 및 가중치 변형에 중점을 두고 입력 체계가 계속 중요합니다.

 아래 표에는 Visual Studio 사용되는 표시 글꼴에 대한 디자인 세부 정보 및 시각적 예제가 포함되어 있습니다. 일부 디스플레이 글꼴 변형에는 모양으로 코딩된 Semilight 또는 Light와 같은 크기와 두께가 모두 있습니다.

 모든 표시 글꼴에 대한 구현 코드 조각은 [서식 지정(크기 조정/굵게 표시) 참조](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)에서 찾을 수 있습니다.

#### <a name="375-environment-font--light"></a>375% 환경 글꼴 + 밝게

|사용|모양|
|-|-|
|**사용법:** 드문. 고유한 브랜드 UI만 해당합니다.<br /><br /> **다음을 수행합니다.**<br /><br /> - 문장 대/소문자 사용<br />- 항상 경량 사용<br /><br /> **안 함:**<br /><br /> - 시작 페이지와 같은 서명 UI 이외의 UI에 사용<br />- 굵게, italic 또는 굵은 italic<br />- 본문 텍스트에 사용<br />- 도구 창에서 사용|**다음과 같이 표시됩니다.** 34pt 맑은 고딕 Light<br /><br /> **시각적 개체 예제:**<br /><br /> *현재 사용되지 않습니다. Visual Studio 2017 시작 페이지에서 사용할 수 있습니다.*|

#### <a name="310-environment-font--light"></a>310% 환경 글꼴 + 밝게

::: moniker range="vs-2017"

|사용|모양|
|-|-|
|**사용법:**<br /><br /> - 서명 대화 상자의 더 큰 제목<br />- 주 보고서 제목<br /><br /> **다음을 수행합니다.**<br /><br /> - 문장 대/소문자 사용<br />- 항상 경량 사용<br /><br /> **안 함:**<br /><br /> - 시작 페이지와 같은 서명 UI 이외의 UI에 사용<br />- 굵게, italic 또는 굵은 italic<br />- 본문 텍스트에 사용<br />- 도구 창에서 사용|**다음과 같이 표시됩니다.** 28pt 맑은 고딕 Light<br /><br /> **시각적 개체 예제:**<br /><br /> ![310% 환경 글꼴 &#43; 밝은 머리글의 예](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|사용|모양|
|-|-|
|**사용법:**<br /><br /> - 서명 대화 상자의 더 큰 제목<br />- 주 보고서 제목<br /><br /> **다음을 수행합니다.**<br /><br /> - 문장 대/소문자 사용<br />- 항상 경량 사용<br /><br /> **안 함:**<br /><br /> - 서명 UI 이외의 UI에 사용<br />- 굵게, italic 또는 굵은 italic<br />- 본문 텍스트에 사용<br />- 도구 창에서 사용|**다음과 같이 표시됩니다.** 28pt 맑은 고딕 Light<br /><br /> **시각적 개체 예제:**<br /><br /> ![310% 환경 글꼴 &#43; 밝은 머리글의 예](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% 환경 글꼴 + Semilight

|사용|모양|
|-|-|
|**사용법:**<br /><br /> - 부제목<br />- 중소형 대화 상자의 제목<br /><br /> **다음을 수행합니다.**<br /><br /> - 문장 대/소문자 사용<br />- 항상 Semilight 가중치 사용<br /><br /> **안 함:**<br /><br /> - 굵게, italic 또는 굵은 italic<br />- 본문 텍스트에 사용<br />- 도구 창에서 사용|**다음으로 표시됩니다.** 18pt 맑은 고딕 Semillight<br /><br /> **시각적 개체 예제:**<br /><br /> ![200% 환경 글꼴 &#43; Semilight의 예](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% 환경 글꼴

|사용|모양|
|-|-|
|**사용법:**<br /><br /> - 문서 웰 UI의 섹션 제목<br />- 보고서<br /><br /> **다음을 수행합니다.** 문장 대/소문자 사용<br /><br /> **안 함:**<br /><br /> - 굵게, italic 또는 굵은 italic<br />- 본문 텍스트에 사용<br />- 표준 Visual Studio 컨트롤에서 사용<br />- 도구 창에서 사용|**다음과 같이 표시됩니다.** 14pt 맑은 고딕<br /><br /> **시각적 개체 예제:**<br /><br /> ![155% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% 환경 글꼴

|사용|모양|
|-|-|
|**사용법:**<br /><br /> - 서명 대화 상자에서 더 작은 하위 헤더<br />- 문서 웰 UI에서 더 작은 하위 헤더<br /><br /> **다음을 수행합니다.** 문장 대/소문자 사용<br /><br /> **안 함:**<br /><br /> - 굵게, italic 또는 굵은 italic<br />- 본문 텍스트에 사용<br />- 표준 Visual Studio 컨트롤에서 사용<br />- 도구 창에서 사용|**다음과 같이 표시됩니다.** 12pt 맑은 고딕<br /><br /> **시각적 개체 예제:**<br /><br /> ![133% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% 환경 글꼴

|사용|모양|
|-|-|
|**사용법:**<br /><br /> -서명 대화 상자의 섹션 제목<br />-트리 뷰의 최상위 노드<br />-세로 탭 탐색<br /><br /> **Do:** 문장 사례 사용<br /><br /> **안 함:**<br /><br /> -굵게, 기울임꼴 또는 굵은 기울임꼴<br />-본문 텍스트에 사용<br />-표준 Visual Studio 컨트롤에서 사용<br />-도구 창에서 사용|**다음과 같이 표시 됩니다.** 11pt 맑은 고딕<br /><br /> **시각적 예제:**<br /><br /> ![122% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>환경 글꼴 + 굵게

|사용|모양|
|-|-|
|**사용법:**<br /><br /> -서명 대화 상자의 레이블 및 부제<br />-보고서의 레이블 및 부제<br />-문서 웰 UI의 레이블 및 부제<br /><br /> **시겠습니까**<br /><br /> -문장 사례 사용<br />-굵은 두께 사용<br /><br /> **안 함:**<br /><br /> -기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트에 사용<br />-표준 Visual Studio 컨트롤에서 사용<br />-도구 창에서 사용|굵게 **표시 되는** 9 pt 맑은 고딕<br /><br /> **시각적 예제:**<br /><br /> ![환경 글꼴 &#43; 굵은 제목 예](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>환경 글꼴

|사용|모양|
|-|-|
|**사용:** 기타 모든 텍스트<br /><br /> **Do:** 문장 사례 사용<br /><br /> **안 함:** 기울임꼴 또는 굵게 기울임꼴|**다음과 같이 표시 됩니다.** 9 pt 맑은 고딕<br /><br /> **시각적 예제:**<br /><br /> ![환경 글꼴의 예](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>안쪽 여백 및 간격
 제목에는 적절 한 강조를 제공 하기 위해 주위의 공간이 필요 합니다. 이 공간은 포인트 크기 및 환경 글꼴의 가로 구분선 또는 텍스트 줄과 같이 머리글 근처의 다른 항목에 따라 달라 집니다.

- 제목의 이상적인 안쪽 여백은 대문자 문자 높이 공간의 90% 여야 합니다. 예를 들어 28 pt 맑은 고딕 밝은 제목에는 캡 높이가 26 pt이 고 안쪽 여백은 약 23 pt 또는 약 31 픽셀 이어야 합니다.

- 머리글 주위의 최소 공간은 대문자 높이의 50% 여야 합니다. 제목이 규칙이 나 기타 엄격한 맞춤 요소와 함께 제공 되는 경우 더 작은 공간을 사용할 수 있습니다.

- 굵게 표시 되는 환경 글꼴 텍스트는 기본 선 높이 간격과 안쪽 여백을 따라야 합니다.

## <a name="see-also"></a>참조

- [글꼴 (Windows)](/windows/desktop/uxguide/vis-fonts)
- [사용자 인터페이스 텍스트 (Windows)](/windows/desktop/uxguide/text-ui)
