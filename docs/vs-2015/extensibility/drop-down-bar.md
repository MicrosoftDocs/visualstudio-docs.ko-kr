---
title: 드롭다운 모음 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204664"
---
# <a name="drop-down-bar"></a>드롭다운 표시줄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

드롭다운 모음은 코드 창의 맨 위에 제공 되며 두 개의 드롭다운 목록을 포함 합니다.  
  
## <a name="drop-down-bar-interfaces"></a>드롭다운 모음 인터페이스  
 예를 들어의 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 드롭다운 막대에는 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 다음 그림과 같이 항목 및 항목 멤버 함수에 대 한 목록이 포함 되어 있습니다.  
  
 ![&#45;음선 삭제](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
드롭다운 모음  
  
 드롭다운 모음을 구현 하는 경우 기본 중요도의 네 가지 인터페이스가 있습니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     드롭다운 모음의 내용을 삽입 하려면이 인터페이스를 구현 합니다. 각 드롭다운 조합에는 일반 텍스트 또는 팬시 텍스트 (굵게, 밑줄 또는 기울임꼴)가 포함 될 수 있으며, 창 텍스트 글꼴 색 지정 또는 회색으로 표시 된 글꼴 색 지정을 사용할 수 있으며, 선택적으로 드롭다운 항목 옆에 작은 비트맵을 제공할 수 있습니다. 인터페이스와 마찬가지로 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 비트맵 이미지는 이미지 목록에 제공 됩니다. 각 드롭다운 조합에는 다른 이미지 목록을 사용할 수 있습니다. 그러나 각 이미지 목록에는 같은 높이의 이미지가 포함 되어야 합니다. 또한 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> 각 조합에 대 한 도구 설명을 제공할 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     이 인터페이스를 호출 하 여 코드 창의 드롭다운 모음을 만들거나 삭제 합니다. 이 인터페이스는 메서드를 호출 하 여 드롭다운 막대가 코드 창에 이미 연결 되어 있는지 여부를 확인 하는 데도 사용할 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> . <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>에서를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 합니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     드롭다운 표시줄과 직접 통신 하려면이 인터페이스를 호출 합니다. 이 인터페이스를 사용 하 여 드롭다운 모음 내용을 강제로 새로 고치거 나 목록 상자 중 하나에서 선택 항목을 변경할 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     을 `ShowDropdownBarOption` 언어 서비스 레지스트리 키에 등록 한 경우 코드 창 관리자는이 이벤트를 모니터링 하 여 드롭다운 모음이 표시 되어야 하는지 여부에 대 한 사용자 기본 설정과 동기화 해야 합니다. 언어 서비스 키에이 옵션을 등록 하지 않으면 **옵션** 메뉴에서 드롭다운 모음을 표시 하거나 숨기는 옵션을 사용할 수 없습니다.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>코드 창에 드롭다운 모음 연결  
 드롭다운 모음을 만들 때 코드 창에 연결 하려면 메서드를 호출할 때 언어 서비스를 드롭다운 모음에 연결 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . 메서드를 호출할 때 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> 드롭다운 막대가 아직 없는 것으로 표시 되 면를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> 합니다. 인터페이스에 액세스 하려면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 구현이 연결 될 때 반환 되는 포인터에서를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [레거시 API를 사용 하 여 코드 창 사용자 지정](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [레거시 언어 서비스의 탐색 모음 지원](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
