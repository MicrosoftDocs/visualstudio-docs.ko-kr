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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704284"
---
# <a name="using-msbuild"></a>MSBuild 사용
MSBuild는 빌드할 프로젝트 항목을 완전히 설명하고, 작업을 빌드하고, 구성을 빌드하는 프로젝트 파일을 만들기 위한 잘 정의된 확장 가능한 XML 형식을 제공합니다.

## <a name="general-msbuild-considerations"></a>일반 MSBuild 고려 사항
 MSBuild 프로젝트 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 파일(예: .csproj 및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj files)에는 빌드 시 사용되는 데이터가 포함되어 있지만 디자인 타임에 사용되는 데이터도 포함될 수 있습니다. 빌드 시간 데이터는 [항목 요소(MSBuild)](../../msbuild/item-element-msbuild.md) 및 [속성 요소(MSBuild)를](../../msbuild/property-element-msbuild.md)포함하여 MSBuild 프리미티브를 사용하여 저장됩니다. 프로젝트 유형 및 관련 프로젝트 하위 유형과 관련된 데이터인 디자인 타임 데이터는 이를 위해 예약된 자유 형식 XML에 저장됩니다.

 MSBuild는 구성 개체에 대한 기본 지원이 없지만 구성 별 데이터를 지정하기 위한 조건부 특성을 제공합니다. 다음은 그 예입니다.

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 조건부 특성에 대한 자세한 내용은 [조건부 구문](../../msbuild/msbuild-conditional-constructs.md)입니다.

### <a name="extending-msbuild-for-your-project-type"></a>프로젝트 유형에 대한 MSBuild 확장
 MSBuild 인터페이스 및 API는 이후 버전에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]변경될 수 있습니다. 따라서 관리되는 패키지 프레임워크(MPF) 클래스는 변경으로부터 차폐를 제공하기 때문에 사용하는 것이 신중합니다.

 MPFProj(프로젝트용 관리되는 패키지 프레임워크)는 새 프로젝트 시스템을 만들고 관리하기 위한 도우미 클래스를 제공합니다. 프로젝트에 대 한 MPF에서 소스 코드 및 컴파일 지침을 찾을 수 [있습니다-Visual Studio 2013.](https://github.com/tunnelvisionlabs/MPFProj10)

 프로젝트별 MPF 클래스는 다음과 같습니다.

|클래스|구현|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`클래스는 MSBuild 항목의 래퍼입니다.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>단일 파일 생성기 vs. MSBuild 작업
 단일 파일 생성기는 디자인 타임에만 액세스할 수 있지만 MSBuild 작업은 디자인 타임 및 빌드 시간에 사용할 수 있습니다. 따라서 유연성을 극대화하려면 MSBuild 작업을 사용하여 코드를 변환하고 생성합니다. 자세한 내용은 [사용자 지정 도구를](../../extensibility/internals/custom-tools.md)참조하십시오.

## <a name="see-also"></a>참조
- [MSBuild 참조](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [사용자 지정 도구](../../extensibility/internals/custom-tools.md)
