---
title: '관리 되는 패키지 프레임 워크를 사용 하 여 프로젝트 형식 구현 (c #) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 066695c6d94603d0a0474243ed05dece4cc0bd1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300366"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>관리 패키지 프레임워크를 사용하여 프로젝트 형식 구현(C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

MPF (관리 되는 패키지 프레임 워크)는 사용자 고유의 프로젝트 형식을 구현 하기 위해에서 사용 하거나 상속할 수 있는 c # 클래스를 제공 합니다. MPF는 Visual Studio에서 제공 하는 프로젝트 형식이 필요한 많은 인터페이스를 구현 하며 프로젝트 형식의 인스턴스와 관련 사항을 구현에 집중할 수 있습니다.  
  
## <a name="using-the-mpf-project-source-code"></a>MPF 프로젝트 소스 코드 사용  
 프로젝트에 대 한 관리 패키지 프레임 워크 (MPFProj)는 새 프로젝트 시스템을 만들고 관리 하기 위한 도우미 클래스를 제공 합니다. MPF의 다른 클래스와 달리 프로젝트 클래스는 Visual Studio와 함께 제공 되는 어셈블리에 포함 되지 않습니다. 대신 프로젝트 클래스는 프로젝트 [2013에 대 한 MPF](https://archive.codeplex.com/?p=mpfproj12)에서 소스 코드로 제공 됩니다.  
  
 VSPackage 솔루션에이 프로젝트를 추가 하려면 다음을 수행 합니다.  
  
1. *Mpfprojectdir*에 MPFProj 파일을 다운로드 합니다.  
  
2. *Mpfprojectdir*\Dev10\Src\CSharp\ProjectBase.file에서 다음 블록을 변경 합니다.  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1. VSPackage 프로젝트를 만듭니다.  
  
2. VSPackage 프로젝트를 언로드합니다.  
  
3. 다른 블록 앞에 다음 블록을 추가 하 여 VSPackage 파일을 편집 합니다 `<Import>` .  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1. 프로젝트를 저장합니다.  
  
2. VSPackage 솔루션을 닫았다가 다시 엽니다.  
  
3. VSPackage 프로젝트를 다시 엽니다. ProjectBase 라는 새 디렉터리가 표시 되어야 합니다.  
  
4. VSPackage 프로젝트에 다음 참조를 추가 합니다.  
  
     Microsoft. 빌드. 작업 4.0  
  
5. 프로젝트를 빌드합니다.  
  
## <a name="hierarchy-classes"></a>계층 클래스  
 다음 표에서는 프로젝트 계층 구조를 지 원하는 MPFProj의 클래스를 요약 합니다. 자세한 내용은 [계층 및 선택](../../extensibility/internals/hierarchies-and-selection.md)을 참조 하세요.  
  
|클래스 이름|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>문서 처리 클래스  
 다음 표에서는 문서 처리를 지 원하는 MPF의 클래스를 나열 합니다. 자세한 내용은 [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)을 참조 하세요.  
  
|클래스 이름|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>구성 및 출력 클래스  
 다음 표에서는 프로젝트 형식에서 디버그 및 릴리스와 같은 여러 구성 및 프로젝트 출력 컬렉션을 지원할 수 있도록 하는 MPF의 클래스를 나열 합니다. 자세한 내용은 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)를 참조 하세요.  
  
|클래스 이름|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>자동화 지원 클래스  
 다음 표에서는 프로젝트 형식의 사용자가 추가 기능을 쓸 수 있도록 자동화를 지 원하는 MPF의 클래스를 나열 합니다.  
  
|클래스 이름|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>속성 클래스  
 다음 표에서는 프로젝트 형식에서 사용자가 속성 브라우저에서 찾아보고 수정할 수 있는 속성을 추가할 수 있게 해 주는 MPF의 클래스를 나열 합니다.  
  
|클래스 이름|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
