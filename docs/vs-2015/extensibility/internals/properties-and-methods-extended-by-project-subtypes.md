---
title: 프로젝트 하위 형식에 의해 확장 된 속성 및 메서드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20892d50afc529b410e8e0bdfa3c4b52fdc1b9b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154119"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>프로젝트 하위 형식에 의해 확장된 속성 및 메서드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 하위 형식에는 기본 프로젝트의 집계로 생성 되기 때문에 프로젝트의 동작에 영향을 줄 수 있는 많은 기능이 있습니다. 이 섹션에서는 프로젝트 하위 형식으로 향상 또는 수정할 수 있는 기능 중 일부를 요약 합니다.  
  
## <a name="features-gained-by-aggregation"></a>집계로 얻은 기능  
 다음 표에서는 집계에서 프로젝트 하위 형식이 기본 프로젝트에서 재정의할 수 있도록 하는 여러 메서드를 요약 합니다.  
  
|집계에 의해 재정의 된 메서드|프로젝트 하위 형식|  
|---------------------------------------|---------------------|  
|시작 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|프로젝트 하위 형식 사용<br /><br /> -프로젝트 노드의 캡션과 아이콘을 변경 합니다.<br />-프로젝트 `Browse` 개체를 완전히 재정의 합니다.<br />-프로젝트의 이름을 바꿀 수 있는지 여부를 제어 합니다.<br />-정렬 순서를 제어 합니다.<br />-동적 도움말의 사용자 컨텍스트를 제어 합니다.|  
|시작 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|프로젝트 하위 형식이 디자이너 및 편집기에 제공 되는 컨텍스트 서비스를 제어할 수 있도록 합니다.|  
|시작 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|프로젝트 하위 형식 사용<br /><br /> -프로젝트 명령에 대 한 명령 라우팅에 참여 합니다.<br />-프로젝트 주변 명령을 추가, 제거 또는 사용 하지 않도록 설정 하 고 활성 명령을 솔루션 탐색기 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|프로젝트 하위 형식이 **새 항목 추가** 대화 상자에서 사용자에 게 표시 되는 항목을 필터링 할 수 있도록 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|프로젝트 하위 형식 사용<br /><br /> -파일 확장명이 지정 된 경우 기본 생성기를 확인 합니다.<br />-사람이 읽을 수 있는 생성기 이름을 COM 개체에 매핑합니다.|  
  
## <a name="properties-used-by-project-subtypes"></a>프로젝트 하위 형식에서 사용 하는 속성  
 환경 및 기본 프로젝트 시스템에서는 다음 표에 설명 된 속성을 사용 하 여 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> 하위 형식이 프로젝트 시스템의 다양 한 기능을 제어할 수 있도록 합니다.  
  
|VSHPROPID 속성|프로젝트 하위 형식|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|프로젝트 하위 형식이 **항목 추가** 대화 상자의 콘텐츠를 제어할 수 있도록 허용 합니다. 프로젝트 하위 유형은 템플릿 디렉터리의 새 사양을 제공 하 고, 새 종류의 항목을 추가 하 고, 기존 항목을 제거 하 고, 기본 프로젝트의 **항목 추가** 대화 상자에서 항목의 하위 집합을 재구성할 수 있습니다.|  
|`PropertyPagesCLSIDList`|프로젝트 하위 형식이 구성 독립적 속성 페이지를 추가 하거나 제거할 수 있습니다.|  
|`CfgPropertyPagesCLSIDList`|프로젝트 하위 형식이 구성 종속 속성 페이지를 추가 하거나 제거할 수 있습니다.|  
|`ExtObjectCATID`|프로젝트 하위 형식이 Extender CATID를 알면 프로젝트 또는 프로젝트 항목 개체에 대 한 자동화 Extender를 제공할 수 있도록 합니다. 예를 들어 프로젝트 하위 형식에서 사용자 지정 개체를 제공할 수 있습니다 `Project.Extender("<subtype>")` .|  
|`BrowseObjectCATID`|프로젝트 하위 형식이 Extender CATID를 알면 개체에 대 한 자동화 Extender를 제공할 수 있도록 합니다 `Browse` . 예를 들어 프로젝트 하위 형식에서 컬렉션에 속성을 더 추가할 수 있습니다 <xref:EnvDTE.Project.Properties%2A> .|  
|`CfgBrowseObjectCATID`|프로젝트 하위 형식에서 프로젝트 구성 찾아보기 개체에 대 한 자동화 Extender를 제공할 수 있도록 합니다. 예를 들어 프로젝트 하위 형식에서 컬렉션에 속성을 더 추가할 수 있습니다 <xref:EnvDTE.Configuration.Properties%2A> .|  
|`CfgExtObjectCATID`|프로젝트 하위 형식이 구성 개체에 대 한 자동화 Extender를 제공할 수 있도록 합니다.|  
|`DefaultPlatformName`|프로젝트 하위 형식에서 프로젝트의 구성 개체에 대 한 플랫폼 이름을 확인할 수 있도록 합니다.|  
  
 기본 프로젝트는 위의 속성에 대 한 기본 구현을 제공 합니다. 기본 프로젝트는 `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 가장 바깥쪽 프로젝트 하위 형식에 대해를 호출 하 여 프로젝트 하위 형식이 속성 구현을 재정의할 수 있도록 하 여 이러한 속성을 가져옵니다.  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 하위 형식 디자인](../../extensibility/internals/project-subtypes-design.md)
