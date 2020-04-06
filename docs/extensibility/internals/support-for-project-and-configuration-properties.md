---
title: 프로젝트 및 구성 속성 지원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704895"
---
# <a name="support-for-project-and-configuration-properties"></a>프로젝트 및 구성 속성 지원
통합 **Properties** 개발 환경(IDE)의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 속성 창은 프로젝트 및 구성 속성을 표시할 수 있습니다. 사용자가 응용 프로그램에 대한 속성을 설정할 수 있도록 사용자 고유의 프로젝트 유형에 대한 속성 페이지를 제공할 수 있습니다.

 **솔루션 탐색기에서** 프로젝트 노드를 선택한 다음 **프로젝트** 메뉴에서 **속성을** 클릭하여 프로젝트 및 구성 속성을 포함하는 대화 상자를 열 수 있습니다. 및 및 프로젝트 형식에서 이러한 언어에서 파생 된 이 대화 상자는 [일반, 환경, 옵션 대화 상자의](../../ide/reference/general-environment-options-dialog-box.md)탭 페이지로 나타납니다. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 자세한 내용은 [빌드: 연습: 프로젝트 및 구성 속성 노출(C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)을 참조하십시오.

 MPFProj(프로젝트용 관리되는 패키지 프레임워크)는 새 프로젝트 시스템을 만들고 관리하기 위한 도우미 클래스를 제공합니다. 프로젝트에 대 한 MPF에서 소스 코드 및 컴파일 지침을 찾을 수 [있습니다-Visual Studio 2013.](https://github.com/tunnelvisionlabs/MPFProj10)

## <a name="persistence-of-project-and-configuration-properties"></a>프로젝트 및 구성 속성의 지속성
 프로젝트 및 구성 속성은 프로젝트 유형과 관련된 파일 이름 확장명이 있는 프로젝트 파일(예: .csproj, .vbproj 및 .myproj)에 유지됩니다. 언어 프로젝트는 일반적으로 템플릿 파일을 사용하여 프로젝트 파일을 생성합니다. 그러나 실제로 프로젝트 유형 과 템플릿을 연결하는 방법에는 여러 가지가 있습니다. 자세한 내용은 [템플릿 디렉터리 설명(를 참조하십시오. Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 프로젝트 및 구성 속성은 템플릿 파일에 항목을 추가하여 만들어집니다. 그런 다음 이 템플릿을 사용하는 프로젝트 형식을 사용하여 만든 모든 프로젝트에서 이러한 속성을 사용할 수 있습니다. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]프로젝트와 MPFProj 모두 템플릿 파일에 [대한 빌드: MSBuild 개요 스키마를](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) 사용하지 않음을 사용합니다. 이러한 파일에는 각 구성에 대한 속성 그룹 섹션이 있습니다. 프로젝트의 속성은 일반적으로 null 문자열로 설정된 Configuration 인수가 있는 첫 번째 PropertyGroup 섹션에서 유지됩니다.

 다음 코드는 기본 MSBuild 프로젝트 파일의 시작을 보여 주며, 기본 MSBuild 프로젝트 파일의 시작을 보여 주며, 이 코드는 기본 MSBuild 프로젝트 파일의 시작을 보여 주며,

```
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Name>SomeProjectSix</Name>
    <SchemaVersion>2.0</SchemaVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
    <Optimize>false</Optimize>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <Optimize>true</Optimize>
```

 이 프로젝트 파일에서 프로젝트 `<Name>` `<SchemaVersion>` 속성이며 `<Optimize>` 구성 속성입니다.

 프로젝트 파일의 프로젝트 및 구성 속성을 유지하는 것은 프로젝트의 책임입니다.

> [!NOTE]
> 프로젝트는 기본값과 다른 속성 값만 유지하여 지속성을 최적화할 수 있습니다.

## <a name="support-for-project-and-configuration-properties"></a>프로젝트 및 구성 속성 지원
 클래스는 `Microsoft.VisualStudio.Package.SettingsPage` 프로젝트 및 구성 속성 페이지를 구현합니다. 기본 구현은 `SettingsPage` 일반 속성 그리드의 사용자에게 공용 속성을 제공합니다. 메서드는 `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` 프로젝트 속성 그리드에 `SettingsPage` 대해 파생된 클래스를 선택합니다. 메서드는 `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` 구성 속성 그리드에 `SettingsPage` 대해 파생된 클래스를 선택합니다. 프로젝트 유형은 이러한 메서드를 재정의하여 적절한 속성 페이지를 선택해야 합니다.

 클래스와 `SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` 클래스는 프로젝트 및 구성 속성을 유지하도록 다음 메서드를 제공합니다.

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`및 `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` 프로젝트 속성을 유지합니다.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`및 `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` 구성 속성을 유지합니다.

  > [!NOTE]
  > 및 클래스의 구현은 (MSBuild) 메서드를 `Microsoft.Build.BuildEngine` 사용하여 프로젝트 파일에서 프로젝트 및 구성 속성을 가져옵니다. `Microsoft.VisualStudio.Package.ProjectNode` `Microsoft.VisualStudio.Package.SettingsPage`

  파생된 클래스는 `SettingsPage` 프로젝트 `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` 파일의 프로젝트 또는 구성 속성을 구현하고 유지해야 합니다.

## <a name="provideobjectattribute-and-registry-path"></a>제공개체 속성 및 레지스트리 경로
 파생된 `SettingsPage` 클래스는 VSPackage에서 공유하도록 설계되었습니다. VSPackage에서 파생된 클래스를 만들 수 있도록 `SettingsPage`하려면 `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` 에서 파생된 클래스에 `Microsoft.VisualStudio.Shell.Package`a를 추가합니다.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 특성이 연결된 VS패키지는 중요하지 않습니다. VSPackage에 등록 될 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]때 만들 수 있는 모든 개체의 클래스 ID (CLSID) <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> 호출을 만들 수 있도록 등록 됩니다.

 만들 수 있는 개체의 레지스트리 경로는 개체 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>형식의 단어, CLSID 및 guid를 결합하여 결정됩니다. 클래스에 {3c693da2-5bca-49ba-bd95-ffe0a39d723}의 guid가 있고 사용자레지스트리루트가 HKEY_CURRENT_USER\Software\VisualStudio\8.0Exp인 경우, `MyProjectPropertyPage` 그런 다음 레지스트리 경로는 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39d723}입니다.

## <a name="project-and-configuration-property-attributes-and-layout"></a>프로젝트 및 구성 속성 속성 및 레이아웃
 의 <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute>및 <xref:System.ComponentModel.DescriptionAttribute> 특성은 일반 속성 페이지에서 프로젝트 및 구성 속성의 레이아웃, 레이블 지정 및 설명을 결정합니다. 이러한 특성은 옵션의 범주, 표시 이름 및 설명을 각각 결정합니다.

> [!NOTE]
> 동등한 특성, SRCategory, LocDisplayName 및 SRDescription는 지역화를 위해 문자열 리소스를 사용하고 [프로젝트용 MPF - Visual Studio 2013에](https://github.com/tunnelvisionlabs/MPFProj10)정의됩니다.

 다음과 같은 코드 조각을 생각해 봅시다.

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 구성 `MyConfigProp` 속성은 구성 속성 페이지에 내 범주, 내 **범주의** **내 구성 속성으로** 나타납니다. 옵션을 선택하면 설명, 내 **설명이**설명 패널에 나타납니다.

## <a name="see-also"></a>참조
- [속성 페이지 추가 및 제거](../../extensibility/adding-and-removing-property-pages.md)
- [프로젝트](../../extensibility/internals/projects.md)
- [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
