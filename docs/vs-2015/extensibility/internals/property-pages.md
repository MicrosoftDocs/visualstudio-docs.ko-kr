---
title: 속성 페이지 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a45e4a98326fe829b8f87a4ecfce669118cd9d0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205757"
---
# <a name="property-pages"></a>속성 페이지
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자는 속성 페이지를 사용 하 여 프로젝트 구성에 종속 된 속성 및 독립적인 속성을 보고 변경할 수 있습니다. 속성 **페이지** 단추는 선택한 개체의 속성 페이지 뷰를 제공 하는 개체의 **속성** 창이 나 솔루션 탐색기 도구 모음에서 사용할 수 있습니다. 속성 페이지는 환경에서 만들어지며 솔루션 및 프로젝트에 사용할 수 있습니다. 그러나 구성에 종속 된 속성을 사용 하는 프로젝트 항목에도 사용할 수 있습니다. 프로젝트 내의 파일이 적절 하 게 빌드하려면 다른 컴파일러 스위치 설정을 사용 해야 하는 경우이 기능을 사용할 수 있습니다.  
  
## <a name="using-property-pages"></a>속성 페이지 사용  
 속성 페이지가 이미 표시 되어 있고 선택 항목이 변경 되 면 (예: 솔루션에서 프로젝트에 대 한) 페이지에 표시 된 정보가 새 선택 항목의 속성을 표시 하도록 변경 됩니다. 개체에 속성 페이지를 지 원하는 속성이 없으면 속성 페이지가 비어 있습니다.  
  
 여러 개체를 선택 하는 경우 속성 페이지에 선택한 모든 항목에 대 한 속성의 교집합이 표시 됩니다. 선택한 항목에 구성 종속 속성이 포함 되어 있지 않고 솔루션 탐색기 도구 모음의 **속성 페이지** 단추를 클릭 하면 속성 창에 포커스가 바뀝니다. 속성 창 및 선택과 관련 된 자세한 내용은 [속성 확장](../../extensibility/internals/extending-properties.md)을 참조 하세요.  
  
 여러 개체에 대 한 속성을 표시 하 고 속성 페이지에서 값을 변경 하는 경우 처음에는 다른 개체의 모든 값이 새 값으로 설정 되 고 개별 개체의 속성이 표시 될 때 페이지는 비어 있습니다.  
  
 에서 사용할 수 있는 **Projectproperty Pages** 대화 상자에는 두 가지 일반 형식이 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 예를 들어, Visual Basic 프로젝트의 경우 다음 스크린샷에 표시 된 것 처럼 필드 형식을 사용 하 여 속성 페이지가 표시 됩니다. 이 섹션의 뒷부분에서 설명 하는 것 처럼 속성 페이지는 속성 창에 있는 것과 유사한 속성 표를 호스팅합니다.  
  
 ![Visual Basic 속성 페이지](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
필드 형식 및 트리 구조가 있는 프로젝트 속성 페이지 대화 상자  
  
 속성 페이지 대화 상자의 트리 구조는를 사용 하 여 빌드되지 않습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . 환경에서 및 인터페이스에 의해 전달 된 수준 이름을 기반으로 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> 이를 빌드합니다.  
  
 속성 페이지에는 두 개의 최상위 범주만 사용할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- 선택 된 개체에 대 한 구성 독립적인 정보를 표시 하는 공용 속성입니다. 따라서 Common Properties 하위 범주 중 하나를 선택 하면 대화 상자 위쪽의 구성, 플랫폼 및 Configuration Manager 옵션을 사용할 수 없습니다.  
  
- 구성 속성-솔루션 또는 프로젝트에 대 한 디버깅, 최적화 및 빌드 매개 변수와 관련 된 구성 종속 정보를 포함 합니다.  
  
  최상위 범주를 추가로 만들 수는 없지만의 구현에서 하나 또는 다른 범주를 표시 하지 않도록 선택할 수 있습니다 `IVsPropertyPage` . 예를 들어 개체에 대해 표시할 구성 독립적 속성이 없으면 공용 속성 범주를 표시 하지 않도록 선택할 수 있습니다. `ISpecifyPropertyPages` `ISpecifyPropertyPages` 구성 개체 (, 및 관련 된 인터페이스를 구현 하는 개체)에서를 구현 하는 경우 항목의 찾아보기 개체 및 구성 속성에서가 구현 되 면 공용 속성을 표시 `IVsCfg` `IVsProjectCfg` 합니다.  
  
  최상위 범주 아래에 표시 되는 각 범주는 별도의 속성 페이지를 나타냅니다. 대화 상자에서 사용할 수 있는 범주 및 하위 범주 항목은 및 구현에 따라 결정 됩니다 `ISpecifyPropertyPages` `IVsPropertyPage` .  
  
  `IDispatch` 속성 페이지에 표시 될 속성이 있는 선택 컨테이너의 항목에 대 한 개체는 `ISpecifyPropertyPages` 를 구현 하 여 클래스 id 목록을 열거 합니다. 클래스 Id는 변수로 전달 되 `ISpecifyPropertyPages` 고 속성 페이지를 인스턴스화하는 데 사용 됩니다. 클래스 Id의 목록도에 전달 되어 `IVsPropertyPage` 대화 상자의 왼쪽에 트리 구조를 만듭니다. 그런 다음 속성 페이지에서를 구현 하는 개체로 정보를 다시 전달 하 `IDispatch` `ISpecifyPropertyPages` 고 각 페이지에 대 한 정보를 채웁니다.  
  
  찾아보기 개체의 속성은 `IDispatch` 선택 컨테이너의 각 개체에 대해를 사용 하 여 검색 됩니다.  
  
  VSPackage에서를 구현 하면 `Help::DisplayTopicFromF1Keyword` 도움말 단추에 대 한 기능을 제공 합니다.  
  
  자세한 내용은 `IDispatch` MSDN library의 및을 참조 하십시오 `ISpecifyPropertyPages` .  
  
  예제에 표시 된 속성 페이지의 두 번째 형식은 다음 스크린샷에 표시 된 것 처럼 속성 그리드 폼을 호스팅합니다.  
  
  ![VC 속성 페이지](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
  속성 표를 사용 하는 속성 페이지 대화 상자  
  
  인터페이스 `IVSMDPropertyBrowser` 및 `IVSMDPropertyGrid` (vsmanaged. h에 선언 됨)는 대화 상자 또는 창에서 속성 표를 만들고 채우는 데 사용 됩니다.  
  
  프로젝트의 아키텍처가 이전 버전의에서 크게 변경 되었습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 특히 프로젝트가 활성화 된 개념이 변경 되었습니다. 에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 는 활성 프로젝트의 개념이 없습니다. 이전 개발 환경에서 활성 프로젝트는 컨텍스트에 관계 없이 빌드 및 배포 명령이 기본적으로 발생 하는 프로젝트 였습니다. 이제 솔루션은 빌드 및 배포 명령이 적용 되는 프로젝트에 적용 되는 조정를 제어 합니다.  
  
  이전에 활성 프로젝트는 다음과 같은 세 가지 방법 중 하나로 캡처됩니다.  
  
- 시작 프로젝트  
  
   사용자가 F5 키를 누르거나 빌드 메뉴에서 실행을 선택 하면 솔루션의 속성 페이지에서 프로젝트 또는 프로젝트를 지정할 수 있습니다. 이는 이름이 굵은 글꼴을 사용 하 여 솔루션 탐색기 표시 된다는 점에서 이전 활성 프로젝트와 비슷한 방식으로 작동 합니다.  
  
   을 호출 하 여 자동화 모델에서 시작 프로젝트를 속성으로 검색할 수 있습니다 `DTE.Solution.SolutionBuild.StartupProjects` . VSPackage에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 또는 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 합니다. `IVsSolutionBuildManager` 는 SID_SVsSolutionBuildManager에서 서비스로 사용할 수 있습니다 `QueryService` . 자세한 내용은 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md) 및 [솔루션 구성](../../extensibility/internals/solution-configuration.md)을 참조 하세요.  
  
- 활성 솔루션 빌드 구성  
  
   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 에는을 구현 하 여 자동화 모델에서 사용할 수 있는 활성 솔루션 구성이 있습니다 `DTE.Solution.SolutionBuild.ActiveConfiguration` . 솔루션 구성은 솔루션의 각 프로젝트에 대해 하나의 프로젝트 구성을 포함 하는 컬렉션입니다. 각 프로젝트에는 여러 플랫폼에서 서로 다른 이름을 가진 여러 구성이 있을 수 있습니다. 솔루션의 속성 페이지와 관련 된 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md)을 참조 하세요.  
  
- 현재 선택 되어 있는 프로젝트  
  
   메서드를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> 하 여 프로젝트 계층 구조와 프로젝트 항목을 검색 합니다. DTE에서 `SelectedItems.SelectedItem.Project` 및 메서드를 사용 `SelectedItems.SelectedItem.ProjectItem` 합니다. 핵심 문서의 해당 제목 아래에는 샘플 코드가 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)   
 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)   
 [솔루션 구성](../../extensibility/internals/solution-configuration.md)
