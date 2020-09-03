---
title: 프로젝트 및 구성 속성에 대 한 지원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b03bc04b1d5b87219110aa65bee53c4a4a8f77e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301067"
---
# <a name="support-for-project-and-configuration-properties"></a>프로젝트 및 구성 속성 지원
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Properties** [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (통합 개발 환경)의 속성 창에는 프로젝트 및 구성 속성이 표시 될 수 있습니다. 사용자가 응용 프로그램에 대 한 속성을 설정할 수 있도록 고유한 프로젝트 형식에 대 한 속성 페이지를 제공할 수 있습니다.  
  
 **솔루션 탐색기** 에서 프로젝트 노드를 선택한 다음 **프로젝트** 메뉴에서 **속성** 을 클릭 하 여 프로젝트 및 구성 속성이 포함 된 대화 상자를 열 수 있습니다. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 이러한 언어에서 파생 된 및 및 프로젝트 형식에서이 대화 상자는 [일반, 환경, 옵션 대화 상자](../../ide/reference/general-environment-options-dialog-box.md)에 탭 페이지로 표시 됩니다. 자세한 내용은 [빌드에 없음: 연습: 프로젝트 및 구성 속성 노출 (c #)](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)을 참조 하세요.  
  
 프로젝트에 대 한 관리 패키지 프레임 워크 (MPFProj)는 새 프로젝트 시스템을 만들고 관리 하기 위한 도우미 클래스를 제공 합니다. [프로젝트에 대 한 MPF](https://archive.codeplex.com/?p=mpfproj12)에서 소스 코드 및 컴파일 지침-Visual Studio 2013를 찾을 수 있습니다.  
  
## <a name="persistence-of-project-and-configuration-properties"></a>프로젝트 및 구성 속성의 지 속성  
 프로젝트 및 구성 속성은 프로젝트 형식과 연결 된 파일 이름 확장명을 가진 프로젝트 파일에 저장 됩니다 (예: .csproj, .vbproj 및 .csproj). 언어 프로젝트는 일반적으로 템플릿 파일을 사용 하 여 프로젝트 파일을 생성 합니다. 그러나 실제로는 여러 가지 방법으로 프로젝트 형식과 템플릿을 연결할 수 있습니다. 자세한 내용은 [NIB: Visual Studio 템플릿](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) 및 [템플릿 디렉터리 설명 (을 참조 하세요. Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 프로젝트 및 구성 속성은 템플릿 파일에 항목을 추가 하 여 만듭니다. 그런 다음이 템플릿을 사용 하는 프로젝트 형식을 사용 하 여 만든 모든 프로젝트에서 이러한 속성을 사용할 수 있습니다. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 프로젝트와 MPFProj는 모두 [빌드에 없음:](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) 템플릿 파일에 대 한 MSBuild 개요 스키마를 사용 합니다. 이러한 파일에는 각 구성에 대 한 PropertyGroup 섹션이 있습니다. 일반적으로 프로젝트의 속성은 null 문자열로 설정 된 구성 인수를 포함 하는 첫 번째 PropertyGroup 섹션에 저장 됩니다.  
  
 다음 코드에서는 기본 MSBuild 프로젝트 파일의 시작을 보여 줍니다.  
  
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
  
 이 프로젝트 파일에서 `<Name>` 및 `<SchemaVersion>` 는 프로젝트 속성 이며 `<Optimize>` 는 구성 속성입니다.  
  
 프로젝트와 프로젝트 파일의 구성 속성을 유지 하는 것은 프로젝트의 책임입니다.  
  
> [!NOTE]
> 프로젝트는 기본값과 다른 속성 값만 유지 하 여 지 속성을 최적화할 수 있습니다.  
  
## <a name="support-for-project-and-configuration-properties"></a>프로젝트 및 구성 속성 지원  
 `Microsoft.VisualStudio.Package.SettingsPage`클래스는 프로젝트 및 구성 속성 페이지를 구현 합니다. 의 기본 구현은 `SettingsPage` 일반 속성 표에서 사용자에 게 공용 속성을 제공 합니다. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`메서드는 `SettingsPage` 프로젝트 속성 표에 대해에서 파생 된 클래스를 선택 합니다. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`메서드는 `SettingsPage` 구성 속성 표에 대해에서 파생 된 클래스를 선택 합니다. 프로젝트 형식은 이러한 메서드를 재정의 하 여 적절 한 속성 페이지를 선택 해야 합니다.  
  
 `SettingsPage`클래스와 클래스는 `Microsoft.VisualStudio.Package.ProjectNode` 다음 메서드를 제공 하 여 프로젝트 및 구성 속성을 유지 합니다.  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty``Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty`프로젝트 속성을 유지 합니다.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty``Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty`구성 속성을 유지 합니다.  
  
  > [!NOTE]
  > 및 클래스의 구현은 `Microsoft.VisualStudio.Package.SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` `Microsoft.Build.BuildEngine` (MSBuild) 메서드를 사용 하 여 프로젝트 파일에서 프로젝트 및 구성 속성을 가져오고 설정 합니다.  
  
  에서 파생 되는 클래스는 프로젝트 `SettingsPage` `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` 파일의 프로젝트 또는 구성 속성을 구현 하 고 유지 해야 합니다.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute 및 레지스트리 경로  
 에서 파생 된 클래스 `SettingsPage` 는 vspackage 간에 공유 되도록 설계 되었습니다. VSPackage가에서 파생 된 클래스를 만들 수 있도록 하려면 `SettingsPage` `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` 에서 파생 된 클래스에를 추가 `Microsoft.VisualStudio.Shell.Package` 합니다.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 특성이 연결 된 VSPackage는 중요 하지 않습니다. VSPackage가에 등록 되 면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 를 호출할 수 있도록 만들 수 있는 모든 개체의 CLSID (클래스 id)가 등록 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> .  
  
 만들 수 있는 개체의 레지스트리 경로는 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> 개체 형식의 guid와 단어, CLSID를 결합 하 여 결정 됩니다. `MyProjectPropertyPage`클래스의 guid가 {3c693da2-5bca-49b3-bd95-ffe0a39dd723}이 고 UserRegistryRoot HKEY_CURRENT_USER가 \software\microsoft\visualstudio\8.0exp 이면 레지스트리 경로는 \software\microsoft\visualstudio\8.0exp\clsid \\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723} HKEY_CURRENT_USER 됩니다.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>프로젝트 및 구성 속성 특성 및 레이아웃  
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute> 및 특성은 <xref:System.ComponentModel.DescriptionAttribute> 일반 속성 페이지에서 프로젝트 및 구성 속성의 레이아웃, 레이블 지정 및 설명을 결정 합니다. 이러한 특성은 옵션에 대 한 범주, 표시 이름 및 설명을 각각 결정 합니다.  
  
> [!NOTE]
> 동일한 특성, SRCategory, LocDisplayName 및 Srcategory은 지역화에 문자열 리소스를 사용 하 고, [프로젝트의 경우 MPF](https://archive.codeplex.com/?p=mpfproj12)에 정의 된 Visual Studio 2013 합니다.  
  
 다음과 같은 코드 조각을 생각해 봅시다.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 구성 `MyConfigProp` 속성은 구성 속성 페이지의 **내 구성** 속성으로 **내 범주**범주에 표시 됩니다. 이 옵션을 선택 하면 설명 패널에 설명, **내 설명이**표시 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [빌드에 없음: 연습: 프로젝트 및 구성 속성 노출 (c #)](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [속성 페이지 추가 및 제거](../../extensibility/adding-and-removing-property-pages.md)   
 [VSPackage 상태](../../misc/vspackage-state.md)   
 [프로젝트](../../extensibility/internals/projects.md)   
 [NIB: Visual Studio 템플릿](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
