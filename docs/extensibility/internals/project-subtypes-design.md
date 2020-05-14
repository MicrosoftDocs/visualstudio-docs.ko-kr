---
title: 프로젝트 하위 유형 설계 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706450"
---
# <a name="project-subtypes-design"></a>프로젝트 하위 형식 디자인

프로젝트 하위 유형을 사용하면 VSPackage가 MSBuild(Microsoft 빌드 엔진)를 기반으로 프로젝트를 확장할 수 있습니다. 집계를 사용하면 구현된 대부분의 핵심 관리 프로젝트 시스템을 다시 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용할 수 있지만 특정 시나리오에 대한 동작을 사용자 지정할 수 있습니다.

 다음 항목에서는 프로젝트 하위 유형의 기본 설계 및 구현에 대해 자세히 설명합니다.

- 프로젝트 하위 유형 설계.

- 다단계 집계.

- 인터페이스 를 지원합니다.

## <a name="project-subtype-design"></a>프로젝트 하위 유형 설계

프로젝트 하위 유형의 초기화는 주 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> 개체를 집계하여 수행됩니다. 이 집계를 사용하면 프로젝트 하위 형식이 기본 프로젝트의 대부분의 기능을 재정의하거나 향상시킬 수 있습니다. 프로젝트 하위 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>유형은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>을 사용하여 및 및 프로젝트 항목 관리를 사용하여 속성을 처리할 첫 번째 기회를 얻습니다. 프로젝트 하위 유형도 확장할 수 있습니다.

- 프로젝트 구성 개체입니다.

- 구성 종속 개체입니다.

- 구성 독립적인 찾아보기 개체입니다.

- 프로젝트 자동화 개체입니다.

- 프로젝트 자동화 속성 컬렉션입니다.

프로젝트 하위 유형별 확장성에 대한 자세한 내용은 [프로젝트 하위 유형별로 확장된 속성 및 메서드를](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)참조하십시오.

### <a name="policy-files"></a>정책 파일

환경은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 정책 파일 구현시 프로젝트 하위 유형으로 기본 프로젝트 시스템을 확장하는 예제를 제공합니다. 정책 파일은 솔루션 탐색기, **프로젝트 추가** 대화 상자, **새 항목 추가** 대화 상자 및 **속성** 대화 상자가 포함된 기능을 관리하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 환경을 형성할 수 있도록 합니다. 정책 하위 유형은 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` 구현을 통해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 이러한 기능을 재정의하고 향상시킵니다.

### <a name="aggregation-mechanism"></a>집계 메커니즘

환경의 프로젝트 하위 유형 집계 메커니즘은 여러 수준의 집계를 지원하므로 풍미가 있는 프로젝트를 추가로 맛을 내서 고급 하위 유형을 구현할 수 있습니다. 또한 와 같은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>프로젝트 하위 유형의 지원 개체는 여러 수준의 계층화를 허용하도록 설계되었습니다. COM 및 COM 집계 규칙의 제약 조건에 따라 내부 하위 유형 또는 기본 프로젝트가 메서드 호출 위임 및 참조 개 수 관리에 제대로 참여할 수 있도록 프로젝트 하위 유형 및 기본 프로젝트를 협력적으로 프로그래밍해야 합니다. 즉, 집계될 프로젝트는 집계를 지원하도록 프로그래밍되어야 합니다.

다음 그림에서는 다단계 프로젝트 하위 유형 집계의 회로도 표현을 보여 주며, 다단계 프로젝트 하위 유형 집계를 보여 주실 수 있습니다.

![Visual Studio 다중 수준 projectflavor 그래픽](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

다중 레벨 프로젝트 하위 유형 집계는 프로젝트 하위 유형으로 집계된 다음 고급 프로젝트 하위 유형으로 추가 집계되는 기본 프로젝트인 세 가지 수준으로 구성됩니다. 이 그림은 프로젝트 하위 유형 아키텍처의 일부로 제공되는 일부 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 지원 인터페이스에 중점을 둡니다.

### <a name="deployment-mechanisms"></a>배포 메커니즘

프로젝트 하위 유형에 의해 향상된 기본 프로젝트 시스템 기능 중 에는 배포 메커니즘이 있습니다. 프로젝트 하위 유형은 에서 Query를 호출하여 검색되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>구성 인터페이스(예: 및)를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>구현하여 배포 메커니즘에 영향을 줍니다. 프로젝트 하위 유형과 고급 프로젝트 하위 유형이 서로 다른 구성 구현을 `QueryInterface` 추가하는 시나리오에서는 기본 프로젝트가 `IUnknown`고급 프로젝트 하위 유형의 을 호출합니다. 내부 프로젝트 하위 유형에 기본 프로젝트가 요구하는 구성 구현이 포함된 경우 고급 프로젝트 하위 유형은 내부 프로젝트 하위 유형에서 제공하는 구현에 위임합니다. 한 집계 수준에서 다른 집계 수준으로 상태를 유지하는 메커니즘으로 모든 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 하위 유형 수준은 비빌드 관련 XML 데이터를 프로젝트 파일에 유지하도록 구현합니다. 자세한 내용은 [MSBuild 프로젝트 파일의 데이터 유지를](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)참조하십시오. <xref:EnvDTE80.IInternalExtenderProvider>프로젝트 하위 유형에서 자동화 익스텐더를 검색하는 메커니즘으로 구현됩니다.

다음 그림에서는 자동화 익스텐더 구현, 특히 프로젝트 구성이 기본 프로젝트 시스템을 확장하는 데 프로젝트 하위 유형에서 사용되는 개체를 찾아내는 데 중점을 둡니다.

![VS 프로젝트 버전 자동 Extender 그래픽](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

프로젝트 하위 유형은 자동화 개체 모델을 확장하여 기본 프로젝트 시스템을 더욱 확장할 수 있습니다. 이러한 개체는 DTE 자동화 개체의 일부로 정의되며 Project 개체, `ProjectItem` 개체 `Configuration` 및 개체를 확장하는 데 사용됩니다. 자세한 내용은 [기본 프로젝트의 객체 모델 확장을](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)참조하십시오.

## <a name="multi-level-aggregation"></a>다단계 집계

하위 수준의 프로젝트 하위 유형을 래핑하는 프로젝트 하위 형식 구현은 내부 프로젝트 하위 유형이 제대로 작동할 수 있도록 협조적으로 프로그래밍해야 합니다. 프로그래밍 책임 목록은 다음과 같습니다.

- 내부 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 하위 유형을 래핑하는 프로젝트 하위 형식의 구현은 메서드 및 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> 메서드 모두에 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> 대한 내부 프로젝트 하위 형식의 구현에 위임해야 합니다.

- 래퍼 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 하위 형식의 구현은 내부 프로젝트 하위 형식의 해당 프로젝트에 위임해야 합니다. 특히 구현은 내부 <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> 프로젝트 하위 유형에서 이름 문자열을 얻은 다음 extenders로 추가하려는 문자열을 연결해야 합니다.

- 래퍼 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> 프로젝트 하위 형식의 구현은 기본 프로젝트의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> 프로젝트 구성 개체만 래퍼 프로젝트 하위 유형 구성 개체가 존재한다는 것을 직접 알고 있으므로 내부 프로젝트 하위 형식의 개체를 인스턴스화하고 개인 대리자로 보유해야 합니다. 외부 프로젝트 하위 유형은 처음에 직접 처리하려는 구성 인터페이스를 선택한 다음 나머지는 내부 프로젝트 하위 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>유형의 구현에 위임할 수 있습니다.

## <a name="supporting-interfaces"></a>인터페이스 지원

기본 프로젝트 대리자는 구현의 다양한 측면을 확장하기 위해 프로젝트 하위 유형에 의해 추가된 지원 인터페이스를 호출합니다. 여기에는 프로젝트 구성 개체 및 다양한 속성 브라우저 개체 확장이 포함됩니다. 이러한 인터페이스는 가장 바깥쪽 프로젝트 하위 유형 집계의 호출(에 `QueryInterface` `punkOuter` 대한 `IUnknown`포인터)을 호출하여 검색됩니다.

|인터페이스|프로젝트 하위 유형|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|프로젝트 하위 유형을 다음을 수행할 수 있습니다.<br /><br /> - 의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>구현을 제공합니다.<br />- 프로젝트 하위 형식이 고유한 구현을 제공할 수 있도록 하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>디버거 의 실행을 제어합니다.<br />- 구현시 `DBGLAUNCH_DesignTimeExprEval` 사례를 적절히 처리하여 설계 시간 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>식 평가를 비활성화합니다.|
|<xref:EnvDTE80.IInternalExtenderProvider>|프로젝트 하위 유형을 다음을 수행할 수 있습니다.<br /><br /> - 프로젝트의 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> 구성 독립적 인 속성을 추가하거나 제거하려면 프로젝트의 확장.<br />- 프로젝트의 프로젝트 자동화<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>개체 () 확장합니다.<br /><br /> 위의 속성 값은 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 열거형에서 가져온 값입니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|프로젝트 하위 유형이 프로젝트 구성 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> 찾아보기 개체를 지정하면 개체에 다시 매핑할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|프로젝트 구성 찾아보기 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 고려하여 `VSITEMID` 프로젝트 하위 유형을 개체 또는 개체에 다시 매핑할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|프로젝트 하위 형식이 임의의 XML 구조화 데이터를 프로젝트 파일(.vbproj 또는 .csproj)에 유지하도록 허용합니다. 이 데이터는 MSBuild에 표시되지 않습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|프로젝트 하위 유형을 다음을 수행할 수 있습니다.<br /><br /> - 지속할 새 MSBuild 속성을 추가합니다.<br />- MSBuild에서 불필요한 속성을 제거합니다.<br />- MSBuild 속성의 현재 값을 쿼리합니다.<br />- MSBuild 속성의 현재 값을 변경합니다.|

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
