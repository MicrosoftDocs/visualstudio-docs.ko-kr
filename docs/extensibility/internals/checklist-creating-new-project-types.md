---
title: '검사 목록: 새 프로젝트 형식 만들기 | Microsoft Docs'
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
ms.openlocfilehash: 9372762f713b6a5ec78a92eeb96e8a616101b5bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183394"
---
# <a name="checklist-create-new-project-types"></a>검사 목록: 새 프로젝트 형식 만들기
새 프로젝트 형식을 만들려면 몇 가지 작업을 완료 해야 합니다. 다음 검사 목록에서는 이러한 작업에 대 한 지침을 제공 합니다.

1. 새 프로젝트 형식에 대 한 기능을 디자인 합니다. 자세한 내용은 [프로젝트 형식 디자인 결정](../../extensibility/internals/project-type-design-decisions.md)을 참조 하세요.

2. 코드 및 기타 프로젝트 요소에 사용 되는 편집기를 확인 합니다. 핵심 또는 표준 편집기를 사용 하거나 프로젝트별 편집기를 만들고 사용할 수 있습니다. 자세한 내용은 [사용자 지정 편집기 및 디자이너 만들기](../../extensibility/creating-custom-editors-and-designers.md) 및 [방법: 프로젝트 관련 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)를 참조 하세요.

3. **클래스 뷰** 및 **개체 브라우저**에 포함 될 프로젝트 항목의 참여 수준을 결정 합니다. 자세한 내용은 [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)을 참조 하세요.

4. 프로젝트 및 프로젝트 항목에 대해 이전에 만든 디자인 결정에 따라 새 클래스를 파생 시킵니다.

5. 다음 프로젝트 형식 구성 요소에 대 한 코드를 작성 합니다.

    - 프로젝트 팩터리-새 프로젝트 만들기 및 기존 프로젝트 열기를 관리 합니다. 자세한 내용은 [프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)를 참조 하세요.

    - 프로젝트 계층 구조 및 명령 처리. 자세한 내용은 [HierUtil7 프로젝트 클래스를 사용 하 여 프로젝트 형식 구현 (c + +)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), 프로젝트 [모델 요소](../../extensibility/internals/elements-of-a-project-model.md), [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)및 [menucommands와 OleMenuCommands 비교](/visualstudio/misc/menucommands-vs-olemenucommands?view=vs-2015)를 참조 하세요.

    - 프로젝트 항목 관리 ( **새 프로젝트** 대화 상자에 프로젝트 추가 포함) 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md) 및 [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)을 참조 하세요.

    - 프로젝트 상태 및 개별 항목의 지 속성 자세한 내용은 [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)을 참조 하세요. 솔루션 정보를 지 속성은 [솔루션](../../extensibility/internals/solutions-overview.md)을 참조 하세요.

    - 속성 창에 표시할 구성 독립적 속성입니다. 자세한 내용은 [확장 속성](../../extensibility/internals/extending-properties.md)을 참조 하세요.

    - 구성 종속 속성을 표시 하기 위해 속성 페이지에서 구현 되는 프로젝트 구성 속성입니다. 자세한 내용은 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)를 참조 하세요.

    - 배포용 출력을 열거 하는 중입니다. 자세한 내용은 [출력에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)을 참조 하세요.

    - Project 시작 서비스입니다. 자세한 내용은 [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md) 및 [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)를 참조 하세요.

    - 자동화에 사용할 수 있는 개체 또는에서 파생 된 클래스 `IDispatch` 입니다.

    - XML 명령 테이블 (*.vvsct*) 파일. 자세한 내용은 [Visual Studio 명령 테이블 (vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)을 참조 하세요.

6. 프로젝트 형식을 테스트, 디버그 및 시작 합니다.

7. 의 값으로를 설정 하 여 **참조 추가** 대화 상자의 **프로젝트** 탭에 프로젝트를 표시 합니다 `VARIANT_TRUE` `VSHPROPID_ShowProjInSolutionPage` . 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>를 참조하세요.

8. Vspackage를 설치 하기 위한 Microsoft Installer (*.msi*) 파일을 만듭니다. 자세한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [프로젝트 형식 등록](../../extensibility/internals/registering-a-project-type.md)및 [vspackage](../../extensibility/internals/vspackages.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [프로젝트 형식을 만들어야 하는 경우](../../extensibility/internals/when-to-create-project-types.md)
- [프로젝트 형식 만들기](../../extensibility/internals/creating-project-types.md)
