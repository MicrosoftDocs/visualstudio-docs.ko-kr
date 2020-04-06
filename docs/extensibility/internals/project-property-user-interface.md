---
title: 프로젝트 속성 사용자 인터페이스 | 마이크로 소프트 문서
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706391"
---
# <a name="project-property-user-interface"></a>프로젝트 속성 사용자 인터페이스

프로젝트 하위 유형은 기본 프로젝트에서 제공하는 대로 프로젝트 **속성 페이지** 대화 상자의 항목을 사용하거나, 제공된 대로 읽기 전용 컨트롤 및 전체 페이지를 숨기거나 만들거나, **속성 페이지** 대화 상자에 프로젝트 하위 유형별 페이지를 추가할 수 있습니다.

## <a name="extending-the-project-property-dialog-box"></a>프로젝트 속성 대화 상자 확장

프로젝트 하위 유형은 자동화 익스텐더를 구현하고 프로젝트 구성은 개체를 찾아봅슬합니다. 이러한 extenders는 <xref:EnvDTE.IFilterProperties> 특정 속성을 숨기거나 읽기 전용으로 만들기 위해 인터페이스를 구현합니다. 기본 프로젝트에 의해 구현된 기본 프로젝트의 **속성 페이지** 대화 상자는 자동화 익스텐더에서 수행하는 필터링을 고려합니다.

**프로젝트 속성** 대화 상자를 확장하는 프로세스는 다음과 같습니다.

- 기본 프로젝트는 인터페이스를 구현하여 프로젝트 하위 유형에서 <xref:EnvDTE80.IInternalExtenderProvider> extenders를 검색합니다. 찾아보기, 프로젝트 자동화 및 프로젝트 구성은 모두 이 인터페이스를 구현하는 기본 프로젝트의 개체를 찾아봅금입니다.

- 프로젝트 찾아보기 개체에 <xref:EnvDTE80.IInternalExtenderProvider> 대한 구현및 프로젝트 자동화 <xref:EnvDTE80.IInternalExtenderProvider> 개체는 프로젝트 하위 유형 애그리게이터(즉, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 프로젝트 개체에 `QueryInterface` 대한 <xref:EnvDTE80.IInternalExtenderProvider> 구현)의 구현에 위임합니다.

- 기본 프로젝트 구성 찾아보기 <xref:EnvDTE80.IInternalExtenderProvider> 개체는 프로젝트 하위 유형 구성 개체에서 자동화 익스텐더에서 직접 와이어링하도록 구현합니다. 해당 구현은 프로젝트 <xref:EnvDTE80.IInternalExtenderProvider> 하위 유형 애그리게이터에 의해 구현된 인터페이스에 위임합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>을 통해 구현된 프로젝트 구성에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 개체를 찾아개체를 반환합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>을 통해 구현된 프로젝트 구성 찾아보기 개체가 개체를 반환합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>

- 프로젝트 하위 유형은 다음 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 값을 검색하여 런타임에 기본 프로젝트의 다양한 확장 가능한 개체에 대한 적절한 CATID를 결정할 수 있습니다.

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

프로젝트 범위에 대한 CATID를 결정하기 위해 프로젝트 하위 유형은 VSITEMID에 대한 위의 속성을 [검색합니다. 에서 루트](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef` 프로젝트 하위 유형은 구성에 따라 다르고 구성에 독립적인 속성 **페이지** 대화 상자 페이지가 프로젝트에 표시되는지 제어할 수도 있습니다. 일부 프로젝트 하위 유형은 기본 제공 페이지를 제거하고 프로젝트 하위 유형 특정 페이지를 추가해야 할 수 있습니다. 이를 활성화하기 위해 관리되는 클라이언트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 프로젝트는 다음 속성에 대한 메서드를 호출합니다.

- `VSHPROPID_PropertyPagesCLSIDList`— 구성 독립적 속성 페이지의 CLSID의 세미콜론 구분 목록입니다.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`구성 종속 속성 페이지의 CLSID의 세미콜론 구분 목록입니다.

프로젝트 하위 유형은 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 집계하므로 이러한 속성의 정의를 재정의하여 표시되는 속성 **페이지** 대화 상자를 제어할 수 있습니다. 프로젝트 하위 유형은 내부 기본 프로젝트에서 이러한 속성을 검색한 다음 필요에 따라 CLSI를 추가하거나 제거할 수 있습니다.

프로젝트 하위 유형에 의해 추가된 새 속성 페이지는 기본 프로젝트 구현에서 프로젝트 구성 찾아보기 개체를 전달합니다. 이 프로젝트 구성 찾아보기 개체는 자동화 익스텐더를 지원합니다. 자동화 익스텐더에 대한 자세한 내용은 [자동화 익스텐더 구현 및 사용을](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)참조하십시오. 프로젝트 하위 유형 호출에 <xref:EnvDTE.Project.Extender%2A> 의해 구현 된 속성 페이지는 기본 프로젝트의 구성 찾아보기 개체를 확장 하는 자체 프로젝트 하위 유형 구성 찾아보기 개체를 검색 합니다.

## <a name="see-also"></a>참조

- <xref:EnvDTE.IFilterProperties>
- [속성 페이지 대화 상자](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
