---
title: 이미지 라이브러리 뷰어 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707743"
---
# <a name="image-library-viewer"></a>이미지 라이브러리 뷰어
Visual Studio 이미지 라이브러리 뷰어 도구는 이미지 매니페스트를 로드하고 검색할 수 있으므로 사용자가 Visual Studio와 동일한 방식으로 이미지를 조작할 수 있습니다. 사용자는 배경, 크기, DPI, 고대비 및 기타 설정을 변경할 수 있습니다. 또한 이 도구는 각 이미지 매니페스트에 대한 로딩 정보를 표시하고 이미지 매니페스트의 각 이미지에 대한 소스 정보를 표시합니다. 이 도구는 다음과 같은 데 유용합니다.

1. 오류 진단

2. 사용자 지정 이미지 매니페스트에서 특성이 올바르게 설정되도록 보장

3. Visual Studio 확장 프로그램이 Visual Studio 스타일에 맞는 이미지를 사용할 수 있도록 Visual Studio 이미지 카탈로그에서 이미지 검색

   ![이미지 라이브러리 뷰어 Hero](../../extensibility/internals/media/image-library-viewer-hero.png "이미지 라이브러리 뷰어 Hero")

   **이미지 모니커**

   이미지 모니커(또는 짧은 경우 모니커)는 이미지 라이브러리에서 이미지 자산 또는 이미지 목록 자산을 고유하게 식별하는 GUID:ID 쌍입니다.

   **이미지 매니페스트 파일**

   이미지 매니페스트(imagemanifest) 파일은 이미지 자산 집합, 해당 자산을 나타내는 모니커 및 각 자산을 나타내는 실제 이미지 또는 이미지를 정의하는 XML 파일입니다. 이미지 매니페스트는 레거시 UI 지원을 위해 독립 실행형 이미지 또는 이미지 목록을 정의할 수 있습니다. 또한 자산 또는 각 자산 뒤에 있는 개별 이미지에 설정하여 해당 자산이 표시되는 시기와 방법을 변경할 수 있는 특성이 있습니다.

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
|ID|기호는 ID를 나타내며 음수 가아닌 정수여야 합니다.|
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
|시스템|윈도우\System32 폴더|
|Windir|%WinDir% 환경 변수의 값|

 **이미지**

 \<이미지> 요소는 모니커에서 참조할 수 있는 이미지를 정의합니다. 함께 가져온 GUID와 ID는 이미지 모니커를 형성합니다. 이미지의 모니커는 전체 이미지 라이브러리에서 고유해야 합니다. 두 개 이상의 이미지에 지정된 모니커가 있는 경우 라이브러리를 빌드하는 동안 처음 발생한 이미지는 유지되는 이미지입니다.

 하나 이상의 소스를 포함해야 합니다. 크기 중립적 인 소스는 광범위한 크기에서 최상의 결과를 제공하지만 필요하지는 않습니다. 서비스가 \<이미지> 요소에 정의되지 않은 크기의 이미지를 요청받고 크기 중립적 소스가 없는 경우 서비스는 최상의 크기별 소스를 선택하고 요청된 크기로 크기를 조정합니다.

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
|Uri|[필수] 이미지를 로드할 수 있는 위치를 정의하는 URI입니다. 다음 중 하나일 수 있습니다.<br /><br /> - application:/// 기관을 사용하는 [팩 URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br /><br /> - 절대 구성 요소 리소스 참조<br /><br /> - 네이티브 리소스를 포함하는 파일에 대한 경로|
|배경|[선택 사항] 소스가 사용할 배경의 종류를 나타냅니다.<br /><br /> 다음 중 하나일 수 있습니다.<br /><br /> - *빛*: 소스는 밝은 배경에 사용할 수 있습니다.<br /><br /> - *어두운*: 소스는 어두운 배경에 사용할 수 있습니다.<br /><br /> - *고대비*: 고대비 모드에서 모든 백그라운드에서 소스를 사용할 수 있습니다.<br /><br /> - *고대비조명*: 고대비 모드에서 라이트 배경에서 소스를 사용할 수 있습니다.<br /><br /> -*고대비암:* 고대비 모드에서 어두운 배경에서 소스를 사용할 수 있습니다.<br /><br /> **Background** 특성이 생략된 경우 모든 백그라운드에서 소스를 사용할 수 있습니다.<br /><br /> **배경이** *밝은*경우, *어둡고,* *대비광이 약하거나,* *대비극을 높이거나, 대비암색이 높으면*소스의 색상이 반전되지 않습니다. **배경을** 생략하거나 *고대비로*설정된 경우 소스 색상의 반전은 이미지의 **AllowColor반전** 특성에 의해 제어됩니다.|

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

## <a name="how-to-use-the-tool"></a>이 도구를 사용 하는 방법
 **사용자 지정 이미지 매니페스트 유효성 검사**

 사용자 지정 매니페스트를 만들려면 ManifestFromResources 도구를 사용하여 매니페스트를 자동으로 생성하는 것이 좋습니다. 사용자 지정 매니페스트의 유효성을 검사하려면 이미지 라이브러리 뷰어를 실행하고 파일 > 설정 경로를 선택합니다... 을 클릭합니다. 이 도구는 검색 디렉토리를 사용하여 이미지 매니페스트를 로드하지만 매니페스트에 이미지가 포함된 .dll 파일을 찾는 데도 사용되므로 이 대화 상자에 매니페스트 와 DLL 디렉토리를 모두 포함해야 합니다.

 ![이미지 라이브러리 뷰어 검색](../../extensibility/internals/media/image-library-viewer-search.png "이미지 라이브러리 뷰어 검색")

 **추가를** 클릭하여 매니페스트 및 해당 DLL을 검색할 새 검색 디렉토리를 선택합니다. 이 도구는 이러한 검색 디렉토리를 기억하고 디렉터리를 선택하거나 선택을 취소하여 켜거나 끌 수 있습니다.

 기본적으로 이 도구는 Visual Studio 설치 디렉터리를 찾고 해당 디렉토리를 검색 디렉터리 목록에 추가하려고 시도합니다. 도구가 찾을 수 없는 디렉토리를 수동으로 추가할 수 있습니다.

 모든 매니페스트가 로드되면 이 도구를 사용하여 **이미지의 배경** 색, **DPI,** **고대비**또는 **그레이스케일링을** 전환하여 사용자가 이미지 자산을 시각적으로 검사하여 다양한 설정에 대해 올바르게 렌더링되고 있는지 확인할 수 있습니다.

 ![이미지 라이브러리 뷰어 배경](../../extensibility/internals/media/image-library-viewer-background.png "이미지 라이브러리 뷰어 배경")

 배경 색은 라이트, 어둡게 또는 사용자 지정 값으로 설정할 수 있습니다. "사용자 지정 색상"을 선택하면 색상 선택 대화 상자가 열리고 나중에 쉽게 기억할 수 있도록 배경 콤보 상자 의 맨 아래에 사용자 지정 색상이 추가됩니다.

 ![이미지 라이브러리 뷰어 사용자 지정 색](../../extensibility/internals/media/image-library-viewer-custom-color.png "이미지 라이브러리 뷰어 사용자 지정 색")

 이미지 모니커를 선택하면 오른쪽의 이미지 세부 정보 창에 해당 모니커 뒤에 있는 각 실제 이미지에 대한 정보가 표시됩니다. 또한 창을 사용하면 모니커를 이름 또는 원시 GUID:ID 값으로 복사할 수 있습니다.

 ![이미지 라이브러리 뷰어 이미지 세부 정보](../../extensibility/internals/media/image-library-viewer-image-details.png "이미지 라이브러리 뷰어 이미지 세부 정보")

 각 이미지 원본에 대해 표시되는 정보에는 표시할 배경의 종류, 테마를 포함할 수 있는지, 고대비를 지원할 수 있는지, 유효한 크기인지 또는 크기 중립적인지 여부, 이미지가 네이티브 어셈블리에서 오는지 여부가 포함됩니다.

 ![이미지 라이브러리 뷰어 Can 테마](../../extensibility/internals/media/image-library-viewer-can-theme.png "이미지 라이브러리 뷰어 Can 테마")

 이미지 매니페스트의 유효성을 검사할 때는 매니페스트 및 이미지 DLL을 실제 위치에 배치하는 것이 좋습니다. 이렇게 하면 상대 경로가 올바르게 작동하고 이미지 라이브러리에서 매니페스트 및 이미지 DLL을 찾아 로드할 수 있는지 확인합니다.

 **이미지 카탈로그 검색 알려진모니커**

 Visual Studio 스타일과 더 잘 일치하기 위해 Visual Studio 확장프로그램은 자체 를 만들고 사용하는 대신 Visual Studio 이미지 카탈로그에서 이미지를 사용할 수 있습니다. 이렇게 하면 이러한 이미지를 유지 관리할 필요가 없으며 이미지에 높은 DPI 백업 이미지가 있으므로 Visual Studio가 지원하는 모든 DPI 설정에서 올바르게 표시되도록 할 수 있습니다.

 이미지 라이브러리 뷰어를 사용하면 사용자가 이미지 자산을 나타내는 모니커를 찾고 코드에서 해당 모니커를 사용할 수 있도록 매니페스트를 검색할 수 있습니다. 이미지를 검색하려면 검색 상자에 원하는 검색어를 입력하고 Enter를 누릅니다. 아래쪽에 있는 상태 표시줄에는 모든 매니페스트의 총 이미지에서 발견된 일치 항목 수가 표시됩니다.

 ![이미지 라이브러리 뷰어 필터](../../extensibility/internals/media/image-library-viewer-filter.png "이미지 라이브러리 뷰어 필터")

 기존 매니페스트에서 이미지 모니커를 검색할 때는 Visual Studio 이미지 카탈로그의 모니커, 의도적으로 공개적으로 액세스할 수 있는 다른 모니커 또는 사용자 지정 모니커만 검색하고 사용하는 것이 좋습니다. 비공개 모니커를 사용하는 경우 사용자 지정 UI가 손상되거나 비공개 모니커 및 이미지가 변경되거나 업데이트되는 경우 예기치 않은 방식으로 이미지가 변경될 수 있습니다.

 또한 GUID로 검색할 수 있습니다. 이 유형의 검색은 매니페스트에 여러 GUID가 포함된 경우 목록을 단일 매니페스트 또는 매니페스트의 단일 하위 섹션으로 필터링하는 데 유용합니다.

 ![이미지 라이브러리 뷰어 필터 GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "이미지 라이브러리 뷰어 필터 GUID")

 마지막으로, ID로 검색도 가능합니다.

 ![이미지 라이브러리 뷰어 필터 ID](../../extensibility/internals/media/image-library-viewer-filter-id.png "이미지 라이브러리 뷰어 필터 ID")

## <a name="notes"></a>메모

- 기본적으로 이 도구는 Visual Studio 설치 디렉토리에 있는 여러 이미지 매니페스트를 가져옵니다. 공개적으로 소모품 모니커가있는 유일한 사람은 **Microsoft.VisualStudio.ImageCatalog** 매니페스트입니다. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (사용자 지정 매니페스트에서 이 GUID를 **재정의하지 않음)** 유형: 알려진 모니커

- 이 도구는 모든 이미지 매니페스트를 로드하기 위해 시작하려고 시도하므로 응용 프로그램이 실제로 나타나려면 몇 초 정도 걸릴 수 있습니다. 매니페스트를 로드하는 동안 느리거나 응답하지 않을 수도 있습니다.

## <a name="sample-output"></a>샘플 출력
 이 도구는 출력을 생성하지 않습니다.
