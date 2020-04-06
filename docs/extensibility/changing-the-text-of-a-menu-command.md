---
title: 메뉴 명령의 텍스트 변경 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739838"
---
# <a name="change-the-text-of-a-menu-command"></a>메뉴 명령의 텍스트 변경
다음 단계에서는 서비스를 사용하여 메뉴 명령의 텍스트 레이블을 <xref:System.ComponentModel.Design.IMenuCommandService> 변경하는 방법을 보여 줍니다.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>IMenuCommandService를 사용하면 메뉴 명령 레이블 변경

1. **ChangeMenuText라는**메뉴 `MenuText` 명령으로 명명된 VSIX 프로젝트를 만듭니다. 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

2. *.vsct* 파일에서 다음 `TextChanges` 예제와 같이 메뉴 명령에 플래그를 추가합니다.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. *ChangeMenuText.cs* 파일에서 메뉴 명령이 표시되기 전에 호출되는 이벤트 처리기를 만듭니다.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    개체의 <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>의 " <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>및 <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> 속성을 변경하여 이 메서드에서 메뉴 명령의 상태를 업데이트할 수도 있습니다. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>

4. ChangeMenuText 생성자에서 원래 명령 초기화 및 배치 코드를 메뉴 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 명령을 나타내는 `MenuCommand`(a가 아닌) 만들고 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 이벤트 처리기를 추가하고 메뉴 명령 서비스에 메뉴 명령을 제공하는 코드로 바꿉니다.

    다음과 같이 보일 수 있습니다.

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험 인스턴스가 나타납니다.

6. **도구** 메뉴에는 **ChangeMenuText 호출이라는**명령이 표시됩니다.

7. 명령을 클릭합니다. **MenuItemCallback이** 호출되었음을 알리는 메시지 상자가 표시됩니다. 메시지 상자를 해제하면 도구 메뉴의 명령 이름이 **이제 새 텍스트인**것을 볼 수 있습니다.
