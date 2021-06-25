---
title: 프로젝트 형식 Essentials | Microsoft Docs
description: 프로젝트 형식을 만들어야 하는 경우와 프로젝트 하위 형식을 사용하여 기존 프로젝트 형식을 확장할 수 있는 경우에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 051e7b76edd4559914307459fdcbdf1b7c0b600e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903560"
---
# <a name="project-type-essentials"></a>프로젝트 형식 필수 항목
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 에는 또는 와 같은 언어에 대한 여러 프로젝트 형식이 포함되어 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 에서는 사용자 고유의 프로젝트 형식을 만들 수도 있습니다.

 사용자 지정 명령, 편집기 또는 도구 창을 에 추가하려는 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 새 프로젝트 형식을 만들지 않고도 추가할 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.

- [명령, 메뉴 및 도구 모음](../../extensibility/internals/commands-menus-and-toolbars.md)

- [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)

- [도구 창 확장 및 사용자 지정](../../extensibility/extending-and-customizing-tool-windows.md)

  마찬가지로 제공된 및 프로젝트 형식의 동작을 사용자 지정하려는 경우 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트 하위 형식을 사용하여 수행할 수 있습니다. 자세한 내용은 [프로젝트 하위 형식을 참조하세요.](../../extensibility/internals/project-subtypes.md)

  다음 중 하나 이상을 지원하려는 경우 이외의 언어를 기반으로 하는 프로젝트에 대해 새 프로젝트 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 형식을 만들어야 합니다. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]

- 빌드

- 배포

- 여러 구성

- 원본 제어

- 디버깅

- 솔루션 탐색기 프로젝트 항목

- **프로젝트 열기** 또는 **새 프로젝트** 대화 상자

- 프로젝트 중첩

- 프로젝트 형식의 기능에 대한 자세한 내용은 다음을 참조하세요.

- 프로젝트 형식은 예상되는 인터페이스 집합을 구현하는 VSPackage의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체입니다. C#을 사용하여 프로젝트 형식을 개발하는 경우 Managed Package Framework 프로젝트 클래스는 필요한 인터페이스를 구현하고 해당 구현을 상속할 수 있습니다. 자세한 내용은 [관리되는 패키지 프레임워크를 사용하여 프로젝트 형식 구현(C#) 을](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)참조하세요.

- C++ 개발자의 경우 HierUtil 라이브러리의 클래스도 비슷한 방식으로 작동합니다. 자세한 내용은 [빌드에 없습니다. HierUtil7 프로젝트 클래스를 사용하여 프로젝트 형식 구현(C++) 을](/previous-versions/bb166212(v=vs.100))참조하세요.

- 프로젝트 형식은 .exe 또는 .dll 어셈블리에 빌드되는 일반적인 소스 코드 파일 이외의 데이터를 지원할 수 있습니다. 예를 들어 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 데이터베이스 프로젝트는 디스크에 저장된 스크립트 및 쿼리 파일에 대한 참조를 포함하고 **솔루션 탐색기** 명령을 추가하여 데이터베이스에 대해 스크립트 및 쿼리를 실행하지만 프로젝트는 빌드 동작을 지원하지 않습니다. 자세한 내용은 [프로젝트 항목 열기 및 저장을 참조하세요.](../../extensibility/internals/opening-and-saving-project-items.md)

- 프로젝트 형식은 파일을 전혀 사용할 필요가 없습니다. 예를 들어 프로젝트 형식은 모든 데이터를 데이터베이스에 저장할 수 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 은 프로젝트 형식이 프로젝트 및 프로젝트 항목에 대한 데이터를 유지하는 방법을 완전히 제어할 수 있도록 합니다. 자세한 내용은 [프로젝트 형식 디자인 결정 을 참조하세요.](../../extensibility/internals/project-type-design-decisions.md)

- 프로젝트 형식은 *프로젝트* 형식을 기반으로 하는 프로젝트를 열거나 만들라는 지시를 받으면 프로젝트 형식의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 인스턴스를 만드는 개체인 프로젝트 팩터리 를 제공해야 합니다. 자세한 내용은 프로젝트 팩터리 를 [사용하여 프로젝트 인스턴스 만들기를 참조하세요.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

- 프로젝트 형식은 프로젝트 및 프로젝트 항목에 대한 템플릿을 제공해야 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는 사용자가 새 프로젝트를 만들고 기존 프로젝트에 새 항목을 추가할 때 템플릿을 사용합니다. 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가를 참조하세요.](../../extensibility/internals/adding-project-and-project-item-templates.md)

- 프로젝트 형식은 디버그 및 릴리스와 같은 여러 구성을 지원할 수 있습니다. 사용자가 제공하는 속성 페이지를 사용하여 프로젝트의 다양한 구성을 변경할 수 있습니다. 자세한 내용은 [구성 옵션 관리를 참조하세요.](../../extensibility/internals/managing-configuration-options.md)

## <a name="see-also"></a>참조
- [프로젝트 형식 배포](../../extensibility/internals/deploying-project-types.md)