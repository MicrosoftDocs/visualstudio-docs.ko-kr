---
title: '방법: 기본 질감 셰이더 만들기 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59a926ab35e04aa120bc57250c3e5b2712858aa5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664494"
---
# <a name="how-to-create-a-basic-texture-shader"></a>방법: 기본 질감 셰이더 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 문서에서는 셰이더 디자이너 및 DGSL(Directed Graph Shader Language)을 사용하여 단일 질감 셰이더를 만드는 방법을 보여 줍니다. 이 셰이더는 최종 색을 바로 질감에서 샘플링된 RGB 및 알파 값으로 설정합니다.

 이 문서는 다음 활동을 보여 줍니다.

- 셰이더 그래프에서 노드 제거

- 그래프에 노드 추가

- 셰이더 매개 변수 설정

- 매개 변수 표시 유형 설정

- 노드 연결

## <a name="creating-a-basic-texture-shader"></a>기본 질감 셰이더 만들기
 질감 샘플의 색 및 알파 값을 직접 최종 출력 색으로 작성하여 기본적인 단일 질감 셰이더를 구현할 수 있습니다.

 시작하기 전에 **속성** 창과 **도구 상자**가 표시되는지 확인하세요.

#### <a name="to-create-a-basic-texture-shader"></a>기본 질감 셰이더를 만들려면

1. 사용할 DGSL 셰이더를 만듭니다. DGSL 셰이더를 프로젝트에 추가하는 방법에 대한 내용은 [셰이더 디자이너](../designers/shader-designer.md)의 시작 섹션을 참조하세요.

2. **점 색** 노드를 삭제합니다. **선택** 모드에서 **점 색** 노드를 선택하고 메뉴 표시줄에서 **편집**, **삭제**를 선택합니다. 그러면 다음 단계에서 추가되는 노드에 대한 공간이 생깁니다.

3. 그래프에 **질감 샘플** 노드를 추가합니다. **도구 상자**의 **질감**에서 **질감 샘플**을 선택하고 디자인 화면으로 이동합니다.

4. 그래프에 **질감 좌표** 노드를 추가합니다. **도구 상자**의 **질감**에서 **질감 좌표**를 선택하고 디자인 화면으로 이동합니다.

5. 적용할 질감을 선택합니다. **선택** 모드에서 **질감 샘플** 노드를 선택하고 **속성** 창에서 **파일 이름** 속성을 사용하여 사용할 질감을 지정합니다.

6. 질감에 공용으로 액세스할 수 있게 설정합니다. **질감 샘플** 노드를 선택하고 **속성** 창에서 the **액세스** 속성을 **공용**으로 설정합니다. 이제 **모델 편집기** 등의 또 다른 도구에서 질감을 설정할 수 있습니다.

7. 질감 좌표를 질감 샘플에 연결합니다. **선택** 모드에서 **질감 좌표** 노드의 **출력** 터미널을 **질감 샘플** 노드의 **UV** 터미널로 이동합니다. 이 연결은 지정된 좌표에서 질감을 샘플링합니다.

8. 질감 샘플을 최종 색에 연결합니다. **질감 샘플** 노드의 **RGB** 터미널을 **최종 색** 노드의 **RGB** 터미널로 이동하고 **질감 샘플** 노드의 **알파** 터미널을 **최종 색** 노드의 **알파** 터미널로 이동합니다.

   다음 그림은 정육면체에 적용된 셰이더의 완료된 셰이더 그래프 및 미리 보기를 보여 줍니다.

> [!NOTE]
> 이 그림에서 평면을 미리 보기 셰이프로 사용되고 셰이더의 효과를 더욱 효과적으로 표시하기 위해 질감이 지정되었습니다.

 ![셰이더 그래프 및 효과 미리 보기](../designers/media/digit-texture-effect.png "숫자-질감-효과")

 일부 셰이더의 경우 특정 도형을 사용하면 미리 보기가 더 잘 표시될 수 있습니다. 셰이더 디자이너에서 셰이더를 미리 보는 방법에 대 한 자세한 내용은 [셰이더 디자이너](../designers/shader-designer.md) 를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [방법: 3 차원 모델에 셰이더 적용](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [이미지 편집기](../designers/image-editor.md) [셰이더 디자이너](../designers/shader-designer.md) [셰이더 디자이너 노드](../designers/shader-designer-nodes.md)
