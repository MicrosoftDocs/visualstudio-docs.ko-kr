---
title: 비주얼 스튜디오를 위한 이미지와 아이콘 | 마이크로 소프트 문서
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfef803d2bffb19cc54974465c7892b4d68ff3d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699044"
---
# <a name="images-and-icons-for-visual-studio"></a>Visual Studio의 이미지 및 아이콘
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>비주얼 스튜디오에서 이미지 사용
 아트웍을 만들기 전에 [Visual Studio 이미지 라이브러리에서](https://www.microsoft.com/download/details.aspx?id=35825)1,000개 이상의 이미지를 사용하는 것이 좋습니다.

### <a name="types-of-images"></a>이미지 유형

- **아이콘**. 명령, 계층 구조, 템플릿 등으로 표시되는 작은 이미지입니다. Visual Studio에서 사용되는 기본 아이콘 크기는 16x16 PNG입니다. 이미지 서비스에서 생성된 아이콘은 HDPI 지원을 위해 XAML 형식을 자동으로 생성합니다.

    > [!NOTE]
    > 이미지는 메뉴 시스템에서 사용되지만 모든 명령에 대한 아이콘을 만들면 안 됩니다. [Visual Studio의 메뉴 및 명령을](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) 참조하여 명령에 아이콘을 받아야 하는지 여부를 확인합니다.

- **축소판.** 새 프로젝트 대화 상자와 같은 대화 상자의 미리 보기 영역에 사용되는 이미지입니다.

- **대화 상자 이미지입니다.** 대화 상자 또는 마법사에 표시되는 이미지(설명그래픽 또는 메시지 표시기)입니다. 어려운 개념을 설명하거나 사용자의 주의를 끌기 위해 필요한 경우에만 자주 사용하지 말거나(경고, 경고).

- **애니메이션 된 이미지입니다.** 진행률 표시기, 상태 표시줄 및 작업 대화 상자에 사용됩니다.

- **커서.** 마우스를 사용하여 작업이 허용되는지 여부, 개체를 삭제할 수 있는 위치 등을 나타내는 데 사용됩니다.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>아이콘 디자인

### <a name="overview"></a>개요
 Visual Studio는 깔끔한 지오메트리와 50/50 의 양수/음수(밝은/어두운) 균형을 가진 현대적인 스타일의 아이콘을 사용하며 직접적이고 이해할 수 있는 은유를 사용합니다. 중요한 아이콘 디자인 포인트는 명확성, 단순화 및 컨텍스트를 중심으로 합니다.

- **선명도:** 아이콘의 의미와 개성을 주는 핵심 은유에 초점을 맞춥니다.

- **단순화 :** 핵심 의미로 아이콘을 줄이십시오 - 필요한 요소와 프릴없이 테마를 가져옵니다.

- **컨텍스트:** 아이콘의 핵심 은유를 구성하는 요소를 결정할 때 중요한 개념 개발 중에 아이콘역할의 모든 측면을 고려합니다.

  아이콘을 사용하면 다음과 같은 여러 가지 디자인 포인트를 사용하지 마십시오.

- 적절한 경우를 제외하고 UI 요소를 나타내는 아이콘은 사용하지 마십시오. UI 요소가 일반적이거나 분명하거나 고유하지 않을 때 보다 추상적이거나 상징적인 방법을 선택합니다.

- 문서, 폴더, 화살표 및 돋보기와 같은 일반적인 요소를 과도하게 사용하지 마십시오. 아이콘의 의미에 필수적인 경우에만 이러한 요소를 사용합니다. 예를 들어 오른쪽 을 향한 돋보기는 검색, 찾아보기 및 찾기만 표시해야 합니다.

- 일부 레거시 아이콘 요소는 원근을 유지하지만 요소가 없는 경우 명확성이 부족하지 않는 한 원근을 사용하여 새 아이콘을 만들지 마십시오.

- 아이콘에 너무 많은 정보를 벼락치 밀어하지 마십시오. 쉽게 인식하거나 인식 할 수있는 기호로 배울 수있는 간단한 이미지는 지나치게 복잡한 이미지보다 훨씬 더 유용합니다. 아이콘은 전체 스토리를 전달할 수 없습니다.

### <a name="icon-creation"></a>아이콘 만들기

#### <a name="concept-development"></a>개념 개발
 Visual Studio에는 UI 내에 다양한 아이콘 유형이 있습니다. 개발 중에 아이콘 유형을 신중하게 고려하십시오. 아이콘 요소에 명확하지 않거나 드문 UI 개체를 사용하지 마십시오. 스마트 태그 아이콘과 같이 이러한 경우 기호를 선택합니다. 왼쪽에 있는 추상 태그의 의미는 오른쪽의 모호한 UI 기반 버전보다 더 분명합니다.

|||
|-|-|
|**기호 이미지의 올바른 사용**|**기호 이미지의 잘못된 사용**|
|![올바른 스마트 태그 아이콘](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![잘못된 스마트 태그 아이콘](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 쉽게 알아볼 수 있는 표준 UI 요소가 아이콘에 적합한 경우가 있습니다. 창 추가는 다음과 같은 예입니다.

|||
|-|-|
|**아이콘의 올바른 UI 요소**|**아이콘의 잘못된 UI 요소**|
|![올바른 창 추가 아이콘](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![잘못된 창 추가 아이콘](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 아이콘의 의미에 필수적인 경우가 아니면 문서를 기본 요소로 사용하지 마십시오. 문서 추가(아래)의 문서 요소가 없으면 의미가 손실되는 반면 새로 고침을 사용하면 문서 요소가 의미를 전달할 필요가 없습니다.

|||
|-|-|
|**문서 아이콘의 올바른 사용**|**문서 아이콘의 잘못된 사용**|
|![올바른 문서 아이콘](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![잘못된 문서 아이콘](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 "show"의 개념은 모든 파일 표시 예제와 같이 표시되는 내용을 가장 잘 보여 주는 아이콘으로 표시되어야 합니다. 리소스 뷰 예제와 같이 필요한 경우 렌즈 비유를 사용하여 "보기"의 개념을 나타낼 수 있습니다.

|||
|-|-|
|**"쇼"**|**"뷰"**|
|![표시 아이콘](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![뷰 아이콘](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 오른쪽 돋보기 아이콘은 검색, 찾기 및 찾아보기만 나타내야 합니다. 더하기 기호 또는 마이너스 기호가 있는 왼쪽 을 향하는 변형은 확대/축소만 나타내야 합니다.

|||
|-|-|
|**"검색"**|**"확대/축소"**|
|![검색 아이콘](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![확대/축소 아이콘](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 트리 뷰에서는 폴더 아이콘과 수정자를 모두 사용하지 마십시오. 사용 가능한 경우 수정자만 사용합니다.

|||
|-|-|
|**올바른 트리 뷰 아이콘**|**잘못된 트리 뷰 아이콘**|
|![올바른 트리 뷰 아이콘 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") 올바른 트리 뷰 아이콘 &#40;2 ![&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![잘못된 트리 뷰 아이콘 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") 잘못된 트리 뷰 아이콘 &#40;2 ![&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>스타일 세부 정보

#### <a name="layout"></a>레이아웃
 표준 16x16 아이콘에 표시된 대로 요소를 스택합니다.

 ![16 x 16 아이콘에 대한 레이아웃 스택](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />16 x 16 아이콘에 대한 레이아웃 스택

 상태 알림 요소는 독립 실행형 아이콘으로 더 잘 사용됩니다. 그러나 작업 완료 아이콘과 같이 기본 요소에 알림을 누적해야 하는 컨텍스트가 있습니다.

 ![Visual Studio의 독립 실행형 알림](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />독립 실행형 알림 아이콘

 ![작업 완료 아이콘](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />작업 완료 아이콘

 프로젝트 아이콘은 일반적으로 여러 크기를 포함하는 .ico 파일입니다. 대부분의 16x16 아이콘에는 동일한 요소가 포함됩니다. 32x32 버전에는 프로젝트 유형(해당하는 경우)을 포함하여 자세한 정보가 있습니다.

 ![Visual Studio의 프로젝트 아이콘](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />VB 윈도우 컨트롤 라이브러리 프로젝트 아이콘, 16x16 및 32x32

 픽셀 프레임 내에 아이콘을 가운데에 두는 것입니다. 그렇지 않은 경우 아이콘을 프레임의 위쪽 및/또는 오른쪽에 맞춥으로 정렬합니다.

 ![픽셀 프레임 내의 가운데에 맞춰진 아이콘](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />픽셀 프레임 내의 가운데에 맞춰진 아이콘

 ![픽셀 프레임의 오른쪽 위에 맞춰진 아이콘](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />프레임 의 오른쪽 상단에 정렬 된 아이콘

 ![픽셀 프레임의 위쪽 가운데에 맞춰진 아이콘](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />아이콘이 프레임 의 맨 위에 가운데로 정렬됩니다.

 이상적인 정렬과 균형을 이루려면 동작 문말으로 아이콘의 기본 요소를 방해하지 마십시오. 글리프는 기본 요소의 왼쪽 위 근처에 배치합니다. 추가 요소를 추가할 때 아이콘의 정렬과 균형을 고려합니다.

|||
|-|-|
|**올바른 정렬 및 균형**|**잘못된 정렬 및 균형**|
|![올바른 아이콘 균형 및 맞춤](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![잘못된 아이콘 균형 및 맞춤](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 요소를 공유하고 집합에 사용되는 아이콘의 크기 패리티를 확인합니다. 잘못된 페어링에서 원과 화살표는 크기가 크고 일치하지 않습니다.

|||
|-|-|
|**올바른 크기 패리티**|**잘못된 크기 패리티**|
|![올바른 아이콘 크기 및 패리티](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![잘못된 아이콘 크기 및 패리티](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 일관된 선 및 시각적 가중치를 사용합니다. 나란히 비교를 사용하여 빌드하는 아이콘이 다른 아이콘과 비교되는 방식을 평가합니다. 전체 16x16 프레임을 사용하지 말고 15x15 이하를 사용하십시오. 음수 대 양수(어두운 대 광) 비율은 50/50이어야 합니다.

|||
|-|-|
|**음수 대 양수 비율 수정**|**잘못된 음수 대 양수 비율**|
|![아이콘 &#40;1&#41;대한 시각적 가중치 수정](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![2&#41;&#40;아이콘에 대한 시각적 가중치 를 수정합니다.](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![3&#41;&#40;아이콘에 대한 시각적 가중치 를 수정합니다.](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![아이콘에 대한 잘못된 시각적 중량감](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 단순하고 비교할 수 있는 모양과 상호 보완적인 각도를 사용하여 요소 무결성을 희생하지 않고 요소를 빌드합니다. 가능한 경우 45° 또는 90° 각도를 사용하십시오.

 ![올바른 아이콘 각도](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>관점
 아이콘을 명확하고 이해할 수 있도록 유지합니다. 필요한 경우에만 원근 및 광원을 사용합니다. 아이콘 요소에 대한 원근을 사용하지 는 피해야 하지만 일부 요소는 아이콘 요소 없이는 인식할 수 없습니다. 이러한 경우 양식에 일치시키는 원근은 요소의 명확성을 전달합니다.

 ![3점 원근감](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />3점 원근감

 ![1점 원근감](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />1점 원근감

 대부분의 요소는 오른쪽으로 향하거나 각도가 있어야 합니다.

 ![오른쪽으로 각진 아이콘](../../extensibility/ux-guidelines/media/0404-33_angledright.png "33_AngledRight 0404-33_AngledRight")

 오브젝트에 필요한 선명도를 추가할 때만 광원을 사용합니다.

|||
|-|-|
|**올바른 광원**|**잘못된 광원**|
|![아이콘에 대한 올바른 광원](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![아이콘에 대한 잘못된 광원](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 윤곽선을 사용하여 가독성을 높이거나 은유를 더 잘 전달할 수 있습니다. 음수-양수(어두운 빛) 균형은 50/50이어야 합니다.

|||
|-|-|
|**윤곽선 올바른 사용**|**윤곽선 잘못된 사용**|
|![올바른 윤곽선](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![잘못된 윤곽선](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>아이콘 유형
 **셸 및 명령 모음** 아이콘은 기본 요소 1개, 수정자 1개, 작업 1개 또는 상태 1개 중 3개 이하로 구성됩니다.

 ![셸 및 명령 모음 아이콘의 예](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />셸 및 명령 모음 아이콘의 예

 **도구 창 명령 모음** 아이콘은 기본 요소 1개, 수정자 1개, 작업 1개 또는 상태 1개 중 세 개 이하로 구성됩니다.

 ![도구 창 명령 모음 아이콘의 예](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />도구 창 명령 모음 아이콘의 예

 **트리 뷰 모호성** 아이콘은 다음 요소 중 3개 이하로 구성됩니다.

 ![트리 뷰 모호성 아이콘의 예](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />트리 뷰 모호성 아이콘의 예

 **상태 기반 값 분류** 아이콘은 활성 상태, 활성 사용 안 함 및 비활성 사용 안 함의 상태에 있습니다.

 ![상태 기반 값 분류 아이콘의 예](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />상태 기반 값 분류 아이콘의 예

 **IntelliSense** 아이콘은 다음 요소 중 세 개 이하로 구성됩니다: 기본 요소 1개, 수정자 1개, 상태 1개.

 ![인텔리센스 아이콘의 예](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />인텔리센스 아이콘의 예

 **작은(16x16) 프로젝트** 아이콘에는 하나의 기본 요소와 한 개의 수정자라는 두 개의 요소가 없어야 합니다.

 ![작은 (16x16) 프로젝트 아이콘의 예](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 프로젝트 아이콘 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 프로젝트 아이콘 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />작은(16x16) 프로젝트 아이콘의 예

 **대형(32x32) 프로젝트** 아이콘은 기본 요소 1개, 수정자 1개, 언어 오버레이 1개 등 네 개 이하로 구성됩니다.

 ![대형(32x32) 프로젝트 아이콘의 예](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />대형(32x32) 프로젝트 아이콘의 예

### <a name="production-details"></a>생산 세부 정보
 모든 새 UI 요소는 WPF(Windows 프레젠테이션 파운데이션)를 사용하여 만들어야 하며 WPF에 대한 모든 새 아이콘은 32비트 PNG 형식이어야 합니다. 24비트 PNG는 투명도를 지원하지 않는 레거시 형식이므로 아이콘에는 권장되지 않습니다.

 해상도를 96 DPI로 저장합니다.

#### <a name="file-types"></a>파일 형식

- **32비트 PNG:** 아이콘에 대한 기본 형식입니다. 단일 래스터(픽셀) 이미지를 저장할 수 있는 무손실 데이터 압축 파일 형식입니다. 32비트 PNG 파일은 알파 채널 투명도, 감마 보정 및 인터레이스를 지원합니다.

- **32비트 BMP:** WPF가 아닌 컨트롤의 경우. XP 또는 높은 색상이라고도 하는 32비트 BMP는 알파 채널 투명도가 있는 트루 컬러 이미지인 RGB/A 이미지 형식입니다. 알파 채널은 Adobe Photoshop에서 지정한 투명도 레이어로 비트맵 내에 추가(네 번째) 색상 채널로 저장됩니다. 모든 32비트 BMP 파일에 아트웍 제작 중에 검은색 배경이 추가되어 색상 깊이에 대한 빠른 시각적 신호를 제공합니다. 이 검은색 배경은 UI에서 마스크할 영역을 나타냅니다.

- **32비트 ICO:** 프로젝트 아이콘 및 항목 추가. 모든 ICO 파일은 알파 채널 투명도(RGB/A)를 가진 32비트 트루 컬러입니다. ICO 파일은 여러 크기와 색상 깊이를 저장할 수 있기 때문에 Vista 아이콘은 종종 16x16, 32x32, 48x48 및 256x256 이미지 크기를 포함하는 ICO 형식으로 표시됩니다. Windows 탐색기에서 제대로 표시하려면 각 이미지 크기에 대해 ICO 파일을 24비트 및 8비트 색상 깊이로 저장해야 합니다.

- **XAML:** 디자인 표면 및 Windows 장식기용. XAML 아이콘은 크기 조정, 회전, 파일 링 및 투명도를 지원하는 벡터 기반 이미지 파일입니다. 오늘날 Visual Studio에서는 흔하지 않지만 유연성 때문에 인기가 높아지고 있습니다.

- **SVG**

- **24비트 BMP:** Visual Studio 명령 모음의 경우. 트루 컬러 RGB 이미지 형식인 24비트 BMP는 마젠타(R=255, G=0, B=255)를 녹아웃 투명도 레이어의 색상 키로 사용하여 투명도 레이어를 만드는 아이콘 규칙입니다. 24비트 BMP에서는 모든 자홍색 표면이 배경색을 사용하여 표시됩니다.

- **24비트 GIF:** Visual Studio 명령 모음의 경우. 투명도를 지원하는 트루 컬러 RGB 이미지 형식입니다. GIF 파일은 마법사 아트웍 및 GIF 애니메이션에 자주 사용됩니다.

### <a name="icon-construction"></a>아이콘 구성
 비주얼 스튜디오에서 가장 작은 아이콘 크기는 16x16입니다. 일반적인 용도에서 가장 큰 것은 32x32입니다. 아이콘을 디자인할 때 전체 16x16, 24x24 또는 32x32 프레임을 채우지 마십시오. 읽기 쉬운 균일 한 아이콘 구조는 사용자 인식에 필수적입니다. 아이콘을 작성할 때 다음 사항을 준수합니다.

- 아이콘은 명확하고 이해하기 가능하며 일관성이 있어야 합니다.

- 상태 알림 요소를 단일 아이콘으로 사용하고 아이콘 기본 요소 위에 쌓지 않는 것이 좋습니다. 특정 컨텍스트에서 UI는 상태 요소를 기본 요소와 페어링해야 할 수 있습니다.

- 프로젝트 아이콘은 일반적으로 여러 크기를 포함하는 .ico 파일입니다. 16x16, 24x24 및 32x32 아이콘만 업데이트됩니다. 대부분의 16x16 및 24x24 아이콘에는 동일한 요소가 포함됩니다. 32x32 아이콘에는 프로젝트 언어 유형(해당하는 경우)을 비롯한 자세한 정보가 포함되어 있습니다.

- 32x32 아이콘의 경우 기본 요소에는 일반적으로 2픽셀 선 가중치가 있습니다. 상세 요소에는 1픽셀 또는 2픽셀 선 가중치를 사용할 수 있습니다. 어떤 것이 더 적합한지 결정하기 위해 최선의 판단을 하십시오.

- 16x16 및 24x24 아이콘의 요소 간에 최소 1픽셀 간격이 있습니다. 32x32 아이콘의 경우 요소 와 수정자와 기본 요소 사이의 2픽셀 간격을 사용합니다.

  ![16x16, 24x24 및 32x32 크기의 아이콘에 대한 요소 간격](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />16x16, 24x24 및 32x32 크기의 아이콘에 대한 요소 간격

#### <a name="color-and-accessibility"></a>색상 및 접근성
 Visual Studio 규정 준수 지침에 따라 제품의 모든 아이콘이 색상 및 대비에 대한 접근성 요구 사항을 통과해야 합니다. 이것은 아이콘 반전을 통해 달성되며, 디자인 할 때, 당신은 그들이 제품에 프로그래밍 방식으로 반전 될 것이라는 점을 알아야한다.

 Visual Studio 아이콘의 색상 사용에 대한 자세한 내용은 [이미지의 색상 사용을](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)참조하십시오.

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>이미지의 색상 사용

### <a name="overview"></a>개요
 비주얼 스튜디오의 아이콘은 주로 단색입니다. 색상은 특정 정보를 전달하고 장식을 위해 예약되지 않습니다. 색상은 다음과 같은 데 사용됩니다.

- 작업을 나타내기 위해

- 을 위해 사용자에게 상태 알림

- 언어 소속을 지정하기 위해

- 인텔리센스 내의 아이템 을 차별화하기 위해

### <a name="accessibility"></a>액세스 가능성
 Visual Studio 규정 준수 지침에서는 제품에 체크 인된 모든 아이콘이 색상 및 대비에 대한 접근성 요구 사항을 통과하도록 요구합니다. 시각적 언어 팔레트의 색상이 테스트되었으며 이러한 요구 사항을 충족합니다.

#### <a name="color-inversion-for-dark-themes"></a>어두운 테마에 대한 색상 반전
 Visual Studio 어두운 테마에서 올바른 명암비로 아이콘을 표시하려면 반전이 프로그래밍 방식으로 적용됩니다. 이 가이드의 색상은 부분적으로 선택되어 올바르게 반전됩니다. 이 팔레트에 색상 사용을 제한하거나 반전이 적용될 때 예기치 않은 결과를 얻을 수 있습니다.

 ![색상이 반전된 아이콘의 예](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />색상이 반전된 아이콘의 예

### <a name="base-palette"></a>베이스 팔레트
 모든 표준 아이콘에는 세 가지 기본 색상이 포함되어 있습니다. 아이콘에는 3D 도구 아이콘에 대해 하나 또는 두 개의 예외가 있는 그라데이션이나 그림자가 포함되어 있지 않습니다.

|사용|이름|값(라이트 테마)|견본|예제|
|-----------|----------|---------------------------|------------|-------------|
|배경/어둡게|VS BG|424242 / 66,66,66|![견본 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![기본 색상표 예](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|전경/라이트|VS FG|F0EFF1 / 240,239,241|![견본 F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|윤곽선|VS 아웃|F6F6F6 / 246,246,246|![견본 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 기본 색상 외에도 각 아이콘에는 확장된 팔레트에서 하나의 추가 색상이 포함될 수 있습니다.

### <a name="extended-palette"></a>확장 팔레트

#### <a name="action-modifiers"></a>작업 수정자
 아래 네 가지 색상은 작업 수정자에 필요한 작업 유형을 나타냅니다.

|사용|이름|값(모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|Positive|VS 액션 그린|388A34 / 56,138,52|![견본 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negative|VS 액션 레드|A1260D / 161,38,13|![견본 A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|무감정|VS 액션 블루|00539C / 0,83,156|![견본 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|만들기/새로 만들기|VS 액션 오렌지|C27D1A / 194,156,26|![견본 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>예
 녹색은 "추가", "실행", "재생", "유효성 검사"와 같은 긍정적인 작업 수정자에 사용됩니다.

|||||
|-|-|-|-|
|![실행 아이콘](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />다음을 실행합니다.|![쿼리 실행 아이콘](../../extensibility/ux-guidelines/media/0405-04_executequery.png "04_ExecuteQuery 0405-04_ExecuteQuery")<br />쿼리 실행|![모든 단계 재생 아이콘](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />모든 단계 재생|![컨트롤 추가 아이콘](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />컨트롤 추가|

 빨간색은 "삭제", "중지", "취소", "닫기"와 같은 부정적인 작업 수정자에 사용됩니다.

|||||
|-|-|-|-|
|![관계 삭제 아이콘](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />관계 삭제|![열 삭제 아이콘](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />열 삭제|![쿼리 중지 아이콘](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />쿼리 중지|![오프라인 연결 상태 아이콘](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />연결 오프라인|

 파란색은 "열기", "다음", "이전", "가져오기" 및 "내보내기"와 같이 가장 일반적으로 화살표로 표시되는 중립 작업 수정자에 적용됩니다.

|||||
|-|-|-|-|
|![필드로 이동 아이콘](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />필드로 이동|![아이콘에 배치된 검사&#45;](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "12_BatchedCheckIn 0405-12_BatchedCheckIn")<br />일괄 체크인|![주소 편집기 아이콘](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />주소 편집기|![연결 편집기 아이콘](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />협회 편집기|

 다크 골드는 주로 "새로운" 수정자에 사용됩니다.

|||||
|-|-|-|-|
|![새 프로젝트 아이콘](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />새 프로젝트|![새 그래프 아이콘 만들기](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />새 그래프 만들기|![새 단위 테스트 아이콘](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />새 단위 테스트|![새 목록 항목 아이콘](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />새 목록 항목|

#### <a name="special-cases"></a>특수 사례
 특별한 경우 컬러 액션 수정자를 독립적으로 독립 실행형 아이콘으로 사용할 수 있습니다. 아이콘에 사용되는 색상은 아이콘이 연관된 작업을 반영합니다. 이 사용은 다음과 같은 작은 아이콘 하위 집합으로 제한됩니다.

||||||
|-|-|-|-|-|
|![실행 아이콘](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />다음을 실행합니다.|![중지 아이콘](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />중지|![삭제 아이콘](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />DELETE|![저장 아이콘](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />저장|![뒤로 탐색 아이콘](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "22_NavigateBack 0405-22_NavigateBack")<br />뒤로 탐색|

### <a name="code-hierarchy-palette"></a>코드 계층 구조 팔레트

#### <a name="folder"></a>폴더

|사용|이름|값(모든 테마)|견본|예제|
|-----------|----------|--------------------------|------------|-------------|
|폴더|폴더|DCB67A / 220,182,122|![견본 DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![폴더 색 아이콘](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>비주얼 스튜디오 언어
 Visual Studio에서 사용할 수 있는 각 공통 언어 또는 플랫폼에는 관련 색상이 있습니다. 이러한 색상은 기본 아이콘 또는 복합 아이콘의 오른쪽 위 모서리에 나타나는 언어 수정자에 사용됩니다.

|사용|이름|값(모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF 블루|0095D7 / 0,149,215|![견본 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP 퍼플|9B4F96 / 155,79,150|![견본 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS 그린(VS 액션 그린)|388A34 / 56,138,52|![견본 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS 레드|BD1E2D / 189,30,45|![견본 BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS 퍼플|672878 / 103,40,120|![견본 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS 오렌지|F16421 / 241,100,33|![견본 F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB 블루 (VS 액션 블루)|00539C / 0,83,156|![견본 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS 오렌지|E04C06 / 224,76,6|![견본 E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY 그린|879636 / 135,150,54|![견본 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>언어 수정자가 있는 아이콘의 예

|||||||
|-|-|-|-|-|-|
|![Visual Basic 아이콘](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![C&#35; 아이콘](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![C&#43;&#43; 아이콘](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![F&#35; 아이콘](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![JavaScript 아이콘](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Python 아이콘](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|
|![HTML 아이콘](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![WPF 아이콘](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![ASP 아이콘](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![CSS 아이콘](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript 아이콘](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense 아이콘은 전용 색상 팔레트를 사용합니다. 이러한 색상은 사용자가 IntelliSense 팝업 목록에서 다른 항목을 빠르게 구분하는 데 사용됩니다.

|사용|이름|값(모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|클래스, 이벤트|VS 액션 오렌지|C27D1A / 194,125,26|![견본 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|확장 방법, 방법, 모듈, 대리자|VS 액션 퍼플|652D90 / 101,45,144|![견본 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|필드, 열거형 항목, 매크로, 구조, 유니온 값 유형, 연산자, 인터페이스|VS 액션 블루|00539C / 0,83,156|![견본 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS 액션 그린|388A34 / 56,138,52|![견본 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|상수, 예외, 열거형 항목, 맵, 맵 항목, 네임스페이스, 템플릿, 유형 정의|배경(VS BG)|424242 / 66,66,66|![견본 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>인텔리센스 아이콘의 예

||||||
|-|-|-|-|-|
|![IntelliSense 클래스 아이콘](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />클래스|![IntelliSense Private 이벤트 아이콘](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />비공개 이벤트|![IntelliSense 대리자 아이콘](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />대리자(delegate)|![IntelliSense 메서드 친구 아이콘](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />메소드 친구|![필드 아이콘](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />필드|
|![IntelliSense 보호된 열거형 항목 아이콘](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />보호된 열거형 항목|![intellisense 개체 아이콘](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "42_IntelliSenseObject 0405-42_IntelliSenseObject")<br />Object|![IntelliSense 템플릿 아이콘](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />템플릿|![IntelliSense 예외 바로 가기 아이콘](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />예외 바로 가기||

### <a name="notifications"></a>알림
 Visual Studio의 알림은 상태를 나타내는 데 사용됩니다. 알림 팔레트는 다음과 같은 네 가지 색상과 검은색 또는 흰색 전경 채우기 옵션을 사용하여 다음과 같은 상태 수준으로 알림을 정의합니다.

|사용|이름|값(모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|상태: 중립|알림 파란색(VS 파란색)|1BA1E2 / 27,161,226|![견본 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|상태: 양수|알림 녹색(VS 녹색)|339933 / 51,153,51|![견본 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|상태: 음수|알림 빨간색(VS 빨간색)|E51400 / 229,20,0|![견본 E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|상태: 경고|알림 노란색(VS 주황색)|FFCC00 / 255,204,0|![견본 FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|전경 채우기|알림 블랙(블랙)|000000 / 0,0,0|![스와시 &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|전경 채우기|알림 흰색(흰색)|FFFF / 255,255,255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>알림 아이콘의 예

|||||
|-|-|-|-|
|![경고 아이콘](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />경고|![경고 아이콘](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />Warning|![완료 아이콘](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />완료|![중지 아이콘](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />중지|

### <a name="visual-studio-online"></a>Visual Studio Online
 일반적으로 Visual Studio Online은 브라우저에서 호스팅되는 기능으로 구성됩니다. 색상은 환경에 따라 다르지만 스타일은 동일하게 유지됩니다.

|그룹|사용|이름|값(모든 테마)|견본|
|-----------|-----------|----------|--------------------------|------------|
|TFS|배경|TFSO BG|656565/ 101, 101, 101|![견본 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|윤곽선|TFSO 아웃|FFFFFF / 255, 255, 255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|나파|배경|흰색|FFFFFF / 255, 255, 255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|모나코|배경|흰색|FFFFFF / 255, 255, 255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|배경|흰색|FFFFFF / 255, 255, 255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|정상|F12 Grey_Primary|555555 / 85, 85, 85|![견본 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|가리키기|F12 Blue_Hover|2279BF / 34,121,191|![견본 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|사용 안 함|F12 LtGrey_Disabled|ABABAC / 171,171,172|![견본 ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|배경 가리키기|호버 bg|D9EBF7 / 217,235,247|![견본 D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|압축된 배경|누른 bg|B2D7F0 / 178,215,240|![견본 B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|윤곽선|대|F6F6F6 / 246,246,246|![견본 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|정보|정보|00BCF2 / 0,188,242|![견본 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Warning|Warning|F28300 / 242,131,0|![견본 F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|오류 / 음수|Error_Negative|E81123 / 232,17,35|![견본 E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|시작 / 양수|Start_Positive|009E49 / 0,158,73|![견본 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|브레이크 타입|브레이크 타입|9B4F96 / 155,79,150|![견본 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|이벤트 마크|이벤트 마크|A51F00 / 165,31,0|![견본 A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|사용자 마크|사용자 마크|F16220 / 241,98,32|![견본 F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>비주얼 스튜디오 온라인 아이콘의 예

|TFS 온라인||||
|----------------|-|-|-|
|![TFS 온라인 팀 아이콘](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam")<br />온라인 팀|![TFS 정보 아이콘](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation")<br />정보|![TFS 기록 아이콘](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />기록|![TFS 분기 아이콘](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch")<br />Branch|

|나파||||
|----------|-|-|-|
|![Napa 콘텐츠 아이콘](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />콘텐츠|![Napa Office 메일 아이콘](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail")<br />오피스 메일|![Napa SharePoint 아이콘](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint")<br />SharePoint|![Napa 작업 창 아이콘](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane")<br />작업창|

|모나코||||
|------------|-|-|-|
|![Monaco 파일 아이콘](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles")<br />파일|![Monaco Git 아이콘](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit")<br />Git|![Monaco 검색 아이콘](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch")<br />검색|![Monaco 텍스트 아이콘](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText")<br />텍스트|

|F12|||
|---------|-|-|
|![F12 깔끔한 코드 아이콘](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode")<br />예쁜 코드|![F12 경고 아이콘](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning")<br />Warning|![F12 에뮬레이션 아이콘](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate")<br />에뮬레이트|
