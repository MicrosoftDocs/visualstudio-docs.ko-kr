---
title: 프로젝트와 솔루션 빌드 및 정리
description: 이 문서에서는 Mac용 Visual Studio에서 프로젝트를 빌드하는 방법을 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128451"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>프로젝트와 솔루션 빌드 및 정리

이 문서의 단계를 수행하여 솔루션의 전체 또는 일부 프로젝트를 빌드, 다시 빌드 또는 정리하는 방법을 알아봅니다.

> [!NOTE]
> 이 토픽은 Mac용 Visual Studio에 적용됩니다. Windows용 Visual Studio의 경우 [Visual Studio에서 프로젝트와 솔루션 빌드 및 정리](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)를 참조하세요.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>전체 솔루션을 빌드, 다시 빌드 또는 정리하려면

1. **Solution Pad**에서 솔루션 노드를 선택합니다.

    ![솔루션 노드 선택](media/compiling-and-building-image1.png)

2. 메뉴 모음에서 **빌드** 메뉴를 선택하고 다음 옵션 중 하나를 선택합니다.

    ![모든 메뉴 항목 빌드 선택](media/compiling-and-building-image2.png)

    * 프로젝트 내에서 가장 최근 빌드 이후에 변경된 파일과 구성 요소를 컴파일하려면 **모두 빌드**를 선택합니다.

    * 솔루션을 “정리”하고 모든 프로젝트 파일과 구성 요소를 빌드하려면 **모두 다시 빌드**를 선택합니다.

    * 중간 파일과 출력 파일을 모두 삭제하려면 **모두 정리**를 선택합니다. 그런 다음 프로젝트 및 구성 요소 파일만 유지하여 중간 파일과 출력 파일의 새 인스턴스를 빌드할 수 있습니다.

## <a name="to-build-or-rebuild-a-single-project"></a>단일 프로젝트를 빌드 또는 다시 빌드하려면

1. **Solution Pad**에서 프로젝트를 선택합니다.

2. 메뉴 모음에서 **빌드** 메뉴를 선택합니다.

3. 빌드[ProjectName], 다시 빌드[ProjectName] 또는 정리[ProjectName] 중 하나를 선택합니다.

## <a name="to-stop-a-build"></a>빌드를 중지하려면

빌드를 중지하려면 다음 옵션 중 하나를 사용합니다.

* 통지 영역에서 빨간색 사각형을 누릅니다.

    ![빨간색 사각형을 눌러 빌드 중지](media/compiling-and-building-image3.png)

* **빌드** 메뉴의 **중지** 항목을 사용합니다.

* **Cmd+Shift+Return**을 누릅니다.

## <a name="see-also"></a>참고 항목

- [프로젝트와 솔루션 빌드 및 정리(Windows의 Visual Studio)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)