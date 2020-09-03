---
title: 프로젝트 중첩 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707025"
---
# <a name="nesting-projects"></a>프로젝트 중첩
VS 패키지를 사용 하는 엔터프라이즈 응용 프로그램 개발자는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *프로젝트 중첩*을 사용 하 여 비슷한 형식의 프로젝트를에서 편리 하 게 그룹화 할 수 있습니다. 예를 들어 Enterprise Template 프로젝트는 중첩 된 프로젝트를 사용 하 여 프로젝트를 범주로 그룹화 합니다. 비즈니스 외관 프로젝트, 웹 UI 프로젝트 등은 하나의 범주에 함께 그룹화 됩니다.

 개발자가 프로그래밍 방식으로 제한을 제공할 수 있지만이 시나리오에서는 개발자가 각 부모 프로젝트에서 중첩할 수 있는 프로젝트 수에 제한이 없습니다. 이러한 종류의 그룹화도 재귀적으로 만들 수 있습니다 .이 경우 자식 프로젝트와 동일한 형식의 프로젝트가 자식에 중첩 되어 부모의 하위 프로젝트가 될 수 있습니다.

 프로젝트 중첩은의 내장 부분이 아닙니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 자식 프로젝트 내에서 중첩 및 하위 프로젝트 중첩을 사용 하도록 설정 하는 코드를 작성 해야 합니다. 부모 프로젝트는 특수 한 VSPackage 또는 프로젝트 형식이 며 프로젝트 중첩을 구현 하는 데 필요한 코드를 포함 하는 고유한 GUID를 사용 하 여 생성 및 등록 됩니다.

 [방법: 중첩 프로젝트 구현](../../extensibility/internals/how-to-implement-nested-projects.md)에서 프로젝트를 중첩 하는 방법에 대 한 예제를 찾을 수 있습니다.

## <a name="nested-projects-example"></a>중첩 프로젝트 예제
 ![중첩 프로젝트 솔루션](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") 중첩 프로젝트 예제

## <a name="see-also"></a>추가 정보
- [중첩된 프로젝트 언로드 및 다시 로드에 대한 고려 사항](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [중첩된 프로젝트에 대한 마법사 지원](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [프로젝트 템플릿 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [중첩된 프로젝트에 대한 명령 처리 구현](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [중첩된 프로젝트에 대한 AddItem 필터링 대화 상자](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)
- [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
