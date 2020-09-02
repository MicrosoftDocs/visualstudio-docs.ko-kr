---
title: 기본 프로젝트의 개체 모델 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187159"
---
# <a name="extending-the-object-model-of-the-base-project"></a>기본 프로젝트의 개체 모델 확장
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 하위 형식이 다음 위치에서 기본 프로젝트의 자동화 개체 모델을 확장할 수 있습니다.  
  
- Project. Extender (" \<ProjectSubtypeName> ") – 프로젝트 하위 형식에서의 사용자 지정 메서드를 사용 하 여 개체를 제공할 수 있습니다 <xref:EnvDTE.Project> . 프로젝트 하위 유형은 Automation Extender를 사용 하 여 개체를 노출할 수 있습니다 `Project` . <xref:EnvDTE80.IInternalExtenderProvider>주 프로젝트 하위 형식 집계에 구현 된 인터페이스는 `VSHPROPID_ExtObjectCATID` from <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> ( `itemid` 값 VSITEMID_ROOT, from) CATID에 해당 하는의 개체를 제공 해야 합니다 `VSITEMID` .  
  
- ProjectItem. Extender (" \<ProjectSubtypeName> ") – 프로젝트 하위 형식에서 프로젝트 내의 특정 개체에 대 한 사용자 지정 메서드를 사용 하 여 개체를 제공할 수 있습니다 <xref:EnvDTE.ProjectItem> . 프로젝트 하위 유형은 Automation Extender를 사용 하 여이 개체를 노출할 수 있습니다. <xref:EnvDTE80.IInternalExtenderProvider>주 프로젝트 하위 형식 집계에 구현 된 인터페이스는 `VSHPROPID_ExtObjectCATID` from <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (desired) CATID에 대 한 개체를 제공 해야 합니다 `VSITEMID` .  
  
- Project. 속성 –이 컬렉션은 개체의 구성 독립적 속성을 노출 합니다 `Project` . 프로젝트 속성에 대 한 자세한 내용은을 참조 하십시오 <xref:EnvDTE.Project.Properties%2A> . 프로젝트 하위 유형은 Automation Extender를 사용 하 여 해당 속성을이 컬렉션에 추가할 수 있습니다. <xref:EnvDTE80.IInternalExtenderProvider>주 프로젝트 하위 형식 집계에서 구현 되는 인터페이스는 `VSHPROPID_BrowseObjectCATID` VSHPROPID2의 값에 해당 하는 ( `itemid` 에서 VSITEMID_ROOT, from) CATID의 개체를 제공 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> .  
  
- 구성 속성 –이 컬렉션은 특정 구성에 대 한 프로젝트의 구성 종속 속성 (예: 디버그)을 노출 합니다. 자세한 내용은 <xref:EnvDTE.Configuration>를 참조하세요. 프로젝트 하위 유형은 Automation Extender를 사용 하 여 해당 속성을이 컬렉션에 추가할 수 있습니다. <xref:EnvDTE80.IInternalExtenderProvider>주 프로젝트 하위 형식 집계에 구현 된 인터페이스는 CATID `VSHPROPID_CfgBrowseObjectCATID` (의 값에 해당)에 대 한 개체를 제공 합니다 `itemid` <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>인터페이스를 사용 하 여 하나의 구성 찾아보기 개체를 서로 구별할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
