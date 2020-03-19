---
title: 빌드 구성 이해
ms.date: 01/20/2020
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a37d4fa5dc92253b94dc64590c9df5fec7703ceb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904167"
---
# <a name="understand-build-configurations"></a>빌드 구성 이해

다른 설정으로 프로젝트를 빌드해야 하는 경우 빌드 구성이 필요합니다. **디버그** 및 **릴리스** 구성이 그 예시이며 이에 따라 빌드 시 다른 컴파일러 옵션이 사용됩니다.  활성 상태인 구성 하나가 IDE 상단의 명령 모음에 표시됩니다.

![활성 구성](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio에서 구성 빌드](/visualstudio/mac/configurations)를 참조하세요.

빌드된 출력 파일이 저장되는 구성 및 플랫폼 컨트롤입니다. 일반적으로 Visual Studio가 프로젝트를 빌드하면 출력 위치는 활성 구성으로 이름이 지정된 프로젝트 하위 폴더지만(예: *bin/Debug/x86*) 이는 변경할 수 있습니다.

솔루션 및 프로젝트 수준에서 고유한 빌드 구성을 만들 수 있습니다. 솔루션 구성은 이 구성이 활성화 상태일 때 빌드에 포함할 프로젝트를 결정합니다. 활성 솔루션 구성에 지정된 프로젝트만 빌드됩니다. 구성 관리자에서 여러 대상 플랫폼을 선택하면 해당 플랫폼에 적용되는 모든 프로젝트가 빌드됩니다. 프로젝트 구성은 프로젝트를 빌드할 때 사용할 빌드 설정과 컴파일러 옵션을 결정합니다.

구성을 만들거나, 선택하거나, 수정하거나, 삭제하려면 **구성 관리자**를 사용합니다. 구성 관리자를 열려면 메뉴 모음에서 **빌드** > **구성 관리자**를 선택하거나 검색 상자에 **구성**을 입력합니다. **표준** 도구 모음에서 **솔루션 구성** 목록을 사용하여 구성을 선택하거나 **구성 관리자**를 열 수도 있습니다.

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> 도구 모음에서 솔루션 구성 설정을 찾을 수 없고 **구성 관리자**에 액세스할 수 없으면 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 개발 설정을 적용할 수 있습니다. 자세한 내용은 [방법: Visual Basic 개발자 설정을 적용하여 구성 관리](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md)를 참조하세요.

기본적으로 **디버그** 및 **릴리스** 구성은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 템플릿을 사용하여 만든 프로젝트에 포함됩니다. **디버그** 구성은 앱의 디버깅을 지원하고 **릴리스** 구성은 배포할 수 있는 앱 버전을 빌드합니다. 자세한 내용은 [방법: 디버그 및 릴리스 구성 설정](../debugger/how-to-set-debug-and-release-configurations.md)을 참조하세요. 사용자 지정 솔루션 구성 및 프로젝트 구성을 만들 수도 있습니다. 자세한 내용은 [방법: 구성 만들기 및 편집](../ide/how-to-create-and-edit-configurations.md)을 참조하세요.

## <a name="solution-configurations"></a>솔루션 구성

솔루션 구성은 솔루션에 있는 프로젝트를 빌드하고 배포하는 데 사용할 방법을 지정합니다. 솔루션 구성을 수정하거나 새 구성을 정의하려면 **구성 관리자**의 **활성 솔루션 구성**에서 **편집** 또는 **새로 만들기**를 선택합니다.

솔루션 구성에서 **프로젝트 컨텍스트** 상자의 각 항목은 솔루션에 있는 프로젝트를 나타냅니다. **활성 솔루션 구성** 및 **활성 솔루션 플랫폼**의 모든 조합에 대해 각 프로젝트가 사용되는 방법을 설정할 수 있습니다. (솔루션 플랫폼에 대한 자세한 내용은 [빌드 플랫폼 이해](../ide/understanding-build-platforms.md)를 참조하세요.)

새 솔루션 구성을 정의하고 **새 프로젝트 구성 만들기** 확인란을 선택하면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 모든 프로젝트에 새 구성이 자동으로 할당됩니다. 마찬가지로, 새 솔루션 플랫폼을 정의하고 **새 프로젝트 플랫폼 만들기** 확인란을 선택하면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 에서 모든 프로젝트에 새 플랫폼이 자동으로 할당됩니다. 또한 새 플랫폼을 대상으로 하는 프로젝트를 추가하면 Visual Studio에서 해당 플랫폼이 솔루션 플랫폼 목록에 추가되고 모든 프로젝트에 할당됩니다. 각 프로젝트에 대한 설정은 여전히 수정할 수 있습니다.

활성 솔루션 구성도 IDE에 컨텍스트를 제공합니다. 예를 들어 프로젝트 작업을 진행 중인데 이 프로젝트가 모바일 디바이스용으로 빌드될 것이라고 구성에 지정되어 있으면, 모바일 디바이스 프로젝트에 사용할 수 있는 항목만 **도구 상자**에 표시됩니다.

## <a name="project-configurations"></a>프로젝트 구성

빌드 시 사용할 빌드 설정과 컴파일러 옵션을 지정할 때는 프로젝트가 대상으로 하는 구성과 플랫폼이 함께 사용됩니다. 프로젝트에서는 각 구성 및 플랫폼 조합에 대해 서로 다른 설정을 지정할 수 있습니다. 프로젝트 속성을 수정하려면 **솔루션 탐색기**에서 프로젝트의 바로 가기 메뉴를 열고 **속성**을 선택합니다.  프로젝트 디자이너의 **빌드** 탭 상단에서 활성 구성을 선택해 빌드 설정을 수정합니다.

![프로젝트 디자이너 구성](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>여러 구성 빌드

**빌드** > **솔루션 빌드** 명령을 사용하여 솔루션을 빌드하면 Visual Studio는 활성 구성만 빌드합니다. 해당 솔루션 구성에 지정된 모든 프로젝트가 빌드되고, 빌드된 프로젝트 구성만 활성 솔루션 구성 및 활성 솔루션 플랫폼에 지정된 구성으로, Visual Studio의 도구 모음에 표시됩니다. 예를 들어 **Debug**와 **x86**이 표시됩니다. 정의된 다른 구성과 플랫폼은 빌드되지 않습니다.

하나의 작업에서 여러 구성 및 플랫폼을 빌드하려는 경우 Visual Studio에서 **빌드** > **일괄 빌드** 옵션을 사용할 수 있습니다. 이 기능에 액세스하려면 **Ctrl**+**Q**를 눌러 검색 상자를 열고 `Batch build`를 입력합니다. 일부 프로젝트 형식에는 일괄 빌드를 사용할 수 없습니다. [방법: 여러 구성 동시 빌드](how-to-build-multiple-configurations-simultaneously.md)를 참조하세요.

## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio가 프로젝트 구성을 할당하는 방법

새 솔루션 구성을 정의하고 기존 구성에서 설정을 복사하지 않으면 Visual Studio가 다음 기준을 사용하여 기본 프로젝트 구성을 할당합니다. 기준은 표시된 순서대로 평가됩니다.

1. 프로젝트에 새 솔루션 구성의 이름과 정확히 일치하는 구성 이름( *\<구성 이름> \<플랫폼 이름>* )이 있으면 해당 구성이 할당됩니다. 구성 이름은 대/소문자를 구분하지 않습니다.

1. 프로젝트에 구성 이름 부분이 새 솔루션 구성과 일치하는 구성 이름이 지정되어 있으면 플랫폼 부분이 일치하는지 여부와 관계없이 해당 구성이 할당됩니다.

1. 일치하는 부분이 없으면 프로젝트에 나열된 첫 번째 구성이 할당됩니다.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Visual Studio가 솔루션 구성을 할당하는 방법

프로젝트 구성을 만들고(**구성 관리자**에서 해당 프로젝트의 **구성** 열에 있는 드롭다운 메뉴의 **새로 만들기** 선택) **새 솔루션 구성 만들기** 확인란을 선택하면 Visual Studio가 각 지원 플랫폼에서 프로젝트를 빌드하기 위해 이름이 같은 솔루션 구성을 찾습니다. 경우에 따라 Visual Studio는 기존 솔루션 구성의 이름을 바꾸거나 새 구성을 정의합니다.

Visual Studio는 다음 기준을 사용하여 솔루션 구성을 할당합니다.

- 프로젝트 구성이 플랫폼을 지정하지 않거나 하나의 플랫폼만 지정하는 경우 새 프로젝트 구성과 이름이 일치하는 솔루션 구성이 검색되거나 추가됩니다. 이 솔루션 구성의 기본 이름은 플랫폼 이름을 포함하지 않으며 *\<<프로젝트 구성 이름>* 양식을 사용합니다.

- 프로젝트가 여러 플랫폼을 지원하는 경우 지원되는 각 플랫폼에 대해 솔루션 구성이 검색되거나 추가됩니다. 각 솔루션 구성의 이름은 프로젝트 구성 이름과 플랫폼 이름을 모두 포함하며 *\<프로젝트 구성 이름> \<플랫폼 이름>* 양식입니다.

## <a name="see-also"></a>참조

- [연습: 애플리케이션 빌드](../ide/walkthrough-building-an-application.md)
- [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)
- [솔루션 및 프로젝트](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++ 빌드 참조](/cpp/build/reference/c-cpp-building-reference)
- [빌드 플랫폼 이해](understanding-build-platforms.md)
- [빌드 구성(Mac용 Visual Studio)](/visualstudio/mac/configurations)
