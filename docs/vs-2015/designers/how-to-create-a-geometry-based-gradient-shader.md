---
title: '방법: 기하 도형 기반 그라데이션 셰이더 만들기 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1d9bfa9a6e9be1a97b3a606aa302defd12a8d062
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664518"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>방법: 기하 도형 기반 그라데이션 셰이더 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 문서에서는 셰이더 디자이너 및 DGSL(Directed Graph Shader Language)을 사용하여 기하 도형 기반 그라데이션 셰이더를 만드는 방법을 보여 줍니다. 이 셰이더는 세계 좌표 위치에서 개체의 각 점 높이로 상수 RGB 색 값의 비율 크기를 조정합니다.

 이 문서는 다음 활동을 보여 줍니다.

- 셰이더 그래프에 노드 추가

- 노드 속성 설정

- 노드 연결 해제

- 노드 연결

## <a name="creating-a-geometry-based-gradient-shader"></a>기하 도형 기반 그라데이션 셰이더 만들기
 픽셀의 위치를 셰이더로 통합하여 기하 도형 기반 셰이더를 구현할 수 있습니다. 음영 언어에서 픽셀에는 2D 화면의 색상 및 위치 보다 더 많은 정보가 포함되어 있습니다. 일부 시스템에서는 *조각*이라고 하는 픽셀은 픽셀에 해당하는 표면을 설명하는 값의 모음입니다. 이 문서에 설명된 셰이더는 조각의 월드 공간에서 최종 출력 색상에 영향을 미치는 3D 개체의 각 픽셀 높이를 사용합니다.

 시작하기 전에 **속성** 창과 **도구 상자**가 표시되는지 확인하세요.

#### <a name="to-create-a-geometry-based-gradient-shader"></a>기하 도형 기반 그라데이션 셰이더를 만들려면

1. 사용할 DGSL 셰이더를 만듭니다. DGSL 셰이더를 프로젝트에 추가하는 방법에 대한 내용은 [셰이더 디자이너](../designers/shader-designer.md)의 시작 섹션을 참조하세요.

2. **최종 색** 노드에서 **점 색** 노드의 연결을 끊습니다. **점 색** 노드의 **RGB** 터미널을 선택하고 **연결 끊기**를 선택합니다. 그러면 다음 단계에서 추가되는 노드에 대한 공간이 생깁니다.

3. **곱하기** 노드를 그래프에 추가합니다. **도구 상자**의 **수학**에서 **곱하기**를 선택하고 디자인 화면으로 이동합니다.

4. **마스크 벡터** 노드를 그래프에 추가합니다. **도구 상자**의 **유틸리티**에서 **마스크 벡터**를 선택하고 디자인 화면으로 이동합니다.

5. **마스크 벡터** 노드에 대한 마스크 값을 지정합니다. **선택** 모드에서 **마스크 벡터** 노드를 선택하고 **속성** 창에서 **녹색 / Y** 속성을 **True**로 설정하고 **빨간색 / X**, **파란색 / Z** 및 **알파 / W** 속성을 **False**로 설정합니다. 이 예제에서 **빨간색 / X**, **녹색 / Y** 및 **파란색 / Z** 속성은 **세계 좌표 위치** 노드의 x, y, z 구성 요소에 해당하며 **알파 / W**는 사용하지 않습니다. **녹색 / Y**만 **True**로 설정했기 때문에 마스킹한 후 입력 벡터의 y 구성 요소만 유지됩니다.

6. **세계 좌표 위치** 노드를 그래프에 추가합니다. **도구 상자**의 **상수**에서 **세계 좌표 위치**를 선택하고 디자인 화면으로 이동합니다.

7. 조각의 세계 좌표 위치를 마스크합니다. **선택** 모드에서 **세계 좌표 위치** 노드의 **출력** 터미널을 **마스크 벡터** 노드의 **벡터** 터미널로 이동합니다. 이 연결은 x 및 z 구성 요소를 무시할 조각의 위치를 마스크합니다.

8. RGB 색 상수에 마스크된 세계 좌표 위치를 곱합니다. **점 색** 노드의 **RGB** 터미널을 **곱하기** 노드의 **Y** 터미널로 이동한 다음 **마스크 벡터** 노드의 **출력** 터미널을 **곱하기** 노드의 **X** 터미널로 이동합니다. 이 연결은 세계 좌표 위치에서 픽셀의 높이로 색상 값의 배율을 조정합니다.

9. 비율 크기가 조정된 색 값을 최종 색에 연결합니다. **곱하기** 노드의 **출력** 터미널을 **최종 색** 노드의 **RGB** 터미널로 이동합니다.

   다음 그림은 구에 적용된 셰이더의 완료된 셰이더 그래프 및 미리 보기를 보여 줍니다.

> [!NOTE]
> 이 그림에서 주황색은 셰이더의 효과를 더 잘 보여 주기 위해 지정되었지만, 미리 보기 도형은 세계 좌표 위치에서 위치가 없으므로 셰이더 디자이너에서 셰이더를 완전히 미리 볼 수 없습니다. 전체 효과를 보여 주려면 실제 장면에서 셰이더를 미리 봐야 합니다.

 ![셰이더 그래프 및 효과 미리 보기](../designers/media/digit-gradient-effect-graph.png "숫자-그라데이션-효과-그래프")

 일부 셰이더의 경우 특정 도형을 사용하면 미리 보기가 더 잘 표시될 수 있습니다. 셰이더 디자이너에서 셰이더를 미리 보는 방법에 대 한 자세한 내용은 [셰이더 디자이너](../designers/shader-designer.md) 에서 **셰이더** 미리 보기를 참조 하세요.

 다음 그림은 [방법: 3 차원 지형 모델](../designers/how-to-model-3-d-terrain.md)에 설명 된 3 차원 장면에 적용 되는이 문서에서 설명 하는 셰이더를 보여 줍니다. 세계 좌표 위치에서 점의 높이와 함께 색의 농도가 증가합니다.

 ![3&#45;D 지형 모델에 적용 된 그라데이션 효과](../designers/media/digit-gradient-effect-result.png "숫자-그라데이션-효과-결과")

 3 차원 모델에 셰이더를 적용 하는 방법에 대 한 자세한 내용은 [방법: 3 차원 모델에 셰이더 적용](../designers/how-to-apply-a-shader-to-a-3-d-model.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 [방법: 3 차원 모델에 셰이더 적용](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [방법: 셰이더 내보내기](../designers/how-to-export-a-shader.md) [방법: 모델 3 차원 지형](../designers/how-to-model-3-d-terrain.md) [방법: 회색조 질감 셰이더](../designers/how-to-create-a-grayscale-texture-shader.md) 셰이더 [디자이너](../designers/shader-designer.md) [셰이더 디자이너 노드](../designers/shader-designer-nodes.md) 만들기
