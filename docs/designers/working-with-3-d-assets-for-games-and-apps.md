---
title: 게임 및 앱을 위한 3D 자산 작업
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa9fc04df3e817730492353e54d74c1e46c3775e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589801"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>게임 및 앱을 위한 3D 자산 작업

이 문서에서는 DirectX 기반 게임 및 앱에 대한 3D 모델, 질감 및 셰이더를 만들거나 수정하는 데 사용할 수 있는 Visual Studio Tools에 대해 설명합니다.

## <a name="directx-app-development-in-visual-studio"></a>Visual Studio에서 DirectX 앱 개발

DirectX 앱은 일반적으로 프로그래밍 논리, DirectX API 및 HLSL(High Level Shading Language) 프로그램과 오디오 및 3D 시각적 자산을 결합하여 풍부한 대화형 멀티미디어 환경을 제공합니다. Visual Studio에는 IDE에서 다른 도구를 사용하지 않고 이미지와 질감, 3D 모델 및 셰이더 작업에 사용할 수 있는 도구가 포함되어 있습니다. Visual Studio 도구는 특히 *자리 표시자* 자산을 만드는 데 적합합니다. 이 자산은 프로덕션 준비 자산을 위임하기 전에 코드를 테스트하거나 프로토타입을 생성하고, 앱을 디버그할 때 프로덕션 준비 자산을 검사 및 수정하는 데 사용할 수 있습니다.

Visual Studio에서 사용할 수 있는 자산의 종류에 대한 자세한 정보는 다음과 같습니다.

### <a name="images-and-textures"></a>이미지와 질감

이미지와 질감은 게임 및 앱에서 색 및 시각적 세밀도를 제공합니다. 3D 그래픽에서 질감은 다양한 용도를 지원하기 위해 다양한 형식, 유형 및 기하 도형으로 제공됩니다. 예를 들어 법선 맵은 3D 모델의 더 자세한 조명에 대해 픽셀당 표면 법선을 제공하며, 큐브 맵은 스카이 박싱, 반사 및 구면 질감 매핑과 같은 용도로 모든 방향의 질감을 제공합니다. 질감은 다양한 세밀도로 효율적인 렌더링을 지원하는 MIP 맵을 제공할 수 있으며, 다양한 색 채널과 색 순서 지정을 지원할 수 있습니다. 질감은 전용 그래픽 메모리를 덜 차지하는 다양한 압축 형식으로 저장할 수 있으며 GPU에서 질감에 더 효율적으로 액세스할 수 있도록 합니다.

Visual Studio 이미지 편집기를 사용하여 많은 공통 유형 및 형식의 이미지와 질감으로 작업할 수 있습니다.

### <a name="3d-models"></a>3D 모델

3D 모델은 게임과 앱에서 공간과 모양을 만듭니다. 최소한, 모델은 모델의 모양을 나타내는 선 또는 삼각형을 정의하기 위해 인덱싱 데이터와 함께 3D 공간에서 *꼭짓점*으로 알려진 점의 위치를 인코딩합니다. 추가 데이터는 이러한 꼭짓점과 연결될 수 있습니다(예: 색 정보, 법선 벡터 또는 앱 관련 특성). 또한 각 모델은 개체 전체 특성을 정의할 수도 있습니다. 예를 들어 개체 표면의 모양을 컴퓨팅하는 데 사용되는 셰이더 또는 개체의 표면에 적용되는 질감을 정의할 수 있습니다.

Visual Studio 모델 편집기를 사용하여 몇 가지 공통 형식으로 3D 모델을 작업할 수 있습니다.

### <a name="shaders"></a>셰이더

셰이더는 GPU(그래픽 처리 장치)에서 실행되는 작은 도메인 특정 프로그램입니다. 셰이더는 3D 모델을 화면상의 모양으로 변환하는 방법과 해당 모양의 각 픽셀에 대해 색 지정하는 방법을 결정합니다. 셰이더를 만들어 게임 또는 앱의 개체에 적용하여 개체에 독특한 모양을 제공할 수 있습니다.

그래프 기반 셰이더 디자인 도구인 Visual Studio 셰이더 디자이너를 사용하여 HLSL 프로그래밍을 알 필요 없이 사용자 지정 시각적 효과를 만들 수 있습니다.

> [!NOTE]
> DirectX 프로그래밍을 시작하는 방법에 대한 자세한 내용은 [DirectX](/windows/win32/directx)를 참조하세요. DirectX 기반 앱을 디버그하는 방법에 대한 자세한 내용은 [그래픽 진단(DirectX 그래픽 디버그)](../debugger/graphics/visual-studio-graphics-diagnostics.md)을 참조하세요.

## <a name="directx-version-compatibility"></a>DirectX 버전 호환성

Visual Studio는 DirectX를 사용하여 2D 및 3D 자산을 렌더링합니다. DirectX 11 렌더러 또는 WARP(Windows Advanced Rasterization Platform) 소프트웨어 렌더러를 선택할 수 있습니다. DirectX 11 렌더러는 DirectX 11 및 DirectX 10 GPU에서 고성능 하드웨어 가속 렌더링을 제공합니다. WARP 렌더러는 자산이 광범위한 컴퓨터에서 작동하는지 확인하는 데 도움이 됩니다. 여기에는 최신 그래픽 하드웨어가 없는 컴퓨터와 통합 그래픽 하드웨어가 있는 컴퓨터가 포함됩니다. WARP에 대한 자세한 내용은 [WARP(Windows Advanced Rasterization Platform) 가이드](/windows/win32/direct3darticles/directx-warp)를 참조하세요.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[질감 및 이미지 작업](../designers/working-with-textures-and-images.md)|Visual Studio를 사용하여 이미지와 질감을 사용하는 방법을 설명합니다.|
|[3D 모델 작업](../designers/working-with-3-d-models.md)|Visual Studio를 사용하여 3D 모델을 작업하는 방법을 설명합니다.|
|[셰이더 작업](../designers/working-with-shaders.md)|Visual Studio 셰이더 디자이너를 사용하여 사용자 지정 셰이더 효과를 만들고 수정하는 방법을 설명합니다.|
|[게임 또는 앱에서 3D 자산 사용](../designers/using-3-d-assets-in-your-game-or-app.md)|이미지 편집기, 모델 편집기 또는 셰이더 디자이너를 사용하여 만든 자산을 게임 또는 앱에서 사용하는 방법을 설명합니다.|
