---
title: 프로젝트 속성 사용자 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31840c40f2a494ffd32f5241e2770938138877e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704093"
---
# <a name="project-property-user-interface"></a>프로젝트 속성 사용자 인터페이스
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 하위 유형은 기본 프로젝트에서 제공 하는 프로젝트 **속성 페이지** 대화 상자의 항목을 사용 하거나, 제공 된 대로 읽기 전용 컨트롤과 전체 페이지를 숨기 거 나 만들거나, **속성 페이지** 대화 상자에 프로젝트 하위 형식 관련 페이지를 추가할 수 있습니다.  
  
## <a name="extending-the-project-property-dialog-box"></a>프로젝트 속성 대화 상자 확장  
 프로젝트 하위 유형은 automation extender 및 프로젝트 구성 찾아보기 개체를 구현 합니다. 이러한 extender는 <xref:EnvDTE.IFilterProperties> 특정 속성을 숨기 거 나 읽기 전용으로 설정 하기 위해 인터페이스를 구현 합니다. 기본 프로젝트에 의해 구현 되는 기본 프로젝트의 **속성 페이지** 대화 상자는 Automation extender에서 수행 하는 필터링을 적용 합니다.  
  
 **프로젝트 속성** 대화 상자를 확장 하는 프로세스는 아래에 설명 되어 있습니다.  
  
- 기본 프로젝트는 인터페이스를 구현 하 여 프로젝트 하위 형식에서 extender를 검색 합니다 <xref:EnvDTE80.IInternalExtenderProvider> . 기본 프로젝트의 browse, project automation 및 project configuration browse 개체는 모두이 인터페이스를 구현 합니다.  
  
- Project <xref:EnvDTE80.IInternalExtenderProvider> browse 개체 및 프로젝트 자동화 개체에 대 한의 구현은 프로젝트 <xref:EnvDTE80.IInternalExtenderProvider> 하위 형식 집계 (즉, `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> project 개체에 대 한)의 구현에 위임 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .  
  
- 또한 기본 프로젝트 구성 찾아보기 개체는 <xref:EnvDTE80.IInternalExtenderProvider> 를 구현 하 여 프로젝트 하위 형식 구성 개체에서 자동화 Extender에 직접 연결 합니다. 해당 구현은 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 하위 형식 집계에 의해 구현 되는 인터페이스에 위임 됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>프로젝트 구성 찾아보기 개체에 의해 구현 되 고 개체를 반환 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>프로젝트 구성 찾아보기 개체에서 구현 되는도 개체를 반환 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> .  
  
- 프로젝트 하위 형식에서 다음 값을 검색 하 여 런타임에 기본 프로젝트의 다양 한 확장 가능한 개체에 대 한 적절 한 Catid를 결정할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> .  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  프로젝트 범위에 대 한 Catid를 확인 하기 위해 프로젝트 하위 유형은에서 위의 속성을 검색 합니다 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> `VSITEMID``typedef` . 프로젝트 하위 형식에서 프로젝트에 대해 표시 되는 **속성 페이지** 대화 상자 페이지 (구성 종속 및 구성 독립적)를 제어할 수도 있습니다. 일부 프로젝트 하위 형식에서는 기본 제공 페이지를 제거 하 고 프로젝트 하위 형식 특정 페이지를 추가 해야 할 수 있습니다. 이를 사용 하도록 설정 하기 위해 관리 되는 클라이언트 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 다음 속성에 대해 메서드를 호출 합니다.  
  
- `VSHPROPID_PropertyPagesCLSIDList` -구성 독립적 속성 페이지의 Clsid를 세미콜론으로 구분한 목록입니다.  
  
- `VSHPROPID_CfgPropertyPagesCLSIDList —` 구성 종속 속성 페이지의 Clsid를 세미콜론으로 구분한 목록입니다.  
  
  프로젝트 하위 유형은 개체를 집계 하므로 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 이러한 속성의 정의를 재정의 하 여 표시 되는 **속성 페이지** 대화 상자를 제어할 수 있습니다. 프로젝트 하위 유형은 내부 기본 프로젝트에서 이러한 속성을 검색 한 다음 필요에 따라 Clsid를 추가 하거나 제거할 수 있습니다.  
  
  프로젝트 하위 형식에 의해 추가 된 새 속성 페이지는 기본 프로젝트 구현에서 프로젝트 구성 찾아보기 개체로 전달 됩니다. 이 프로젝트 구성 찾아보기 개체는 Automation Extender를 지원 합니다. AutomationExtenders에 대 한 자세한 내용은 [Automation Extender 구현 및 사용](https://msdn.microsoft.com/library/0d5c218c-f412-4b28-ab0c-33a611f62356)을 참조 하세요. <xref:EnvDTE.Project.Extender%2A>기본 프로젝트의 구성 찾아보기 개체를 확장 하는 자체 프로젝트 하위 형식 구성 찾아보기 개체를 검색 하기 위해 프로젝트 하위 형식 호출에 의해 구현 되는 속성 페이지입니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:EnvDTE.IFilterProperties>   
 [속성 페이지 대화 상자](https://msdn.microsoft.com/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
