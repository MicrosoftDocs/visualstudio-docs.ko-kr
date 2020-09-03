---
title: 이미지 서비스 및 카탈로그 | Microsoft Docs
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7df93a801b5ec34a433849baa41f2fd255790c86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536333"
---
# <a name="image-service-and-catalog"></a>이미지 서비스 및 카탈로그
이 cookbook에는 visual studio 2015에 도입 된 Visual Studio 이미지 서비스 및 이미지 카탈로그를 채택 하는 방법에 대 한 지침과 모범 사례가 포함 되어 있습니다.

 개발자는 Visual Studio 2015에 도입 된 이미지 서비스를 사용 하 여 장치에 대 한 최상의 이미지와 사용자가 선택한 테마를 사용 하 여 표시 되는 컨텍스트에 대 한 올바른 테마를 비롯 한 이미지를 표시할 수 있습니다. 이미지 서비스를 채택 하면 자산 유지 관리, HDPI 배율 및 테마와 관련 된 주요 불만 사항을 제거 하는 데 도움이 됩니다.

|**오늘 문제**|**솔루션**|
|-|-|
|배경 색 혼합|기본 제공 알파 혼합|
|테마 (일부) 이미지|테마 메타 데이터|
|고대비 모드|대체 고대비 리소스|
|여러 DPI 모드에 대해 여러 리소스가 필요 합니다.|벡터 기반 대체 (fallback)를 사용 하 여 선택할 수 있는 리소스|
|중복 이미지|이미지 개념 당 하나의 식별자|

 이미지 서비스를 채택 하는 이유

- Visual Studio에서 항상 최신 "픽셀 완벽" 이미지 가져오기

- 사용자 고유의 이미지를 제출 하 고 사용할 수 있습니다.

- Windows에서 새로운 DPI 배율을 추가할 때 이미지를 테스트 하지 않아도 됨

- 구현에서 이전 아키텍처의 장애물 해결

  이미지 서비스를 사용 하기 전과 후의 Visual Studio shell 도구 모음:

  ![이미지 서비스 이전 및 이후](../extensibility/media/image-service-before-and-after.png "이미지 서비스 이전 및 이후")

## <a name="how-it-works"></a>작동 방법
 이미지 서비스는 지원 되는 모든 UI 프레임 워크에 적합 한 비트맵 이미지를 제공할 수 있습니다.

- WPF: BitmapSource

- WinForms: Drawing.

- Win32: HBITMAP

  이미지 서비스 흐름 다이어그램

  ![이미지 서비스 흐름 다이어그램](../extensibility/media/image-service-flow-diagram.png "이미지 서비스 흐름 다이어그램")

  **이미지 모니커**

  이미지 모니커 (또는 short 모니커)는 이미지 라이브러리에서 이미지 자산 또는 이미지 목록 자산을 고유 하 게 식별 하는 GUID/ID 쌍입니다.

  **알려진 모니커**

  Visual Studio 이미지 카탈로그에 포함 되 고 Visual Studio 구성 요소나 확장이 공개적으로 사용할 때 사용할 이미지 모니커의 집합입니다.

  **이미지 매니페스트 파일**

  이미지 매니페스트 (*imagemanifest*) 파일은 이미지 자산 집합, 해당 자산을 나타내는 모니커 및 각 자산을 나타내는 실제 이미지를 정의 하는 XML 파일입니다. 이미지 매니페스트는 레거시 UI 지원에 대 한 독립 실행형 이미지 또는 이미지 목록을 정의할 수 있습니다. 또한 자산이 표시 되는 경우와 각 자산을 표시 하는 방식에 따라 자산 또는 개별 이미지에서 설정할 수 있는 특성도 있습니다.

  **이미지 매니페스트 스키마**

  전체 이미지 매니페스트는 다음과 같습니다.

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symbols**

 가독성 및 유지 관리를 돕기 위해 이미지 매니페스트는 특성 값에 기호를 사용할 수 있습니다. 기호는 다음과 같이 정의 됩니다.

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**하위 요소**|**정의**|
|-|-|
|가져오기|현재 매니페스트에서 사용할 지정 된 매니페스트 파일의 기호를 가져옵니다.|
|GUID|기호는 GUID를 나타내며 GUID 형식과 일치 해야 합니다.|
|ID|기호는 ID를 나타내고 음수가 아닌 정수 여야 합니다.|
|String|기호는 임의의 문자열 값을 나타냅니다.|

 기호는 대/소문자를 구분 하며 $ (기호-이름) 구문을 사용 하 여 참조 됩니다.

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 일부 기호는 모든 매니페스트에 대해 미리 정의 됩니다. 이러한 속성은 또는 요소의 Uri 특성에 사용 \<Source> 하 여 \<Import> 로컬 컴퓨터에서 경로를 참조할 수 있습니다.

|**기호**|**설명**|
|-|-|
|CommonProgramFiles|% CommonProgramFiles% 환경 변수의 값입니다.|
|LocalAppData|% LocalAppData% 환경 변수의 값입니다.|
|ManifestFolder|매니페스트 파일을 포함 하는 폴더입니다.|
|MyDocuments|현재 사용자의 내 문서 폴더에 대 한 전체 경로입니다.|
|ProgramFiles|% ProgramFiles% 환경 변수의 값입니다.|
|시스템|*Windows\System32* 폴더|
|I|% WinDir% 환경 변수의 값입니다.|

 **이미지**

 \<Image>요소는 모니커가 참조할 수 있는 이미지를 정의 합니다. 함께 사용 된 GUID 및 ID는 이미지 모니커를 형성 합니다. 이미지의 모니커는 전체 이미지 라이브러리에서 고유 해야 합니다. 하나 이상의 이미지가 지정 된 모니커를 포함 하는 경우 라이브러리를 빌드하는 동안 발생 한 첫 번째 이미지는 유지 되는 것입니다.

 하나 이상의 소스를 포함 해야 합니다. 크기 중립적인 소스는 광범위 한 크기에서 최상의 결과를 제공 하지만 필요 하지 않습니다. 요소에 정의 되지 않은 크기의 이미지를 요청 하는 메시지가 표시 되 \<Image> 고 크기 중립적인 소스가 없으면 서비스에서 가장 적합 한 크기의 원본을 선택 하 고 요청 된 크기로 크기를 조정 합니다.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Attribute**|**정의**|
|-|-|
|GUID|하다 이미지 모니커의 GUID 부분입니다.|
|ID|하다 이미지 모니커의 ID 부분입니다.|
|AllowColorInversion|[선택 사항, 기본값 true] 이미지에서 짙은 배경에 사용 될 때 해당 색을 프로그래밍 방식으로 반전 시킬 수 있는지 여부를 나타냅니다.|

 **원본**

 \<Source>요소는 단일 이미지 소스 자산 (XAML 및 PNG)을 정의 합니다.

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Attribute**|**정의**|
|-|-|
|URI|하다 이미지를 로드할 수 있는 위치를 정의 하는 URI입니다. 다음 중 하나일 수 있습니다.<br /><br /> -Application:///authority를 사용 하는 [PACK URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br />-절대 구성 요소 리소스 참조<br />-네이티브 리소스를 포함 하는 파일의 경로|
|배경|필드 소스를 사용 하기 위해 사용할 배경의 종류를 나타냅니다.<br /><br /> 다음 중 하나일 수 있습니다.<br /><br /> *광원:* 원본은 밝은 배경에 사용할 수 있습니다.<br /><br /> *어둡게:* 원본은 어두운 배경에서 사용할 수 있습니다.<br /><br /> *System.windows.forms.systeminformation.highcontrast:* 소스는 고대비 모드의 모든 백그라운드에서 사용할 수 있습니다.<br /><br /> *HighContrastLight:* 소스는 고대비 모드에서 밝은 배경에 사용할 수 있습니다.<br /><br /> *HighContrastDark:* 소스는 고대비 모드에서 짙은 배경으로 사용할 수 있습니다.<br /><br /> 배경 특성을 생략 하면 모든 배경에서 소스를 사용할 수 있습니다.<br /><br /> 배경이 *Light*, *어둡게*, *HighContrastLight*또는 *HighContrastDark*인 경우 소스의 색은 반전 되지 않습니다. 배경이 생략 되거나 *system.windows.forms.systeminformation.highcontrast*로 설정 된 경우 소스 색의 반전은 이미지의 **allowcolorinversion** 특성에 의해 제어 됩니다.|

요소에는 \<Source> 다음과 같은 선택적 하위 요소 중 하나만 있을 수 있습니다.

|**Element**|**특성 (모두 필수)**|**정의**|
|-|-|-|
|\<Size>|값|원본은 지정 된 크기 (장치 단위)의 이미지에 사용 됩니다. 이미지가 정사각형이 됩니다.|
|\<SizeRange>|MinSize, MaxSize|원본은 MinSize에서 MaxSize (장치 단위)까지 이미지에 사용 됩니다. 이미지가 정사각형이 됩니다.|
|\<Dimensions>|너비, 높이|원본은 지정 된 너비 및 높이 (장치 단위)의 이미지에 사용 됩니다.|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, Maxwidth|이 소스는 최소 너비/높이에서 최대 너비/높이 (장치 단위)로 이루어진 이미지에 사용 됩니다.|

 요소는 관리 되는 \<Source> \<NativeResource> \<Source> 어셈블리가 아니라 네이티브 어셈블리에서 로드 되는을 정의 하는 선택적 하위 요소를 포함할 수도 있습니다.

```xml
<NativeResource Type="type" ID="int" />
```

|**Attribute**|**정의**|
|-|-|
|형식|하다 네이티브 리소스의 형식 (XAML 또는 PNG)입니다.|
|ID|하다 네이티브 리소스의 정수 ID 부분입니다.|

 **ImageList**

 \<ImageList>요소는 단일 스트립에서 반환 될 수 있는 이미지의 컬렉션을 정의 합니다. 스트라이프는 필요에 따라 요청 시 작성 됩니다.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Attribute**|**정의**|
|-|-|
|GUID|하다 이미지 모니커의 GUID 부분입니다.|
|ID|하다 이미지 모니커의 ID 부분입니다.|
|외부|[선택 사항, 기본값 false] 이미지 모니커가 현재 매니페스트의 이미지를 참조 하는지 여부를 나타냅니다.|

 포함 된 이미지의 모니커는 현재 매니페스트에 정의 된 이미지를 참조할 필요가 없습니다. 이미지 라이브러리에서 포함 된 이미지를 찾을 수 없는 경우 빈 자리 표시자 이미지가 대신 사용 됩니다.

## <a name="using-the-image-service"></a>Image service 사용

### <a name="first-steps-managed"></a>첫 번째 단계 (관리 됨)
 이미지 서비스를 사용 하려면 다음 어셈블리 중 일부 또는 전부에 대 한 참조를 프로젝트에 추가 해야 합니다.

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - 기본 제공 이미지 카탈로그 **Knownmonikers**를 사용 하는 경우 필요 합니다.

- *Microsoft.VisualStudio.Imaging.dll*

  - WPF UI에서 **CrispImage** 및 **Imagethemingutilities** 를 사용 하는 경우 필요 합니다.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - **ImageMoniker** 및 **ImageAttributes** 형식을 사용 하는 경우 필요 합니다.

  - **EmbedInteropTypes** 를 true로 설정 해야 합니다.

- *VisualStudio. 14.0 시간입니다.*

  - **IVsImageService2** 형식을 사용 하는 경우 필수 사항입니다.

  - **EmbedInteropTypes** 를 true로 설정 해야 합니다.

- *Microsoft.VisualStudio.Utilities.dll*

  - WPF UI에서 ImageBackgroundColor에 **BrushToColorConverter** 를 사용 하는 경우 필요 합니다 **.**

- *VisualStudio \<VSVersion> . 0*

  - **Ivsuiobject** 유형을 사용 하는 경우 필요 합니다.

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - WinForms 관련 UI 도우미를 사용 하는 경우 필요 합니다.

  - **EmbedInteropTypes** 는 true로 설정 해야 합니다.

### <a name="first-steps-native"></a>첫 번째 단계 (네이티브)
 이미지 서비스를 사용 하려면 다음 헤더 중 일부 또는 모두를 프로젝트에 포함 해야 합니다.

- **KnownImageIds**

  - 기본 제공 이미지 카탈로그 **Knownmonikers**를 사용 하지만 **IVsHierarchy GetGuidProperty** 또는 **GetProperty** 호출에서 값을 반환 하는 경우와 같이 **ImageMoniker** 형식을 사용할 수 없는 경우에 필요 합니다.

- **KnownMonikers .h**

  - 기본 제공 이미지 카탈로그 **Knownmonikers**를 사용 하는 경우 필요 합니다.

- **ImageParameters140**

  - **ImageMoniker** 및 **ImageAttributes** 형식을 사용 하는 경우 필요 합니다.

- **VSShell140**

  - **IVsImageService2** 형식을 사용 하는 경우 필수 사항입니다.

- **ImageThemingUtilities .h**

  - 이미지 서비스가 테마를 처리 하도록 허용할 수 없는 경우에 필요 합니다.

  - 이미지 서비스가 이미지 테마를 처리할 수 있는 경우에는이 헤더를 사용 하지 마세요.

::: moniker range="vs-2017"
- **VSUIDPIHelper. h**

  - DPI 도우미를 사용 하 여 현재 DPI를 가져오는 경우에 필요 합니다.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness**

  - DPI 인식 도우미를 사용 하 여 현재 DPI를 가져오는 경우에 필요 합니다.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>새 WPF UI를 작성할 어떻게 할까요? 있나요?

1. 위의 첫 번째 단계 섹션에 필요한 어셈블리 참조를 프로젝트에 추가 하 여 시작 합니다. 모든 항목을 추가할 필요는 없으므로 필요한 참조만 추가 합니다. (참고: **브러시**대신 또는를 사용 하 여 **색** 에 액세스할 경우 변환기가 필요 하지 않으므로 **유틸리티**에 대 한 참조를 건너뛸 수 있습니다.)

2. 원하는 이미지를 선택 하 고 모니커를 가져옵니다. **Knownmoniker**를 사용 하거나 고유한 사용자 지정 이미지 및 모니커를 사용 하는 경우 사용자 고유의 모니커를 사용 합니다.

3. XAML에 **CrispImages** 를 추가 합니다. (아래 예제 참조)

4. UI 계층 구조에서 **ImageBackgroundColor** 속성을 설정 합니다. 이는 **CrispImage**에 반드시 있어야 하는 것이 아니라 배경색이 알려진 위치에 설정 해야 합니다. (아래 예제 참조)

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **기존 WPF UI를 업데이트 어떻게 할까요??**

 기존 WPF UI 업데이트는 다음 세 가지 기본 단계로 구성 된 비교적 간단한 프로세스입니다.

1. \<Image>UI의 모든 요소를 요소로 바꿉니다 \<CrispImage> .

2. 모든 원본 특성을 모니커 특성으로 변경 합니다.

    - 이미지가 변경 되지 않으며 **Knownmonikers**를 사용 하는 경우 해당 속성을 **knownmonikers**에 정적으로 바인딩합니다. 위의 예제를 참조 하십시오.

    - 이미지가 변경 되지 않으며 사용자 고유의 사용자 지정 이미지를 사용 하는 경우 고유한 모니커에 정적으로 바인딩합니다.

    - 이미지가 변경 될 수 있는 경우 속성 변경에 대해 알리는 코드 속성에 모니커 특성을 바인딩합니다.

3. UI 계층 구조의 어딘가에 **ImageImageBackgroundColor** 를 설정 하 여 색 반전이 올바르게 작동 하는지 확인 합니다.

    - 이렇게 하려면 **BrushToColorConverter** 클래스를 사용 해야 할 수 있습니다. 위의 예제를 참조 하십시오.

## <a name="how-do-i-update-win32-ui"></a>Win32 UI를 업데이트 어떻게 할까요??
 적절 한 위치에 있는 코드에 다음을 추가 하 여 이미지의 원시 로드를 대체 합니다. 필요에 따라 HBITMAPs Hbitmaps HBITMAPS를 반환 하기 위한 값을 전환 합니다.

 **이미지 서비스 가져오기**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **이미지 요청**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>WinForms UI를 업데이트 어떻게 할까요??
 적절 한 위치에 있는 코드에 다음을 추가 하 여 이미지의 원시 로드를 대체 합니다. 필요에 따라 비트맵과 아이콘을 반환 하기 위한 값을 전환 합니다.

 **유용한 using 문**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **이미지 서비스 가져오기**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **이미지 요청**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>새 도구 창에서 이미지 모니커를 사용할 어떻게 할까요? 있나요?
 Visual Studio 2015에 대해 VSIX 패키지 프로젝트 템플릿이 업데이트 되었습니다. 새 도구 창을 만들려면 VSIX 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목** 추가 (**Ctrl** + **Shift** + **a**)를 선택 합니다. 프로젝트 언어의 확장성 노드 아래에서 **사용자 지정 도구 창**을 선택 하 고 도구 창에 이름을 지정한 다음 **추가** 단추를 누릅니다.

 도구 창에서 모니커를 사용 하는 주요 위치입니다. 각각에 대 한 지침을 따르세요.

1. 탭이 충분히 작은 경우 ( **Ctrl** + **tab** 창 전환기 에서도 사용 됨) 도구 창 탭

    **ToolWindowPane** 형식에서 파생 되는 클래스에 대 한 생성자에 다음 줄을 추가 합니다.

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. 도구 창을 여는 명령입니다.

    패키지에 대 한 *. vsct* 파일에서 도구 창의 명령 단추를 편집 합니다.

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **기존 도구 창에서 이미지 모니커를 사용할 어떻게 할까요? 있나요?**

   이미지 모니커를 사용 하도록 기존 도구 창을 업데이트 하는 것은 새 도구 창을 만드는 단계와 비슷합니다.

   도구 창에서 모니커를 사용 하는 주요 위치입니다. 각각에 대 한 지침을 따르세요.

3. 탭이 충분히 작은 경우 ( **Ctrl** + **tab** 창 전환기 에서도 사용 됨) 도구 창 탭

   1. **ToolWindowPane** 형식에서 파생 되는 클래스에 대 한 생성자에서 이러한 줄 (있는 경우)을 제거 합니다.

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. "새 도구 창에서 이미지 모니커 사용 어떻게 할까요?"의 #1 단계를 참조 하세요. 섹션을 참조하세요.

4. 도구 창을 여는 명령입니다.

   - "새 도구 창에서 이미지 모니커 사용 어떻게 할까요?"의 #2 단계를 참조 하세요. 섹션을 참조하세요.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Vsct 파일에서 이미지 모니커를 사용 어떻게 할까요??
 아래 주석 처리 된 줄에 표시 된 대로 *vsct* 파일을 업데이트 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **이전 버전의 Visual Studio에서 vsct 파일을 읽어야 하는 경우는 어떻게 되나요?**

 이전 버전의 Visual Studio에서는 **Iconismoniker** 명령 플래그를 인식 하지 못합니다. 이미지 서비스를 지 원하는 Visual Studio 버전에서 이미지 서비스의 이미지를 사용할 수 있지만 이전 버전의 Visual Studio에서는 이전 스타일의 이미지를 계속 사용 합니다. 이렇게 하려면 *. vsct* 파일을 변경 되지 않은 상태로 두고 (따라서 이전 버전의 Visual Studio와 호환), *vsct* 파일의 요소에 정의 된 GUID/id 쌍에서 \<Bitmaps> 이미지 모니커 guid/ID 쌍으로 매핑되는 CSV (쉼표로 구분 된 값) 파일을 만듭니다.

 매핑 CSV 파일의 형식은 다음과 같습니다.

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 CSV 파일은 패키지와 함께 배포 되 고 해당 위치는 **ProvideMenuResource** package 특성의 **IconMappingFilename** 속성으로 지정 됩니다.

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename** 는 $PackageFolder $ (위 예제에서와 같이)에서 암시적으로 루 팅 된 상대 경로 이거나, *@ "% UserProfile% \dir1\dir2\MyMappingFile.csv"* 와 같이 환경 변수에 의해 정의 된 디렉터리에서 명시적으로 루트 된 절대 경로입니다.

## <a name="how-do-i-port-a-project-system"></a>프로젝트 시스템의 포트를 어떻게 할까요? 하 시겠습니까?
 **프로젝트에 대 한 ImageMonikers를 제공 하는 방법**

1. 프로젝트의 **IVsHierarchy**에 대 한 **VSHPROPID_SupportsIconMonikers** 를 구현 하 고 true를 반환 합니다.

2. **VSHPROPID_IconMonikerImageList** (원본 프로젝트가 **VSHPROPID_IconImgList**사용 되는 경우) 또는 **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (원본 프로젝트가 **VSHPROPID_IconHandle** 및 **VSHPROPID_OpenFolderIconHandle**사용 되는 경우)를 구현 합니다.

3. 아이콘에 대 한 원래 VSHPROPIDs의 구현을 변경 하 여 확장 지점이 요청 하는 경우 "레거시" 버전의 아이콘을 만듭니다. **IVsImageService2** 는 이러한 아이콘을 가져오는 데 필요한 기능을 제공 합니다.

   **VB/c # 프로젝트 특색에 대 한 추가 요구 사항**

   프로젝트가 **가장 바깥쪽 버전**임을 감지 하는 경우에만 **VSHPROPID_SupportsIconMonikers** 을 구현 합니다. 그렇지 않으면 실제 가장 바깥쪽 버전이 실제로는 이미지 모니커를 지원 하지 않을 수 있으며, 기본 버전은 사용자 지정 된 이미지를 효과적으로 "숨길" 수 있습니다.

   **CPS에서 이미지 모니커를 사용 어떻게 할까요??**

   CPS (Common Project System)에서 사용자 지정 이미지를 설정 하는 작업은 수동으로 수행 하거나 Project System 확장성 SDK와 함께 제공 되는 항목 템플릿을 통해 설정할 수 있습니다.

   **Project System 확장성 SDK 사용**

   [프로젝트 형식/항목 형식에 대 한 사용자 지정 아이콘 제공](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) 의 지침에 따라 CPS 이미지를 사용자 지정 합니다. CPS에 대 한 자세한 내용은 [Visual Studio 프로젝트 시스템 확장성 설명서](https://github.com/Microsoft/VSProjectSystem) 에서 찾을 수 있습니다.

   **수동으로 ImageMonikers 사용**

4. 프로젝트 시스템에서 **IProjectTreeModifier** 인터페이스를 구현 하 고 내보냅니다.

5. 사용할 **knownmoniker** 또는 사용자 지정 이미지 모니커를 결정 합니다.

6. **Applymodifications** 방법에서 다음 예제와 같이 새 트리를 반환 하기 전에 메서드에서 다음을 수행 합니다.

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. 새 트리를 만드는 경우 아래 예제와 같이 원하는 모니커를 NewTree 메서드로 전달 하 여 사용자 지정 이미지를 설정할 수 있습니다.

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>실제 이미지 스트립에서 모니커 기반 이미지 스트립으로 변환 어떻게 할까요?
 **HIMAGELISTs를 지원 해야 합니다.**

 이미지 서비스를 사용 하기 위해 업데이트 하려는 코드에 이미 기존 이미지 스트립이 있지만 이미지 목록을 전달 해야 하는 Api에 의해 제한 되는 경우에도 이미지 서비스의 이점을 얻을 수 있습니다. 모니커 기반 이미지 스트립을 만들려면 아래 단계에 따라 기존 모니커의 매니페스트를 만듭니다.

1. **ManifestFromResources** 도구를 실행 하 여 이미지 스트립을 전달 합니다. 그러면 스트립의 매니페스트가 생성 됩니다.

   - 권장: 사용에 맞게 매니페스트에 기본이 아닌 이름을 제공 합니다.

2. **Knownmonikers**만 사용 하는 경우 다음을 수행 합니다.

   - \<Images>매니페스트의 섹션을로 바꿉니다 \<Images/> .

   - 모든 하위 이미지 Id를 제거 합니다 (_ # #을 사용 하는 모든 항목 \<imagestrip name> ).

   - 권장: 사용에 맞게 AssetsGuid 기호 및 이미지 스트립 기호의 이름을 바꿉니다.

   - 각 **ContainedImage**의 GUID를 $ (ImageCatalogGuid)로 바꾸고 각 **ContainedImage**의 ID를 $ ()로 바꾸고 \<moniker> External = "True" 특성을 각 **ContainedImage** 에 추가 합니다.

       - \<moniker> 이미지와 일치 하지만 "Knownmoniker"와 일치 하는 **Knownmoniker** 로 바꾸어야 합니다. 이름에서 제거 되었습니다.

   - <가져오기 매니페스트 = "$ (ManifestFolder) \\<상대 설치 디렉터리 경로를 * \> \Microsoft.VisualStudio.ImageCatalog.imagemanifest"/ \*> 섹션의 맨 위에 추가 \<Symbols> 합니다.

       - 상대 경로는 매니페스트에 대 한 설치 제작에 정의 된 배포 위치에 따라 결정 됩니다.

3. **ManifestToCode** 도구를 실행 하 여 기존 코드에 이미지 스트립을 위한 이미지 서비스를 쿼리 하는 데 사용할 수 있는 모니커가 있도록 래퍼를 생성 합니다.

   - 권장: 사용에 맞게 래퍼 및 네임 스페이스에 대해 기본이 아닌 이름을 제공 합니다.

4. 이미지 서비스 및 새 파일을 사용 하기 위해 모든 추가, 작성/배포 및 기타 코드 변경 작업을 수행 합니다.

   내부 및 외부 이미지를 포함 하는 샘플 매니페스트는 다음과 같이 표시 됩니다.

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **HIMAGELISTs를 지원할 필요가 없습니다.**

1. 이미지 스트립의 이미지와 일치 하는 **knownmonikers** 집합을 확인 하거나 이미지 스트립의 이미지에 대 한 사용자 고유의 모니커를 만듭니다.

2. 대신, 모니커를 사용 하기 위해 이미지 스트립의 필수 인덱스에서 이미지를 가져오는 데 사용한 매핑을 업데이트 합니다.

3. 업데이트 된 매핑을 통해 모니커를 요청 하는 이미지 서비스를 사용 하도록 코드를 업데이트 합니다. (이는 관리 코드에 대 한 **CrispImages** 업데이트 하거나, 이미지 서비스에서 Hbitmaps hbitmaps 요청 하 고 네이티브 코드를 위해이를 전달 하는 것을 의미할 수 있습니다.)

## <a name="testing-your-images"></a>이미지 테스트
 이미지 라이브러리 뷰어 도구를 사용 하 여 이미지 매니페스트를 테스트 하 여 모든 것이 올바르게 작성 되었는지 확인할 수 있습니다. 이 도구는 [Visual Studio 2015 SDK](visual-studio-sdk.md)에서 찾을 수 있습니다. 이 도구 및 기타 도구에 대 한 설명서는 [여기](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015)에서 찾을 수 있습니다.

## <a name="additional-resources"></a>추가 자료

### <a name="samples"></a>샘플
 다양 한 Visual Studio 확장 지점의 일부로 이미지 서비스를 사용 하는 방법을 보여 주기 위해 GitHub의 몇 가지 Visual Studio 샘플이 업데이트 되었습니다.

 최신 샘플을 확인 하세요 [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) .

### <a name="tooling"></a>도구
 Image service를 사용 하는 UI를 만들고 업데이트 하는 데 도움이 되도록 이미지 서비스에 대 한 지원 도구 집합을 만들었습니다. 각 도구에 대 한 자세한 내용은 도구와 함께 제공 되는 설명서를 참조 하세요. 이 도구는 [Visual Studio 2015 SDK](visual-studio-sdk.md)의 일부로 포함 되어 있습니다.

 **ManifestFromResources**

 Manifest from Resources 도구는 이미지 리소스 (PNG 또는 XAML) 목록을 사용 하 고 이미지 서비스에서 해당 이미지를 사용 하기 위한 이미지 매니페스트 파일을 생성 합니다.

 **ManifestToCode**

 Manifest to Code 도구는 이미지 매니페스트 파일을 사용 하 고 코드 (c + +, c # 또는 VB) 또는 *. vsct* 파일의 매니페스트 값을 참조 하기 위한 래퍼 파일을 생성 합니다.

 **Image라이브러리 뷰어**

 이미지 라이브러리 뷰어 도구는 이미지 매니페스트를 로드 하 고 사용자가 Visual Studio에서 매니페스트가 올바르게 작성 되었는지 확인 하는 것과 동일한 방식으로이를 조작할 수 있습니다. 사용자는 배경, 크기, DPI 설정, 고대비 및 기타 설정을 변경할 수 있습니다. 또한 매니페스트에서 오류를 찾기 위한 로드 정보를 표시 하 고 매니페스트의 각 이미지에 대 한 소스 정보를 표시 합니다.

## <a name="faq"></a>FAQ

- 로드할 때 포함 해야 하는 종속성이 \<Reference Include="Microsoft.VisualStudio.*.Interop.14.0.DesignTime" /> 있나요?

  - 모든 interop Dll에 대해 EmbedInteropTypes = "true"를 설정 합니다.

- 확장을 사용 하 여 이미지 매니페스트를 배포 어떻게 할까요?

  - 프로젝트에 *imagemanifest* 파일을 추가 합니다.

  - "VSIX에 포함"을 True로 설정 합니다.

- 내 CPS 프로젝트 시스템을 업데이트 하 고 있습니다. **ImageName** 및 **StockIconService**는 어떻게 되었습니까?

  - 이러한 업데이트는 CPS를 사용 하도록 업데이트 될 때 제거 되었습니다. 더 이상 **StockIconService**를 호출할 필요가 없으며 CPS 유틸리티의 **ToProjectSystemType ()** 확장 메서드를 사용 하 여 원하는 **knownmoniker** 를 메서드나 속성에 전달 하기만 하면 됩니다. 다음은 **ImageName** 에서 **knownmonikers** 대 한 매핑을 찾을 수 있습니다.

    |**ImageName**|**KnownMoniker**|
    |-|-|
    |OfflineWebApp|KnownImageIds|
    |WebReferencesFolder|KnownImageIds|
    |ImageName. OpenReferenceFolder|KnownImageIds 열기|
    |ImageName. ReferenceFolder|KnownImageIds|
    |ImageName. 참조|KnownImageIds|
    |ImageName. SdlWebReference|KnownImageIds. WebReferenceFolder|
    |DiscoWebReference|KnownImageIds. DynamicDiscoveryDocument|
    |ImageName 폴더|KnownImageIds 닫힌 폴더|
    |ImageName. OpenFolder|KnownImageIds 열기|
    |ExcludedFolder|KnownImageIds.HiddenFolderClosed|
    |OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|
    |ExcludedFile|KnownImageIds.HiddenFile|
    |DependentFile|KnownImageIds 파일|
    |MissingFile|KnownImageIds.DocumentWarning|
    |ImageName WindowsForm|KnownImageIds|
    |ImageName WindowsUserControl|KnownImageIds|
    |WindowsComponent|KnownImageIds 파일|
    |ImageName.Xml스키마|KnownImageIds.XML스키마|
    |ImageName.Xml파일|KnownImageIds.XML파일|
    |WebForm|KnownImageIds|
    |ImageName 웹 서비스|KnownImageIds|
    |ImageName. WebUserControl|KnownImageIds|
    |ImageName. WebCustomUserControl|KnownImageIds.WebCustomControl|
    |ImageName 페이지|KnownImageIds 파일|
    |ImageName. GlobalApplicationClass|KnownImageIds 파일|
    |ImageName. WebConfig|KnownImageIds.ConfigurationFile|
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|
    |ImageName. 스타일 시트|KnownImageIds|
    |ScriptFile|KnownImageIds.JS스크립트|
    |TextFile|KnownImageIds.Document|
    |ImageName 파일|KnownImageIds|
    |ImageName 리소스|KnownImageIds.DocumentGroup|
    |ImageName 비트맵|KnownImageIds|
    |ImageName. 아이콘|KnownImageIds 파일|
    |ImageName. 이미지|KnownImageIds|
    |ImageMap|KnownImageIds.ImageMapFile|
    |ImageName. XWorld|KnownImageIds.XWorldFile|
    |ImageName 오디오|KnownImageIds|
    |ImageName. 비디오|KnownImageIds|
    |ImageName.Cab|KnownImageIds.CAB프로젝트|
    |ImageName Jar|KnownImageIds. JARFile|
    |ImageName. DataEnvironment|KnownImageIds|
    |PreviewFile|KnownImageIds|
    |DanglingReference|KnownImageIds|
    |XsltFile|KnownImageIds. XSLTransform|
    |ImageName 커서|KnownImageIds.CursorFile|
    |ImageName. AppDesignerFolder|KnownImageIds|
    |ImageName. 데이터|KnownImageIds|
    |ImageName 응용 프로그램|KnownImageIds|
    |ImageName. DataSet|KnownImageIds 그룹|
    |ImageName .Pfx|KnownImageIds|
    |ImageName|KnownImageIds|
    |ImageName. VisualBasicProject|KnownImageIds 노드|
    |CSharpProject|KnownImageIds|
    |ImageName. 비어 있음|KnownImageIds|
    |MissingFolder|KnownImageIds 오프 라인|
    |ImageName. SharedImportReference|KnownImageIds 프로젝트|
    |ImageName. SharedProjectCs|KnownImageIds. CSSharedProject|
    |ImageName. SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName. SharedProjectJs|KnownImageIds.JSSharedProject|
    |CSharpCodeFile|KnownImageIds.CSFileNode|
    |ImageName. VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - 완성 목록 공급자를 업데이트 하 고 있습니다. 이전 **StandardGlyphGroup** 및 **standardglyph** 값과 일치 하는 **knownmonikers** 는 무엇 인가요?

    |Name|Name|Name|
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupConstant|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant|GlyphItemInternal|ConstantInternal|
    |GlyphGroupConstant|GlyphItemFriend|ConstantInternal|
    |GlyphGroupConstant|GlyphItemProtected|ConstantProtected|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|
    |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationItemPublic|
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationItemShortcut|
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |GlyphGroupEvent|GlyphItemInternal|EventInternal|
    |GlyphGroupEvent|GlyphItemFriend|EventInternal|
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut 가기|
    |GlyphGroupException|GlyphItemPublic|ExceptionPublic|
    |GlyphGroupException|GlyphItemInternal|ExceptionInternal|
    |GlyphGroupException|GlyphItemFriend|ExceptionInternal|
    |GlyphGroupException|GlyphItemProtected|ExceptionProtected|
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemInternal|FieldInternal|
    |GlyphGroupField|GlyphItemFriend|FieldInternal|
    |GlyphGroupField|GlyphItemProtected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut 가기|
    |GlyphGroupInterface|GlyphItemPublic|인터페이스 공용|
    |GlyphGroupInterface|GlyphItemInternal|내부 인터페이스|
    |GlyphGroupInterface|GlyphItemFriend|내부 인터페이스|
    |GlyphGroupInterface|GlyphItemProtected|인터페이스 보호|
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupMacro|GlyphItemPublic|MacroPublic|
    |GlyphGroupMacro|GlyphItemInternal|MacroInternal|
    |GlyphGroupMacro|GlyphItemFriend|MacroInternal|
    |GlyphGroupMacro|GlyphItemProtected|MacroProtected|
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|
    |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|
    |GlyphGroupMap|GlyphItemPublic|MapPublic|
    |GlyphGroupMap|GlyphItemInternal|MapInternal|
    |GlyphGroupMap|GlyphItemFriend|MapInternal|
    |GlyphGroupMap|GlyphItemProtected|안 됨|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|
    |GlyphGroupMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut 가기|
    |GlyphGroupOverload|GlyphItemPublic|MethodPublic|
    |GlyphGroupOverload|GlyphItemInternal|MethodInternal|
    |GlyphGroupOverload|GlyphItemFriend|MethodInternal|
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|
    |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut 가기|
    |GlyphGroupModule|GlyphItemPublic|ModulePublic|
    |GlyphGroupModule|GlyphItemInternal|ModuleInternal|
    |GlyphGroupModule|GlyphItemFriend|ModuleInternal|
    |GlyphGroupModule|GlyphItemProtected|ModuleProtected|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|
    |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|
    |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|
    |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|
    |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|
    |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|
    |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|
    |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|
    |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|
    |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|
    |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|
    |GlyphGroupStruct|GlyphItemPublic|StructurePublic|
    |GlyphGroupStruct|GlyphItemInternal|StructureInternal|
    |GlyphGroupStruct|GlyphItemFriend|StructureInternal|
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|
    |GlyphGroupTemplate|GlyphItemPublic|템플릿 공용|
    |GlyphGroupTemplate|GlyphItemInternal|템플릿 내부|
    |GlyphGroupTemplate|GlyphItemFriend|템플릿 내부|
    |GlyphGroupTemplate|GlyphItemProtected|템플릿 보호|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInternal|유형 내부|
    |GlyphGroupType|GlyphItemFriend|유형 내부|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal|
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|
    |GlyphGroupVariable|GlyphItemProtected|FieldProtected|
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut 가기|
    |GlyphGroupValueType|GlyphItemPublic|이상 공용|
    |GlyphGroupValueType|GlyphItemInternal|고 내부|
    |GlyphGroupValueType|GlyphItemFriend|고 내부|
    |GlyphGroupValueType|GlyphItemProtected|이상 보호 됨|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut 가기|
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut 가기|
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|인터페이스 공용|
    |GlyphGroupJSharpInterface|GlyphItemInternal|내부 인터페이스|
    |GlyphGroupJSharpInterface|GlyphItemFriend|내부 인터페이스|
    |GlyphGroupJSharpInterface|GlyphItemProtected|인터페이스 보호|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||ClassFile|
    |GlyphAssembly||참조|
    |GlyphLibrary||라이브러리|
    |GlyphVBProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||대화 상자|
    |GlyphOpenFolder||FolderOpened|
    |GlyphClosedFolder||FolderClosed|
    |GlyphArrow||GoToNext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphCSharpExpansion||코드 조각|
    |GlyphKeyword||IntellisenseKeyword|
    |GlyphInformation||StatusInformation|
    |GlyphReference||ClassMethodReference|
    |GlyphRecursion||재귀|
    |GlyphXmlItem||태그|
    |GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpDocument||문서|
    |GlyphForwardType||GoToNext|
    |GlyphCallersGraph||CallTo|
    |GlyphCallGraph||CallFrom|
    |GlyphWarning||StatusWarning|
    |GlyphMaybeReference||QuestionMark|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||CallFrom|
    |GlyphExtensionMethod||ExtensionMethod|
    |GlyphExtensionMethodInternal||ExtensionMethod|
    |GlyphExtensionMethodFriend||ExtensionMethod|
    |GlyphExtensionMethodProtected||ExtensionMethod|
    |GlyphExtensionMethodPrivate||ExtensionMethod|
    |GlyphExtensionMethodShortcut||ExtensionMethod|
    |GlyphXmlAttribute||XmlAttribute|
    |GlyphXmlChild||XmlElement|
    |GlyphXmlDescendant||XmlDescendant 항목|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarning|
