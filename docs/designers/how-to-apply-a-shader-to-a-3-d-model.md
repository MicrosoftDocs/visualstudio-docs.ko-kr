---
title: '방법: 3D 모델에 셰이더 적용'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f1ae981704287a74bb4e37117190b8b6111d0a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769238"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>방법: 3D 모델에 셰이더 적용

이 문서에서는 모델 편집기를 사용하여 DGSL(Directed Graph Shader Language) 셰이더를 3D 모델에 적용하는 방법을 보여 줍니다.

## <a name="apply-a-shader-to-a-3d-model"></a>3D 모델에 셰이더 적용

3D 모델에 셰이더 효과를 적용하여 흥미로운 모양을 제공할 수 있습니다.

시작하기 전에 **속성** 창이 표시되는지 확인하세요.

1. 하나 이상의 모델이 포함된 3D 장면으로 시작합니다. 적합한 3D 장면이 없으면 [방법: 기본 3D 모델 만들기](../designers/how-to-create-a-basic-3-d-model.md)에 설명된 대로 장면을 만듭니다. 또한 모델에 적용할 수 있는 DGSL 셰이더가 있어야 합니다. 적합한 셰이더가 없으면 [방법: 기본 색 셰이더 만들기](../designers/how-to-create-a-basic-color-shader.md)에 설명된 대로 셰이더를 만들고 계속하기 전에 파일에 저장했는지 확인합니다.

2. **선택** 모드에서 셰이더를 적용할 모델을 선택한 다음, **속성** 창에 있는 **효과** 속성 그룹의 **파일 이름** 속성에서 모델에 적용할 DGSL 셰이더를 지정합니다.

다음은 기본 색 효과가 적용된 모델입니다.

![기본 색 효과를 보여 주는 3D 장면](../designers/media/digit-3d-model-effect.png)

모델에 셰이더를 적용한 후 모델을 선택하고 **속성** 창에 있는 **효과** 속성 그룹의 **(고급)** 속성에서 말줄임표( **...** ) 단추를 선택하여 셰이더 디자이너에서 모델을 열 수 있습니다.

## <a name="see-also"></a>참고 항목

- [방법: 기본 3D 모델 만들기](../designers/how-to-create-a-basic-3-d-model.md)
- [방법: 기본 색 셰이더 만들기](../designers/how-to-create-a-basic-color-shader.md)
- [모델 편집기](../designers/model-editor.md)
- [셰이더 디자이너](../designers/shader-designer.md)
