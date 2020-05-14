---
title: 빌드 구성 만들기 및 편집
description: 이 문서에서는 Mac용 Visual Studio에서의 빌드 구성 만들기에 대해 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.openlocfilehash: 26f6e25bfe1284fc31bcd484b905bf5d75c2ba15
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128431"
---
# <a name="creating-and-editing-build-configurations"></a>빌드 구성 만들기 및 편집

빌드 구성을 통해 빌드를 세부적으로 제어하여 다양한 테스트 및 배포 상황에 맞는 구성을 만들 수 있습니다. 개별 프로젝트 또는 솔루션 전체의 빌드 구성을 만들 수 있습니다.

프로젝트 옵션 대화 상자를 사용하여 프로젝트와 솔루션의 새 구성을 만들고 기존 구성을 편집할 수 있습니다.

>[!NOTE]
>이 토픽은 Mac용 Visual Studio에 적용됩니다. Windows용 Visual Studio의 경우 [방법: 구성 만들기 및 편집](/visualstudio/ide/how-to-create-and-edit-configurations)을 참조하세요.

## <a name="creating-a-project-build-configuration"></a>프로젝트 빌드 구성 만들기

프로젝트 빌드 구성을 만들려면 다음 단계를 수행합니다.

1. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **옵션**을 선택합니다. 프로젝트 노드를 두 번 클릭하여 프로젝트 옵션 대화 상자를 표시할 수도 있습니다.

2. 프로젝트 옵션 대화 상자에서 **빌드 > 구성**을 선택합니다.

    ![프로젝트 옵션의 구성 관리자](media/create-and-edit-configurations-image2.png)

3. **추가**를 선택하여 새 구성을 만듭니다. 기존 구성을 복사할 수도 있습니다.

구성을 만든 후에 프로젝트 옵션의 **빌드** 섹션을 사용하여 속성을 구성에 맞게 조정할 수 있습니다.

![빌드 옵션 구성](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>솔루션 빌드 구성 만들기

솔루션 빌드 구성을 만들려면 다음 단계를 수행합니다.

1. 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **옵션**을 선택합니다. 솔루션 노드를 두 번 클릭하여 솔루션 옵션 대화 상자를 표시할 수도 있습니다.

2. 솔루션 옵션 대화 상자에서 **빌드 > 구성**을 선택합니다.

    ![솔루션 옵션의 구성 관리자](media/create-and-edit-configurations-image1.png)

3. **추가**를 선택하여 새 구성을 만듭니다. 기존 구성을 복사할 수도 있습니다.

구성을 만든 후에 각 프로젝트에 대한 프로젝트 옵션 대화 상자의 **빌드** 섹션을 사용하여 속성을 구성에 맞게 조정할 수 있습니다.

![빌드 옵션 구성](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>빌드 구성 이름 바꾸기

구성의 이름을 바꾸려면 프로젝트 또는 솔루션 옵션의 **빌드 > 구성**으로 이동하여 구성 목록에서 구성을 선택합니다.

![구성 목록](media/create-and-edit-configurations-image4.png)

**이름 바꾸기** 단추를 선택합니다.

![이름 바꾸기 대화 상자](media/create-and-edit-configurations-image5.png)

**확인**을 클릭하여 확인합니다.

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>참조

- [빌드 구성 만들기 및 편집(Windows의 Visual Studio)](/visualstudio/ide/how-to-create-and-edit-configurations)