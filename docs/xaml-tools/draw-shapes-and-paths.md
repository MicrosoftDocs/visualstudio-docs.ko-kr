---
title: 도형 및 패스 그리기
description: Blend for Visual Studio를 사용 하 여 도형 및 경로에 세부 정보 추가
titleSuffix: Blend for Visual Studio
ms.date: 09/22/2020
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 368619a55316e0af59fc5351e187ced8892a6116
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022512"
---
# <a name="draw-shapes-and-paths"></a>도형 및 패스 그리기

XAML 디자이너에서 *도형은* 정확히 필요한 것입니다. (예: 사각형, 원, 또는 타원). *패스* 는 도형의 보다 유연한 버전으로 도형의 모양을 변경하거나 도형을 결합하는 등 작업을 수행하여 새 도형을 만들 수 있습니다.

도형 및 패스는 벡터 그래픽을 사용하여 고해상도 디스플레이에 맞게 조정됩니다.

## <a name="draw-a-shape"></a>도형 그리기

**자산** 창에서 도형을 찾습니다.

:::image type="content" source="media/blend-shapes.png" alt-text="Blend for Visual Studio 자산 창의 셰이프 범주 스크린샷":::

아트보드에 원하는 모든 도형을 끕니다. 그런 다음 도형에서 핸들을 사용하여 비율 크기를 조정하고 셰이프를 회전, 이동하거나 기울일 수 있습니다.

![핸들](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="draw-a-path"></a>패스 그리기

패스는 일련의 연결된 선 및 곡선입니다. 패스를 사용하여 **자산** 창에서 사용할 수 없는, 흥미로운 도형을 만들 수 있습니다.

선, 펜 또는 연필을 사용하여 패스를 그릴 수 있습니다. 이러한 도구는 **도구** 창에 있습니다.

### <a name="draw-a-straight-line"></a>직선 그리기

**펜** 도구나 **줄** 도구를 사용합니다.

**펜 도구 사용**

아트보드에서 한 번 클릭하여 시작 점을 정의한 후 다시 클릭하여 줄의 끝을 정의합니다.

**줄 도구 사용**

아트보드에서 줄을 시작할 위치에서 마우스를 끌어 줄을 끝낼 지점에서 마우스를 놓습니다.

### <a name="draw-a-curve"></a>곡선 그리기

**펜** 도구를 사용합니다.

아트보드에서 한 번 클릭하여 줄의 시작 점을 정의한 후 마우스 포인터를 클릭한 상태에서 끌어 원하는 곡선을 만듭니다.

패스를 닫으려면 줄에서 처음 지점을 클릭합니다.

### <a name="change-the-shape-of-a-curve"></a>곡선의 모양 변경

**직접 선택** 도구를 사용합니다.

도형을 클릭하고 도형에서 아무 점을 마우스로 끌어 곡선 모양을 변경합니다.

### <a name="draw-a-free-form-path"></a>자유형 패스 그리기

**연필** 도구를 사용합니다.

아트보드에서 실제 연필을 사용하는 것처럼 자유형 패스를 그립니다.

### <a name="remove-part-of-a-path"></a>패스의 일부 제거

**직접 선택** 도구를 사용합니다.

삭제할 세그먼트가 있는 패스를 선택한 후 **삭제** 단추를 클릭합니다.

### <a name="remove-a-point-in-a-path"></a>패스에서 점 제거

**선택** 도구를 사용 하 여 경로를 선택 합니다. 그런 다음 **펜** 도구를 사용하여 제거하려는 점을 클릭합니다.

### <a name="add-a-point-to-a-path"></a>패스에 점 추가

**선택** 도구를 사용 하 여 경로를 선택 합니다. **펜** 도구를 사용하여 패스에서 점을 추가할 위치를 클릭합니다.

## <a name="convert-a-shape-to-a-path"></a>도형을 패스로 변환

패스를 수정하는 방법과 같은 방법으로 도형을 수정하려면 도형을 패스로 변환합니다. 셰이프를 선택한 다음 **서식**  >  **경로**  >  **패스로 변환**를 선택 합니다.

**짧은 비디오 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.png) [경로 사용: 도형을 경로로 변환](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

> [!NOTE]
> **패스로 변환**은 최소`TargetPlatformVersion` 10.0.16299.0 이상인 UWP 앱에는 현재 사용할 수 없습니다.

## <a name="combine-paths"></a>패스 결합

패스 및 도형을 하나의 패스로 결합할 수 있습니다.

![패스 결합](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|번호|작업|
|-|-|
|![결합하기 전의 두 도형](../designers/media/b1_1.png)|결합하기 전의 두 도형|
|![통합](../designers/media/b1_2.png)|통합|
|![나누기](../designers/media/b1_3.png)|나누기|
|![Intersect](../designers/media/b1_4.png)|Intersect|
|![겹침 제외](../designers/media/b1_5.png)|겹침 제외|
|![빼기](../designers/media/b1_6.png)|빼기|

**짧은 비디오 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.png) [경로 사용: 경로 결합](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="create-a-compound-path"></a>복합형 패스 만들기

복합형 패스를 만들 때 패스의 교차되는 부분은 결과에서 제외되며, 결과 패스는 맨 아래 패스의 시각적 속성을 사용합니다.

복합형 패스를 만든 후 언제든지 분리할 수 있습니다.

![복합형 패스 중단](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

**짧은 비디오 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.png) [패스 사용: 복합형 패스 만들기](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="create-a-clipping-path"></a>클리핑 패스 만들기

클리핑 패스는 다른 개체에 적용되는 패스나 도형이며, 개체에서 클리핑 패스를 벗어나는, 마스킹된 개체 부분을 숨깁니다.

![클리핑 패스](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

**짧은 비디오 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.png) [패스 사용: 클리핑 패스 만들기](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).
