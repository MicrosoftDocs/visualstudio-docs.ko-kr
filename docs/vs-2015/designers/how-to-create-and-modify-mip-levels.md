---
title: '방법: MIP 수준 만들기 및 수정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99d2b07a64781929962ff37823ddcbf219598331
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664475"
---
# <a name="how-to-create-and-modify-mip-levels"></a>방법: MIP 수준 만들기 및 수정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 문서에서는 **이미지 편집기**를 사용하여 질감 공간 LoD(세밀도)에 대한 *MIP 수준*을 생성하고 수정하는 방법을 보여 줍니다.

## <a name="generating-mip-levels"></a>MIP 수준 생성
 *MIP 매핑*은 다양한 크기로 질감의 여러 복사본을 미리 계산하고 저장하여 렌더링 속도를 높이고 질감 개체의 앨리어싱 아티팩트를 줄이는 데 사용되는 기술입니다. MIP 수준이라고 하는 각 복사본은 이전 복사본의 너비와 높이의 절반입니다. 질감이 개체 표면에서 렌더링되면 질감 표면의 화면 공간 영역과 가장 가깝게 대응하는 MIP 수준이 자동으로 선택됩니다. 즉 그래픽 하드웨어에서 일관된 시각적 품질을 유지하기 위해 너무 큰 질감을 필터링할 필요가 없습니다. MIP 수준을 저장하는 데 드는 메모리 비용은 원래 질감의 메모리 비용보다 약 33% 더 많지만 성능 및 이미지 품질의 이점을 통해 이를 정당화할 수 있습니다.

#### <a name="to-generate-mip-levels"></a>MIP 수준을 생성하려면

1. [방법: 기본 질감 만들기](../designers/how-to-create-a-basic-texture.md)에서 설명한 대로 기본 질감으로 시작합니다. 최상의 결과를 얻으려면 너비와 높이가 2의 거듭제곱(예: 256, 512, 1024 등)인 질감을 지정합니다.

2. MIP 수준을 생성합니다. **이미지 편집기 모드** 도구 모음에서 **고급**, **도구**, **MIP 생성**을 차례로 선택합니다.

     이제 **다음 MIP 수준으로 이동** 및 **이전 MIP 수준으로 이동** 단추가 **이미지 편집기 모드** 도구 모음에 표시됩니다. **속성** 창이 표시되면 **MIP 수준** 및 **MIP 수준 수** 읽기 전용 속성이 이미지 속성에 표시됩니다.

## <a name="modifying-mip-levels"></a>MIP 수준 수정
 특수 효과를 얻거나 특정 세밀도에서 이미지 품질을 높이기 위해 각 MIP 수준을 개별적으로 수정할 수 있습니다. 예를 들어 질감이 있는 개체에 먼 거리의 다른 모양을 지정할 수 있거나(거리가 멀수록 MIP 수준이 작아짐), 더 작은 MIP 수준에서도 텍스트 또는 기호가 포함된 질감을 읽을 수 있습니다.

#### <a name="to-modify-an-individual-mip-level"></a>개별 MIP 수준을 수정하려면

1. 수정하려는 MIP 수준을 선택합니다. **이미지 편집기 모드** 도구 모음에서 **다음 MIP 수준으로 이동** 및 **이전 MIP 수준으로 이동** 단추를 사용하여 MIP 수준 간에 이동합니다.

2. 수정하려는 MIP 수준을 선택하면 그리기 도구를 사용하여 다른 MIP 수준의 콘텐츠를 변경하지 않고 수정할 수 있습니다. 그리기 도구는 **이미지 편집기** 도구 모음에서 사용할 수 있습니다. 도구를 선택하면 **속성** 창에서 해당 속성을 변경할 수 있습니다. 그리기 도구 및 해당 속성에 대한 자세한 내용은 [이미지 편집기](../designers/image-editor.md)를 참조하세요.

> [!NOTE]
> 특정 효과를 얻기 위해 수행할 수 있는 것처럼 개별 MIP 수준의 콘텐츠를 수정할 필요가 없는 경우 빌드할 때 원본 질감에서 MIP 맵을 생성하는 것이 좋습니다. 이렇게 하면 MIP 수준 수정이 자동으로 다른 수준으로 전파되지 않으므로 MIP 수준이 원본 질감과 동기화되도록 할 수 있습니다. 빌드 시간에 MIP 맵을 생성하는 방법에 대한 자세한 내용은 [방법: MIP 맵을 포함하는 질감 내보내기](../designers/how-to-export-a-texture-that-contains-mipmaps.md)를 참조하세요.

## <a name="see-also"></a>관련 항목
 [방법: 기본 질감 만들기](../designers/how-to-create-a-basic-texture.md)
