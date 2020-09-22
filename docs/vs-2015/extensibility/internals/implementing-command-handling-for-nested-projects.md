---
title: 중첩 된 프로젝트에 대 한 명령 처리 구현 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2fbce80b2e8c337eddf0d34954a7fd70b895d891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841754"
---
# <a name="implementing-command-handling-for-nested-projects"></a>중첩된 프로젝트에 대한 명령 처리 구현
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE는를 통해 전달 되는 명령 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 및 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 중첩 된 프로젝트에 전달 하거나 부모 프로젝트가 명령을 필터링 하거나 재정의할 수 있습니다.  
  
> [!NOTE]
> 부모 프로젝트에서 일반적으로 처리 하는 명령만 필터링 할 수 있습니다. IDE에서 처리 되는 **빌드** 및 **배포** 와 같은 명령은 필터링 할 수 없습니다.  
  
 다음 단계에서는 명령 처리를 구현 하는 과정을 설명 합니다.  
  
## <a name="procedures"></a>프로시저  
  
#### <a name="to-implement-command-handling"></a>명령 처리를 구현 하려면  
  
1. 사용자가 중첩 된 프로젝트 또는 중첩 된 프로젝트의 노드를 선택 하는 경우:  
  
   1. IDE는 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> .  
  
      — 또는 —  
  
   2. 솔루션 탐색기에서 바로 가기 메뉴 명령과 같은 계층 창에서 명령이 시작 되 면 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 프로젝트의 부모에서 메서드를 호출 합니다.  
  
2. 부모 프로젝트는 및와 같이에 전달 되는 매개 변수를 검사 `QueryStatus` `pguidCmdGroup` 하 여 `prgCmds` 부모 프로젝트가 명령을 필터링 해야 하는지 여부를 확인할 수 있습니다. 명령을 필터링 하기 위해 부모 프로젝트가 구현 된 경우 다음을 설정 해야 합니다.  
  
   ```  
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
   // make sure it is disabled  
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
   ```  
  
    그런 다음 부모 프로젝트가를 반환 해야 합니다 `S_OK` .  
  
    부모 프로젝트가 명령을 필터링 하지 않는 경우만 반환 해야 `S_OK` 합니다. 이 경우 IDE는 자동으로 명령을 자식 프로젝트로 라우팅합니다.  
  
    부모 프로젝트는 명령을 자식 프로젝트로 라우팅할 필요가 없습니다. IDE에서이 작업을 수행 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [명령, 메뉴 및 도구 모음](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [프로젝트 중첩](../../extensibility/internals/nesting-projects.md)
