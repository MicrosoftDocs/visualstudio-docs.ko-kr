---
title: 명령의 모양 변경 | 마이크로 소프트 문서
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
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739856"
---
# <a name="change-the-appearance-of-a-command"></a>명령의 모양 변경
명령의 모양을 변경하여 사용자에게 피드백을 제공할 수 있습니다. 예를 들어 명령을 사용할 수 없는 경우 다르게 표시하도록 할 수 있습니다. 명령을 사용 가능또는 사용할 수 없게 만들거나 숨기거나 표시하거나 메뉴에서 명령을 선택 하거나 선택을 취소할 수 있습니다.

명령의 모양을 변경하려면 다음 작업 중 하나를 수행합니다.

- 명령 테이블 파일에서 명령 정의에 적절한 플래그를 지정합니다.

- <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 서비스를 사용합니다.

- 인터페이스를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 구현하고 원시 명령 개체를 수정합니다.

  다음 단계에서는 MPF(관리되는 패키지 프레임워크)를 사용하여 명령의 모양을 찾고 업데이트하는 방법을 보여 준다.

### <a name="to-change-the-appearance-of-a-menu-command"></a>메뉴 명령의 모양을 변경하려면

1. [메뉴 명령의 텍스트 변경 명령의 지침에](../extensibility/changing-the-text-of-a-menu-command.md) 따라 `New Text`을 라는 메뉴 항목을 만듭니다.

2. *ChangeMenuText.cs* 파일에서 다음 using 문을 추가합니다.

    ```csharp
    using System.Security.Permissions;
    ```

3. *ChangeMenuTextPackageGuids.cs* 파일에서 다음 줄을 추가합니다.

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. *ChangeMenuText.cs* 파일에서 ShowMessageBox 메서드의 코드를 다음과 같은 것으로 바꿉니다.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 개체에서 업데이트할 명령을 얻은 다음 명령 개체에 적절한 속성을 설정합니다. 예를 들어 다음 메서드를 사용하면 VSPackage 명령 집합에서 지정된 명령을 사용할 수 없거나 사용할 수 없게 됩니다. 다음 코드는 메뉴를 클릭한 후 명명된 `New Text` 메뉴 항목을 사용할 수 없게 만듭니다.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))
            as OleMenuCommandService;
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

6. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험 인스턴스가 나타나야 합니다.

7. **도구** 메뉴에서 변경 **메뉴 텍스트 호출** 명령을 클릭합니다. 이 시점에서 명령 이름은 **ChangeMenuText**호출이므로 명령 처리기에서 **ChangeMyCommand()를**호출하지 않습니다.

8. **도구** 메뉴에 새 **텍스트가**표시됩니다. **새 텍스트를 클릭합니다.** 이제 명령이 회색으로 표시됩니다.

## <a name="see-also"></a>참조
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [비주얼 스튜디오 명령 테이블(. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
