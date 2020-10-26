---
title: '방법: 프로젝트 종속성 만들기 및 제거'
description: Visual Studio를 사용하여 다른 프로젝트의 코드에 대한 프로젝트 종속성을 만들고 제거할 수 있는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: how-to
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
ms.technology: vs-ide-compile
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b2a99e297b4ce7291c0dd94947155794cf8c3d4
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92137027"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>방법: 프로젝트 종속성 만들기 및 제거

여러 프로젝트가 포함된 솔루션을 빌드할 때 다른 프로젝트에서 사용되는 코드를 생성하기 위해 특정 프로젝트를 먼저 빌드해야 할 수 있습니다. 프로젝트가 다른 프로젝트에서 생성된 실행 코드를 사용하는 경우 코드를 생성하는 프로젝트는 코드를 사용하는 프로젝트의 프로젝트 종속성이라고 합니다. 해당 종속성 관계는 **프로젝트 종속성** 대화 상자에서 정의할 수 있습니다.

## <a name="to-assign-dependencies-to-projects"></a>프로젝트에 종속성을 할당하려면

1. **솔루션 탐색기** 에서 프로젝트를 선택합니다.

2. **프로젝트** 메뉴에서 **프로젝트 종속성** 을 선택합니다.

    **프로젝트 종속성** 대화 상자가 열립니다.

   > [!NOTE]
   > **프로젝트 종속성** 옵션은 프로젝트가 두 개 이상 포함된 솔루션에서만 사용할 수 있습니다.

3. **종속성** 탭의 **프로젝트** 드롭다운 메뉴에서 프로젝트를 선택합니다.

4. **다음에 종속** 필드에서 이 프로젝트를 빌드하기 전에 빌드해야 하는 다른 프로젝트의 확인란을 선택합니다.

   프로젝트 종속성을 만들기 전에 솔루션이 두 개 이상의 프로젝트로 구성되어 있어야 합니다.

## <a name="to-remove-dependencies-from-projects"></a>프로젝트에서 종속성을 제거하려면

1. **솔루션 탐색기** 에서 프로젝트를 선택합니다.

2. **프로젝트** 메뉴에서 **프로젝트 종속성** 을 선택합니다.

     **프로젝트 종속성** 대화 상자가 열립니다.

    > [!NOTE]
    > **프로젝트 종속성** 옵션은 프로젝트가 두 개 이상 포함된 솔루션에서만 사용할 수 있습니다.

3. **종속성** 탭의 **프로젝트** 드롭다운 메뉴에서 프로젝트를 선택합니다.

4. **다음에 종속** 필드에서 더 이상 이 프로젝트의 종속성이 아닌 모든 다른 프로젝트 옆의 확인란을 선택 취소합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 프로젝트 및 솔루션 빌드 및 정리](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)
- [빌드 구성 이해](../ide/understanding-build-configurations.md)
- [프로젝트 및 솔루션 속성 관리](managing-project-and-solution-properties.md)
