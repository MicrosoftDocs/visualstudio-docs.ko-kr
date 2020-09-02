---
title: 프로젝트 항목 업그레이드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698694"
---
# <a name="upgrading-project-items"></a>프로젝트 항목 업그레이드
구현 하지 않는 프로젝트 시스템 내에서 항목을 추가 하거나 관리 하는 경우 프로젝트 업그레이드 프로세스에 참여 해야 할 수 있습니다. Crystal Reports는 프로젝트 시스템에 추가할 수 있는 항목의 예입니다.  
  
 일반적으로 프로젝트 항목 구현자는 프로젝트 참조가 무엇 인지 알고 있어야 하 고 업그레이드 결정을 내리는 기타 프로젝트 속성을 알아야 하므로 이미 완전히 인스턴스화되어 업그레이드 된 프로젝트를 활용 하려고 합니다.  
  
### <a name="to-get-the-project-upgrade-notification"></a>프로젝트 업그레이드 알림을 가져오려면  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>프로젝트 항목 구현에서 플래그 (vsshell80에 정의 됨)를 설정 합니다. 이로 인해 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 셸에서 프로젝트 시스템을 업그레이드 하는 중 이라고 결정 하는 경우 프로젝트 항목 VSPackage 자동으로 로드 됩니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>메서드를 통해 인터페이스에 대해 Advise 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> .  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>인터페이스는 프로젝트 시스템 구현에서 업그레이드 작업을 완료 하 고 업그레이드 된 새 프로젝트가 생성 된 후에 발생 합니다. 시나리오에 따라 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> , 또는 메서드 후에 인터페이스가 발생 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> .  
  
### <a name="to-upgrade-the-project-item-files"></a>프로젝트 항목 파일을 업그레이드 하려면  
  
1. 프로젝트 항목 구현에서 파일 백업 프로세스를 신중 하 게 관리 해야 합니다. 이는 side-by-side 백업에 특히 적용 됩니다 .이 경우 `fUpgradeFlag` 메서드의 매개 변수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 로 설정 되 고 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> , 백업 된 파일은 ".old"로 지정 된 side-by-side 파일에 배치 됩니다. 프로젝트를 업그레이드할 때 시스템 시간 보다 오래 된 백업 파일은 오래 된 것으로 지정할 수 있습니다. 또한이를 방지 하기 위해 특정 단계를 수행 하지 않는 한 덮어쓸 수 있습니다.  
  
2. 프로젝트 항목에 프로젝트 업그레이드 알림이 표시 될 때 **Visual Studio 변환 마법사** 가 계속 표시 됩니다. 따라서 인터페이스의 메서드를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> 하 여 마법사 UI에 업그레이드 메시지를 제공 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 변환 마법사](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [사용자 지정 프로젝트 업그레이드](../misc/upgrading-custom-projects.md)