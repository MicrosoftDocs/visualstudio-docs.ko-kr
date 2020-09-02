---
title: 프로젝트 형식 Essentials | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e45d5f252deaf1788ae5093048ef8afb900fbe4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704068"
---
# <a name="project-type-essentials"></a>프로젝트 형식 필수 항목
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 에는 또는과 같은 언어에 대 한 여러 가지 프로젝트 형식이 포함 되어 있습니다 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 사용자 고유의 프로젝트 형식을 만들 수도 있습니다.  
  
 사용자 지정 명령, 편집기 또는 도구 창을에 추가 하려는 경우에는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 새 프로젝트 형식을 만들지 않고도이 작업을 수행할 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.  
  
- [명령, 메뉴 및 도구 모음](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)  
  
- [도구 창 확장 및 사용자 지정](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  마찬가지로 제공 된 및 프로젝트 형식의 동작을 사용자 지정 하려는 경우 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 프로젝트 하위 형식을 사용 하면 됩니다. 자세한 내용은 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)을 참조 하세요.  
  
  이외의 언어를 기반으로 하는 프로젝트의 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 경우 다음 중 하나 이상을 지원 하려는 경우에는 새 프로젝트 형식을 만들어야 합니다.  
  
- 빌드  
  
- 배포  
  
- 여러 구성  
  
- 원본 제어  
  
- 디버깅  
  
- 솔루션 탐색기의 프로젝트 항목  
  
- **프로젝트 열기** 또는 **새 프로젝트** 대화 상자  
  
- 프로젝트 중첩  
  
- 프로젝트 형식의 기능에 대 한 자세한 내용은 다음을 참조 하세요.  
  
- 프로젝트 형식은 필요한 인터페이스 집합을 구현 하는 VSPackage의 개체 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 입니다. C #을 사용 하 여 프로젝트 형식을 개발 하는 경우 관리 되는 패키지 프레임 워크 프로젝트 클래스는 필요한 인터페이스를 구현 하 고 해당 구현을 상속할 수 있도록 합니다. 자세한 내용은 [관리 되는 패키지 프레임 워크를 사용 하 여 프로젝트 형식 구현 (c #)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)을 참조 하세요.  
  
- C + + 개발자의 경우 HierUtil 라이브러리의 클래스는 비슷한 방식으로 작동 합니다. 자세한 내용은 [빌드에 없음: HierUtil7 프로젝트 클래스를 사용 하 여 프로젝트 형식 구현 (c + +)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)을 참조 하세요.  
  
- 프로젝트 형식은 .exe 또는 .dll 어셈블리에 빌드하는 일반적인 소스 코드 파일 이외의 데이터를 지원할 수 있습니다. 예를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 들어 데이터베이스 프로젝트는 디스크에 저장 된 스크립트 및 쿼리 파일에 대 한 참조를 포함 하 고 데이터베이스에 대 한 스크립트 및 쿼리를 실행 하기 위해 **솔루션 탐색기** 에 명령을 추가 하지만 빌드 동작은 지원 하지 않습니다. 자세한 내용은 [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)을 참조 하세요.  
  
- 프로젝트 형식에서는 파일을 전혀 사용할 필요가 없습니다. 예를 들어, 프로젝트 형식에서 모든 데이터를 데이터베이스에 저장할 수 있습니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 형식에서 프로젝트 및 프로젝트 항목의 데이터를 유지 하는 방법을 완벽 하 게 제어할 수 있습니다. 자세한 내용은 [프로젝트 형식 디자인 결정](../../extensibility/internals/project-type-design-decisions.md)을 참조 하세요.  
  
- 프로젝트 형식은 프로젝트 *팩터리*를 제공 해야 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .이 개체는가 해당 프로젝트 형식을 기반으로 하는 프로젝트를 열거나 만들도록 지시 될 때마다 프로젝트 형식의 인스턴스를 만드는 개체입니다. 자세한 내용은 [프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)를 참조 하세요.  
  
- 프로젝트 형식은 프로젝트 및 프로젝트 항목에 대 한 템플릿을 제공 해야 합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 사용자가 새 프로젝트를 만들고 기존 프로젝트에 새 항목을 추가할 때 템플릿을 사용 합니다. 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)를 참조 하세요.  
  
- 프로젝트 형식은 디버그 및 릴리스와 같은 여러 구성을 지원할 수 있습니다. 사용자는 사용자가 제공 하는 속성 페이지를 사용 하 여 프로젝트의 다양 한 구성을 변경할 수 있습니다. 자세한 내용은 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 형식 배포](../../extensibility/internals/deploying-project-types.md)
