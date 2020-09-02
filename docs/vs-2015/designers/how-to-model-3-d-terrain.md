---
title: '방법: 3D 지형 모델 만들기 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ab202ed97ce2056313eb661d51d7150bb9689829
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664418"
---
# <a name="how-to-model-3-d-terrain"></a>방법: 3차원 지형 모델 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 문서에서는 모델 편집기를 사용하여 3D 지형 모델을 만드는 방법을 설명합니다.

 이 문서는 다음 활동을 보여 줍니다.

- 장면에 개체 추가

- 면 및 점 선택

- 선택 영역 변환

- **면 나누기** 도구 사용

- 디자인 화면에서 개체 프레이밍

## <a name="creating-a-3-d-terrain-model"></a>3D 지형 모델 만들기
 평면을 나눠서 추가적인 면을 만들고 꼭짓점을 조작하여 흥미로운 지형 특성을 만드는 방식으로 3D 지형을 만들 수 있습니다.

 작업을 완료하면 모델이 다음과 같이 나타납니다.

 ![지형 모델을 보여 주는 3&#45;D 장면](../designers/media/digit-terrain-model.png "Digit-지형 모델")

 시작하기 전에 **속성** 창과 **도구 상자**가 표시되는지 확인합니다.

#### <a name="to-create-a-3-d-terrain-model"></a>3D 지형 모델을 만들려면

1. 작업할 3D 모델을 만듭니다. 모델을 프로젝트에 추가하는 방법에 대한 내용은 [모델 편집기](../designers/model-editor.md)의 시작 섹션을 참조하세요.

2. 장면에 평면을 추가합니다. **도구 상자**의 **도형**에서 **평면**을 선택하고 디자인 화면으로 이동합니다.

   > [!TIP]
   > 평면 개체를 더 쉽게 사용할 수 있도록 디자인 화면에서 개체를 프레이밍할 수 있습니다. **선택** 모드에서 평면 개체를 선택하고 [모델 편집기] 도구 모음에서 **프레임 개체** 단추를 선택합니다.

3. 면 선택 모드를 시작합니다. [모델 편집기] 도구 모음에서 **표면 선택**을 선택합니다.

4. 평면을 나눕니다. 면 선택 모드에서 평면을 한 번 선택하여 선택할 수 있도록 활성화하고 평면을 다시 선택하여 해당 면만 선택합니다. [모델 편집기] 도구 모음에서 **면 나누기**를 선택합니다. 그러면 평면을 균일한 크기의 파티션 4개로 분할하는 새 꼭짓점이 평면에 추가됩니다.

5. 추가적인 하위 분류 단위를 만듭니다. 새 면을 선택한 채 **면 나누기**를 두 번 더 선택합니다. 그러면 총 64개의 면이 만들어집니다. 추가적인 하위 분류 단위를 만들어 훨씬 더 세부적인 지형을 제공할 수 있습니다.

6. 점 선택 모드를 시작합니다. [모델 편집기] 도구 모음에서 **점 선택**을 선택합니다.

7. 점을 수정하여 지형 특성을 만듭니다. 점 선택 모드에서 점 중 하나를 선택하고 [모델 편집기] 도구 모음에서 **좌표 이동** 도구를 선택합니다. 점을 표현하는 상자가 디자인 화면에 표시됩니다. 녹색 화살표를 사용하여 상자를 이동하고 여기에서 점의 높이를 수정합니다. 다른 점에 대해 이 단계를 반복하여 흥미로운 지형 특성을 만듭니다.

   > [!TIP]
   > 한 번에 여러 점을 선택하여 동일한 방식으로 수정할 수 있습니다.

   지형 모델이 완료되었습니다. 다음은 다시 퐁 음영이 적용된 최종 모델입니다.

   ![지형 모델을 보여 주는 3&#45;D 장면](../designers/media/digit-terrain-model.png "Digit-지형 모델")

   이 지형 모델을 사용 하 여 [방법: 기 하 도형 기반 그라데이션 셰이더 만들기](../designers/how-to-create-a-geometry-based-gradient-shader.md)에 설명 된 그라데이션 셰이더의 효과를 보여줄 수 있습니다.

## <a name="see-also"></a>관련 항목
 [모델 편집기](../designers/model-editor.md)
