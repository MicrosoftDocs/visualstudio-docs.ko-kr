---
title: '방법: 여러 플랫폼을 대상으로 한 프로젝트 구성'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0618d571258817b5e9653a38a7801c2e4d14e687
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284570"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>방법: 여러 플랫폼을 대상으로 한 프로젝트 구성

Visual Studio에서는 솔루션에서 다양한 CPU 아키텍처 또는 플랫폼을 한 번에 대상으로 지정할 수 있습니다. 이를 설정하는 속성은 **Configuration Manager** 대화 상자를 통해 액세스합니다.

## <a name="target-a-platform"></a>대상 플랫폼 지정

**Configuration Manager** 대화 상자를 사용하면 솔루션 수준 및 프로젝트 수준 구성 및 플랫폼을 만들고 설정할 수 있습니다. 솔루션 수준 구성과 대상의 각 조합에는 이와 관련된 고유한 속성 집합이 포함될 수 있으므로 예를 들어 [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] 플랫폼을 대상으로 하는 릴리스 구성, x86 플랫폼을 대상으로 하는 릴리스 구성, x86 플랫폼을 대상으로 하는 디버그 구성 간에 쉽게 전환할 수 있습니다.

1. **빌드** 메뉴에서 **Configuration Manager**를 클릭합니다.

2. **활성 솔루션 플랫폼 상자**에서 솔루션의 대상이 될 플랫폼을 선택하거나 **\<New>** 를 선택하여 새 플랫폼을 만듭니다. Visual Studio는 애플리케이션을 컴파일하여 **구성 관리자** 대화 상자에서 활성 플랫폼으로 설정된 플랫폼을 대상으로 지정합니다.

## <a name="remove-a-platform"></a>플랫폼 제거

플랫폼에 대한 요구가 없다고 생각되면 **Configuration Manager** 대화 상자를 사용하여 제거할 수 있습니다. 그러면 구성 및 대상 조합에 대해 구성한 모든 솔루션 및 프로젝트 설정이 제거됩니다.

1. **빌드** 메뉴에서 **Configuration Manager**를 클릭합니다.

2. **활성 솔루션 플랫폼 상자**에서 **\<Edit>** 을 선택합니다. **솔루션 플랫폼 편집** 대화 상자가 열립니다.

3. 제거하려는 플랫폼을 클릭하고 **제거**를 클릭합니다.

## <a name="target-multiple-platforms-with-one-solution"></a>한 솔루션으로 여러 플랫폼 대상 지정

구성 및 플랫폼 설정 조합을 기반으로 설정을 변경할 수 있기 때문에 둘 이상의 플랫폼을 대상으로 지정할 수 있는 솔루션을 설정할 수 있습니다.

### <a name="to-target-multiple-platforms"></a>여러 플랫폼을 대상으로 지정하려면

1. **Configuration Manager**를 사용하여 솔루션에 대해 두 개 이상의 대상 플랫폼을 추가합니다.

2. **활성 솔루션 플랫폼** 목록에서 대상으로 지정할 플랫폼을 선택합니다.

3. 솔루션을 빌드합니다.

### <a name="to-build-multiple-solution-configurations-at-once"></a>한 번에 여러 솔루션 구성을 빌드하려면

1. **Configuration Manager**를 사용하여 솔루션에 대해 두 개 이상의 대상 플랫폼을 추가합니다.

2. **일괄 빌드** 창을 사용하여 한 번에 여러 솔루션 구성을 빌드합니다.

   예를 들어 솔루션 수준 플랫폼을 [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)](으)로 설정하고 동일한 플랫폼을 대상으로 하는 솔루션 내에 프로젝트가 없도록 할 수 있습니다. 사용자 솔루션에는 각각 다른 플랫폼을 대상으로 하는 여러 프로젝트를 포함할 수 있습니다. 이러한 상황 중 하나가 발생하면 혼동을 피하기 위해 설명적인 이름으로 새 구성을 만드는 것이 좋습니다.

## <a name="see-also"></a>참조

- [방법: 구성 만들기 및 편집](../ide/how-to-create-and-edit-configurations.md)
- [빌드 구성 이해](../ide/understanding-build-configurations.md)
- [Visual Studio에서 프로젝트 및 솔루션 빌드 및 정리](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
