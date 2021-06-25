---
title: 속성 페이지 | Microsoft Docs
description: 사용자가 프로젝트 속성을 보고 변경할 수 있도록 하는 Visual Studio SDK에서 새 프로젝트 형식에 대한 속성 페이지 작업에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88ebf99ef2361a232c4a5c4c02b9a140155d66e9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903413"
---
# <a name="property-pages"></a>속성 페이지
사용자는 속성 페이지를 사용하여 프로젝트 구성 종속 및 독립 속성을 보고 변경할 수 있습니다. **속성 페이지** 단추는 속성 창 또는 선택한 개체의 **속성** 페이지 보기를 제공하는 개체의 솔루션 탐색기 도구 모음에서 사용할 수 있습니다. 속성 페이지는 환경에서 만들어지고 솔루션 및 프로젝트에 사용할 수 있습니다. 그러나 구성 종속 속성을 사용하는 프로젝트 항목에도 사용할 수 있습니다. 이 기능은 프로젝트 내의 파일을 제대로 빌드하기 위해 다른 컴파일러 스위치 설정이 필요한 경우에 사용할 수 있습니다.

## <a name="using-property-pages"></a>속성 페이지 사용
 속성 페이지가 이미 표시되고 선택 항목이 변경된 경우(예: 솔루션에서 프로젝트로) 페이지에 표시되는 정보가 변경되어 새 선택 항목의 속성이 표시됩니다. 속성 페이지를 지원하는 개체에 속성이 없으면 속성 페이지가 비어 있습니다.

 여러 개체를 선택하면 속성 페이지에 선택한 모든 항목에 대한 속성의 교집합이 표시됩니다. 선택한 항목에 구성 종속 속성이 포함되어 있지 않고 솔루션 탐색기 도구 모음의 **속성 페이지** 단추를 클릭하면 포커스가 속성 창 변경됩니다. 속성 창 및 선택 항목과 관련된 자세한 내용은 [속성 확장을 참조하세요.](../../extensibility/internals/extending-properties.md)

 속성이 여러 개체에 대해 표시되고 속성 페이지에서 값을 변경하는 경우 개체의 모든 값은 처음에 다르고 개별 개체의 속성이 표시될 때 페이지가 비어 있는 경우에도 새 값으로 설정됩니다.

 에서 사용할 수 있는 두 가지 일반적인 유형의 **ProjectProperty Pages** 대화 상자가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있습니다. 예를 들어 Visual Basic 프로젝트의 경우 다음 스크린샷과 같이 필드 형식을 사용하여 속성 페이지가 표시됩니다. 이 섹션의 후반부에 표시된 두 번째에서 속성 페이지는 속성 창에 있는 것과 유사한 속성 표를 호스팅합니다.

 ![Visual Basic 속성 페이지](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") 필드 형식 및 트리 구조가 있는 프로젝트 속성 페이지 대화 상자

 속성 페이지 대화 상자의 트리 구조는 를 사용하여 작성되지 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 않습니다. 환경은 및 인터페이스에 의해 전달된 수준 이름을 기반으로 <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> 하여 환경을 빌드합니다.

 속성 페이지에서 사용할 수 있는 최상위 범주는 두 개뿐입니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

- 공용 속성 - 선택한 개체 또는 개체에 대한 구성 독립적 정보를 표시합니다. 따라서 공용 속성 하위 범주 중 하나를 선택하면 대화 상자 맨 위에 있는 구성, 플랫폼 및 구성 관리자 옵션을 사용할 수 없습니다.

- 구성 속성 - 솔루션 또는 프로젝트에 대한 디버깅, 최적화 및 빌드 매개 변수와 관련된 구성 종속 정보를 포함합니다.

  추가 최상위 범주를 만들 수는 없지만 구현에서 하나 또는 다른 범주를 표시하지 않도록 선택할 수 `IVsPropertyPage` 있습니다. 예를 들어 개체에 대해 표시할 구성 독립적 속성이 없는 경우 공용 속성 범주를 표시하지 않도록 선택할 수 있습니다. 구성 `ISpecifyPropertyPages` `ISpecifyPropertyPages` 개체(, 및 관련 인터페이스를 구현하는 개체)에서 를 구현할 때 항목의 찾아보기 개체 및 구성 속성에서 를 구현하는 경우 공용 속성을 `IVsCfg` `IVsProjectCfg` 표시합니다.

  최상위 범주 아래에 표시되는 각 범주는 별도의 속성 페이지를 나타냅니다. 대화 상자에서 사용할 수 있는 범주 및 하위 범주 항목은 및 의 구현에 따라 `ISpecifyPropertyPages` `IVsPropertyPage` 결정됩니다.

  `IDispatch` 속성 페이지에 표시할 속성이 있는 선택 컨테이너의 항목에 대한 개체는 `ISpecifyPropertyPages` 클래스 ID 목록을 열거하기 위해 를 구현합니다. 클래스 ID는 에 변수로 `ISpecifyPropertyPages` 전달되고 속성 페이지를 인스턴스화하기 위해 사용됩니다. 클래스의 목록도 에 전달되어 `IVsPropertyPage` 대화 상자 왼쪽에 트리 구조를 만듭니다. 그런 다음 속성 페이지는 `IDispatch` 각 페이지에 대한 정보를 `ISpecifyPropertyPages` 구현하고 채우는 개체에 정보를 다시 전달합니다.

  찾아보기 개체의 속성은 `IDispatch` 선택 컨테이너의 각 개체에 대해 를 사용하여 검색됩니다.

  `Help::DisplayTopicFromF1Keyword`VSPackage에서 를 구현하면 도움말 단추에 대한 기능이 제공됩니다.

  자세한 내용은 `IDispatch` `ISpecifyPropertyPages` MSDN 라이브러리의 및 를 참조하세요.

  샘플에 표시되는 두 번째 유형의 속성 페이지는 다음 스크린샷과 같이 속성 표의 형식을 호스팅합니다.

  ![VC 속성 페이지](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") 속성 표가 있는 속성 페이지 대화 상자

  `IVSMDPropertyBrowser` `IVSMDPropertyGrid` 및 인터페이스(vsmanaged.h에서 선언)는 대화 상자 또는 창 내에서 속성 표를 만들고 채우는 데 사용됩니다.

  프로젝트의 아키텍처는 의 과거 버전에서 크게 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 변경되었습니다. 특히 어떤 프로젝트가 활성 상태인지에 대한 개념이 변경되었습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에는 활성 프로젝트의 개념이 없습니다. 이전 개발 환경에서 활성 프로젝트는 컨텍스트에 관계없이 명령 빌드 및 배포가 기본값인 프로젝트였습니다. 이제 솔루션은 어떤 빌드 및 배포 명령이 어떤 프로젝트에 적용되는지 제어하고 중재합니다.

  이전에는 활성 프로젝트였던 것이 이제 다음 세 가지 방법 중 하나로 캡처됩니다.

- 시작 프로젝트

   사용자가 F5 키를 누르거나 빌드 메뉴에서 실행을 선택할 때 시작될 솔루션의 속성 페이지에서 프로젝트 또는 프로젝트를 지정할 수 있습니다. 이는 이름이 굵은 글꼴로 솔루션 탐색기 표시된다는 점에서 이전 활성 프로젝트와 비슷한 방식으로 작동합니다.

   를 호출하여 자동화 모델에서 시작 프로젝트를 속성으로 검색할 수 `DTE.Solution.SolutionBuild.StartupProjects` 있습니다. VSPackage에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 메서드를 호출합니다. `IVsSolutionBuildManager` 는 SID_SVsSolutionBuildManager 에서 서비스로 사용할 수 `QueryService` 있습니다. 자세한 내용은 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md) 및 솔루션 구성 을 [참조하세요.](../../extensibility/internals/solution-configuration.md)

- 활성 솔루션 빌드 구성

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 에는 를 구현하여 자동화 모델에서 사용할 수 있는 활성 솔루션 구성이 `DTE.Solution.SolutionBuild.ActiveConfiguration` 있습니다. 솔루션 구성은 솔루션의 각 프로젝트에 대해 하나의 프로젝트 구성을 포함하는 컬렉션입니다(각 프로젝트는 서로 다른 이름의 여러 플랫폼에서 여러 구성을 포함할 수 있습니다). 솔루션의 속성 페이지와 관련된 자세한 내용은 솔루션 구성 을 [참조하세요.](../../extensibility/internals/solution-configuration.md)

- 현재 선택한 프로젝트

   프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> 계층 구조와 선택한 프로젝트 항목 또는 항목을 검색하는 메서드를 구현합니다. DTE에서 `SelectedItems.SelectedItem.Project` 및 `SelectedItems.SelectedItem.ProjectItem` 메서드를 사용합니다. 핵심 문서의 제목 아래에 샘플 코드가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있습니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)
- [솔루션 구성](../../extensibility/internals/solution-configuration.md)
