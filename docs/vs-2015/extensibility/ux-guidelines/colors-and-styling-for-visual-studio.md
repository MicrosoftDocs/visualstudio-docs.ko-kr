---
title: 색 및 스타일 지정
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0330ef80fc1127893590ef8d326cb5b8e0cf0160
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301346"
---
# <a name="colors-and-styling-for-visual-studio"></a>Visual Studio의 색 및 스타일 지정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>비주얼 스튜디오에서 색상 사용
 Visual Studio에서 색상은 주로 장식이 아닌 통신 도구로 사용됩니다. 색상을 최소한으로 사용하고 다음을 수행하려는 상황에 대비하여 색상을 예약합니다.

- 의미 또는 소속 전달(예: 플랫폼 또는 언어 수정자)

- 주의력 끌기(예: 상태 변경 표시)

- 가독성을 개선하고 UI 탐색을 위한 랜드마크 제공

- 바람직성 향상

  Visual Studio의 UI 요소에 색상을 할당하기 위한 몇 가지 옵션이 있습니다. 때로는 어떤 옵션을 사용해야 하는지 또는 올바르게 사용하는 방법을 파악하기가 어려울 수 있습니다. 이 항목은 다음과 같은 데 도움이 됩니다.

1. Visual Studio에서 색상을 정의하는 데 사용되는 다양한 서비스와 시스템을 이해합니다.

2. 지정된 요소에 대해 올바른 옵션을 선택합니다.

3. 선택한 옵션을 올바르게 사용합니다.

   **중요 사항:** UI 요소에 육신, RGB 또는 시스템 색상을 하드코딩하지 마십시오. 이 서비스를 사용하면 색조를 유연게 조정할 수 있습니다. 또한 서비스가 없으면 [VSColor 서비스의](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)테마 전환 기능을 활용할 수 없습니다.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio 인터페이스 요소에 색상을 할당하는 방법
 UI 요소에 가장 적합한 방법을 선택합니다.

|Your UI|방법|그들은 무엇입니까?|
|-------------|------------|--------------------|
|포함된 대화 상자 또는 독립 실행형 대화 상자가 있습니다.|**시스템 색상**|운영 체제에서 일반적인 대화 상자 컨트롤과 같이 UI 요소의 색상과 모양을 정의할 수 있는 시스템 이름입니다.|
|전체 VS 환경과 일치하도록 하려는 사용자 지정 UI가 있고 공유 토큰의 범주 및 의미 체계 의미와 일치하는 UI 요소가 있습니다.|**공통 공유 색상**|특정 UI 요소에 대해 미리 정의된 기존 색상 토큰 이름|
|개별 피쳐 또는 피쳐 그룹이 있으며 유사한 요소에 대한 공유 색상이 없습니다.|**사용자 지정 색**|영역에 특정하고 다른 UI와 공유하기 위한 것이 아닌 색상 토큰 이름|
|최종 사용자가 UI 또는 콘텐츠(예: 텍스트 편집기 또는 특수 디자이너 창)를 사용자 지정하도록 허용하려고 합니다.|**최종 사용자 사용자 지정**<br /><br /> **(옵션 대화 상자와 > 도구)**|**도구 > 옵션** 대화 상자의 "글꼴 및 색상" 페이지에 정의된 설정 또는 하나의 UI 기능에 특정한 특수 페이지입니다.|

### <a name="visual-studio-themes"></a>비주얼 스튜디오 테마
 비주얼 스튜디오는 세 가지 다른 색상 테마를 갖추고 있습니다 : 빛, 어두운, 파란색 . 또한 접근성을 위해 설계된 시스템 전체 색상 테마인 고대비 모드를 감지합니다.

 사용자는 Visual Studio를 처음 사용하는 동안 테마를 선택하라는 메시지가 표시되며 나중에 일반 환경 > **도구 > 옵션 >** 이동하여 테마를 전환할 수 > "색상 테마" 드롭다운 메뉴에서 새 테마를 선택할 수 있습니다.

 또한 사용자는 제어판을 사용하여 전체 시스템을 여러 고대비 테마 중 하나로 전환할 수 있습니다. 사용자가 고대비 테마를 선택하면 사용자가 고대비 모드를 종료할 때 테마 변경 내용이 저장되지만 Visual Studio 색상 테마 선택기는 더 이상 Visual Studio의 색상에 영향을 주지 않습니다. 고대비 모드에 대한 자세한 내용은 [고대비 색상 선택을](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)참조하십시오.

### <a name="the-vscolor-service"></a>VSColor 서비스
 Visual Studio는 VSColor 서비스라고 하는 환경 색상 서비스를 제공하므로 UI 요소의 색상 값을 각 Visual Studio 테마에 대한 색상 값을 포함하는 명명된 항목에 바인딩할 수 있습니다. 이렇게 하면 색상이 자동으로 변경되어 현재 사용자가 선택한 테마 또는 시스템 고대비 모드를 반영합니다. 이 서비스를 사용하면 모든 테마 관련 색상 변경 사항을 한 곳에서 구현할 수 있으며 서비스에서 공통 공유 색상을 사용하는 경우 UI가 이후 버전의 Visual Studio에 새 테마를 자동으로 반영합니다.

### <a name="implementation"></a>구현
 Visual Studio 소스 코드에는 토큰 이름 목록과 각 테마에 대한 각 색상 값이 포함된 여러 패키지 정의 파일이 포함되어 있습니다. 색상 서비스는 이러한 패키지 정의 파일에 정의된 VSColors를 읽습니다. 이러한 색상은 XAML 태그 또는 코드에서 참조된 다음 **IVsUIShell5.GetThemedColor** 메서드 또는 DynamicResource 매핑을 통해 로드됩니다.

### <a name="system-colors"></a>시스템 색상
 공통 컨트롤은 기본적으로 시스템 색상을 참조합니다. 포함된 대화 상자나 독립 실행형 대화 상자를 만들 때와 같이 UI에서 시스템 색상을 사용하려면 아무 것도 수행할 필요가 없습니다.

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor 서비스의 공통 공유 색상
 인터페이스 요소는 전체 Visual Studio 환경을 반영해야 합니다. 디자인하는 UI 구성 요소에 적합한 공통 공유 색상을 다시 사용하면 인터페이스가 다른 Visual Studio 인터페이스와 일치하고 테마가 추가되거나 업데이트될 때 색상이 자동으로 업데이트되도록 합니다.

 공통 공유 색상을 사용하기 전에 색상을 올바르게 사용하는 방법을 이해해야 합니다. 공통 공유 색상을 잘못 사용하면 사용자에게 일관성이 없거나 실망스럽거나 혼란스러운 환경이 발생할 수 있습니다.

### <a name="user-customizable-colors"></a>사용자 지정 가능한 색상
 참조: [최종 사용자를 위한 색상 노출](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

 코드 편집기 또는 디자인 표면을 만들 때와 같이 최종 사용자가 UI를 사용자 지정하도록 허용하는 경우가 있습니다. 사용자 지정 가능한 UI 구성 요소는 도구 > **옵션** 대화 상자의 **글꼴 및 색상** 섹션에서 찾을 수 있으며, 여기서 사용자는 전경 색상, 배경 색 또는 둘 다를 변경할 수 있습니다.

 ![비주얼 스튜디오에서 도구 &#62; 옵션 대화 상자](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")

 **도구>옵션 대화 상자**

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>VS컬러 서비스
 Visual Studio는 VSColor 서비스 또는 셸 색상 서비스라고도 하는 환경 색상 서비스를 제공합니다. 이 서비스를 사용하면 UI 요소의 색상 값을 각 테마의 색상을 포함하는 이름 값 색상 집합에 바인딩할 수 있습니다. VSColor 서비스는 모든 UI 요소에 사용해야 하므로 색상이 자동으로 변경되어 현재 사용자가 선택한 테마를 반영하고 환경 색상 서비스에 바인딩된 UI가 이후 버전의 Visual Studio에서 새 테마와 통합되도록 해야 합니다.

### <a name="how-the-service-works"></a>서비스의 작동 방식
 환경 색상 서비스는 UI 구성 요소에 대한 .pkgdef에 정의된 VSColors를 읽습니다. 그런 다음 이러한 VSColors는 XAML 태그 또는 코드에서 참조되며 **IVsUIShell5.GetThemedColor** 또는 DynamicResource 매핑을 통해 로드됩니다.

 ![환경 색 서비스 아키텍처](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")

 **환경 색 서비스 아키텍처**

### <a name="accessing-the-service"></a>서비스 액세스
 사용 중인 색상 토큰의 종류와 코드 종류에 따라 VSColor 서비스에 액세스하는 방법에는 여러 가지가 있습니다.

#### <a name="predefined-environment-colors"></a>미리 정의된 환경 색상

##### <a name="from-native-code"></a>네이티브 코드에서
 셸은 색상의 COLORREF에 대한 액세스를 제공하는 서비스를 제공합니다. 서비스/인터페이스는 다음과 같은 것입니다.

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

 파일 VSShell80.idl에서 열거 **__VSSYSCOLOREX** 쉘 색상 상수가 있습니다. 이를 사용하려면 MSDN에 설명된 열거형 __VSSYSCOLOREX 값 중 하나 또는 Windows 시스템 **API인 GetSysColor가**허용하는 일반 인덱스 번호 중 하나를 인덱스 값으로 전달합니다. 이렇게 하면 두 번째 매개 변수에 사용해야 하는 색상의 RGB 값이 다시 표시됩니다.

 새 색상으로 펜이나 브러시를 저장하는 경우 Visual Studio 셸에서 벗어나 서 브로드캐스트 메시지를 사용하며 WM_SYSCOLORCHANGE 및 WM_THEMECHANGED 메시지를 수신해야 합니다.

```
// To access the color service in native code, you'll make a call that resembles this:
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);

```

 **참고:** **GetVSSysColorEx()에서** 반환된 COLORREF 값에는 테마 색상의 R, G, B 구성 요소만 포함되어 있습니다. 테마 항목에서 투명도를 사용하는 경우 알파 채널 값은 반환하기 전에 삭제됩니다. 따라서 투명도 채널이 중요한 장소에서 환경 색상을 사용해야 하는 경우 이 항목의 후반부에서 설명한 대로 IVsUIShell2:GetVSSysColorEx 대신 IVsUIShell5.GetThemedColor를 사용해야 합니다.

##### <a name="from-managed-code"></a>관리 코드에서
 네이티브 코드를 통해 VSColor 서비스에 액세스하는 것은 매우 간단합니다. 그러나 관리 코드를 통해 작업하는 경우 서비스를 사용하는 방법을 결정하는 것이 까다로울 수 있습니다. 이 점을 염두에 두고 이 프로세스를 보여 주는 C# 코드 조각은 다음과 같습니다.

```
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

 비주얼 베이직에서 작업하는 경우 다음을 사용합니다.

```
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF UI에서
 응용 프로그램의 ResourceDictionary로 내보낸 값을 통해 Visual Studio 색상에 바인딩할 수 있습니다. 다음은 색상 테이블의 리소스를 사용하고 XAML의 환경 글꼴 데이터에 바인딩하는 예제입니다.

```
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
 관리되는 코드의 경우 셸의 관리되는 패키지 프레임워크 라이브러리(Microsoft.VisualStudio.Shell.12.0.dll)에는 테마 색상 사용을 용이하게 하는 몇 가지 도우미 클래스가 포함되어 있습니다.

 **MPF의 Microsoft.VisualStudio.Shell.VsColors** 클래스의 도우미 메서드에는 **GetThemedGDIColor()** 및 **GetThemedWPFColor()** 등이 있습니다. 이러한 도우미 메서드는 WinForms 또는 WPF UI에서 사용할 수 있는 System.Drawing.Color.Color 또는 System.Windows.Media.Color로 테마 항목의 색상 값을 반환합니다.

```
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

 클래스는 지정된 WPF 색상 리소스 키에 대한 VSCOLOR 식별자를 가져오는 데 사용하거나 그 반대의 경우도 마찬가지입니다.

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

 **VsColors** 클래스의 메서드는 VSColor 서비스를 쿼리하여 호출될 때마다 색상 값을 반환합니다. **System.Drawing.Color로**색상 값을 얻으려면 더 나은 성능을 가진 대안은 대신 VSColor 서비스에서 얻은 색상 값을 캐시하는 **Microsoft.VisualStudio.PlatformUI.VSThemeColor** 클래스의 메서드를 사용하는 것입니다. 클래스는 셸 브로드캐스트 메시지 이벤트에 내부적으로 구독하고 테마 변경 이벤트가 발생하면 캐시된 값을 삭제합니다. 또한 클래스는 을 제공합니다. 테마 변경 사항을 구독하는 NET 친화적 인 이벤트. 테마 **변경** 이벤트를 사용하여 새 처리기를 추가하고 **GetThemedColor()** 메서드를 사용하여 관심 있는 **테마리소스 키에** 대한 색상 값을 가져옵니다. 샘플 코드는 다음과 같습니다.

```
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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>고대비 색상 선택

### <a name="overview"></a>개요
 Windows는 텍스트, 배경 및 이미지의 색상 대비를 높이는 몇 가지 고대비 시스템 수준 테마를 사용하여 요소가 화면에 더 뚜렷하게 나타납니다. 접근성상의 이유로 사용자가 고대비 테마로 전환할 때 Visual Studio 인터페이스 요소가 올바르게 응답하는 것이 중요합니다.

 고대비 테마에는 소수의 시스템 색상만 사용할 수 있습니다. 시스템 색상 이름을 선택할 때 다음 팁을 기억하십시오.

1. 색칠하는 요소와 **의미 체계 의미가 같은 시스템 색상을 선택합니다.** 예를 들어 창 내의 텍스트에 대해 대비가 높은 색상을 선택하는 경우 ControlText가 아닌 WindowText를 사용합니다.

2. **전경 /배경 쌍을** 함께 선택하거나 색상 선택이 모든 고대비 테마에서 작동할 것이라고 확신하지 못할 것입니다.

3. **UI의 어떤 부분이 가장 중요한지 확인하고 콘텐츠 영역이 두드러지도록 합니다.** 색상 색조의 미묘한 차이가 일반적으로 구별되는 세부 사항을 많이 잃게 되므로 다른 콘텐츠 영역에 대한 색상 변형이 없기 때문에 강한 테두리 색상을 사용하여 콘텐츠 영역을 정의하는 것이 일반적입니다.

### <a name="system-color-set"></a>시스템 색상 세트
 [WPF 팀 블로그: SystemColors 참조의](https://devblogs.microsoft.com/wpf/systemcolors-reference/) 표는 시스템 색상 이름의 전체 집합과 각 테마에 표시되는 해당 색조를 나타냅니다.

 UI에 이 제한된 색상 집합을 적용할 때 *"일반" 테마에 있던 미묘한 세부 정보가 손실될 것으로 예상됩니다.* 다음은 도구 창 내의 영역을 구분하는 데 사용되는 미묘한 회색 색상의 UI의 예입니다. 고대비 모드로 표시된 동일한 창과 페어링하면 모든 배경이 동일한 색조이고 해당 영역의 테두리가 테두리만 으로 표시되는 것을 볼 수 있습니다.

 ![속성 창](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303-a_PropertiesWindow")

 **고대비에서 미묘한 세부 사항이 손실되는 방법의 예**

#### <a name="choosing-text-colors-in-an-editor"></a>편집기에서 텍스트 색상 선택
 색상이 있는 텍스트는 편집기 또는 디자인 표면에 사용되어 유사한 항목 그룹을 쉽게 식별할 수 있도록 하는 등의 의미를 나타냅니다. 그러나 고대비 테마에서는 세 개 이상의 텍스트 색상을 구분할 수 없습니다. 창텍스트, 그레이텍스트 및 핫트랙텍스트는 창백서열 표면에서 사용할 수 있는 유일한 색상입니다. 세 가지 이상의 색상을 사용할 수 없으므로 고대비 모드에서 표시할 가장 중요한 차이점을 신중하게 선택합니다.

 각 고대비 테마에 나타나는 각 토큰 이름에 대한 색조는 편집기 표면에서 허용됩니다.

 ![고대비 편집기 비교](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303-b_HCEditorComparison")

 **고대비 편집기 비교**

 파란색 테마의 편집기 표면의 예:

 ![파란색 테마의 편집기](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303-c_EditorBlue")

 **파란색 테마의 편집기**

 ![고대비 테마의 편집기](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303-d_EditorHC1")

 **고대비 #1 테마의 편집자**

### <a name="usage-patterns"></a>사용 패턴
 많은 일반적인 UI 요소에는 이미 고대비 색상이 정의되어 있습니다. 고유한 시스템 색상 이름을 선택할 때 이러한 사용 패턴을 참조하여 UI 요소가 유사한 구성 요소와 일치되도록 할 수 있습니다.

|시스템 색상|사용|
|------------------|-----------|
|ActiveCaption|- 호버에 활성 IDE 및 래프팅 창 버튼 문말<br />- IDE 및 래프팅 된 창에 대한 제목 표시 줄 배경<br />- 기본 상태 표시줄 배경|
|ActiveCaptionText|- 타이틀 바 전경 (텍스트 및 문자 문야)에 대한 활성 IDE 및 래프팅 창<br />- 가리키고 누르면 활성 창 버튼의 배경과 테두리|
|제어|- 콤보 상자, 드롭 다운 목록, 드롭 다운 버튼을 포함하여 설정 설정 및 비활성화 된 배경, 검색 컨트롤 기본 및 비활성화 된 배경<br />- 도크 대상 버튼 배경<br />- 명령 바 배경<br />- 도구 창 배경|
|ControlDark|- IDE 배경<br />- 메뉴 및 명령 바 구분 기호<br />- 명령 바 테두리<br />- 메뉴 그림자<br />- 도구 창 탭 기본 및 호버 테두리 와 구분 기호<br />- 문서 잘 오버 플로우 버튼 배경<br />- 도크 대상 문말 테두리|
|ControlDarkDark|- 포커스가 없는 선택된 문서 탭 창|
|ControlLight|- 자동 숨기기 탭 테두리<br />- 콤보 상자 및 드롭 다운 목록 테두리<br />- 도크 대상 배경 및 테두리|
|컨트롤라이트라이트|- 선택된 초점 임시 테두리|
|컨트롤 텍스트|- 콤보 상자 및 드롭 다운 목록 문입니다<br />- 도구 창 선택되지 않은 탭 텍스트|
|그레이 텍스트|- 콤보 상자 및 드롭 다운 목록 비활성화 테두리, 드롭 다운 문자, 텍스트 및 메뉴 항목 텍스트<br />- 비활성화 된 메뉴 텍스트<br />- 검색 제어 '검색 옵션'헤더 텍스트<br />- 검색 제어 섹션 구분 기호|
|하이라이트|- 콤보 상자 드롭 다운 버튼 배경 및 문서 잘 오버 플로우 버튼 테두리를 제외하고 모든 호버 및 누른 배경과 테두리<br />- 선택한 항목 배경|
|하이라이트텍스트|- 모든 호버 및 누른 전경 (텍스트 및 문자 문야)<br />- 포커스 도구 창 및 문서 탭 창 제어 전경<br />- 초점을 맞춘 도구 창 제목 표시 줄 테두리<br />- 포커스, 선택된 임시 탭 전경<br />- 호버에 잘 오버 플로우 버튼 테두리를 누르고<br />- 선택한 아이콘 테두리|
|핫트랙|- 스크롤 바 엄지 손가락 배경과 테두리에 눌러<br />- 누를 때 스크롤 막대 화살표|
|비활성 캡션|- 비활성 IDE 및 래프팅 창 버튼 문말 호버에<br />- IDE 및 래프팅 된 창에 대한 제목 표시 줄 배경<br />- 비활성화 된 검색 컨트롤 배경|
|비활성 캡션텍스트|- 비활성 IDE 및 래프팅 된 창 제목 표시 줄 전경 (텍스트 및 문자 문표)<br />- 비활성 창 버튼 배경과 호버에 테두리<br />- 초점이 맞지 않는 도구 창 버튼 배경 및 테두리<br />- 비활성화 된 검색 제어 전경|
|메뉴|- 드롭다운 메뉴 배경<br />- 선택 및 비활성화 된 체크 표시 배경|
|메뉴 텍스트|- 드롭다운 메뉴 테두리<br />- 체크 표시 확인<br />- 메뉴 문말<br />- 드롭 다운 메뉴 텍스트<br />- 선택한 아이콘 테두리|
|스크롤 막대|- 스크롤 막대 및 스크롤 막대 화살표 배경, 모든 상태|
|시간 범위|- 자동 숨기기 탭 배경<br />- 메뉴 바 및 명령 선반 배경<br />- 열려 있는 탭과 임시 탭 모두에 대해 포커스가 없거나 선택되지 않은 문서 창 탭 배경 및 문서 테두리<br />- 초점이 맞지 않는 도구 창 제목 표시줄 배경<br />- 도구 창 탭 배경, 모두 선택및 선택되지 않은|
|윈도우 프레임|- IDE 테두리|
|윈도우 텍스트|- 자동 숨기기 탭 전경<br />- 선택한 도구 창 탭 전경<br />- 포커스가 없는 문서 창 탭 및 포커스가 없거나 선택되지 않은 임시 탭 전경<br />- 트리뷰 기본 전경 및 선택되지 않은 글리프 위로 마우스를 가져가기<br />- 도구 창 선택 탭 테두리<br />- 스크롤 바 엄지 손가락 배경, 테두리, 글리프|

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>최종 사용자를 위한 색상 노출

### <a name="overview"></a>개요
 코드 편집기 또는 디자인 표면을 만들 때와 같이 최종 사용자가 UI를 사용자 지정하도록 허용하는 경우가 있습니다. 이 작업을 수행하는 가장 일반적인 방법은 **도구 > 옵션** 대화 상자를 사용하는 것입니다. 특수 컨트롤이 필요한 고도로 전문화된 UI가 없는 한 사용자 지정을 표시하는 가장 쉬운 방법은 대화 상자의 **환경** 섹션 내의 **글꼴 및 색상** 페이지를 사용하는 것입니다. 사용자 지정을 위해 노출하는 각 요소에 대해 사용자는 전경 색상, 배경 색 또는 둘 다를 변경하도록 선택할 수 있습니다.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>사용자 정의 가능한 색상을 위한 VS패키지 구축
 VSPackage는 사용자 지정 범주를 통해 글꼴 및 색상을 제어하고 글꼴 및 색상 속성 페이지에 항목을 표시할 수 있습니다. 이 메커니즘을 사용하는 경우 VSPackage는 [IVsFontAndColorDefaults공급자](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) 인터페이스와 관련 인터페이스를 구현해야 합니다.

 원칙적으로 이 메커니즘은 모든 기존 표시 항목과 해당 항목을 포함하는 범주를 수정하는 데 사용할 수 있습니다. 그러나 텍스트 편집기 범주 또는 표시 항목을 수정하는 데 사용해서는 안 됩니다. 텍스트 편집기 범주에 대한 자세한 내용은 [글꼴 및 색상 개요를](https://msdn.microsoft.com/library/bb165065.aspx)참조하십시오.

 사용자 지정 범주를 구현하거나 항목을 표시하려면 VSPackage는 다음을 수행해야 합니다.

- **레지스트리에서 범주를 만들거나 식별합니다.** IDE의 **글꼴 및 색상** 속성 페이지 구현은 이 정보를 사용하여 지정된 범주를 지원하는 서비스를 올바르게 쿼리합니다.

- **레지스트리에서 그룹을 만들거나 식별합니다(선택 사항).** 둘 이상의 범주의 결합을 나타내는 그룹을 정의하는 것이 유용할 수 있습니다. 그룹이 정의된 경우 IDE는 하위 범주를 자동으로 병합하고 그룹 내에서 표시 항목을 배포합니다.

- **IDE 지원을 구현합니다.**

- **글꼴 및 색상 변경 사항을 처리합니다.**

#### <a name="to-create-or-identify-categories"></a>범주를 만들거나 식별하려면
 [HKLM\SOFTWARE\Microsoft\비주얼\\ 스튜디오<비주얼 스튜디오 버전\>\FontAndColors\\<카테고리]에서\>카테고리 레지스트리 항목의 특별한 유형을 구성합니다. \<범주> 범주의 지역화되지 않은 이름입니다.

 레지스트리를 다음 두 값으로 채웁니다.

|속성|Type|데이터|Description|
|----------|----------|----------|-----------------|
|Category|REG_SZ|GUID|범주를 식별하기 위해 만든 GUID|
|패키지|REG_SZ|GUID|범주를 지원하는 VSPackage 서비스의 GUID|

 레지스트리에 지정된 서비스는 해당 범주에 대한 [IVsFontAndColors의 구현을](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 제공해야 합니다.

#### <a name="to-create-or-identify-groups"></a>그룹을 만들거나 식별하려면
 [HKLM\SOFTWARE\Microsoft\비주얼\\ 스튜디오<비주얼 스튜디오 버전\>\FontAndColors\\<그룹]에서\>범주 레지스트리 항목의 특수 유형을 구성합니다. \<그룹> 그룹의 지역화되지 않은 이름입니다.

 레지스트리를 다음 두 값으로 채웁니다.

|속성|Type|데이터|Description|
|----------|----------|----------|-----------------|
|Category|REG_SZ|GUID|범주를 식별하기 위해 만든 GUID|
|패키지|REG_SZ|GUID|범주를 지원하는 VSPackage 서비스의 GUID|

 레지스트리에 지정된 서비스는 해당 그룹에 대한 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup의** 구현을 제공해야 합니다.

 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304-a_FontAndColorGroup")

### <a name="to-implement-ide-support"></a>IDE 지원을 구현하려면
 구현 [GetObject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 인터페이스 또는 **T:마이크로소프트.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 인터페이스를 제공 하는 각 범주 또는 그룹 GUID에 대 한 IDE에 반환 합니다.

 지원하는 모든 범주에 대해 VSPackage는 [IVsFontAndColors](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 인터페이스의 별도의 인스턴스를 구현합니다.

 [IVsFontAndColordefaults를](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 통해 구현 된 방법은 IDE를 제공해야합니다 :

- 범주의 표시 항목 목록

- 표시 항목에 대한 지역화 가능한 이름

- 범주의 각 구성원에 대한 정보 표시

  **참고:** 모든 범주에는 하나 이상의 표시 항목이 포함되어야 합니다.

  IDE는 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 인터페이스를 사용하여 여러 범주의 결합을 정의합니다.

  이 구현은 IDE에 다음을 제공합니다.

- 지정된 그룹을 구성하는 범주 목록

- 그룹 내의 각 범주를 지원하는 [IVsFontAndColordefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 인스턴스에 대한 액세스

- 지역화 가능한 그룹 이름

#### <a name="updating-the-ide"></a>IDE 업데이트
 IDE는 글꼴 및 색상 설정에 대한 정보를 캐시합니다. 따라서 IDE 글꼴 및 색상 구성을 수정한 후 캐시가 최신 상태임을 확인하는 것이 가장 좋습니다.

 캐시 업데이트는 [IvsFontAndColorCacheManager 인터페이스를](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 통해 수행되며 전역적으로 또는 선택한 항목에 대해 수행할 수 있습니다.

### <a name="handling-font-and-color-changes"></a>글꼴 및 색상 변경 처리
 VSPackage가 표시하는 텍스트의 색상화를 제대로 지원하려면 VSPackage를 지원하는 색상 화 서비스가 글꼴 및 색상 속성 페이지를 통해 사용자가 시작한 변경 사항에 응답해야 합니다.

 이렇게 하려면 VSPackage는 다음을 수행해야 합니다.

- [은 IVsFontAndColorEvents](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) 인터페이스를 구현하여 **IDE에서 생성된 이벤트를 처리합니다.** IDE는 글꼴 및 색상 페이지를 사용자가 수정한 후 적절한 방법을 호출합니다. 예를 들어 새 글꼴을 선택한 경우 [OnFontChanged](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) 메서드를 호출합니다.

  **또는**

- **변경 에 대한 IDE를 폴링합니다.** 이것은 시스템 구현 [IVsFontAndColor 저장](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) 인터페이스를 통해 수행 할 수 있습니다. 주로 지속성을 지원하기 위해 [GetItem](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) 메서드는 표시 항목에 대한 글꼴 및 색상 정보를 가져올 수 있습니다. 글꼴 및 색상 설정에 대한 자세한 내용은 [저장된 글꼴 및 색상 설정 에 액세스하는](https://msdn.microsoft.com/library/bb166382.aspx)MSDN 문서를 참조하십시오.

  **참고:** 폴링 결과가 올바른지 확인하려면 IVsFontAndColorStorage 인터페이스의 검색 방법을 호출하기 전에 [IVsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 인터페이스를 사용하여 캐시 플러시 및 업데이트가 필요한지 확인합니다. [IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>인터페이스를 구현하지 않고 사용자 정의 글꼴 및 색상 범주 등록
 다음 코드 예제에서는 인터페이스를 구현하지 않고 사용자 지정 글꼴 및 색상 범주를 등록하는 방법을 보여 줍니다.

```xml
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

 **참고:**

- "NameID" = 패키지에서 지역화된 범주 이름의 리소스 ID

- "도구 창 패키지" = 패키지 GUID

- "카테고리"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"는 예에 불과하며 실제 값은 구현자가 제공하는 새 GUID일 수 있습니다.

### <a name="set-the-font-and-color-property-category-guid"></a>글꼴 및 색상 속성 범주 GUID 설정
 아래 코드 예제에서는 범주 GUID 설정을 보여 줍니다.

```cs
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
  IVsTextEditorPropertyContainer spPropContainer;
  Guid GUID_EditPropCategory_View_MasterSettings =
  new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
  hr = spPropCatContainer.GetPropertyCategory(
  ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer);
  if(hr == 0)
  {
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID);
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID);
  }
}
```
