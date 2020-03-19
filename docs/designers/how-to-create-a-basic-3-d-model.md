---
title: '방법: 기본 3D 모델 만들기'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce16e436172a7d369f2df8342f6b027b574056ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589528"
---
# <a name="how-to-create-a-basic-3d-model"></a>방법: 기본 3D 모델 만들기

이 문서에서는 모델 편집기를 사용하여 기본 3D 모델을 만드는 방법을 설명합니다. 다음과 같은 작업을 설명합니다.

- 장면에 개체 추가

- 면 및 가장자리 선택

- 선택 영역 변환

- **면 나누기** 및 **면 돌출** 도구 사용

- **삼각 측량** 명령 사용

## <a name="create-a-basic-3d-model"></a>기본 3D 모델 만들기
모델 편집기를 사용하여 게임 또는 앱에 사용할 3D 모델 및 장면을 만들고 수정할 수 있습니다. 다음 단계에서는 모델 편집기를 사용하여 집의 단순 3D 모델을 만드는 방법을 보여줍니다. 단순 모델은 계속 생성 중인 최종 아트 자산의 대체물로, 충돌 탐지를 위한 메시로, 표현하는 개체가 너무 멀어 자세한 렌더링을 사용할 수 없을 때 덜 자세한 모델로 사용할 수 있습니다.

작업을 완료하면 모델이 다음과 같이 나타납니다.

![완료된 간이형 집 모델](../designers/media/gfx_model_demo_house_final.png)

시작하기 전에 **속성** 창과 **도구 상자**가 표시되는지 확인합니다.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>집의 단순 3D 모델을 만들려면

1. 작업할 3D 모델을 만듭니다. 모델을 프로젝트에 추가하는 방법에 대한 내용은 [모델 편집기](../designers/model-editor.md)의 시작 섹션을 참조하세요.

2. 장면에 큐브를 추가 합니다. **도구 상자** 창의 **도형** 아래에서 **정육면체**를 선택한 다음 디자인 화면으로 옮깁니다.

3. 면 선택 영역으로 전환합니다. [모델 편집기] 도구 모음에서 **표면 선택**을 선택합니다.

4. 정육면체의 맨 위를 나눕니다. 표면 선택 모드에서 정육면체를 한 번 선택하여 선택 영역을 활성화하고 정육면체의 맨 위를 선택하여 위쪽 표면을 선택합니다. [모델 편집기] 도구 모음에서 **면 나누기**를 선택합니다. 이렇게 하면 균등하게 4등분된 파티션으로 나누는 정육면체의 맨 위에 새 꼭짓점이 추가됩니다.

    ![정육면체의 위쪽이 나뉨](../designers/media/gfx_model_demo_house_subdiv.png)

5. 정육면체의 인접한 두 면, 예를 들어 정육면체의 앞면과 오른쪽 면을 돌출합니다. 표면 선택 모드에서 정육면체를 한 번 선택하여 선택 영역을 활성화한 다음 정육면체의 한 면을 선택합니다. **Ctrl** 키를 누른 상태에서 먼저 선택한 정육면체의 면과 인접한 다른 쪽 면을 선택한 다음, [모델 편집기] 도구 모음에서 **면 돌출**을 선택합니다.

    ![정육면체의 양쪽 면이 돌출됨](../designers/media/gfx_model_demo_house_extrude.png)

6. 돌출된 면 중 하나를 확장합니다. 돌출한 표면 중 하나를 선택한 다음 [모델 편집기] 도구 모음에서 **좌표 이동** 도구를 선택하고 변환 조작자를 돌출과 같은 방향을 이동합니다.

    ![정육면체의 한쪽 면이 더 돌출됨](../designers/media/gfx_model_demo_house_extend.png)

7. 모델을 삼각 측량합니다. [모델 편집기] 도구 모음에서 **고급** > **도구** > **삼각 측량**을 선택합니다.

8. 집의 지붕을 만듭니다. [모델 편집기] 도구 모음에서 **가장자리 선택**을 선택하여 가장자리 선택 모드로 전환한 다음 정육면체를 선택하여 활성화합니다. 아래와 같이 가장자리가 선택되도록 **Ctrl** 키를 길게 누릅니다.

    ![지붕 끝을 형성할 가장자리](../designers/media/gfx_model_demo_house_edges.png)

    가장자리가 선택되었으면 [모델 편집기] 도구 모음에서 **좌표 이동** 도구를 선택한 다음 변환 조작자를 위로 이동하여 집의 지붕을 만듭니다.

   간소화된 집 모델이 완성되었습니다. 플랫 음영이 적용된 최종 모델은 다음과 같습니다.

   ![완료된 간이형 집 모델](../designers/media/gfx_model_demo_house_final.png)

   다음 단계에서 이 3D 모델에 셰이더를 적용할 수 있습니다. 자세한 내용은 [방법: 3D 모델에 셰이더 적용](../designers/how-to-apply-a-shader-to-a-3-d-model.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [방법: 3D 지형 모델 만들기](../designers/how-to-model-3-d-terrain.md)
- [모델 편집기](../designers/model-editor.md)
- [셰이더 디자이너](../designers/shader-designer.md)
