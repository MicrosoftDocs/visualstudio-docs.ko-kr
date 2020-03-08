---
title: Visual Studio의 색 및 스타일 지정 | Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ceea00a3fa77a9c1106f24f28ac1d5890437b41
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409003"
---
# <a name="colors-and-styling-for-visual-studio"></a>Visual Studio의 색 및 스타일 지정

## <a name="use-color-in-visual-studio"></a>Visual Studio에서 색 사용

Visual Studio에서 색은 주로 데코레이션 뿐만 아니라 통신 도구로 사용 됩니다. 최소 색을 사용 하 고 다음을 수행 하려는 경우에 대비 합니다.

- 의미 또는 정보 (예: 플랫폼 또는 언어 한정자)를 전달 합니다.

- 상태 변경을 나타내는 등의 관심

- 가독성 향상 및 UI 탐색을 위한 랜드마크 제공

- 원활 증가

Visual Studio의 UI 요소에 색을 할당 하기 위한 몇 가지 옵션이 있습니다. 어떤 옵션을 사용 해야 하는지 또는 올바르게 사용 하는 방법을 파악 하기 어려울 수 있습니다. 이 항목은 다음 작업을 도와 줍니다.

- Visual Studio에서 색을 정의 하는 데 사용 되는 다양 한 서비스 및 시스템을 이해 합니다.

- 지정 된 요소에 대 한 올바른 옵션을 선택 합니다.

- 선택한 옵션을 올바르게 사용 합니다.

> [!NOTE]
> UI 요소에 대 한 16 진수, RGB 또는 시스템 색을 하드 코딩 하지 마십시오. 서비스를 사용 하면 색상을 유연 하 게 조정할 수 있습니다. 또한 서비스를 사용 하지 않을 경우 [VSColor 서비스](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)의 테마 전환 기능을 활용할 수 없습니다.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio 인터페이스 요소에 색을 할당 하는 방법

UI 요소에 가장 적합 한 방법을 선택 합니다.

| UI | 방법 | 무엇 인가요? |
| --- | --- | --- |
| 포함 되거나 독립 실행형 대화 상자가 있습니다. | **시스템 색** | 운영 체제에서 일반적인 대화 상자 컨트롤과 같은 UI 요소의 색과 모양을 정의할 수 있도록 하는 시스템 이름입니다. |
| 전반적인 VS 환경과 일치 시키고 공유 토큰의 범주 및 의미 체계와 일치 하는 UI 요소를 포함 하는 사용자 지정 UI가 있습니다. | **공통 공유 색** | 특정 UI 요소에 대해 미리 정의 된 기존 색 토큰 이름 |
| 개별 기능이 나 기능 그룹이 있으며 유사한 요소에 대 한 공유 색이 없습니다. | **사용자 지정 색** | 영역에 고유 하며 다른 UI와 공유 하지 않는 색 토큰 이름 |
| 최종 사용자가 UI 나 콘텐츠를 사용자 지정할 수 있도록 허용 하려고 합니다 (예: 텍스트 편집기나 특수 디자이너 창). | **최종 사용자 사용자 지정**<br /><br />**(도구 &gt; 옵션 대화 상자)** | **도구 &gt; 옵션** 대화 상자의 "글꼴 및 색" 페이지 또는 하나의 UI 기능과 관련 된 특수 한 페이지에 정의 된 설정입니다. |

### <a name="visual-studio-themes"></a>Visual Studio 테마

Visual Studio는 밝은 색, 어둡게, 파랑의 세 가지 색 테마를 제공 합니다. 내게 필요한 옵션을 위해 디자인 된 시스템 차원 색 테마 인 고대비 모드도 검색 합니다.

사용자에 게는 처음 Visual Studio를 사용 하는 동안 테마를 선택 하 라는 메시지가 표시 되 고 **도구 &gt; 옵션 &gt; 환경 &gt; 일반** 으로 이동한 후 "색 테마" 드롭다운 메뉴에서 새 테마를 선택 하 여 테마를 전환할 수 있습니다.

또한 사용자는 제어판을 사용 하 여 전체 시스템을 여러 고대비 테마 중 하나로 전환할 수 있습니다. 사용자가 고대비 테마를 선택 하면 visual Studio 색 테마 선택 기가 더 이상 Visual Studio의 색에 영향을 주지 않습니다. 단, 사용자가 고대비 모드를 끝내 면 테마 변경 내용이 저장 됩니다. 고대비 모드에 대 한 자세한 내용은 [고대비 색 선택](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)을 참조 하세요.

### <a name="the-vscolor-service"></a>VSColor 서비스

Visual Studio는 VSColor 서비스 라고 하는 환경 색 서비스를 제공 합니다 .이를 통해 각 Visual Studio 테마에 대 한 색 값을 포함 하는 명명 된 항목에 UI 요소의 색 값을 바인딩할 수 있습니다. 이렇게 하면 현재 사용자가 선택한 테마 또는 시스템 고대비 모드가 반영 되도록 색이 자동으로 변경 됩니다. 서비스를 사용 하면 모든 테마 관련 색 변경의 구현이 한 곳에서 처리 되며, 서비스에서 공통 된 공유 색을 사용 하는 경우 UI는 이후 버전의 Visual Studio에서 새 테마를 자동으로 반영 합니다.

### <a name="implementation"></a>구현

Visual Studio 소스 코드에는 토큰 이름 목록과 각 테마에 대 한 각 색 값을 포함 하는 여러 패키지 정의 파일이 포함 되어 있습니다. Color service는 이러한 패키지 정의 파일에 정의 된 VSColors를 읽습니다. 이러한 색은 XAML 태그 또는 코드에서 참조 된 다음 `IVsUIShell5.GetThemedColor` 메서드 또는 DynamicResource 매핑을 통해 로드 됩니다.

### <a name="system-colors"></a>시스템 색

공용 컨트롤은 기본적으로 시스템 색을 참조 합니다. 포함 된 대화 상자 또는 독립 실행형 대화 상자를 만들 때와 같이 UI에서 시스템 색을 사용 하 게 하려면 아무것도 수행할 필요가 없습니다.

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor 서비스의 공통 공유 색

인터페이스 요소는 전체 Visual Studio 환경을 반영 해야 합니다. 디자인 하는 UI 구성 요소에 적절 한 공통 공유 색을 다시 사용 하 여 인터페이스가 다른 Visual Studio 인터페이스와 일치 하는지 확인 하 고 테마가 추가 되거나 업데이트 될 때 색이 자동으로 업데이트 됩니다.

공통 된 공유 색을 사용 하기 전에이를 올바르게 사용 하는 방법을 이해 해야 합니다. 공통 공유 색의 잘못 된 사용으로 인해 사용자에 게 일관 되지 않거나, 당황 하거나, 혼동 될 수 있습니다.

### <a name="user-customizable-colors"></a>사용자 지정이 가능한 색

참조: [최종 사용자에 대 한 색 노출](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

때로는 코드 편집기 또는 디자인 화면을 만들 때와 같이 최종 사용자가 UI를 사용자 지정할 수 있도록 하는 것이 좋습니다. 사용자 지정 가능한 UI 구성 요소는 **도구 &gt; 옵션** 대화 상자의 **글꼴 및 색** 섹션에서 찾을 수 있습니다. 여기서 사용자는 전경색, 배경색 또는 둘 다를 변경 하도록 선택할 수 있습니다.

![도구 &gt; 옵션 대화 상자](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />도구 &gt; 옵션 대화 상자

## <a name="BKMK_TheVSColorService"></a>VSColor 서비스

Visual Studio는 VSColor 서비스 또는 셸 색 서비스 라고도 하는 환경 색 서비스를 제공 합니다. 이 서비스를 사용 하면 UI 요소의 색 값을 각 테마에 대 한 색을 포함 하는 이름-값 색 집합에 바인딩할 수 있습니다. 모든 UI 요소에 대해 VSColor 서비스를 사용 하 여 현재 사용자가 선택한 테마를 반영 하도록 색을 자동으로 변경 하 고, 환경 색 서비스에 바인딩된 UI가 이후 버전의 Visual Studio에서 새 테마와 통합 되도록 합니다.

### <a name="how-the-service-works"></a>서비스의 작동 방식

환경 색 서비스는 UI 구성 요소에 대 한 .pkgdef에 정의 된 VSColors를 읽습니다. 이러한 VSColors는 XAML 태그 또는 코드에서 참조 되며 `IVsUIShell5.GetThemedColor` 또는 `DynamicResource` 매핑을 통해 로드 됩니다.

![환경 색 서비스 아키텍처](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />환경 색 서비스 아키텍처

### <a name="accessing-the-service"></a>서비스 액세스

사용 중인 색 토큰의 종류와 사용 하는 코드의 종류에 따라 VSColor 서비스에 액세스할 수 있는 여러 가지 방법이 있습니다.

#### <a name="predefined-environment-colors"></a>미리 정의 된 환경 색

##### <a name="from-native-code"></a>네이티브 코드에서

Shell은 색의 `COLORREF`에 대 한 액세스를 제공 하는 서비스를 제공 합니다. 서비스/인터페이스는 다음과 같습니다.

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

VSShell80 파일에서 열거형 `__VSSYSCOLOREX`에는 셸 색 상수가 있습니다. 이를 사용 하려면 MSDN에 설명 된 `enum __VSSYSCOLOREX` 값 중 하나 또는 Windows 시스템 API `GetSysColor`가 수락 하는 일반 인덱스 번호 중 하나를 인덱스 값으로 전달 합니다. 이렇게 하면 두 번째 매개 변수에 사용 해야 하는 색의 RGB 값이 반환 됩니다.

펜 또는 브러시를 새 색으로 저장 하는 경우 `AdviseBroadcastMessages` (Visual Studio shell)를 사용 하 여 `WM_SYSCOLORCHANGE` 및 `WM_THEMECHANGED` 메시지를 수신 해야 합니다.

네이티브 코드에서 색 서비스에 액세스 하려면 다음과 같은 호출을 수행 합니다.

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `GetVSSysColorEx()`에서 반환 하는 `COLORREF` 값에는 테마 색의 R, G, B 구성 요소만 포함 됩니다. 테마 항목에서 투명도를 사용 하는 경우를 반환 하기 전에 알파 채널 값을 삭제 합니다. 따라서 관심 있는 환경 색을 투명도 채널이 중요 한 위치에 사용 해야 하는 경우이 항목의 뒷부분에 설명 된 대로 `IVsUIShell2::GetVSSysColorEx`대신 `IVsUIShell5.GetThemedColor`를 사용 해야 합니다.

##### <a name="from-managed-code"></a>관리 코드에서

네이티브 코드를 통해 VSColor 서비스에 액세스 하는 것은 매우 간단 합니다. 그러나 관리 코드를 사용 하 여 작업 하는 경우에는 서비스를 사용 하는 방법을 결정 하기가 어려울 수 있습니다. 이를 염두에 두면 다음 과정을 C# 보여 주는 코드 조각입니다.

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

Visual Basic에서 작업 하는 경우 다음을 사용 합니다.

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF UI에서

응용 프로그램의 `ResourceDictionary`로 내보낸 값을 통해 Visual Studio 색에 바인딩할 수 있습니다. 다음은 color 테이블의 리소스를 사용 하는 방법과 XAML의 환경 글꼴 데이터에 바인딩하는 예입니다.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>관리 코드에 대 한 도우미 클래스 및 메서드

관리 코드의 경우 셸의 관리 되는 패키지 프레임 워크 라이브러리 (`Microsoft.VisualStudio.Shell.12.0.dll`)에는 테마가 적용 된 색의 사용을 용이 하 게 하는 몇 가지 도우미 클래스가 포함 되어 있습니다.

MPF에서 `Microsoft.VisualStudio.Shell.VsColors` 클래스의 도우미 메서드는 `GetThemedGDIColor()` 및 `GetThemedWPFColor()`를 포함 합니다. 이러한 도우미 메서드는 테마 항목의 색 값을 WinForms 또는 WPF UI에서 사용할 `System.Drawing.Color` 또는 `System.Windows.Media.Color`로 반환 합니다.

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

`VsColors` 클래스의 메서드는 VSColor 서비스를 쿼리하여 호출 될 때마다 색 값을 반환 합니다. 색 값을 `System.Drawing.Color`으로 얻으려면 더 나은 성능 대신 VSColor 서비스에서 가져온 색 값을 캐시 하는 `Microsoft.VisualStudio.PlatformUI.VSThemeColor` 클래스의 메서드를 대신 사용 하는 것이 좋습니다. 클래스는 내부적으로 셸 브로드캐스트 메시지 이벤트를 구독 하 고, 테마 변경 이벤트가 발생할 때 캐시 된 값을 삭제 합니다. 또한 클래스는를 제공 합니다. 테마 변경 내용을 구독할 수 있는 NET 친화적인 이벤트입니다. `ThemeChanged` 이벤트를 사용 하 여 새 처리기를 추가 하 고 `GetThemedColor()` 메서드를 사용 하 여 원하는 `ThemeResourceKeys`의 색 값을 가져옵니다. 샘플 코드는 다음과 같습니다.

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

## <a name="BKMK_ChoosingHighContrastColors"></a>고대비 색 선택

### <a name="overview"></a>개요

Windows에서는 텍스트, 배경 및 이미지의 색 대비를 높이는 여러 고대비 시스템 수준 테마를 사용 하 여 요소가 화면에 더 뚜렷이 표시 되도록 합니다. 내게 필요한 옵션을 위해 사용자가 고대비 테마로 전환할 때 Visual Studio 인터페이스 요소가 올바르게 응답 하는 것이 중요 합니다.

고대비 테마에는 몇 가지 시스템 색상만 사용할 수 있습니다. 시스템 색 이름을 선택할 때 다음 팁을 명심 하세요.

- 강조 표시 하는 요소와 **의미 체계가 동일한 시스템 색을 선택** 합니다. 예를 들어 창 내의 텍스트에 대해 고대비 색을 선택 하는 경우에는 WindowText를 사용 하 고 ControlText는 사용 하지 마십시오.

- **전경/배경 쌍** 을 함께 선택 하거나 색 선택이 모든 고대비 테마에서 작동 한다는 확신을 주지 않습니다.

- **UI에서 가장 중요 한 부분을 확인 하 고 콘텐츠 영역을 확장 해야 합니다.** 색 색상의 미묘한 차이로 인해 일반적으로 구분 되는 많은 세부 정보가 손실 됩니다. 따라서 다양 한 콘텐츠 영역에 대 한 색 변형이 없기 때문에 강력한 테두리 색을 사용 하 여 콘텐츠 영역을 정의 하는 것이 일반적입니다.

### <a name="system-color-set"></a>시스템 색 집합

[WPF 팀 블로그: SystemColors 참조](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) 의 표는 시스템 색 이름의 전체 집합과 각 테마에 표시 되는 해당 색상을 나타냅니다.

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
| ControlText | -콤보 상자 및 드롭다운 목록 문자 모양<br />-도구 창 선택 하지 않은 탭 텍스트 |
| GrayText |-콤보 상자 및 드롭다운 목록 사용 안 함 테두리, 드롭다운 문자 모양, 텍스트 및 메뉴 항목 텍스트<br />-사용 안 함 메뉴 텍스트<br />-검색 컨트롤 ' 검색 옵션 ' 헤더 텍스트<br />-검색 컨트롤 섹션 구분 기호 |
| 하이라이트 | -콤보 상자 드롭다운 단추 배경 및 문서 웰 오버플로 단추 테두리를 제외 하 고 모든 마우스로 가리키고 누른 상태 배경 및 테두리<br />-선택한 항목 배경 |
| HighlightText | -모든 가리키기 및 누름 foregrounds (텍스트 및 문자 모양)<br />-포커스가 있는 도구 창 및 문서 탭 창 컨트롤 전경<br />-포커스가 있는 도구 창 제목 표시줄 테두리<br />-포커스가 있는 provisional 탭 전경<br />-문서 웰 오버플로 단추 테두리 가리키기 및 누르기<br />-선택한 아이콘 테두리|
| HotTrack | -누름 스크롤 막대 thumb 배경 및 테두리 누름<br />-누를 때 스크롤 막대 화살표 문자 모양 |
| InactiveCaption | -비활성 IDE 및 rafted 창 단추 문자 모양 가리키기<br />-IDE 및 rafted 창의 제목 표시줄 배경<br />-사용 하지 않도록 설정 된 검색 컨트롤 배경 |
| InactiveCaptionText | -비활성 IDE 및 rafted windows 제목 표시줄 전경 (텍스트 및 문자 모양)<br />-비활성 창 단추 배경 및 테두리 가리키기<br />-포커스가 없는 도구 창 단추 배경 및 테두리<br />-사용 하지 않도록 설정 된 검색 컨트롤 전경 |
| 메뉴 | -드롭다운 메뉴 배경<br />-검사 및 사용 안 함 확인 표시 배경 |
| 확장 | -드롭다운 메뉴 테두리<br />-확인 표시<br />-메뉴 문자 모양<br />-드롭다운 메뉴 텍스트<br />-선택한 아이콘 테두리 |
| 스크롤 막대 | -스크롤 막대 및 스크롤 막대 화살표 배경, 모든 상태 |
| 시간 범위 | -자동 숨기기 탭 배경<br />-메뉴 모음 및 명령 선반 배경<br />-Open 및 provisional 탭 모두에 대해 포커스가 없는 또는 선택 하지 않은 문서 창 탭 배경 및 문서 테두리<br />-포커스가 없는 도구 창 제목 표시줄 배경<br />-도구 창 탭 배경, 선택 및 선택 취소 |
| WindowFrame | -IDE 테두리 |
| WindowText | -탭 전경 자동 숨기기<br />-선택한 도구 창 탭 전경<br />-포커스가 없는 document window tab and 포커스가 없는 또는 선택 하지 않은 provisional 탭 전경<br />-트리 뷰 기본 전경 및 선택 되지 않은 문자 모양 위로 가리키기<br />-도구 창 선택한 탭 테두리<br />-스크롤 막대 thumb 배경, 테두리 및 문자 모양 |

## <a name="BKMK_ExposingColorsForEndUsers"></a>최종 사용자에 대 한 색 노출

### <a name="overview"></a>개요

코드 편집기 또는 디자인 화면을 만들 때와 같이 최종 사용자가 UI를 사용자 지정할 수 있도록 하려는 경우가 있습니다. 이 작업을 수행 하는 가장 일반적인 방법은 **도구 &gt; 옵션** 대화 상자를 사용 하는 것입니다. 특수 컨트롤이 필요한 매우 특수 한 UI가 없는 경우 사용자 지정을 제공 하는 가장 쉬운 방법은 대화 상자의 **환경** 섹션 내 **글꼴 및 색** 페이지를 사용 하는 것입니다. 사용자는 사용자 지정을 위해 노출 하는 각 요소에 대해 전경색, 배경색 또는 둘 다를 변경 하도록 선택할 수 있습니다.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>사용자 지정 가능한 색에 대 한 VSPackage 빌드

VSPackage는 글꼴 및 색 속성 페이지에서 사용자 지정 범주와 표시 항목을 통해 글꼴 및 색을 제어할 수 있습니다. 이 메커니즘을 사용 하는 경우 Vspackage는 [Ivsfontandcolordefaultsprovider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) 인터페이스 및 관련 된 인터페이스를 구현 해야 합니다.

원칙적으로이 메커니즘을 사용 하 여 기존의 모든 표시 항목과 해당 항목을 포함 하는 범주를 수정할 수 있습니다. 그러나 텍스트 편집기 범주 또는 표시 항목을 수정 하는 데 사용 하면 안 됩니다. 텍스트 편집기 범주에 대 한 자세한 내용은 [글꼴 및 색 개요](/visualstudio/extensibility/font-and-color-overview?view=vs-2015)를 참조 하세요.

사용자 지정 범주 또는 표시 항목을 구현 하려면 VSPackage가 다음을 수행 해야 합니다.

- **레지스트리에서 범주를 만들거나 식별 합니다.** **글꼴 및 색** 속성 페이지의 IDE 구현에서는이 정보를 사용 하 여 지정 된 범주를 지 원하는 서비스를 올바르게 쿼리 합니다.

- **레지스트리에서 그룹을 만들거나 식별 합니다 (선택 사항).** 두 개 이상의 범주의 합집합을 나타내는 그룹을 정의 하는 것이 유용할 수 있습니다. 그룹이 정의 된 경우 IDE는 자동으로 하위 범주를 병합 하 고 그룹 내에 표시 항목을 배포 합니다.

- **IDE 지원을 구현 합니다.**

- **글꼴 및 색 변경을 처리 합니다.**

#### <a name="to-create-or-identify-categories"></a>범주를 만들거나 식별 하려면

`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]`에서 특수 한 종류의 범주 레지스트리 항목을 생성 합니다. 여기서 `<Category>`는 범주의 지역화 되지 않은 이름입니다.

레지스트리를 다음 두 값으로 채웁니다.

| 속성 | Type | data | Description |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | 범주를 식별 하기 위해 만든 GUID입니다. |
| 패키지 | REG_SZ | GUID | 범주를 지 원하는 VSPackage 서비스의 GUID입니다. |

 레지스트리에 지정 된 서비스는 해당 범주에 대해 [Ivsfontandcolordefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 구현을 제공 해야 합니다.

#### <a name="to-create-or-identify-groups"></a>그룹을 만들거나 식별 하려면

`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]`에서 특수 한 종류의 범주 레지스트리 항목을 생성 합니다. 여기서 `<group>`는 그룹의 지역화 되지 않은 이름입니다.

레지스트리를 다음 두 값으로 채웁니다.

| 속성 | Type | data | Description |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | 범주를 식별 하기 위해 만든 GUID입니다. |
| 패키지 | REG_SZ | GUID | 범주를 지 원하는 VSPackage 서비스의 GUID입니다. |

레지스트리에 지정 된 서비스는 해당 그룹에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 구현을 제공 해야 합니다.

![IVsFontAndColorGroup의 구현](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />`IVsFontAndColorGroup` 구현

### <a name="to-implement-ide-support"></a>IDE 지원을 구현 하려면

지정 된 각 범주 또는 그룹 GUID에 대해 [Ivsfontandcolordefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 인터페이스 또는 IDE에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 인터페이스를 반환 하는 [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject)를 구현 합니다.

VSPackage은 지원 되는 모든 범주에 대해 [Ivsfontandcolordefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 인터페이스의 별도 인스턴스를 구현 합니다.

[Ivsfontandcolordefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 를 통해 구현 된 메서드는 IDE에를 제공 해야 합니다.

- 범주의 표시 항목 목록

- 표시 항목의 지역화할 수 있는 이름

- 범주의 각 구성원에 대 한 정보를 표시 합니다.

> [!NOTE]
> 모든 범주에는 하나 이상의 표시 항목이 포함 되어야 합니다.

IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 인터페이스를 사용 하 여 여러 범주의 합집합을 정의 합니다.

구현에서는 다음과 같이 IDE를 제공 합니다.

- 지정 된 그룹을 구성 하는 범주 목록

- 그룹 내의 각 범주를 지 원하는 [Ivsfontandcolordefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 의 인스턴스에 대 한 액세스

- 지역화 가능한 그룹 이름

#### <a name="updating-the-ide"></a>IDE 업데이트

IDE는 글꼴 및 색 설정에 대 한 정보를 캐시 합니다. 따라서 IDE 글꼴 및 색 구성을 수정한 후 캐시가 최신 상태 인지 확인 하는 것이 가장 좋습니다.

캐시 업데이트는 [Ivsfontandcolorcachemanager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) 인터페이스를 통해 수행 되며, 선택 된 항목에 대해 전역적으로 또는만 수행할 수 있습니다.

### <a name="handling-font-and-color-changes"></a>글꼴 및 색 변경 처리

VSPackage에 표시 되는 텍스트의 색 지정을 제대로 지원 하려면 VSPackage를 지 원하는 색 지정 서비스에서 글꼴 및 색 속성 페이지를 통해 사용자가 시작한 변경 내용에 응답 해야 합니다.

이렇게 하려면 VSPackage에서 다음을 수행 해야 합니다.

- [Ivsfontandcolorevents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) 인터페이스를 구현 하 여 **IDE에서 생성 된 이벤트를 처리** 합니다. IDE는 글꼴 및 색 페이지의 사용자 수정에 따라 적절 한 메서드를 호출 합니다. 예를 들어 새 글꼴이 선택 된 경우 [On글꼴 changed](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) 메서드를 호출 합니다.

  **OR**

- **변경 내용에 대 한 IDE를 폴링합니다**. 시스템 구현 [Ivsfontandcolorstorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) 인터페이스를 통해이 작업을 수행할 수 있습니다. 주로 지 속성 지원을 위해 [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) 메서드는 표시 항목의 글꼴 및 색 정보를 가져올 수 있습니다. 글꼴 및 색 설정에 대 한 자세한 내용은 MSDN 문서 [저장 된 글꼴 및 색 설정 액세스](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015)를 참조 하세요.

> [!NOTE]
> 폴링 결과가 올바른지 확인 하려면 [Ivsfontandcolorcachemanager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) 인터페이스를 사용 하 여 [Ivsivandcolorstorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) 인터페이스의 검색 메서드를 호출 하기 전에 캐시 플러시 및 업데이트가 필요한 지 확인 합니다.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>인터페이스를 구현 하지 않고 사용자 지정 글꼴 및 색 범주 등록

다음 코드 예제에서는 인터페이스를 구현 하지 않고 사용자 지정 글꼴 및 색 범주를 등록 하는 방법을 보여 줍니다.

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

이 코드 예제는 다음과 같습니다.

- `"NameID"` = 패키지의 지역화 된 범주 이름에 대 한 리소스 ID
- `"ToolWindowPackage"` = 패키지 GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` 단지 예제 이며 실제 값은 구현자에서 제공 하는 새 GUID 일 수 있습니다.

### <a name="set-the-font-and-color-property-category-guid"></a>글꼴 및 색 속성 범주 GUID를 설정 합니다.

아래 코드 예제에서는 범주 Guid를 설정 하는 방법을 보여 줍니다.

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
