---
title: Visual Studio Shell | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ec79aab58e167ff2c935317897ba10a042a2e5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180363"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]셸은의 기본 통합 에이전트입니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 셸은 Vspackage가 공통 서비스를 공유할 수 있도록 하는 데 필요한 기능을 제공 합니다. 의 아키텍처 목표는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] vspackage의 vest 기본 기능에 대 한 것 이기 때문에 shell은 기본 기능을 제공 하 고 해당 구성 요소 vspackage 간의 교차 통신을 지 원하는 프레임 워크입니다.  
  
## <a name="shell-responsibilities"></a>셸 책임  
 셸에는 다음과 같은 주요 책임이 있습니다.  
  
- UI (사용자 인터페이스)의 기본 요소를 지 원하는 (COM 인터페이스를 통해) 여기에는 기본 메뉴 및 도구 모음, 문서 창 프레임 또는 MDI (다중 문서 인터페이스) 자식 창, 도구 창 프레임 및 도킹 지원이 포함 됩니다.  
  
- 문서 지 속성을 조정 하 고 한 문서를 여러 가지 방법으로 열 수 없도록 하거나 호환 되지 않는 방식으로 열 수 없도록 하기 위해 현재 열려 있는 모든 문서의 실행 중인 문서를 RDT (실행 중인 문서 테이블)에서 유지 관리 합니다.  
  
- 명령 라우팅 및 명령 처리 인터페이스인를 지원 `IOleCommandTarget` 합니다.  
  
- 적절 한 시간에 Vspackage를 로드 하는 중입니다. 셸의 성능을 향상 시키려면 VSPackage를 지연 로드 해야 합니다.  
  
- 기본 창 기능을 제공 하는와 같은 특정 공유 서비스 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> 및 기본 창 기능을 제공 하는를 관리 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 합니다.  
  
- 솔루션 파일 (.sln) 관리 솔루션에는 Visual C++ 6.0의 작업 영역 (. dsw) 파일과 유사한 관련 프로젝트 그룹이 포함 되어 있습니다.  
  
- 셸 전체 선택, 컨텍스트 및 통화 추적 Shell은 다음 유형의 항목을 추적 합니다.  
  
  - 현재 프로젝트  
  
  - 현재 프로젝트 항목 또는 ItemID 현재입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
  - **속성** 창의 현재 선택 또는`SelectionContainer`  
  
  - 명령, 메뉴 및 도구 모음의 표시 여부를 제어 하는 UI 컨텍스트 Id 또는 CmdUIGuids  
  
  - 활성 창, 문서 및 실행 취소 관리자와 같은 현재 활성 요소  
  
  - 동적 도움말을 구동 하는 사용자 컨텍스트 특성  
  
  셸은 설치 된 Vspackage와 현재 서비스 간의 통신도 중재 합니다. 셸의 핵심 기능을 지원 하며에 통합 된 모든 Vspackage 사용할 수 있도록 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 합니다. 이러한 핵심 기능에는 다음 항목이 포함 됩니다.  
  
- 대화 상자 및 시작 화면 **정보**  
  
- **새 항목 추가 및 기존 항목 추가** 대화 상자  
  
- **클래스 뷰** 창 및 **개체 브라우저**  
  
- **참조** 대화 상자  
  
- **문서 개요** 창  
  
- **동적 도움말** 창  
  
- **찾기** 및 **바꾸기**  
  
- **프로젝트 열기** 및 **새로 만들기** 메뉴에서 **파일 열기** 대화 상자  
  
- **도구** 메뉴의 **옵션** 대화 상자  
  
- **속성** 창  
  
- **솔루션 탐색기**  
  
- **작업 목록** 창  
  
- **도구 상자**  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackages](../../extensibility/internals/vspackages.md)
