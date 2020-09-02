---
title: 상태 지 속성 지원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434321"
---
# <a name="support-for-state-persistence"></a>상태 지속성 지원
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 공용 개체의 상태를 유지할 수 있습니다. 예를 들어 솔루션 및 프로젝트 속성은 솔루션 및 프로젝트 파일에 저장 되 고 복원 됩니다. 설정 파일에서 사용자 설정을 내보내고 가져올 수 있습니다.  
  
 Vspackage는 일반적으로 시스템 레지스트리 또는 현재 사용자나 컴퓨터의 응용 프로그램 데이터 폴더에 있는 로컬 저장소를 사용 합니다. 정수 및 문자열과 같이 저장소에 적은 양의 공간이 필요한 값은 일반적으로 시스템 레지스트리에 저장 됩니다. 비트맵과 같이 저장소에 필요한 공간이 많은 값은 파일에 저장 됩니다. 파일의 경로 자체를 시스템 레지스트리에 저장할 수 있습니다. 지 속성 메커니즘에는 로컬 저장소에 액세스할 수 있는 권한이 있어야 합니다.  
  
## <a name="support-for-locating-local-storage"></a>로컬 저장소 찾기 지원  
 <xref:Microsoft.VisualStudio.Shell.Package>클래스는 현재 사용자 또는 컴퓨터에 대 한 시스템 레지스트리 또는 응용 프로그램 데이터 폴더에 상태 정보를 찾기 위한 지원을 제공 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\8.0Exp.와 같은에 대 한 로컬 컴퓨터의 레지스트리 루트 경로를 반환 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
 로컬 레지스트리 루트는 서비스에서 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> . 사용할 수 없는 경우 <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> VSPackage의 특성에서 가져옵니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp.와 같은에 대 한 현재 사용자의 (컴퓨터당) 레지스트리 루트의 경로를 반환 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
 로컬 레지스트리 루트는 서비스에서 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> . 사용할 수 없는 경우 VSPackage의 DefaultLocalRegistryRoot 특성에서 가져옵니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 현재 로밍 사용자의 데이터에 대 한 공용 리포지토리로 사용 되는 디렉터리의 경로를 반환 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (예: C:\Documents 및 Settings \\ *YourAccountName*\Application Data\Microsoft\VisualStudio\8.0Exp.).  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 현재 로밍되지 않는 사용자의 데이터에 대 한 공용 리포지토리로 사용 되는 디렉터리의 경로를 반환 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (예: C:\Documents 및 Settings \\ *YourAccountName*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp.).  
  
## <a name="see-also"></a>관련 항목  
 [VSPackage 상태](../misc/vspackage-state.md)