---
title: Blend를 사용하여 UI 만들기
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a65f42dafca696bfa638964b825410b576d4845
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544289"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Blend for Visual Studio를 사용하여 UI 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Blend for Visual Studio를 사용하면 XAML 기반 Windows 데스크톱, 웹, [Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx) 및 [Windows 스토어](https://msdn.microsoft.com/library/windows/apps/jj129478.aspx) 앱을 디자인할 수 있습니다. Visual Studio와 같은 기본 XAML 디자인 환경을 제공하고, 애니메이션 및 동작과 같은 고급 작업에 대한 비주얼 디자이너를 추가합니다.

 Blend for Visual Studio는 Visual Studio의 일부로 포함되어 있으므로 다운로드할 필요가 없습니다. 그러나 시스템에 설치하려면 Visual Studio 설치 관리자에서 직접 선택해야 합니다.

 Blend for Visual Studio를 처음 접하는 경우 시간을 두고 작업 영역의 고유 기능을 익히세요. 이 항목에 이러한 작업 영역이 간단히 설명되어 있습니다.

> [!NOTE]
> 아트보드, 문서 개요 창 및 디바이스 창과 같은 공유 디자인 기능을 둘러보려면 [XAML 디자이너를 사용하여 UI 만들기](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)를 참조하세요.

 **항목**내용

- [도구 패널 둘러보기](#Tools)

- [자산 패널 둘러보기](#Assets)

- [개체 및 타임라인 패널 둘러보기](#Objects)

- [속성 패널 둘러보기](#Properties)

## <a name="tour-of-the-tools-panel"></a><a name="Tools"></a> 도구 패널 둘러보기
 Blend for Visual Studio에서 **도구** 패널을 사용하여 애플리케이션의 개체를 만들고 수정할 수 있습니다. 도구를 선택한 다음 마우스로 아트보드에 그려 개체를 만들 수 있습니다.

 ![도구 패널](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|이미지|도구 형식|이미지|도구 형식|
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|**선택 도구** 개체 및 패스를 선택합니다.<br /><br /> **직접 선택** 도구는 중첩된 개체 및 패스 세그먼트를 선택하는 데 사용합니다.|![설명선 A](../designers/media/b5-label-a.png "b5_label_A")|**그라데이션 및 브러시 도구**|
|![](../designers/media/b1-2.png "B1_2")|**뷰 도구** 이동, 확대/축소 등 아트보드의 뷰를 조정합니다.|![설명선 B](../designers/media/b5-label-b.png "b5_label_B")|**패스 도구**|
|![](../designers/media/b1-3.png "B1_3")|**브러시 도구** 브러시를 변형하거나, 개체를 칠하거나, 한 개체의 특성을 선택하여 다른 개체에 적용하는 등 개체의 시각적 특성에 대한 작업에 사용됩니다.|![설명선 C](../designers/media/b5-label-c.png "b5_label_C")|**도형 도구**|
|![](../designers/media/b1-4.png "B1_4")|**개체 도구** 아트보드에서 패스, 도형, 레이아웃 패널, 텍스트, 컨트롤 등 가장 일반적으로 사용되는 개체를 그리는 데 사용합니다.|![설명선 D](../designers/media/b5-label-d.png "b5_label_D")|**레이아웃 패널**|
|![](../designers/media/b1-5.png "B1_5")|**자산 도구****자산** 패널에 액세스하고 라이브러리에서 가장 최근에 사용된 자산을 표시하는 데 사용합니다.|![설명선 E](../designers/media/b5-label-e.png "b5_label_E")|**텍스트 컨트롤**|
|||![설명선 F](../designers/media/b5-label-f.png "b5_label_F")|**공용 컨트롤**|

 **짧은 동영상 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [도구 모음](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a><a name="Assets"></a> 자산 패널 둘러보기
 Visual Studio의 **도구 상자**와 비슷한 **자산** 패널에서 모든 컨트롤을 찾을 수 있습니다. 컨트롤 외에도, 스타일, 미디어, 동작 및 효과를 포함 하 여 **자산** 패널에서 아트 보드에 추가할 수 있는 모든 항목을 찾을 수 있습니다.

 ![자산 패널](../designers/media/blend5-assets-panel.png "Blend5_Assets_panel")

|이미지|설명|
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**검색 상자****검색** 상자에 입력하여 자산 목록을 필터링합니다.|
|![](../designers/media/b1-2.png "B1_2")|**표 모드 및 목록 모드** 자산의 **표 모드** 보기와 **목록 모드** 보기 간에 전환합니다.|
|![](../designers/media/b1-3.png "B1_3")|**자산 범주** 해당 범주의 자산 목록을 보려면 범주 또는 하위 범주를 클릭합니다.|
|![](../designers/media/b1-4.png "B1_4")|**스타일** 리소스 사전에 포함된 모든 스타일을 표시합니다.|
|![](../designers/media/b1-5.png "B1_5")|**설명** 선택한 자산 범주 또는 하위 범주에 대한 설명을 표시합니다.|

## <a name="tour-of-the-objects-and-timeline-panel"></a><a name="Objects"></a>개체 및 타임라인 패널 둘러보기
 이 패널에서는 아트보드에서 개체를 구성하고 원하는 경우 개체에 애니메이션 효과를 적용할 수 있습니다.

 ![애니메이션 모드의 개체 및 타임라인 패널](../designers/media/b5-object-timeline-animation.png "b5_object_timeline_animation")

|이미지|설명|
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**개체 뷰** 문서의 시각적 트리를 표시합니다. 다양한 세부 수준으로 드릴다운할 수 있습니다. 레이어를 추가하여 아트보드의 개체를 자세히 구성하고 하나의 그룹으로 잠그거나 숨길 수 있습니다.|
|![](../designers/media/b1-2.png "B1_2")|**레코드 모드 표시기** 타임 라인에 속성 변경을 기록 하 고 있는지 여부를 확인 합니다.|
|![](../designers/media/b1-3.png "B1_3")|**스토리 보드 선택기** 만든 스토리 보드 목록을 표시 합니다.|
|![](../designers/media/b1-4.png "B1_4")|**스토리보드 닫기** 현재 스토리보드를 닫습니다.|
|![](../designers/media/b1-5.png "B1_5")|**스토리보드 옵션** 스토리보드의 만들기, 복제, 반전, 삭제, 이름 바꾸기 또는 닫기 작업을 수행합니다.|
|![](../designers/media/b1-6.png "B1_6")|**재생 컨트롤** 타임라인을 탐색합니다. 플레이헤드를 끌어 타임라인 전체로 이동(*스크럽*)할 수도 있습니다.|
|![](../designers/media/b1-7.png "B1_7")|**범위 되돌리기** 이전 루트 개체 또는 이전 범위로 개체 뷰를 되돌립니다. 이 작업은 스타일이나 템플릿을 수정할 때만 가능합니다.|
|![](../designers/media/b1-8.png "B1_8")|**키 프레임 기록** 현재 시점에서 선택한 개체의 속성에 대한 스냅샷을 기록합니다.|
|![](../designers/media/b1-9.png "B1_9")|**맞추기 옵션** 타임라인 맞추기 및 맞춤 해상도를 설정하고 타임라인 맞추기를 해제합니다.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**표시/숨기기**, **잠금/잠금 해제** 개체 뷰의 표시 유형 및 잠금 옵션을 표시하거나 숨깁니다.|
|![](../designers/media/b1-11.png "B1_11")|**타임라인의 플레이헤드 위치** 현재 시간을 밀리초 단위로 표시합니다. 이 필드에 직접 시간 값을 입력하여 특정 시점으로 이동할 수도 있습니다. **맞추기 옵션**에서 설정한 맞춤 해상도에 따라 정밀도가 달라집니다.|
|![](../designers/media/b1-12.png "B1_12")|**플레이헤드** 애니메이션이 있는 시점을 나타냅니다. 타임라인에서 플레이헤드를 끌어 애니메이션을 미리 볼 수 있습니다.|
|![](../designers/media/b1-13.png "B1_13")|**타임라인의 키 프레임 설정** 특정 시점에서의 속성 값을 변경합니다.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**개체의 순서 변경** 개체의 표시 순서를 설정합니다. 이 단추를 클릭하여 구조 뷰에서 Z 순서(앞에서 뒤로) 또는 태그 순서(**XAML** 뷰에 나타나는 순서)로 개체를 정렬할 수 있습니다.|
|![](../designers/media/b1-15.png "B1_15")|**타임라인 확대/축소** 타임라인의 확대/축소 해상도를 설정합니다. 확대하면 애니메이션을 좀 더 자세하게 편집할 수 있고 축소하면 더 긴 시간 동안 발생하는 동작이 좀 더 간략하게 표시됩니다. 확대했지만 원하는 시점에 키 프레임을 설정할 수 없다면 맞춤 해상도가 충분히 높게 설정되어 있는지 확인하십시오.|
|![설명선 16](../designers/media/b5-label-16.png "b5_label_16")|**타임라인 합성 영역** 타임라인이 표시됩니다. 키 프레임을 직접 끌거나 바로 가기 메뉴를 사용하여 이동할 수 있습니다.|

## <a name="tour-of-the-properties-panel"></a><a name="Properties"></a>속성 패널 둘러보기
 이 패널에서는 개체의 속성을 보고 수정할 수 있으며, 아트보드에서 직접 수정하도록 설정할 수도 있습니다. 이렇게 하면 속성 변경 내용이 **속성** 패널에 반영됩니다.

 ![속성 패널](../designers/media/blend5-properties-panel.png "Blend5_properties_panel")

 **범주** 속성의 범주를 확장하고 축소합니다. 범주 세부 정보를 표시하거나 숨기려면 **확장** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") 및 **축소** ![축소](../designers/media/b5-collapse-button.png "b5_collapse_button")를 클릭합니다.

|                                                                                                         |                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                 ![](../designers/media/b1-1.png "B1_1")                                 |                                                                              **이름 및 형식** 선택한 개체의 아이콘, 이름 및 형식을 표시합니다.                                                                              |
|                                 ![](../designers/media/b1-2.png "B1_2")                                 |                                                                          **정렬 기준** 속성을 이름, 소스 또는 범주를 기준으로 사전순으로 정렬합니다.                                                                          |
|                                 ![](../designers/media/b1-3.png "B1_3")                                 |                                                        **브러시 속성** Fill 브러시, Stroke 브러시 및 Foreground 브러시와 같은 브러시의 시각적 속성을 설정합니다.                                                        |
|                                 ![](../designers/media/b1-4.png "B1_4")                                 |                                                                                    **색 편집기** 단색 및 그라데이션 브러시에 사용합니다.                                                                                    |
|                                 ![](../designers/media/b1-5.png "B1_5")                                 |                                                                                                 **색 선택** 색을 선택합니다.                                                                                                 |
|                                 ![](../designers/media/b1-6.png "B1_6")                                 |                                                                              **색 칩** 첫 색, 현재 색 및 끝 색을 표시합니다.                                                                               |
|                                 ![](../designers/media/b1-7.png "B1_7")                                 | **스포이트** 화면에 모든 요소의 색을 사용합니다. **색 스포이트**는 **단색 브러시**가 선택되어 있을 때 사용할 수 있습니다. **그라데이션 스포이트**는 **그라데이션 브러시**가 선택되어 있을 때 사용할 수 있습니다. |
|                                 ![](../designers/media/b1-8.png "B1_8")                                 |                                                                        **속성 및 이벤트** 선택한 요소에 대한 이벤트를 선택하거나 속성을 설정합니다.                                                                         |
|                                 ![](../designers/media/b1-9.png "B1_9")                                 |                                                         **검색 상자** 속성을 검색합니다. **검색** 상자에 텍스트를 입력하여 표시되는 속성을 필터링합니다.                                                          |
| ![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209") |                                **브러시 편집기 탭** 브러시 편집기를 선택하는 데 사용합니다. **브러시 없음**, **단색 브러시**, **그라데이션 브러시**, **타일 브러시** 또는 **브러시 리소스** 중에서 선택할 수 있습니다.                                |
|                                ![](../designers/media/b1-11.png "B1_11")                                |                                    **색 리소스** 서로 다른 속성에 동일한 색을 적용합니다. **색 리소스** 탭에는 **로컬 리소스** 및 **시스템 리소스**가 포함됩니다.                                    |
|                                ![](../designers/media/b1-12.png "B1_12")                                |                                                 **RGB 색 공간****R**, **G** 또는 **B**(빨강, 초록, 파랑) 숫자 편집기에 대한 값을 조정하여 색을 수정합니다.                                                  |
|                                ![](../designers/media/b1-13.png "B1_13")                                |                                                                        **알파 채널****A** 옆의 숫자 편집기를 사용하여 알파 값을 수정합니다.                                                                        |
| ![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe") |                                       **색을 리소스로 변환** 선택한 색을 색 리소스로 변환합니다. 색 리소스는 색 리소스 탭을 클릭하면 사용할 수 있습니다.                                        |
|                                ![](../designers/media/b1-15.png "B1_15")                                |                                                                                 **16진수 값** 표시된 색의 16진수 값을 표시합니다.                                                                                 |
|                     ![설명선 16](../designers/media/b5-label-16.png "b5_label_16")                     |                                                                                **그라데이션 슬라이더** 그라데이션 브러시를 선택한 경우에만 나타납니다.                                                                                 |
| ![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8") |                                                                     **고급 속성 표시** 자주 사용되지 않는 속성의 범주를 표시합니다.                                                                      |

 **짧은 동영상 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [속성 패널](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>참고 항목
 [컨트롤을 삽입 하 고 해당 동작을 수정](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md) 합니다. [개체](../designers/animate-objects-in-xaml-designer.md) [그리기 도형 및 패스 그리기](../designers/draw-shapes-and-paths.md) [Visual Studio에서 XAML 디자인 및 Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)
