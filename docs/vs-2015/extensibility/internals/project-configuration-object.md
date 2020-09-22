---
title: 프로젝트 구성 개체 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e4d34ec3d1fbe8753b4185cab76caa77038bd1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842031"
---
# <a name="project-configuration-object"></a>프로젝트 구성 개체
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 구성 개체는 UI에 대 한 구성 정보 표시를 관리 합니다.  
  
 ![Visual Studio 프로젝트 구성](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
프로젝트 구성 속성 페이지  
  
 프로젝트 구성 공급자는 프로젝트 구성을 관리 합니다. 환경 및 기타 패키지를 사용 하 여 프로젝트 구성에 대 한 정보에 액세스 하 고이에 대 한 정보를 검색 하려면 프로젝트 구성 공급자 개체에 연결 된 인터페이스를 호출 합니다.  
  
> [!NOTE]
> 프로그래밍 방식으로 솔루션 구성 파일을 만들거나 편집할 수 없습니다. `DTE.SolutionBuilder`을 사용해야 합니다. 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md) 을 참조 하세요.  
  
 구성 UI에서 사용할 표시 이름을 게시 하려면 프로젝트에서를 구현 해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> 합니다. 환경에서는를 호출 하며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , `IVsCfg` 환경 UI에 나열 될 구성 및 플랫폼 정보에 대 한 표시 이름을 가져오는 데 사용할 수 있는 포인터 목록을 반환 합니다. 활성 구성 및 플랫폼은 활성 솔루션 구성에 저장 된 프로젝트의 구성에 따라 결정 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>메서드는 활성 프로젝트 구성을 검색 하는 데 사용할 수 있습니다.  
  
 개체는 개체를 사용 하 여 개체 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> 에서 선택적으로 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> 하 여 `IVsProjectCfg2` 정식 프로젝트 구성 이름을 기반으로 개체를 검색할 수 있습니다.  
  
 프로젝트 구성에 대 한 액세스 권한이 있는 환경 및 기타 프로젝트를 제공 하는 또 다른 방법은 프로젝트에서 하나 이상의 `IVsCfgProvider2::GetCfgs` 구성 개체를 반환 하는 메서드 구현을 제공 하는 것입니다. 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> `IVsProjectCfg` `IVsCfg` 구성 관련 정보를 제공 하기 위해에서 상속 되는를 구현할 수도 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 는 플랫폼 및 프로젝트 구성을 추가, 삭제 및 이름 변경 하는 기능을 지원 합니다.  
  
> [!NOTE]
> Visual Studio는 더 이상 두 개의 구성 형식으로 제한 되지 않으므로 구성을 처리 하는 코드는 구성 수에 대 한 가정을 사용 하 여 작성 해서는 안 되며, 구성이 하나뿐인 프로젝트가 반드시 디버그 또는 일반 정품 이어야 한다고 가정 하 여 작성 해서는 안 됩니다. 이렇게 하면 및가 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> 되지 않습니다.  
  
 `QueryInterface`에서 반환 되는 개체에 대해를 호출 하면가 `IVsGetCfgProvider::GetCfgProvider` 검색 `IVsCfgProvider2` 됩니다. `IVsGetCfgProvider`프로젝트 개체에 대해를 호출 하 여를 찾을 수 없는 경우 `QueryInterface` `IVsProject3` `QueryInterface` 에 대해 반환 된 개체의 계층 루트 브라우저 개체에서를 호출 `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` 하거나에 대해 반환 된 구성 공급자에 대 한 포인터를 통해 구성 공급자 개체에 액세스할 수 있습니다 `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .  
  
 `IVsProjectCfg2` 는 주로 빌드, 디버그 및 배포 관리 개체에 대 한 액세스를 제공 하며 프로젝트에서 출력을 그룹화 할 수 있도록 합니다. 및의 메서드를 사용 하 여 `IVsProjectCfg` `IVsProjectCfg2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 빌드 프로세스를 관리 하 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 구성의 출력 그룹에 대 한 포인터를 구현할 수 있습니다.  
  
 그룹에 포함 된 출력 수가 구성에 따라 다를 수 있지만 프로젝트에서 지 원하는 각 구성에 대해 동일한 수의 그룹을 반환 해야 합니다. 또한 그룹은 구성에서 프로젝트 내의 구성으로의 식별자 정보 (정식 이름, 표시 이름 및 그룹 정보)가 동일 해야 합니다. 자세한 내용은 [출력에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)을 참조 하세요.  
  
 디버깅을 사용 하도록 설정 하려면 구성에서을 구현 해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 합니다. `IVsDebuggableProjectCfg` 는 디버거가 구성을 시작할 수 있도록 하 고 및를 사용 하 여 구성 개체에서 구현 되는 프로젝트에 의해 구현 되는 선택적 인터페이스입니다 `IVsCfg` `IVsProjectCfg` . 사용자가 F5 키를 눌러 디버거를 시작 하는 경우 환경에서 호출 합니다.  
  
 `ISpecifyPropertyPages` 및 `IDispatch` 는 속성 페이지와 함께 사용 되어 구성에 종속 된 정보를 검색 하 고 사용자에 게 표시 합니다. 자세한 내용은 [속성 페이지](../../extensibility/internals/property-pages.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)   
 [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)   
 [출력에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)   
 [속성 페이지](../../extensibility/internals/property-pages.md)   
 [솔루션 구성](../../extensibility/internals/solution-configuration.md)
