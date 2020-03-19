---
title: 셰이더 작업
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7ccb4f838c702cb1843d5c0f44dd7f54219f27a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589775"
---
# <a name="work-with-shaders"></a>셰이더 작업

Visual Studio의 그래프 기반 셰이더 디자이너를 사용하여 사용자 지정 셰이더 효과를 디자인할 수 있습니다. DirectX 기반 게임 또는 앱에서 이 셰이더를 사용할 수 있습니다.

## <a name="shaders"></a>셰이더

*셰이더*는 그래픽 계산(예: 꼭짓점 변환 또는 픽셀 색 지정)을 수행하는 컴퓨터 프로그램으로, 일반적으로 CPU 대신 GPU(그래픽 처리 장치)에서 실행됩니다. 기존의 고정 함수 그래픽 파이프라인의 단계 대부분이 이제 셰이더 프로그램에서 수행되므로 이를 사용하여 앱의 요구 사항에 맞는 파이프라인을 만들 수 있습니다.

가장 일반적인 종류의 셰이더는 *꼭짓점 셰이더* 및 *픽셀 셰이더*입니다. 전자는 꼭짓점별 계산을 수행하고 프로그래밍할 수 없는 그래픽 하드웨어에서 고정 함수 변환 및 조명 회로를 대체하며, 후자는 픽셀의 색을 결정하는 픽셀별 계산을 수행하고 프로그래밍할 수 없는 그래픽 하드웨어에서 고정 함수 색 결합 회로를 대체합니다. 최신 그래픽 하드웨어는 더 많은 종류의 셰이더, 즉 그래픽 컴퓨팅용 *헐 셰이더*, *도메인 셰이더*, *기하 도형 셰이더* 및 비그래픽 컴퓨팅용 *컴퓨팅 셰이더*를 만들 수 있습니다. 이러한 단계들 중 어느 것도 프로그래밍할 수 없는 그래픽 하드웨어에서 사용할 수 없습니다. 셰이더는 원래 데이터 병렬(SIMD) 및 그래픽 중심(내적) 명령을 제공하는 어셈블리와 비슷한 언어를 사용하여 만들어졌습니다. 이제 셰이더는 일반적으로 HLSL(High Level Shader Language)과 같은 C 유사 고급 언어를 사용하여 만듭니다.

셰이더 디자이너를 사용하여 코드를 입력하고 컴파일하는 대신 대화형으로 픽셀 셰이더를 만들 수 있습니다. 셰이더 디자이너에서 셰이더는 데이터와 작업을 나타내는 많은 노드 및 셰이더를 통한 데이터 값과 중간 결과의 흐름을 나타내는 노드 간의 연결로 정의됩니다. 셰이더 디자이너에서 이러한 방법과 실시간 미리 보기를 사용하여 셰이더 실행을 더 쉽게 시각화하고 실험을 통해 흥미로운 셰이더 변형을 "검색"할 수 있습니다.

## <a name="dgsl-documents"></a>DGSL 문서

셰이더 디자이너는 셰이더를 DGSL(Directed Graph Shader Language) 형식으로 저장합니다. 이 형식은 DGML(Directed Graph Markup Language)을 기반으로 하는 XML 형식입니다. 모델 편집기에서는 3D 모델에 DGSL 셰이더를 직접 적용할 수 있습니다. 그러나 앱에서 DGSL 셰이더를 사용하려면 먼저 DirectX에서 이해할 수 있는 형식(예: HLSL)으로 내보내야 합니다.

DGSL은 DGML과 호환되므로 DGML 문서를 분석하여 DGSL 셰이더를 분석하도록 설계된 도구를 사용할 수 있습니다. DGML에 대한 자세한 내용은 [DGML(Directed Graph Markup Language) 이해](../modeling/customize-code-maps-by-editing-the-dgml-files.md)를 참조하세요.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[셰이더 디자이너](../designers/shader-designer.md)|Visual Studio 셰이더 디자이너를 사용하여 셰이더 작업을 수행하는 방법을 설명합니다.|
|[셰이더 디자이너 노드](../designers/shader-designer-nodes.md)|그래픽 효과를 얻기 위해 사용할 수 있는 셰이더 디자이너 노드의 종류를 설명합니다.|
|[셰이더 디자이너 예제](../designers/how-to-create-a-basic-color-shader.md)|셰이더 디자이너를 사용하여 공통 그래픽 효과를 얻는 방법을 보여 주는 항목에 대한 링크를 제공합니다.|
