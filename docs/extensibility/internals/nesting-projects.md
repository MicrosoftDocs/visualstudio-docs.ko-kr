---
title: 네스팅 프로젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707025"
---
# <a name="nesting-projects"></a>프로젝트 중첩
VS 패키지를 사용하는 엔터프라이즈 응용 프로그램 개발자는 프로젝트 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *중첩을*사용하여 유사한 유형의 프로젝트를 편리하게 그룹화할 수 있습니다. 예를 들어 엔터프라이즈 템플릿 프로젝트는 중첩된 프로젝트를 사용하여 프로젝트를 범주로 그룹화합니다. 비즈니스 파사드 프로젝트, 웹 UI 프로젝트 등은 하나의 범주로 그룹화됩니다.

 이 시나리오에서는 개발자가 프로그래밍 방식으로 제한을 제공할 수 있지만 개발자가 각 상위 프로젝트 아래에 중첩할 수 있는 프로젝트 수에는 제한이 없습니다. 이러한 유형의 그룹화는 다시 할 수 있으며, 이 경우 자식 프로젝트와 동일한 유형의 프로젝트를 자식 아래에 중첩하여 하위 프로젝트의 하위 프로젝트인 하위 프로젝트가 될 수 있습니다.

 프로젝트 중첩은 의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]본질적인 부분이 아닙니다. 하위 프로젝트 내에서 중첩 및 하위 프로젝트 중첩을 사용하도록 코드를 작성해야 합니다. 상위 프로젝트는 프로젝트 중첩을 구현하는 데 필요한 코드를 포함하는 자체 GUID를 만들고 등록한 특수 VSPackage 또는 프로젝트 유형입니다.

 프로젝트를 중첩하는 [방법: 중첩 프로젝트 구현에서](../../extensibility/internals/how-to-implement-nested-projects.md)프로젝트를 중첩하는 방법에 대한 예제를 찾을 수 있습니다.

## <a name="nested-projects-example"></a>중첩된 프로젝트 예제
 ![중첩 된 프로젝트 솔루션](../../extensibility/internals/media/vsnestedprojects.gif "vs네스트프로젝트") 중첩된 프로젝트 예제

## <a name="see-also"></a>참조
- [중첩된 프로젝트 언로드 및 다시 로드에 대한 고려 사항](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [중첩된 프로젝트에 대한 마법사 지원](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [프로젝트 템플릿 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [중첩된 프로젝트에 대한 명령 처리 구현](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [중첩된 프로젝트에 대한 AddItem 필터링 대화 상자](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)
- [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
