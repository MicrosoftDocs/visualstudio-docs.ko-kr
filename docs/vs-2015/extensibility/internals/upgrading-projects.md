---
title: 프로젝트 업그레이드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841463"
---
# <a name="upgrading-projects"></a>프로젝트 업그레이드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 모델을의 특정 버전에서 다음 버전 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 으로 변경 하면 최신 버전에서 실행 될 수 있도록 프로젝트와 솔루션을 업그레이드 해야 할 수 있습니다. 는 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 자체 프로젝트에서 업그레이드 지원을 구현 하는 데 사용할 수 있는 인터페이스를 제공 합니다.  
  
## <a name="upgrade-strategies"></a>업그레이드 전략  
 업그레이드를 지원 하려면 프로젝트 시스템 구현에서 업그레이드 전략을 정의 하 고 구현 해야 합니다. 전략 결정에서 SxS (side-by-side) 백업, 복사 백업 또는 둘 다를 지원 하도록 선택할 수 있습니다.  
  
- SxS 백업은 프로젝트에서 업그레이드가 필요한 파일만 복사 하 여 적절 한 파일 이름 접미사를 추가 하는 것을 의미 합니다 (예: ".old").  
  
- 백업 복사는 프로젝트가 모든 프로젝트 항목을 사용자가 제공한 백업 위치에 복사 하는 것을 의미 합니다. 그런 다음 원본 프로젝트 위치에 있는 관련 파일이 업그레이드 됩니다.  
  
## <a name="how-upgrade-works"></a>업그레이드 작동 방법  
 이전 버전의에서 만든 솔루션이 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 최신 버전에서 열리면 IDE는 솔루션 파일을 확인 하 여 업그레이드 해야 하는지 여부를 확인 합니다. 업그레이드 해야 하는 경우 업그레이드 **마법사** 가 자동으로 시작 되어 업그레이드 프로세스를 통해 사용자를 안내 합니다.  
  
 솔루션을 업그레이드 해야 하는 경우 각 프로젝트 팩터리에서 업그레이드 전략을 쿼리 합니다. 전략은 프로젝트 팩터리가 복사 백업 또는 SxS 백업을 지원 하는지 여부를 결정 합니다. 이 정보는 백업에 필요한 정보를 수집 하 고 해당 옵션을 사용자에 게 제공 하는 **업그레이드 마법사**에 전송 됩니다.  
  
### <a name="multi-project-solutions"></a>다중 프로젝트 솔루션  
 솔루션에 여러 프로젝트가 포함 되어 있고 업그레이드 전략이 다른 경우 (예: SxS 백업만 지 원하는 c + + 프로젝트와 복사 백업만 지 원하는 웹 프로젝트의 경우) 프로젝트 팩터리가 업그레이드 전략을 협상 해야 합니다.  
  
 솔루션은에 대 한 각 프로젝트 팩터리를 쿼리 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 합니다. 그런 다음 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> 를 호출 하 여 전역 프로젝트 파일을 업그레이드 해야 하는지 여부를 확인 하 고 지원 되는 업그레이드 전략을 결정 합니다. 그러면 **업그레이드 마법사** 가 호출 됩니다.  
  
 사용자가 마법사를 완료 한 후에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 는 각 프로젝트 팩터리에서를 호출 하 여 실제 업그레이드를 수행 합니다. 백업을 용이 하 게 하기 위해 IVsProjectUpgradeViaFactory 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 업그레이드 프로세스의 세부 정보를 기록 하는 서비스를 제공 합니다. 이 서비스는 캐시할 수 없습니다.  
  
 모든 관련 전역 파일을 업데이트 한 후에는 각 프로젝트 팩터리가 프로젝트를 인스턴스화하기 위해 선택할 수 있습니다. 프로젝트 구현은를 지원 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>그런 다음 메서드를 호출 하 여 모든 관련 프로젝트 항목을 업그레이드 합니다.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>이 메서드는 SVsUpgradeLogger 서비스를 제공 하지 않습니다. 을 호출 하 여이 서비스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>모범 사례  
 서비스를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 하 여 파일을 편집 하기 전에 편집할 수 있는지 확인 하 고 저장 하기 전에 저장할 수 있습니다. 이렇게 하면 백업 및 업그레이드 구현이 소스 제어에서 프로젝트 파일, 권한이 부족 한 파일 등을 처리 하는 데 도움이 됩니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>백업 및 업그레이드의 모든 단계에서 서비스를 사용 하 여 업그레이드 프로세스의 성공 또는 실패에 대 한 정보를 제공 합니다.  
  
 프로젝트를 백업 하 고 업그레이드 하는 방법에 대 한 자세한 내용은 vsshell2의 IVsProjectUpgrade에 대 한 설명을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트](../../extensibility/internals/projects.md)   
 [사용자 지정 프로젝트 업그레이드](../../misc/upgrading-custom-projects.md)   
 [프로젝트 항목 업그레이드](../../misc/upgrading-project-items.md)
