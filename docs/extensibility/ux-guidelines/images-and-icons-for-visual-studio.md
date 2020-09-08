---
title: Visual Studio의 이미지 및 아이콘 | Microsoft Docs
ms.date: 04/26/2017
ms.topic: overview
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edbf1542277189f37565e7ff415a52025094e595
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85906121"
---
# <a name="images-and-icons-for-visual-studio"></a>Visual Studio의 이미지 및 아이콘
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Visual Studio에서 이미지 사용
 아트워크를 만들기 전에 [Visual Studio 이미지 라이브러리](https://www.microsoft.com/download/details.aspx?id=35825)에 있는 1,000개 이상 이미지의 사용을 고려해 보세요.

### <a name="types-of-images"></a>이미지 형식

- **아이콘**. 명령, 계층 구조, 템플릿 등에 표시되는 작은 이미지입니다. Visual Studio에 사용되는 기본 아이콘 크기는 16x16 PNG입니다. 이미지 서비스에서 생성한 아이콘은 HDPI 지원을 위한 XAML 형식을 자동으로 생성합니다.

    > [!NOTE]
    > 이미지는 메뉴 시스템에서 사용되지만 모든 명령에 아이콘을 만들면 안 됩니다. 명령에 아이콘이 있어야 하는지를 확인하려면 [Visual Studio의 메뉴 및 명령](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)을 확인하세요.

- **썸네일.** 새 프로젝트 대화 상자와 같은 대화 상자의 미리 보기 영역에 사용되는 이미지입니다.

- **대화 상자 이미지.** 설명 그래픽 또는 메시지 표시기로 대화 상자 또는 마법사에 표시되는 이미지입니다. 어려운 개념을 설명하거나 사용자의 주의를 끌기 위해(알림, 경고) 필요한 경우에만 사용합니다.

- **애니메이션 이미지.** 진행률 표시기, 상태 표시줄 및 작업 대화 상자에서 사용됩니다.

- **커서.** 작업에서 마우스 사용이 허용되는지 여부, 개체를 놓을 수 있는 위치 등을 나타내는 데 사용됩니다.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a> 아이콘 디자인

### <a name="overview"></a>개요
 Visual Studio는 깔끔한 기하 도형과 양수/음수(밝게/어둡게)의 50/50 균형을 사용하고 직접적이며 이해 가능한 메타포를 사용하는 최신 스타일 아이콘을 사용합니다. 중요한 아이콘 디자인은 명확성, 단순화 및 컨텍스트를 중심으로 합니다.

- **명확성:** 아이콘에 의미와 개별성을 제공하는 핵심 메타포에 초점을 맞춥니다.

- **단순화:** 아이콘을 핵심 의미로 줄입니다. 장식 없이 필요한 요소만을 포함하여 테마를 가져옵니다.

- **컨텍스트:** 개념 개발 도중 아이콘의 역할의 모든 측면을 고려합니다. 이는 아이콘의 핵심 메타포를 구성하는 요소를 결정할 때 중요합니다.

  아이콘을 사용하면 다음과 같은 여러 디자인 요소를 피해야 합니다.

- 적절한 경우를 제외하고 UI 요소를 나타내는 아이콘을 사용하지 마세요. UI 요소가 일반적이고 명확하거나 고유하지 않은 경우 더 추상적이거나 기호화된 방법을 선택합니다.

- 문서, 폴더, 화살표 및 돋보기와 같은 일반적인 요소를 남용하지 마세요. 아이콘의 의미에 필요한 경우에만 해당 요소를 사용합니다. 예를 들어 오른쪽에 있는 돋보기는 검색, 찾아보기 및 찾기만 나타내야 합니다.

- 일부 레거시 아이콘 요소는 원근감의 사용을 유지하지만 원근감 없이 요소의 명확성이 부족한 경우를 제외하고는 새 아이콘을 만들지 마세요.

- 너무 많은 정보를 아이콘에 표시하지 마세요. 쉽게 인식할 수 있거나 인식 가능한 기호로 알 수 있는 간단한 이미지가 복잡한 이미지보다 유용합니다. 아이콘은 전체 스토리를 전달할 수 없습니다.

### <a name="icon-creation"></a>아이콘 만들기

#### <a name="concept-development"></a>개념 개발
 Visual Studio의 UI 내에는 다양한 아이콘 형식이 있습니다. 개발 도중 아이콘 형식을 신중하게 고려해야 합니다. 아이콘 요소에 명확하지 않거나 일반적이지 않은 UI 개체를 사용하지 마세요. 이러한 경우에는 스마트 태그 아이콘을 사용하는 등 기호화된 개체를 사용합니다. 왼쪽에 있는 추상 태그의 의미는 오른쪽에 있는 모호한 UI 기반 버전보다 훨씬 명확합니다.

|**기호화된 이미지의 올바른 사용**|**기호화된 이미지의 잘못된 사용**|
|-|-|
|![올바른 스마트 태그 아이콘](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![잘못된 스마트 태그 아이콘](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 쉽게 인식할 수 있는 표준 UI 요소가 아이콘에 적합한 경우가 있습니다. 창 추가를 예로 들 수 있습니다.

|**아이콘의 올바른 UI 요소**|**아이콘의 잘못된 UI 요소**|
|-|-|
|![올바른 창 추가 아이콘](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![잘못된 창 추가 아이콘](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 아이콘의 의미에 필요한 경우가 아니라면 문서를 기본 요소로 사용하지 마세요. 문서 추가(아래)에 문서 요소가 없으면 의미가 손실되지만 새로 고침을 사용하면 문서 요소가 의미를 전달하는 데 필요하지 않습니다.

|**올바른 문서 아이콘 사용**|**잘못된 문서 아이콘 사용**|
|-|-|
|![올바른 문서 아이콘](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![잘못된 문서 아이콘](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 “표시”의 개념은 모든 파일 표시 예제와 같이 표시되는 항목을 가장 잘 보여주는 아이콘으로 표시되어야 합니다. 리소스 뷰 예제와 같이 필요한 경우 “뷰”의 개념을 나타내기 위해 렌즈 메타포를 사용할 수 있습니다.

|**“표시”**|**“뷰”**|
|-|-|
|![표시 아이콘](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![뷰 아이콘](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 오른쪽을 향하는 돋보기 아이콘은 검색, 찾기 및 찾아보기만을 표현해야 합니다. 더하기 기호 또는 빼기 기호가 있는 왼쪽을 향하는 변형은 확대/축소만 표시해야 합니다.

|**“검색”**|**“확대/축소”**|
|-|-|
|![검색 아이콘](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![확대/축소 아이콘](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 트리 뷰에서는 폴더 아이콘과 한정자를 둘 다 사용하지 마세요. 가능한 경우 한정자만 사용하세요.

|**올바른 트리 뷰 아이콘**|**잘못된 트리 뷰 아이콘**|
|-|-|
|![올바른 트리 뷰 아이콘 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![올바른 트리 뷰 아이콘 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![잘못된 트리 뷰 아이콘 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![잘못된 트리 뷰 아이콘 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>스타일 세부 정보

#### <a name="layout"></a>Layout
 표준 16x16 아이콘에 대해 표시된 스택 요소:

 ![16 x 16 아이콘에 대한 레이아웃 스택](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />16 x 16 아이콘에 대한 레이아웃 스택

 상태 알림 요소는 독립 실행형 아이콘으로 사용하는 것이 더 좋습니다. 하지만 작업 완료 아이콘과 같이 기본 요소에 대한 알림이 누적되는 컨텍스트가 있습니다.

 ![Visual Studio의 독립 실행형 알림](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />독립 실행형 알림 아이콘

 ![작업 완료 아이콘](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />작업 완료 아이콘

 프로젝트 아이콘은 일반적으로 여러 크기를 포함하는 .ico 파일입니다. 대부분의 16x16 아이콘에는 같은 요소가 포함됩니다. 32x32 버전은 프로젝트 형식을 포함하여 더 많은 정보를 포함합니다.

 ![Visual Studio의 프로젝트 아이콘](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />VB Windows 컨트롤 라이브러리 프로젝트 아이콘, 16x16 및 32x32

 아이콘을 픽셀 프레임 내 중앙에 배치합니다. 가능하지 않은 경우 아이콘을 프레임의 상단 및/또는 오른쪽에 맞춥니다.

 ![픽셀 프레임 내의 가운데에 맞춰진 아이콘](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />픽셀 프레임 내의 가운데에 맞춰진 아이콘

 ![픽셀 프레임의 오른쪽 위에 맞춰진 아이콘](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />프레임의 오른쪽 상단에 맞춰진 아이콘

 ![픽셀 프레임의 위쪽 가운데에 맞춰진 아이콘](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />프레임의 상단 가운데에 맞춰진 아이콘

 이상적인 맞춤 및 균형을 유지하려면 아이콘의 기본 요소가 작업 문자 모양을 방해하지 않도록 해야 합니다. 기본 요소의 상단 왼쪽 근처에 문자 모양을 삽입합니다. 요소를 추가할 때 아이콘의 맞춤 및 균형을 고려합니다.

|**올바른 맞춤 및 균형**|**잘못된 맞춤 및 균형**|
|-|-|
|![올바른 아이콘 균형 및 맞춤](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![잘못된 아이콘 균형 및 맞춤](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 요소를 공유하고 세트로 사용되는 아이콘에 대한 크기 패리티를 확인합니다. 잘못된 쌍에서 원과 화살표의 크기가 크고 일치하지 않습니다.

|**올바른 크기 패리티**|**잘못된 크기 패리티**|
|-|-|
|![올바른 아이콘 크기 및 패리티](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![잘못된 아이콘 크기 및 패리티](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 일관된 선 및 시각적 중량감을 사용합니다. 병렬 비교를 사용하여 빌드하는 아이콘이 다른 아이콘과 어떻게 비교되는지 평가합니다. 전체 16x16 프레임을 사용하지 않고, 15x15 이하를 사용합니다. 음수-양수(어두움-밝음) 비율은 50/50이어야 합니다.

|**올바른 음수-양수 비율**|**잘못된 음수-양수 비율**|
|-|-|
|![아이콘에 대한 정확한 시각적 중량감 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![아이콘에 대한 정확한 시각적 중량감 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![아이콘에 대한 정확한 시각적 중량감 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![아이콘에 대한 잘못된 시각적 중량감](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 간단하고 비교 가능한 도형 및 상호 보완적 각도를 사용하여 요소 무결성을 저하하지 않고 요소를 빌드합니다. 가급적 45° 또는 90° 각도를 사용합니다.

 ![올바른 아이콘 각도](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>관점
 아이콘을 명확하고 이해하기 쉽도록 유지합니다. 필요한 경우 원근감과 광원을 사용합니다. 아이콘 요소에서 원근감을 사용하는 것은 좋지 않지만 일부 요소는 원근감 없이는 인식할 수 없습니다. 이러한 경우 세련된 원근감은 요소의 명확성을 전달합니다.

 ![3점 원근감](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />3점 원근감

 ![1점 원근감](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />1점 원근감

 대부분의 요소는 오른쪽을 향하거나 오른쪽으로 각집니다.

 ![오른쪽으로 각진 아이콘](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 개체에 필요한 명확성을 더하는 경우에만 광원을 사용합니다.

|**올바른 광원**|**잘못된 광원**|
|-|-|
|![아이콘에 대한 올바른 광원](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![아이콘에 대한 잘못된 광원](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 윤곽선만을 사용하여 가독성을 높이거나 의미를 전달합니다. 음수-양수(어둡게-밝게) 균형은 50/50입니다.

|**올바른 윤곽선 사용**|**잘못된 윤곽선 사용**|
|-|-|
|![올바른 윤곽선](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![잘못된 윤곽선](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>아이콘 유형
 **셸 및 명령 모음** 아이콘은 다음 요소 중 세 가지 이하로 구성됩니다. 하나의 기본, 하나의 한정자, 하나의 동작 또는 하나 이상의 상태입니다.

 ![셸 및 명령 모음 아이콘의 예](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />셸 및 명령 모음 아이콘의 예

 **도구 창 명령 모음** 아이콘은 다음 요소 중 세 가지 이하로 구성됩니다. 하나의 기본, 하나의 한정자, 하나의 동작 또는 하나 이상의 상태입니다.

 ![도구 창 명령 모음 아이콘의 예](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />도구 창 명령 모음 아이콘의 예

 **트리 뷰 중의성 해결기** 아이콘은 다음 요소 중 세 가지 이하로 구성됩니다. 하나의 기본, 하나의 한정자, 하나의 동작 또는 하나 이상의 상태입니다.

 ![트리 뷰 중의성 해결기 아이콘의 예](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />트리 뷰 중의성 해결기 아이콘의 예

 **상태 기반 값 분류** 아이콘은 활성, 활성 사용 안 함, 비활성 사용 안 함 상태로 존재합니다.

 ![상태 기반 값 분류 아이콘의 예](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />상태 기반 값 분류 아이콘의 예

 **IntelliSense** 아이콘은 다음 요소 중 세 가지 이하로 구성됩니다. 하나의 기본, 하나의 한정자, 하나의 상태입니다.

 ![IntelliSense 아이콘의 예](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />IntelliSense 아이콘의 예

 **작은(16x16) 프로젝트** 아이콘에는 두 가지 이하의 요소가 있어야 합니다. 하나의 기본 및 하나의 한정자입니다.

 ![작은(16x16) 프로젝트 아이콘의 예](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 프로젝트 아이콘 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 프로젝트 아이콘 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />작은(16x16) 프로젝트 아이콘의 예

 **큰(32x32) 프로젝트** 아이콘에는 네 가지 이하의 요소가 있어야 합니다. 하나의 기본, 1~2개의 한정자 및 하나의 언어 오버레이입니다.

 ![큰(32x32) 프로젝트 아이콘의 예](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />큰(32x32) 프로젝트 아이콘의 예

### <a name="production-details"></a>프로덕션 세부 정보
 모든 새 UI 요소는 Windows Presentation Foundation(WPF)을 사용하여 만들어야 하며 WPF의 모든 새 아이콘은 32비트 PNG 형식이어야 합니다. 24비트 PNG는 투명도를 지원하는 레거시 형식이므로 아이콘에는 권장되지 않습니다.

 해상도를 96DPI로 저장합니다.

#### <a name="file-types"></a>파일 형식

- **32비트 PNG:** 아이콘의 기본 형식입니다. 단일 래스터(픽셀) 이미지를 저장할 수 있는 무손실 데이터 압축 파일 형식입니다. 32비트 PNG 파일은 알파 채널 투명도, 감마 보정 및 인터레이스를 지원합니다.

- **32비트 BMP:** 비 WPF 컨트롤용입니다. XP 또는 하이 컬러라고도 하는 32비트 BMP는 RGB/A 이미지 형식으로, 알파 채널 투명도를 사용하는 트루 컬러 이미지입니다. 알파 채널은 Adobe Photoshop에서 지정된 투명도 레이어로, 비트맵 내에 추가(4번째) 색 채널로 저장됩니다. 검은색 배경은 아트워크 제작 도중 모든 32비트 BMP 파일에 추가되어 색 농도에 대한 간단한 시각적 정보를 제공합니다. 이 검은색 배경은 UI에서 마스킹되는 영역을 나타냅니다.

- **32비트 ICO:** 프로젝트 아이콘 및 항목 추가용입니다. 모든 ICO 파일은 알파 채널 투명도(RGB/A)를 사용하는 32비트 트루 컬러입니다. ICO 파일은 여러 크기와 색 농도를 저장할 수 있으므로 Vista 아이콘은 종종 16x16, 32x32, 48x48 및 256x256 이미지 크기를 포함하는 ICO 형식입니다. Windows 탐색기에서 제대로 표시되려면 각 이미지 크기에 24비트 및 8비트 색 농도로 ICO 파일을 저장해야 합니다.

- **XAML:** 디자인 화면 및 Windows 표시기용입니다. XAML 아이콘은 스케일링, 회전, 파일링 및 투명도를 지원하는 벡터 기반 이미지 파일입니다. 현재는 Visual Studio에서 일반적으로 사용하지 않지만 유연성 덕분에 많이 사용되고 있습니다.

- **SVG**

- **24비트 BMP:** Visual Studio 명령 모음. 트루 컬러 RGB 이미지 형식인 24비트 BMP는 자홍색(R = 255, G = 0, B = 255)을 녹아웃 투명도 레이어에 대한 색상 키로 사용하여 투명도 레이어를 만드는 아이콘 규칙입니다. 24비트 BMP에서 모든 자홍색 화면은 배경색을 사용하여 표시됩니다.

- **24비트 GIF:** Visual Studio 명령 모음. 투명도를 지원하는 트루 컬러 RGB 이미지 형식입니다. GIF 파일은 마법사 아트워크 및 GIF 애니메이션에서 자주 사용됩니다.

### <a name="icon-construction"></a>아이콘 생성
 Visual Studio에서 가장 작은 아이콘 크기는 16x16입니다. 일반적으로 사용되는 가장 큰 값은 32x32입니다. 아이콘을 디자인할 때 16x16, 24x24 또는 32x32프레임 전체를 채우지 않도록 주의하세요. 이해하기 쉽고 일관성 있는 아이콘 생성은 사용자 인식에 필수적입니다. 아이콘을 생성하는 경우 다음 사항을 따릅니다.

- 아이콘은 명확하고 이해하기 쉬우며 일관적이어야 합니다.

- 상태 알림 요소를 단일 아이콘으로 사용하고 이를 아이콘 기본 요소 위에 쌓지 않는 것이 좋습니다. 특정 컨텍스트에서 UI를 사용하려면 상태 요소가 기본 요소와 쌍을 이루어야 할 수 있습니다.

- 프로젝트 아이콘은 일반적으로 여러 크기를 포함하는 .ico 파일입니다. 16x16, 24x24 및 32x32 아이콘만 업데이트됩니다. 대부분의 16x16 및 24x24 아이콘에는 동일한 요소가 포함됩니다. 32x32 아이콘에는 해당되는 경우 프로젝트 언어 형식을 포함한 자세한 내용이 포함됩니다.

- 32x32 아이콘의 경우 기본 요소에는 일반적으로 두께가 2픽셀인 선이 있습니다. 1~2픽셀 선 두께는 세부 요소에 사용할 수 있습니다. 최적의 판단을 활용하여 더욱 적합한 것을 결정하세요.

- 16x16 및 24x24 아이콘의 요소 사이에 적어도 1픽셀의 간격이 있어야 합니다. 32x32 아이콘의 경우 요소 사이와 한정자 및 기본 요소 사이에 2픽셀 간격을 사용합니다.

  ![16x16, 24x24 및 32x32 크기 아이콘을 위한 요소 간격](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />16x16, 24x24 및 32x32 크기 아이콘을 위한 요소 간격

#### <a name="color-and-accessibility"></a>색 및 접근성
 Visual Studio 규정 준수 지침에 따르면 제품의 모든 아이콘이 색 및 대비에 대한 접근성 요구 사항을 통과해야 합니다. 이는 아이콘 반전을 통해 이루어지고, 디자인할 때 제품에서 프로그래밍 방식으로 반전된다는 점을 인식해야 합니다.

 Visual Studio 아이콘에서 색을 사용하는 방법에 대한 자세한 내용은 [이미지에서 색 사용](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)을 참조하세요.

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> 이미지에서 색 사용

### <a name="overview"></a>개요
 Visual Studio의 아이콘은 주로 단색입니다. 색은 특정 정보를 전달하기 위해 예약되어 있으며 데코레이션으로 사용되지 않습니다. 색의 용도:

- 작업 표시

- 사용자에게 상태 알림 경고

- 언어 소속 지정

- IntelliSense 내에서 항목 구분

### <a name="accessibility"></a>액세스 가능성
 Visual Studio 규정 준수 지침에 따르면 제품의 모든 아이콘이 색 및 대비에 대한 접근성 요구 사항을 통과해야 합니다. 시각적 개체 언어 색상표의 색은 테스트되었으며 요구 사항을 충족합니다.

#### <a name="color-inversion-for-dark-themes"></a>어두운 테마에서 색 반전
 Visual Studio의 어두운 테마에서 아이콘이 올바른 명암비로 표시되도록 반전은 프로그래밍 방식으로 적용됩니다. 이 가이드의 색은 올바르게 반전되도록 선택되었습니다. 이 색상표에서 색 사용을 제한하지 않으면 반전이 적용될 때 예기치 않은 결과가 발생할 수 있습니다.

 ![색이 반전된 아이콘의 예](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />색이 반전된 아이콘의 예

### <a name="base-palette"></a>기본 색상표
 모든 표준 아이콘에는 세 가지 기본색이 포함되어 있습니다. 3D 도구 아이콘에 대해 1~2개의 예외를 포함하는 아이콘에는 그라데이션 또는 그림자가 포함되지 않습니다.

|사용량|Name|값(밝은 테마)|견본|예|
|-----------|----------|---------------------------|------------|-------------|
|배경/어두운|VS BG|424242 / 66,66,66|![견본 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![기본 색상표 예](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|전경/밝은|VS FG|F0EFF1 / 240,239,241|![견본 F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|윤곽선|VS Out|F6F6F6 / 246,246,246|![견본 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 기본색 외에도 각 아이콘에는 확장된 색상표에서 하나의 추가 색이 포함될 수 있습니다.

### <a name="extended-palette"></a>확장된 색상표

#### <a name="action-modifiers"></a>작업 한정자
 아래 4가지 색은 작업 한정자에 필요한 작업 유형을 표시합니다.

|사용량|Name|값(모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|양수|VS Action Green|388A34 / 56,138,52|![견본 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|음수|VS Action Red|A1260D / 161,38,13|![견본 A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|무감정|VS Action Blue|00539C / 0,83,156|![견본 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|만들기/새|VS Action Orange|C27D1A / 194,156,26|![견본 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>예제
 녹색은 “추가”, “실행”, “재생” 및 “유효성 검사”와 같은 긍정 작업 한정자에 사용됩니다.

|실행|쿼리 실행|모든 단계 재생|컨트롤 추가|
|-|-|-|-|
|![실행 아이콘](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![쿼리 실행 아이콘](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![모든 단계 재생 아이콘](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![컨트롤 추가 아이콘](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 빨간색은 “삭제”, “중지”, “취소” 및 “닫기”와 같은 음수 작업 한정자에 사용됩니다.

|관계 삭제|열 삭제|쿼리 중지|오프라인 연결|
|-|-|-|-|
|![관계 삭제 아이콘](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![열 삭제 아이콘](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![쿼리 중지 아이콘](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![오프라인 연결 상태 아이콘](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 파란색은 “열기”, “다음”, “이전”, “가져오기” 및 “내보내기”와 같이 주로 화살표로 표시되는 중립 작업 한정자에 적용됩니다.

|필드로 이동|일괄 처리된 체크 인|주소 편집기|연결 편집기|
|-|-|-|-|
|![필드로 이동 아이콘](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![일괄 처리된 체크인 아이콘](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![주소 편집기 아이콘](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![연결 편집기 아이콘](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 어두운 황금색은 주로 “새” 한정자에 사용됩니다.

|새 프로젝트|새 그래프 만들기|새 단위 테스트|새 목록 항목|
|-|-|-|-|
|![새 프로젝트 아이콘](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![새 그래프 아이콘 만들기](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![새 단위 테스트 아이콘](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![새 목록 항목 아이콘](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>특수 사례
 특수한 사례에서 색이 지정된 작업 한정자를 독립 실행형 아이콘으로 독립적으로 사용할 수 있습니다. 아이콘에 사용되는 색은 아이콘이 연결된 동작을 반영합니다. 다음을 포함한 아이콘의 작은 하위 집합으로 사용이 제한됩니다.

|실행|중지|삭제|저장|뒤로 탐색|
|-|-|-|-|-|
|![실행 아이콘](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![중지 아이콘](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![삭제 아이콘](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![저장 아이콘](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![뒤로 탐색 아이콘](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>코드 계층 구조 색상표

#### <a name="folder"></a>폴더

|사용량|Name|값(모든 테마)|견본|예|
|-----------|----------|--------------------------|------------|-------------|
|폴더|폴더|DCB67A / 220,182,122|![견본 DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![폴더 색 아이콘](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio 언어
 Visual Studio에서 사용할 수 있는 각 공용 언어 또는 플랫폼에는 연결된 색이 있습니다. 해당 색은 기본 아이콘 또는 복합 아이콘의 오른쪽 상단에 표시되는 언어 한정자에 사용됩니다.

|사용량|Name|값(모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Blue|0095D7 / 0,149,215|![견본 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP Purple|9B4F96 / 155,79,150|![견본 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS Green(VS Action Green)|388A34 / 56,138,52|![견본 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS Red|BD1E2D / 189,30,45|![견본 BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS Purple|672878 / 103,40,120|![견본 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Orange|F16421 / 241,100,33|![견본 F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Blue(VS Action Blue)|00539C / 0,83,156|![견본 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Orange|E04C06 / 224,76,6|![견본 E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY Green|879636 / 135,150,54|![견본 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>언어 한정자가 있는 아이콘의 예

|VB|C#|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Visual Basic 아이콘](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![C&#35; 아이콘](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![C&#43;&#43; 아이콘](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![F&#35; 아이콘](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![JavaScript 아이콘](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Python 아이콘](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|-|
|![HTML 아이콘](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![WPF 아이콘](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![ASP 아이콘](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![CSS 아이콘](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript 아이콘](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense 아이콘은 전용 색상표를 사용합니다. 해당 색은 사용자가 IntelliSense 팝업 목록의 여러 항목을 신속하게 구분할 수 있도록 돕는 데 사용됩니다.

|사용량|Name|값(모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|클래스, 이벤트|VS Action Orange|C27D1A / 194,125,26|![견본 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|확장 메서드, 메서드, 모듈, 대리자|VS Action Purple|652D90 / 101,45,144|![견본 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|필드, 열거형 항목, 매크로, 구조체, 공용 구조체 값 형식, 연산자, 인터페이스|VS Action Blue|00539C / 0,83,156|![견본 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS Action Green|388A34 / 56,138,52|![견본 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|상수, 예외, 열거형 항목, 맵, 맵 항목, 네임스페이스, 템플릿, 형식 정의|배경(VS BG)|424242 / 66,66,66|![견본 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense 아이콘의 예

|클래스|프라이빗 이벤트|대리자|메서드 친구|필드|
|-|-|-|-|-|
|![IntelliSense 클래스 아이콘](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![IntelliSense Private 이벤트 아이콘](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![IntelliSense 대리자 아이콘](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![IntelliSense 메서드 친구 아이콘](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![필드 아이콘](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|보호된 열거형 항목|Object|템플릿|예외 바로 가기|
|-|-|-|-|
|![IntelliSense 보호된 열거형 항목 아이콘](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![intellisense 개체 아이콘](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![IntelliSense 템플릿 아이콘](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![IntelliSense 예외 바로 가기 아이콘](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>공지
 Visual Studio의 알림은 상태를 나타내는 데 사용됩니다. 알림 색상표는 다음 4가지 색 및 검은색 또는 흰색 전경 채우기 옵션을 사용하여 다음 상태 수준으로 알림을 정의합니다.

|사용량|Name|값(모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|상태: 보통|Notification Blue(VS Blue)|1BA1E2 / 27,161,226|![견본 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|상태: 긍정|Notification Green(VS Green)|339933 / 51,153,51|![견본 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|상태: 부정|Notification Red(VS Red)|E51400 / 229,20,0|![견본 E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|상태: 경고|Notification Yellow(VS Orange)|FFCC00 / 255,204,0|![견본 FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|전경 채우기|Notification Black(Black)|000000 / 0,0,0|![견본 &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|전경 채우기|Notification White(White)|FFFFFF / 255,255,255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>알림 아이콘의 예

|경고|경고|완료|중지|
|-|-|-|-|
|![경고 아이콘](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![경고 아이콘](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![완료 아이콘](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![중지 아이콘](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|