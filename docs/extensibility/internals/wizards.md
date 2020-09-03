---
title: 마법사 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703206"
---
# <a name="wizards"></a>마법사
마법사를 만든 후에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는 다른 사용자가 사용할 수 있도록 일반적으로 IDE (통합 개발 환경)에 추가 하려고 합니다. 그러면 추가 된 마법사가 **새 프로젝트 추가** 또는 **새 항목 추가** 대화 상자에 나타납니다. **새 프로젝트 추가** 또는 **새 항목 추가** 대화 상자를 표시 하려면 **솔루션 탐색기**에서 열려 있는 솔루션을 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 프로젝트** 또는 **새 항목**을 클릭 합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]사용자가 **새 프로젝트 추가** 대화 상자 또는 **새 항목 추가** 대화 상자를 열거나 **솔루션 탐색기**항목을 마우스 오른쪽 단추로 클릭할 때 사용 가능한 값의 트리 뷰에서 선택할 수 있도록에서 마법사를 구현할 수 있습니다.

 마법사에서 새 프로젝트 또는 유틸리티의 이름을 지역화 하는 옵션을 제공 하 고 사용자가 마법사를 선택할 때 표시 되는 아이콘을 확인할 수 있습니다. 또한 다른 사용 가능한 항목을 기준으로 새 항목이 표시 되는 순서를 제어할 수 있습니다. 항목을 사전순으로 구성할 필요가 없습니다.

 마법사를 열 때 마법사에 전달 되는 사용자 지정 매개 변수에 따라 다르게 시작 되는 마법사를 제공할 수도 있습니다.

 이 단원의 항목에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **새 프로젝트 추가** 및 **새 항목 추가** 대화 상자를 사용 하 여 마법사에서 사용 가능한 마법사와 템플릿을 표시 하 고 마법사가 IDE에서 제대로 작동 하기 위해 충족 해야 하는 요구 사항을 충족 하기 위해 구현 하는 파일에 대해 설명 합니다.

## <a name="in-this-section"></a>섹션 내용
- [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 템플릿 디렉터리 설명 파일의 개요를 제공 하 고 IDE에서 폴더, 마법사 .vsz 파일 및 대화 상자의 프로젝트와 관련 된 템플릿 파일을 표시 하는 방법을 설명 합니다.

- [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)

 IDE에서 마법사를 시작 하 고 .vsz 파일의 세 부분을 나열 하는 방법을 설명 합니다.

- [마법사 인터페이스(IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 `IDTWizard`IDE에서 작업 하기 위해 마법사에서 구현 해야 하는 인터페이스에 대해 설명 합니다.

- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)

 IDE가 구현에 컨텍스트 매개 변수를 전달할 때 마법사를 구현 하는 방법과 어떻게 되는지 설명 합니다.

- [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)

 사용자 지정 매개 변수를 사용 하 여 마법사가 시작 된 후의 마법사 작업을 제어 하는 방법을 설명 합니다.

## <a name="related-sections"></a>관련 섹션
- [프로젝트 형식](../../extensibility/internals/project-types.md):

 새 프로젝트 형식을 디자인 하는 방법에 대 한 정보를 제공 하는 추가 항목에 대 한 링크를 제공 합니다.

- [프로젝트 확장](../../extensibility/extending-projects.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 및 솔루션을 사용하여 코드 파일 및 리소스 파일을 구성하는 방법 및 소스 제어를 구현하는 방법을 설명합니다.
