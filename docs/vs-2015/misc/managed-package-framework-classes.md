---
title: 관리 되는 패키지 프레임 워크 클래스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: 2e9fe1abb82d3d64232e3e5e2a6d117c1068aa1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297696"
---
# <a name="managed-package-framework-classes"></a>관리되는 패키지 프레임워크 클래스
MPF(관리되는 패키지 프레임워크) 클래스를 사용하여 관리 코드를 사용하는 Vspackage를 만들 수 있습니다. 이 클래스는 많은 VSPackage 인터페이스에 대한 기본 구현을 제공합니다. MPF는 구현 세부 정보 및 복잡성을 숨겨 최소한의 코드로 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 통합 제품을 만들 수 있습니다.  
  
> [!WARNING]
> 관리되는 패키지 프레임워크 클래스를 포함하는 어셈블리는 대부분 Visual Studio SDK와 함께 제공됩니다. [프로젝트에 대한 관리되는 패키지 프레임워크](https://archive.codeplex.com/?p=mpfproj11)에서 프로젝트에 대한 관리되는 패키지 프레임워크용 소스 코드를 다운로드할 수 있습니다.  
  
## <a name="mpf-namespaces"></a>MPF 네임스페이스  
 다음 표에서는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]에서 제공하는 MPF 네임스페이스 목록을 보여 줍니다.  
  
|네임스페이스|콘텐츠|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|COM 오류를 처리하기 위한 유용한 클래스, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 상수 및 Win32 창을 포함합니다.|  
|<xref:Microsoft.VisualStudio.Package>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트, 편집기 및 MSBuild에 대한 관리 코드 래퍼를 포함합니다.|  
|<xref:Microsoft.VisualStudio.Shell>|일반적인 Visual Studio의 여러 개체의 구현을 파생할 수 있는 MPF 기본 클래스를 포함합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디자이너 확장을 포함합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] serialization 디자이너 확장을 포함합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CodeDom 디자이너 확장을 포함합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|프로젝트 하위 형식("버전")을 지원합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [Vspackage 및 관리 패키지 프레임 워크](../misc/vspackages-and-the-managed-package-framework.md)   
 [Visual Studio Interop 어셈블리 사용](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackage 및 관리 패키지 프레임워크](../misc/vspackages-and-the-managed-package-framework.md)