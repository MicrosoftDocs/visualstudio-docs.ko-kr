---
title: 이미지 라이브러리 뷰어 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f6423c569fd1909539de9460ab3dcde0bcf753c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532030"
---
# <a name="image-library-viewer"></a>이미지 라이브러리 뷰어
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 이미지 라이브러리 뷰어 도구는 이미지 매니페스트를 로드 하 고 검색 하 여 사용자가 Visual Studio와 동일한 방식으로 조작할 수 있도록 합니다. 사용자는 배경, 크기, DPI, 고대비 및 기타 설정을 변경할 수 있습니다. 또한이 도구는 각 이미지 매니페스트에 대 한 로딩 정보를 표시 하 고 이미지 매니페스트의 각 이미지에 대 한 소스 정보를 표시 합니다. 이 도구는 다음과 같은 경우에 유용 합니다.  
  
1. 오류 진단  
  
2. 사용자 지정 이미지 매니페스트에서 특성이 올바르게 설정 되었는지 확인  
  
3. Visual studio 확장에서 visual studio 스타일에 맞는 이미지를 사용할 수 있도록 Visual studio 이미지 카탈로그에서 이미지를 검색 하는 중  
  
   ![이미지 라이브러리 뷰어 Hero](../../extensibility/internals/media/image-library-viewer-hero.png "이미지 라이브러리 뷰어 Hero")  
  
   **이미지 모니커**  
  
   이미지 모니커 (또는 short 모니커)는 이미지 라이브러리에서 이미지 자산 또는 이미지 목록 자산을 고유 하 게 식별 하는 GUID: ID 쌍입니다.  
  
   **이미지 매니페스트 파일**  
  
   이미지 매니페스트 (imagemanifest) 파일은 이미지 자산 집합, 해당 자산을 나타내는 모니커 및 각 자산을 나타내는 실제 이미지를 정의 하는 XML 파일입니다. 이미지 매니페스트는 레거시 UI 지원에 대 한 독립 실행형 이미지 또는 이미지 목록을 정의할 수 있습니다. 또한 자산이 표시 되는 경우와 각 자산을 표시 하는 방식에 따라 자산 또는 개별 이미지에서 설정할 수 있는 특성도 있습니다.  
  
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
  
 **기호**  
  
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
|Guid|기호는 GUID를 나타내며 GUID 형식과 일치 해야 합니다.|  
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
|시스템|Windows\System32 폴더|  
|I|% WinDir% 환경 변수의 값입니다.|  
  
 **이미지**  
  
 \<Image>요소는 모니커가 참조할 수 있는 이미지를 정의 합니다. 함께 사용 된 GUID 및 ID는 이미지 모니커를 형성 합니다. 이미지의 모니커는 전체 이미지 라이브러리에서 고유 해야 합니다. 하나 이상의 이미지가 지정 된 모니커를 포함 하는 경우 라이브러리를 빌드하는 동안 발생 한 첫 번째 이미지는 유지 되는 것입니다.  
  
 하나 이상의 소스를 포함 해야 합니다. 크기 중립적인 원본은 광범위 한 크기의 범위에서 최상의 결과를 제공 하지만 필요 하지는 않습니다. 요소에 정의 되지 않은 크기의 이미지를 요청 하는 메시지가 표시 되 \<Image> 고 크기 중립적인 소스가 없으면 서비스에서 가장 적합 한 크기의 원본을 선택 하 고 요청 된 크기로 크기를 조정 합니다.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
    
|**특성**|**정의**|  
|-|-|
|Guid|하다 이미지 모니커의 GUID 부분입니다.|  
|ID|하다 이미지 모니커의 ID 부분입니다.|  
|AllowColorInversion|[선택 사항, 기본값 true] 이미지에서 짙은 배경에 사용 될 때 해당 색을 프로그래밍 방식으로 반전 시킬 수 있는지 여부를 나타냅니다.|  
  
 **원본**  
  
 \<Source>요소는 단일 이미지 소스 자산 (XAML 및 PNG)을 정의 합니다.  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|**특성**|**정의**|  
|-|-|  
|URI|하다 이미지를 로드할 수 있는 위치를 정의 하는 URI입니다. 다음 중 하나일 수 있습니다.<br /><br /> -Application:///authority를 사용 하는 [PACK URI](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx)<br /><br /> -절대 구성 요소 리소스 참조<br /><br /> -네이티브 리소스를 포함 하는 파일의 경로|  
|배경|필드 소스를 사용 하기 위해 사용할 배경의 종류를 나타냅니다.<br /><br /> 다음 중 하나일 수 있습니다.<br /><br /> - *Light*: 소스를 밝은 배경에 사용할 수 있습니다.<br /><br /> - *어둡게*: 소스를 짙은 배경으로 사용할 수 있습니다.<br /><br /> - *System.windows.forms.systeminformation.highcontrast*: 소스는 고대비 모드의 모든 백그라운드에서 사용할 수 있습니다.<br /><br /> - *HighContrastLight*: 소스는 고대비 모드에서 밝은 배경에 사용할 수 있습니다.<br /><br /> -*HighContrastDark*: 소스를 고대비 모드의 어두운 배경에 사용할 수 있습니다.<br /><br /> **배경** 특성을 생략 하면 모든 배경에서 소스를 사용할 수 있습니다.<br /><br /> **배경이** *Light*, *어둡게*, *HighContrastLight*또는 *HighContrastDark*인 경우 소스의 색은 반전 되지 않습니다. **배경이** 생략 되거나 *system.windows.forms.systeminformation.highcontrast*로 설정 된 경우 소스 색의 반전은 이미지의 **allowcolorinversion** 특성에 의해 제어 됩니다.|  
  
 요소에는 \<Source> 다음과 같은 선택적 하위 요소 중 하나만 있을 수 있습니다.  
  
|**요소**|**특성 (모두 필수)**|**정의**|  
|-|-|-|  
|\<Size>|값|원본은 지정 된 크기 (장치 단위)의 이미지에 사용 됩니다. 이미지가 정사각형이 됩니다.|  
|\<SizeRange>|MinSize, MaxSize|원본은 MinSize에서 MaxSize (장치 단위)까지 이미지에 사용 됩니다. 이미지가 정사각형이 됩니다.|  
|\<Dimensions>|너비, 높이|원본은 지정 된 너비 및 높이 (장치 단위)의 이미지에 사용 됩니다.|  
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, Maxwidth|이 소스는 최소 너비/높이에서 최대 너비/높이 (장치 단위)로 이루어진 이미지에 사용 됩니다.|  
  
 요소는 관리 되는 \<Source> \<NativeResource> \<Source> 어셈블리가 아니라 네이티브 어셈블리에서 로드 되는을 정의 하는 선택적 하위 요소를 포함할 수도 있습니다.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|**특성**|**정의**|  
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
  
|**특성**|**정의**|  
|-|-|  
|Guid|하다 이미지 모니커의 GUID 부분입니다.|  
|ID|하다 이미지 모니커의 ID 부분입니다.|  
|외부|[선택 사항, 기본값 false] 이미지 모니커가 현재 매니페스트의 이미지를 참조 하는지 여부를 나타냅니다.|  
  
 포함 된 이미지의 모니커는 현재 매니페스트에 정의 된 이미지를 참조할 필요가 없습니다. 이미지 라이브러리에서 포함 된 이미지를 찾을 수 없는 경우 빈 자리 표시자 이미지가 대신 사용 됩니다.  
  
## <a name="how-to-use-the-tool"></a>이 도구를 사용 하는 방법  
 **사용자 지정 이미지 매니페스트 유효성 검사**  
  
 사용자 지정 매니페스트를 만들려면 ManifestFromResources 도구를 사용 하 여 매니페스트를 자동으로 생성 하는 것이 좋습니다. 사용자 지정 매니페스트의 유효성을 검사 하려면 이미지 라이브러리 뷰어를 시작 하 고 파일 > 경로 설정 ...을 선택 합니다. 를 열려면 디렉터리 검색 대화 상자를 엽니다. 이 도구는 검색 디렉터리를 사용 하 여 이미지 매니페스트를 로드 하지만이 도구를 사용 하 여 매니페스트에 이미지를 포함 하는 .dll 파일을 찾을 수도 있으므로이 대화 상자에 매니페스트 및 DLL 디렉터리를 모두 포함 해야 합니다.  
  
 ![이미지 라이브러리 뷰어 검색](../../extensibility/internals/media/image-library-viewer-search.png "이미지 라이브러리 뷰어 검색")  
  
 **추가** ...를 클릭 합니다. 새 검색 디렉터리를 선택 하 여 매니페스트 및 해당 Dll을 검색 합니다. 이 도구는 디렉터리를 선택 하거나 선택 취소 하 여 이러한 검색 디렉터리를 설정 하거나 해제할 수 있습니다.  
  
 기본적으로이 도구는 Visual Studio 설치 디렉터리를 찾아 디렉터리 검색 목록에 해당 디렉터리를 추가 하려고 합니다. 도구에서 찾을 수 없는 디렉터리를 수동으로 추가할 수 있습니다.  
  
 모든 매니페스트가 로드 된 후에는 도구를 사용 하 여 이미지에 대 한 **배경색** , **DPI**, **고대비**또는 **grayscaling** 를 전환 하 여 다양 한 설정에 맞게 이미지 자산을 올바르게 렌더링 하는지 확인할 수 있습니다.  
  
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
