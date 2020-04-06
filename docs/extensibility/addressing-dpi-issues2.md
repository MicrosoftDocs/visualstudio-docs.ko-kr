---
title: DPI 문제 해결2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740100"
---
# <a name="address-dpi-issues"></a>DPI 문제 해결
점점 더 많은 장치가 "고해상도" 화면으로 배송되고 있습니다. 이러한 화면은 일반적으로 인치당 200픽셀(ppi) 이상을 갖습니다. 이러한 컴퓨터에서 응용 프로그램을 작업하려면 장치의 정상적인 보기 거리에서 콘텐츠를 볼 필요가 있도록 콘텐츠를 확장해야 합니다. 2014년 현재 고밀도 디스플레이의 주요 목표는 모바일 컴퓨팅 장치(태블릿, 클램쉘 랩톱 및 휴대폰)입니다.

Windows 8.1 이상에는 이러한 컴퓨터가 고밀도 및 표준 밀도 디스플레이에 동시에 연결된 디스플레이 및 환경에서 작동할 수 있도록 하는 몇 가지 기능이 포함되어 있습니다.

- Windows를 사용하면 "텍스트 및 기타 항목을 더 크거나 작게 만들기" 설정을 사용하여 장치에 콘텐츠를 확장할 수 있습니다(Windows XP 이후 사용 가능).

- Windows 8.1 이상은 픽셀 밀도가 다른 디스플레이 간에 이동할 때 대부분의 응용 프로그램이 일관되도록 콘텐츠를 자동으로 배율조정합니다. 기본 디스플레이가 고밀도(200% 크기 조정)이고 보조 디스플레이가 표준 밀도(100%)인 경우 Windows는 보조 디스플레이에서 응용 프로그램 창 내용을 자동으로 축소합니다(응용 프로그램에서 렌더링하는 4픽셀마다 1픽셀 표시).

- Windows는 디스플레이의 픽셀 밀도 및 보기 거리(Windows 7 이상, OEM 구성 가능)에 대한 올바른 크기 조정으로 기본설정됩니다.

- Windows는 280ppi를 초과하는 새 장치에서 최대 250%까지 콘텐츠를 자동으로 확장할 수 있습니다(Windows 8.1 S14 현재).

  Windows에는 증가된 픽셀 수를 활용하기 위해 UI를 확장하는 방법을 제공합니다. 응용 프로그램은 "시스템 DPI 인식"을 선언하여 이 시스템에 옵트인됩니다. 이렇게 하지 않는 응용 프로그램은 시스템에 의해 확장됩니다. 이로 인해 전체 응용 프로그램이 균일하게 픽셀 단위로 늘어나는 "퍼지" 사용자 환경이 발생할 수 있습니다. 다음은 그 예입니다.

  ![DPI 문제 퍼지](../extensibility/media/dpi-issues-fuzzy.png "DPI 문제 퍼지")

  Visual Studio는 DPI 크기를 인식하는 데 동의하므로 "가상화"되지 않습니다.

  Windows(및 Visual Studio)는 시스템에서 설정한 크기 조정 요소를 처리하는 다양한 방법이 있는 여러 UI 기술을 활용합니다. 다음은 그 예입니다.

- WPF는 장치 독립적인 방식으로 컨트롤을 측정합니다(픽셀이 아닌 단위). WPF UI는 현재 DPI에 대해 자동으로 확장됩니다.

- UI 프레임워크에 관계없이 모든 텍스트 크기는 포인트로 표현되므로 시스템에서 DPI 독립적인 것으로 처리됩니다. 디스플레이 장치에 그릴 때 Win32, WinForms 및 WPF의 텍스트가 이미 올바르게 확장됩니다.

- Win32/WinForms 대화 상자 및 창에는 텍스트로 크기를 조정하는 레이아웃(예: 그리드, 흐름 및 테이블 레이아웃 패널)을 사용할 수 있습니다. 이렇게 하면 글꼴 크기를 늘릴 때 배율이 조정되지 않는 하드 코딩된 픽셀 위치를 피할 수 있습니다.

- 시스템 메트릭(예: SM_CXICON 및 SM_CXSMICON)을 기반으로 시스템에서 제공하는 아이콘이 이미 확장되어 있습니다.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>이전 Win32 (GDI, GDI +) 및 윈폼 기반 UI
WPF는 이미 높은 DPI 인식, 우리의 Win32/GDI 기반 코드의 대부분은 원래 마음에 DPI 인식작성 되지 않았습니다. Windows에서 DPI 크기 조정 API를 제공했습니다. Win32 문제에 대한 수정은 제품 전체에서 일관되게 사용해야 합니다. Visual Studio는 기능 중복을 방지하고 제품 전체에서 일관성을 보장하기 위해 도우미 클래스 라이브러리를 제공했습니다.

## <a name="high-resolution-images"></a>고해상도 이미지
이 섹션은 주로 Visual Studio 2013을 확장하는 개발자를 위한 것입니다. Visual Studio 2015의 경우 Visual Studio에 내장된 이미지 서비스를 사용합니다. 또한 여러 버전의 Visual Studio를 지원/대상으로 지정해야 하므로 이전 버전에는 존재하지 않으므로 2015년에 이미지 서비스를 사용하는 것은 옵션이 아닙니다. 이 섹션은 다음 당신을 위한 것입니다.

## <a name="scaling-up-images-that-are-too-small"></a>너무 작은 이미지 크기 조정
너무 작은 이미지는 몇 가지 일반적인 방법을 사용하여 GDI 및 WPF에서 크기를 조정하고 렌더링할 수 있습니다. 관리되는 DPI 도우미 클래스는 내부 및 외부 Visual Studio 통합자가 사용하여 크기 조정 아이콘, 비트맵, 이미지 트립 및 이미지목록을 해결할 수 있습니다. Win32 기반 네이티브 C/C++도우미는 HICON, HBITMAP, 히마게리스트 및 VsUI::GdiplusImage의 스케일링에 사용할 수 있습니다. 비트맵의 크기 조정은 일반적으로 도우미 라이브러리에 대한 참조를 포함한 후 한 줄만 변경하면 됩니다. 다음은 그 예입니다.

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

이미지 목록의 크기 조정은 로드 시 이미지 목록이 완료되었는지 또는 런타임에 추가되었는지여부에 따라 달라집니다. 로드 시 완료되면 비트맵과 마찬가지로 이미지 리스트에 문의하십시오. `LogicalToDeviceUnits()` 이미지 목록을 작성하기 전에 코드가 개별 비트맵을 로드해야 하는 경우 이미지 리스트의 이미지 크기를 조정해야 합니다.

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

네이티브 코드에서 다음과 같이 이미지 목록을 만들 때 차원의 크기를 조정할 수 있습니다.

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

라이브러리의 함수를 사용하면 크기 조정 알고리즘을 지정할 수 있습니다. 이미지 리스트에 배치할 이미지의 배율 조정을 할 때투명도에 사용되는 배경색을 지정하거나 NearestNeighbor 크기 조정(125% 및 150%)을 사용해야 합니다.

MSDN에 대한 설명서를 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> 참조하십시오.

다음 표에서는 해당 DPI 크기 조정 요소에서 이미지의 크기를 조정하는 방법의 예를 보여 주실 수 있습니다. 주황색으로 설명된 이미지는 Visual Studio 2013(100%-200% DPI 크기 조정)의 모범 사례를 나타냅니다.

![DPI 문제 배율](../extensibility/media/dpi-issues-scaling.png "DPI 문제 배율")

## <a name="layout-issues"></a>레이아웃 문제
일반적인 레이아웃 문제는 주로 절대 위치(특히 픽셀 단위)를 사용하는 대신 UI의 포인트 크기를 조정하고 서로 기준으로 유지하여 피할 수 있습니다. 다음은 그 예입니다.

- 레이아웃/텍스트 위치는 확장된 이미지를 고려하여 조정해야 합니다.

- 격자의 열은 확대된 텍스트에 맞게 너비를 조정해야 합니다.

- 요소 간의 하드 코딩된 크기 또는 공간도 확장해야 합니다. 글꼴이 자동으로 크기 조정되므로 텍스트 차원만 을 기반으로 하는 크기는 일반적으로 괜찮습니다.

  도우미 함수는 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> 클래스에서 X 및 Y 축의 배율 조정을 허용하는 데 사용할 수 있습니다.

- LogicToDeviceUnitsX/LogicToDeviceUnitsY(함수를 사용하면 X/Y축에서 배율 조정허용)

- int 공간 = DpiHelper.LogicToDeviceUnitsX (10);

- int 높이 = VsUI::DpiHelper::LogicToDeviceUnitsY(5);

  LogicToDeviceUnits는 직사각형, 점 및 크기와 같은 객체의 배율을 허용하는 오버로드가 있습니다.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>DPIHelper 라이브러리/클래스를 사용하여 이미지 및 레이아웃 확장
Visual Studio DPI 도우미 라이브러리는 기본 및 관리되는 양식으로 사용할 수 있으며 다른 응용 프로그램에서 Visual Studio 셸 외부에서 사용할 수 있습니다.

라이브러리를 사용하려면 Visual [Studio VSSDK 확장성 샘플로](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 이동하여 DPI_Images_Icons 샘플을 복제합니다.

원본 파일에서 *VsUIDpiHelper.h를* 포함하고 클래스의 `VsUI::DpiHelper` 정적 함수를 호출합니다.

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> 모듈 수준 또는 클래스 수준 정적 변수에서 도우미 함수를 사용하지 마십시오. 라이브러리는 스레드 동기화에 정적을 사용하며 순서 초기화 문제가 발생할 수 있습니다. 이러한 정적을 비정적 멤버 변수로 변환하거나 함수로 래핑합니다(첫 번째 액세스시 생성).

Visual Studio 환경 내에서 실행되는 관리 코드에서 DPI 도우미 함수에 액세스하려면 다음을 수행하십시오.

- 소비 프로젝트는 최신 버전의 Shell MPF를 참조해야 합니다. 다음은 그 예입니다.

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- 프로젝트에 **System.Windows.Forms,** **프레젠테이션 코어**및 **프레젠테이션UI에**대한 참조가 있는지 확인합니다.

- 코드에서 **Microsoft.VisualStudio.PlatformUI** 네임스페이스를 사용하고 DpiHelper 클래스의 정적 함수를 호출합니다. 지원되는 형식(점, 크기, 사각형 등)의 경우 새 축척된 개체를 반환하는 확장 함수가 제공됩니다. 다음은 그 예입니다.

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>확대 가능한 UI에서 WPF 이미지 퍼지 처리
WPF에서 비트맵은 사진이나 큰 스크린샷에 적합하지만 인식된 퍼지를 발생하기 때문에 메뉴 항목 아이콘에 적합하지 않은 고품질 쌍입방 알고리즘(기본값)을 사용하여 현재 DPI 줌 수준에 대해 WPF에 의해 자동으로 크기조정됩니다.

권장 사항:

- 로고 이미지 및 배너 아트웍의 경우 기본 <xref:System.Windows.Media.BitmapScalingMode> 크기 조정 모드를 사용할 수 있습니다.

- 메뉴 항목 및 도상 <xref:System.Windows.Media.BitmapScalingMode> 이미지의 경우 다른 왜곡 아티팩트가 퍼지(200% 및 300%)를 제거하지 않는 경우 사용해야 합니다.

- 100%의 배수가 아닌 큰 확대/축소 레벨의 경우(예: 250% 또는 350%), 이중 입방으로 도상 이미지의 배율 조정은 흐릿하고 흐려진 UI를 생성합니다. 먼저 NearestNeighbor를 사용하여 이미지를 100%의 가장 큰 배수로 배율조정하여 더 나은 결과를 얻을 수 있습니다(예: 200% 또는 300%). 거기에서 쌍입방으로 스케일링. 자세한 내용은 대용량 DPI 수준에 대해 WPF 이미지의 사전 크기 조정을 참조하세요.

  Microsoft.VisualStudio.PlatformUI 네임스페이스의 DpiHelper 클래스는 <xref:System.Windows.Media.BitmapScalingMode> 바인딩에 사용할 수 있는 멤버를 제공합니다. 이를 통해 Visual Studio 셸은 DPI 크기 조정 계수에 따라 제품 전체에서 비트맵 크기 조정 모드를 균일하게 제어할 수 있습니다.

  XAML에서 사용하려면 다음을 추가합니다.

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Visual Studio 셸은 이미 최상위 창 및 대화 상자에 이 속성을 설정합니다. Visual Studio에서 실행되는 WPF 기반 UI는 이미 상속됩니다. 설정이 특정 UI 에 전파되지 않으면 XAML/WPF UI의 루트 요소에 설정할 수 있습니다. 이러한 경우 팝업, Win32 부모가 있는 요소, Blend와 같은 프로세스가 부족한 디자이너 창 등이 있습니다.

일부 UI는 Visual Studio 텍스트 편집기 및 WPF 기반 디자이너(WPF 데스크톱 및 Windows 스토어)와 같은 시스템 설정 DPI 확대/축소 수준과 독립적으로 확장할 수 있습니다. 이러한 경우 DpiHelper.BitmapScalingMode를 사용해서는 안 됩니다. 편집기에서 이 문제를 해결하기 위해 IDE 팀은 RenderOptions.BitmapScalingMode라는 사용자 지정 속성을 만들었습니다. 해당 속성 값을 높은 품질 또는 NearestNeighbor로 설정하여 시스템과 UI의 결합된 확대/축소 수준에 따라 설정합니다.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>특수 케이스: 대형 DPI 레벨을 위한 WPF 이미지 사전 크기 조정
100%의 배수가 아닌 매우 큰 확대/축소 수준의 경우(예: 250%, 350% 등) 이중 입방으로 도상 이미지의 배율을 조정하면 흐릿하고 잘린 UI가 생성됩니다. 선명한 텍스트와 함께 이러한 이미지의 인상은 거의 착시처럼. 이미지는 텍스트와 관련하여 눈에 더 가깝고 초점이 보이지 않는 것처럼 보입니다. 이 확대된 크기의 배율 조정 결과는 먼저 NearestNeighbor를 사용하여 이미지를 가장 큰 배수100%(예: 200% 또는 300%)로 배율 조정하여 개선할 수 있습니다. 및 나머지 (추가 50 %)에 쌍입으로 크기 조정.

다음은 개선된 이중 크기 조정 알고리즘100%->200%->250%로 첫 번째 이미지의 배율을 조정하고 두 번째 이미지는 이중 입방 100%->250%로 조정되는 결과의 차이점을 예로 들 수 있습니다.

![DPI 문제 이중 크기 조정 예제](../extensibility/media/dpi-issues-double-scaling-example.png "DPI 문제 이중 크기 조정 예제")

UI가 이 이중 크기 조정을 사용하도록 설정하려면 각 이미지 요소를 표시하기 위한 XAML 태그를 수정해야 합니다. 다음 예제에서는 DpiHelper 라이브러리 및 Shell.12/14를 사용하여 Visual Studio에서 WPF에서 이중 크기 조정을 사용하는 방법을 보여 줍니다.

1단계: NearestNeighbor 를 사용하여 이미지를 200%, 300%로 미리 조정합니다.

바인딩에 적용된 변환기 또는 XAML 태그 확장을 사용하여 이미지를 미리 조정합니다. 다음은 그 예입니다.

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

이미지의 테마를 지정해야 하는 경우(전부는 아니지만 대부분) 태그는 먼저 이미지의 테마를 지정한 다음 미리 배율을 조정하는 다른 변환기를 사용할 수 있습니다. 태그는 원하는 변환 <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>출력에 따라 또는

```xaml
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />

<Image Width="16" Height="16">
  <Image.Source>
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">
      <Binding Path="Icon" />
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"
               RelativeSource="{RelativeSource Self}" />
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />
    </MultiBinding>
  </Image.Source>
</Image>
```

2단계: 현재 DPI에 대한 최종 크기가 올바른지 확인합니다.

WPF는 UIElement에 설정된 BitmapScalingMode 속성을 사용하여 현재 DPI의 UI를 조정하므로 소스로 미리 조정된 이미지를 사용하는 이미지 컨트롤은 예상보다 두 배 또는 3배 더 크게 보입니다. 다음은 이 효과에 대처하는 몇 가지 방법입니다.

- 원본 이미지의 치수를 100%로 알고 있는 경우 이미지 컨트롤의 정확한 크기를 지정할 수 있습니다. 이러한 크기는 크기 조정이 적용되기 전에 UI의 크기를 반영합니다.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- 원본 이미지의 크기를 알 수 없는 경우 LayoutTransform을 사용하여 최종 이미지 개체를 축소할 수 있습니다. 다음은 그 예입니다.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>웹OC에 HDPI 지원 지원
기본적으로 WebOC 컨트롤(예: WPF의 웹 브라우저 컨트롤 또는 IWebBrowser2 인터페이스)은 HDPI 검색 및 지원을 사용할 수 없습니다. 그 결과 고해상도 디스플레이에서 너무 작은 디스플레이 콘텐츠가 포함된 임베디드 컨트롤이 생성됩니다. 다음은 특정 웹 WebOC 인스턴스에서 높은 DPI 지원을 활성화하는 방법에 대해 설명합니다.

IDocHostUIHandler 인터페이스를 [구현합니다(IDocHostUIHandler의](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85))MSDN 문서 참조)

```idl
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]
public interface IDocHostUIHandler
{
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowContextMenu(
        [In, MarshalAs(UnmanagedType.U4)] int dwID,
        [In] POINT pt,
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowUI(
        [In, MarshalAs(UnmanagedType.I4)] int dwID,
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,
        [In, MarshalAs(UnmanagedType.Interface)] object frame,
        [In, MarshalAs(UnmanagedType.Interface)] object doc);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int HideUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int UpdateUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ResizeBorder(
        [In] COMRECT rect,
        [In, MarshalAs(UnmanagedType.Interface)] object doc,
        bool fFrameWindow);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateAccelerator(
        [In] ref MSG msg,
        [In] ref Guid group,
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetOptionKeyPath(
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,
        [In, MarshalAs(UnmanagedType.U4)] int dw);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetDropTarget(
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateUrl(
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int FilterDataObject(
        IDataObject pDO,
        out IDataObject ppDORet);
    }
```

선택적으로 ICustomDoc 인터페이스를 [구현합니다(ICustomDoc의](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))MSDN 문서 참조)

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

IDocHostUIHandler를 구현하는 클래스를 WebOC의 문서와 연결합니다. 위의 ICustomDoc 인터페이스를 구현 한 경우 WebOC의 문서 속성이 유효한 즉시 ICustomDoc에 캐스팅하고 SetUIHandler 메서드를 호출하여 IDocHostUIHandler를 구현하는 클래스를 전달합니다.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

ICustomDoc 인터페이스를 구현 하지 않은 경우 WebOC의 문서 속성이 유효한 즉시 IOleObject에 캐스팅 하 고 메서드를 `SetClientSite` 호출 해야 합니다., IDocHostUIHandler를 구현 하는 클래스에 전달. DOCHOSTUIINFO에서 DOCHOSTUIFLAG_DPI_AWARE 플래그를 메서드 `GetHostInfo` 호출에 전달합니다.

```csharp
public int GetHostInfo(DOCHOSTUIINFO info)
{
    // This is what the default site provides.
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;
    // Add the DPI flag to the defaults
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;
    return S_OK;
}
```

HPDI를 지원하기 위해 WebOC 컨트롤을 얻는 데 필요한 모든 것이 필요합니다.

## <a name="tips"></a>팁

1. WebOC 컨트롤의 문서 속성이 변경되면 문서를 IDocHostUIHandler 클래스와 다시 연결해야 할 수 있습니다.

2. 위의 문제가 작동하지 않으면 WebOC에서 DPI 플래그에 대한 변경 을 선택하지 않는 알려진 문제가 있습니다. 이 문제를 해결하는 가장 신뢰할 수 있는 방법은 WebOC의 광학 줌을 전환하는 것입니다. 또한 이 해결 방법을 필요한 경우 모든 탐색 호출에서 이 문제를 수행해야 할 수 있습니다.

    ```csharp
    // browser2 is a SHDocVw.IWebBrowser2 in this case
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;
    if (cmdTarget != null)
    {
        object commandInput = zoomPercent;
        cmdTarget.Exec(IntPtr.Zero,
                       OLECMDID_OPTICAL_ZOOM,
                       OLECMDEXECOPT_DONTPROMPTUSER,
                       ref commandInput,
                       ref commandOutput);
    }
    ```
