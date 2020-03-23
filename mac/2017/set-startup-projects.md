---
title: 여러 시작 프로젝트 설정
description: 이 문서에서는 실행 또는 디버그를 시작할 여러 프로젝트를 설정하는 방법을 설명합니다.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 55519960a6b84968ced43183833167a365e91b35
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68872319"
---
# <a name="set-multiple-startup-projects"></a>여러 시작 프로젝트 설정

Mac용 visual Studio를 사용하면 솔루션을 디버그하거나 실행할 때 둘 이상의 프로젝트를 시작해야 하도록 지정할 수 있습니다.

## <a name="to-set-multiple-startup-projects"></a>여러 시작 프로젝트를 설정하려면

1. Solution Pad에서 솔루션(최상위 노드)을 선택합니다.

2. 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트 설정**을 선택합니다.

   ![시작 프로젝트 설정 선택](media/startup-proj-ctx-menu.png)

3. **솔루션 실행 구성 만들기** 대화 상자가 열립니다. 이 대화 상자를 사용하여 솔루션에 대한 새 명명된 솔루션 실행 구성을 만들 수 있습니다. 원하는 이름을 임의로 사용할 수 있습니다. 기본 이름은 `Multiple Projects`입니다.

   ![솔루션 실행 구성 만들기 대화 상자](media/create-sln-run-config.png)

4. **실행 구성 만들기**를 선택합니다. **솔루션 옵션** 대화 상자가 열리고 새 솔루션 실행 구성이 선택됩니다.

   ![솔루션 옵션 대화 상자](media/sln-options-run-config-multi-projects.png)

5. Mac용 Visual Studio에서 앱을 디버그하거나 실행할 때 시작할 프로젝트를 선택합니다.

   ![선택한 프로젝트가 있는 솔루션 옵션 대화 상자](media/sln-options-run-config-multi-projects-configured.png)

6. **확인**을 선택합니다. 새 솔루션 실행 구성이 활성 실행 구성으로 설정됩니다.

   ![여러 프로젝트가 디버그 또는 실행 시 시작하도록 구성된 솔루션](media/startup-project-configured.png)

   두 프로젝트 모두 Solution Pad에서 **굵게** 표시되므로, 두 프로젝트가 시작하도록 구성된 것을 알 수 있습니다. 도구 모음에서 새 실행 구성이 현재 솔루션 실행 구성으로 설정되었습니다.

## <a name="next-steps"></a>다음 단계

- [Mac용 Visual Studio에서 컴파일 및 빌드](compiling-and-building.md)
- [빌드 구성 이해](configurations.md)
