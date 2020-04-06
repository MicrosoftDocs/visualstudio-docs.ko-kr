---
title: 명령 구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709574"
---
# <a name="command-implementation"></a>명령 구현
VSPackage에서 명령을 구현하려면 다음 작업을 수행해야 합니다.

1. *.vsct* 파일에서 명령 그룹을 설정한 다음 명령을 추가합니다. 자세한 내용은 [Visual Studio 명령 테이블(.vsct) 파일을](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)참조하십시오.

2. Visual Studio에 명령을 등록합니다.

3. 명령을 구현합니다.

다음 섹션에서는 명령을 등록하고 구현하는 방법을 설명합니다.

## <a name="register-commands-with-visual-studio"></a>비주얼 스튜디오로 명령 등록
 명령이 메뉴에 표시되려면 VSPackage에 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 이 명령을 추가하고 메뉴 이름 또는 리소스 ID의 값으로 사용해야 합니다.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 또한 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>명령을 에 등록해야 합니다. VSPackage에서 파생 된 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 경우 메서드를 사용 하 <xref:Microsoft.VisualStudio.Shell.Package>여이 서비스를 얻을 수 있습니다.

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

## <a name="implement-commands"></a>명령 구현
 명령을 구현하는 방법에는 여러 가지가 있습니다. 항상 같은 방식으로 동일한 메뉴에 나타나는 명령인 정적 메뉴 명령을 원하는 경우 이전 섹션의 예제와 같이 사용하여 <xref:System.ComponentModel.Design.MenuCommand> 명령을 만듭니다. 정적 명령을 만들려면 명령을 실행하는 이벤트 처리기를 제공해야 합니다. 명령은 항상 활성화되고 표시되므로 Visual Studio에 상태를 제공할 필요가 없습니다. 특정 조건에 따라 명령의 상태를 변경하려는 경우 명령을 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 클래스의 인스턴스로 만들고 생성자에서 명령의 상태가 변경될 때 Visual Studio에 `QueryStatus` 알리는 명령과 처리기를 실행하는 이벤트 처리기를 제공할 수 있습니다. 명령 클래스의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 일부로 구현하거나 프로젝트의 일부로 명령을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 제공하는 경우 구현할 수도 있습니다. 두 인터페이스와 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 클래스에는 모두 Visual Studio에 명령 상태 변경을 알리는 메서드와 명령 실행을 제공하는 다른 메서드가 있습니다.

 명령이 명령 서비스에 추가되면 명령 체인 중 하나가 됩니다. 명령에 대한 상태 알림 및 실행 메서드를 구현할 때는 해당 특정 명령에 대해서만 제공하고 다른 모든 경우를 체인의 다른 명령으로 전달하도록 주의하십시오. 명령을 전달하지 못하면(일반적으로 반환) <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>Visual Studio가 제대로 작동하지 않을 수 있습니다.

## <a name="querystatus-methods"></a>쿼리 상태 메서드
 메서드 또는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 메서드를 구현하는 경우 명령이 속한 명령 집합의 GUID와 명령의 ID를 확인합니다. 다음 지침을 따릅니다.

- GUID가 인식되지 않으면 두 메서드 중 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>하나를 구현하면 반환해야 합니다.

- 두 방법 중 하나를 구현하여 GUID를 인식하지만 명령을 구현하지 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>않은 경우 메서드가 반환되어야 합니다.

- 두 방법 중 하나를 구현하여 GUID와 명령을 모두 인식하는 경우 메서드는 다음 `prgCmds` <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 플래그를 사용하여 모든 명령(매개 변수)의 명령 플래그 필드를 설정해야 합니다.

  - `OLECMDF_SUPPORTED`: 명령이 지원됩니다.

  - `OLECMDF_INVISIBLE`: 명령이 표시되지 않아야 합니다.

  - `OLECMDF_LATCHED`: 명령이 켜지고 확인된 것으로 나타납니다.

  - `OLECMDF_ENABLED`: 명령이 활성화되었습니다.

  - `OLECMDF_DEFHIDEONCTXTMENU`: 바로 가기 메뉴에 나타나는 경우 명령을 숨김해야 합니다.

  - `OLECMDF_NINCHED`: 명령은 메뉴 컨트롤러이며 활성화되지 않지만 드롭다운 메뉴 목록은 비어 있지 않으며 여전히 사용할 수 있습니다. (이 플래그는 거의 사용되지 않습니다.)

- `TextChanges` 플래그가 있는 *.vsct* 파일에 명령이 정의된 경우 다음 매개 변수를 설정합니다.

  - `pCmdText` 매개 변수의 `rgwz` 요소를 명령의 새 텍스트로 설정합니다.

  - `pCmdText` 매개 변수의 `cwActual` 요소를 명령 문자열의 크기로 설정합니다.

또한 명령이 자동화 함수를 처리하도록 특별히 의도되지 않는 한 현재 컨텍스트가 자동화 함수가 아닌지 확인합니다.

특정 명령을 지원함을 나타내려면 <xref:Microsoft.VisualStudio.VSConstants.S_OK>을 반환합니다. 다른 모든 명령의 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>경우 을 반환합니다.

다음 예제에서 메서드는 `QueryStatus` 먼저 컨텍스트가 자동화 함수가 아닌지 확인한 다음 올바른 명령 집합 GUID 및 명령 ID를 찾습니다. 명령 자체가 활성화되고 지원됩니다. 다른 명령은 지원되지 않습니다.

```csharp
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

## <a name="execution-methods"></a>실행 방법
 메서드의 `Exec` 구현은 메서드의 `QueryStatus` 구현과 유사합니다. 먼저 컨텍스트가 자동화 기능이 아닌지 확인합니다. 그런 다음 GUID와 명령 ID를 모두 테스트합니다. GUID 또는 명령 ID가 인식되지 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>않으면 을 반환합니다.

 명령을 처리하려면 명령을 실행하고 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 실행이 성공하면 반환합니다. 명령은 오류 감지 및 알림을 담당합니다. 따라서 실행이 실패하면 오류 코드를 반환합니다. 다음 예제에서는 실행 메서드를 구현 하는 방법을 보여 줍니다.

```csharp
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

## <a name="see-also"></a>참조

- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
