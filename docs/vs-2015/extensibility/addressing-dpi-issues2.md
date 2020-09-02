---
title: DPI Issues2의 주소 지정 Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9b8bc5963ba9263d72800cc473cfa56324884ace
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699265"
---
# <a name="addressing-dpi-issues"></a>DPI 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

장치 수가 늘어나고 "고해상도" 화면에 제공 됩니다. 일반적으로 이러한 화면에는 인치당 200 픽셀 (ppi)이 있습니다. 이러한 컴퓨터에서 응용 프로그램을 사용 하려면 장치에 대 한 일반적인 보기 거리에서 콘텐츠를 보는 데 필요한 요구에 맞게 콘텐츠를 확장 해야 합니다. 2014의 경우 고밀도 디스플레이의 기본 대상은 모바일 컴퓨팅 장치 (태블릿, clamshell 랩톱 및 휴대폰)입니다.  
  
 Windows 8.1 이상에는 컴퓨터가 고밀도 및 표준 밀도 디스플레이 모두에 동시에 연결 된 디스플레이 및 환경에서 작동할 수 있도록 하는 몇 가지 기능이 포함 되어 있습니다.  
  
- Windows에서 "텍스트 및 기타 항목 확대/축소" 설정 (Windows XP 이후 사용 가능)을 사용 하 여 콘텐츠를 장치로 확장할 수 있습니다.  
  
- Windows 8.1 이상에서는 서로 다른 픽셀 밀도 표시 사이에서 이동할 때 대부분의 응용 프로그램의 콘텐츠가 일관 되도록 자동으로 크기를 조정 합니다. 기본 디스플레이가 고밀도 (200% 배율)이 고 보조 디스플레이가 표준 밀도 (100%) 인 경우 Windows에서 자동으로 응용 프로그램 창 내용의 크기를 자동으로 조정 합니다 (응용 프로그램에서 렌더링 하는 4 픽셀 마다 1 픽셀 표시 됨).  
  
- Windows에서는 기본적으로 픽셀 밀도를 적절 하 게 조정 하 고 디스플레이의 거리를 확인 합니다 (Windows 7 이상, OEM 구성 가능).  
  
- Windows는 280 ppi를 초과 하는 새 장치 (Windows 8.1 S14)에서 최대 250%의 콘텐츠를 자동으로 확장할 수 있습니다.  
  
  Windows에서는 증가 하는 픽셀 수를 활용 하기 위해 UI를 확장 하는 방법을 제공 합니다. 응용 프로그램은 "시스템 DPI 인식" 자체를 선언 하 여이 시스템에 opts 합니다. 이 작업을 수행 하지 않는 응용 프로그램은 시스템에 의해 확장 됩니다. 이로 인해 전체 응용 프로그램이 균일 하 게 픽셀 스트레치 되는 "유사" 사용자 환경을 만들 수 있습니다. 예를 들면 다음과 같습니다.  
  
  ![DPI 문제 퍼지](../extensibility/media/dpi-issues-fuzzy.png "DPI 문제 퍼지")  
  
  Visual Studio는 DPI 확장을 인식 하기 위해 opts "가상화" 되지 않습니다.  
  
  Windows 및 Visual Studio는 시스템에서 설정 하는 크기 조정 요소를 서로 다른 방식으로 처리 하는 여러 가지 UI 기술을 활용 합니다. 예를 들면 다음과 같습니다.  
  
- WPF는 장치 독립적 방식 (픽셀이 아닌 단위)으로 컨트롤을 측정 합니다. WPF UI는 현재 DPI에 맞게 자동으로 확장 됩니다.  
  
- UI 프레임 워크에 관계 없이 모든 텍스트 크기는 점으로 표현 되므로 시스템에서 DPI 독립적으로 처리 됩니다. Win32, WinForms 및 WPF의 텍스트는 디스플레이 장치에 그려질 때 이미 올바르게 확장 됩니다.  
  
- Win32/WinForms 대화 상자 및 창에는 텍스트를 사용 하 여 크기를 조정 하는 레이아웃을 사용할 수 있습니다 (예: 그리드, 흐름 및 테이블 레이아웃 패널을 통해). 이러한 기능을 사용 하면 글꼴 크기를 늘릴 때 크기가 조정 되지 않는 하드 코딩 된 픽셀 위치를 방지할 수 있습니다.  
  
- 시스템에서 제공 하는 아이콘 또는 시스템 메트릭 (예: SM_CXICON 및 SM_CXSMICON)을 기반으로 하는 리소스는 이미 확장 되었습니다.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>이전 Win32 (GDI, GDI +) 및 WinForms 기반 UI  
 WPF는 이미 DPI를 인식 하지만 대부분의 Win32/GDI 기반 코드는 원래 DPI 인식을 염두에 두고 작성 되지 않았습니다. Windows에서 DPI 확장 Api를 제공 했습니다. Win32 문제에 대 한 수정 사항은 제품 전체에서 이러한 문제를 일관 되 게 사용 해야 합니다. Visual Studio에서는 기능을 복제 하 고 제품 전체에서 일관성을 유지 하기 위해 도우미 클래스 라이브러리를 제공 했습니다.  
  
## <a name="high-resolution-images"></a>고해상도 이미지  
 이 섹션은 Visual Studio 2013를 확장 하는 개발자를 위한 것입니다. Visual Studio 2015의 경우 Visual Studio에 기본 제공 되는 이미지 서비스를 사용 합니다. 여러 버전의 Visual Studio를 지원 하거나 대상으로 해야 하므로 2015에서 이미지 서비스를 사용 하는 것은 이전 버전에서는 존재 하지 않으므로 옵션이 아닙니다. 이 섹션은 또한 사용자를 위한 것입니다.  
  
## <a name="scaling-up-images-that-are-too-small"></a>너무 작은 이미지 확장  
 너무 작은 이미지는 일반적인 메서드를 사용 하 여 GDI 및 WPF에서 "확장" 하 고 렌더링할 수 있습니다. 관리 되는 DPI 도우미 클래스는 내부 및 외부 Visual Studio 통합 자가 크기 조정 아이콘, 비트맵, imagestrips 및 imagelists를 처리 하는 데 사용할 수 있습니다. Win32 기반 네이티브 C/C + + 도우미는 HICON, HBITMAP, HICON 및 VsUI:: GdiplusImage의 크기를 조정 하는 데 사용할 수 있습니다. 비트맵을 확장 하려면 일반적으로 도우미 라이브러리에 대 한 참조를 포함 한 후에 한 줄만 변경 하면 됩니다. 예를 들면 다음과 같습니다.  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Imagelist를 확장 하는 것은 로드 시 imagelist가 완료 되었는지 아니면 런타임에 추가 되는지에 따라 달라 집니다. 로드 시에 완료 되 면 비트맵과 함께 LogicalToDeviceUnits ()을 호출 합니다. Imagelist를 작성 하기 전에 코드에서 개별 비트맵을 로드 해야 하는 경우 imagelist의 이미지 크기를 조정 해야 합니다.  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 네이티브 코드에서 다음과 같이 imagelist를 만들 때 크기를 조정할 수 있습니다.  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 라이브러리의 함수를 사용 하면 크기 조정 알고리즘을 지정할 수 있습니다. Imagelists에 배치할 이미지의 크기를 조정 하는 경우 투명도에 사용 되는 배경색을 지정 하거나 NearestNeighbor 크기 조정을 사용 해야 합니다. 그러면 125% 및 150%에서 왜곡이 발생 합니다.  
  
 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>MSDN의 설명서를 참조 하십시오.  
  
 다음 표에서는 해당 DPI 배율 인수에서 이미지를 조정 하는 방법의 예를 보여 줍니다. 녹색 이미지는 Visual Studio 2013 (100%-200% DPI 배율)의 모범 사례를 나타냅니다.  
  
 ![DPI 문제 배율](../extensibility/media/dpi-issues-scaling.png "DPI 문제 배율")  
  
## <a name="layout-issues"></a>레이아웃 문제  
 일반적으로는 절대 위치 (픽셀 단위)를 사용 하지 않고 UI의 요소를 서로 상대적으로 크기를 조정 하 여 일반적인 레이아웃 문제를 방지할 수 있습니다. 예를 들면 다음과 같습니다.  
  
- 확대 이미지를 고려 하 여 레이아웃/텍스트 위치를 조정 해야 합니다.  
  
- 모눈의 열에는 축소 된 텍스트에 대해 너비가 조정 되어야 합니다.  
  
- 요소 사이에 하드 코드 된 크기나 공간을 확장 해야 합니다. 글꼴 크기가 자동으로 확장 되기 때문에 텍스트 차원만을 기반으로 하는 크기는 일반적으로 문제가 되지 않습니다.  
  
  클래스에서 도우미 함수를 사용 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> 하 여 X 축과 Y 축에서 크기를 조정할 수 있습니다.  
  
- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (X/Y 축에서 크기 조정을 허용 하는 함수)  
  
- int space = DpiHelper. Logicaltodevice단위 Sx (10);  
  
- int height = VsUI::D piHelper:: LogicalToDeviceUnitsY (5);  
  
  Rect, Point 및 Size와 같은 개체의 크기를 조정할 수 있는 LogicalToDeviceUnits 오버 로드가 있습니다.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>이미지 및 레이아웃 크기를 조정 하는 데에는 DPIHelper 라이브러리/클래스 사용  
 Visual Studio DPI 도우미 라이브러리는 네이티브 및 관리 되는 폼에서 사용할 수 있으며, 다른 응용 프로그램에서 Visual Studio shell 외부에서 사용할 수 있습니다.  
  
 이 라이브러리를 사용 하려면 Visual Studio의로는 [진한 확장성 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 로 이동 하 여 DPI_Images_Icons 높은 샘플을 복제 합니다.  
  
 소스 파일에서 VsUIDpiHelper .h를 포함 하 고 VsUI::D piHelper 클래스의 정적 함수를 호출 합니다.  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
> 모듈 수준 또는 클래스 수준 정적 변수에 도우미 함수를 사용 하지 마십시오. 또한 라이브러리는 스레드 동기화를 위해 정적을 사용 하며, 주문 초기화 문제가 발생할 수 있습니다. 이러한 정적 멤버를 비정적 멤버 변수로 변환 하거나 함수에 래핑하여 처음 액세스할 때 생성 되도록 합니다.  
  
 Visual Studio 환경 내에서 실행 되는 관리 코드에서 DPI 도우미 함수에 액세스 하려면 다음을 수행 합니다.  
  
- 소비 하는 프로젝트는 최신 버전의 Shell MPF를 참조 해야 합니다. 예를 들면 다음과 같습니다.  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
- 프로젝트에 **PresentationCore**및 **PresentationUI**에 **대**한 참조가 있는지 확인 합니다.  
  
- 코드에서 **VisualStudio ui** 네임 스페이스를 사용 하 고, DpiHelper 클래스의 정적 함수를 호출 합니다. 지원 되는 형식 (요소, 크기, 사각형 등)의 경우 확장 된 새 개체를 반환 하는 확장 함수가 제공 됩니다. 예를 들면 다음과 같습니다.  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>확대/해제할 수 있는 UI의 WPF 이미지 허용량 처리  
 WPF에서 비트맵은 그림 또는 큰 스크린샷에서 잘 작동 하는 고품질 이중 알고리즘 (기본값)을 사용 하 여 WPF에 의해 자동으로 크기가 조정 되지만, 인식 되는 허용량을 도입 하기 때문에 메뉴 항목 아이콘에는 적합 하지 않습니다.  
  
 권장 사항:  
  
- 로고 이미지 및 배너 아트 워크의 경우 기본 <xref:System.Windows.Media.BitmapScalingMode> 크기 조정 모드를 사용할 수 있습니다.  
  
- 메뉴 항목 및 iconography 이미지의 경우 <xref:System.Windows.Media.BitmapScalingMode> 다른 왜곡 아티팩트가 발생 하지 않는 경우 (200% 및 300%)를 사용 해야 합니다.  
  
- • 100%의 배수가 아닌 확대 확대/축소 수준인 경우 (예: 250% 또는 350%), 쌍입방을 사용 하 여 iconography 이미지의 크기를 조정 하면 유사 하지 않은 씻어 아웃 UI가 발생 합니다. 먼저 NearestNeighbor 이미지를 100%의 가장 큰 배수로 크기를 조정 하 여 더 나은 결과를 얻을 수 있습니다 (예: 200% 또는 300%). 그리고 여기에서 쌍입방으로 크기를 조정 합니다. 자세한 내용은 특수 한 경우: prescaling WPF images for large DPI (영문)를 참조 하세요.  
  
  VisualStudio Ui 네임 스페이스의 DpiHelper 클래스는 <xref:System.Windows.Media.BitmapScalingMode> 바인딩에 사용할 수 있는 멤버를 제공 합니다. 이를 통해 Visual Studio shell은 DPI 배율 인수에 따라 제품 전체에서 비트맵 크기 조정 모드를 균일 하 게 제어할 수 있습니다.  
  
  XAML에서 사용 하려면 다음을 추가 합니다.  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio shell은 최상위 창과 대화 상자에서 이미이 속성을 설정 합니다. Visual Studio에서 실행 되는 WPF 기반 UI는 이미이를 상속 합니다. 설정이 특정 UI 부분으로 전파 되지 않으면 XAML/WPF UI의 루트 요소에서 설정할 수 있습니다. 이러한 현상이 발생 하는 위치에는 팝업, Win32 부모가 있는 요소 및 Blend와 같이 out-of-process로 실행 되는 디자이너 창이 있습니다.  
  
 일부 UI는 Visual Studio 텍스트 편집기 및 WPF 기반 디자이너 (WPF 데스크톱 및 Windows 스토어)와 같은 시스템 집합 DPI 확대/축소 수준과 별개로 확장할 수 있습니다. 이러한 경우에는 BitmapScalingMode을 사용 하면 안 됩니다. 편집기에서이 문제를 해결 하기 위해 IDE 팀은 RenderOptions. BitmapScalingMode 라는 사용자 지정 속성을 만들었습니다. 시스템 및 UI의 조합 된 확대/축소 수준에 따라 속성 값을 HighQuality 또는 NearestNeighbor으로 설정 합니다.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>특수 한 경우: prescaling WPF 이미지를 큼 DPI 수준으로  
 100%의 배수가 아닌 매우 큰 확대/축소 수준 (예: 250%, 350% 등)의 경우 iconography를 사용 하 여 이미지의 크기를 조정 하면 유사 하지 않은 UI가 발생 합니다. 이러한 이미지는 선명한 텍스트와 함께 시각적 효과의 인상을 거의 같습니다. 이미지는 텍스트와 관련 하 여 집중 하 고 포커스를 벗어난 것 처럼 보입니다. 이 확대 된 크기의 크기 조정 결과는 먼저 NearestNeighbor으로 이미지를 100%의 가장 큰 배수로 크기를 조정 하 여 향상 시킬 수 있습니다 (예: 200% 또는 300%). 및를 나머지 (추가 50%)로 확장 합니다.  
  
 다음은 결과의 차이에 대 한 예입니다. 첫 번째 이미지는 향상 된 이중 크기 조정 알고리즘 100%->200%->250%로 확장 되 고 두 번째 는%->250%의 100 두 번째입니다.  
  
 ![DPI 문제 이중 크기 조정 예제](../extensibility/media/dpi-issues-double-scaling-example.png "DPI 문제 이중 크기 조정 예제")  
  
 UI에서이 이중 크기 조정을 사용 하도록 설정 하려면 각 이미지 요소를 표시 하는 XAML 태그를 수정 해야 합니다. 다음 예제에서는 Visual Studio의 Visual Studio에서 d/14를 사용 하 여 WPF에서 이중 크기 조정을 사용 하는 방법을 보여 줍니다.  
  
 1 단계: NearestNeighbor을 사용 하 여 이미지를 200%, 300%로 Prescale.  
  
 바인딩에 적용 된 변환기나 XAML 태그 확장을 사용 하 여 이미지를 Prescale 합니다. 예를 들면 다음과 같습니다.  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 이미지가 테마에도 적용 되어야 하는 경우 (대부분의 경우에는 그렇지 않은 경우), 먼저 이미지에 테마를 지정 하 고 미리 크기를 조정 하는 다른 변환기를 사용할 수 있습니다. 태그는 <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> 원하는 변환 출력에 따라 또는 중 하나를 사용할 수 있습니다.  
  
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
  
 2 단계: 마지막 크기가 현재 DPI에 맞게 올바른지 확인 합니다.  
  
 WPF는 UIElement에 설정 된 BitmapScalingMode 속성을 사용 하 여 현재 DPI에 대 한 UI의 크기를 조정 하므로 prescaled 이미지를 소스로 사용 하는 이미지 컨트롤은 2 또는 3 배 이상이 되는 것으로 보입니다. 다음은 이러한 효과를 반영 하는 몇 가지 방법입니다.  
  
- 100%에서 원본 이미지의 차원을 알고 있는 경우 이미지 컨트롤의 정확한 크기를 지정할 수 있습니다. 이러한 크기는 크기 조정을 적용 하기 전에 UI의 크기를 반영 합니다.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
- 원본 이미지의 크기를 알 수 없는 경우 LayoutTransform을 사용 하 여 최종 이미지 개체를 축소할 수 있습니다. 예를 들면 다음과 같습니다.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>WebOC에 대 한 HDPI 지원 사용  
 기본적으로 WebOC 컨트롤 (예: WPF의 WebBrowser 컨트롤 또는 IWebBrowser2 인터페이스)은 HDPI 검색 및 지원을 사용 하지 않습니다. 고해상도 디스플레이에서 너무 작은 표시 콘텐츠가 포함 된 컨트롤이 생성 됩니다. 다음에서는 특정 웹 WebOC 인스턴스에서 높은 DPI 지원을 사용 하도록 설정 하는 방법을 설명 합니다.  
  
 IDocHostUIHandler 인터페이스를 구현 합니다. [IDocHostUIHandler](https://msdn.microsoft.com/library/aa753260.aspx) 인터페이스에 대 한 MSDN 문서를 참조 하세요.  
  
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
  
 필요에 따라 ICustomDoc 인터페이스를 구현 합니다. [ICustomDoc](https://msdn.microsoft.com/library/aa753272.aspx) 인터페이스에 대 한 MSDN 문서를 참조 하세요.  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 IDocHostUIHandler을 구현 하는 클래스를 WebOC의 문서와 연결 합니다. 위의 ICustomDoc 인터페이스를 구현한 경우 WebOC의 문서 속성이 유효 하면 바로 ICustomDoc로 캐스팅 하 고 SetUIHandler 메서드를 호출 하 여 IDocHostUIHandler를 구현 하는 클래스를 전달 합니다.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 ICustomDoc 인터페이스를 구현 하지 않은 경우 WebOC의 문서 속성이 유효 하면 바로 IOleObject로 캐스팅 하 고 SetClientSite 메서드를 호출 하 여 IDocHostUIHandler를 구현 하는 클래스를 전달 해야 합니다. GetHostInfo 메서드 호출에 전달 된 DOCHOSTUIINFO에 대 한 DOCHOSTUIFLAG_DPI_AWARE 플래그를 설정 합니다.  
  
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
  
 이는 HPDI을 지원 하기 위해 WebOC 컨트롤을 받아야 하는 것입니다.  
  
## <a name="tips"></a>팁  
  
1. WebOC 컨트롤의 문서 속성이 변경 되는 경우 문서를 IDocHostUIHandler 클래스와 다시 연결 해야 할 수 있습니다.  
  
2. 위의 내용이 적용 되지 않는 경우에는 DPI 플래그의 변경을 WebOC 하는 알려진 문제가 발생 합니다. 이 문제를 해결 하는 가장 신뢰할 수 있는 방법은 확대/축소 비율에 대해 두 개의 서로 다른 값을 사용 하 여 두 번 호출 하는 WebOC 광 확대/축소 하는 것입니다. 또한이 해결 방법이 필요한 경우 모든 탐색 호출에서 수행 해야 할 수도 있습니다.  
  
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
