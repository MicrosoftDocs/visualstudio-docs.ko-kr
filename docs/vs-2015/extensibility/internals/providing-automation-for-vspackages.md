---
title: Vspackage에 대 한 자동화 제공 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6eb76eba76567f2966323d4058c9e752cb6fb69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200976"
---
# <a name="providing-automation-for-vspackages"></a>VSPackage에 대한 자동화 제공
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vspackage에 대 한 자동화를 제공 하는 두 가지 주요 방법은 VSPackage 관련 개체를 구현 하 고 표준 자동화 개체를 구현 하는 것입니다. 일반적으로 환경의 자동화 모델을 확장 하는 데 함께 사용 됩니다.  
  
## <a name="vspackage-specific-objects"></a>VSPackage 개체  
 자동화 모델 내의 특정 위치에서는 VSPackage에 고유한 자동화 개체를 제공 해야 합니다. 예를 들어 새 프로젝트에는 VSPackage에서 제공 하는 고유 개체가 필요 합니다. 이러한 개체의 이름은 레지스트리에 입력 되며 environment 개체에 대 한 호출을 통해 가져옵니다 `DTE` .  
  
 VSPackage 개체는 자동화 소비자가 표준 개체의 개체 속성을 통해 제공 된 개체를 사용 하는 경우에도 가져올 수 있습니다. 예를 들어 표준 개체에는 `Window` `Object` 일반적으로 속성으로 알려진 속성이 있습니다 `Windows.Object` . 소비자가 VSPackage에서 구현 된 창에서를 호출 하는 경우 `Window.Object` 고유한 디자인의 특정 자동화 개체를 다시 전달 합니다.  
  
#### <a name="projects"></a>프로젝트  
 Vspackage는 고유한 VSPackage 관련 개체를 통해 새 프로젝트 형식에 대 한 자동화 모델을 확장할 수 있습니다. VSPackage에 대 한 새 자동화 개체를 제공 하는 주요 목적은 또는 개체의 고유한 프로젝트 개체를 구분 하는 것입니다 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> <xref:VSLangProj80.VSProject2> . 이러한 차별화는 다른 프로젝트 형식과 분리 하 여 프로젝트 형식을 단일 확장 하거나 반복 하는 방법을 제공 하려는 경우에 유용 합니다. 솔루션에 나란히 표시 되어야 합니다. 자세한 내용은 [프로젝트 개체 노출](../../extensibility/internals/exposing-project-objects.md)을 참조 하세요.  
  
#### <a name="events"></a>이벤트  
 환경의 이벤트 아키텍처는 VSPackage 특정 개체를 추가할 수 있는 다른 장소를 제공 합니다. 예를 들어 고유한 이벤트 개체를 만들어 프로젝트에 대 한 환경의 이벤트 모델을 확장할 수 있습니다. 사용자 고유의 프로젝트 형식에 새 항목이 추가 될 때 사용자 고유의 이벤트를 제공할 수 있습니다. 자세한 내용은 [이벤트 노출](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)을 참조 하세요.  
  
#### <a name="window-objects"></a>창 개체  
 Windows에서는 호출 될 때 VSPackage automation 개체를 환경에 다시 전달할 수 있습니다. 에서 파생 되거나 속성을 전달 하는 개체를 구현 하 여 이동 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> `IDispatch` 창 개체를 확장 합니다. 예를 들어이 방법을 사용 하 여 창 프레임으로 배치 되는 컨트롤에 대 한 자동화를 제공할 수 있습니다. 이 개체의 의미 체계와이 개체를 확장할 수 있는 다른 개체의 의미 체계는 의도적으로 설계 되었습니다. 자세한 내용은 [방법: Windows에 대 한 자동화 제공](../../extensibility/internals/how-to-provide-automation-for-windows.md)을 참조 하세요.  
  
#### <a name="options-pages-on-the-tools-menu"></a>도구 메뉴의 옵션 페이지  
 페이지를 만들어 페이지를 구현 하 고 레지스트리에 정보를 추가 하는 방법으로 도구, 옵션 자동화 모델을 확장 하 여 사용자 고유의 옵션을 만들 수 있습니다. 그런 다음 다른 옵션 페이지와 같이 환경 개체 모델을 통해 페이지를 호출할 수 있습니다. Vspackage를 통해 환경에 추가 하는 기능을 디자인 하려면 옵션 페이지를 추가 해야 합니다. 자세한 내용은 [옵션 페이지에 대 한 자동화 지원](../../extensibility/internals/automation-support-for-options-pages.md)을 참조 하세요.  
  
## <a name="standard-automation-objects"></a>표준 자동화 개체  
 프로젝트에 대 한 자동화를 확장 하기 위해 다른 프로젝트 개체 옆에 있는 표준 자동화 개체 (에서 파생 됨)를 구현 하 `IDispatch` 고 표준 메서드 및 속성을 구현 합니다. 표준 개체의 예로는,,, 등의 솔루션 계층에 삽입 되는 project `Projects` 개체가 `Project` `ProjectItem` `ProjectItems` 있습니다. 모든 새 프로젝트 형식은 이러한 개체 (그리고 프로젝트의 의미 체계에 따라 다른 개체)를 구현 해야 합니다.  
  
 이러한 개체는 VSPackage 관련 프로젝트 개체의 반대 장점을 제공 합니다. 표준 자동화 개체를 사용 하면 동일한 개체를 지 원하는 다른 프로젝트와 마찬가지로 프로젝트를 일반적인 방식으로 사용할 수 있습니다. 따라서 일반 및 개체에 대해 작성 된 추가 기능은 `Project` `ProjectItem` 모든 형식의 프로젝트에 대해 작동할 수 있습니다. 자세한 내용은 [프로젝트 모델링](../../extensibility/internals/project-modeling.md)을 참조 하세요.
