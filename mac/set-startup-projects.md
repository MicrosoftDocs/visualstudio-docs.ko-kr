---
title: 여러 시작 프로젝트 설정
description: 이 문서에서는 실행 또는 디버그를 시작할 여러 프로젝트를 설정하는 방법을 설명합니다.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: df1e088a5e2d0f65d8b72dad0895f1edb1740f1f
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493571"
---
# <a name="set-multiple-startup-projects"></a>여러 시작 프로젝트 설정

Mac용 visual Studio를 사용하면 솔루션을 디버그하거나 실행할 때 둘 이상의 프로젝트를 시작해야 하도록 지정할 수 있습니다.

## <a name="to-set-multiple-startup-projects"></a>여러 시작 프로젝트를 설정하려면

1. 솔루션 창에서 솔루션(최상위 노드)을 선택합니다.

2. 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트 설정** 을 선택합니다.

   ![시작 프로젝트 설정 선택](media/startup-proj-ctx-menu.png)

3. **솔루션 실행 구성 만들기** 대화 상자가 열립니다. 이 대화 상자를 사용하여 솔루션에 대한 새 명명된 솔루션 실행 구성을 만들 수 있습니다. 원하는 이름을 임의로 사용할 수 있습니다. 기본 이름은 `Multiple Projects`입니다.

   ![솔루션 실행 구성 만들기 대화 상자](media/create-sln-run-config.png)

4. **실행 구성 만들기** 를 선택합니다. **솔루션 옵션** 대화 상자가 열리고 새 솔루션 실행 구성이 선택됩니다.

   ![솔루션 옵션 대화 상자](media/sln-options-run-config-multi-projects.png)

5. Mac용 Visual Studio에서 앱을 디버그하거나 실행할 때 시작할 프로젝트를 선택합니다.

   ![선택한 프로젝트가 있는 솔루션 옵션 대화 상자](media/sln-options-run-config-multi-projects-configured.png)

6. **확인** 을 선택합니다. 새 솔루션 실행 구성이 활성 실행 구성으로 설정됩니다.

   ![여러 프로젝트가 디버그 또는 실행 시 시작하도록 구성된 솔루션](media/startup-project-configured.png)

   이제 두 프로젝트가 시작하도록 구성되었습니다. 따라서 두 프로젝트가 솔루션 창에 **굵게** 표시되어 나타납니다. 도구 모음에서 새 실행 구성이 현재 솔루션 실행 구성으로 설정되었습니다.

## <a name="next-steps"></a>다음 단계

- [Mac용 Visual Studio에서 컴파일 및 빌드](compiling-and-building.md)
- [빌드 구성 이해](configurations.md)
