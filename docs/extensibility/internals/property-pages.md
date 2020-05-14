---
title: 속성 페이지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706052"
---
# <a name="property-pages"></a>속성 페이지
사용자는 속성 페이지를 사용하여 프로젝트 구성에 종속적이고 -독립적인 속성을 보고 변경할 수 있습니다. **속성 페이지** 단추는 **속성** 창 또는 선택한 개체의 속성 페이지 보기를 제공 하는 개체에 대 한 솔루션 탐색기 도구 모음에서 활성화 됩니다. 속성 페이지는 환경에 의해 만들어지며 솔루션 및 프로젝트에 사용할 수 있습니다. 그러나 구성 종속 속성을 사용하는 프로젝트 항목에도 사용할 수 있습니다. 이 기능은 프로젝트 내의 파일이 제대로 빌드하기 위해 다른 컴파일러 스위치 설정이 필요한 경우에 사용될 수 있습니다.

## <a name="using-property-pages"></a>속성 페이지 사용
 속성 페이지가 이미 표시되고 선택 영역이 변경되는 경우(예: 솔루션에서 프로젝트로), 페이지에 표시된 정보가 변경되어 새 선택 영역에 대한 속성을 표시합니다. 속성 페이지를 지원하는 개체에 속성이 없는 경우 속성 페이지가 비어 있습니다.

 여러 객체를 선택하면 속성 페이지에 선택한 모든 항목에 대한 속성의 교차점이 표시됩니다. 선택한 항목에 구성 종속 속성이 포함되어 있지 않고 솔루션 탐색기 도구 모음의 **속성 페이지** 단추를 클릭하면 속성 창에 포커스가 변경됩니다. 속성 창 및 선택 영역과 관련된 자세한 내용은 [속성 확장](../../extensibility/internals/extending-properties.md)을 참조하십시오.

 속성이 여러 개체에 대해 표시되고 속성 페이지에서 값을 변경하는 경우 개체의 모든 값은 처음에 다르고 개별 개체의 속성이 표시될 때 페이지가 비어 있더라도 새 값으로 설정됩니다.

 에서 사용할 수 있는 **ProjectProperty 페이지** 대화 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]상자에는 두 가지 일반적인 유형이 있습니다. 예를 들어 Visual Basic 프로젝트의 경우 다음 스크린샷과 같이 필드 형식을 사용하여 속성 페이지가 표시됩니다. 이 섹션의 후반부에 표시된 두 번째 에서 속성 페이지는 속성 창에 있는 것과 유사한 속성 그리드를 호스트합니다.

 ![시각적 기본 속성 페이지](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") 필드 형식 및 트리 구조를 가진 프로젝트 속성 페이지 대화 상자

 속성 페이지 대화 상자의 트리 구조는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>을 사용하여 빌드되지 않습니다. 환경은 <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> 인터페이스에 의해 전달되는 수준 이름을 기반으로 환경을 빌드합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 속성 페이지에서 사용할 수 있는 최상위 범주는 두 가지뿐입니다.

- 선택한 개체 또는 개체에 대한 구성 독립적 정보를 표시하는 공통 속성입니다. 따라서 공통 속성 하위 범주 중 하나를 선택하면 대화 상자 상단의 구성, 플랫폼 및 구성 관리자 옵션을 사용할 수 없습니다.

- 솔루션 또는 프로젝트에 대한 디버깅, 최적화 및 빌드 매개 변수와 관련된 구성 종속 정보를 포함하는 구성 속성입니다.

  추가 최상위 범주를 만들 수는 없지만 `IVsPropertyPage`구현에서 하나 또는 다른 범주를 표시하지 않도록 선택할 수 있습니다. 예를 들어 객체에 대해 표시할 구성 독립적 속성이 없는 경우 공통 속성 범주를 표시하지 않도록 선택할 수 있습니다. 구성 개체(구현 `ISpecifyPropertyPages` `ISpecifyPropertyPages` `IVsCfg`및 `IVsProjectCfg`관련 인터페이스)에서 구현할 때 항목의 찾아보기 개체 및 Configuration 속성에서 구현된 경우 공통 속성을 표시합니다.

  최상위 범주 아래에 표시되는 각 범주는 별도의 속성 페이지를 나타냅니다. 대화 상자에서 사용할 수 있는 범주 및 하위 `ISpecifyPropertyPages` 범주 `IVsPropertyPage`항목은 의 구현에 따라 결정됩니다.

  `IDispatch`속성 페이지에 표시할 속성이 있는 항목에 대한 개체는 클래스 아이디 목록을 열거하기 위해 구현됩니다. `ISpecifyPropertyPages` 클래스 아이디는 변수로 `ISpecifyPropertyPages` 전달되며 속성 페이지를 인스턴스화하는 데 사용됩니다. 클래스 아이디 목록은 대화 상자 `IVsPropertyPage` 왼쪽에 있는 트리 구조를 만들기 위해 전달됩니다. 그런 다음 속성 페이지는 각 `IDispatch` 페이지에 대한 `ISpecifyPropertyPages` 정보를 구현하고 채우는 개체에 정보를 다시 전달합니다.

  찾아보기 개체의 속성은 선택 `IDispatch` 컨테이너의 각 개체에 대해 검색됩니다.

  VSPackage에서 구현하면 `Help::DisplayTopicFromF1Keyword` 도움말 단추에 대한 기능이 제공됩니다.

  자세한 내용은 MSDN 라이브러리를 참조하십시오. `IDispatch` `ISpecifyPropertyPages`

  샘플에 표시되는 두 번째 속성 페이지는 다음 스크린샷과 같이 속성 그리드의 형태를 호스팅합니다.

  ![VC 속성 페이지](../../extensibility/internals/media/vsvcproppages.gif "vsVC프로프페이지") 속성 그리드가 있는 속성 페이지 대화 상자

  `IVSMDPropertyBrowser` 인터페이스와 `IVSMDPropertyGrid` (vsmanaged.h에서 선언) 만들고 대화 상자 또는 창 내에서 속성 그리드를 채우는 데 사용 됩니다.

  프로젝트의 아키텍처는 의 과거 버전에서 상당히 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]변경되었습니다. 특히 어떤 프로젝트가 활성화되어 있는지에 대한 개념이 바뀌었습니다. 에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]활성 프로젝트의 개념이 없습니다. 이전 개발 환경에서 활성 프로젝트는 컨텍스트에 관계없이 명령을 빌드하고 배포하는 프로젝트가 기본값으로 설정되었습니다. 이제 솔루션은 명령을 빌드하고 배포하는 것을 제어하고 중재하여 어떤 프로젝트에 적용합니다.

  이전에 는 활성 프로젝트가 었던 프로젝트가 이제 세 가지 방법 중 하나로 캡처됩니다.

- 시작 프로젝트

   사용자가 F5를 누르거나 빌드 메뉴에서 실행을 선택할 때 시작되는 솔루션의 속성 페이지에서 프로젝트 또는 프로젝트를 지정할 수 있습니다. 이 이름은 굵은 글꼴로 솔루션 탐색기에 표시 된다는 의미에서 이전 활성 프로젝트와 비슷한 방식으로 작동 합니다.

   을 호출하여 `DTE.Solution.SolutionBuild.StartupProjects`시작 프로젝트를 자동화 모델의 속성으로 검색할 수 있습니다. VSPackage에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 메서드 또는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 호출합니다. `IVsSolutionBuildManager`SID_SVsSolutionBuildManager 서비스로 `QueryService` 사용할 수 있습니다. 자세한 내용은 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md) 및 솔루션 [구성](../../extensibility/internals/solution-configuration.md)을 참조하십시오.

- 활성 솔루션 빌드 구성

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]을 구현하여 `DTE.Solution.SolutionBuild.ActiveConfiguration`자동화 모델에서 사용할 수 있는 활성 솔루션 구성이 있습니다. 솔루션 구성은 솔루션의 각 프로젝트에 대해 하나의 프로젝트 구성을 포함하는 컬렉션입니다(각 프로젝트는 서로 다른 이름으로 여러 플랫폼에서 여러 구성을 가질 수 있음). 솔루션의 속성 페이지와 관련된 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md)을 참조하십시오.

- 프로젝트가 현재 선택됨

   선택한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> 프로젝트 계층 및 프로젝트 항목 또는 항목을 검색하는 메서드를 구현합니다. DTE에서 및 `SelectedItems.SelectedItem.ProjectItem` 메서드를 `SelectedItems.SelectedItem.Project` 사용합니다. 핵심 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 문서의 이러한 제목 아래에 샘플 코드가 있습니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)
- [솔루션 구성](../../extensibility/internals/solution-configuration.md)
