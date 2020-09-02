---
title: 서비스 사용 및 제공 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f58e29797e9a7760aa0f48c68868199f51b3c92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177435"
---
# <a name="using-and-providing-services"></a>서비스 사용 및 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

서비스는 두 Vspackage 사이의 계약입니다. 하나의 VSPackage는 다른 VSPackage에서 사용할 특정 인터페이스 집합을 제공 합니다. 예를 들어는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 로드 되는 모든 VSPackage에 서비스를 제공 합니다. 이 서비스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 활동 로그에 쓰는 데 사용할 수 있는 인터페이스를 제공 합니다. 자세한 내용은 [방법: 활동 로그 사용](../extensibility/how-to-use-the-activity-log.md)을 참조 하세요.  
  
 Vspackage는 인터페이스를 사용 하 여 자체 서비스를 제공할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>  
  
 Visual Studio는 다음과 같은 중요 한 서비스를 제공 합니다.  
  
|IDE 서비스|설명|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|기본 기능, Vspackage 및 레지스트리를 처리 하는 IDE 서비스에 대 한 액세스를 제공 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|도구와 문서 창을 만들 수 있는 기능과 같은 IDE에서 기본 창 및 UI 관련 기능을 제공 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|프로젝트를 열거 하 고, 새 프로젝트를 만들고, 프로젝트 변경 내용을 모니터링 하는 기능과 같은 기본적인 솔루션 관련 기능을 제공 합니다.|  
  
## <a name="in-this-section"></a>섹션 내용  
 [서비스 필수 항목](../extensibility/internals/service-essentials.md)  
 Visual Studio 서비스의 중요 한 요소를 표시 합니다.  
  
 [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md)  
 서비스를 요청 (사용) 하는 방법에 대해 설명 합니다.  
  
 [방법: 서비스 제공](../extensibility/how-to-provide-a-service.md)  
 서비스를 제공 하는 방법을 설명 합니다.  
  
 [방법: 비동기 Visual Studio 서비스 제공](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 비동기 서비스를 제공 하는 방법을 설명 합니다.  
  
 [방법: 서비스 문제 해결](../extensibility/how-to-troubleshoot-services.md)  
 일반적인 문제에 대해 설명 하 고 해결 방법을 제공 합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
