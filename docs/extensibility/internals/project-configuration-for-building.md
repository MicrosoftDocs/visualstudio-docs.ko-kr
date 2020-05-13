---
title: 건축을 위한 프로젝트 구성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706738"
---
# <a name="project-configuration-for-building"></a>빌드를 위한 프로젝트 구성
지정된 솔루션의 솔루션 구성 목록은 솔루션 구성 대화 상자에서 관리합니다.

 사용자는 고유한 이름을 가진 추가 솔루션 구성을 만들 수 있습니다. 사용자가 새 솔루션 구성을 만들 면 IDE는 프로젝트의 해당 구성 이름으로 기본값또는 해당 이름이 없는 경우 디버그합니다. 필요한 경우 특정 요구 사항을 충족하도록 선택 영역을 변경할 수 있습니다. 이 동작의 유일한 예외는 프로젝트가 새 솔루션 구성의 이름과 일치하는 구성을 지원하는 경우입니다. 예를 들어 솔루션에 Project1 및 Project2가 포함되어 있다고 가정합니다. Project1에는 프로젝트 구성디버그, 소매 및 MyConfig1이 있습니다. Project2에는 프로젝트 구성디버그, 소매 및 MyConfig2가 있습니다.

 사용자가 MyConfig2라는 새 솔루션 구성을 만드는 경우 Project1은 기본적으로 디버그 구성을 솔루션 구성에 바인딩합니다. 또한 Project2는 기본적으로 MyConfig2 구성을 솔루션 구성에 바인딩합니다.

> [!NOTE]
> 바인딩은 대/소문자를 구분하지 않습니다.

 사용자가 구성 드롭다운 목록에서 **여러 선택** 항목을 선택하면 사용 가능한 구성 목록을 제공하는 대화 상자가 환경에 표시됩니다.

 ![여러 구성](../../extensibility/internals/media/vsmultiplecfgs.gif "vs멀티플Cfgs") 여러 구성

 이 대화 상자 내에서 사용자는 하나 또는 여러 구성을 선택할 수 있습니다. 속성 페이지 대화 상자에 표시되는 속성 값은 선택한 구성에 대한 값의 교차를 반영합니다.

 솔루션 및 프로젝트에 대한 구성 추가 및 이름 바꾸기와 관련된 정보는 솔루션 [구성을](../../extensibility/internals/solution-configuration.md) 참조하십시오.

 프로젝트 종속성 및 빌드 순서는 솔루션 구성에 독립적입니다. 솔루션 또는 프로젝트를 마우스 오른쪽 단추로 클릭하고 **프로젝트 종속성** 또는 **프로젝트 빌드 순서** 옵션을 선택하면 프로젝트 **종속성** 대화 상자가 열립니다. **프로젝트** 메뉴에서 열 수도 있습니다.

 ![프로젝트 종속성](../../extensibility/internals/media/vsprojdependencies.gif "vs프로이의존도") 프로젝트 종속성

 프로젝트 종속성은 프로젝트가 빌드되는 순서를 결정합니다. 대화 상자의 주문 빌드 탭을 사용하여 솔루션 내의 프로젝트가 빌드할 정확한 순서를 확인하고 종속성 탭을 사용하여 빌드 순서를 수정합니다.

> [!NOTE]
> 선택된 확인란이 있지만 흐리게 표시되는 목록의 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 인터페이스에서 지정한 명시적 종속성으로 인해 환경에 의해 추가되었으며 변경할 수 없습니다. 예를 들어 프로젝트에서 다른 프로젝트에 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트 참조를 추가하면 참조를 삭제해야만 제거할 수 있는 빌드 종속성이 자동으로 추가됩니다. 확인란이 명확하고 흐리게 표시되는 프로젝트는 종속성 루프를 만들기 때문에 선택할 수 없습니다(예: Project1은 Project2에 종속되고 Project2는 Project1에 종속됨) 빌드가 지연됩니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]빌드 프로세스에는 단일 Build 명령으로 호출되는 일반적인 컴파일 및 링크 작업이 포함됩니다. 이전 빌드에서 모든 출력 항목을 삭제하는 정리 작업과 구성의 출력 항목이 변경되었는지 확인하는 최신 검사 등 두 가지 다른 빌드 프로세스를 지원할 수도 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>개체는 빌드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 프로세스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>관리하기 위해 해당(반환됨)를 반환합니다. 빌드 작업이 발생하는 동안 빌드 작업의 상태를 보고하기 위해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>구성은 환경이 구현한 인터페이스 및 빌드 상태 이벤트에 관심이 있는 다른 개체에 대해 호출합니다.

 빌드된 후에는 구성 설정을 사용하여 디버거의 제어하에 실행할 수 있는지 여부를 결정할 수 있습니다. 구성은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 디버깅을 지원하기 위해 구현됩니다.

 프로젝트 종속성을 구현한 후 자동화 모델을 통해 종속성을 프로그래밍 방식으로 조작할 수 있습니다. 자동화 <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> 모델에서 호출합니다. 솔루션 빌드 관리자 구성 및 해당 속성을 직접 조작할 수 있는 사용 가능한 VSIP API 수준 인터페이스가 없습니다.

 또한 프로젝트 종속성 창에서 그리드를 제공할 수 있습니다. 자세한 내용은 [속성 표시 그리드](../../extensibility/internals/properties-display-grid.md)를 참조하십시오.

## <a name="see-also"></a>참조
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [배포 관리를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)
