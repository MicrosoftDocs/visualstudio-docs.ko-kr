---
title: 명령 라우팅 알고리즘 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3b8602df40045a3f4e1fc91fee92151bf5dd4ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195107"
---
# <a name="command-routing-algorithm"></a>명령 라우팅 알고리즘
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio의 명령은 다양 한 구성 요소에 의해 처리 됩니다. 명령은 현재 선택 항목을 기반으로 하는 가장 안쪽 컨텍스트부터 가장 바깥쪽 (전역) 컨텍스트로 라우팅됩니다. 자세한 내용은 [Availability](../../extensibility/internals/command-availability.md)을 참조 하세요.  
  
## <a name="order-of-command-resolution"></a>명령 확인 순서  
 명령은 다음과 같은 수준의 명령 컨텍스트를 통해 전달 됩니다.  
  
1. 추가 기능: 환경에서는 먼저 있는 추가 기능에 대 한 명령을 제공 합니다.  
  
2. 우선 순위 명령: 이러한 명령은를 사용 하 여 등록 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Visual Studio의 모든 명령에 대해 호출 되며 등록 된 순서 대로 호출 됩니다.  
  
3. 상황에 맞는 메뉴 명령: 상황에 맞는 메뉴에 있는 명령은 먼저 상황에 맞는 메뉴에 제공 되는 명령 대상에 제공 된 후 일반 라우팅에 대해 제공 됩니다.  
  
4. Toolbar set 명령 대상: 이러한 명령 대상은를 호출할 때 등록 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . 합니다 `pCmdTarget` 매개 변수 수 `null`입니다. 그렇지 않으면 `null` 이 명령 대상이 설정 된 도구 모음에 있는 모든 명령을 업데이트 하는 데 사용 됩니다. 셸에서 도구 모음을 설정 하는 경우 창 프레임을로 전달 하 여 `pCmdTarget` 도구 모음에 있는 명령에 대 한 모든 업데이트가 포커스가 없는 경우에도 창 프레임을 통과 하도록 합니다.  
  
5. 도구 창: 일반적으로 인터페이스를 구현 하는 도구 창은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . 그러면 도구 창이 활성 창인 경우에도 Visual Studio에서 명령 대상을 가져올 수 있습니다. 그러나 포커스가 있는 도구 창이 **프로젝트** 창인 경우 명령이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 선택 된 항목의 공통 부모인 인터페이스로 라우팅됩니다 (해당). 이 선택 영역이 여러 프로젝트에 걸쳐 있으면 명령이 계층으로 라우팅됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> . 인터페이스에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 인터페이스의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 해당 명령과 유사한 및 메서드가 포함 되어 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
6. 문서 창: 명령이 RouteToDocs 파일에 설정 된 경우 Visual Studio는 인터페이스의 인스턴스이거나 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 문서 개체의 인스턴스 (일반적으로 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 인터페이스 또는 인터페이스) 인 문서 뷰 개체에서 명령 대상을 검색 하는 것 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 입니다. 문서 보기 개체가 명령을 지원 하지 않는 경우 Visual Studio는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 반환 되는 인터페이스로 명령을 라우팅합니다. 이는 문서 데이터 개체에 대 한 선택적 인터페이스입니다.  
  
7. 현재 계층: 현재 계층은 활성 문서 창이 나 **솔루션 탐색기**에서 선택 된 계층을 소유 하는 프로젝트 일 수 있습니다. Visual Studio는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 현재 또는 활성 계층에 구현 된 인터페이스를 찾습니다. 계층은 프로젝트 항목의 문서 창에 포커스가 있더라도 계층이 활성화 될 때마다 유효한 명령을 지원 해야 합니다. 그러나 **Solution Explorer** <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 인터페이스와 해당 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 및 메서드를 사용 하 여 솔루션 탐색기에 포커스가 있는 경우에만 적용 되는 명령을 지원 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .  
  
     **잘라내기**, **복사**, **붙여넣기**, **삭제**, **이름 바꾸기**, **입력**및 **DoubleClick** 명령에는 특별 한 처리가 필요 합니다. 계층에서 **Delete** 및 **Remove** 명령을 처리 하는 방법에 대 한 자세한 내용은 인터페이스를 참조 하세요 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> .  
  
8. 전역: 이전에 언급 한 컨텍스트에서 명령이 처리 되지 않은 경우 Visual Studio는 인터페이스를 구현 하는 명령을 소유 하는 VSPackage로 라우트 하려고 시도 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . VSPackage가 아직 로드 되지 않은 경우 Visual Studio에서 메서드를 호출할 때 로드 되지 않습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . VSPackage는 메서드가 호출 될 때만 로드 됩니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> .  
  
## <a name="see-also"></a>관련 항목  
 [명령 디자인](../../extensibility/internals/command-design.md)
