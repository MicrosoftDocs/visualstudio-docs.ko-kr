---
title: 명령 모양 변경 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c1574704f8848c16f4740189688cb1719f19623
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183719"
---
# <a name="change-the-appearance-of-a-command"></a>명령 모양 변경
명령의 모양을 변경 하 여 사용자에 게 피드백을 제공할 수 있습니다. 예를 들어, 사용할 수 없는 경우 명령이 다르게 표시 되도록 할 수 있습니다. 명령을 사용 하거나 사용 하지 않도록 설정 하거나, 메뉴에서 표시 하거나 숨길 수 있습니다.

명령 모양을 변경 하려면 다음 작업 중 하나를 수행 합니다.

- 명령 테이블 파일에서 명령 정의에 적절 한 플래그를 지정 합니다.

- 서비스를 사용 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 합니다.

- 인터페이스를 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 하 고 원시 명령 개체를 수정 합니다.

  다음 단계에서는 MPF (관리 패키지 프레임 워크)를 사용 하 여 명령의 모양을 찾고 업데이트 하는 방법을 보여 줍니다.

### <a name="to-change-the-appearance-of-a-menu-command"></a>메뉴 명령의 모양을 변경 하려면

1. [메뉴 명령 텍스트 변경](../extensibility/changing-the-text-of-a-menu-command.md) 의 지침에 따라 이라는 메뉴 항목을 만듭니다 `New Text` .

2. *ChangeMenuText.cs* 파일에서 다음 using 문을 추가 합니다.

    ```csharp
    using System.Security.Permissions;
    ```

3. *ChangeMenuTextPackageGuids.cs* 파일에 다음 줄을 추가 합니다.

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. *ChangeMenuText.cs* 파일에서 showmessagebox 메서드의 코드를 다음으로 바꿉니다.

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. 개체에서 업데이트 하려는 명령을 가져온 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 다음 명령 개체에서 적절 한 속성을 설정 합니다. 예를 들어 다음 메서드는 VSPackage 명령 집합에서 지정 된 명령을 사용 하거나 사용할 수 없게 만듭니다. 다음 코드는 클릭 된 메뉴 항목을 `New Text` 사용할 수 없게 만듭니다.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.package.GetService<IMenuCommandService, OleMenuCommandService>();
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);
        MenuCommand mc = mcs.FindCommand(newCmdID);
        if (mc != null)
        {
            mc.Enabled = enableCmd;
            cmdUpdated = true;
        }
        return cmdUpdated;
    }
    ```

6. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 표시 되어야 합니다.

7. **도구** 메뉴에서 **ChangeMenuText 호출** 명령을 클릭 합니다. 이 시점에서 명령 이름은 ChangeMenuText를 **호출**하므로 명령 처리기가 **ChangeMyCommand ()** 를 호출 하지 않습니다.

8. 이제 **도구** 메뉴에 **새 텍스트가**표시 됩니다. **새 텍스트**를 클릭 합니다. 이제 명령이 회색으로 표시 됩니다.

## <a name="see-also"></a>참고 항목
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [Visual Studio 명령 테이블 (. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
