---
title: Project Model 핵심 구성 요소 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706533"
---
# <a name="project-model-core-components"></a>프로젝트 모델 핵심 구성 요소
다음 표에서는 프로젝트 모델을 확장 합니다. 테이블에는 모델에서 식별 된 인터페이스 및 서비스에 대 한 간략 한 설명과 특정 개체와 관련 된 인터페이스 및 서비스가 있습니다. 또한 표에는 특정 프로젝트 형식에 대 한 요구 사항에 따라 프로젝트 생성 및 유지 관리에서 선택적으로 사용할 수 있는 다른 인터페이스가 자세히 나와 있습니다.

 자세한 내용은 [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)을 참조 하세요.

### <a name="package-object"></a>Package 개체

|인터페이스|주석|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE에서 VSPackage를 초기화 하 고 IDE에서 해당 서비스를 사용할 수 있도록 합니다.|

### <a name="project-factory-object"></a>프로젝트 팩터리 개체

|인터페이스|주석|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|새 프로젝트 만들기 및 기존 프로젝트 열기를 관리 합니다.|

### <a name="project-objects"></a>Project 개체

|인터페이스|주석|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|프로젝트 항목의 추가 및 제거를 관리 하 고, 편집기를 열고, 각 문서 모니커와 간의 매핑을 유지 관리 합니다 `VSITEMID` . 는 및에서 상속 `IVsProject` `IVsProject2` 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|탐색 및 표시 속성을 관리 하 고 이벤트를 제공 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|`IOleCommandTarget`포커스가 솔루션 탐색기에 있는 경우에만 적용 되는 잘라내기 및 이름 바꾸기와 같은 명령의 경우와 유사 하 게 명령 실행을 사용 하도록 설정 합니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|프로젝트 계층 구조에 대 한 기본 명령 대상 인터페이스로 사용 됩니다. 명령 상태 또는 상태 및 실행 명령에 대 한 개체를 쿼리 하는 표준 인터페이스입니다. 프로젝트 창에 포커스가 없는 경우 사용할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|프로젝트 상태에 대 한 지 속성을 조정 합니다. 일반적으로 프로젝트 상태는 프로젝트 파일로 저장 되지만 파일 기반이 아닌 저장소 시스템에 맞게 조정 될 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|프로젝트에서 해당 프로젝트 항목의 모든 요소를 디스크의 파일 또는 다른 저장소 시스템의 개체와 함께 관리할 수 있도록 합니다. 인터페이스는 `IVsPersistHierarchyItem2` 인터페이스를 구현 하지 않는 항목에 사용 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|소스 코드 제어를 사용 하 여 상호 작용을 조정 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|프로젝트에서 구성 정보를 관리할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|디버그/릴리스 구성과 같은 프로젝트 구성 개체를 관리 합니다. 빌드, 배포 및 디버그 작업은 프로젝트 구성 개체를 통해 조정 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|계층 항목에 대 한 삭제 (소거식) 또는 제거 (비 소거식) 옵션을 제어 하기 위해 계층에 의해 구현 됩니다. 인터페이스에서 인터페이스에 대 한 쿼리 인터페이스를 호출 `IVsHierarchyDeleteHandler` `IVsHierarchy` 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|인터페이스를 `IVsCfgProvider2` 구현 하는 프로젝트 개체와 다른 COM id에서 인터페이스를 지 원하는 개체를 구현 하는 옵션을 제공 합니다 `IVsHierarchy` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|다른 개발자가 프로젝트를 확장할 수 있도록 구현 된 선택적 인터페이스입니다. 인터페이스를 사용 하면 타사 `IVsProjectStartupServices` VSPackage 프로젝트 파일에 유지 하는 guid를 등록 하 여 프로젝트를 로드할 때마다 타사 서비스 GUID를 프로젝트 파일에 로드 하 고 `QueryService` 해당 guid에 대해를 호출할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|`UIHierarchy`잘라내기, 복사, 붙여넣기 등의 클립보드 작업을 조정 하기 위해 창에서 소스 계층에 의해 구현 됩니다. 인터페이스를 사용 `AdviseClipboardHelperEvents` 하 여 클립보드 이벤트를 등록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|UI 계층 구조 창에서 끌어서 놓기 작업을 수행 하는 동안 데이터 소스를 기준으로 끌어 온 항목에 대 한 정보를 제공 합니다. 인터페이스에서 호출 `IVsHierarchy` 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|UI 계층 구조 창에서 끌어서 놓기 작업을 수행 하는 동안 끌어 놓기 대상에 상대적인 끌어 온 항목에 대 한 정보를 제공 합니다. 인터페이스에서 호출 `IVsHierarchy` 됩니다.|

### <a name="configuration-object"></a>구성 개체

|인터페이스|주석|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|구성에 대 한 정보를 제공 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|프로젝트에서 구성 정보를 관리할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|디버거를 제어 하 여 프로젝트를 실행할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|다른 프로젝트에 대 한 배포 작업을 수행 하는 배포 프로젝트에 의해 구현 됩니다.|

### <a name="configuration-builder-object"></a>구성 작성기 개체

|인터페이스|주석|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|프로젝트 구성의 빌드 작업을 관리 합니다.|

### <a name="additional-project-objects"></a>추가 프로젝트 개체

|인터페이스|주석|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|**속성** 창에 항목 속성을 표시 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|배포에 대 한 출력을 표시 합니다.|

 다음 표에서는 프로젝트 모델에서 식별 된 서비스에 대 한 간략 한 설명을 제공 합니다.

### <a name="services"></a>Services

|서비스|주석|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Vspackage에서 프로젝트 형식을 구현 하 여 IDE에 프로젝트 팩터리가 존재 함을 등록 하는 데 사용 됩니다. VSPackage `QueryService` 는이 서비스에 대해를 호출 하 고 `IVsPackage::SetSite` 메서드를 호출할 때 해당 프로젝트 팩터리를 등록 해야 합니다. 메서드를 `SetSite` 호출 하지 않으면 프로젝트가 인스턴스화되지 않습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|프로젝트를 열거 하 고, 새 프로젝트를 만들고, 프로젝트 변경 내용을 확인 하는 등 현재 솔루션에 대 한 IDE의 내부 기본 제공 개념에 대 한 액세스를 제공 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|소스 제어에 참여 하려는 프로젝트에 의해 호출 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|하나 이상의 프로젝트 항목이 이미 열려 있는지 여부를 확인 하기 위해 열려 있는 문서 테이블을 유지 관리 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|표준 편집기나 특정 편집기를 사용 하 여 프로젝트 항목을 실제로 열기 위해 호출 되는 인터페이스 및 메서드를 포함 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|항목을 추가, 제거 또는 이름을 바꿀 때 모든 프로젝트에서 호출 해야 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|파일이 나 디렉터리에 대 한 변경 내용을 관리 하 고 디스크에서 선택한 파일이 변경 되 면 클라이언트에 알립니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|모든 프로젝트와 편집기에서 항목을 변경 하거나 저장 하기 전에 호출 해야 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|프로젝트 구성에 대 한 빌드 및 배포 작업의 순서를 관리 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|대부분의 디버깅 컨트롤에 사용 되는 하위 수준 디버거 서비스에 대 한 액세스를 제공 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|현재 선택 항목에 대 한 정보에 대 한 Vspackage 액세스를 사용 하도록 설정 하 고 **속성** 창과 통신할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|도구 창이 나 문서 창을 만들거나 열거 하거나 사용자에 게 오류를 보고 하는 기능과 같은 기본적인 UI 관련 IDE 기능을 제공 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE의 상태 표시줄에 대 한 액세스를 제공 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|자동화 모델을 구현 하는 데 사용 됩니다. 프로젝트 모델에서이 개체의 인스턴스를 만들 수 있는 속성 개체를 반환 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|계층의 프로젝트 개체에 대해 클립보드 이벤트를 구현 하는 데 사용 됩니다. `SVsUIHierWinClipboardHelper` 잘라내기, 복사 및 붙여넣기 작업을 올바르게 처리할 수 있습니다.|

## <a name="see-also"></a>추가 정보
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [빌드에 없음: HierUtil7 프로젝트 클래스를 사용 하 여 프로젝트 형식 구현 (c + +)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)
