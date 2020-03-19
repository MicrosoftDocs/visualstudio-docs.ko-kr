---
title: '방법: 회색조 질감 셰이더 만들기'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b74e956a74ff4c04dbc5a1c990fab708937d8f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112621"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>방법: 회색조 질감 셰이더 만들기

이 문서에서는 셰이더 디자이너 및 DGSL(Directed Graph Shader Language)을 사용하여 회색조 질감 셰이더를 만드는 방법을 보여 줍니다. 이 셰이더는 질감 샘플의 RGB 색 값을 수정하고 이 값과 수정되지 않은 알파 값을 함께 사용해서 최종 색을 설정합니다.

## <a name="create-a-grayscale-texture-shader"></a>회색조 질감 셰이더 만들기

최종 출력 색으로 작성하기 전에 질감 샘플의 색 값을 수정하여 회색조 질감 셰이더를 구현할 수 있습니다.

시작하기 전에 **속성** 창과 **도구 상자**가 표시되는지 확인하세요.

1. [방법: 기본 질감 셰이더 만들기](../designers/how-to-create-a-basic-texture-shader.md)에 설명된 대로 기본 질감 셰이더를 만듭니다.

2. **최종 색**노드의 **RGB** 터미널에서 **질감 샘플** 노드의 **RGB** 터미널 연결을 끊습니다. **선택** 모드에서 **질감 샘플** 노드의 **RGB** 터미널을 선택하고 **연결 끊기**를 선택합니다. 그러면 다음 단계에서 추가되는 노드에 대한 공간이 생깁니다.

3. **흐리기** 노드를 그래프에 추가합니다. **도구 상자**의 **필터**에서 **흐리기**를 선택하고 디자인 화면으로 이동합니다.

4. **흐리기** 노드를 사용하여 회색조 값을 계산합니다. **선택** 모드에서 **질감 샘플** 노드의 **RGB** 터미널을 **흐리기** 노드의 **RGB** 터미널로 이동합니다.

    > [!NOTE]
    > 기본적으로 **흐리기** 노드는 입력 코드의 채도를 완전히 감소시키고 회색조 변환을 위해 표준 광도 가중치를 사용합니다. **광도** 속성의 값을 변경하거나 입력 색의 채도를 부분적으로만 감소시켜서 **흐리기** 노드의 동작 방식을 변경할 수 있습니다. 입력 색의 채도를 부분적으로 감소시키려면 **흐리기** 노드의 **백분율** 터미널에 [0,1) 범위의 스칼라 값을 제공합니다.

5. 회색조 색 값을 최종 색에 연결합니다. **흐리기** 노드의 **출력** 터미널을 **최종 색** 노드의 **RGB** 터미널로 이동합니다.

다음 그림은 정육면체에 적용된 셰이더의 완료된 셰이더 그래프 및 미리 보기를 보여 줍니다.

> [!NOTE]
> 이 그림에서 평면을 미리 보기 셰이프로 사용되고 셰이더의 효과를 더욱 효과적으로 표시하기 위해 질감이 지정되었습니다.

![셰이더 그래프 및 효과 미리 보기](../designers/media/digit-grayscale-effect.png)

일부 셰이더의 경우 특정 도형을 사용하면 미리 보기가 더 잘 표시될 수 있습니다. 셰이더 디자이너에서 셰이더를 미리 보는 방법에 대한 자세한 내용은 [셰이더 디자이너](../designers/shader-designer.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [방법: 3D 모델에 셰이더 적용](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [방법: 셰이더 내보내기](../designers/how-to-export-a-shader.md)
- [이미지 편집기](../designers/image-editor.md)
- [셰이더 디자이너](../designers/shader-designer.md)
- [셰이더 디자이너 노드](../designers/shader-designer-nodes.md)
