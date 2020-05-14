---
title: 프로젝트 하위 유형으로 확장된 속성 및 메서드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706204"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>프로젝트 하위 형식에 의해 확장된 속성 및 메서드
프로젝트 하위 유형은 기본 프로젝트의 집계자로 구성되므로 프로젝트의 동작에 영향을 미칠 수 있는 많은 힘이 있습니다. 이 섹션에서는 프로젝트 하위 유형에서 향상하거나 수정할 수 있는 몇 가지 기능을 요약합니다.

## <a name="features-gained-by-aggregation"></a>집계에 의해 얻은 특징
 다음 표에서는 집계를 통해 프로젝트 하위 형식이 기본 프로젝트에서 재정의할 수 있는 많은 메서드를 요약합니다.

|집계에 의해 재정의된 메서드|프로젝트 하위 유형|
|---------------------------------------|---------------------|
|에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|프로젝트 하위 유형을<br /><br /> - 프로젝트 노드의 캡션 및 아이콘을 변경합니다.<br />- 프로젝트 `Browse` 객체를 완전히 재정의합니다.<br />- 프로젝트의 이름을 바꿀 수 있는지 여부를 제어합니다.<br />- 제어 정렬 순서.<br />- 동적 도움말에 대한 사용자 컨텍스트를 제어합니다.|
|에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|프로젝트 하위 형식이 디자이너 및 편집자에게 제공되는 컨텍스트 서비스를 제어할 수 있도록 합니다.|
|에서 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|프로젝트 하위 유형을<br /><br /> - 프로젝트 명령에 대한 명령 라우팅에 참여합니다.<br />- 프로젝트 앰비언트 명령과 솔루션 탐색기 활성 명령을 모두 추가, 제거 또는 비활성화합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|프로젝트 하위 유형이 **새 항목 추가** 대화 상자에 표시되는 내용을 필터링할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|프로젝트 하위 유형을<br /><br /> - 파일 확장이 주어진 기본 생성기를 결정합니다.<br />- 사람이 읽을 수 있는 생성기 이름을 COM 개체에 매핑합니다.|

## <a name="properties-used-by-project-subtypes"></a>프로젝트 하위 유형에서 사용되는 속성
 환경 및 기본 프로젝트 시스템은 다음 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> 표에 자세히 설명된 속성을 사용하여 프로젝트 하위 유형이 프로젝트 시스템의 다양한 기능을 제어할 수 있도록 할 수 있습니다.

|VSHPROPID 속성|프로젝트 하위 유형|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|프로젝트 하위 유형이 **항목 추가** 대화 상자의 내용을 제어할 수 있도록 허용합니다. 프로젝트 하위 유형은 템플릿 디렉터리의 새 사양을 제공하고, 새 종류의 항목을 추가하고, 기존 항목을 제거하고, 기본 프로젝트의 **항목 추가** 대화 상자에서 항목의 하위 집합을 재구성할 수 있습니다.|
|`PropertyPagesCLSIDList`|프로젝트 하위 유형이 구성 독립적인 속성 페이지를 추가하거나 제거할 수 있도록 허용합니다.|
|`CfgPropertyPagesCLSIDList`|프로젝트 하위 유형이 구성 종속 속성 페이지를 추가하거나 제거할 수 있도록 허용합니다.|
|`ExtObjectCATID`|프로젝트 하위 형식이 Extender CATID를 알고 프로젝트 또는 프로젝트 항목 개체에 대한 자동화 익스텐더를 제공할 수 있습니다. 예를 들어 프로젝트 하위 유형은 `Project.Extender("<subtype>")` 사용자 지정 개체를 제공할 수 있습니다.|
|`BrowseObjectCATID`|프로젝트 하위 형식이 Extender CATID를 `Browse` 알고 개체에 대한 자동화 익스텐더를 제공할 수 있습니다. 예를 들어 프로젝트 하위 유형은 컬렉션에 <xref:EnvDTE.Project.Properties%2A> 추가 속성을 추가할 수 있습니다.|
|`CfgBrowseObjectCATID`|프로젝트 하위 형식이 프로젝트 구성 찾아보기 개체에 대한 자동화 익스텐더를 제공할 수 있습니다. 예를 들어 프로젝트 하위 유형은 컬렉션에 <xref:EnvDTE.Configuration.Properties%2A> 추가 속성을 추가할 수 있습니다.|
|`CfgExtObjectCATID`|프로젝트 하위 형식이 구성 개체에 대한 자동화 익스텐더를 제공할 수 있습니다.|
|`DefaultPlatformName`|프로젝트 하위 유형이 프로젝트의 구성 개체에 대한 플랫폼 이름을 결정할 수 있도록 허용합니다.|

 기본 프로젝트는 위의 속성의 기본 구현을 제공합니다. 기본 프로젝트는 가장 바깥쪽 프로젝트 하위 형식을 호출하여 `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 이를 가져옵니다.

## <a name="see-also"></a>참조
- [프로젝트 하위 형식 디자인](../../extensibility/internals/project-subtypes-design.md)
