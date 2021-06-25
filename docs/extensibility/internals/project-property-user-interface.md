---
title: 프로젝트 속성 사용자 인터페이스 | Microsoft Docs
description: 프로젝트 하위 형식이 기본 프로젝트에서 제공하는 대로 프로젝트 속성 페이지 대화 상자를 수정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77e3554f2a3fd3b0dc1d608bb7d0a1198116a4e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903591"
---
# <a name="project-property-user-interface"></a>프로젝트 속성 사용자 인터페이스

프로젝트 하위 유형은 기본 프로젝트에서 제공된 대로 프로젝트 **속성 페이지** 대화 상자의 항목을 사용하거나, 제공된 읽기 전용 컨트롤과 전체 페이지를 숨기거나 만들거나, 프로젝트 하위 유형별 페이지를 **속성 페이지** 대화 상자에 추가할 수 있습니다.

## <a name="extending-the-project-property-dialog-box"></a>프로젝트 속성 대화 상자 확장

프로젝트 하위 형식은 자동화 extenders 및 프로젝트 구성 찾아보기 개체를 구현합니다. 이러한 extenders는 <xref:EnvDTE.IFilterProperties> 인터페이스를 구현하여 특정 속성을 숨기거나 읽기 전용으로 만듭니다. 기본 프로젝트에서 구현하는 기본 프로젝트의 **속성 페이지** 대화 상자는 Automation Extenders에서 수행하는 필터링을 적용합니다.

**프로젝트 속성** 대화 상자를 확장하는 프로세스는 아래에 설명되어 있습니다.

- 기본 프로젝트는 인터페이스를 구현하여 프로젝트 하위 형식에서 extenders를 <xref:EnvDTE80.IInternalExtenderProvider> 검색합니다. 기본 프로젝트의 찾아보기, 프로젝트 자동화 및 프로젝트 구성 찾아보기 개체는 모두 이 인터페이스를 구현합니다.

- 프로젝트 찾아보기 개체에 대한 의 구현 <xref:EnvDTE80.IInternalExtenderProvider> 및 프로젝트 자동화 개체 <xref:EnvDTE80.IInternalExtenderProvider> 대리자는 프로젝트 하위 형식 집계의 구현(즉, `QueryInterface` 프로젝트 개체의 에 <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 해당)입니다.

- 또한 기본 프로젝트 구성 찾아보기 개체는 <xref:EnvDTE80.IInternalExtenderProvider> 를 구현하여 프로젝트 하위 형식 구성 개체에서 Automation Extender에 직접 연결합니다. 해당 구현은 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 하위 형식 집계에 의해 구현된 인터페이스에 위임됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>프로젝트 구성 찾아보기 개체에 의해 구현된 는 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 반환합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>또한 프로젝트 구성 찾아보기 개체에서 구현된 는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> 개체를 반환합니다.

- 프로젝트 하위 형식은 다음 값을 검색하여 런타임에 기본 프로젝트의 다양한 확장 가능한 개체에 대한 적절한 CATID를 확인할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

프로젝트 범위의 CATID를 확인하기 위해 프로젝트 하위 유형은 VSITEMID에 대해 위의 속성을 [검색합니다. 의](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef` 루트입니다. 프로젝트 하위 유형은 구성 종속 페이지와 구성 독립적 모두에 따라 프로젝트에 대해 표시되는 **속성 페이지** 대화 상자 페이지를 제어할 수도 있습니다. 일부 프로젝트 하위 유형은 기본 제공 페이지를 제거하고 프로젝트 하위 유형 특정 페이지를 추가해야 할 수 있습니다. 이를 사용하도록 설정하기 위해 관리되는 클라이언트 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 다음 속성에 대해 메서드를 호출합니다.

- `VSHPROPID_PropertyPagesCLSIDList` - 구성 독립적 속성 페이지의 CLSID에 대한 세미콜론으로 구분된 목록입니다.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` 구성 종속 속성 페이지의 CLSID에 대한 세미콜론으로 구분된 목록입니다.

프로젝트 하위 형식은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 개체를 집계하므로 이러한 속성의 정의를 재정의하여 표시되는 **속성 페이지** 대화 상자를 제어할 수 있습니다. 프로젝트 하위 형식은 내부 기본 프로젝트에서 이러한 속성을 검색한 다음 필요에 따라 CLSID를 추가하거나 제거할 수 있습니다.

프로젝트 하위 유형에 의해 추가된 새 속성 페이지는 기본 프로젝트 구현에서 프로젝트 구성 찾아보기 개체를 전달합니다. 이 프로젝트 구성 찾아보기 개체는 Automation Extenders를 지원합니다. AutomationExtenders에 대한 자세한 내용은 [Automation Extenders 구현 및 사용을 참조하세요.](/previous-versions/0y92k2w2(v=vs.140)) 기본 프로젝트의 <xref:EnvDTE.Project.Extender%2A> 구성 찾아보기 개체를 확장하는 자체 프로젝트 하위 형식 구성 찾아보기 개체를 검색하기 위해 프로젝트 하위 형식 호출에 의해 구현되는 속성 페이지입니다.

## <a name="see-also"></a>참조

- <xref:EnvDTE.IFilterProperties>
- [속성 페이지 대화 상자](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))