---
title: 펜 도구 한정자 키
titleSuffix: Blend for Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3ab14c6-a320-46db-a6b3-7fd1ca261587
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95a00fe4b87a0a9e1ee55497b84c59536d66d285
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "82921342"
---
# <a name="pen-tool-modifier-keys-in-blend-for-visual-studio"></a>Blend for Visual Studio의 펜 도구 보조 키

다음 표에는 **펜** 도구 ![펜 도구](../designers/media/d514358f-185a-412f-a55d-36633b25dc8a.png)를 사용하여 패스를 만드는 동안 패스를 수정하는 데 사용할 수 있는 바로 가기가 나와 있습니다. **펜** 도구를 사용하여 기존 패스에서 점을 추가 또는 제거하거나 두 개의 기존 패스를 연결할 수 있습니다.

|수행할 작업|단계|포인터|
| - |-------------|-------------|
|직선 세그먼트를 시작할 점 만들기|클릭하여 새 점을 만듭니다.|![직선 세그먼트를 시작할 점 만들기](../designers/media/0bfb1b71-80ac-4ad4-aed8-40e09f8b7ab8.png)<br /><br /> 펜 포인터|
|곡선 세그먼트를 시작할 점 만들기|클릭하여 새 점을 만든 후 마우스 단추를 손에서 떼기 전에 탄젠트 핸들을 끌어서 조정합니다.|![곡선 세그먼트를 시작할 점 만들기](../designers/media/0bfb1b71-80ac-4ad4-aed8-40e09f8b7ab8.png)<br /><br /> 펜 포인터|
|날카로운 모퉁이를 만들도록 부드러운 제약 조건 없이 마지막 탄젠트 조정|클릭하여 새 점을 만든 다음, 마우스 단추에서 손을 떼기 전에 **Alt** 키를 누릅니다.|![부드러운 제약 조건 없이 마지막 탄젠트 조정](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png)<br /><br /> 펜 조정 포인터|
|탄젠트 끝점이 개별적으로 작동하여 날카로운 모퉁이를 만들도록 마지막 탄젠트 분할|클릭하여 새 점을 만든 다음, 마우스 단추에서 손을 떼기 전에 **Alt** 키를 누른 채로 끕니다.|![탄젠트 끝점이 개별적으로 작동하도록 마지막 탄젠트 분할](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png)<br /><br /> 펜 조정 포인터|
|탄젠트 끝점을 새 점 주변에서 15도씩 늘려가며 이동|클릭 하 여 새 점을 만든 후 마우스 단추를 놓기 전에 **Shift**+**Alt** 를 누른 채로 끕니다.|![탄젠트 끝점을 새 점 주변에서 15도씩 늘려가며 이동](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png)<br /><br /> 펜 조정 포인터|
|끝점의 탄젠트 길이를 0으로 줄이기|끝점을 클릭합니다.|![끝점의 탄젠트 길이를 0으로 줄이기](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png)<br /><br /> 펜 조정 포인터|
|기존 패스에 새 점 추가|새 점을 만들 위치의 패스를 클릭합니다.|![기존 패스에 새 점 추가](../designers/media/b004ad5a-33a4-46ae-81c0-20be0d819332.png)<br /><br /> 펜 삽입 포인터|
|패스에서 점 제거|기존 점 위를 마우스로 가리키고 클릭합니다.|![경로에서 점 제거](../designers/media/08a64b78-f3df-4730-8169-c56b5631b071.png)<br /><br /> 펜 삭제 포인터|
|날카로운 모퉁이가 있는 패스 닫기|시작점을 클릭합니다.|![날카로운 모퉁이가 있는 패스 닫기](../designers/media/a12fd3b4-a553-4762-b01c-c35efa594362.png)<br /><br /> 펜 닫기 포인터|
|모퉁이에서 부드러운 곡선이 있는 패스 닫기|시작점을 클릭하고 마우스 단추를 손에서 떼기 전에 탄젠트 핸들을 끌어서 수정합니다.|![모퉁이에서 부드러운 곡선이 있는 패스 닫기](../designers/media/a12fd3b4-a553-4762-b01c-c35efa594362.png)<br /><br /> 펜 닫기 포인터|
|두 개의 패스를 연결할 때 날카로운 모퉁이 만들기|두 개의 경로를 선택하고 **펜** 도구를 클릭하고 패스 중 하나의 끝점을 클릭한 후 다른 패스의 끝점을 클릭합니다.|![두 개의 패스를 연결할 때 날카로운 모퉁이 만들기](../designers/media/bd12dfa4-112e-4f37-9765-3479e6b69894.png)<br /><br /> 펜 연결 포인터|
|두 개의 패스를 연결할 때 부드러운 모퉁이 만들기|두 개의 경로를 선택하고 **펜** 도구를 클릭하고 패스 중 하나의 끝점을 클릭한 후 다른 패스의 끝점을 끕니다.|![두 개의 패스를 연결할 때 부드러운 모퉁이 만들기](../designers/media/bd12dfa4-112e-4f37-9765-3479e6b69894.png)<br /><br /> 펜 연결 포인터|
|새 패스 만들기|**Ctrl** 키를 누른 채로 이전 패스의 외부 영역을 클릭하여 이전 패스에 점을 추가하는 것을 중지한 다음, 새 패스를 시작하려는 위치를 클릭하거나 이 위치로 끕니다.|![새 패스 만들기](../designers/media/69758176-5f53-465b-808c-f13fd1a0b3f2.png)<br /><br /> 펜 시작 포인터|

## <a name="see-also"></a>참고 항목

- [아트보드 보조 키](artboard-modifier-keys-in-blend.md)
- [직접 선택 도구 보조 키](direct-selection-tool-modifier-keys-in-blend.md)
- [도형 및 패스 그리기](draw-shapes-and-paths.md)