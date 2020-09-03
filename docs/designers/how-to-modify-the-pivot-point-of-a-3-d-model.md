---
title: '방법: 3D 모델의 피벗 점 수정'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9f79f8f5a39a8721e433207f2fbb17fd85a1150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85768839"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>방법: 3D 모델의 피벗 점 수정

이 문서에서는 모델 편집기를 사용하여 3D 모델의 *피벗 점*을 수정하는 방법을 설명합니다. 피벗 점은 회전 및 크기 조정에 사용할 개체의 수학적 중심을 정의하는 공간의 점입니다.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>3D 모델의 피벗 점 수정

3D 모델의 피벗 점을 수정하여 3D 모델의 원본을 다시 정의할 수 있습니다.

**속성** 창과 **도구 상자**가 표시되는지 확인하세요.

1. [방법: 기본 3D 모델 만들기](../designers/how-to-create-a-basic-3-d-model.md)에 설명된 모델과 같은 기존 3D 모델로 시작합니다.

2. 피벗 모드를 시작합니다. **모델 편집기 모드** 도구 모음에서 **피벗 모드** 단추를 선택하여 피벗 모드를 활성화합니다. 모델 편집기가 현재 피벗 모드임을 나타내는 **피벗 모드** 단추가 상자 주변에 나타납니다. 피벗 모드에서 좌표 이동 등의 작업은 세계 좌표 위치에 있는 개체의 구조가 아니라 개체의 피벗 점에 영향을 미칩니다.

3. 개체의 피벗 점을 수정합니다. **선택** 모드에서 개체를 선택하고 **모델 뷰어** 도구 모음에서 **좌표 이동** 도구를 선택합니다. 피벗 점을 표현하는 상자가 디자인 화면에 표시됩니다. 상자를 이동하여 개체의 피벗 점을 수정합니다.

     상자를 이동하는 방식으로 3개의 차원에서 모두 피벗 점을 이동할 수 있습니다. 한 축을 따라 피벗 점을 좌표 이동하려면 이 축과 일치하는 화살표를 이동합니다. 상자와 화살표가 노란색으로 변경되어 좌표 이동의 영향을 받은 축을 표시합니다.

     **속성** 창의 **중심점 변환** 속성을 사용하여 피벗 점을 지정할 수도 있습니다.

    > [!TIP]
    > 개체를 회전하여 새 피벗 점의 효과를 확인할 수 있습니다. 개체를 회전하려면 **회전** 도구를 사용하거나 **회전** 속성을 수정합니다.

수정된 피벗 점이 있는 모델은 다음과 같습니다.

![수정된 피벗 점이 있는 집 모델](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>참고 항목

- [방법: 기본 3D 모델 만들기](../designers/how-to-create-a-basic-3-d-model.md)
- [모델 편집기](../designers/model-editor.md)
