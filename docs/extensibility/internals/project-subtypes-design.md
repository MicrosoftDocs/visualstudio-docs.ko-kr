---
title: 프로젝트 하위 형식 디자인 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706450"
---
# <a name="project-subtypes-design"></a>프로젝트 하위 형식 디자인

프로젝트 하위 유형을 사용 하면 Microsoft Build Engine (MSBuild)를 기반으로 프로젝트를 Vspackage 확장할 수 있습니다. 집계를 사용 하면에서 구현 된 대부분의 핵심 관리 프로젝트 시스템을 다시 사용할 수 있지만 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 여전히 특정 시나리오에 대 한 동작을 사용자 지정 합니다.

 다음 항목에서는 프로젝트 하위 형식의 기본 디자인 및 구현에 대해 자세히 설명 합니다.

- 프로젝트 하위 형식 디자인.

- 다중 수준 집계.

- 지원 인터페이스

## <a name="project-subtype-design"></a>프로젝트 하위 형식 디자인

프로젝트 하위 형식 초기화는 주 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 개체와 개체를 집계 하 여 구현 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . 이 집계를 사용 하면 프로젝트 하위 형식이 기본 프로젝트의 기능을 대부분 재정의 하거나 향상 시킬 수 있습니다. 프로젝트 하위 유형은를 사용 하 여 속성을 처리 하 고, 및를 사용 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 명령을 사용 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 하 고,를 사용 하 여 프로젝트 항목을 관리 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> 프로젝트 하위 형식 또한 다음과 같이 확장할 수 있습니다.

- 프로젝트 구성 개체입니다.

- 구성 종속 개체입니다.

- 구성 독립적인 찾아보기 개체입니다.

- 프로젝트 자동화 개체.

- 프로젝트 자동화 속성 컬렉션입니다.

프로젝트 하위 형식으로 확장 하는 방법에 대 한 자세한 내용은 [프로젝트 하위 형식으로 확장 된 속성 및 메서드](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)를 참조 하세요.

### <a name="policy-files"></a>정책 파일

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]환경에서는 정책 파일의 구현에서 프로젝트 하위 형식으로 기본 프로젝트 시스템을 확장 하는 예제를 제공 합니다. 정책 파일은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 솔루션 탐색기, **프로젝트 추가** 대화 상자, **새 항목 추가** 대화 상자 및 **속성** 대화 상자를 포함 하는 기능을 관리 하 여 환경을 셰이핑 하는 데 사용할 수 있습니다. 정책 하위 유형은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> , 및 구현을 통해 이러한 기능을 재정의 하 고 향상 시킵니다 `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .

### <a name="aggregation-mechanism"></a>집계 메커니즘

환경의 프로젝트 하위 형식 집계 메커니즘은 여러 수준의 집계를 지원 하므로 flavoring a flavored 프로젝트를 추가 하 여 고급 하위 형식을 구현할 수 있습니다. 또한와 같은 프로젝트 하위 형식의 지원 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> 여러 수준의 계층화를 허용 하도록 설계 되었습니다. COM 및 COM 집계 규칙의 제약 조건을 유지 하면서 내부 하위 형식 또는 기본 프로젝트가 메서드 호출을 위임 하 고 참조 횟수를 관리 하는 데 제대로 참여 하도록 하려면 프로젝트 하위 형식 및 기본 프로젝트를 협조적으로 프로그래밍 해야 합니다. 즉, 집계할 프로젝트를 집계를 지원 하도록 프로그래밍 해야 합니다.

다음 그림에서는 다중 수준 프로젝트 하위 형식 집계의 구조 표현을 보여 줍니다.

![Visual Studio 다중 수준 projectflavor 그래픽](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

다중 수준 프로젝트 하위 형식 집계는 세 가지 수준으로 구성 됩니다. 기본 프로젝트는 프로젝트 하위 형식으로 집계 된 다음 고급 프로젝트 하위 형식으로 집계 됩니다. 이 그림에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 하위 형식 아키텍처의 일부로 제공 되는 몇 가지 지원 인터페이스에 대해 중점적으로 설명 합니다.

### <a name="deployment-mechanisms"></a>배포 메커니즘

프로젝트 하위 형식에 의해 향상 된 대부분의 기본 프로젝트 시스템 기능 중에는 배포 메커니즘이 있습니다. 프로젝트 하위 유형은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 에서 QueryInterface를 호출 하 여 검색 되는 구성 인터페이스 (예: 및)를 구현 하 여 배포 메커니즘에 영향을 미칩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . 프로젝트 하위 형식 및 고급 프로젝트 하위 형식이 서로 다른 구성 구현을 추가 하는 시나리오에서는 기본 프로젝트가 `QueryInterface` 고급 프로젝트 하위 형식에서를 호출 합니다 `IUnknown` . 내부 프로젝트 하위 형식에 기본 프로젝트에서 요청 하는 구성 구현이 포함 되어 있으면 고급 프로젝트 하위 형식이 내부 프로젝트 하위 형식에서 제공 하는 구현에 위임 됩니다. 한 집계 수준에서 다른 집계 수준으로 상태를 유지 하는 메커니즘으로, 모든 수준의 프로젝트 하위 형식에서를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 하 여 비 빌드 관련 XML 데이터를 프로젝트 파일에 유지 합니다. 자세한 내용은 [MSBuild 프로젝트 파일에 데이터 유지](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)를 참조 하세요. <xref:EnvDTE80.IInternalExtenderProvider> 는 프로젝트 하위 형식에서 automation extender를 검색 하는 메커니즘으로 구현 됩니다.

다음 그림은 프로젝트 하위 형식에서 기본 프로젝트 시스템을 확장 하는 데 사용 하는 특히, 프로젝트 구성 찾아보기 개체인 자동화 extender 구현을 중점적으로 다룹니다.

![VS 프로젝트 버전 자동 Extender 그래픽](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

프로젝트 하위 유형은 자동화 개체 모델을 확장 하 여 기본 프로젝트 시스템을 추가로 확장할 수 있습니다. 이러한 개체는 DTE 자동화 개체의 일부로 정의 되며 프로젝트 개체, 개체 및 개체를 확장 하는 데 사용 됩니다 `ProjectItem` `Configuration` . 자세한 내용은 [기본 프로젝트의 개체 모델 확장](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)을 참조 하세요.

## <a name="multi-level-aggregation"></a>다중 수준 집계

하위 수준 프로젝트 하위 형식을 래핑하는 프로젝트 하위 형식 구현은 내부 프로젝트 하위 형식이 제대로 작동 하도록 프로그래밍 해야 합니다. 프로그래밍 책임 목록에는 다음이 포함 됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>내부 하위 형식을 래핑하는 프로젝트 하위 형식의 구현은 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 및 메서드에 대 한 내부 프로젝트 하위 형식의 구현에 위임 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .

- <xref:EnvDTE80.IInternalExtenderProvider>래퍼 프로젝트 하위 형식의 구현은 내부 프로젝트 하위 형식에 대해 위임 되어야 합니다. 특히의 구현은 <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> 내부 프로젝트 하위 형식에서 이름 문자열을 가져온 다음 extender로 추가 하려는 문자열을 연결 해야 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> 기본 프로젝트의 프로젝트 구성 개체는 래퍼 프로젝트 하위 형식 구성 개체가 존재 한다는 것을 직접 인식 하므로 래퍼 프로젝트 하위 형식의 구현은 내부 프로젝트 하위 형식의 개체를 인스턴스화하고 전용 대리자로 저장 해야 합니다. 외부 프로젝트 하위 형식에서 처음에는 직접 처리 하려는 구성 인터페이스를 선택 하 고 나머지를 내부 프로젝트 하위 형식의 구현에 위임할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>지원 인터페이스

기본 프로젝트는 프로젝트 하위 형식에 의해 추가 된 지원 인터페이스에 대 한 호출을 위임 하 여 구현에 대 한 다양 한 측면을 확장 합니다. 여기에는 프로젝트 구성 개체와 다양 한 속성 브라우저 개체가 확장 됩니다. 이러한 인터페이스는 `QueryInterface` `punkOuter` `IUnknown` 가장 바깥쪽 프로젝트 하위 형식 집계의 (에 대 한 포인터)에서를 호출 하 여 검색 됩니다.

|인터페이스|프로젝트 하위 형식|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|프로젝트 하위 형식에서 다음을 수행할 수 있습니다.<br /><br /> -의 구현을 제공 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 합니다.<br />-프로젝트 하위 형식이의 자체 구현을 제공 하도록 허용 하 여 디버거 시작을 제어 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />-의 구현에서 사례를 적절 하 게 처리 하 여 디자인 타임 식 계산을 사용 하지 않도록 설정 `DBGLAUNCH_DesignTimeExprEval` <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> 합니다.|
|<xref:EnvDTE80.IInternalExtenderProvider>|프로젝트 하위 형식에서 다음을 수행할 수 있습니다.<br /><br /> -프로젝트의을 확장 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> 하 여 프로젝트의 구성 독립적 속성을 추가 하거나 제거 합니다.<br />-프로젝트의 프로젝트 자동화 개체 ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> )를 확장 합니다.<br /><br /> 위의 속성 값은 열거형에서 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|프로젝트 구성 찾아보기 개체가 지정 된 경우 프로젝트 하위 형식에서 개체에 다시 매핑할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> `VSITEMID` 구성 찾아보기 개체가 지정 된 경우 프로젝트 하위 형식에서 또는 개체로 다시 매핑할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|프로젝트 하위 형식에서 임의의 XML 구조화 된 데이터를 프로젝트 파일 (.vbproj 또는 .csproj)에 유지할 수 있습니다. MSBuild에는이 데이터가 표시 되지 않습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|프로젝트 하위 형식에서 다음을 수행할 수 있습니다.<br /><br /> -유지할 새 MSBuild 속성을 추가 합니다.<br />-MSBuild에서 불필요 한 속성을 제거 합니다.<br />-MSBuild 속성의 현재 값을 쿼리 합니다.<br />-MSBuild 속성의 현재 값을 변경 합니다.|

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
