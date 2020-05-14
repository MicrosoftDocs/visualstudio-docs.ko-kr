---
title: XAML 디자이너에서 개체를 레이아웃 컨테이너로 구성
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 3f05874459553b0b83c5e43f326a5deb6b0d4798
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "82921108"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>XAML 디자이너에서 개체를 레이아웃 컨테이너로 구성

이 문서에서는 XAML 디자이너에 대한 레이아웃 패널과 컨트롤을 설명합니다.

페이지에 개체를 표시할 위치를 가정해 보겠습니다. &mdash;개체로는 이미지, 단추, 비디오 등을 들 수 있습니다. 개체를 행 및 열로 표시하거나 가로나 세로로 한 줄로 표시하거나 고정된 위치에 표시할 수 있습니다.

페이지에 어떻게 표시할지 결정했으면 레이아웃 패널을 선택합니다. 개체를 추가할 대상이 필요하기 때문에 모든 페이지 작업은 여기에서 시작됩니다. 기본적으로 **Grid**가 설정되지만 변경할 수 있습니다.

레이아웃 패널은 페이지에 개체를 정렬하는 데 도움이 될 뿐만 아니라 그 이상의 역할을 합니다. 서로 다른 화면 크기 및 해상도를 설계하는 데에도 도움이 됩니다. 사용자가 앱을 실행할 때 레이아웃 패널의 모든 항목은 디바이스의 실제 화면 공간에 맞게 크기가 조정됩니다. 자동으로 크기가 조정되지 않도록 하려면 레이아웃 일부 또는 전체 레이아웃에 대해 이러한 동작을 재정의할 수 있습니다. 이러한 동작은 높이 및 너비 속성을 사용하여 제어할 수 있습니다.

## <a name="layout-panels"></a>레이아웃 패널

다음 레이아웃 패널 중 하나를 선택하여 페이지를 시작합니다. 페이지에 둘 이상의 레이아웃 패널을 지정할 수 있습니다. 예를 들어 **Grid** 레이아웃 패널에서 시작한 후 **Grid**의 영역에 **StackPanel**을 추가하여 해당 요소에서 컨트롤을 세로로 정렬할 수 있습니다.

다음은 가장 많이 사용되는 레이아웃 패널이며, 다른 레이아웃 패널도 있습니다. 이 모든 항목은 Visual Studio의 **도구 상자** 또는 Blend for Visual Studio의 **자산** 패널에서 확인할 수 있습니다.

### <a name="grid"></a>표

개체를 행 및 열로 정렬합니다.

![표 레이아웃 패널](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

개체를 동일하게 또는 균일하게 모눈 영역에 정렬합니다. 이 패널은 이미지의 목록을 정렬할 때 매우 유용 합니다.

(WPF 프로젝트에만 사용 가능)

![UniformGrid 레이아웃 패널](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

### <a name="canvas"></a>Canvas

원하는 방식으로 개체를 정렬합니다. 사용자가 앱을 실행할 때 이러한 요소는 화면에서 고정 위치에 표시됩니다.

![Canvas 레이아웃 패널](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

개체를 가로 또는 세로로 한 줄로 정렬합니다.

![StackPanel 레이아웃 패널](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

개체를 순서대로 왼쪽에서 오른쪽으로 정렬합니다. 패널의 맨 오른쪽 가장자리에 공간이 부족한 경우 콘텐츠를 다음 줄로 *줄바꿈*하며 왼쪽에서 오른쪽, 위쪽에서 아래쪽 가로로 배치됩니다. 위쪽에서 아래쪽, 왼쪽에서 오른쪽 세로로 배치할 수도 있습니다.

(WPF 프로젝트에만 사용 가능)

![WrapPanel 레이아웃 패널](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

개체가 패널의 한쪽 가장자리에 *고정*되도록 개체를 정렬합니다.

(WPF 프로젝트에만 사용 가능)

![DockPanel 레이아웃 패널](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**짧은 비디오 보기:** ![재생 단추](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>레이아웃 컨트롤

개체를 레이아웃 컨트롤에도 추가할 수 있습니다. 이러한 개체는 레이아웃 패널만큼 기능이 다양하지는 않지만 특정 시나리오에서 유용할 수 있습니다.

다음은 가장 많이 사용되는 레이아웃 컨트롤이며, 다른 레이아웃 컨트롤도 있습니다. 이 모든 항목은 Visual Studio의 **도구 상자** 또는 Blend for Visual Studio의 **자산** 패널에서 확인할 수 있습니다.

### <a name="border"></a>테두리

개체 주위에 테두리, 배경 또는 둘 다를 그립니다. **Border**에는 개체를 하나만 추가할 수 있습니다. 둘 이상의 개체에 테두리나 배경을 적용하려면 레이아웃 패널을 **Border**에 추가합니다. 그런 다음 해당 패널 또는 컨트롤에 개체를 추가합니다.

![Border 레이아웃 컨트롤](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Popup

창의 사용자에게 정보나 옵션을 표시합니다. **Popup**에 개체를 하나만 추가할 수 있습니다. 기본적으로 **Popup**에는 **Grid**가 포함되지만 변경할 수 있습니다.

### <a name="scrollviewer"></a>ScrollViewer

사용자가 페이지나 페이지의 특정 영역을 스크롤할 수 있습니다. **ScrollViewer**에 개체를 하나만 추가할 수 있으므로 **Grid** 또는 **StackPanel** 등과 같은 레이아웃 패널을 추가합니다.

![ScrollViewer 레이아웃 컨트롤](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

확대/축소 컨트롤과 유사하게 개체의 비율 크기를 조정합니다. **Viewbox**에 하나의 개체만 추가할 수 있습니다. 둘 이상의 개체에 해당 효과를 적용하려면 레이아웃 패널을 **ViewBox**에 추가한 후 컨트롤을 해당 레이아웃 패널에 추가합니다.

(WPF 프로젝트에만 사용 가능)

![ViewBox 레이아웃 컨트롤](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>참고 항목

- [XAML 디자이너의 요소 작업](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [XAML 디자이너를 사용하여 UI 만들기](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
