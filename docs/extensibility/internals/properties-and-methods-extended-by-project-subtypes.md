---
title: 프로젝트 하위 형식으로 확장된 속성 및 메서드 | Microsoft Docs
description: Visual Studio 프로젝트 시스템의 동작을 사용자 지정할 수 있도록 프로젝트 하위 형식이 향상되거나 수정될 수 있는 기능에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ddcf020cf0b3e3e4f0f4a7c61ff1f15ce9ded5e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903543"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>프로젝트 하위 형식에 의해 확장된 속성 및 메서드
프로젝트 하위 형식은 기본 프로젝트의 집계로 생성되므로 프로젝트의 동작에 영향을 줄 수 있는 많은 권한이 있습니다. 이 섹션에서는 프로젝트 하위 유형에 의해 향상되거나 수정될 수 있는 몇 가지 기능을 요약합니다.

## <a name="features-gained-by-aggregation"></a>집계를 통해 얻은 기능
 다음 표에는 집계를 통해 기본 프로젝트에서 프로젝트 하위 형식을 재정의할 수 있는 많은 메서드가 요약됩니다.

|집계로 재정의된 메서드|프로젝트 하위 유형|
|---------------------------------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>에서:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|프로젝트 하위 형식을 다음으로 설정합니다.<br /><br /> - 프로젝트 노드의 캡션 및 아이콘을 변경합니다.<br />- 프로젝트 개체를 완전히 `Browse` 재정의합니다.<br />- 프로젝트 이름을 바꿀 수 있는지 여부를 제어합니다.<br />- 정렬 순서를 제어합니다.<br />- 동적 도움말에 대한 사용자 컨텍스트를 제어합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>에서:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|프로젝트 하위 유형을 사용하여 디자이너 및 편집기에서 제공되는 컨텍스트 서비스를 제어할 수 있습니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>에서:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|프로젝트 하위 형식을 다음으로 설정합니다.<br /><br /> - 프로젝트 명령에 대한 명령 라우팅에 참여합니다.<br />- 프로젝트 앰비언트 명령과 솔루션 탐색기 활성 명령을 모두 추가, 제거 또는 사용하지 않도록 설정합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|프로젝트 하위 유형을 사용하여 새 **항목 추가** 대화 상자에서 사용자에게 표시되는 내용을 필터링할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|프로젝트 하위 형식을 다음으로 설정합니다.<br /><br /> - 파일 확장명에서 기본 생성기를 결정합니다.<br />- 사람이 읽을 수 있는 생성기 이름을 COM 개체에 매핑합니다.|

## <a name="properties-used-by-project-subtypes"></a>프로젝트 하위 유형에서 사용하는 속성
 환경 및 기본 프로젝트 시스템은 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> 다음 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> 표에 설명된 및 열거형의 속성을 사용하여 프로젝트 하위 형식이 프로젝트 시스템의 다양한 기능을 제어할 수 있도록 합니다.

|VSHPROPID 속성|프로젝트 하위 유형|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|프로젝트 하위 유형이 **항목 추가** 대화 상자의 내용을 제어할 수 있도록 합니다. 프로젝트 하위 형식은 템플릿 디렉터리의 새 사양을 제공하고, 새 종류의 항목을 추가하고, 기존 항목을 제거하고, 기본 프로젝트의 **항목 추가** 대화 상자에서 항목의 하위 집합을 다시 구성합니다.|
|`PropertyPagesCLSIDList`|프로젝트 하위 유형에서 구성 독립적 속성 페이지를 추가하거나 제거할 수 있습니다.|
|`CfgPropertyPagesCLSIDList`|프로젝트 하위 유형에서 구성 종속 속성 페이지를 추가하거나 제거할 수 있습니다.|
|`ExtObjectCATID`|프로젝트 하위 유형이 Extender CATID를 알고 프로젝트 또는 프로젝트 항목 개체에 대한 Automation Extender를 제공할 수 있도록 합니다. 예를 들어 프로젝트 하위 형식은 사용자 지정 개체를 제공할 수 `Project.Extender("<subtype>")` 있습니다.|
|`BrowseObjectCATID`|프로젝트 하위 형식이 Extender CATID를 알고 개체에 대한 Automation Extender를 제공할 수 있도록 `Browse` 합니다. 예를 들어 프로젝트 하위 형식은 컬렉션에 속성을 더 추가할 수 <xref:EnvDTE.Project.Properties%2A> 있습니다.|
|`CfgBrowseObjectCATID`|프로젝트 하위 형식이 프로젝트 구성 찾아보기 개체에 대한 Automation Extender를 제공할 수 있도록 허용합니다. 예를 들어 프로젝트 하위 형식은 컬렉션에 속성을 더 추가할 수 <xref:EnvDTE.Configuration.Properties%2A> 있습니다.|
|`CfgExtObjectCATID`|프로젝트 하위 유형이 구성 개체에 대한 Automation Extender를 제공할 수 있도록 합니다.|
|`DefaultPlatformName`|프로젝트 하위 형식이 프로젝트의 구성 개체에 대한 플랫폼 이름을 확인할 수 있도록 허용합니다.|

 기본 프로젝트는 위의 속성에 대한 기본 구현을 제공합니다. 기본 프로젝트는 `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 가장 바깥쪽 프로젝트 하위 형식에서 를 호출하여 이를 가져오므로 프로젝트 하위 형식이 속성의 구현을 재정의할 수 있습니다.

## <a name="see-also"></a>참조
- [프로젝트 하위 형식 디자인](../../extensibility/internals/project-subtypes-design.md)
