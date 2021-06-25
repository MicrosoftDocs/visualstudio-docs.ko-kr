---
title: 이미지 라이브러리 뷰어 | Microsoft Docs
description: 이미지 특성을 보고 조작할 수 있도록 이미지 매니페스트를 로드하고 검색하는 Visual Studio 이미지 라이브러리 뷰어 도구에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02e7c5d5ed45b7a6c19c248e949e667ec0a1bdc0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898712"
---
# <a name="image-library-viewer"></a>이미지 라이브러리 뷰어
Visual Studio 이미지 라이브러리 뷰어 도구는 이미지 매니페스트를 로드하고 검색하여 사용자가 Visual Studio 것과 동일한 방식으로 조작할 수 있도록 합니다. 사용자는 배경, 크기, DPI, 고대비 및 기타 설정을 변경할 수 있습니다. 또한 도구는 각 이미지 매니페스트에 대한 로드 정보를 표시하고 이미지 매니페스트의 각 이미지에 대한 원본 정보를 표시합니다. 이 도구는 다음과 같은 경우 유용합니다.

1. 오류 진단

2. 사용자 지정 이미지 매니페스트에서 특성이 올바르게 설정되었는지 확인

3. Visual Studio 확장에서 스타일에 맞는 이미지를 사용할 수 있도록 Visual Studio 이미지 카탈로그 Visual Studio에서 이미지 검색

   ![이미지 라이브러리 뷰어 Hero](../../extensibility/internals/media/image-library-viewer-hero.png "이미지 라이브러리 뷰어 Hero")

   **이미지 모니커**

   이미지 모니커(또는 짧은 모니커)는 이미지 라이브러리에서 이미지 자산 또는 이미지 목록 자산을 고유하게 식별하는 GUID:ID 쌍입니다.

   **이미지 매니페스트 파일**

   이미지 매니페스트(.imagemanifest) 파일은 이미지 자산 집합, 해당 자산을 나타내는 모니커 및 각 자산을 나타내는 실제 이미지 또는 이미지를 정의하는 XML 파일입니다. 이미지 매니페스트는 레거시 UI 지원을 위한 독립 실행형 이미지 또는 이미지 목록을 정의할 수 있습니다. 또한 자산 또는 각 자산 뒤에 있는 개별 이미지에 설정할 수 있는 특성이 있으며, 이러한 자산이 표시되는 시기와 방법을 변경할 수 있습니다.

   **이미지 매니페스트 스키마**

   전체 이미지 매니페스트는 다음과 같습니다.

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
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

 가독성 및 유지 관리 지원을 위해 이미지 매니페스트는 특성 값에 기호를 사용할 수 있습니다. 기호는 다음과 같이 정의됩니다.

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
|가져오기|현재 매니페스트에서 사용할 지정된 매니페스트 파일의 기호를 가져옵니다.|
|Guid|기호는 GUID를 나타내며 GUID 서식과 일치해야 합니다.|
|ID|기호는 ID를 나타내며 무한 정수여야 합니다.|
|String|기호는 임의의 문자열 값을 나타냅니다.|

 기호는 대/소문자를 구분하며 $(symbol-name) 구문을 사용하여 참조됩니다.

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 일부 기호는 모든 매니페스트에 대해 미리 정의됩니다. 이러한 특성은 또는 요소의 Uri 특성에서 \<Source> 로컬 컴퓨터의 경로를 참조하는 데 사용할 수 \<Import> 있습니다.

|**기호**|**설명**|
|-|-|
|CommonProgramFiles|%CommonProgramFiles% 환경 변수의 값|
|LocalAppData|%LocalAppData% 환경 변수의 값|
|ManifestFolder|매니페스트 파일이 포함된 폴더|
|MyDocuments|현재 사용자의 내 문서 폴더 전체 경로|
|ProgramFiles|%ProgramFiles% 환경 변수의 값|
|시스템|Windows\System32 폴더|
|Windir|%WinDir% 환경 변수의 값|

 **Image**

 \<Image>요소는 모니커에서 참조할 수 있는 이미지를 정의합니다. 함께 가져온 GUID와 ID는 이미지 모니커를 형성합니다. 이미지의 모니커는 전체 이미지 라이브러리에서 고유해야 합니다. 이미지에 지정된 모니커가 두 개 이상 있는 경우 라이브러리를 빌드하는 동안 처음 발생하는 모니커가 유지됩니다.

 하나 이상의 소스를 포함해야 합니다. 크기 중립적 원본은 광범위한 크기에서 최상의 결과를 제공하지만 필수는 아닙니다. 서비스에 요소에 정의되지 않은 크기의 이미지가 요청되고 \<Image> 크기 중립적 원본이 없는 경우 서비스는 가장 적합한 크기별 원본을 선택하고 요청된 크기로 크기를 조정합니다.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Attribute**|**정의**|
|-|-|
|Guid|[필수] 이미지 모니커의 GUID 부분입니다.|
|ID|[필수] 이미지 모니커의 ID 부분입니다.|
|AllowColorInversion|[선택 사항, 기본값 true] 어두운 배경에서 사용할 때 이미지의 색을 프로그래밍 방식으로 반전할 수 있는지 여부를 나타냅니다.|

 **원본**

 \<Source>요소는 단일 이미지 원본 자산(XAML 및 PNG)을 정의합니다.

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Attribute**|**정의**|
|-|-|
|URI|[필수] 이미지를 로드할 수 있는 위치를 정의하는 URI입니다. 다음 중 하나일 수 있습니다.<br /><br /> - application:/// 기관을 사용하는 [Pack URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br /><br /> - 절대 구성 요소 리소스 참조<br /><br /> - 네이티브 리소스를 포함하는 파일의 경로|
|배경|[선택 사항] 소스가 사용하려는 배경의 종류를 나타냅니다.<br /><br /> 다음 중 하나일 수 있습니다.<br /><br /> - *밝게:* 밝은 배경에서 소스를 사용할 수 있습니다.<br /><br /> - *어둡게:* 소스는 어두운 배경에서 사용할 수 있습니다.<br /><br /> - *HighContrast:* 소스는 고대비 모드의 모든 백그라운드에서 사용할 수 있습니다.<br /><br /> - *HighContrastLight:* 고대비 모드에서 밝은 배경에서 소스를 사용할 수 있습니다.<br /><br /> -*HighContrastDark:* 소스는 고대비 모드의 어두운 배경에서 사용할 수 있습니다.<br /><br /> **Background** 특성을 생략하면 모든 백그라운드에서 원본을 사용할 수 있습니다.<br /><br /> **배경이** *밝게,* *어둡게,* *HighContrastLight* 또는 *HighContrastDark인* 경우 원본의 색은 반전되지 않습니다. **Background를** 생략하거나 *HighContrast* 로 설정하면 소스 색의 반전이 이미지의 **AllowColorInversion** 특성에 의해 제어됩니다.|

 \<Source>요소에는 다음 선택적 하위 요소 중 하나만 있을 수 있습니다.

|**요소**|**특성(모두 필수)**|**정의**|
|-|-|-|
|\<Size>|값|원본은 지정된 크기의 이미지(디바이스 단위)에 사용됩니다. 이미지는 정사각형입니다.|
|\<SizeRange>|MinSize, MaxSize|원본은 MinSize에서 MaxSize까지(디바이스 단위) 이미지에 사용됩니다. 이미지는 정사각형입니다.|
|\<Dimensions>|너비, 높이|원본은 지정된 너비와 높이(디바이스 단위)의 이미지에 사용됩니다.|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, Maxwidth|이 소스는 최소 너비/높이에서 최대 너비/높이 (장치 단위)로 이루어진 이미지에 사용 됩니다.|

 요소는 관리 되는 \<Source> \<NativeResource> \<Source> 어셈블리가 아니라 네이티브 어셈블리에서 로드 되는을 정의 하는 선택적 하위 요소를 포함할 수도 있습니다.

```xml
<NativeResource Type="type" ID="int" />
```

|**Attribute**|**정의**|
|-|-|
|Type|하다 네이티브 리소스의 형식 (XAML 또는 PNG)입니다.|
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
|Guid|하다 이미지 모니커의 GUID 부분입니다.|
|ID|하다 이미지 모니커의 ID 부분입니다.|
|외부|[선택 사항, 기본값 false] 이미지 모니커가 현재 매니페스트의 이미지를 참조 하는지 여부를 나타냅니다.|

 포함 된 이미지의 모니커는 현재 매니페스트에 정의 된 이미지를 참조할 필요가 없습니다. 이미지 라이브러리에서 포함 된 이미지를 찾을 수 없는 경우 빈 자리 표시자 이미지가 대신 사용 됩니다.

## <a name="how-to-use-the-tool"></a>이 도구를 사용 하는 방법
 **사용자 지정 이미지 매니페스트 유효성 검사**

 사용자 지정 매니페스트를 만들려면 ManifestFromResources 도구를 사용 하 여 매니페스트를 자동으로 생성 하는 것이 좋습니다. 사용자 지정 매니페스트의 유효성을 검사 하려면 이미지 라이브러리 뷰어를 시작 하 고 파일 > 경로 설정 ...을 선택 합니다. 를 열려면 디렉터리 검색 대화 상자를 엽니다. 도구는 검색 디렉터리를 사용 하 여 이미지 매니페스트를 로드 하지만이 도구를 사용 하 여 매니페스트에 이미지를 포함 하는 .dll 파일을 찾을 수 있습니다. 따라서이 대화 상자에 매니페스트 및 DLL 디렉터리를 모두 포함 해야 합니다.

 ![이미지 라이브러리 뷰어 검색](../../extensibility/internals/media/image-library-viewer-search.png "이미지 라이브러리 뷰어 검색")

 **추가** ...를 클릭 하 여 매니페스트 및 해당 dll을 검색 하는 새 검색 디렉터리를 선택 합니다. 이 도구는 디렉터리를 선택 하거나 선택 취소 하 여 이러한 검색 디렉터리를 설정 하거나 해제할 수 있습니다.

 기본적으로이 도구는 Visual Studio 설치 디렉터리를 찾아 디렉터리 검색 목록에 해당 디렉터리를 추가 하려고 합니다. 도구에서 찾을 수 없는 디렉터리를 수동으로 추가할 수 있습니다.

 모든 매니페스트가 로드 된 후에는 도구를 사용 하 여 이미지에 대 한 **배경색** , **DPI**, **고대비** 또는 **grayscaling** 를 전환 하 여 다양 한 설정에 맞게 이미지 자산을 올바르게 렌더링 하는지 확인할 수 있습니다.

 ![이미지 라이브러리 뷰어 배경](../../extensibility/internals/media/image-library-viewer-background.png "이미지 라이브러리 뷰어 배경")

 배경색을 밝은, 어둡게 또는 사용자 지정 값으로 설정할 수 있습니다. "사용자 지정 색"을 선택 하면 색 선택 대화 상자가 열리고 나중에 쉽게 회수할 수 있도록 배경 콤보 상자의 아래쪽에 해당 사용자 지정 색을 추가 합니다.

 ![이미지 라이브러리 뷰어 사용자 지정 색](../../extensibility/internals/media/image-library-viewer-custom-color.png "이미지 라이브러리 뷰어 사용자 지정 색")

 이미지 모니커를 선택 하면 오른쪽에 있는 이미지 세부 정보 창에 해당 모니커 뒤의 각 실제 이미지에 대 한 정보가 표시 됩니다. 또한이 창을 사용 하면 사용자가 이름 또는 원시 GUID: ID 값으로 모니커를 복사할 수 있습니다.

 ![이미지 라이브러리 뷰어 이미지 세부 정보](../../extensibility/internals/media/image-library-viewer-image-details.png "이미지 라이브러리 뷰어 이미지 세부 정보")

 각 이미지 원본에 대해 표시 되는 정보에는 표시 되는 배경 종류, 테마를 적용 하거나 고대비 지원할 수 있는지 여부, 올바른 크기 또는 크기 중립적 인지 여부, 이미지를 네이티브 어셈블리에서 가져오는지 여부 등이 포함 됩니다.

 ![이미지 라이브러리 뷰어 Can 테마](../../extensibility/internals/media/image-library-viewer-can-theme.png "이미지 라이브러리 뷰어 Can 테마")

 이미지 매니페스트의 유효성을 검사할 때 매니페스트 및 이미지 DLL을 실제 위치에 배포 하는 것이 좋습니다. 이렇게 하면 상대 경로가 제대로 작동 하 고 이미지 라이브러리가 매니페스트와 이미지 DLL을 찾아 로드할 수 있는지 확인 합니다.

 **이미지 카탈로그 KnownMonikers를 검색 하는 중**

 Visual studio 스타일을 보다 정확 하 게 일치 시키기 위해 visual studio 확장은 자체를 만들고 사용 하는 대신 Visual Studio 이미지 카탈로그에서 이미지를 사용할 수 있습니다. 이러한 방식으로 이러한 이미지를 유지 관리할 필요가 없으며 이미지의 DPI가 높은 지원 이미지를 갖도록 하 여 Visual Studio에서 지 원하는 모든 DPI 설정에서 정확 하 게 보이도록 할 수 있습니다.

 이미지 라이브러리 뷰어를 사용 하면 사용자가 이미지 자산을 나타내는 모니커를 찾고 코드에서 해당 모니커를 사용할 수 있도록 매니페스트를 검색할 수 있습니다. 이미지를 검색 하려면 검색 상자에 원하는 검색 용어를 입력 하 고 enter 키를 누릅니다. 아래쪽의 상태 표시줄에는 모든 매니페스트의 전체 이미지 중에서 발견 된 일치 항목이 표시 됩니다.

 ![이미지 라이브러리 뷰어 필터](../../extensibility/internals/media/image-library-viewer-filter.png "이미지 라이브러리 뷰어 필터")

 기존 매니페스트에서 이미지 모니커를 검색 하는 경우 Visual Studio 이미지 카탈로그의 모니커, 의도적으로 공개적으로 액세스할 수 있는 다른 모니커 또는 고유한 사용자 지정 모니커를 검색 하 여 사용 하는 것이 좋습니다. Public이 아닌 모니커를 사용 하는 경우 사용자 지정 UI가 손상 되었거나 이러한 public이 아닌 모니커 및 이미지를 변경 하거나 업데이트할 때 예기치 않은 방식으로 해당 이미지가 변경 될 수 있습니다.

 또한 GUID로 검색할 수 있습니다. 이 유형의 검색은 단일 매니페스트 또는 매니페스트의 단일 하위 섹션에 대 한 목록을 필터링 하는 데 유용 합니다.

 ![이미지 라이브러리 뷰어 필터 GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "이미지 라이브러리 뷰어 필터 GUID")

 마지막으로 ID로 검색도 가능 합니다.

 ![이미지 라이브러리 뷰어 필터 ID](../../extensibility/internals/media/image-library-viewer-filter-id.png "이미지 라이브러리 뷰어 필터 ID")

## <a name="notes"></a>참고

- 기본적으로이 도구는 Visual Studio 설치 디렉터리에 있는 여러 이미지 매니페스트를 가져옵니다. 공개적으로 사용할 수 있는 모니커가 있는 유일한 모니커는 **VisualStudio. ImageCatalog** 매니페스트입니다. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (사용자 지정 매니페스트에서이 GUID를 재정의 **하지** 않음) 형식: knownmonikers

- 도구는 시작 시 검색 된 모든 이미지 매니페스트를 로드 하 여 응용 프로그램이 실제로 표시 될 때까지 몇 초 정도 걸릴 수 있습니다. 매니페스트를 로드 하는 동안 느리거나 응답이 없는 수도 있습니다.

## <a name="sample-output"></a>샘플 출력
 이 도구는 어떠한 출력도 생성 하지 않습니다.
