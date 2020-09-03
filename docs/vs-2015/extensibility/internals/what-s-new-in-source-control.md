---
title: 소스 제어의 새로운 기능
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200946"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Visual Studio 2015에서 소스 제어의 새로운 기능&#39;

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

에서 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 소스 제어 VSPackage을 구현 하 여 긴밀 하 게 통합 된 소스 제어 솔루션을 제공할 수 있습니다. 이 섹션에서는 소스 제어 Vspackage의 기능에 대해 설명 하 고 구현 단계에 대 한 개요를 제공 합니다.  
  
## <a name="the-source-control-vspackage"></a>소스 제어 VSPackage  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 에서는 두 가지 형식의 원본 제어 솔루션을 지원 합니다. 모든 버전의에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 원본 제어 플러그 인 API 기반 플러그 인을 계속 통합할 수 있습니다. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]높은 수준의 복잡성과 자율성이 필요한 소스 제어 솔루션에 적합 한 심층 통합 경로를 제공 하는 소스 제어에 대 한 VSPackage 만들 수도 있습니다.  
  
 VSPackage는 거의 모든 종류의 기능을에 추가할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 소스 제어 VSPackage는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 사용자에 게 제공 되는 UI에서 원본 제어 시스템을 사용 하 여 백 엔드 통신으로의 전체 소스 제어 기능을 제공 합니다.  
  
 소스 제어 VSPackage를 구현 하려면 "모두 또는 없음" 전략이 필요 합니다. 소스 제어 VSPackage의 작성자는 전체 소스 제어 기능을 포함 하 고, 패키지에 성공적으로 통합 하는 데 필요한 인터페이스를 포함 하 여 다양 한 소스 제어 인터페이스 및 새 UI 요소 (대화 상자, 메뉴, 도구 모음)를 구현 하는 데 상당한 노력을 투자 해야 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 다음 단계에서는 소스 제어 패키지를 구현 하는 데 필요한 사항에 대 한 일반적인 개요를 제공 합니다. 자세한 내용은 [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)를 참조 하세요.  
  
1. 개인 소스 제어 서비스를 지 원하는 VSPackage를 만듭니다.  
  
2. 및 인터페이스와 같이 제공 되 된 소스 제어 관련 서비스에서 인터페이스를 구현 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> 합니다.  
  
3. 소스 제어 VSPackage를 등록 합니다.  
  
4. 메뉴 항목, 대화 상자, 도구 모음 및 상황에 맞는 메뉴를 비롯 한 모든 소스 제어 UI를 구현 합니다.  
  
5. 모든 소스 제어 관련 이벤트는 활성 상태이 고 VSPackage에서 처리 해야 하는 경우 소스 제어 VSackage 전달 됩니다.  
  
6. 소스 제어 VSPackage는 인터페이스를 구현 하는 것과 같은 이벤트를 수신 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> 고, 인터페이스에 의해 구현 된 대로 TPD (Project Document) 이벤트를 추적 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 하 고 필요한 작업을 수행 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [설명은](../../extensibility/internals/source-control-integration-overview.md)   
 [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)
