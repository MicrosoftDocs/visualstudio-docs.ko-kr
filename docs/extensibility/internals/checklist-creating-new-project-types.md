---
title: '체크리스트: 새 프로젝트 유형 만들기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709745"
---
# <a name="checklist-create-new-project-types"></a>검사 목록: 새 프로젝트 유형 만들기
새 프로젝트 유형을 만들려면 여러 작업을 완료해야 합니다. 다음 검사 목록은 이러한 작업에 대한 지침을 제공합니다.

1. 새 프로젝트 유형에 대한 기능을 디자인합니다. 자세한 내용은 [프로젝트 유형 설계 결정을](../../extensibility/internals/project-type-design-decisions.md)참조하십시오.

2. 코드 및 기타 프로젝트 요소에 사용되는 편집기(편집기)를 결정합니다. 코어 또는 표준 편집기또는 프로젝트별 편집기만들기 및 사용할 수 있습니다. 자세한 내용은 [사용자 지정 편집기 및 디자이너 만들기 및](../../extensibility/creating-custom-editors-and-designers.md) [방법: 프로젝트별 편집기 열기를](../../extensibility/how-to-open-project-specific-editors.md)참조하십시오.

3. 프로젝트 항목이 **클래스 보기** 및 **개체 브라우저에**참여할 수 있는 수준을 결정합니다. 자세한 내용은 [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)을 참조하십시오.

4. 프로젝트 및 프로젝트 항목에 대해 이전에 내린 디자인 결정에 따라 새 클래스를 도출합니다.

5. 다음 프로젝트 유형 구성 요소에 대한 코드를 작성합니다.

    - 프로젝트 팩토리, 새로운 프로젝트를 만들고 기존 프로젝트를 열기 관리합니다. 자세한 내용은 [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 만들기를](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)참조하십시오.

    - 프로젝트 계층 구조 및 명령 처리. 자세한 내용은 [HierUtil7 프로젝트 클래스 를 사용하여 프로젝트 유형(C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)및 [프로젝트 모델의 요소,](../../extensibility/internals/elements-of-a-project-model.md) [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)및 [MenuCommands 대 OleMenuCommands를 구현합니다.](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)

    - **새** 프로젝트 대화 상자에 프로젝트를 추가하는 것을 포함하여 프로젝트 항목 관리. 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md) 및 프로젝트 및 항목 템플릿 [등록을](../../extensibility/internals/registering-project-and-item-templates.md)참조하십시오.

    - 프로젝트 상태 및 개별 항목의 지속성입니다. 자세한 내용은 [프로젝트 항목 열기 및 저장을](../../extensibility/internals/opening-and-saving-project-items.md)참조하십시오. 솔루션 정보의 지속성은 [솔루션](../../extensibility/internals/solutions-overview.md)을 참조하십시오.

    - 속성 창에 표시할 구성 독립적 속성입니다. 자세한 내용은 [속성 확장](../../extensibility/internals/extending-properties.md)을 참조하십시오.

    - 속성 페이지에 구현된 프로젝트 구성 속성은 구성 종속 속성을 표시합니다. 자세한 내용은 [구성 관리 옵션을](../../extensibility/internals/managing-configuration-options.md)참조하십시오.

    - 배포를 위한 출력을 등록합니다. 자세한 내용은 [출력에 대한 프로젝트 구성을](../../extensibility/internals/project-configuration-for-output.md)참조하십시오.

    - 프로젝트 시작 서비스. 자세한 내용은 프로젝트 모델 및 [프로젝트 모델 핵심 구성 요소의](../../extensibility/internals/project-model-core-components.md) [요소를](../../extensibility/internals/elements-of-a-project-model.md) 참조하십시오.

    - 에서 파생된 `IDispatch`개체 또는 클래스는 자동화에 사용할 수 있습니다.

    - XML 명령 테이블 *(.vsct)* 파일입니다. 자세한 내용은 [Visual Studio 명령 테이블(.vsct) 파일을](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)참조하십시오.

6. 프로젝트 유형을 테스트, 디버깅 및 시작합니다.

7. **참조 추가** 대화 상자의 **프로젝트** 탭에 프로젝트를 `VARIANT_TRUE` 에 대한 `VSHPROPID_ShowProjInSolutionPage`값으로 설정하여 표시합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>를 참조하세요.

8. VSPackage를 설치하기 위한 Microsoft 설치*프로그램(.msi)* 파일을 만듭니다. 자세한 내용은 [WINDOWS 설치 관리자를 통해 VSPackage 설치,](../../extensibility/internals/installing-vspackages-with-windows-installer.md) [프로젝트 유형 등록](../../extensibility/internals/registering-a-project-type.md)및 [VSPackage 를](../../extensibility/internals/vspackages.md)참조하십시오.

## <a name="see-also"></a>참조
- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [프로젝트 유형을 작성하는 시기](../../extensibility/internals/when-to-create-project-types.md)
- [프로젝트 유형 만들기](../../extensibility/internals/creating-project-types.md)
