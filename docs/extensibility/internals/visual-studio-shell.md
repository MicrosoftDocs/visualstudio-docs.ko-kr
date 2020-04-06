---
title: 비주얼 스튜디오 쉘 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703999"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 셸은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 통합의 기본 에이전트입니다. 셸은 VSPackage가 공통 서비스를 공유할 수 있도록 하는 데 필요한 기능을 제공합니다. 아키텍처 목표는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage에서 기본 기능을 조끼하는 것이기 때문에 셸은 기본 기능을 제공하고 구성 요소 VSPackage 간의 상호 통신을 지원하는 프레임워크입니다.

## <a name="shell-responsibilities"></a>쉘 책임
 셸에는 다음과 같은 주요 책임이 있습니다.

- 사용자 인터페이스(UI)의 기본 요소(COM 인터페이스를 통해)를 지원합니다. 여기에는 기본 메뉴 및 도구 모음, 문서 창 프레임 또는 MDI(다중 문서 인터페이스) 자식 창, 도구 창 프레임 및 도킹 지원이 포함됩니다.

- 문서의 지속성을 조정하고 한 문서를 여러 가지 방법으로 열 수 없거나 호환되지 않는 방식으로 열 수 없도록 하기 위해 현재 열려 있는 모든 문서 의 실행 중인 문서 목록을 RDT(실행 중인 문서 테이블)에 유지 관리합니다.

- 명령 라우팅 및 명령 처리 인터페이스지원. `IOleCommandTarget`

- 적절한 시간에 VS패키지 로드. 셸의 성능을 향상시키기 위해서는 VSPackage를 지연로드해야 합니다.

- 기본 셸 기능을 제공하는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>및 기본 창 기능을 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>제공하는 및 를 제공하는 와 같은 특정 공유 서비스 관리

- 솔루션(.sln) 파일 관리. 솔루션에는 Visual C++ 6.0의 작업 영역(.dsw) 파일과 유사한 관련 프로젝트 그룹이 포함되어 있습니다.

- 셸 전체 선택, 컨텍스트 및 통화 추적. 셸은 다음과 같은 유형의 항목을 추적합니다.

  - 현재 프로젝트

  - 현재 프로젝트 항목 또는 현재 ItemID<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - **속성** 창 또는`SelectionContainer`

  - 명령, 메뉴 및 도구 모음의 가시성을 제어하는 UI 컨텍스트 아이디 또는 CmdUIGuids

  - 활성 창, 문서 및 관리자 취소와 같은 현재 활성 요소

  - 동적 도움말을 구동하는 사용자 컨텍스트 특성

  셸은 설치된 VSPackage 및 현재 서비스 간의 통신도 중재합니다. 셸의 핵심 기능을 지원하며 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에 통합된 모든 VSPackage에서 사용할 수 있습니다. 이러한 핵심 기능에는 다음 항목이 포함됩니다.

- 대화 상자 및 시작 화면 **소개**

- **새 항목 추가 및 기존 항목** 대화 상자 추가

- **클래스 보기** 창 및 **개체 브라우저**

- **참조** 대화 상자

- **문서 개요** 창

- **동적 도움말** 창

- **찾기** 및 **바꾸기**

- **새** 메뉴에서 **프로젝트** 열기 및 파일 대화 상자 **열기**

- **도구** 메뉴의 **옵션** 대화 상자

- **속성** 창

- **솔루션 탐색기**

- **작업 목록** 창

- **도구 상자**

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackage](../../extensibility/internals/vspackages.md)
