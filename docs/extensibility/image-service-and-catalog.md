---
title: 이미지 서비스 및 카탈로그 | 마이크로 소프트 문서
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710385"
---
# <a name="image-service-and-catalog"></a>이미지 서비스 및 카탈로그
이 쿡북에는 Visual Studio 2015에 소개된 Visual Studio 이미지 서비스 및 이미지 카탈로그를 채택하기 위한 지침과 모범 사례가 포함되어 있습니다.

 Visual Studio 2015에 도입된 이미지 서비스를 통해 개발자는 장치에 가장 적합한 이미지를 얻을 수 있으며 사용자가 선택한 테마를 사용하여 표시되는 컨텍스트에 대한 올바른 테마를 포함하여 이미지를 표시할 수 있습니다. 이미지 서비스를 채택하면 자산 유지 관리, HDPI 크기 조정 및 테마와 관련된 주요 문제점을 제거하는 데 도움이 됩니다.

|||
|-|-|
|**오늘날의 문제**|**솔루션**|
|배경 색 혼합|내장 알파 블렌딩|
|테마(일부) 이미지|테마 메타데이터|
|고대비 모드|대체 고대비 리소스|
|다른 DPI 모드에 대해 여러 리소스필요|벡터 기반 대체를 통해 선택 가능한 리소스|
|이미지 복제|이미지 개념당 하나의 식별자|

 왜 이미지 서비스를 채택합니까?

- 항상 Visual Studio에서 최신 "픽셀 완벽한" 이미지를 얻으십시오.

- 당신은 제출하고 자신의 이미지를 사용할 수 있습니다

- Windows에서 새 DPI 크기 조정을 추가 할 때 이미지를 테스트 할 필요가 없습니다.

- 구현에서 오래된 아키텍처 장애물 해결

  이미지 서비스를 사용하기 전과 후에 Visual Studio 셸 도구 모음:

  ![이미지 서비스 이전 및 이후](../extensibility/media/image-service-before-and-after.png "이미지 서비스 이전 및 이후")

## <a name="how-it-works"></a>작동 방법
 이미지 서비스는 지원되는 모든 UI 프레임워크에 적합한 비트매핑된 이미지를 제공할 수 있습니다.

- WPF: 비트맵 소스

- 윈폼: 시스템.드로잉.비트맵

- 윈32: HBITMAP

  이미지 서비스 흐름 다이어그램

  ![이미지 서비스 흐름 다이어그램](../extensibility/media/image-service-flow-diagram.png "이미지 서비스 흐름 다이어그램")

  **이미지 모니커**

  이미지 모니커(또는 짧은 경우 모니커)는 이미지 라이브러리에서 이미지 자산 또는 이미지 목록 자산을 고유하게 식별하는 GUID/ID 쌍입니다.

  **알려진 모니커**

  Visual Studio 이미지 카탈로그에 포함된 이미지 모니커 집합이며 Visual Studio 구성 요소 또는 확장에서 공개적으로 사용할 수 있습니다.

  **이미지 매니페스트 파일**

  이미지*매니페스트(.imagemanifest)* 파일은 이미지 자산 집합, 해당 자산을 나타내는 모니커 및 각 자산을 나타내는 실제 이미지 또는 이미지를 정의하는 XML 파일입니다. 이미지 매니페스트는 레거시 UI 지원을 위해 독립 실행형 이미지 또는 이미지 목록을 정의할 수 있습니다. 또한 자산 또는 각 자산 뒤에 있는 개별 이미지에 설정하여 해당 자산이 표시되는 시기와 방법을 변경할 수 있는 특성이 있습니다.

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

 가독성 및 유지 관리 지원으로 이미지 매니페스트는 속성 값에 기호를 사용할 수 있습니다. 기호는 다음과 같이 정의됩니다.

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**하위 요소**|**정의**|
|가져오기|현재 매니페스트에서 사용할 지정된 매니페스트 파일의 기호를 가져옵니다.|
|Guid|기호는 GUID를 나타내며 GUID 서식과 일치해야 합니다.|
|ID|기호는 ID를 나타내며 음수 정수여야 합니다.|
|String|기호는 임의의 문자열 값을 나타냅니다.|

 기호는 대/소문자를 구분하며 $(기호 이름) 구문을 사용하여 참조됩니다.

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 일부 기호는 모든 매니페스트에 대해 미리 정의되어 있습니다. \<소스> 또는 \<가져오기> 요소의 Uri 특성에서 로컬 컴퓨터의 참조 경로를 참조하는 데 사용할 수 있습니다.

|||
|-|-|
|**기호**|**설명**|
|CommonProgramFiles|%공통프로그램파일% 환경 변수값|
|로컬 앱데이터|%LocalAppData% 환경 변수의 값|
|매니페스트 폴더|매니페스트 파일이 들어 있는 폴더|
|마이 문서|현재 사용자의 내 문서 폴더의 전체 경로|
|ProgramFiles|%ProgramFiles% 환경 변수의 값|
|시스템|*윈도우\System32* 폴더|
|Windir|%WinDir% 환경 변수의 값|

 **이미지**

 \<이미지> 요소는 모니커에서 참조할 수 있는 이미지를 정의합니다. 함께 가져온 GUID와 ID는 이미지 모니커를 형성합니다. 이미지의 모니커는 전체 이미지 라이브러리에서 고유해야 합니다. 두 개 이상의 이미지에 지정된 모니커가 있는 경우 라이브러리를 빌드하는 동안 처음 발생한 이미지는 유지되는 이미지입니다.

 하나 이상의 소스를 포함해야 합니다. 크기 중립적 인 소스는 광범위한 크기에서 최상의 결과를 제공하지만 필수는 아닙니다. 서비스가 \<이미지> 요소에 정의되지 않은 크기의 이미지를 요청받고 크기 중립적 소스가 없는 경우 서비스는 최상의 크기별 소스를 선택하고 요청된 크기로 크기를 조정합니다.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**attribute**|**정의**|
|Guid|[필수] 이미지 모니커의 GUID 부분|
|ID|[필수] 이미지 모니커의 ID 부분|
|허용색상 반전|[선택 사항, 기본 true] 어두운 배경에서 사용할 때 이미지의 색상이 프로그래밍 방식으로 반전될 수 있는지 여부를 나타냅니다.|

 **원본**

 \<소스> 요소는 단일 이미지 원본 자산(XAML 및 PNG)을 정의합니다.

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**attribute**|**정의**|
|Uri|[필수] 이미지를 로드할 수 있는 위치를 정의하는 URI입니다. 다음 중 하나일 수 있습니다.<br /><br /> - application:/// 기관을 사용하는 [팩 URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br />- 절대 구성 요소 리소스 참조<br />- 네이티브 리소스를 포함하는 파일에 대한 경로|
|배경|[선택 사항] 소스가 사용할 배경의 종류를 나타냅니다.<br /><br /> 다음 중 하나일 수 있습니다.<br /><br /> *빛:* 소스는 밝은 배경에서 사용할 수 있습니다.<br /><br /> *어두운:* 소스는 어두운 배경에서 사용할 수 있습니다.<br /><br /> *고대비:* 소스는 고대비 모드에서 모든 백그라운드에서 사용할 수 있습니다.<br /><br /> *고대비라이트:* 소스는 고대비 모드에서 밝은 배경에서 사용할 수 있습니다.<br /><br /> *고대비다크:* 소스는 고대비 모드에서 어두운 배경에서 사용할 수 있습니다.<br /><br /> Background 특성이 생략된 경우 모든 백그라운드에서 소스를 사용할 수 있습니다.<br /><br /> 배경이 *밝은*경우, *어둡고,* *대비광이 약하거나,* *대비극을 높이거나, 대비암색이 높으면*소스의 색상이 반전되지 않습니다. 배경을 생략하거나 *고대비로*설정된 경우 소스 색상의 반전은 이미지의 **AllowColor반전** 특성에 의해 제어됩니다.|

\<소스> 요소는 다음 선택적 하위 요소 중 하나를 가질 수 있습니다.

||||
|-|-|-|
|**요소**|**특성(모두 필수)**|**정의**|
|\<크기>|값|소스는 지정된 크기의 이미지(장치 단위)에 사용됩니다. 이미지가 정사각형이 됩니다.|
|\<크기 범위>|최소 크기, 최대 크기|소스는 MinSize에서 MaxSize(장치 단위)까지의 이미지에 포함되는 데 사용됩니다. 이미지가 정사각형이 됩니다.|
|\<치수>|너비, 높이|소스는 지정된 너비와 높이의 이미지(장치 단위)에 사용됩니다.|
|\<차원 범위>|최소 너비, 최소 높이,<br /><br /> 최대 폭, 최대 높이|소스는 최소 너비/높이에서 최대 너비/높이(장치 단위)까지의 이미지에 대해 포함됩니다.|

 소스> 요소에는 관리되는 \<어셈블리가 아닌 네이티브 \<어셈블리에서 로드되는 소스> 정의하는 선택적 NativeResource> 하위 요소도 있을 수 있습니다. \<

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**attribute**|**정의**|
|형식|[필수] XAML 또는 PNG의 네이티브 리소스 유형|
|ID|[필수] 네이티브 리소스의 정수 ID 부분|

 **Imagelist**

 \<ImageList> 요소는 단일 스트립에서 반환할 수 있는 이미지 컬렉션을 정의합니다. 스트립은 필요에 따라 필요에 따라 제작됩니다.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**attribute**|**정의**|
|Guid|[필수] 이미지 모니커의 GUID 부분|
|ID|[필수] 이미지 모니커의 ID 부분|
|외부|[선택 사항, 기본 거짓] 이미지 모니커가 현재 매니페스트에서 이미지를 참조하는지 여부를 나타냅니다.|

 포함된 이미지의 모니커는 현재 매니페스트에 정의된 이미지를 참조할 필요가 없습니다. 포함된 이미지를 이미지 라이브러리에서 찾을 수 없는 경우 빈 자리 표시자 이미지가 그 자리에서 사용됩니다.

## <a name="using-the-image-service"></a>이미지 서비스 사용

### <a name="first-steps-managed"></a>첫 번째 단계(관리)
 이미지 서비스를 사용하려면 다음 어셈블리 중 일부 또는 전부에 대한 참조를 프로젝트에 추가해야 합니다.

- *마이크로소프트.비주얼 스튜디오.이미지카탈로그.dll*

  - 기본 제공 이미지 카탈로그 **KnownMonikers를**사용하는 경우 필요합니다.

- *마이크로소프트.비주얼 스튜디오.이미징.dll*

  - WPF UI에서 **선명한 이미지** 및 **이미지Them유틸리티를** 사용하는 경우 필요합니다.

- *마이크로소프트.비주얼스튜디오.이미징.인터롭.14.0.디자인타임.dll*

  - **ImageMoniker** 및 **ImageAttributes** 유형을 사용하는 경우 필요합니다.

  - **임베드인터옵타입은** true로 설정되어야 합니다.

- *마이크로소프트.비주얼스튜디오.쉘.인터롭.14.0.디자인타임*

  - **당신이 IVsImageService2** 유형을 사용하는 경우 필요합니다.

  - **임베드인터옵타입은** true로 설정되어야 합니다.

- *마이크로소프트.비주얼 스튜디오.유틸리티.dll*

  - 이미지에 대 한 **BrushToColorConverter를** 사용 하는 경우 **필요.이미지배경 색상** WPF UI에서.

- *마이크로소프트.비주얼 스튜디오.쉘. \<VS버전>.0*

  - **IVsUIObject** 형식을 사용하는 경우 필요합니다.

- *마이크로소프트.비주얼 스튜디오.쉘.인터롭.10.0.dll*

  - WinForms 관련 UI 도우미를 사용하는 경우 필요합니다.

  - **임베드인터옵타입은** true로 설정해야 합니다.

### <a name="first-steps-native"></a>첫 번째 단계(기본 단계)
 이미지 서비스를 사용하려면 다음 헤더의 일부 또는 전부를 프로젝트에 포함해야 합니다.

- **알려진 이미지 Ids.h**

  - 기본 제공 이미지 카탈로그 **KnownMonikers를**사용 하지만 **IVsHierarchy GetGuidProperty** 또는 **GetProperty** 호출에서 값을 반환 하는 경우와 같은 **ImageMoniker** 형식을 사용할 수 없습니다.

- **알려진 모니커스.h**

  - 기본 제공 이미지 카탈로그 **KnownMonikers를**사용하는 경우 필요합니다.

- **이미지매개 변수140.h**

  - **ImageMoniker** 및 **ImageAttributes** 유형을 사용하는 경우 필요합니다.

- **VSShell140.h**

  - **당신이 IVsImageService2** 유형을 사용하는 경우 필요합니다.

- **이미지테마잉유틸리티.h**

  - 이미지 서비스에서 테마를 처리할 수 없는 경우 필요합니다.

  - 이미지 서비스에서 이미지 테마를 처리할 수 있는 경우 이 헤더를 사용하지 마십시오.

::: moniker range="vs-2017"
- **VSUIDPI헬프어.h**

  - 현재 DPI를 얻으려면 DPI 도우미를 사용하는 경우 필요합니다.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - 현재 DPI를 얻으려면 DPI 인식 도우미를 사용하는 경우 필요합니다.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>새 WPF UI를 작성하려면 어떻게 해야 합니까?

1. 먼저 위의 첫 번째 단계 섹션에 필요한 어셈블리 참조를 프로젝트에 추가합니다. 모든 것을 추가할 필요는 없으므로 필요한 참조만 추가합니다. (참고: **브러시**대신 **색상을** 사용하거나 액세스할 수 있는 경우 변환기가 필요하지 않으므로 **유틸리티에**대한 참조를 건너뛸 수 있습니다.)

2. 원하는 이미지를 선택하고 모니커를 가져옵니다. **KnownMoniker를**사용하거나 사용자 지정 이미지와 모니커가 있는 경우 직접 사용합니다.

3. XAML에 **선명한 이미지를** 추가합니다. (아래 예제를 참조하십시오.)

4. UI 계층 구조에서 **이미지 채점유틸리티.ImageBackgroundColor** 속성을 설정합니다. (이 설정 해야 배경 색은 알려진 위치에, 반드시 **는 CrispImage**.) (아래 예제를 참조하십시오.)

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

 **기존 WPF UI를 업데이트하려면 어떻게 해야 합니까?**

 기존 WPF UI 업데이트는 세 가지 기본 단계로 구성된 비교적 간단한 프로세스입니다.

1. UI의 \<모든 이미지> \<요소를 CrispImage> 요소로 바꿉으로 바꿉꿉으로 바꿉꿉을 바꿉꿉으로 바꿉꿉을 올바랄 뿐입니다.

2. 모든 소스 특성을 Moniker 특성으로 변경합니다.

    - 이미지가 변경되지 않으며 **KnownMonikers를**사용하는 경우 해당 속성을 **KnownMoniker**에 정적으로 바인딩합니다. (위의 예제를 참조하십시오.)

    - 이미지가 변경되지 않으며 사용자 지정 이미지를 사용하는 경우 사용자 고유의 모니커에 정적으로 바인딩합니다.

    - 이미지가 변경될 수 있는 경우 Moniker 특성을 속성 변경 내용을 알리는 코드 속성에 바인딩합니다.

3. UI 계층 의 어딘가에 **이미지ThemingUtilities.ImageBackgroundColor를** 설정하여 색상 반전이 올바르게 작동하는지 확인합니다.

    - 이렇게 하려면 **BrushToColorConverter** 클래스를 사용해야 할 수 있습니다. (위의 예제를 참조하십시오.)

## <a name="how-do-i-update-win32-ui"></a>Win32 UI를 업데이트하려면 어떻게 해야 합니까?
 이미지의 원시 로드를 대체하기 위해 적절한 경우 코드에 다음을 추가합니다. 필요에 따라 HBITMAPs대 HICONs 대 히마지리스트를 반환하는 값을 전환합니다.

 **이미지 서비스 받기**

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

## <a name="how-do-i-update-winforms-ui"></a>WinForms UI를 업데이트하려면 어떻게 해야 합니까?
 이미지의 원시 로드를 대체하기 위해 적절한 경우 코드에 다음을 추가합니다. 필요에 따라 비트맵과 아이콘을 반환하기 위한 값을 전환합니다.

 **문 사용 에 도움이**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **이미지 서비스 받기**

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

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>새 도구 창에서 이미지 모니커를 사용하려면 어떻게 해야 합니까?
 VSIX 패키지 프로젝트 템플릿이 Visual Studio 2015용으로 업데이트되었습니다. 새 도구 창을 만들려면 VSIX 프로젝트를 마우스 오른쪽 단추로 클릭하고 > **새 항목** +**Shift**+**추가(Ctrl**Shift**A)를**선택합니다. **Add** 프로젝트 언어의 확장성 노드 아래에서 **사용자 지정 도구 창을**선택하고 도구 창에 이름을 지정하고 **추가** 단추를 누릅니다.

 도구 창에서 모니커를 사용하는 주요 장소입니다. 각 방법에 대한 지침을 따르십시오.

1. 탭이 충분히 작아지면 도구 창 탭이 **됩니다(Ctrl**+**Tab** 창 스위처에서도 사용).

    **ToolWindowPane** 형식에서 파생 되는 클래스에 대 한 생성자에 이 줄을 추가 합니다.

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. 도구 창을 여는 명령입니다.

    패키지의 *.vsct* 파일에서 도구 창의 명령 단추를 편집합니다.

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

   **기존 도구 창에서 이미지 모니커를 사용하려면 어떻게 해야 합니까?**

   이미지 모니커를 사용하도록 기존 도구 창을 업데이트하는 것은 새 도구 창을 만드는 단계와 유사합니다.

   도구 창에서 모니커를 사용하는 주요 장소입니다. 각 방법에 대한 지침을 따르십시오.

3. 탭이 충분히 작아지면 도구 창 탭이 **됩니다(Ctrl**+**Tab** 창 스위처에서도 사용).

   1. **ToolWindowPane** 형식에서 파생된 클래스의 생성자에서 이러한 줄(있는 경우)을 제거합니다.

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. "새 도구 창에서 이미지 모니커를 사용하려면 어떻게 해야 합니까?" #1 단계를 참조하십시오. 섹션을 참조하십시오.

4. 도구 창을 여는 명령입니다.

   - "새 도구 창에서 이미지 모니커를 사용하려면 어떻게 해야 합니까?" #2 단계를 참조하십시오. 섹션을 참조하십시오.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>.vsct 파일에서 이미지 모니커를 사용하려면 어떻게 해야 합니까?
 아래 주석 줄로 표시된 대로 *.vsct* 파일을 업데이트합니다.

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

 **이전 버전의 Visual Studio에서도 .vsct 파일을 읽어야 하는 경우 어떻게 해야 합니까?**

 이전 버전의 Visual Studio에서는 **IconIsMoniker** 명령 플래그를 인식하지 못합니다. 이를 지원하는 Visual Studio 버전에서 이미지 서비스의 이미지를 사용할 수 있지만 이전 버전의 Visual Studio에서는 이전 스타일의 이미지를 계속 사용할 수 있습니다. 이렇게 하려면 *.vsct* 파일을 변경하지 않고(이전 버전의 Visual Studio와 호환됨) *.vsct* 파일의 \<비트맵> 요소에 정의된 GUID/ID 쌍에서 이미지 모니커 GUID/ID 쌍에 매핑하는 CSV(쉼표 구분값) 파일을 만듭니다.

 매핑 CSV 파일의 형식은 다음과 입니다.

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 CSV 파일은 패키지와 함께 배포되며 해당 위치는 **ProvideMenuResource** 패키지 특성의 **IconMappingFilename** 속성에 의해 지정됩니다.

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename은** 암시적으로 $PackageFolder$(위의 예와 같이)에 암시적으로 뿌리를 둔 상대 경로이거나 *@"%UserProfile%\dir1\MyMappingFile.csv"와*같은 환경 변수에 의해 정의된 디렉토리에 명시적으로 루팅된 절대 경로입니다.

## <a name="how-do-i-port-a-project-system"></a>프로젝트 시스템을 포팅하려면 어떻게 해야 합니까?
 **프로젝트에 ImageMonikers를 공급하는 방법**

1. 프로젝트의 **iVsHierarchy에서** **VSHPROPID_SupportsIconMonikers** 구현하고 true를 반환합니다.

2. **VSHPROPID_IconMonikerImageList(원래** 프로젝트가 **VSHPROPID_IconImgList**사용된 경우) 또는 **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId** **VSHPROPID_OpenFolderIconMonikerGuid** **VSHPROPID_OpenFolderIconMonikerId(원래** 프로젝트가 **VSHPROPID_IconHandle** 사용된 경우 및 **VSHPROPID_OpenFolderIconHandle)를**구현합니다.

3. 확장 지점이 요청하는 경우 아이콘의 "레거시" 버전을 만들려면 아이콘에 대한 원래 VSHPROPID의 구현을 변경합니다. **IVsImageService2는** 이러한 아이콘을 얻는 데 필요한 기능을 제공합니다.

   **VB/C# 프로젝트 맛에 대한 추가 요구 사항**

   프로젝트가 **가장 바깥쪽 맛임을**감지하는 경우에만 **VSHPROPID_SupportsIconMonikers** 구현합니다. 그렇지 않으면 실제 바깥쪽 의 맛은 실제로 이미지 모니커를 지원하지 않을 수 있으며 기본 맛은 사용자 정의 이미지를 효과적으로 "숨길"수 있습니다.

   **CPS에서 이미지 모니커를 사용하려면 어떻게 해야 합니까?**

   CPS(공통 프로젝트 시스템)에서 사용자 지정 이미지를 설정하거나 프로젝트 시스템 확장성 SDK와 함께 제공되는 항목 템플릿을 통해 수행할 수 있습니다.

   **프로젝트 시스템 확장성 SDK 사용**

   [프로젝트 유형/항목 유형에 대한 사용자 지정 아이콘 제공의](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) 지침을 따라 CPS 이미지를 사용자 지정합니다. CPS에 대한 자세한 내용은 [Visual Studio 프로젝트 시스템 확장성 설명서에서](https://github.com/Microsoft/VSProjectSystem) 확인할 수 있습니다.

   **수동으로 이미지모니커 사용**

4. 프로젝트 시스템에서 **IProjectTreeModifier** 인터페이스를 구현하고 내보냅니다.

5. 사용할 **KnownMoniker** 또는 사용자 지정 이미지 모니커를 결정합니다.

6. **ApplyModifications** 메서드에서 아래 예제와 마찬가지로 새 트리를 반환 하기 전에 메서드의 어딘가에 다음을 수행 합니다.

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. 새 트리를 만드는 경우 아래 예제와 마찬가지로 원하는 모니커를 NewTree 메서드로 전달하여 사용자 지정 이미지를 설정할 수 있습니다.

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>실제 이미지 스트립에서 모니커 기반 이미지 스트립으로 변환하려면 어떻게 해야 합니까?
 **히마겔리스를 지원해야 합니다.**

 이미지 서비스를 사용하도록 업데이트하려는 코드에 이미 기존 이미지 스트립이 있지만 이미지 목록을 전달해야 하는 API에 제약을 받는 경우에도 이미지 서비스의 이점을 얻을 수 있습니다. 모니커 기반 이미지 스트립을 만들려면 아래 단계를 따라 기존 모니커에서 매니페스트를 만듭니다.

1. **매니페스트를 실행FromResources** 도구를 실행, 그것을 전달 하는 이미지 스트립. 이렇게 하면 스트립에 대한 매니페스트가 생성됩니다.

   - 권장 사항: 매니페스트의 사용량에 맞게 매니페스트에 대한 기본이름이 아닌 이름을 제공합니다.

2. **KnownMonikers만**사용하는 경우 다음을 수행합니다.

   - 매니페스트의 \<이미지> 섹션을 \<이미지/> 바꿉을 바꿉습니다.

   - 모든 하위 이미지 아이디(이미지트립 \<이름이 있는 모든 것>_ ##)를 제거합니다.

   - 권장 사항: AssetsGuid 기호 및 이미지 스트립 기호의 용도에 맞게 이름을 바꿉니다.

   - 각 **포함 이미지의**GUID를 $(ImageCatalogGuid)로 바꾸고, 각 포함된\< **이미지의**ID를 $(모니커>)로 바꾸고, 각 포함 이미지에 외부="true" 특성을 **추가합니다.**

       - \<모니커> 이미지와 일치하지만 "알려진 **모니커"로** 대체되어야 합니다. 이름에서 제거됩니다.

   - <\\ 가져오기 매니페스트 ="$(ManifestFolder)<상대\>설치 dir 경로를 * \Microsoft.VisualStudio.ImageCatalog.imagemanifest"/\* \<기호> 섹션의 상단에> 추가합니다.

       - 상대 경로는 매니페스트에 대한 설치 작성에 정의된 배포 위치에 의해 결정됩니다.

3. **ManifestToCode** 도구를 실행하여 래퍼를 생성하여 기존 코드에 이미지 스트립에 대한 이미지 서비스를 쿼리하는 데 사용할 수 있는 모니커가 있습니다.

   - 권장: 래퍼 및 네임스페이스의 기본값이 아닌 이름을 해당 용도에 맞게 제공합니다.

4. 이미지 서비스 및 새 파일로 작업할 모든 추가, 설치 작성/배포 및 기타 코드 변경 작업을 수행합니다.

   내부 및 외부 이미지를 모두 포함하는 샘플 매니페스트를 사용하여 다음과 같이 표시해야 합니다.

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

 **히마겔리스를 지원할 필요가 없습니다.**

1. 이미지 스트립의 이미지와 일치하는 **KnownMonikers** 집합을 결정하거나 이미지 스트립의 이미지에 대해 고유한 모니커를 만듭니다.

2. 대신 모니커를 사용 하 여 이미지 스트립에 필요한 인덱스에서 이미지를 얻기 위해 사용 하는 모든 매핑을 업데이트 합니다.

3. 업데이트된 매핑을 통해 모니커를 요청하려면 이미지 서비스를 사용하도록 코드를 업데이트합니다. 이는 관리 코드에 대해 **CrispImages로** 업데이트하거나 이미지 서비스에서 HBITMAPs 또는 HICONs를 요청하고 네이티브 코드에 대해 전달하는 것을 의미할 수 있습니다.

## <a name="testing-your-images"></a>이미지 테스트
 이미지 라이브러리 뷰어 도구를 사용하여 이미지 매니페스트를 테스트하여 모든 것이 올바르게 작성되었는지 확인할 수 있습니다. 이 도구는 Visual [Studio 2015 SDK에서](visual-studio-sdk.md)찾을 수 있습니다. 이 도구 및 기타 도구에 대한 설명서는 [여기에서](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015)찾을 수 있습니다.

## <a name="additional-resources"></a>추가 자료

### <a name="samples"></a>샘플
 GitHub의 여러 Visual Studio 샘플이 업데이트되어 다양한 Visual Studio 확장성 지점의 일부로 이미지 서비스를 사용하는 방법을 보여 주도록 업데이트되었습니다.

 최신 [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 샘플을 확인합니다.

### <a name="tooling"></a>도구
 이미지 서비스와 함께 작동하는 UI를 만들고 업데이트하는 데 도움이 되도록 이미지 서비스에 대한 지원 도구 집합이 만들어졌습니다. 각 도구에 대한 자세한 내용은 도구와 함께 제공되는 설명서를 참조하십시오. 이 도구는 [Visual Studio 2015 SDK의](visual-studio-sdk.md)일부로 포함되어 있습니다.

 **매니페스트자원**

 리소스의 매니페스트 도구는 PNG 또는 XAML(이미지 리소스) 목록을 가져와 이미지 서비스와 함께 해당 이미지를 사용하기 위한 이미지 매니페스트 파일을 생성합니다.

 **매니페스트토코드**

 코드에 매니페스트 도구는 이미지 매니페스트 파일을 가져와 코드(C++, C# 또는 VB) 또는 *.vsct* 파일에서 매니페스트 값을 참조하기 위한 래퍼 파일을 생성합니다.

 **이미지 라이브러리뷰어**

 이미지 라이브러리 뷰어 도구는 이미지 매니페스트를 로드할 수 있으며 Visual Studio에서 매니페스트가 올바르게 작성되었는지 확인하는 것과 동일한 방식으로 이미지 매니페스트를 조작할 수 있습니다. 사용자는 배경, 크기, DPI 설정, 대대비 및 기타 설정을 변경할 수 있습니다. 또한 매니페스트에서 오류를 찾기 위해 로딩 정보를 표시하고 매니페스트의 각 이미지에 대한 소스 정보를 표시합니다.

## <a name="faq"></a>FAQ

- 참조 포함="Microsoft.VisualStudio.*를 \<로드할 때 포함해야 하는 종속성이 있습니까? Interop.14.0.DesignTime" />?

  - 모든 interop DLL에서 임베드인터옵타입="true"를 설정합니다.

- 확장과 함께 이미지 매니페스트를 배포하려면 어떻게 해야 합니까?

  - 프로젝트에 *.imagemanifest* 파일을 추가합니다.

  - "VSIX에 포함"을 True로 설정합니다.

- CPS 프로젝트 시스템을 업데이트하고 있습니다. **이미지 이름과** **주식아이콘 서비스에**무슨 일이 있었습니까?

  - 이러한 제거 는 CPS 모니커를 사용 하 여 업데이트 되었습니다. 더 이상 **StockIconService를**호출 할 필요가 없습니다, 그냥 CPS 유틸리티에서 **ToProjectSystemType()** 확장 방법을 사용하여 메서드 또는 속성에 원하는 **KnownMoniker를** 전달합니다. **아래에서 이미지네임에서** **KnownMonikers로** 의 매핑을 찾을 수 있습니다.

    |||
    |-|-|
    |**ImageName**|**알려진 모니커**|
    |이미지네임.오프라인웹앱|알려진 이미지 Ids.웹|
    |이미지 이름.웹 참조폴더|알려진 이미지 Ids.웹|
    |이미지이름.오픈레퍼런스폴더|알려진 이미지 Ids.폴더 열|
    |이미지네임.레퍼런스폴더|알려진 이미지 Ids.참조|
    |이미지 이름.참조|알려진 이미지 Ids.참조|
    |이미지 이름.SdlWeb참조|알려진 이미지 Ids.웹 참조 폴더|
    |이미지네임.디스코웹참조|알려진 이미지 Ids.동적 디스커버리문서|
    |이미지 이름.폴더|알려진 이미지 Ids.폴더닫힘|
    |이미지이름.오픈폴더|알려진 이미지 Ids.폴더 열|
    |이미지 이름.제외폴더|알려진 이미지 Ids.숨겨진폴더폐쇄|
    |이미지 이름.열기제외폴더|알려진 이미지 Ids.숨겨진폴더오픈|
    |이미지 이름.제외파일|알려진 이미지 Ids.HiddenFile|
    |이미지 이름.종속 파일|알려진 이미지 Ids.생성파일|
    |이미지 이름.누락된 파일|알려진 이미지 Ids.문서 경고|
    |이미지이름.윈도우폼|알려진이미지Ids.윈도우폼|
    |이미지이름.윈도우사용자제어|알려진 이미지 Ids.사용자 제어|
    |이미지 이름.윈도우컴포넌트|알려진 이미지 Ids.구성 요소 파일|
    |이미지네임.XmlSchema|알려진 이미지 Ids.XMLSchema|
    |이미지네임.XmlFile|알려진 이미지 Ids.XML파일|
    |이미지네임.웹폼|알려진 이미지 Ids.웹|
    |이미지네임.웹서비스|알려진 이미지 Ids.웹 서비스|
    |이미지 이름.웹사용자 제어|알려진 이미지 Ids.웹 사용자 제어|
    |이미지 이름.웹 사용자 제어|알려진 이미지 Ids.웹 사용자 정의 제어|
    |이미지네임.아스프페이지|알려진 이미지 Ids.ASP파일|
    |이미지 이름.글로벌 응용 프로그램 클래스|알려진 이미지 Ids.설정파일|
    |이미지네임.웹콘피그|알려진 이미지 Ids.구성파일|
    |이미지네임.HtmlPage|알려진 이미지 Ids.HTML파일|
    |이미지 이름.스타일 시트|알려진 이미지 Ids.스타일 시트|
    |이미지 이름.스크립트파일|알려진 이미지 Ids.JSScript|
    |이미지 이름.텍스트 파일|알려진 이미지 Ids.문서|
    |이미지 이름.설정파일|알려진 이미지 Ids.설정|
    |이미지 이름.리소스|알려진 이미지 Ids.문서 그룹|
    |이미지네임.비트맵|알려진 이미지 Ids.이미지|
    |이미지 이름.아이콘|알려진 이미지 Ids.아이콘파일|
    |이미지 이름.이미지|알려진 이미지 Ids.이미지|
    |이미지네임.이미지맵|알려진 이미지 Ids.이미지맵 파일|
    |이미지네임.XWorld|알려진 이미지 Ids.X월드파일|
    |이미지네임.오디오|알려진 이미지 Ids.사운드|
    |이미지 네임.비디오|알려진 이미지 Ids.미디어|
    |이미지네임.캡|알려진 이미지 Ids.CAB 프로젝트|
    |이미지네임.Jar|알려진 이미지 Ids.JAR파일|
    |이미지 이름.데이터환경|알려진 이미지 Ids.데이터 테이블|
    |이미지 이름.미리 보기파일|알려진 이미지 Ids.보고서|
    |이미지이름.매달려 참조|알려진 이미지 Ids.참조 경고|
    |이미지네임.XsltFile|알려진 이미지 Ids.XSL변환|
    |이미지이름.커서|알려진 이미지 Ids.커서파일|
    |이미지네임.앱디자이너폴더|알려진 이미지 Ids.속성|
    |이미지 이름.데이터|알려진 이미지 Ids.데이터베이스|
    |이미지 이름.응용 프로그램|알려진 이미지 Ids.응용 프로그램|
    |이미지 이름.데이터 집합|알려진 이미지 Ids.데이터베이스 그룹|
    |이미지네임.Pfx|알려진 이미지 Ids.인증서|
    |이미지네임.Snk|알려진 이미지 Ids.규칙|
    |이미지네임.비주얼베이직프로젝트|알려진 이미지 Ids.VB프로젝트노드|
    |이미지이름.C샤프프로젝트|알려진 이미지 Ids.CS프로젝트노드|
    |이미지 이름.비어 있음|알려진 이미지 Id.Blank|
    |이미지 이름.누락된 폴더|알려진 이미지 Ids.폴더오프라인|
    |이미지 이름.공유 가져오기 참조|알려진 이미지 Ids.공유 프로젝트|
    |이미지네임.공유프로젝트|알려진 이미지 Ids.CS공유 프로젝트|
    |이미지네임.공유프로젝트Vc|알려진 이미지 Ids.CPP 공유 프로젝트|
    |이미지네임.공유프로젝트Js|알려진 이미지 Ids.JSShared 프로젝트|
    |이미지 이름.C샤프코드파일|알려진 이미지 Ids.CS파일노드|
    |이미지 이름.비주얼 베이직코드파일|알려진 이미지 Ids.VB파일노드|

  - 완료 목록 공급자를 업데이트하고 있습니다. 알려진 **모니커가** 이전 **스탠다드글리프 그룹** 및 **스탠다드글리프** 값과 일치하는 것은 무엇입니까?

    ||||
    |-|-|-|
    |글리프그룹클래스|글리프아이템퍼블릭|클래스퍼블릭|
    |글리프그룹클래스|글리프아이템 내부|클래스 내부|
    |글리프그룹클래스|글리프아이템프렌드|클래스 내부|
    |글리프그룹클래스|글리프항목보호|클래스 보호|
    |글리프그룹클래스|글리프아이템프라이빗|클래스프라이빗|
    |글리프그룹클래스|글리프아이템 바로 가기|클래스 바로 가기|
    |글리프그룹 콘티드|글리프아이템퍼블릭|상수 공개|
    |글리프그룹 콘티드|글리프아이템 내부|상수 내부|
    |글리프그룹 콘티드|글리프아이템프렌드|상수 내부|
    |글리프그룹 콘티드|글리프항목보호|상수 보호|
    |글리프그룹 콘티드|글리프아이템프라이빗|상수개인|
    |글리프그룹 콘티드|글리프아이템 바로 가기|상수 바로 가기|
    |글리프그룹대리자|글리프아이템퍼블릭|대리자공개|
    |글리프그룹대리자|글리프아이템 내부|대리자 내부|
    |글리프그룹대리자|글리프아이템프렌드|대리자 내부|
    |글리프그룹대리자|글리프항목보호|대리자 보호|
    |글리프그룹대리자|글리프아이템프라이빗|대리자프라이빗|
    |글리프그룹대리자|글리프아이템 바로 가기|대리자 바로 가기|
    |글리프그룹에눔|글리프아이템퍼블릭|열거공개|
    |글리프그룹에눔|글리프아이템 내부|열거내부|
    |글리프그룹에눔|글리프아이템프렌드|열거내부|
    |글리프그룹에눔|글리프항목보호|열거보호|
    |글리프그룹에눔|글리프아이템프라이빗|열거개인|
    |글리프그룹에눔|글리프아이템 바로 가기|열거 바로 가기|
    |글리프그룹에눔회원|글리프아이템퍼블릭|열거항목공개|
    |글리프그룹에눔회원|글리프아이템 내부|열거항목 내부|
    |글리프그룹에눔회원|글리프아이템프렌드|열거항목 내부|
    |글리프그룹에눔회원|글리프항목보호|열거항목보호|
    |글리프그룹에눔회원|글리프아이템프라이빗|열거항목개인|
    |글리프그룹에눔회원|글리프아이템 바로 가기|열거항목 바로 가기|
    |글리프 그룹이벤트|글리프아이템퍼블릭|이벤트 공개|
    |글리프 그룹이벤트|글리프아이템 내부|이벤트 내부|
    |글리프 그룹이벤트|글리프아이템프렌드|이벤트 내부|
    |글리프 그룹이벤트|글리프항목보호|이벤트 보호|
    |글리프 그룹이벤트|글리프아이템프라이빗|이벤트프라이빗|
    |글리프 그룹이벤트|글리프아이템 바로 가기|이벤트 바로 가기|
    |글리프 그룹예외|글리프아이템퍼블릭|예외공개|
    |글리프 그룹예외|글리프아이템 내부|예외 내부|
    |글리프 그룹예외|글리프아이템프렌드|예외 내부|
    |글리프 그룹예외|글리프항목보호|예외 보호|
    |글리프 그룹예외|글리프아이템프라이빗|예외프라이빗|
    |글리프 그룹예외|글리프아이템 바로 가기|예외 바로 가기|
    |글리프그룹필드|글리프아이템퍼블릭|필드퍼블릭|
    |글리프그룹필드|글리프아이템 내부|필드 내부|
    |글리프그룹필드|글리프아이템프렌드|필드 내부|
    |글리프그룹필드|글리프항목보호|필드 보호|
    |글리프그룹필드|글리프아이템프라이빗|필드프라이빗|
    |글리프그룹필드|글리프아이템 바로 가기|필드 바로 가기|
    |글리프 그룹인터페이스|글리프아이템퍼블릭|인터페이스공용|
    |글리프 그룹인터페이스|글리프아이템 내부|인터페이스 내부|
    |글리프 그룹인터페이스|글리프아이템프렌드|인터페이스 내부|
    |글리프 그룹인터페이스|글리프항목보호|인터페이스 보호|
    |글리프 그룹인터페이스|글리프아이템프라이빗|인터페이스개인|
    |글리프 그룹인터페이스|글리프아이템 바로 가기|인터페이스 바로 가기|
    |글리프그룹매크로|글리프아이템퍼블릭|매크로 퍼블릭|
    |글리프그룹매크로|글리프아이템 내부|매크로 내부|
    |글리프그룹매크로|글리프아이템프렌드|매크로 내부|
    |글리프그룹매크로|글리프항목보호|매크로 보호|
    |글리프그룹매크로|글리프아이템프라이빗|매크로 프라이빗|
    |글리프그룹매크로|글리프아이템 바로 가기|매크로 바로 가기|
    |글리프그룹맵|글리프아이템퍼블릭|맵퍼블릭|
    |글리프그룹맵|글리프아이템 내부|지도 내부|
    |글리프그룹맵|글리프아이템프렌드|지도 내부|
    |글리프그룹맵|글리프항목보호|지도 보호|
    |글리프그룹맵|글리프아이템프라이빗|맵프라이빗|
    |글리프그룹맵|글리프아이템 바로 가기|지도 바로 가기|
    |글리프그룹맵항목|글리프아이템퍼블릭|맵아이템퍼블릭|
    |글리프그룹맵항목|글리프아이템 내부|맵아이템 내부|
    |글리프그룹맵항목|글리프아이템프렌드|맵아이템 내부|
    |글리프그룹맵항목|글리프항목보호|맵항목보호|
    |글리프그룹맵항목|글리프아이템프라이빗|맵아이템프라이빗|
    |글리프그룹맵항목|글리프아이템 바로 가기|맵항목 바로 가기|
    |글리프그룹메소드|글리프아이템퍼블릭|메소드퍼블릭|
    |글리프그룹메소드|글리프아이템 내부|방법 내부|
    |글리프그룹메소드|글리프아이템프렌드|방법 내부|
    |글리프그룹메소드|글리프항목보호|MethodProtected|
    |글리프그룹메소드|글리프아이템프라이빗|메서드개인|
    |글리프그룹메소드|글리프아이템 바로 가기|메서드 바로 가기|
    |글리프그룹 과부하|글리프아이템퍼블릭|메소드퍼블릭|
    |글리프그룹 과부하|글리프아이템 내부|방법 내부|
    |글리프그룹 과부하|글리프아이템프렌드|방법 내부|
    |글리프그룹 과부하|글리프항목보호|MethodProtected|
    |글리프그룹 과부하|글리프아이템프라이빗|메서드개인|
    |글리프그룹 과부하|글리프아이템 바로 가기|메서드 바로 가기|
    |글리프그룹모듈|글리프아이템퍼블릭|모듈퍼블릭|
    |글리프그룹모듈|글리프아이템 내부|모듈 내부|
    |글리프그룹모듈|글리프아이템프렌드|모듈 내부|
    |글리프그룹모듈|글리프항목보호|모듈 보호|
    |글리프그룹모듈|글리프아이템프라이빗|모듈프라이빗|
    |글리프그룹모듈|글리프아이템 바로 가기|모듈 바로 가기|
    |글리프그룹네임스페이스|글리프아이템퍼블릭|네임스페이스퍼블릭|
    |글리프그룹네임스페이스|글리프아이템 내부|네임스페이스 내부|
    |글리프그룹네임스페이스|글리프아이템프렌드|네임스페이스 내부|
    |글리프그룹네임스페이스|글리프항목보호|네임스페이스보호|
    |글리프그룹네임스페이스|글리프아이템프라이빗|네임스페이스프라이빗|
    |글리프그룹네임스페이스|글리프아이템 바로 가기|네임스페이스 바로 가기|
    |글리프그룹운영자|글리프아이템퍼블릭|운영자공개|
    |글리프그룹운영자|글리프아이템 내부|연산자 내부|
    |글리프그룹운영자|글리프아이템프렌드|연산자 내부|
    |글리프그룹운영자|글리프항목보호|연산자 보호|
    |글리프그룹운영자|글리프아이템프라이빗|운영자개인|
    |글리프그룹운영자|글리프아이템 바로 가기|연산자 바로 가기|
    |글리프그룹프로퍼티|글리프아이템퍼블릭|부동산 퍼블릭|
    |글리프그룹프로퍼티|글리프아이템 내부|프로퍼티 내부|
    |글리프그룹프로퍼티|글리프아이템프렌드|프로퍼티 내부|
    |글리프그룹프로퍼티|글리프항목보호|속성 보호|
    |글리프그룹프로퍼티|글리프아이템프라이빗|프로퍼티프라이빗|
    |글리프그룹프로퍼티|글리프아이템 바로 가기|속성 바로 가기|
    |글리프그룹스트럭터트|글리프아이템퍼블릭|구조공개|
    |글리프그룹스트럭터트|글리프아이템 내부|구조 내부|
    |글리프그룹스트럭터트|글리프아이템프렌드|구조 내부|
    |글리프그룹스트럭터트|글리프항목보호|구조 보호|
    |글리프그룹스트럭터트|글리프아이템프라이빗|구조개인|
    |글리프그룹스트럭터트|글리프아이템 바로 가기|구조 바로 가기|
    |글리프 그룹 템플릿|글리프아이템퍼블릭|템플릿공개|
    |글리프 그룹 템플릿|글리프아이템 내부|템플릿 내부|
    |글리프 그룹 템플릿|글리프아이템프렌드|템플릿 내부|
    |글리프 그룹 템플릿|글리프항목보호|템플릿 보호|
    |글리프 그룹 템플릿|글리프아이템프라이빗|템플릿비공개|
    |글리프 그룹 템플릿|글리프아이템 바로 가기|템플릿 바로 가기|
    |글리프 그룹타이프|글리프아이템퍼블릭|형식정의공용|
    |글리프 그룹타이프|글리프아이템 내부|형식 정의 내부|
    |글리프 그룹타이프|글리프아이템프렌드|형식 정의 내부|
    |글리프 그룹타이프|글리프항목보호|형식 정의보호|
    |글리프 그룹타이프|글리프아이템프라이빗|형식정의개인|
    |글리프 그룹타이프|글리프아이템 바로 가기|유형정의 바로 가기|
    |글리프그룹타입|글리프아이템퍼블릭|형식 공개|
    |글리프그룹타입|글리프아이템 내부|유형 내부|
    |글리프그룹타입|글리프아이템프렌드|유형 내부|
    |글리프그룹타입|글리프항목보호|유형 보호|
    |글리프그룹타입|글리프아이템프라이빗|형식비공개|
    |글리프그룹타입|글리프아이템 바로 가기|유형 바로 가기|
    |글리프그룹유니온|글리프아이템퍼블릭|유니온퍼블릭|
    |글리프그룹유니온|글리프아이템 내부|유니온 내부|
    |글리프그룹유니온|글리프아이템프렌드|유니온 내부|
    |글리프그룹유니온|글리프항목보호|유니온보호|
    |글리프그룹유니온|글리프아이템프라이빗|유니온프라이빗|
    |글리프그룹유니온|글리프아이템 바로 가기|유니온 바로 가기|
    |글리프 그룹변수|글리프아이템퍼블릭|필드퍼블릭|
    |글리프 그룹변수|글리프아이템 내부|필드 내부|
    |글리프 그룹변수|글리프아이템프렌드|필드 내부|
    |글리프 그룹변수|글리프항목보호|필드 보호|
    |글리프 그룹변수|글리프아이템프라이빗|필드프라이빗|
    |글리프 그룹변수|글리프아이템 바로 가기|필드 바로 가기|
    |글리프 그룹밸류타입|글리프아이템퍼블릭|값 유형공용|
    |글리프 그룹밸류타입|글리프아이템 내부|값 유형 내부|
    |글리프 그룹밸류타입|글리프아이템프렌드|값 유형 내부|
    |글리프 그룹밸류타입|글리프항목보호|값 유형 보호|
    |글리프 그룹밸류타입|글리프아이템프라이빗|값유형프라이빗|
    |글리프 그룹밸류타입|글리프아이템 바로 가기|값유형 바로 가기|
    |글리프그룹 인트린시크|글리프아이템퍼블릭|개체 공개|
    |글리프그룹 인트린시크|글리프아이템 내부|개체 내부|
    |글리프그룹 인트린시크|글리프아이템프렌드|개체 내부|
    |글리프그룹 인트린시크|글리프항목보호|개체 보호|
    |글리프그룹 인트린시크|글리프아이템프라이빗|개체개인|
    |글리프그룹 인트린시크|글리프아이템 바로 가기|개체 바로 가기|
    |글리프그룹J샤프메소|글리프아이템퍼블릭|메소드퍼블릭|
    |글리프그룹J샤프메소|글리프아이템 내부|방법 내부|
    |글리프그룹J샤프메소|글리프아이템프렌드|방법 내부|
    |글리프그룹J샤프메소|글리프항목보호|MethodProtected|
    |글리프그룹J샤프메소|글리프아이템프라이빗|메서드개인|
    |글리프그룹J샤프메소|글리프아이템 바로 가기|메서드 바로 가기|
    |글리프그룹J샤프필드|글리프아이템퍼블릭|필드퍼블릭|
    |글리프그룹J샤프필드|글리프아이템 내부|필드 내부|
    |글리프그룹J샤프필드|글리프아이템프렌드|필드 내부|
    |글리프그룹J샤프필드|글리프항목보호|필드 보호|
    |글리프그룹J샤프필드|글리프아이템프라이빗|필드프라이빗|
    |글리프그룹J샤프필드|글리프아이템 바로 가기|필드 바로 가기|
    |글리프그룹J샤프클래스|글리프아이템퍼블릭|클래스퍼블릭|
    |글리프그룹J샤프클래스|글리프아이템 내부|클래스 내부|
    |글리프그룹J샤프클래스|글리프아이템프렌드|클래스 내부|
    |글리프그룹J샤프클래스|글리프항목보호|클래스 보호|
    |글리프그룹J샤프클래스|글리프아이템프라이빗|클래스프라이빗|
    |글리프그룹J샤프클래스|글리프아이템 바로 가기|클래스 바로 가기|
    |글리프그룹J샤프네임스페이스|글리프아이템퍼블릭|네임스페이스퍼블릭|
    |글리프그룹J샤프네임스페이스|글리프아이템 내부|네임스페이스 내부|
    |글리프그룹J샤프네임스페이스|글리프아이템프렌드|네임스페이스 내부|
    |글리프그룹J샤프네임스페이스|글리프항목보호|네임스페이스보호|
    |글리프그룹J샤프네임스페이스|글리프아이템프라이빗|네임스페이스프라이빗|
    |글리프그룹J샤프네임스페이스|글리프아이템 바로 가기|네임스페이스 바로 가기|
    |글리프그룹J샤프인터페이스|글리프아이템퍼블릭|인터페이스공용|
    |글리프그룹J샤프인터페이스|글리프아이템 내부|인터페이스 내부|
    |글리프그룹J샤프인터페이스|글리프아이템프렌드|인터페이스 내부|
    |글리프그룹J샤프인터페이스|글리프항목보호|인터페이스 보호|
    |글리프그룹J샤프인터페이스|글리프아이템프라이빗|인터페이스개인|
    |글리프그룹J샤프인터페이스|글리프아이템 바로 가기|인터페이스 바로 가기|
    |글리프 그룹 오류||StatusError|
    |글리프브스크파일||클래스 파일|
    |글리프 어셈블리||참조|
    |글리프 라이브러리||라이브러리|
    |글리프VB프로젝트||VB프로젝트노드|
    |글리프쿨 프로젝트||CS프로젝트노드|
    |글리프콥프로젝트||CPP프로젝트노드|
    |글리프디아로지드||대화 상자|
    |글리프오픈폴더||폴더 열기|
    |글리프클로드폴더||폴더 닫힘|
    |글리프로우||고토넥스트|
    |글리프C샤프파일||CSFile노드|
    |글리프C샤프확장||코드 조각|
    |글리프 키워드||인텔리센스키워드|
    |글리프 정보||상태 정보|
    |글리프 레퍼런스||클래스 메서드 참조|
    |글리프 레큐레이션||재귀|
    |글리프Xml항목||태그|
    |글리프J샤프프로젝트||DocumentCollection|
    |글리프J샤프문서||문서|
    |글리프포워드 타입||고토넥스트|
    |글리프콜러스그래프||콜토|
    |글리프그라프||콜에서|
    |글리프 경고||StatusWarning|
    |글리프아마레퍼런스||물음표|
    |글리프메이아콜러||콜토|
    |글리프메이그콜||콜에서|
    |글리프익스텐션방법||확장 방법|
    |글리프익스텐션내부||확장 방법|
    |글리프익스텐션프렌드프렌드||확장 방법|
    |글리프익스텐션보호||확장 방법|
    |글리프익스텐션프라이빗||확장 방법|
    |글리프익스텐프메소드 바로 가기||확장 방법|
    |글리프Xml속성||XmlAttribute|
    |글리프Xml차일드||XmlElement|
    |글리프Xml 후손||엑스후소두|
    |글리프Xml네임스페이스||XmlNamespace|
    |글리프Xml속성질문||Xml속성낮은신뢰|
    |글리프Xml속성 체크||Xml속성높은신뢰|
    |글리프Xml어린이질문||XmlElementLowconfidence|
    |글리프Xml차일드 체크||XmlElement높은신뢰|
    |글리프Xml 후손질문||Xml후손낮은자신감|
    |글리프Xml 후손체크||Xml후손높은신뢰|
    |글리프 완성경고||인텔리센스 경고|
