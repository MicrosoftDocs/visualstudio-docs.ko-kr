---
title: 모델링 솔루션 구조화 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83c8d8e7a1afe0946c1b1f5eb25c8650e2b512f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917321"
---
# <a name="structure-your-modeling-solution"></a>모델링 솔루션 구성

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

개발 프로젝트에서 모델을 효과적으로 사용하려면 팀 멤버가 프로젝트의 다른 파트 모델에서 동시에 작업할 수 있어야 합니다. 이 항목에서는 전체 레이어 다이어그램의 레이어에 해당하는 여러 파트로 애플리케이션을 나누는 체계를 제안합니다.

프로젝트 또는 하위 프로젝트에서 신속하게 시작하려면 선택한 프로젝트 구조를 따르는 프로젝트 템플릿을 사용하는 것이 유용합니다. 이 항목에서는 이러한 템플릿을 만들고 사용하는 방법을 설명합니다.

이 항목에서는 여러 팀 멤버는 물론 여러 팀이 필요할 만큼 큰 프로젝트에서 작업 중이라고 가정합니다. 프로젝트의 코드와 모델은 [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]와 같은 소스 제어 시스템에 저장됩니다. 적어도 일부 팀 멤버는 Visual Studio를 사용하여 모델을 개발하고, 다른 팀 멤버는 다른 Visual Studio 버전을 사용하여 모델을 볼 수 있습니다.

각 도구 및 모델링 기능을 지 원하는 Visual Studio 버전을 확인 하려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조 하세요.

## <a name="solution-structure"></a>솔루션 구조

중간 규모 또는 대규모 프로젝트에서 팀의 구조는 애플리케이션 구조를 기반으로 합니다. 각 팀이 Visual Studio 솔루션을 사용합니다.

#### <a name="to-divide-an-application-into-layers"></a>애플리케이션을 레이어로 나누려면

1. 웹 애플리케이션, 서비스 애플리케이션 또는 데스크톱 애플리케이션과 같은 애플리케이션 구조에 따라 솔루션 구조를 지정합니다. 다양 한 공통 아키텍처는 [Microsoft 응용 프로그램 아키텍처 가이드의 Application archetype](/previous-versions/msp-n-p/ee658107(v=pandp.10))에 설명 되어 있습니다.

2. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션을 만들고 아키텍처 솔루션이라고 부릅니다. 이 솔루션은 시스템의 전반적인 디자인을 만드는 데 사용됩니다. 모델을 포함하지만 코드는 포함하지 않습니다.

    이 솔루션에 레이어 다이어그램을 추가합니다. 레이어 다이어그램에서 애플리케이션에 대해 선택한 아키텍처를 그립니다. 예를 들어 다이어그램에 프레젠테이션; 비즈니스 논리 및 데이터 레이어와 레이어 간의 종속성이 표시될 수 있습니다.

    **아키텍처** 메뉴에서 **새 UML 또는 레이어 다이어그램** 명령을 사용 하 여 레이어 다이어그램 및 새 Visual Studio 솔루션을 동시에 만들 수 있습니다.

3. 중요한 비즈니스 개념을 나타내는 UML 다이어그램 및 모든 레이어의 디자인에서 참조되는 사용 사례를 아키텍처 모델에 추가합니다.

4. 아키텍처 레이어 다이어그램의 각 레이어에 대해 별도의 Visual Studio 솔루션을 만듭니다.

    이러한 솔루션은 레이어의 코드를 개발하는 데 사용됩니다.

5. 레이어의 디자인을 나타내는 UML 모델 및 모든 레이어에 공통적으로 적용되는 개념을 만듭니다. 아키텍처 솔루션에서 모든 모델을 볼 수 있고 각 레이어에서 관련 모델을 볼 수 있도록 모델을 정렬합니다.

    다음 절차 중 하나를 사용하여 이 작업을 수행할 수 있습니다. 첫 번째 대안은 각 레이어에 대해 별도의 모델링 프로젝트를 만드는 것이고, 두 번째 대안은 레이어 간에 공유되는 단일 모델링 프로젝트를 만드는 것입니다.

###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>각 레이어에 대해 별도의 모델링 프로젝트를 사용하려면

1. 각 레이어 솔루션에서 모델링 프로젝트를 만듭니다.

    이 모델에는 해당 레이어의 요구 사항과 디자인을 설명하는 UML 다이어그램이 포함됩니다. 중첩된 레이어를 표시하는 레이어 다이어그램이 포함될 수도 있습니다.

    이제 각 레이어에 대한 모델과 애플리케이션 아키텍처에 대한 모델이 만들어졌습니다. 각 모델은 자체 솔루션에 포함됩니다. 이렇게 하면 팀 멤버가 레이어에서 동시에 작업할 수 있습니다.

2. 아키텍처 솔루션을 사용하려면 각 레이어 솔루션의 모델링 프로젝트를 추가합니다. 이 작업을 수행하려면 아키텍처 솔루션을 엽니다. 솔루션 탐색기에서 솔루션 노드를 마우스 오른쪽 단추로 클릭 하 고 추가를 가리킨 다음 **기존 프로젝트**를 클릭 합니다. 한 레이어 솔루션의 모델링 프로젝트(.modelproj)로 이동합니다.

    이제 각 모델에 두 개의 솔루션, 즉 "홈" 솔루션과 아키텍처 솔루션이 표시됩니다.

3. 각 레이어의 모델링 프로젝트에 레이어 다이어그램을 추가합니다. 아키텍처 레이어 다이어그램의 복사본으로 시작합니다. 레이어 다이어그램의 종속성이 아닌 파트를 삭제할 수 있습니다.

    이 레이어의 자세한 구조를 나타내는 레이어 다이어그램을 추가할 수도 있습니다.

    이러한 다이어그램은 이 레이어에서 개발된 코드의 유효성을 검사하는 데 사용됩니다.

4. 아키텍처 솔루션에서 Visual Studio를 사용하여 모든 레이어의 요구 사항 및 디자인 모델을 편집합니다.

    각 레이어 솔루션에서 모델을 참조하여 해당 레이어에 대한 코드를 개발합니다. 동일한 컴퓨터를 사용하여 모델을 업데이트하지 않고 개발하는 데 만족하는 경우 모델을 만들 수 없는 Visual Studio 버전을 사용하여 모델을 읽고 코드를 개발할 수 있습니다. 이러한 버전의 모델에서 코드를 생성할 수도 있습니다.

    이 메서드는 동시에 레이어 모델을 편집하는 개발자에 의해 간섭이 발생하지 않도록 합니다.

    그러나 모델이 분리되어 있으므로 공통 개념을 참조하기 어렵습니다. 각 모델에 다른 레이어 및 아키텍처에서 종속된 요소의 자체 복사본이 있어야 합니다. 각 레이어의 레이어 다이어그램을 아키텍처 레이어 다이어그램과 동기화된 상태로 유지해야 합니다. 이 작업을 수행하는 도구를 개발할 수는 있지만 이러한 요소가 변경되는 경우 동기화를 유지하기 어렵습니다.

###### <a name="to-use-a-separate-package-for-each-layer"></a>각 레이어에 대해 별도의 패키지를 사용하려면

1. 각 레이어에 대한 솔루션에서 아키텍처 모델링 프로젝트를 추가합니다. 솔루션 탐색기에서 솔루션 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **기존 프로젝트**를 클릭 합니다. 이제 모든 솔루션에서 아키텍처 프로젝트 및 각 레이어에 대한 개발 프로젝트인 단일 모델링 프로젝트에 액세스할 수 있습니다.

2. 공유 UML 모델에서 각 레이어에 대한 패키지를 만듭니다. 솔루션 탐색기에서 모델링 프로젝트를 선택합니다. UML 모델 탐색기에서 모델 루트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **패키지**를 클릭 합니다.

    각 패키지에는 해당 레이어의 요구 사항과 디자인을 설명하는 UML 다이어그램이 포함됩니다.

3. 필요한 경우 각 레이어의 내부 구조에 대한 로컬 레이어 다이어그램을 추가합니다.

    이 메서드를 사용하면 각 레이어의 디자인 요소가 레이어 및 해당 레이어가 종속된 공통 아키텍처의 디자인 요소를 직접 참조할 수 있습니다.

    서로 다른 패키지의 동시 작업으로 인해 일부 충돌이 발생할 수는 있지만 패키지가 별도의 파일에 저장되기 때문에 관리가 비교적 용이합니다. 중요한 문제는 종속 패키지에서 참조된 요소 삭제에 의해 발생합니다. 자세한 내용은 [버전 제어에서 모델 및 다이어그램 관리](../modeling/manage-models-and-diagrams-under-version-control.md)를 참조 하세요.

## <a name="creating-architecture-templates"></a>아키텍처 템플릿 만들기

실제로 동시에 모든 Visual Studio 솔루션을 만드는 것이 아니라 프로젝트가 진행됨에 따라 추가합니다. 이후 프로젝트에서 동일한 솔루션 구조를 사용하는 경우도 있습니다.  새 솔루션을 신속하게 만들 수 있도록 솔루션 또는 프로젝트 템플릿을 만들 수 있습니다. 다른 컴퓨터에 쉽게 배포하고 설치할 수 있도록 템플릿을 VSIX(Visual Studio Integration Extension)에 캡처할 수 있습니다.

예를 들어 프레젠테이션, 비즈니스 및 데이터 레이어를 포함하는 솔루션을 자주 사용하는 경우 해당 구조가 포함된 새 솔루션을 만드는 템플릿을 구성할 수 있습니다.

#### <a name="to-create-a-solution-template"></a>솔루션 템플릿을 만들려면

1. 아직 수행 하지 않은 경우 [템플릿 내보내기 마법사를 다운로드 하 여 설치](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard)합니다.

2. 이후 프로젝트의 시작점으로 사용할 솔루션 구조를 만듭니다.

3. **파일** 메뉴에서 **VSIX로 템플릿 내보내기**를 클릭합니다. **VSIX로 템플릿 내보내기 마법사** 가 열립니다.

4. 마법사의 지침에 따라 템플릿에 포함할 프로젝트를 선택하고, 템플릿의 이름 및 설명을 제공하고, 출력 위치를 지정합니다.

> [!NOTE]
> 이 항목의 자료는 MVP(Most Valued Professional), Microsoft 서비스 및 Visual Studio 제품 팀과 작성자기 공동으로 작업한, Visual Studio ALM Rangers에서 작성된 Visual Studio 아키텍처 도구 사용 지침을 요약하고 쉽게 설명한 것입니다. [전체 지침 패키지를 다운로드 하려면 여기를 클릭 하세요.](https://archive.codeplex.com/?p=vsarchitectureguide)

## <a name="related-materials"></a>관련 자료

[모델 구성 및 관리](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models) -Clint Edmondson 비디오

[Visual Studio 아키텍처 도구 지침](../modeling/visual-studio-architecture-tooling-guidance.md) -팀에서 모델을 관리 하는 방법에 대 한 추가 지침

## <a name="see-also"></a>관련 항목

[버전 제어](../modeling/manage-models-and-diagrams-under-version-control.md) 
 에서 모델 및 다이어그램 관리 [개발 프로세스에서 모델 사용](../modeling/use-models-in-your-development-process.md)
