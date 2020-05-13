---
title: 프로젝트 모델 핵심 구성요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706533"
---
# <a name="project-model-core-components"></a>프로젝트 모델 핵심 구성 요소
다음 테이블은 프로젝트 모델에서 확장됩니다. 표에서는 모델에서 식별된 인터페이스 및 서비스 및 특정 개체와 연결된 인터페이스 및 서비스에 대한 간략한 설명을 제공합니다. 또한 이 표는 특정 프로젝트 유형의 요구 사항에 따라 프로젝트 생성 및 유지 관리에서 선택 사항인 다른 인터페이스를 자세히 설명합니다.

 자세한 내용은 [심볼 브라우징 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)을 참조하십시오.

### <a name="package-object"></a>패키지 개체

|인터페이스|주석|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE에서 VSPackage를 초기화하고 해당 서비스를 IDE에서 사용할 수 있도록 합니다.|

### <a name="project-factory-object"></a>프로젝트 팩터리 개체

|인터페이스|주석|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|새 프로젝트를 만들고 기존 프로젝트를 여는 것을 관리합니다.|

### <a name="project-objects"></a>프로젝트 객체

|인터페이스|주석|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|프로젝트 항목의 추가 및 제거를 관리하고, 편집기 열기 및 각 문서 `VSITEMID`모니커와 . 에서 `IVsProject` 상속합니다. `IVsProject2`|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|탐색 및 표시 속성을 관리하고 이벤트를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|포커스가 솔루션 탐색기에 `IOleCommandTarget` 있을 때만 적용되는 잘라내기 및 이름 바꾸기와 같은 명령의 명령 실행과 유사한 명령 실행을 활성화합니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|프로젝트 계층 구조에 대 한 기본 명령 대상 인터페이스역할을 합니다. 명령 상태 또는 상태에 대한 개체를 쿼리하고 명령을 실행하는 표준 인터페이스입니다. 프로젝트 창에 포커스가 없는 경우에 사용할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|프로젝트 상태의 지속성을 조정합니다. 일반적으로 프로젝트 상태는 프로젝트 파일로 저장되지만 파일 기반이 아닌 저장소 시스템에 맞게 조정할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|프로젝트를 사용하여 디스크의 파일이나 다른 저장소 시스템의 개체와 같이 프로젝트 항목에 대한 지속성의 모든 측면을 관리할 수 있습니다. 인터페이스는 `IVsPersistHierarchyItem2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 인터페이스를 구현하지 않는 항목에 사용됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|소스 코드 제어와의 상호 작용을 조정합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|프로젝트가 구성 정보를 관리할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|디버그/릴리스 구성과 같은 프로젝트 구성 개체를 관리합니다. 빌드, 배포 및 디버그 작업은 프로젝트 구성 개체를 통해 조정됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|계층 구조에 의해 구현되어 계층 항목에 대한 삭제(파괴) 또는 제거(비파괴) 옵션을 제어합니다. 인터페이스에서 인터페이스에 `IVsHierarchyDeleteHandler` 쿼리 `IVsHierarchy` 인터페이스를 호출합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|인터페이스를 구현하는 `IVsHierarchy` 프로젝트 개체와 다른 `IVsCfgProvider2` COM ID의 인터페이스를 지원하는 개체를 갖는 구현 옵션을 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|다른 개발자가 프로젝트를 확장 할 수 있도록 구현 된 선택적 인터페이스. 이 `IVsProjectStartupServices` 인터페이스를 사용하면 타사 VSPackage에서 프로젝트 파일에 유지되는 GUID를 등록할 수 있으므로 프로젝트가 로드될 때마다 타사 서비스 GUID를 프로젝트 파일에 로드하고 해당 GUID를 호출할 `QueryService` 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|`UIHierarchy` 창의 소스 계층구조에 의해 구현되어 잘라내기, 복사 및 붙여넣기와 같은 클립보드 작업을 조정합니다. 인터페이스를 `AdviseClipboardHelperEvents` 사용하여 클립보드 이벤트를 등록합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|UI 계층 구조 창에서 끌어서 놓기 작업 하는 동안 데이터 원본을 기준으로 드래그된 항목에 대 한 정보를 제공 합니다. 인터페이스에서 `IVsHierarchy` 호출됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|UI 계층 구조 창에서 끌어서 놓기 작업 중에 끌어놓기 대상을 기준으로 드래그된 항목에 대한 정보를 제공합니다. 인터페이스에서 `IVsHierarchy` 호출됩니다.|

### <a name="configuration-object"></a>구성 개체

|인터페이스|주석|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|구성에 대한 정보를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|프로젝트가 구성 정보를 관리할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|디버거의 제어하에 프로젝트를 실행할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|다른 프로젝트에 대한 배포 작업을 수행하는 배포 프로젝트에 의해 구현됩니다.|

### <a name="configuration-builder-object"></a>구성 빌더 개체

|인터페이스|주석|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|프로젝트 구성의 빌드 작업을 관리합니다.|

### <a name="additional-project-objects"></a>추가 프로젝트 객체

|인터페이스|주석|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|**속성** 창에 항목 속성을 표시합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|배포를 위한 출력을 표시합니다.|

 다음 표에서는 프로젝트 모델에서 식별된 서비스에 대한 간략한 설명을 제공합니다.

### <a name="services"></a>Services

|서비스|주석|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|프로젝트 형식을 구현하는 VSPackage에서 프로젝트 팩터리가 IDE에 있는 것을 등록하는 데 사용됩니다. VSPackage 는 `QueryService` 메서드가 호출될 때 `IVsPackage::SetSite` 이 서비스를 호출하고 프로젝트 팩터리를 등록해야 합니다. 메서드가 `SetSite` 호출되지 않으면 프로젝트가 인스턴스화되지 않습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|프로젝트를 개명하고, 새 프로젝트를 만들고, 프로젝트 변경 사항을 주의하는 기능 등과 같이 현재 솔루션에 대한 IDE의 기본 제공 개념에 대한 액세스를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|소스 제어에 참여하려는 프로젝트에서 호출합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|열려 있는 문서 테이블을 유지 관리하여 하나 이상의 프로젝트 항목이 이미 열려 있는지 확인합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|표준 편집기 또는 특정 편집기를 사용하여 실제로 프로젝트 항목을 여는 데 호출되는 인터페이스와 메서드를 포함합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|항목을 추가, 제거 또는 이름을 바꿀 때 모든 프로젝트에서 호출해야 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|파일 또는 디렉터리에 대한 변경 내용을 관리하고 디스크에서 선택한 파일이 변경되었을 때 클라이언트에 대해 보시기 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|항목을 더럽게 하거나 저장하기 전에 모든 프로젝트와 편집자가 호출해야 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|프로젝트 구성에 대한 빌드 및 배포 작업 순서를 관리합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|대부분의 디버깅 컨트롤에 사용되는 하위 수준 디버거 서비스에 대한 액세스를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|VSPackage가 현재 선택 항목에 대한 정보에 액세스할 수 있도록 하고 **속성** 창과 통신할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|도구 창 또는 문서 창을 만들고 개명하거나 사용자에게 오류를 보고하는 기능과 같은 기본 UI 관련 IDE 기능을 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE의 상태 표시줄에 대한 액세스를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|자동화 모델을 구현하는 데 사용됩니다. 프로젝트 모델에서 해당 개체의 인스턴스를 만들 수 있는 속성 개체를 반환합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|계층 구조의 프로젝트 개체에 클립보드 이벤트를 구현하는 데 사용됩니다. `SVsUIHierWinClipboardHelper`잘라내기, 복사 및 붙여넣기 작업을 올바르게 처리할 수 있습니다.|

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [빌드 중이지 않음: HierUtil7 프로젝트 클래스를 사용하여 프로젝트 유형 구현(C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)
