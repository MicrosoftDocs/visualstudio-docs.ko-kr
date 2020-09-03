---
title: 기본 프로젝트의 개체 모델 확장 | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708390"
---
# <a name="extend-the-object-model-of-the-base-project"></a>기본 프로젝트의 개체 모델 확장

프로젝트 하위 형식이 다음 위치에서 기본 프로젝트의 자동화 개체 모델을 확장할 수 있습니다.

- Project. Extender (" \<ProjectSubtypeName> "): 프로젝트 하위 형식에서 개체의 사용자 지정 메서드를 사용 하 여 개체를 제공할 수 있도록 <xref:EnvDTE.Project> 합니다. 프로젝트 하위 유형은 Automation Extender를 사용 하 여 개체를 노출할 수 있습니다 `Project` . <xref:EnvDTE80.IInternalExtenderProvider>주 프로젝트 하위 형식 집계에 구현 된 인터페이스는 `VSHPROPID_ExtObjectCATID` From <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> ( `itemid` VSITEMID의 값에 해당)에 대 한 개체를 제공 해야 합니다 [. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem. Extender (" \<ProjectSubtypeName> "): 프로젝트 하위 형식에서 프로젝트 내의 특정 개체에 대 한 사용자 지정 메서드를 사용 하 여 개체를 제공할 수 있습니다 <xref:EnvDTE.ProjectItem> . 프로젝트 하위 유형은 automation extender를 사용 하 여이 개체를 노출할 수 있습니다. <xref:EnvDTE80.IInternalExtenderProvider>주 프로젝트 하위 형식 집계에 구현 된 인터페이스는 `VSHPROPID_ExtObjectCATID` from <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (desired) CATID에 대 한 개체를 제공 해야 합니다 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> .

- Project. Properties:이 컬렉션은 개체의 구성 독립적 속성을 노출 합니다 `Project` . `Project` 속성에 대한 자세한 내용은 <xref:EnvDTE.Project.Properties%2A>를 참조하세요. 프로젝트 하위 유형은 Automation Extender를 사용 하 여 해당 속성을이 컬렉션에 추가할 수 있습니다. <xref:EnvDTE80.IInternalExtenderProvider>주 프로젝트 하위 형식 집계에 구현 된 인터페이스는 `VSHPROPID_BrowseObjectCATID` From <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ( `itemid` VSITEMID의 값에 해당)에 대해 개체를 제공 해야 합니다 [. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- 구성 속성:이 컬렉션은 특정 구성에 대 한 프로젝트의 구성 종속 속성 (예: 디버그)을 노출 합니다. 자세한 내용은 <xref:EnvDTE.Configuration>를 참조하세요. 프로젝트 하위 유형은 Automation Extender를 사용 하 여 해당 속성을이 컬렉션에 추가할 수 있습니다. <xref:EnvDTE80.IInternalExtenderProvider>주 프로젝트 하위 형식 집계에 구현 된 인터페이스는 CATID `VSHPROPID_CfgBrowseObjectCATID` ( `itemid` VSITEMID의 값에 해당)에 대 한 개체를 제공 합니다 [. 루트](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>인터페이스를 사용 하 여 하나의 구성 찾아보기 개체를 서로 구별할 수 있습니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
