---
title: 기본 프로젝트의 객체 모델 확장 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708390"
---
# <a name="extend-the-object-model-of-the-base-project"></a>기본 프로젝트의 개체 모델 확장

프로젝트 하위 유형은 다음과 같은 위치에서 기본 프로젝트의 자동화 개체 모델을 확장할 수 있습니다.

- Project.Extender("ProjectSubtypeName\<>"): 프로젝트 하위 형식이 <xref:EnvDTE.Project> 개체의 사용자 지정 메서드를 사용하여 개체를 제공할 수 있습니다. 프로젝트 하위 유형은 자동화 익스텐더를 사용하여 개체를 `Project` 노출할 수 있습니다. 기본 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 하위 유형 애그리게이터에서 구현된 `VSHPROPID_ExtObjectCATID` 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> `itemid` 에서(VSITEMID 값에 해당하는)에 대한 개체를 제공해야 [합니다. 루트)](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)CATID.

- ProjectItem.Extender("ProjectSubtypeName\<>"): 프로젝트 하위 형식이 프로젝트 내의 특정 <xref:EnvDTE.ProjectItem> 개체의 사용자 지정 메서드를 사용하여 개체를 제공할 수 있습니다. 프로젝트 하위 유형은 자동화 익스텐더를 사용하여 이 개체를 노출할 수 있습니다. 주 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 하위 유형 애그리게이터에 구현된 인터페이스는 `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (원하는 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>에 대응하는) CATID에 대한 개체를 제공해야 합니다.

- Project.Properties: 이 컬렉션은 개체의 구성 `Project` 독립적인 속성을 노출합니다. `Project` 속성에 대한 자세한 내용은 <xref:EnvDTE.Project.Properties%2A>를 참조하세요. 프로젝트 하위 유형은 자동화 익스텐더를 사용하여 이 컬렉션에 해당 속성을 추가할 수 있습니다. 기본 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 하위 유형 애그리게이터에서 구현된 인터페이스는 `VSHPROPID_BrowseObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> `itemid` 에서(VSITEMID 값에 해당)에 대한 개체를 제공해야 [합니다. 루트)](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)CATID.

- Configuration.Properties: 이 컬렉션은 특정 구성(예: 디버그)에 대한 프로젝트의 구성 종속 속성을 노출합니다. 자세한 내용은 <xref:EnvDTE.Configuration>을 참조하세요. 프로젝트 하위 유형은 자동화 익스텐더를 사용하여 이 컬렉션에 해당 속성을 추가할 수 있습니다. 주 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 하위 유형 애그리게이터에서 구현된 인터페이스는 `VSHPROPID_CfgBrowseObjectCATID` CATID에 `itemid` 대한 개체를 제공합니다(VSITEMID 값에 [해당). 루트)를 참조하십시오.](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>) 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> 한 구성 찾아보기 개체를 다른 구성과 구별하는 데 사용됩니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
