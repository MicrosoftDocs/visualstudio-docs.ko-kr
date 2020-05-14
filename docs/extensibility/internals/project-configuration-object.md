---
title: 프로젝트 구성 개체 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706651"
---
# <a name="project-configuration-object"></a>프로젝트 구성 개체
프로젝트 구성 개체는 UI에 구성 정보의 표시를 관리합니다.

 ![비주얼 스튜디오 프로젝트 구성](../../extensibility/internals/media/vsprojectcfg.gif "vs프로젝트Cfg") 프로젝트 구성 속성 페이지

 프로젝트 구성 공급자는 프로젝트 구성을 관리합니다. 환경 및 기타 패키지를 사용하여 프로젝트 구성에 대한 정보에 액세스하고 검색하려면 프로젝트 구성 공급자 개체에 연결된 인터페이스를 호출합니다.

> [!NOTE]
> 솔루션 구성 파일을 프로그래밍 방식으로 만들거나 편집할 수 없습니다. `DTE.SolutionBuilder`을 사용해야 합니다. 자세한 내용은 [솔루션 구성을](../../extensibility/internals/solution-configuration.md) 참조하십시오.

 구성 UI에서 사용할 표시 이름을 게시하려면 프로젝트를 구현해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>합니다. 환경 호출은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>환경의 `IVsCfg` UI에 나열할 구성 및 플랫폼 정보의 표시 이름을 얻는 데 사용할 수 있는 포인터 목록을 반환합니다. 활성 구성 및 플랫폼은 활성 솔루션 구성에 저장된 프로젝트의 구성에 의해 결정됩니다. 이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> 메서드는 활성 프로젝트 구성을 검색하는 데 사용할 수 있습니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> 표준 프로젝트 구성 이름에 따라 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> `IVsProjectCfg2` 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> 검색할 수 있도록 개체를 선택적으로 개체와 함께 개체에 구현할 수 있습니다.

 환경 및 기타 프로젝트에 프로젝트 구성에 대한 액세스를 제공하는 또 다른 방법은 `IVsCfgProvider2::GetCfgs` 프로젝트가 하나 이상의 구성 개체를 반환하는 메서드의 구현을 제공하는 것입니다. 프로젝트는 구성 관련 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>정보를 제공하기 `IVsProjectCfg` 위해 `IVsCfg`에서 상속되는 을 구현할 수도 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>는 프로젝트 구성을 추가, 삭제 및 바꾸기 위한 플랫폼 및 기능을 지원합니다.

> [!NOTE]
> Visual Studio는 더 이상 두 가지 구성 유형으로 제한되지 않으므로 구성을 처리하는 코드는 구성 수에 대한 가정으로 작성해서는 안 되며 구성이 하나뿐인 프로젝트가 반드시 디버그 또는 소매라는 가정하에 작성해서는 안 됩니다. 이렇게 하면 사용이 더 이상 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> 사용되지 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> 않습니다.

 검색에서 `QueryInterface` `IVsGetCfgProvider::GetCfgProvider` 반환된 개체에 대한 호출 `IVsCfgProvider2`. `IVsProject3` 프로젝트 `IVsGetCfgProvider` 개체를 호출하여 `QueryInterface` 찾을 수 없는 경우 에 대해 `QueryInterface` 반환된 개체에 대해 계층 루트 `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`브라우저 개체를 호출하거나 에 `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`대해 반환된 구성 공급자에 대한 포인터를 통해 구성 공급자 개체에 액세스할 수 있습니다.

 `IVsProjectCfg2`주로 빌드, 디버그 및 배포 관리 개체에 대한 액세스를 제공하고 프로젝트에서 출력을 자유롭게 그룹화할 수 있습니다. 의 `IVsProjectCfg` 메서드및 `IVsProjectCfg2` 빌드 프로세스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 관리하기 위해 구현하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 데 사용할 수 있으며, 구성의 출력 그룹에 대한 포인터.

 프로젝트는 그룹에 포함된 출력 수가 구성마다 다를 수 있더라도 지원하는 각 구성에 대해 동일한 수의 그룹을 반환해야 합니다. 또한 그룹에는 프로젝트 내의 구성에서 구성에 이르는 동일한 식별자 정보(표준 이름, 표시 이름 및 그룹 정보)도 있어야 합니다. 자세한 내용은 [출력에 대한 프로젝트 구성을](../../extensibility/internals/project-configuration-for-output.md)참조하십시오.

 디버깅을 사용하려면 구성을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>구현해야 합니다. `IVsDebuggableProjectCfg`는 디버거가 구성을 시작할 수 있도록 프로젝트에 의해 구현된 선택적 인터페이스이며 `IVsProjectCfg`및 을 사용하여 `IVsCfg` 구성 개체에 구현됩니다. 사용자가 F5를 눌러 디버거를 시작하도록 선택하면 환경이 호출합니다.

 `ISpecifyPropertyPages``IDispatch` 속성 페이지와 함께 사용하여 구성 종속 정보를 검색하고 사용자에게 표시합니다. 자세한 내용은 [속성 페이지를](../../extensibility/internals/property-pages.md)참조하십시오.

## <a name="see-also"></a>참조
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)
- [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)
- [속성 페이지](../../extensibility/internals/property-pages.md)
- [솔루션 구성](../../extensibility/internals/solution-configuration.md)
