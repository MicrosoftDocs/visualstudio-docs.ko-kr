---
title: 명령 구현 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a208fabd3d205793763698cde0f6fe367c7bb8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195065"
---
# <a name="command-implementation"></a>명령 구현
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage에서 명령을 구현 하려면 다음 작업을 수행 해야 합니다.  
  
1. . Vsct 파일에서 명령 그룹을 설정 하 고 명령 그룹에 명령을 추가 합니다. 자세한 내용은 [Visual Studio 명령 테이블 (를 참조 하세요. Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2. Visual Studio에 명령을 등록 합니다.  
  
3. 명령을 구현 합니다.  
  
   다음 섹션에서는 명령을 등록 하 고 구현 하는 방법을 설명 합니다.  
  
## <a name="registering-commands-with-visual-studio"></a>Visual Studio를 사용 하 여 명령 등록  
 메뉴가 메뉴에 표시 되는 경우 VSPackage에를 추가 하 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 고 메뉴 이름 또는 해당 리소스 ID로을 값으로 사용 해야 합니다.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 또한 명령을에 등록 해야 합니다 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>VSPackage가에서 파생 된 경우 메서드를 사용 하 여이 서비스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package> .  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>명령 구현  
 명령을 구현 하는 방법에는 여러 가지가 있습니다. 항상 동일한 방식으로 표시 되는 동일한 메뉴에 정적 메뉴 명령을 사용 하려면 <xref:System.ComponentModel.Design.MenuCommand> 이전 섹션의 예제에 표시 된 대로를 사용 하 여 명령을 만듭니다. 정적 명령을 만들려면 명령 실행을 담당 하는 이벤트 처리기를 제공 해야 합니다. 이 명령은 항상 사용 하도록 설정 되 고 표시 되므로 Visual Studio에 상태를 제공 하지 않아도 됩니다. 특정 조건에 따라 명령의 상태를 변경 하려는 경우 명령을 클래스의 인스턴스로 만들고 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 해당 생성자에서 명령 및 쿼리 상태 처리기를 제공 하는 이벤트 처리기를 제공 하 여 명령 상태가 변경 될 때 Visual Studio에 알릴 수 있습니다. 를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 명령 클래스의 일부로 구현 하거나, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 프로젝트의 일부로 명령을 제공 하는 경우를 구현할 수도 있습니다. 두 인터페이스와 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 클래스 모두에는 Visual Studio에 명령 상태 변경을 알리는 메서드와 명령의 실행을 제공 하는 다른 메서드가 있습니다.  
  
 명령이 명령 서비스에 추가 되 면 명령 체인 중 하나가 됩니다. 명령에 대 한 상태 알림 및 실행 메서드를 구현 하는 경우 해당 특정 명령만 제공 하 고 다른 모든 사례를 체인의 다른 명령에 전달 하도록 주의 해야 합니다. 명령을 전달 하지 못한 경우 (일반적으로를 반환 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.Constants> ) Visual Studio가 제대로 작동 하지 않을 수 있습니다.  
  
## <a name="query-status-methods"></a>쿼리 상태 메서드  
 메서드 또는 메서드 중 하나를 구현 하는 경우 명령이 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 속한 명령 집합의 GUID와 명령의 ID를 확인 합니다. 다음 지침을 따릅니다.  
  
- GUID가 인식 되지 않으면 두 메서드의 구현에서을 반환 해야 <xref:Microsoft.VisualStudio.OLE.Interop.Constants> 합니다.  
  
- 두 메서드의 구현이 GUID를 인식 하지만 실제로 명령을 구현 하지 않은 경우이 메서드는를 반환 해야 <xref:Microsoft.VisualStudio.OLE.Interop.Constants> 합니다.  
  
- 두 메서드의 구현에서 GUID와 명령을 모두 인식 하는 경우 메서드는 `prgCmds` 다음 플래그를 사용 하 여 매개 변수에서 모든 명령의 명령 플래그 필드를 설정 해야 합니다.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 명령이 지원 되는 경우입니다.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 명령이 표시 되지 않아야 하는 경우입니다.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 명령이 설정 되어 있고 확인 된 것으로 표시 되 면입니다.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 명령을 사용할 수 있으면입니다.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 명령이 바로 가기 메뉴에 나타나면이 고, 그렇지 않으면입니다.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 명령이 메뉴 컨트롤러이 고 사용 하도록 설정 되어 있지 않지만 드롭다운 메뉴 목록이 비어 있지 않고 계속 사용할 수 있는 경우 이 플래그는 거의 사용 되지 않습니다.  
  
- 명령이 플래그를 사용 하 여 vsct 파일에 정의 된 경우 `TextChanges` 다음 매개 변수를 설정 합니다.  
  
  - `rgwz` `pCmdText` 매개 변수의 요소를 명령의 새 텍스트로 설정 합니다.  
  
  - `cwActual` `pCmdText` 매개 변수의 요소를 명령 문자열의 크기로 설정 합니다.  
  
  또한 명령을 사용 하 여 자동화 함수를 처리 하지 않는 한 현재 컨텍스트가 자동화 함수가 아닌지 확인 합니다.  
  
  특정 명령이 지원 됨을 나타내려면를 반환 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 합니다. 다른 모든 명령의 경우를 반환 <xref:Microsoft.VisualStudio.OLE.Interop.Constants> 합니다.  
  
  다음 예제에서 쿼리 상태 메서드는 먼저 컨텍스트가 자동화 함수가 아닌지를 지정한 다음 올바른 명령 집합 GUID 및 명령 ID를 찾습니다. 명령 자체는 사용 하도록 설정 되 고 지원 됩니다. 다른 명령은 지원 되지 않습니다.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>실행 메서드  
 Execute 메서드의 구현은 쿼리 상태 메서드의 구현과 유사 합니다. 먼저 컨텍스트가 자동화 함수가 아닌지 확인 합니다. 그런 다음 GUID와 명령 ID를 모두 테스트 합니다. GUID 또는 명령 ID를 인식할 수 없는 경우을 반환 <xref:Microsoft.VisualStudio.OLE.Interop.Constants> 합니다.  
  
 명령을 처리 하려면 명령을 실행 하 고 실행이 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 성공 하면를 반환 합니다. 명령은 오류 검색 및 알림을 담당 합니다. 따라서 실행이 실패 하면 오류 코드를 반환 합니다. 다음 예제에서는 실행 메서드를 구현 하는 방법을 보여 줍니다.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
