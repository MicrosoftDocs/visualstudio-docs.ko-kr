---
title: 빌드에 대 한 프로젝트 구성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 953a02c27f40e92c41d2e43bc818727118eb0a27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841638"
---
# <a name="project-configuration-for-building"></a>빌드를 위한 프로젝트 구성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정 된 솔루션에 대 한 솔루션 구성 목록은 솔루션 구성 대화 상자에서 관리 합니다.  
  
 사용자는 고유한 이름을 가진 추가 솔루션 구성을 만들 수 있습니다. 사용자가 새 솔루션 구성을 만들 때 IDE는 프로젝트에서 해당 하는 구성 이름으로 기본 설정 되 고, 해당 이름이 없는 경우에는 Debug를 사용 합니다. 사용자는 필요한 경우 특정 요구 사항을 충족 하도록 선택 항목을 변경할 수 있습니다. 이 동작의 유일한 예외는 프로젝트가 새 솔루션 구성의 이름과 일치 하는 구성을 지 원하는 경우입니다. 예를 들어 솔루션에 Project1 및 Project2이 포함 되어 있다고 가정 합니다. Project1에는 디버그, 일반 정품 및 MyConfig1 프로젝트 구성이 있습니다. Project2에는 디버그, 일반 정품 및 MyConfig2 프로젝트 구성이 있습니다.  
  
 사용자가 MyConfig2 이라는 새 솔루션 구성을 만드는 경우 Project1는 기본적으로 해당 디버그 구성을 솔루션 구성에 바인딩합니다. 또한 Project2는 기본적으로 MyConfig2 구성을 솔루션 구성에 바인딩합니다.  
  
> [!NOTE]
> 바인딩은 대/소문자를 구분 하지 않습니다.  
  
 사용자가 구성 드롭다운 목록에서 **여러 선택** 항목을 선택 하면 사용 가능한 구성 목록을 제공 하는 대화 상자가 환경에 표시 됩니다.  
  
 ![여러 구성](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
여러 구성  
  
 이 대화 상자에서 사용자는 하나 또는 여러 개의 구성을 선택할 수 있습니다. 선택 하면 속성 페이지 대화 상자에 표시 되는 속성 값에 선택한 구성의 값이 교차 하는 것이 반영 됩니다.  
  
 솔루션 및 프로젝트에 대 한 구성 추가 및 이름 바꾸기와 관련 된 정보는 [솔루션 구성](../../extensibility/internals/solution-configuration.md) 을 참조 하세요.  
  
 프로젝트 종속성 및 빌드 순서는 솔루션 구성에 독립적입니다. 즉, 솔루션의 모든 프로젝트에 대해 하나의 종속성 트리를 설정할 수 있습니다. 솔루션 또는 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **프로젝트 종속성** 또는 **프로젝트 빌드 순서** 옵션을 선택 하 여 **프로젝트 종속성** 대화 상자를 엽니다. **프로젝트** 메뉴에서 열 수도 있습니다.  
  
 ![프로젝트 종속성](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
프로젝트 종속성  
  
 프로젝트 종속성은 프로젝트 빌드 순서를 결정 합니다. 대화 상자의 빌드 순서 탭을 사용 하 여 솔루션 내의 프로젝트가 생성 되는 정확한 순서를 확인 하 고 종속성 탭을 사용 하 여 빌드 순서를 수정할 수 있습니다.  
  
> [!NOTE]
> 확인란이 선택 되어 있지만 희미하게 표시 되는 목록의 프로젝트는 또는 인터페이스에 의해 지정 된 명시적 종속성으로 인해 환경에서 추가 되었으며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 변경할 수 없습니다. 예를 들어 프로젝트의 프로젝트 참조를 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 다른 프로젝트에 추가 하면 참조를 삭제 해야만 제거할 수 있는 빌드 종속성이 자동으로 추가 됩니다. 확인란의 선택을 취소 하 고 흐리게 표시 되는 프로젝트는 종속성 루프를 만들기 때문에 선택할 수 없습니다. 예를 들어 Project1는 Project2에 종속 되 고 Project2는 Project1에 종속 되므로 빌드를 정지 하 게 됩니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 빌드 프로세스에는 단일 빌드 명령으로 호출 되는 일반적인 컴파일 및 링크 작업이 포함 됩니다. 다른 두 개의 빌드 프로세스 (이전 빌드에서 모든 출력 항목을 삭제 하는 정리 작업 및 구성의 출력 항목이 변경 되었는지 여부를 확인 하는 최신 검사)도 지원 될 수 있습니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> 빌드 프로세스를 관리 하기 위해 해당 (에서 반환)을 반환 합니다. 빌드 작업이 발생 하는 동안 빌드 작업의 상태를 보고 하기 위해 구성은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> 환경에서 구현 되는 인터페이스 및 빌드 상태 이벤트에 관심이 있는 다른 모든 개체에 대 한 호출을 수행 합니다.  
  
 빌드 후에는 구성 설정을 사용 하 여 디버거의 제어를 통해 실행할 수 있는지 여부를 확인할 수 있습니다. 구성을 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 하 여 디버깅을 지원 합니다.  
  
 프로젝트 종속성을 구현한 후 자동화 모델을 통해 프로그래밍 방식으로 종속성을 조작할 수 있습니다. <xref:EnvDTE.SolutionBuild.BuildDependencies%2A>자동화 모델에서를 호출 합니다. 솔루션 빌드 관리자 구성 및 해당 속성을 직접 조작할 수 있는 사용 가능한 VSIP API 수준 인터페이스는 없습니다.  
  
 또한 프로젝트 종속성 창에서 표를 제공할 수 있습니다. 자세한 내용은 [속성 표시 그리드](../../extensibility/internals/properties-display-grid.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)   
 [배포 관리를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)
