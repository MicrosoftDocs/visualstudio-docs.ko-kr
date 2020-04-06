---
title: 마법사 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703206"
---
# <a name="wizards"></a>마법사
마법사를 만든 후에는 일반적으로 다른 사용자가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용할 수 있도록 통합 개발 환경(IDE)에 마법사를 추가하려고 합니다. 그러면 추가된 마법사가 **새 프로젝트 추가** 또는 새 항목 **추가** 대화 상자에 나타납니다. **새 프로젝트 추가** 또는 새 항목 **추가** 대화 상자가 보려면 **솔루션 탐색기에서**열린 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가를**가리키고 **새 프로젝트** 또는 **새 항목을**클릭합니다.

 마법사를 구현하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자가 **새 프로젝트 추가** 대화 상자 또는 새 **항목 추가** 대화 상자를 열 때 또는 **솔루션 탐색기에서**항목을 마우스 오른쪽 단추로 클릭할 때 사용 가능한 값의 트리 보기에서 선택할 수 있도록 할 수 있습니다.

 마법사에서 새 프로젝트 또는 IT의 이름을 지역화하는 옵션을 제공할 수 있으며 사용자가 마법사를 선택할 때 표시되는 아이콘을 확인할 수 있습니다. 사용 가능한 다른 항목에 대해 새 항목이 표시되는 순서를 제어할 수도 있습니다. 항목을 사전순으로 구성할 필요는 없습니다.

 마법사가 열릴 때 마법사에 전달되는 사용자 지정 매개 변수에 따라 다르게 시작하는 마법사를 제공할 수도 있습니다.

 이 섹션의 항목에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **새 프로젝트 추가** 및 새 **항목 추가** 대화 상자를 사용하여 사용 가능한 마법사 및 템플릿 간에 마법사를 나열하기 위해 구현하는 파일과 마법사가 IDE에서 올바르게 작동하기 위해 충족해야 하는 요구 사항에 대해 설명합니다.

## <a name="in-this-section"></a>섹션 내용
- [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 어떤 템플릿 디렉터리 설명 파일에 대한 개요를 제공하고 대화 상자의 프로젝트와 연결된 폴더, 마법사 .vsz 파일 및 템플릿 파일을 표시하기 위해 IDE에서 작동하는 방법을 설명합니다.

- [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)

 IDE가 마법사를 시작하는 방법을 설명하고 .vsz 파일의 세 부분을 나열합니다.

- [마법사 인터페이스(IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 마법사가 `IDTWizard` IDE에서 작동하도록 구현해야 하는 인터페이스에 대해 설명합니다.

- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)

 마법사가 구현되는 방법과 IDE가 컨텍스트 매개 변수를 구현에 전달할 때 발생하는 현상에 대해 설명합니다.

- [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)

 사용자 지정 매개 변수를 사용하여 마법사를 시작한 후 마법사의 작업을 제어하는 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 유형](../../extensibility/internals/project-types.md)

 새 프로젝트 유형을 디자인하는 방법에 대한 정보를 제공하는 추가 항목에 대한 링크를 제공합니다.

- [프로젝트 확장](../../extensibility/extending-projects.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 및 솔루션을 사용하여 코드 파일 및 리소스 파일을 구성하는 방법 및 소스 제어를 구현하는 방법을 설명합니다.
