---
title: 프로젝트 모델 핵심 구성 요소 | Microsoft Docs
description: 이 문서에는 프로젝트 모델 코어에서 식별된 인터페이스 및 서비스 및 개체와 연결된 인터페이스 및 서비스에 대한 설명이 포함되어 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88dc53378e7e06d0a7d4ad362f7bb3876e186c80
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899708"
---
# <a name="project-model-core-components"></a>프로젝트 모델 핵심 구성 요소
다음 표는 프로젝트 모델에서 확장됩니다. 표에는 모델에서 식별된 인터페이스 및 서비스와 특정 개체와 연결된 인터페이스 및 서비스에 대한 간략한 설명이 있습니다. 또한 테이블은 특정 프로젝트 형식의 요구 사항에 따라 프로젝트 만들기 및 유지 관리에서 선택 사항인 다른 인터페이스에 대해 자세히 설명합니다.

 자세한 내용은 [Symbol-Browsing 도구 지원을 참조하세요.](../../extensibility/internals/supporting-symbol-browsing-tools.md)

### <a name="package-object"></a>패키지 개체

|인터페이스|의견|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE에서 VSPackage를 초기화하고 해당 서비스를 IDE에서 사용할 수 있도록 합니다.|

### <a name="project-factory-object"></a>Project Factory 개체

|인터페이스|의견|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|새 프로젝트를 만들고 기존 프로젝트를 여는 것을 관리합니다.|

### <a name="project-objects"></a>프로젝트 개체

|인터페이스|의견|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|프로젝트 항목의 추가 및 제거를 관리하고, 편집기를 열고, 각 문서 모니커와 간의 매핑을 유지 `VSITEMID` 관리합니다. 및 에서 `IVsProject` `IVsProject2` 상속됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|탐색 및 표시 속성을 관리하고 이벤트를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|`IOleCommandTarget`포커스가 솔루션 탐색기 경우에만 적용되는 잘라내기 및 이름 바꾸기와 같은 명령에 대해 와 비슷한 명령을 실행하도록 설정합니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|프로젝트 계층 구조의 기본 명령 대상 인터페이스 역할을 합니다. 개체의 명령 상태 또는 상태를 쿼리하고 명령을 실행하기 위한 표준 인터페이스입니다. 프로젝트 창에 포커스가 없는 경우 사용할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|프로젝트 상태의 지속성을 조정합니다. 일반적으로 프로젝트 상태는 프로젝트 파일로 저장되지만 파일 기반이 아닌 스토리지 시스템에 적용할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|프로젝트가 디스크의 파일 또는 다른 스토리지 시스템의 개체로 프로젝트 항목에 대한 지속성의 모든 측면을 관리할 수 있도록 합니다. `IVsPersistHierarchyItem2`인터페이스는 인터페이스를 구현하지 않는 항목에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 사용됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|소스 코드 컨트롤과의 상호 작용을 조정합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|프로젝트에서 구성 정보를 관리할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|디버그/릴리스 구성과 같은 프로젝트 구성 개체를 관리합니다. 빌드, 배포 및 디버그 작업은 프로젝트 구성 개체를 통해 조정됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|계층 구조 항목에 대한 삭제(파괴적) 또는 제거(비파괴적) 옵션을 제어하기 위해 계층에 의해 구현됩니다. 인터페이스에서 인터페이스의 쿼리 `IVsHierarchyDeleteHandler` 인터페이스를 `IVsHierarchy` 호출합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|인터페이스를 구현하는 프로젝트 개체와 다른 COM ID에서 인터페이스를 지원하는 개체를 포함하는 구현 옵션을 `IVsCfgProvider2` `IVsHierarchy` 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|다른 개발자가 프로젝트를 실행할 수 있도록 구현된 선택적 인터페이스입니다. `IVsProjectStartupServices`인터페이스를 사용하면 타사 VSPackage가 프로젝트 파일에 유지되는 GUID를 등록할 수 있으므로 프로젝트가 로드할 때마다 타사 서비스 GUID를 프로젝트 파일에 로드하고 해당 GUID를 호출할 수 `QueryService` 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|`UIHierarchy`잘라내기, 복사 및 붙여넣기와 같은 클립보드 작업을 조정하기 위해 창의 원본 계층에 의해 구현됩니다. 인터페이스를 사용하여 `AdviseClipboardHelperEvents` 클립보드 이벤트를 등록합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|UI 계층 구조 창에서 끌어서 놓기 작업 중에 데이터 원본을 기준으로 끌어서 놓는 항목에 대한 정보를 제공합니다. `IVsHierarchy`인터페이스에서 호출됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|UI 계층 구조 창에서 끌어서 놓기 작업 중에 놓기 대상을 기준으로 끌어서 놓기 항목에 대한 정보를 제공합니다. `IVsHierarchy`인터페이스에서 호출됩니다.|

### <a name="configuration-object"></a>구성 개체

|인터페이스|의견|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|구성에 대한 정보를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|프로젝트에서 구성 정보를 관리할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|디버거의 제어 하에 프로젝트를 실행할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|다른 프로젝트에 대한 배포 작업을 수행하는 배포 프로젝트에 의해 구현됩니다.|

### <a name="configuration-builder-object"></a>Configuration Builder 개체

|인터페이스|의견|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|프로젝트 구성의 빌드 작업을 관리합니다.|

### <a name="additional-project-objects"></a>추가 Project 개체

|인터페이스|의견|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|**속성** 창에 항목 속성을 표시합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|배포에 대한 출력을 표시합니다.|

 다음 표에서는 프로젝트 모델에서 식별된 서비스에 대한 간략한 설명을 제공합니다.

### <a name="services"></a>서비스

|서비스|의견|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|프로젝트 형식을 구현하여 프로젝트 팩터리 가 IDE에 있는지 등록하는 VSPackage에서 사용됩니다. VSPackage는 이 서비스에 대해 를 `QueryService` 호출하고 메서드가 호출되면 해당 프로젝트 팩터리 를 등록해야 `IVsPackage::SetSite` 합니다. `SetSite`메서드가 호출되지 않으면 프로젝트가 인스턴스화되지 않습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|프로젝트를 열거하고, 새 프로젝트를 만들고, 프로젝트 변경 내용을 주의를 기울이는 기능 등 현재 솔루션에 대한 IDE의 내부 기본 제공 개념에 대한 액세스를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|소스 제어에 참여하려는 프로젝트에서 호출합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|열려 있는 문서 테이블을 유지 관리하여 하나 이상의 프로젝트 항목이 이미 열려 있는지 여부를 확인합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|표준 편집기 또는 특정 편집기를 사용하여 프로젝트 항목을 실제로 열기 위해 호출된 인터페이스 및 메서드를 포함합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|모든 프로젝트에서 항목을 추가, 제거 또는 이름을 바꿀 때 호출해야 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|파일 또는 디렉터리에 대한 변경 내용을 관리하고 선택한 파일이 디스크에서 변경된 경우 클라이언트에 알린 다음|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|모든 프로젝트와 편집기에서 항목을 더티하거나 저장하기 전에 호출해야 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|프로젝트 구성에 대한 빌드 및 배포 작업의 순서를 관리합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|대부분의 디버깅 컨트롤에 사용되는 낮은 수준의 디버거 서비스에 대한 액세스를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|VSPackage가 현재 선택 항목에 대한 정보에 액세스할 수 있도록 하고 **속성** 창과의 통신을 사용하도록 설정합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|도구 창이나 문서 창을 만들고 열거하거나 사용자에게 오류를 보고하는 기능과 같은 기본 UI 관련 IDE 기능을 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE의 상태 표시줄에 대한 액세스를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|자동화 모델을 구현하는 데 사용됩니다. 프로젝트 모델에서 해당 개체의 인스턴스를 만들 수 있는 속성 개체를 반환합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|계층 구조의 프로젝트 개체에서 클립보드 이벤트를 구현하는 데 사용됩니다. `SVsUIHierWinClipboardHelper` 를 사용하면 잘라내기, 복사 및 붙여넣기 작업을 올바르게 처리할 수 있습니다.|

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [빌드에 없는 경우: HierUtil7 프로젝트 클래스를 사용하여 프로젝트 형식 구현(C++)](/previous-versions/bb166212(v=vs.100))
- [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)