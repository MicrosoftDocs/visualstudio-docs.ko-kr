---
title: VS패키지자동화 제공 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705957"
---
# <a name="providing-automation-for-vspackages"></a>VSPackage에 대한 자동화 제공
VSPackage 관련 개체를 구현하고 표준 자동화 개체를 구현하여 VSPackage에 자동화를 제공하는 방법에는 두 가지가 있습니다. 일반적으로 이러한 환경의 자동화 모델을 확장 하기 위해 함께 사용 됩니다.

## <a name="vspackage-specific-objects"></a>VS패키지 관련 개체
 자동화 모델 내의 특정 위치에서는 VSPackage에 고유한 자동화 개체를 제공해야 합니다. 예를 들어 새 프로젝트에는 VSPackage에서만 제공하는 고유한 개체가 필요합니다. 이러한 개체의 이름은 레지스트리에 입력되고 환경 `DTE` 개체에 대한 호출을 통해 가져옵니다.

 VSPackage 관련 개체는 자동화 소비자가 표준 개체의 Object 속성을 통해 제공된 개체를 사용할 때도 가져올 수 있습니다. 예를 들어 표준 `Window` 개체에는 `Object` 일반적으로 속성으로 `Windows.Object` 알려진 속성이 있습니다. 소비자가 `Window.Object` VSPackage에서 구현된 창을 호출하면 사용자 고유의 디자인의 특정 자동화 개체를 다시 전달합니다.

#### <a name="projects"></a>프로젝트
 VSPackage는 자체 VSPackage 관련 개체를 통해 새 프로젝트 유형에 대한 자동화 모델을 확장할 수 있습니다. VSPackage에 새 자동화 개체를 제공하는 주요 목적은 고유한 프로젝트 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> 개체를 또는 <xref:VSLangProj80.VSProject2> 개체와 구분하는 것입니다. 이 차별화는 솔루션에 나란히 나타나는 경우 다른 프로젝트 유형과 는 별도로 프로젝트 유형을 선택하거나 반복하는 방법을 제공하려는 경우에 유용합니다. 자세한 내용은 [프로젝트 개체 노출을](../../extensibility/internals/exposing-project-objects.md)참조하십시오.

#### <a name="events"></a>이벤트
 환경의 이벤트 아키텍처는 사용자 고유의 VSPackage 관련 개체를 추가할 수 있는 또 다른 위치를 제공합니다. 예를 들어 고유한 이벤트 개체를 만들어 프로젝트에 대한 환경의 이벤트 모델을 확장할 수 있습니다. 새 항목이 사용자 고유의 프로젝트 유형에 추가될 때 고유한 이벤트를 제공할 수 있습니다. 자세한 내용은 [이벤트 노출](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)을 참조하십시오.

#### <a name="window-objects"></a>창 개체
 Windows는 호출될 때 VSPackage 관련 자동화 개체를 환경으로 다시 전달할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>에서 <xref:EnvDTE.IExtensibleObject> 파생되거나 `IDispatch` 해당 속성에서 파생된 개체를 구현하여 해당 개체가 사이트된 창 개체를 확장합니다. 예를 들어 이 방법을 사용하여 창 프레임에 있는 컨트롤에 대한 자동화를 제공할 수 있습니다. 이 개체와 확장할 수 있는 다른 개체의 의미 체계는 디자인할 대상입니다. 자세한 내용은 Windows 에 [대한 자동화 제공 방법을](../../extensibility/internals/how-to-provide-automation-for-windows.md)참조하십시오.

#### <a name="options-pages-on-the-tools-menu"></a>도구 메뉴의 옵션 페이지
 페이지를 구현하고 레지스트리에 정보를 추가하여 도구, 옵션 자동화 모델을 확장하는 페이지를 만들어 고유한 옵션을 만들 수 있습니다. 그런 다음 다른 옵션 페이지와 마찬가지로 환경 개체 모델을 통해 페이지를 호출할 수 있습니다. VSPackage를 통해 환경에 추가하는 기능의 디자인에 옵션 페이지가 필요한 경우 자동화 지원도 추가해야 합니다. 자세한 내용은 [옵션 페이지에 대한 자동화 지원을](../../extensibility/internals/automation-support-for-options-pages.md)참조하십시오.

## <a name="standard-automation-objects"></a>표준 자동화 개체
 프로젝트의 자동화를 확장하려면 다른 프로젝트 개체 옆에 서 `IDispatch`있고 표준 메서드 및 속성을 구현하는 표준 자동화 개체(파생)도 구현합니다. Examples of standard objects include the project objects that are inserted into the solution hierarchy such as `Projects`, `Project`, `ProjectItem`, and `ProjectItems`. 모든 새 프로젝트 유형은 이러한 개체(및 프로젝트의 의미 체계에 따라 다른 개체)를 구현해야 합니다.

 어떤 의미에서 이러한 개체는 VSPackage 관련 프로젝트 개체의 반대 이점을 제공합니다. 표준 자동화 개체를 사용하면 동일한 개체를 지원하는 다른 프로젝트와 마찬가지로 일반화된 방식으로 프로젝트를 사용할 수 있습니다. 따라서 일반 `Project` 및 `ProjectItem` 개체에 대해 작성 된 추가 기능은 모든 형식의 프로젝트에 대해 작동할 수 있습니다. 자세한 내용은 [프로젝트 모델링](../../extensibility/internals/project-modeling.md)을 참조하십시오.
