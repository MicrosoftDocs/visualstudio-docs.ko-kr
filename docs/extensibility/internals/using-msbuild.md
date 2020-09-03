---
title: MSBuild 사용 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704284"
---
# <a name="using-msbuild"></a>MSBuild 사용
MSBuild는 빌드할 프로젝트 항목을 완벽 하 게 설명 하는 프로젝트 파일을 만들기 위한 잘 정의 된 확장 가능한 XML 형식을 제공 합니다.

## <a name="general-msbuild-considerations"></a>일반 MSBuild 고려 사항
 .Csproj와 .vbproj 파일 등의 MSBuild 프로젝트 파일에 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 는 빌드 시에 사용 되는 데이터가 포함 되지만 디자인 타임에 사용 되는 데이터도 포함 될 수 있습니다. 빌드 시간 데이터는 [Item 요소 (msbuild)](../../msbuild/item-element-msbuild.md) 및 [Property 요소 (msbuild)](../../msbuild/property-element-msbuild.md)를 비롯 한 msbuild 기본 형식을 사용 하 여 저장 됩니다. 프로젝트 형식 및 관련 된 프로젝트 하위 형식에 해당 하는 데이터 인 디자인 타임 데이터는 해당 데이터에 대해 예약 된 자유 형식 XML로 저장 됩니다.

 MSBuild는 구성 개체에 대 한 기본 지원을 제공 하지 않지만 구성 관련 데이터를 지정 하기 위한 조건부 특성을 제공 합니다. 예를 들면 다음과 같습니다.

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 조건부 특성에 대 한 자세한 내용은 [조건부 구문](../../msbuild/msbuild-conditional-constructs.md)을 참조 하세요.

### <a name="extending-msbuild-for-your-project-type"></a>프로젝트 형식에 대 한 MSBuild 확장
 MSBuild 인터페이스 및 Api는 이후 버전의에서 변경 될 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 따라서 MPF (관리 패키지 프레임 워크) 클래스는 변경 으로부터 차폐를 제공 하기 때문에이 클래스를 사용 하는 것이 좋습니다.

 프로젝트에 대 한 관리 패키지 프레임 워크 (MPFProj)는 새 프로젝트 시스템을 만들고 관리 하기 위한 도우미 클래스를 제공 합니다. [프로젝트에 대 한 MPF](https://github.com/tunnelvisionlabs/MPFProj10)에서 소스 코드 및 컴파일 지침-Visual Studio 2013를 찾을 수 있습니다.

 프로젝트별 MPF 클래스는 다음과 같습니다.

|클래스|구현|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` 클래스는 MSBuild 항목에 대 한 래퍼입니다.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>단일 파일 생성기 및 MSBuild 작업
 디자인 타임에만 단일 파일 생성기에 액세스할 수 있지만 디자인 타임 및 빌드 시에는 MSBuild 작업을 사용할 수 있습니다. 따라서 유연성을 최대화 하기 위해 MSBuild 작업을 사용 하 여 코드를 변환 하 고 생성 합니다. 자세한 내용은 [사용자 지정 도구](../../extensibility/internals/custom-tools.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [MSBuild 참조](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [사용자 지정 도구](../../extensibility/internals/custom-tools.md)
