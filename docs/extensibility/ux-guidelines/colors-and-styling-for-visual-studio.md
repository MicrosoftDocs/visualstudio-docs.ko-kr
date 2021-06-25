---
title: Visual Studio | 색 및 스타일 Microsoft Docs
description: Visual Studio 사용자 환경이 순수한 미적 이유 대신 색을 통신 도구로 사용하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: reference
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 307a4013c06258524c60619c6eff40e4d64740b6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904489"
---
# <a name="colors-and-styling-for-visual-studio"></a>Visual Studio의 색 및 스타일 지정

## <a name="use-color-in-visual-studio"></a>Visual Studio 색 사용

Visual Studio 색은 주로 장식뿐만 아니라 통신 도구로 사용됩니다. 색을 최소한으로 사용하고 다음을 수행하려는 상황에 대비하여 예약합니다.

- 의미 또는 소속 통신(예: 플랫폼 또는 언어 한정자)

- 관심 끌기(예: 상태 변경 표시)

- 가독성 향상 및 UI 탐색을 위한 랜드마크 제공

- 바람직성 향상

Visual Studio UI 요소에 색을 할당하는 몇 가지 옵션이 있습니다. 어떤 옵션을 사용해야 하는지 또는 올바르게 사용하는 방법을 파악하기가 어려울 수 있습니다. 이 항목은 다음을 도와 드립니다.

- Visual Studio 색을 정의하는 데 사용되는 다양한 서비스 및 시스템을 이해합니다.

- 지정된 요소에 대해 올바른 옵션을 선택합니다.

- 선택한 옵션을 올바르게 사용합니다.

> [!NOTE]
> 16진수, RGB 또는 시스템 색을 UI 요소에 하드 코딩하지 않습니다. 서비스를 사용하면 유연하게 튜닝할 수 있습니다. 또한 서비스가 없으면 [VSColor 서비스의](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)테마 전환 기능을 활용할 수 없습니다.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio 인터페이스 요소에 색을 할당하는 메서드

UI 요소에 가장 적합한 메서드를 선택합니다.

| Your UI | 메서드 | 무엇인가요? |
| --- | --- | --- |
| 포함된 대화 상자 또는 독립 실행형 대화 상자가 있습니다. | **시스템 색** | 운영 체제에서 일반적인 대화 상자 컨트롤과 같은 UI 요소의 색과 모양을 정의할 수 있도록 하는 시스템 이름입니다. |
| 전체 VS 환경과 일관성을 유지하려는 사용자 지정 UI가 있고 공유 토큰의 범주 및 의미 체계 의미와 일치하는 UI 요소가 있습니다. | **공통 공유 색** | 특정 UI 요소에 대해 미리 정의된 기존 색 토큰 이름 |
| 개별 기능 또는 기능 그룹이 있으며 비슷한 요소에 대한 공유 색이 없습니다. | **사용자 지정 색** | 영역과 관련되고 다른 UI와 공유되지 않는 색 토큰 이름 |
| 최종 사용자가 UI 또는 콘텐츠(예: 텍스트 편집기 또는 특수 디자이너 창)를 사용자 지정할 수 있도록 허용하려고 합니다. | **최종 사용자 지정**<br /><br />**(도구 &gt; 옵션 대화 상자)** | **도구 &gt; 옵션** 대화 상자의 "글꼴 및 색" 페이지 또는 하나의 UI 기능과 관련한 특수 페이지에 정의된 설정입니다. |

### <a name="visual-studio-themes"></a>Visual Studio 테마

Visual Studio 밝은 색 테마, 어둡게 및 파랑의 세 가지 색 테마를 제공합니다. 또한 접근성을 위해 설계된 시스템 차원의 색 테마인 고대비 모드를 검색합니다.

사용자는 Visual Studio 처음 사용하는 동안 테마를 선택하라는 메시지가 표시되며 나중에 도구 옵션 **&gt; 환경 &gt; &gt; 일반으로** 가서 "색 테마" 드롭다운 메뉴에서 새 테마를 선택하여 테마를 전환할 수 있습니다.

사용자는 제어판 사용하여 전체 시스템을 여러 고대비 테마 중 하나로 전환할 수도 있습니다. 사용자가 고대비 테마를 선택하면 사용자가 고대비 모드를 종료할 때 테마 변경 내용이 저장되지만 Visual Studio 색 테마 선택기는 더 이상 Visual Studio 색에 영향을 주지 않습니다. 고대비 모드에 대한 자세한 내용은 [고대비 색 선택을 참조하세요.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)

### <a name="the-vscolor-service"></a>VSColor 서비스

Visual Studio VSColor 서비스라고 하는 환경 색 서비스를 제공하며, 이를 통해 UI 요소의 색 값을 각 Visual Studio 테마의 색 값이 포함된 명명된 항목에 바인딩할 수 있습니다. 이렇게 하면 현재 사용자가 선택한 테마 또는 시스템 고대비 모드를 반영하도록 색이 자동으로 변경됩니다. 서비스의 사용은 모든 테마 관련 색 변경의 구현이 한 곳에서 처리된다는 것을 의미하며, 서비스에서 공통 공유 색을 사용하는 경우 UI는 이후 버전의 Visual Studio 새 테마를 자동으로 반영합니다.

### <a name="implementation"></a>구현

Visual Studio 소스 코드에는 토큰 이름 목록과 각 테마의 해당 색 값이 포함된 여러 패키지 정의 파일이 포함되어 있습니다. 색 서비스는 이러한 패키지 정의 파일에 정의된 VSColors를 읽습니다. 이러한 색은 XAML 태그 또는 코드에서 참조된 다음 `IVsUIShell5.GetThemedColor` 메서드 또는 DynamicResource 매핑을 통해 로드됩니다.

### <a name="system-colors"></a>시스템 색

공용 컨트롤은 기본적으로 시스템 색을 참조합니다. 포함된 대화 상자나 독립 실행형 대화 상자를 만들 때처럼 UI에서 시스템 색을 사용하도록 하려면 아무 것도 수행할 필요가 없습니다.

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor 서비스의 공통 공유 색

인터페이스 요소는 전체 Visual Studio 환경을 반영해야 합니다. 디자인하는 UI 구성 요소에 적합한 공통 공유 색을 다시 사용하면 인터페이스가 다른 Visual Studio 인터페이스와 일치하고 테마가 추가되거나 업데이트될 때 색이 자동으로 업데이트됩니다.

공통 공유 색을 사용하기 전에 올바르게 사용하는 방법을 이해해야 합니다. 일반적인 공유 색을 잘못 사용하면 사용자에게 일관되지 않거나, 불편하거나, 혼동을 초래할 수 있습니다.

### <a name="user-customizable-colors"></a>사용자 지정 가능한 색

참조: [최종 사용자에 대한 색 노출](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

코드 편집기 또는 디자인 표면을 만들 때와 같이 최종 사용자가 UI를 사용자 지정할 수 있도록 하는 경우가 있습니다. 사용자 지정 가능한 UI 구성 요소는 사용자가 전경색, 배경색 또는 둘 다 변경하도록 선택할 수 있는 **도구 &gt; 옵션** 대화 상자의 **글꼴 및** 색 섹션에 있습니다.

![도구 &gt; 옵션 대화 상자](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />도구 &gt; 옵션 대화 상자

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> VSColor 서비스

Visual Studio VSColor 서비스 또는 셸 색 서비스라고도 하는 환경 색 서비스를 제공합니다. 이 서비스를 사용하면 UI 요소의 색 값을 각 테마의 색이 포함된 이름-값 색 집합에 바인딩할 수 있습니다. VSColor 서비스는 모든 UI 요소에 사용해야 하므로 색이 현재 사용자가 선택한 테마를 반영하도록 자동으로 변경되고 환경 색 서비스에 바인딩된 UI가 이후 버전의 Visual Studio 새 테마와 통합되도록 해야 합니다.

### <a name="how-the-service-works"></a>서비스의 작동 방식

환경 색 서비스는 UI 구성 요소에 대한 .pkgdef에 정의된 VSColors를 읽습니다. 이러한 VSColors는 XAML 태그 또는 코드에서 참조되고 또는 `IVsUIShell5.GetThemedColor` 매핑을 통해 로드됩니다. `DynamicResource`

![환경 색 서비스 아키텍처](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />환경 색 서비스 아키텍처

### <a name="accessing-the-service"></a>서비스 액세스

사용 중인 색 토큰의 종류 및 코드 종류에 따라 VSColor 서비스에 액세스하는 방법에는 여러 가지가 있습니다.

#### <a name="predefined-environment-colors"></a>미리 정의된 환경 색

##### <a name="from-native-code"></a>네이티브 코드에서

셸은 색의 에 대한 액세스를 제공하는 서비스를 `COLORREF` 제공합니다. 서비스/인터페이스는 다음과 같습니다.

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

VSShell80.idl 파일에서 열거형에는 `__VSSYSCOLOREX` 셸 색 상수가 있습니다. 이를 사용하려면 MSDN에 설명된 값 중 하나 `enum __VSSYSCOLOREX` 또는 Windows 시스템 API가 허용하는 일반 인덱스 번호 중 하나로 인덱스 값으로 `GetSysColor` 전달합니다. 이렇게 하면 두 번째 매개 변수에 사용해야 하는 색의 RGB 값이 다시 표시됩니다.

새 색으로 펜 또는 브러시를 저장하는 경우 `AdviseBroadcastMessages` Visual Studio 셸에서 해제하고 및 메시지를 수신 대기해야 `WM_SYSCOLORCHANGE` `WM_THEMECHANGED` 합니다.

네이티브 코드에서 색 서비스에 액세스하려면 다음과 유사한 호출을 수행합니다.

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `COLORREF`에서 반환되는 값에는 `GetVSSysColorEx()` 테마 색의 R,G,B 구성 요소만 포함됩니다. 테마 항목에서 투명도를 사용하는 경우 알파 채널 값은 반환하기 전에 삭제됩니다. 따라서 투명도 채널이 중요한 곳에서 관심 있는 환경 색을 사용해야 하는 경우 `IVsUIShell5.GetThemedColor` `IVsUIShell2::GetVSSysColorEx` 이 항목의 후반부에 설명된 대로 대신 를 사용해야 합니다.

##### <a name="from-managed-code"></a>관리 코드에서

네이티브 코드를 통해 VSColor 서비스에 액세스하는 것은 매우 간단합니다. 그러나 관리 코드를 통해 작업하는 경우 서비스를 사용하는 방법을 결정하는 것이 어려울 수 있습니다. 이 점을 염두에 두고 이 프로세스를 보여 주는 C# 코드 조각은 다음과 같습니다.

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Visual Basic 작업하는 경우 다음을 사용합니다.

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF UI에서

애플리케이션의 로 내보낸 값을 통해 Visual Studio 색에 바인딩할 수 `ResourceDictionary` 있습니다. 다음은 색 테이블의 리소스를 사용하고 XAML의 환경 글꼴 데이터에 바인딩하는 예제입니다.

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>관리 코드에 대한 도우미 클래스 및 메서드

관리 코드의 경우 셸의 Managed Package Framework 라이브러리( `Microsoft.VisualStudio.Shell.12.0.dll` )에는 테마 색을 쉽게 사용할 수 있도록 하는 몇 가지 도우미 클래스가 포함되어 있습니다.

`Microsoft.VisualStudio.Shell.VsColors`MPF의 클래스에 있는 도우미 메서드에는 `GetThemedGDIColor()` 및 가 `GetThemedWPFColor()` 포함됩니다. 이러한 도우미 메서드는 `System.Drawing.Color` `System.Windows.Media.Color` WINFORMS 또는 WPF UI에서 사용할 테마 항목의 색 값을 또는로 반환 합니다.

```csharp
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}
```

클래스를 사용 하 여 지정 된 WPF 색 리소스 키에 대 한 VSCOLOR 식별자를 가져올 수도 있고 그 반대의 경우도 마찬가지입니다.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

클래스의 메서드는 `VsColors` vscolor 서비스를 쿼리하여 호출 될 때마다 색 값을 반환 합니다. 로 색 값을 얻으려면 `System.Drawing.Color` 더 나은 성능 대신 `Microsoft.VisualStudio.PlatformUI.VSThemeColor` , vscolor 서비스에서 가져온 색 값을 캐시 하는 클래스의 메서드를 대신 사용 하는 것이 더 좋습니다. 클래스는 내부적으로 셸 브로드캐스트 메시지 이벤트를 구독 하 고, 테마 변경 이벤트가 발생할 때 캐시 된 값을 삭제 합니다. 또한 클래스는를 제공 합니다. 테마 변경 내용을 구독할 수 있는 NET 친화적인 이벤트입니다. 이벤트를 사용 `ThemeChanged` 하 여 새 처리기를 추가 하 고 메서드를 사용 하 여 `GetThemedColor()` 관련의 색 값을 가져옵니다 `ThemeResourceKeys` . 샘플 코드는 다음과 같습니다.

```csharp
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> 고대비 색 선택

### <a name="overview"></a>개요

Windows에서는 텍스트, 배경 및 이미지의 색 대비를 높이는 여러 고대비 시스템 수준 테마를 사용 하 여 요소가 화면에 더 뚜렷이 표시 되도록 합니다. 내게 필요한 옵션을 위해 사용자가 고대비 테마로 전환할 때 Visual Studio 인터페이스 요소가 올바르게 응답 하는 것이 중요 합니다.

고대비 테마에는 몇 가지 시스템 색상만 사용할 수 있습니다. 시스템 색 이름을 선택할 때 다음 팁을 명심 하세요.

- 강조 표시 하는 요소와 **의미 체계가 동일한 시스템 색을 선택** 합니다. 예를 들어 창 내의 텍스트에 대해 고대비 색을 선택 하는 경우에는 WindowText를 사용 하 고 ControlText는 사용 하지 마십시오.

- **전경/배경 쌍** 을 함께 선택 하거나 색 선택이 모든 고대비 테마에서 작동 한다는 확신을 주지 않습니다.

- **UI에서 가장 중요 한 부분을 확인 하 고 콘텐츠 영역을 확장 해야 합니다.** 색 색상의 미묘한 차이로 인해 일반적으로 구분 되는 많은 세부 정보가 손실 됩니다. 따라서 다양 한 콘텐츠 영역에 대 한 색 변형이 없기 때문에 강력한 테두리 색을 사용 하 여 콘텐츠 영역을 정의 하는 것이 일반적입니다.

### <a name="system-color-set"></a>시스템 색 집합

[WPF 팀 블로그: SystemColors 참조](/archive/blogs/wpf/systemcolors-reference) 의 표는 시스템 색 이름의 전체 집합과 각 테마에 표시 되는 해당 색상을 나타냅니다.

이 제한 된 색 집합을 UI에 적용할 때 *"일반" 테마에 표시 되는 미묘한 세부 정보는 손실 될 것으로 예상 됩니다*. 다음은 도구 창 내에서 영역을 구분 하는 데 사용 되는 연한 회색 색이 있는 UI의 예입니다. 고대비 모드에 표시 된 것과 같은 창에 연결 되어 있는 경우 모든 배경이 동일한 지 확인 하 고 해당 영역의 테두리는 border로만 표시 됩니다.

![고대비에서 미묘한 세부 정보를 손실 하는 방법의 예](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />고대비에서 미묘한 세부 정보를 손실 하는 방법의 예

#### <a name="choosing-text-colors-in-an-editor"></a>편집기에서 텍스트 색 선택

색이 지정 된 텍스트는 유사한 항목 그룹을 쉽게 식별할 수 있도록 허용 하는 것과 같은 의미를 나타내기 위해 편집기나 디자인 화면에서 사용 됩니다. 그러나 고대비 테마에는 세 개 이상의 텍스트 색을 구분 하는 기능이 없습니다. Windowtext 화면에서 사용할 수 있는 유일한 색은 WindowText, GrayText 및 HotTrackText입니다. 3 개 이상의 색을 사용할 수 없기 때문에 고대비 모드에서 표시 하려는 가장 중요 한 차이점을 신중 하 게 선택 합니다.

각 고대비 테마에 표시 되는 것 처럼 편집기 화면에서 사용할 수 있는 각 토큰 이름에 대 한 색상입니다.

![고대비 편집기 비교](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />고대비 편집기 비교

파란색 테마의 편집기 화면 예:

![파란색 테마의 편집기](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />파란색 테마의 편집기

![고대비 #1 테마의 편집기](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />고대비 #1 테마의 편집기

### <a name="usage-patterns"></a>사용 패턴

대부분의 일반적인 UI 요소에는 고대비 색이 이미 정의 되어 있습니다. 사용자 고유의 시스템 색 이름을 선택할 때 이러한 사용 패턴을 참조 하 여 UI 요소가 유사한 구성 요소와 일치 하도록 할 수 있습니다.

| 시스템 색 | 사용 |
| --- | --- |
| ActiveCaption | -활성 IDE 및 rafted 창의 단추 문자 모양 가리키기 및 누르기<br />-IDE 및 rafted 창의 제목 표시줄 배경<br />-기본 상태 표시줄 배경 |
| ActiveCaptionText | -제목 표시줄 전경 (텍스트 및 문자 모양)의 활성 IDE 및 rafted 창<br />-마우스로 가리키면 활성 창 단추의 배경색과 테두리 |
| 제어 | -콤보 상자, 드롭다운 목록, 검색 컨트롤의 기본 및 비활성화 된 배경 (드롭다운 단추 포함)<br />-도킹 대상 단추 배경<br />-명령 모음 배경<br />-도구 창 배경 |
| ControlDark | -IDE 배경<br />-메뉴 및 명령 모음 구분 기호<br />-명령 모음 테두리<br />-메뉴 그림자<br />-도구 창 탭 기본 및 가리키기 테두리 및 구분 기호<br />-문서 웰 오버플로 단추 배경<br />-도킹 대상 문자 모양 테두리 |
| ControlDarkDark |-포커스가 없는, 선택한 문서 탭 창 |
| ControlLight |-자동 숨기기 탭 테두리<br />-콤보 상자 및 드롭다운 목록 테두리<br />-도킹 대상 배경 및 테두리 |
| ControlLightLight | -선택, 포커스가 있는 provisional border |
| 컨트롤 텍스트 | -콤보 상자 및 드롭다운 목록 문자 모양<br />-도구 창 선택 하지 않은 탭 텍스트 |
| GrayText |-콤보 상자 및 드롭다운 목록 사용 안 함 테두리, 드롭다운 문자 모양, 텍스트 및 메뉴 항목 텍스트<br />-사용 안 함 메뉴 텍스트<br />-검색 컨트롤 ' 검색 옵션 ' 헤더 텍스트<br />-검색 컨트롤 섹션 구분 기호 |
| 강조 표시 | -콤보 상자 드롭다운 단추 배경 및 문서 웰 오버플로 단추 테두리를 제외 하 고 모든 마우스로 가리키고 누른 상태 배경 및 테두리<br />-선택한 항목 배경 |
| HighlightText | -모든 가리키기 및 누름 foregrounds (텍스트 및 문자 모양)<br />-포커스가 있는 도구 창 및 문서 탭 창 컨트롤 전경<br />-포커스가 있는 도구 창 제목 표시줄 테두리<br />-포커스가 있는 provisional 탭 전경<br />-문서 웰 오버플로 단추 테두리 가리키기 및 누르기<br />-선택한 아이콘 테두리|
| HotTrack | -누름 스크롤 막대 thumb 배경 및 테두리 누름<br />-누를 때 스크롤 막대 화살표 문자 모양 |
| InactiveCaption | -비활성 IDE 및 rafted 창 단추 문자 모양 가리키기<br />-IDE 및 rafted 창의 제목 표시줄 배경<br />-사용 하지 않도록 설정 된 검색 컨트롤 배경 |
| InactiveCaptionText | -비활성 IDE 및 rafted windows 제목 표시줄 전경 (텍스트 및 문자 모양)<br />-비활성 창 단추 배경 및 테두리 가리키기<br />-포커스가 없는 도구 창 단추 배경 및 테두리<br />- 검색 컨트롤 포그라운드 사용 안 함 |
| 메뉴 | - 드롭다운 메뉴 배경<br />- 확인 표시 배경 확인 및 사용 안 함 |
| MenuText | - 드롭다운 메뉴 테두리<br />- 확인 표시<br />- 메뉴 문자<br />- 드롭다운 메뉴 텍스트<br />- 선택한 아이콘 테두리 |
| 스크롤 막대 | - 스크롤 막대 및 스크롤 막대 화살표 배경, 모든 상태 |
| 시간 범위 | - 탭 배경 자동 숨기기<br />- 메뉴 모음 및 명령 보관 배경<br />- 열려 있는 탭과 빈 탭 모두에 대해 할당되지 않거나 선택되지 않은 문서 창 탭 배경 및 문서 테두리<br />- 사용되지 않는 도구 창 제목 표시줄 배경<br />- 도구 창 탭 배경(선택 및 선택 취소) |
| WindowFrame | - IDE 테두리 |
| WindowText | - 탭 전경 자동 숨기기<br />- 선택한 도구 창 탭 전경<br />- 할당되지 않은 문서 창 탭 및 사용되지 않거나 선택되지 않은 비표시 탭 전경<br />- 트리 뷰 기본 전경 및 선택되지 않은 문자로 가리키기<br />- 도구 창이 선택한 탭 테두리<br />- 스크롤 막대 엄지 배경, 테두리 및 문자 |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> 최종 사용자의 색 노출

### <a name="overview"></a>개요

코드 편집기 또는 디자인 표면을 만들 때와 같이 최종 사용자가 UI를 사용자 지정할 수 있도록 허용하는 경우가 있습니다. 이 작업을 수행하는 가장 일반적인 방법은 **도구 &gt; 옵션** 대화 상자를 사용하는 것입니다. 특수한 컨트롤이 필요한 매우 특수한 UI가 없는 경우 사용자 지정을 제공하는 가장 쉬운 방법은 대화 상자의 **환경** 섹션에 있는 **글꼴 및 색** 페이지를 통하는 것입니다. 사용자 지정을 위해 노출하는 각 요소에 대해 사용자는 전경색, 배경색 또는 둘 다 변경하도록 선택할 수 있습니다.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>사용자 지정 가능한 색에 대한 VSPackage 빌드

VSPackage는 사용자 지정 범주를 통해 글꼴 및 색을 제어하고 글꼴 및 색 속성 페이지에 항목을 표시할 수 있습니다. 이 메커니즘을 사용하는 경우 VSPackages는 [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) 인터페이스 및 관련 인터페이스를 구현해야 합니다.

원칙에 따라 이 메커니즘을 사용하여 모든 기존 표시 항목과 해당 항목이 포함된 범주를 수정할 수 있습니다. 그러나 텍스트 편집기 범주 또는 해당 표시 항목을 수정하는 데 사용하면 안 됩니다. 텍스트 편집기 범주에 대한 자세한 내용은 [글꼴 및 색 개요를 참조하세요.](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015)

사용자 지정 범주를 구현하거나 항목을 표시하려면 VSPackage는 다음을 수행해야 합니다.

- **레지스트리에서 범주를 만들거나 식별합니다.** IDE의 **글꼴 및 색** 속성 페이지 구현에서는 이 정보를 사용하여 지정된 범주를 지원하는 서비스를 올바르게 쿼리합니다.

- **레지스트리에서 그룹을 만들거나 식별합니다(선택 사항).** 둘 이상의 범주의 합집합을 나타내는 그룹을 정의하는 것이 유용할 수 있습니다. 그룹이 정의된 경우 IDE는 자동으로 하위 범주를 병합하고 그룹 내에 표시 항목을 배포합니다.

- **IDE 지원을 구현합니다.**

- **글꼴 및 색 변경을 처리합니다.**

#### <a name="to-create-or-identify-categories"></a>범주를 만들거나 식별하려면

에서 특수한 유형의 범주 레지스트리 항목을 `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` 생성합니다. 여기서 `<Category>` 는 범주의 지역화가 아닌 이름입니다.

레지스트리를 다음 두 값으로 채웁합니다.

| 속성 | Type | 데이터 | Description |
| --- | --- | --- | --- |
| 범주 | REG_SZ | GUID | 범주를 식별하기 위해 만든 GUID |
| 패키지 | REG_SZ | GUID | 범주를 지원하는 VSPackage 서비스의 GUID |

 레지스트리에 지정된 서비스는 해당 범주에 대한 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 구현을 제공해야 합니다.

#### <a name="to-create-or-identify-groups"></a>그룹을 만들거나 식별하려면

에서 특수한 유형의 범주 레지스트리 항목을 `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` 생성합니다. 여기서 `<group>` 은 그룹의 지역화가 아닌 이름입니다.

레지스트리를 다음 두 값으로 채웁합니다.

| 속성 | Type | 데이터 | Description |
|--- | --- | --- | --- |
| 범주 | REG_SZ | GUID | 범주를 식별하기 위해 만든 GUID |
| 패키지 | REG_SZ | GUID | 범주를 지원하는 VSPackage 서비스의 GUID |

레지스트리에 지정된 서비스는 해당 그룹에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 구현을 제공해야 합니다.

![IVsFontAndColorGroup 구현](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />`IVsFontAndColorGroup`의 구현입니다.

### <a name="to-implement-ide-support"></a>IDE 지원을 구현하려면

제공된 각 범주 또는 그룹 GUID에 대해 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 인터페이스 또는 IDE에 대한 인터페이스를 반환하는 [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject)를 구현합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>

VSPackage는 지원하는 모든 범주에 대해 [별도의 IVsFontAndColorDefaults 인터페이스 인스턴스를 구현합니다.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)

[IVsFontAndColorDefaults를](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 통해 구현된 메서드는 IDE에 다음을 제공해야 합니다.

- 범주의 표시 항목 목록

- 표시 항목의 지역화할 수 있는 이름

- 범주의 각 멤버에 대한 정보 표시

> [!NOTE]
> 모든 범주에는 하나 이상의 표시 항목이 포함되어야 합니다.

IDE는 인터페이스를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 여러 범주의 합집합을 정의합니다.

해당 구현은 IDE에 다음을 제공합니다.

- 지정된 그룹을 구성하는 범주 목록

- 그룹 내의 각 범주를 지원하는 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 인스턴스에 대한 액세스

- 지역화할 수 있는 그룹 이름

#### <a name="updating-the-ide"></a>IDE 업데이트

IDE는 글꼴 및 색 설정에 대한 정보를 캐시합니다. 따라서 IDE 글꼴 및 색 구성을 수정한 후에는 캐시가 최신 상태로 유지되도록 하는 것이 가장 좋습니다.

캐시 업데이트는 [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) 인터페이스를 통해 수행되며 전역적으로 또는 선택한 항목에서만 수행할 수 있습니다.

### <a name="handling-font-and-color-changes"></a>글꼴 및 색 변경 처리

VSPackage가 표시하는 텍스트의 색 지정을 제대로 지원하려면 VSPackage를 지원하는 색 지정 서비스가 글꼴 및 색 속성 페이지를 통해 사용자가 시작한 변경 내용에 응답해야 합니다.

이렇게 하려면 VSPackage는 다음을 수행해야 합니다.

- [는 IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) 인터페이스를 구현하여 **IDE에서 생성된 이벤트를 처리합니다.** IDE는 글꼴 및 색 페이지의 사용자 수정에 따라 적절한 메서드를 호출합니다. 예를 들어 새 글꼴이 선택된 경우 [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) 메서드를 호출합니다.

  **OR**

- **변경 내용에 대해 IDE를 폴링합니다.** 이 작업은 시스템 구현 [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) 인터페이스를 통해 수행할 수 있습니다. [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) 메서드는 주로 지속성을 지원하지만 표시 항목에 대한 글꼴 및 색 정보를 가져올 수 있습니다. 글꼴 및 색 설정에 대한 자세한 내용은 MSDN 문서 저장된 글꼴 및 색 설정 액세스 를 [참조하세요.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015)

> [!NOTE]
> 폴링 결과가 올바른지 확인하려면 [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) 인터페이스를 사용하여 [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) 인터페이스의 검색 메서드를 호출하기 전에 캐시 플러시 및 업데이트가 필요한지 확인합니다.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>인터페이스를 구현하지 않고 사용자 지정 글꼴 및 색 범주 등록

다음 코드 예제에서는 인터페이스를 구현하지 않고 사용자 지정 글꼴 및 색 범주를 등록하는 방법을 보여줍니다.

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

이 코드 예제의 경우:

- `"NameID"` = 패키지에 있는 지역화된 범주 이름의 리소스 ID
- `"ToolWindowPackage"` = 패키지 GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` 는 예제일 뿐이며 실제 값은 구현자가 제공하는 새 GUID일 수 있습니다.

### <a name="set-the-font-and-color-property-category-guid"></a>글꼴 및 색 속성 범주 GUID 설정

아래 코드 예제에서는 범주GUID를 설정하는 것을 보여줍니다.

```csharp
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
