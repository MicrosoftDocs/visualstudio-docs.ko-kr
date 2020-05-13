---
title: 프로젝트 및 프로젝트 항목 템플릿 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710202"
---
# <a name="add-project-and-project-item-templates"></a>프로젝트 및 프로젝트 항목 템플릿 추가
고유한 프로젝트 유형을 만들 때 표준 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE(통합 개발 환경) 대화 상자를 사용하여 새 프로젝트 및 프로젝트 항목을 추가하는 데 대한 지원을 제공해야 합니다. 다음 항목에서는 프로젝트 및 프로젝트 항목을 추가하기 위한 다양한 기술에 대해 설명합니다.

## <a name="in-this-section"></a>섹션 내용
- [프로젝트 컨텍스트](../../extensibility/internals/project-context.md)

 이 프로젝트는 환경에서 발생하는 내용에 대한 대부분의 컨텍스트 정보를 제공한다고 설명합니다.

- [프로젝트 우선 순위](../../extensibility/internals/project-priority.md)

 프로젝트 항목은 일반적으로 항목을 여는 데 사용되는 프로젝트에 대한 모호성을 피하기 위해 한 프로젝트의 구성원이라고 설명합니다.

- [기타 파일 프로젝트](../../extensibility/internals/miscellaneous-files-project.md)

 프로젝트에서 파일을 여는 데 사용할 수 있는 두 가지 유형의 편집기와 프로젝트 항목을 열 때 사용할 편집기를 결정하는 데 프로젝트가 수행하는 역할에 대한 정보를 제공합니다.

- [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)

 프로젝트를 만들 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 발생하는 현상을 설명합니다.

- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 새 항목 추가 대화 상자에 항목을 추가하는 프로세스를 **설명합니다.**

- [새 프로젝트 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 VSPackage에서 사용할 수 있는 사용자 지정 템플릿이 포함된 새 디렉터리를 등록하는 예제를 제공합니다.

- [새 항목 추가 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 **새 항목 추가** 대화 상자에 대한 새 디렉터리 집합을 등록하는 예제를 제공합니다.

- [프로젝트 시스템 확장을 위한 IDE 정의 명령](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 프로젝트 시스템 확장에 사용되는 다양한 유형의 명령 항목을 나열합니다.

- [일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 및 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트 시스템을 확장하는 데 사용되는 개체에 대한 CATID를 나열합니다.

## <a name="related-sections"></a>관련 단원
- [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)

 프로젝트의 특정 편집기로 본질적으로 바인딩된 항목을 여는 단계별 지침을 제공합니다.

- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)

 표준 편집기 열기위한 단계별 지침을 제공합니다.

- [프로젝트 하위 유형](../../extensibility/internals/project-subtypes.md)

 프로젝트 하위 유형 개념 항목에 대한 링크를 제공합니다. 프로젝트 하위 유형은 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 기존 및 프로젝트를 확장합니다. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]

- [프로젝트 형식](../../extensibility/internals/project-types.md)

 새 프로젝트 유형을 디자인하는 방법에 대한 정보를 제공하는 추가 항목에 대한 링크를 제공합니다.
