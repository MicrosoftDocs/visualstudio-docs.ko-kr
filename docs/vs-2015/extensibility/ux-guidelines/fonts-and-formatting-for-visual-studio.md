---
title: 글꼴 및 서식 지정
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ede8844b34473e1c900bd6af040cac99ceee1514
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301322"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Visual Studio의 글꼴 및 서식 지정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>환경 글꼴
 사용자 지정을 위해 Visual Studio 내의 모든 글꼴을 사용자에게 노출해야 합니다. 이 작업은 주로 **도구 > 옵션** 대화 상자의 **글꼴 및 색상** 페이지를 통해 수행됩니다. 글꼴 설정의 세 가지 주요 범주는 다음과 같습니다.

- **환경 글꼴** — 대화 상자, 메뉴, 도구 창 및 문서 창을 비롯한 모든 인터페이스 요소에 사용되는 IDE(통합 개발 환경)의 기본 글꼴입니다. 기본적으로 환경 글꼴은 현재 버전의 Windows에서 9pt Segoe UI로 표시되는 시스템 글꼴에 연결됩니다. 모든 인터페이스 요소에 하나의 글꼴을 사용하면 IDE 전체에서 일관된 글꼴 모양을 유지할 수 있습니다.

- **텍스트 편집기** — 코드 및 기타 텍스트 기반 편집기에서 표시되는 요소는 **도구 > 옵션의**텍스트 편집기 페이지에서 사용자 지정할 수 있습니다.

- **특정 컬렉션** - 사용자 인터페이스 요소의 사용자 지정을 제공하는 디자이너 창은 **도구 > 옵션의**자체 설정 페이지에서 설계 표면에 특정글꼴을 노출할 수 있습니다.

### <a name="editor-font-customization-and-resizing"></a>편집자 글꼴 사용자 지정 및 크기 조정
 사용자는 일반적인 사용자 인터페이스와 관계없이 기본 설정에 따라 편집기에서 텍스트의 크기 및/또는 색상을 확대하거나 확대하는 경우가 많습니다. 환경 글꼴은 편집기/디자이너 내에서 또는 편집기/디자이너의 일부로 나타날 수 있는 요소에 사용되므로 이러한 글꼴 분류 중 하나가 변경될 때 예상되는 동작을 기록해야 합니다.

 편집기에서 나타나지만 *콘텐츠의*일부가 아닌 UI 요소를 만들 때는 텍스트 글꼴이 아닌 환경 글꼴을 사용하여 요소가 예측 가능한 방식으로 크기를 조정하도록 하는 것이 중요합니다.

1. 편집기의 코드 텍스트의 경우 코드 텍스트 글꼴 설정으로 크기를 조정하고 편집기 텍스트의 확대/축소 수준에 응답합니다.

2. 인터페이스의 다른 모든 요소는 환경 글꼴 설정에 연결되어야 하며 환경의 전역 변경 사항에 응답해야 합니다. 여기에는 다음이 포함됩니다(이에 국한되지 않음).

    - 컨텍스트 메뉴의 텍스트

    - 전구 메뉴 텍스트, 빠른 편집기 창 찾기 및 창으로 이동과 같은 편집기 장식의 텍스트

    - 파일에서 찾기 또는 리팩터링과 같은 대화 상자의 텍스트 레이블 지정

### <a name="accessing-the-environment-font"></a>환경 글꼴 에 액세스
 네이티브 또는 WinForms 코드에서 환경 글꼴은 SID_SUIHostLocale 서비스에서 인터페이스를 쿼리 한 후 **IUIHostLocale::GetDialogFont** 메서드를 호출 하여 액세스할 수 있습니다.

 WPF(Windows 프레젠테이션 파운데이션)의 경우 WPF의 창 클래스 대신 셸의 **대화 창** 클래스에서 대화 **창** 클래스를 파생시다.

 XAML에서 코드는 다음과 같습니다.

```
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>

code behind:

internal partial class WebConfigModificationWindow : DialogWindow
{
}

```

 (MPF dll의 현재 버전으로 바꿉니다.) `Microsoft.VisualStudio.Shell.11.0`

 대화 상자를 표시하려면 **ShowDialog()** 위에 클래스에서 **"ShowModal()**"를 호출합니다. **ShowModal()은** 셸에서 올바른 모달 상태를 설정하고 대화 상자가 부모 창의 가운데에 있는지 확인하는 등의 것입니다.

 코드는 다음과 같습니다.

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **쇼모달은** 멧돼지를 반환? (nullable Boolean)와 **대화결과,** 필요한 경우 사용할 수 있습니다. 대화 상자가 **확인으로**닫힌 경우 반환 값은 true입니다.

 대화 상자가 아니며 팝업 창또는 Win32/WinForms 부모 창의 WPF 자식 창과 같이 자체 **HwndSource에서**호스팅되는 일부 WPF UI를 표시해야 하는 경우 WPF 요소의 루트 요소에 **FontFamily** 및 **FontSize를** 설정해야 합니다. 셸은 기본 창에서 속성을 설정하지만 HWND를 지나 상속되지는 않습니다. 셸은 다음과 같이 속성을 바인딩할 수 있는 리소스를 제공합니다.

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>서식 지정(크기 조정/굵게) 참조
 일부 대화 상자에서는 특정 텍스트가 굵게 또는 환경 글꼴 이외의 크기여야 합니다. 이전에는 환경 글꼴보다 큰 글꼴이 "환경 글꼴 +2" 또는 이와 유사한 것으로 코딩되었습니다. 제공된 코드 조각을 사용하면 높은 DPI 모니터를 지원하고 표시 텍스트가 항상 올바른 크기와 무게(예: Light 또는 Semilight)로 표시되도록 합니다.

> **참고: 서식을 적용하기 전에 [텍스트 스타일에](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)있는 지침을 따르고 있는지 확인합니다.**

 환경 글꼴의 크기를 조정하려면 TextBlock 또는 레이블의 스타일을 표시된 대로 설정합니다. 제대로 사용된 이러한 각 코드 조각은 적절한 크기와 무게 변형을 포함하여 올바른 글꼴을 생성합니다.

 여기서 "vsui"는 네임스페이스 Microsoft.VisualStudio.Shell에 대한 참조입니다.

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>375% 환경 글꼴 + 빛
 **로 나타납니다 :** 34 pt 세고에 UI 라이트

 **에 대 한 사용:** (드문) 고유 한 브랜드 UI(예: 시작 페이지)

 **절차 코드:** 여기서 "textBlock"은 이전에 정의된 TextBlock이고 "레이블"은 이전에 정의된 레이블입니다.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **XAML:** 그림과 같이 텍스트 블록 또는 레이블의 스타일을 설정합니다.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>310% 환경 글꼴 + 라이트
 **로 나타납니다 :** 28 pt 세고에 UI 라이트

 **사용:** 큰 서명 대화 상자 제목, 보고서의 기본 제목

 **절차 코드:** 여기서 "textBlock"은 이전에 정의된 TextBlock이고 "레이블"은 이전에 정의된 레이블입니다.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **XAML:** 그림과 같이 텍스트 블록 또는 레이블의 스타일을 설정합니다.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>200% 환경 글꼴 + 세미라이트
 **로 나타납니다 :** 18 pt 세고에 UI 세미 라이트

 **에 대 한 사용:** 부제목, 작은 및 중간 대화 상자에서 제목

 **절차 코드:** 여기서 "textBlock"은 이전에 정의된 TextBlock이고 "레이블"은 이전에 정의된 레이블입니다.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **XAML:** 그림과 같이 텍스트 블록 또는 레이블의 스타일을 설정합니다.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>155% 환경 글꼴
 **다음과 같이 나타납니다 :** 14 pt 세고에 UI

 **에 대 한 사용:** 문서 잘 UI 또는 보고서의 섹션 제목

 **절차 코드:** 여기서 "textBlock"은 이전에 정의된 TextBlock이고 "레이블"은 이전에 정의된 레이블입니다.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **XAML:** 그림과 같이 텍스트 블록 또는 레이블의 스타일을 설정합니다.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>133% 환경 글꼴
 **다음과 같이 나타납니다 :** 12 pt 세고에 UI

 **에 대 한 사용:** 서명 대화 상자및 문서 잘 UI에서 작은 부제목

 **절차 코드:** 여기서 "textBlock"은 이전에 정의된 TextBlock이고 "레이블"은 이전에 정의된 레이블입니다.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **XAML:** 그림과 같이 텍스트 블록 또는 레이블의 스타일을 설정합니다.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>122% 환경 글꼴
 **다음과 같이 나타납니다 :** 11 pt 세고에 UI

 **에 대한 사용:** 서명 대화 상자의 단면 머리글, 트리 보기의 최상위 노드, 세로 탭 탐색

 **절차 코드:** 여기서 "textBlock"은 이전에 정의된 TextBlock이고 "레이블"은 이전에 정의된 레이블입니다.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **XAML:** 그림과 같이 텍스트 블록 또는 레이블의 스타일을 설정합니다.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>환경 글꼴 + 굵게
 **다음과 같이 나타납니다 :** 굵게 9 pt 세고에 UI

 **에 대 한 사용:** 서명 대화 상자, 보고서 및 문서 잘 UI에서 레이블 및 하위 헤드

 **절차 코드:** 여기서 "textBlock"은 이전에 정의된 TextBlock이고 "레이블"은 이전에 정의된 레이블입니다.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **XAML:** 그림과 같이 텍스트 블록 또는 레이블의 스타일을 설정합니다.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>지역화 가능한 스타일
 경우에 따라 지역 화자는 동아시아 언어의 텍스트에서 굵게 표시된 텍스트를 제거하는 등 다른 로캘에 대한 글꼴 스타일을 수정해야 합니다. 글꼴 스타일을 현지화하려면 해당 스타일이 .resx 파일 내에 있어야 합니다. 이를 달성하고 Visual Studio 양식 디자이너에서 글꼴 스타일을 편집하는 가장 좋은 방법은 디자인 타임에 글꼴 스타일을 명시적으로 설정하는 것입니다. 이렇게 하면 전체 글꼴 개체가 생성되고 상위 글꼴의 상속이 중단될 수 있지만 FontStyle 속성만 글꼴을 설정하는 데 사용됩니다.

 해결 방법은 대화 상자 양식의 **FontChanged** 이벤트를 연결하는 것입니다. **FontChanged** 이벤트에서 모든 컨트롤을 걷고 글꼴이 설정되어 있는지 확인합니다. 설정된 경우 양식의 글꼴과 컨트롤의 이전 글꼴 스타일에 따라 새 글꼴로 변경합니다. 코드에서 이것의 예는 다음과 같은 것입니다.

```
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

 이 코드를 사용하면 폼의 글꼴이 업데이트될 때 컨트롤 글꼴도 업데이트됩니다. 대화 상자가 **IUIService의** 인스턴스를 얻지 못하고 **FontChanged** 이벤트가 발생하지 않을 수 있으므로 폼의 생성자에서 이 메서드를 호출해야 합니다. **FontChanged** 후킹을 사용하면 대화 상자가 이미 열려 있는 경우에도 대화 상자가 새 글꼴을 동적으로 선택할 수 있습니다.

### <a name="testing-the-environment-font"></a>환경 글꼴 테스트
 UI가 환경 글꼴을 사용하고 크기 설정을 준수하도록 하려면 **도구 > 옵션 > 환경 > 글꼴 및 색상을** 열고 "환경 글꼴 표시:" 드롭다운 메뉴에서 "환경 글꼴"을 선택합니다.

 ![도구 &#62; 옵션 대화 상자의 글꼴 및 색상 페이지](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201-a_OptionsFonts")

 **도구 > 옵션 대화 상자의 글꼴 및 색상 설정**

 글꼴을 기본값과 매우 다른 것으로 설정합니다. 업데이트되지 않는 UI를 분명히 하려면 세리프가 있는 글꼴(예: "Times New Roman")을 선택하고 매우 큰 크기를 설정합니다. 그런 다음 UI를 테스트하여 환경을 준수하는지 확인합니다. 다음은 라이센스 대화 상자를 사용하는 예제입니다.

 ![환경 글꼴을 사용하지 않는 대화 상자의 예](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201-b_WrongFontDialog")

 **환경 글꼴을 준수하지 않는 UI 텍스트의 예**

 이 경우 "사용자 정보" 및 "제품 정보"는 글꼴을 존중하지 않습니다. 경우에 따라 명시적 디자인 선택일 수 있지만 명시적 글꼴이 redline 사양의 일부로 지정되지 않은 경우 버그가 될 수 있습니다.

 글꼴을 재설정하려면 도구 > 옵션 에서 "기본값 사용"을 **클릭> 환경 > 글꼴 및 색상.**

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>텍스트 스타일
 텍스트 스타일은 글꼴 크기, 가중치 및 대/소문자를 나타냅니다. 구현 지침은 [환경 글꼴](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)을 참조하십시오.

### <a name="text-casing"></a>텍스트 대/소문자

#### <a name="all-caps"></a>모든 대문자
 Visual Studio의 제목이나 레이블에 대해 모든 대문자를 사용하지 마십시오.

#### <a name="all-lowercase"></a>모든 소문자
 Visual Studio의 제목이나 레이블에는 모든 소문자를 사용하지 마십시오.

#### <a name="sentence-and-title-case"></a>문장 및 제목 케이스
 Visual Studio의 텍스트는 상황에 따라 제목 대/소문자 또는 문장 대/소문자를 사용해야 합니다.

|다음을 위해 제목 케이스를 사용합니다.|다음의 경우 문장 케이스를 사용합니다.|
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
 제목 대/소문자는 구 내의 대부분의 또는 모든 단어의 첫 글자가 대문자로 표기되는 스타일입니다. Visual Studio에서 제목 케이스는 다음을 포함한 많은 항목에 사용됩니다.

- **툴팁.** 예: "선택한 항목 미리 보기"

- **열 헤더입니다.** 예: "시스템 응답"

- **메뉴 항목입니다.** 예: "모두 저장"

  제목 대/소문자를 사용할 때 단어를 대문자로 사용하는 시기와 소문자를 남겨둘 시기에 대한 지침입니다.

|대문자|주석 및 예제|
|---------------|---------------------------|
|모든 가사||
|모든 동사|"Is"와 다른 형태의 "될 것"을 포함|
|모든 부사|"보다"와 "때"를 포함|
|모든 형용사|"This"와 "그"를 포함|
|모든 대명사|소유 "Its"뿐만 아니라 "It's", 대명사 "it"과 동사의 수축을 포함 "이다"|
|첫 번째와 마지막 단어, 음성의 일부에 관계없이||
|동사 구문의 일부인 전치사|"모든 창 닫기" 또는 "시스템 종료"|
|약어의 모든 문자|HTML, XML, URL, IDE, RGB|
|명사 또는 적절한 형용사인 경우 또는 단어의 가중치가 동일한 경우 복합 단어의 두 번째 단어|상호 참조, 사전 Microsoft 소프트웨어, 읽기/쓰기 액세스, 런타임|

|소문자|예|
|---------------|--------------|
|복합 단어의 두 번째 단어는 음성의 다른 부분이거나 첫 번째 단어를 수정하는 분할인 경우|방법, 이륙|
|기사, 제목에 첫 번째 단어가 없는 경우|a, an, the|
|좌표 연결|하지만,|
|동사 구 외에 4자 이하의 단어가 있는 전치사|에, 에, 에 관해서는, 밖으로, 위에|
|부정한 표현으로 사용될 때의 "To"|"하드 디스크 포맷 하는 방법"|

##### <a name="sentence-case"></a>문장 케이스
 문장 케이스는 적절한 명사 및 대명사 "I"와 함께 문장의 첫 번째 단어만 대문자로 쓰는 표준 대문자 지정 방법입니다. 일반적으로 문장 케이스는 특히 콘텐츠가 기계로 번역될 때 전 세계 시청자가 읽기가 더 쉽습니다. 다음의 경우 문장 케이스를 사용합니다.

1. **상태 표시줄 메시지입니다.** 이는 간단하고 짧으며 상태 정보만 제공합니다. 예: "프로젝트 파일 로드"

2. 레이블, 확인란, 라디오 단추 및 목록 상자 항목을 포함한 **기타 모든 UI 요소입니다.** 예: "목록에 있는 모든 항목 선택"

### <a name="text-formatting"></a>텍스트 서식 지정
 Visual Studio 2013의 기본 텍스트 서식은 [환경 글꼴에](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)의해 제어됩니다. 이 서비스는 IDE(통합 개발 환경)에서 일관된 글꼴 모양을 보장하는 데 도움이 되며, 이를 사용하여 사용자에게 일관된 환경을 보장해야 합니다.

 Visual Studio 글꼴 서비스에서 사용하는 기본 크기는 Windows에서 제공되며 9pt로 나타납니다.

 환경 글꼴에 서식을 적용할 수 있습니다. 이 항목에서는 스타일을 사용하는 방법과 위치를 다룹니다. 구현 정보는 환경 [글꼴을](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)참조하십시오.

#### <a name="bold-text"></a>굵은 텍스트
 굵은 텍스트는 Visual Studio에서 드물게 사용되며 다음을 위해 예약해야 합니다.

- 마법사의 질문 레이블

- 솔루션 탐색기에서 활성 프로젝트 지정

- 속성 도구 창에서 재정의된 값

- 비주얼 베이직 편집기 드롭다운 목록의 특정 이벤트

- 웹 페이지의 문서 개요에 서버에서 생성된 콘텐츠

- 복잡한 대화 상자 또는 디자이너 UI의 섹션 헤더

#### <a name="italics"></a>기울임꼴
 Visual Studio는 기울임꼴 또는 굵은 기울임꼴 텍스트를 사용하지 않습니다.

#### <a name="color"></a>색

- 파란색은 하이퍼링크(탐색 및 명령)용으로 예약되어 있으며 방향에 사용해서는 안 됩니다.

- 더 큰 머리글(환경 글꼴 x 155% 이상)은 다음과 같은 목적으로 색상이 지정될 수 있습니다.

  - 시그니처 Visual Studio UI에 시각적 어필을 제공하려면

  - 특정 영역에 주의를 환기시키기 위해

  - 표준 다크 그레이/블랙 환경 텍스트 색상에서 릴리프를 제공 하려면

- 제목의 색상은 주로 메인 퍼플, #FF68217A 기존 Visual Studio 브랜드 색상을 활용해야 합니다.

- 머리글에서 색상을 사용하는 경우 명암비 및 기타 접근성 고려 사항을 포함하여 [Windows 색상 지침을](https://msdn.microsoft.com/library/dn742482.aspx)준수해야 합니다.

### <a name="font-size"></a>글꼴 크기
 비주얼 스튜디오 UI 디자인은 더 넓은 공백과 밝은 모양을 갖추고 있습니다. 가능한 경우 크롬 및 제목 표시줄이 축소되거나 제거되었습니다. Visual Studio에서는 정보 밀도가 요구사항이지만 타이포그래피는 계속해서 중요하지만, 더 많은 개방된 줄 간격과 글꼴 크기 및 가중치의 변형에 중점을 둡습니다.

 아래 표에는 Visual Studio에서 사용되는 디스플레이 글꼴에 대한 디자인 세부 정보와 시각적 예제가 포함되어 있습니다. 일부 디스플레이 글꼴 변형에는 세미라이트 또는 라이트와 같은 크기와 가중치가 모두 모양으로 코딩되어 있습니다.

 모든 표시 글꼴에 대한 구현 코드 조각은 [서식 지정(크기 조정/굵게 표시) 참조에서](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)찾을 수 있습니다.

#### <a name="375-environment-font--light"></a>375% 환경 글꼴 + 빛

|||
|-|-|
|**사용 법:** 드문. 고유한 브랜드 UI만.<br /><br /> **다음을 수행합니다.**<br /><br /> - 사용 문장 케이스<br />- 항상 가벼운 무게를 사용<br /><br /> **수행하지 않아야 할 작업:**<br /><br /> - 시작 페이지와 같은 서명 UI 이외의 UI에 사용<br />- 굵게, 기울임꼴, 또는 굵은 기울임꼴<br />- 본문 텍스트에 사용<br />- 도구 창에서 사용|**로 나타납니다 :** 34 pt 세고에 UI 라이트<br /><br /> **시각적 인 예 :**<br /><br /> *현재 사용되지 않습니다. 시작 페이지에서 사용할 수 있습니다.*|

#### <a name="310-environment-font--light"></a>310% 환경 글꼴 + 라이트

|||
|-|-|
|**Usage:**<br /><br /> - 서명 대화 상자에서 더 큰 제목<br />- 주요 보고서 제목<br /><br /> **다음을 수행합니다.**<br /><br /> - 사용 문장 케이스<br />- 항상 가벼운 무게를 사용<br /><br /> **수행하지 않아야 할 작업:**<br /><br /> - 시작 페이지와 같은 서명 UI 이외의 UI에 사용<br />- 굵게, 기울임꼴, 또는 굵은 기울임꼴<br />- 본문 텍스트에 사용<br />- 도구 창에서 사용|**로 나타납니다 :** 28 pt 세고에 UI 라이트<br /><br /> **시각적 인 예 :**<br /><br /> ![310% 환경 글꼴 &#43; 라이트 제목의 예](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202-a_EF310")|

#### <a name="200-environment-font--semilight"></a>200% 환경 글꼴 + 세미라이트

|||
|-|-|
|**Usage:**<br /><br /> - 부제목<br />- 중소 대화 상자의 제목<br /><br /> **다음을 수행합니다.**<br /><br /> - 사용 문장 케이스<br />- 항상 세미 라이트 무게를 사용<br /><br /> **수행하지 않아야 할 작업:**<br /><br /> - 굵게, 기울임꼴, 또는 굵은 기울임꼴<br />- 본문 텍스트에 사용<br />- 도구 창에서 사용|**로 나타납니다 :** 18 pt 세고에 UI 세미 라이트<br /><br /> **시각적 인 예 :**<br /><br /> ![200% 환경 글꼴 &#43; 세미라이트의 예](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% 환경 글꼴

|||
|-|-|
|**Usage:**<br /><br /> - 문서 잘 UI의 섹션 제목<br />- 보고서<br /><br /> **다음을 수행합니다.** 사용 문장 케이스<br /><br /> **수행하지 않아야 할 작업:**<br /><br /> - 굵게, 기울임꼴, 또는 굵은 기울임꼴<br />- 본문 텍스트에 사용<br />- 표준 비주얼 스튜디오 컨트롤에 사용<br />- 도구 창에서 사용|**다음과 같이 나타납니다 :** 14 pt 세고에 UI<br /><br /> **시각적 인 예 :**<br /><br /> ![155% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% 환경 글꼴

|||
|-|-|
|**Usage:**<br /><br /> - 서명 대화 상자의 작은 부제목<br />- 문서 웰 UI의 작은 부제목<br /><br /> **다음을 수행합니다.** 사용 문장 케이스<br /><br /> **수행하지 않아야 할 작업:**<br /><br /> - 굵게, 기울임꼴, 또는 굵은 기울임꼴<br />- 본문 텍스트에 사용<br />- 표준 비주얼 스튜디오 컨트롤에 사용<br />- 도구 창에서 사용|**다음과 같이 나타납니다 :** 12 pt 세고에 UI<br /><br /> **시각적 인 예 :**<br /><br /> ![133% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% 환경 글꼴

|||
|-|-|
|**Usage:**<br /><br /> - 서명 대화 상자의 섹션 제목<br />- 트리 보기의 상단 노드<br />- 세로 탭 탐색<br /><br /> **다음을 수행합니다.** 사용 문장 케이스<br /><br /> **수행하지 않아야 할 작업:**<br /><br /> - 굵게, 기울임꼴, 또는 굵은 기울임꼴<br />- 본문 텍스트에 사용<br />- 표준 비주얼 스튜디오 컨트롤에 사용<br />- 도구 창에서 사용|**다음과 같이 나타납니다 :** 11 pt 세고에 UI<br /><br /> **시각적 인 예 :**<br /><br /> ![122% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>환경 글꼴 + 굵게

|||
|-|-|
|**Usage:**<br /><br /> - 서명 대화 상자의 레이블 및 하위 헤드<br />- 보고서의 라벨 및 하위 헤드<br />- 문서 웰 UI의 레이블 및 하위 헤드<br /><br /> **다음을 수행합니다.**<br /><br /> - 사용 문장 케이스<br />- 대담한 무게를 사용<br /><br /> **수행하지 않아야 할 작업:**<br /><br /> - 기울임꼴 또는 굵은 기울임꼴<br />- 본문 텍스트에 사용<br />- 표준 비주얼 스튜디오 컨트롤에 사용<br />- 도구 창에서 사용|**다음과 같이 나타납니다 :** 굵게 9 pt 세고에 UI<br /><br /> **시각적 인 예 :**<br /><br /> ![환경 글꼴 &#43; 굵은 글꼴의 예](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>환경 글꼴

|||
|-|-|
|**사용 법:** 기타 모든 텍스트<br /><br /> **다음을 수행합니다.** 사용 문장 케이스<br /><br /> **다음을 수행하지 마십시오.** 기울임꼴 또는 굵은 기울임꼴|**다음과 같이 나타납니다 :** 9 pt 세고에 UI<br /><br /> **시각적 인 예 :**<br /><br /> ![환경 글꼴의 예](../../extensibility/ux-guidelines/media/0202-g-ef.png "g_EF 0202-")|

### <a name="padding-and-spacing"></a>패딩 및 간격
 제목은 적절한 강조를 제공하기 위해 그들 주위에 공간이 필요합니다. 이 공간은 점 크기에 따라 달라지며, 다른 공간은 가로 규칙이나 환경 글꼴의 텍스트 줄과 같이 제목 근처에 있습니다.

- 제목 자체에 대한 이상적인 패딩은 대문자 높이 공간의 90%여야 합니다. 예를 들어 28pt Segoe UI 라이트 제목의 캡 높이는 26pt이고 패딩은 약 23pt 또는 약 31픽셀이어야 합니다.

- 제목 주위의 최소 공간은 대문자 높이의 50%여야 합니다. 제목에 규칙 또는 기타 밀착 요소가 동반될 때 더 적은 공간을 사용할 수 있습니다.

- 굵게 표시된 환경 글꼴 텍스트는 기본 줄 높이 간격 및 패딩을 따라야 합니다.

## <a name="see-also"></a>참고 항목
 [MSDN : 글꼴 (윈도우)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN : 사용자 인터페이스 텍스트 (윈도우)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
