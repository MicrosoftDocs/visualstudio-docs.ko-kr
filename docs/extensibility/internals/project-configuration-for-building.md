---
title: 빌드 | 대한 프로젝트 구성 Microsoft Docs
description: 새 프로젝트 형식의 솔루션 구성 대화 상자에서 특정 솔루션에 대한 솔루션 구성 목록을 관리하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf98698d3527220c4bc25cdf36132f0088ae4ea7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899929"
---
# <a name="project-configuration-for-building"></a>빌드를 위한 프로젝트 구성
지정된 솔루션에 대한 솔루션 구성 목록은 솔루션 구성 대화 상자에서 관리됩니다.

 사용자는 각각 고유한 이름을 가진 추가 솔루션 구성을 만들 수 있습니다. 사용자가 새 솔루션 구성을 만들 때 IDE는 프로젝트의 해당 구성 이름으로 기본 설정되거나 해당 이름이 없으면 디버그로 설정됩니다. 사용자는 필요한 경우 특정 요구 사항에 맞게 선택을 변경할 수 있습니다. 이 동작의 유일한 예외는 프로젝트가 새 솔루션 구성의 이름과 일치하는 구성을 지원하는 경우입니다. 예를 들어 솔루션에 Project1 및 Project2가 포함되어 있다고 가정합니다. Project1에는 프로젝트 구성 Debug, Retail 및 MyConfig1이 있습니다. Project2에는 프로젝트 구성 Debug, Retail 및 MyConfig2가 있습니다.

 사용자가 MyConfig2라는 새 솔루션 구성을 만드는 경우 Project1은 기본적으로 해당 디버그 구성을 솔루션 구성에 바인딩합니다. 또한 Project2는 기본적으로 MyConfig2 구성을 솔루션 구성에 바인딩합니다.

> [!NOTE]
> 바인딩은 대/소문자를 구분하지 않습니다.

 사용자가 구성 드롭다운 목록에서 **다중 선택** 항목을 선택하면 사용 가능한 구성 목록을 제공하는 대화 상자가 환경에 표시됩니다.

 ![여러 구성](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") 여러 구성

 이 대화 상자 내에서 사용자는 하나 또는 여러 구성을 선택할 수 있습니다. 선택한 후 속성 페이지 대화 상자에 표시되는 속성 값은 선택한 구성에 대한 값의 교집합을 반영합니다.

 솔루션 및 프로젝트에 대한 [구성](../../extensibility/internals/solution-configuration.md) 추가 및 이름 바꾸기와 관련된 자세한 내용은 솔루션 구성을 참조하세요.

 프로젝트 종속성 및 빌드 순서는 솔루션 구성에 독립적입니다. 즉, 솔루션의 모든 프로젝트에 대해 하나의 종속성 트리만 설정할 수 있습니다. 솔루션 또는 프로젝트를 마우스 오른쪽 단추로 클릭하고 **프로젝트 의존성** 또는 **프로젝트 빌드 순서** 옵션을 선택하면 **프로젝트 Dependencies** 대화 상자가 열립니다. **프로젝트** 메뉴에서 열 수도 있습니다.

 ![프로젝트 Dependencies](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") 프로젝트 의존성

 프로젝트 dependencies는 프로젝트가 빌드되는 순서를 결정합니다. 대화 상자의 빌드 순서 탭을 사용하여 솔루션 내의 프로젝트가 빌드되는 정확한 순서를 확인하고, Dependencies 탭을 사용하여 빌드 순서를 수정할 수 있습니다.

> [!NOTE]
> 목록의 해당 확인란이 선택되었지만 흐리게 표시되는 프로젝트는 또는 인터페이스에서 지정한 명시적 의존성으로 인해 환경에 의해 추가되었으며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 변경할 수 없습니다. 예를 들어 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트에서 다른 프로젝트에 프로젝트 참조를 추가하면 참조를 삭제해야만 제거할 수 있는 빌드 종속성이 자동으로 추가됩니다. 확인란이 명확하고 흐리게 표시되는 프로젝트는 종속성 루프를 만들기 때문에 선택할 수 없습니다.(예를 들어 Project1은 Project2에 종속되고 Project2는 Project1에 종속되어 빌드가 중단됩니다.)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 빌드 프로세스에는 단일 Build 명령으로 호출되는 일반적인 컴파일 및 링크 작업이 포함됩니다. 이전 빌드에서 모든 출력 항목을 삭제하는 정리 작업과 구성의 출력 항목이 변경되었는지 확인하는 최신 검사 등 두 가지 다른 빌드 프로세스를 지원할 수도 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 개체는 에서 반환된 해당 를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> 반환하여 빌드 프로세스를 관리합니다. 빌드 작업이 발생하는 동안 빌드 작업의 상태를 보고하기 위해 구성은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> 환경 및 빌드 상태 이벤트에 관심이 있는 다른 개체에 의해 구현된 인터페이스인 를 호출합니다.

 빌드되면 구성 설정을 사용하여 디버거의 제어 하에서 실행할 수 있는지 여부를 결정할 수 있습니다. 구성은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 디버깅을 지원하기 위해 를 구현합니다.

 프로젝트 종속성 구현 후 자동화 모델을 통해 종속성 프로그래밍 방식으로 조작할 수 있습니다. 자동화 <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> 모델에서 를 호출합니다. 솔루션 빌드 관리자 구성 및 해당 속성을 직접 조작할 수 있는 사용 가능한 VSIP API 수준 인터페이스는 없습니다.

 또한 프로젝트 의존성 창에서 표를 제공할 수 있습니다. 자세한 내용은 속성 표시 표 를 [참조하세요.](../../extensibility/internals/properties-display-grid.md)

## <a name="see-also"></a>참조
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [배포 관리를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)
