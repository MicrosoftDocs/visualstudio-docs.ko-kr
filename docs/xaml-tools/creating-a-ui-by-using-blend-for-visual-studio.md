---
title: Blend for Visual Studio 기능 둘러보기
titleSuffix: ''
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8348ba38849b76a745a56f941850d6b61a8f433f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85332091"
---
# <a name="blend-for-visual-studio-overview"></a>Blend for Visual Studio 개요

Blend for Visual Studio를 사용하면 XAML 기반 Windows 및 웹 애플리케이션을 디자인할 수 있습니다. Visual Studio와 같은 기본 XAML 디자인 환경을 제공하고, 애니메이션 및 동작과 같은 고급 작업에 대한 비주얼 디자이너를 추가합니다. Blend 및 Visual Studio 비교를 보려면 [Visual Studio 및 Blend for Visual Studio에서 XAML 디자인](../xaml-tools/designing-xaml-in-visual-studio.md)을 참조하세요.

Blend for Visual Studio는 Visual Studio의 구성 요소입니다. Blend를 설치하려면 **Visual Studio 설치 관리자**에서 **유니버설 Windows 플랫폼 개발** 또는 **.NET 데스크톱 개발** 워크로드를 선택합니다. 이러한 워크로드에는 둘 다 Blend for Visual Studio 구성 요소가 포함됩니다.

![UWP 워크로드 구성 요소](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![.NET 데스크톱 개발 워크로드 구성 요소](media/installer-dotnet-desktop.png)

Blend for Visual Studio를 처음 접하는 경우 시간을 두고 작업 영역의 고유 기능을 익히세요. 이 항목에 이러한 작업 영역이 간단히 설명되어 있습니다.

## <a name="tools-panel"></a>도구 패널

Blend for Visual Studio에서 **도구** 패널을 사용하여 애플리케이션의 개체를 만들고 수정할 수 있습니다. *.xaml* 파일이 열려 있을 때 **도구** 패널이 XAML 디자이너의 왼쪽에 표시됩니다.

도구를 선택한 다음 마우스로 아트보드에 그려 개체를 만들 수 있습니다.

![Blend for Visual Studio의 도구 패널](media/blend-tools-panel.png)

> [!TIP]
> **도구** 패널의 일부 도구에는 사각형이 아닌 변형이 있습니다. 예를 들어 타원이나 선을 선택할 수 있습니다. 이러한 변형에 액세스하려면 도구를 마우스 오른쪽 단추로 클릭하거나 누른 상태를 유지합니다.
>
> ![Blend for Visual Studio의 도형 도구 변형](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>선택 도구

개체 및 패스를 선택합니다. **직접 선택** 도구는 중첩된 개체 및 패스 세그먼트를 선택하는 데 사용합니다.

### <a name="view-tools"></a>뷰 도구

이동, 확대/축소 등 아트보드의 뷰를 조정합니다.

### <a name="brush-tools"></a>브러시 도구

브러시 변형, 그라데이션 적용 등 개체의 시각적 특성으로 작업합니다.

### <a name="object-tools"></a>개체 도구

아트보드에서 패스, 도형, 레이아웃 패널, 텍스트, 컨트롤 등 가장 일반적으로 사용되는 개체를 그리는 데 사용합니다.

### <a name="asset-tools"></a>자산 도구

자산 창에 액세스하고 라이브러리에서 가장 최근에 사용된 자산을 표시하는 데 사용합니다.

## <a name="assets-window"></a>자산 창

**자산** 창에는 사용 가능한 모든 컨트롤이 포함되어 있으며 Visual Studio의 **도구 상자**와 유사합니다. 컨트롤 외에도, 스타일, 미디어, 동작, 효과 등 무엇이든 **자산** 창의 아트보드에 추가할 수 있습니다. **자산** 창을 열려면 **보기** > **자산 창**을 선택하거나 **Ctrl**+**Alt**+**X**를 누릅니다.

![Blend for Visual Studio의 자산 창](media/blend-assets-window.png)

- **자산 검색** 상자에 텍스트를 입력하여 자산 목록을 필터링합니다.
- 오른쪽 위에 있는 단추를 사용하여 자산의 Grid 모드와 List 모드 뷰 보기 간에 전환합니다.

## <a name="objects-and-timeline-window"></a>개체 및 타임라인 창

이 창에서는 아트보드에서 개체를 구성하고 원하는 경우 개체에 애니메이션 효과를 적용할 수 있습니다. **개체 및 타임라인** 창을 열려면 **보기** > **문서 개요**를 선택합니다. Visual Studio의 [문서 개요 창](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window)에 제공된 기능 외에도 Blend for Visual Studio의 개체 및 타임라인 창의 오른쪽에는 타임라인 컴퍼지션 영역이 있습니다. 애니메이션을 만들고 편집할 때 타임라인을 사용합니다.

![애니메이션 모드의 개체 및 타임라인 창](media/storyboard-timeline.png)

스토리보드 관련 단추 사용 ![Blend for Visual Studio의 스토리보드 단추](media/storyboard-buttons.png) 스토리보드를 만들거나 삭제하거나 닫거나 선택합니다. 오른쪽의 타임라인 컴퍼지션 영역을 사용하여 타임라인을 확인하고 키 프레임을 이동합니다.

사용 가능한 기능에 대한 자세한 내용을 보려면 창의 각 단추를 마우스로 가리킵니다.

## <a name="see-also"></a>추가 정보

- [개체에 애니메이션 적용](../xaml-tools/animate-objects-in-xaml-designer.md)
- [도형 및 패스 그리기](../xaml-tools/draw-shapes-and-paths.md)
- [Visual Studio 및 Blend for Visual Studio에서 XAML 디자인](../xaml-tools/designing-xaml-in-visual-studio.md)
