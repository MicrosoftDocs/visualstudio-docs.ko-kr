---
title: R을 사용하여 코드 시각화
description: 플롯 창을 사용하여 Visual Studio의 R 프로그램에서 데이터를 그리는 방법입니다.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: a48ad7800f8ea2b992e848cfbf6b4fdac99b2062
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62811190"
---
# <a name="create-visual-data-plots-with-r"></a>R을 사용하여 시각적 데이터 플롯 만들기

그리기는 데이터 과학자 워크플로의 주요 부분입니다. RTVS(Visual Studio용 R 도구)에서 모든 그리기 작업은 이 주요 작업을 통해 생산성을 향상하도록 디자인된 하나 이상의 플롯 창을 중심으로 수행됩니다.

![영웅 이미지 그리기](media/plotting-hero-image.png)

|   |   |
|---|---|
| ![동영상에 대한 비디오 카메라 아이콘](../install/media/video-icon.png "비디오 보기") | R을 사용한 그리기에 대한 [동영상(youtube.com)을 시청](https://www.youtube.com/watch?v=ZTbKmz5RSgY)하세요(2분 02초). |

## <a name="the-plot-window"></a>플롯 창

플롯 창에는 일련의 플롯이 포함됩니다. 여기서 각 플롯은 `plot` 명령으로 생성됩니다. 예를 들어 `plot(1:100)`를 사용하면 새 플롯 창이 만들어집니다(없는 경우).

![1:100 선형 플롯](media/plotting-1-to-100.png)

기술적으로 말하면 R `plot` 명령은 R 그래픽 디바이스에 대한 출력을 렌더링하고, 플롯 창에서는 R 그래픽 디바이스의 콘텐츠를 렌더링합니다. 이런 이유로 각 플롯 창에는 디바이스 번호가 지정됩니다.

플롯 창은 Visual Studio 프로젝트에 독립적이고 프로젝트를 열고 닫을 때 열려 있습니다.

플롯 생성 시 모든 이전 플롯을 플롯 기록에 저장하는 “활성” 플롯 창이 사용됩니다([플롯 기록](#plot-history) 참조). 예를 들어 `plot(100:1)`을 입력하면 첫 번째 플롯이 아래쪽 방향 선으로 바뀝니다.

모든 기타 Visual Studio 창처럼 플롯 창에서는 사용자 지정 레이아웃을 지원합니다([Visual Studio에서 창 레이아웃 사용자 지정](../ide/customizing-window-layouts-in-visual-studio.md) 참조). 플롯 창은 Visual Studio 프레임 내의 여러 위치에 고정되거나, 해당 프레임 내에서 크기가 조정되거나, 독립적인 크기 조정을 위해 프레임에서 완전히 분리됩니다.

플롯 창의 크기를 조정하면 항상 플롯이 다시 렌더링되어 최고 품질의 이미지를 제공합니다. 일반적으로 다음 섹션에 설명된 명령을 사용하여 플롯을 파일 또는 클립보드로 내보내기 전에 플롯 크기를 조정하는 것이 좋습니다.

## <a name="plot-window-commands"></a>플롯 창 명령

플롯 창의 도구 모음에는 적용 가능한 명령이 포함되고 이러한 명령은 대부분 **R 도구** > **플롯** 메뉴를 통해서도 사용할 수 있습니다.

| 단추 | 명령 | Description |
| --- | --- | --- |
| ![새 플롯 창 단추](media/plotting-toolbar-01-new-plot-window.png) | 새 플롯 창 | 자체 기록이 포함된 별도의 플롯 창을 만듭니다. [여러 플롯 창](#multiple-plot-windows)을 참조하세요. |
| ![플롯 창 활성화 단추](media/plotting-toolbar-02-activate-plot-window.png) | 플롯 창 활성화 | 현재 플롯 창을 활성 창으로 설정하므로 후속 `plot` 명령은 해당 창으로 렌더링됩니다. [여러 플롯 창](#multiple-plot-windows)을 참조하세요. [여러 플롯 창](#multiple-plot-windows)을 참조하세요. |
| ![플롯 기록 창 단추](media/plotting-toolbar-03-plot-history.png) | 플롯 기록 창 | 기록의 모든 플롯이 미리 보기로 표시되는 창을 엽니다. [플롯 기록](#plot-history)을 참조하세요. |
| ![플롯 기록 단추](media/plotting-toolbar-04-plot-history-arrows.png) | 이전/다음 플롯 |  기록에서 이전 또는 다음 플롯으로 이동합니다. Ctrl+Alt+F11(이전) 및 Ctrl+Alt+F12(다음)를 사용하여 기록을 탐색할 수도 있습니다. [플롯 기록](#plot-history)을 참조하세요. |
| ![이미지로 저장 단추](media/plotting-toolbar-05-save-as-image.png)| 이미지로 저장 | 파일 이름을 입력하라는 메시지를 표시하고 현재 플롯(창 콘텐츠, 창 크기)을 이미지 파일에 저장합니다. 사용 가능한 형식은 `.png`, `.jpg`, `.bmp` 및 `.tif`입니다. |
| ![PDF로 저장 단추](media/plotting-toolbar-06-save-as-pdf.png)| PDF로 저장 | 현재 창 크기를 사용하여 현재 플롯을 PDF 파일로 저장합니다. PDF 크기를 조정하면 플롯이 다시 렌더링됩니다. |
| ![비트맵으로 복사 단추](media/plotting-toolbar-07-copy-as-bitmap.png)| 비트맵으로 복사 | 현재 창 크기를 사용하여 플롯을 클립보드에 래스터 비트맵으로 복사합니다. |
| ![메타파일로 복사 단추](media/plotting-toolbar-08-copy-as-metafile.png)| 메타파일로 복사 | 플롯을 클립보드에 [Windows 메타파일](https://en.wikipedia.org/wiki/Windows_Metafile)(Wikipedia)로 복사합니다. |
| ![플롯 제거 단추](media/plotting-toolbar-09-remove-plot.png)| 플롯 제거 | 기록에서 현재 플롯을 제거합니다. |
| ![모든 플롯 지우기 단추](media/plotting-toolbar-10-clear-all-plots.png) | 모든 플롯 지우기 | 기록에서 모든 플롯을 제거합니다(확인 메시지 표시). |

## <a name="multiple-plot-windows"></a>여러 플롯 창

데이터 과학자는 보통 다양한 데이터 세트의 많은 플롯을 사용하므로 RTVS를 통해 해당 개수만큼 독립적인 플롯 창을 만들 수 있습니다. 그런 다음 Visual Studio 프레임 내부 또는 해당 프레임 외부에서 이러한 창을 원하는 대로 정렬할 수 있습니다. 창 고정 및 크기 조정에 대한 일반적인 내용은 [Visual Studio에서 창 레이아웃 사용자 지정](../ide/customizing-window-layouts-in-visual-studio.md)을 참조하세요.

도구 모음 단추 또는 **R 도구** > **플롯** > **새 플롯 창**을 사용하여 새 플롯 창을 만듭니다. 새 플롯 창은 새 플롯*활성* 창이 되며, 여기서 새 플롯이 렌더링됩니다. 활성 창을 변경하려면 해당 창으로 전환하고 **플롯 창 활성화** 도구 모음 단추 또는 **R 도구** > **플롯** > **플롯 창 활성화**를 선택합니다.

플롯도 독립적인 개체입니다. 따라서 마우스로 끌어서 놓기를 사용하거나 마우스 오른쪽 클릭 상황에 맞는 메뉴 및 **편집** 메뉴의 **복사**, **잘라내기**, **붙여넣기** 명령을 사용하여 플롯을 복사하거나 이동할 수 있습니다.

끌어서 놓기의 기본 동작은 복사입니다. 이동하려면 **Shift** 키를 누른 채 끌어서 놓습니다.

## <a name="plot-history"></a>플롯 기록

플롯 명령은 각 창에 대한 플롯 기록 내에 유지되므로 세션 내의 모든 그리기가 보존됩니다. 기록을 탐색하려면 플롯 창 도구 모음의 화살표 단추를 사용하거나 **Ctrl**+**Alt**+**F11** 및 **Ctrl**+**Alt**+**F12**를 사용합니다. 다시 도구 모음 단추 또는 **R 도구** > **플롯** 메뉴 명령을 사용하여 창에서 단일 플롯을 제거하거나 모든 플롯을 지울 수도 있습니다.

전체 플롯 컬렉션을 확인하려면 도구 모음 단추 또는 **R 도구** > **플롯** > **플롯 기록 창**을 사용하여 플롯 기록 창을 엽니다.
기록은 해당 창에 표시된 플롯의 미리 보기 목록을 플롯 창(또는 디바이스)별로 그룹화하여 제공합니다. 도구 모음에서 확대/축소 단추를 사용하여 미리 보기 크기를 변경할 수 있습니다.

![플롯 기록 창](media/plotting-plot-history-window.png)

플롯을 연결된 창에서 열려면 해당 플롯을 두 번 클릭하여 선택하고 **플롯 표시** 도구 모음 단추를 선택하거나, 마우스 오른쪽 단추를 클릭하고 **플롯 표시**를 선택합니다. 개별 플롯을 선택하고 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴 또는 **편집** 메뉴에서 복사, 잘라내기 또는 삭제할 수도 있습니다.

모든 창에 대한 플롯 기록의 수명은 대화형 R 세션의 수명으로 제한됩니다. R 세션을 다시 설정하거나 Visual Studio를 종료하고 다시 시작하면 플롯 기록이 다시 설정됩니다.

## <a name="programmatically-manipulate-plot-windows"></a>프로그래밍 방식으로 플롯 창 조작

디바이스 번호를 통해 특정 플롯 창을 식별하여 R 코드에서 플롯 창을 프로그래밍 방식으로 조작할 수 있습니다.

- `dev.list()`: 현재 R 세션 내의 그래픽 디바이스를 모두 나열합니다.
- `dev.new()`: 새 그래픽 디바이스를 만듭니다(새 플롯 디바이스).
- `dev.set(<device number>)`: 활성 그래픽 디바이스를 설정합니다.
- `dev.off()`: 활성 디바이스를 삭제합니다.
