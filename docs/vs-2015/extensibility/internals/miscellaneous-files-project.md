---
title: 기타 파일 프로젝트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c128475ad9f5cb71b98325bbece4e524507a08b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179790"
---
# <a name="miscellaneous-files-project"></a>기타 파일 프로젝트
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자가 프로젝트 항목을 열면 IDE는 솔루션에서 프로젝트의 멤버가 아닌 모든 항목을 기타 파일 프로젝트에 할당 합니다.  
  
 프로젝트는 사용자가 프로젝트 항목을 열 때 사용 되는 편집기를 결정 하는 데 중요 한 역할을 합니다. 프로젝트 관련 편집기 또는 표준 편집기를 사용 하 여 특정 파일을 열도록 프로젝트를 디자인할 수 있습니다.  
  
 프로젝트별 편집기를 사용 하려면 일반적으로 사용자에 게 특별 한 지식이 있거나 프로젝트의 특수 한 인터페이스를 사용 해야 합니다. 자세한 내용은 [방법: 프로젝트 관련 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)를 참조 하세요.  
  
 표준 편집기는 모든 프로젝트에서 특정 확장명의 모든 파일을 열 수 있습니다. 사용자는 프로젝트에 대해 텍스트 편집기와 같은 일부 표준 편집기를 사용자 지정할 수 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 있지만 해당 공개 문자는 계속 유지 합니다. 표준 편집기는 메서드를 사용 하 여 만듭니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
 솔루션의 프로젝트에서 프로젝트 항목을 열 수 있다는 응답이 없으면 IDE는 파일을 여는 기타 파일 프로젝트 라는 특수 한 프로젝트를 제공 합니다.  
  
 이 특수 프로젝트는 프로젝트의 컨텍스트 외부에서 파일을 여는 기능을 제공 합니다. 메서드를 처리 하는 동안 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 기타 파일 프로젝트는 항상 매우 낮은 우선 순위를 사용 하 여 응답 합니다. 따라서 기타 파일 프로젝트는 항상 파일을 열 수 있는 우선 순위가 높은 프로젝트를 생성 합니다.  
  
 기타 파일 프로젝트에서는 사용자가 **새 프로젝트** 대화 상자를 사용 하 여 명시적으로 만들 필요가 없습니다. 또한 기타 파일 프로젝트는 프로젝트 멤버 목록을 영구적으로 관리 하지 않습니다. 선택적 기능을 사용 하 여 각 사용자에 대해 가장 최근에 사용한 파일 목록을 기록 합니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [방법: 프로젝트 관련 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)   
 [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)   
 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
