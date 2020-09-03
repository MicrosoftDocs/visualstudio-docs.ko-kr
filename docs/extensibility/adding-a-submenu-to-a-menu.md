---
title: 메뉴에 하위 메뉴 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5887dba1ed1c583653b93792174524f8dfb84609
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86972324"
---
# <a name="add-a-submenu-to-a-menu"></a>메뉴에 하위 메뉴 추가
이 연습은 **Testmenu** 메뉴에 하위 메뉴를 추가 하는 방법을 보여 주기 [위해 Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 의 데모를 기반으로 합니다.

 하위 메뉴는 다른 메뉴에 표시 되는 보조 메뉴입니다. 하위 메뉴는 이름 뒤에 오는 화살표로 식별할 수 있습니다. 이름을 클릭 하면 하위 메뉴와 해당 명령이 표시 됩니다.

 이 연습에서는 Visual Studio 메뉴 모음의 메뉴에 하위 메뉴를 만들고 하위 메뉴에 새 명령을 삽입 합니다. 또한이 연습에서는 새 명령을 구현 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="add-a-submenu-to-a-menu"></a>메뉴에 하위 메뉴 추가

1. [Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 의 단계에 따라 프로젝트 및 메뉴 항목을 만듭니다. 이 연습의 단계에서는 VSIX 프로젝트의 이름이 인 것으로 가정 합니다 `TopLevelMenu` .

2. *Testcommandpackage. vsct*를 엽니다. 섹션에서 하위 `<Symbols>` `<IDSymbol>` 메뉴에 대 한 요소, 하위 메뉴 그룹 및 명령에 대 한 요소를 모두 `<GuidSymbol>` "guidTopLevelMenuCmdSet" 라는 노드에 추가 합니다. `<IDSymbol>`최상위 메뉴에 대 한 요소를 포함 하는 동일한 노드입니다.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. 새로 만든 하위 메뉴를 섹션에 추가 합니다 `<Menus>` .

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     부모의 GUID/ID 쌍은 [Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)에서 생성 된 메뉴 그룹을 지정 하 고 최상위 메뉴의 자식입니다.

4. 2 단계에서 정의한 메뉴 그룹을 섹션에 추가 하 `<Groups>` 고 하위 메뉴의 자식으로 만듭니다.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. `<Button>`섹션에 새 요소를 추가 `<Buttons>` 하 여 2 단계에서 만든 명령을 하위 메뉴의 항목으로 정의 합니다.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. 솔루션을 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다.

7. **Testmenu** 를 클릭 하 여 **하위 메뉴**라는 새 하위 메뉴를 표시 합니다. 하위 **메뉴** 를 클릭 하 여 하위 메뉴를 열고 새 명령 **Test Sub command**를 확인 합니다. **Test Sub Command** 를 클릭 하면 아무 작업도 수행 되지 않습니다.

## <a name="add-a-command"></a>명령 추가

1. *TestCommand.cs* 를 열고 다음 명령 id를 기존 명령 id 뒤에 추가 합니다.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. 하위 명령을 추가 합니다. 명령 생성자를 찾습니다. 메서드를 호출한 직후에 다음 줄을 추가 합니다 `AddCommand` .

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    `SubItemCallback`명령 처리기는 나중에 정의 됩니다. 이제 생성자는 다음과 같습니다.

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. `SubItemCallback()`를 추가합니다. 하위 메뉴의 새 명령이 클릭 될 때 호출 되는 메서드입니다.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        IVsUIShell uiShell = this.package.GetService<SVsUIShell, IVsUIShell>();
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다.

5. **Testmenu** 메뉴에서 **하위 메뉴** 를 클릭 한 다음 **Test sub Command**를 클릭 합니다. 메시지 상자가 나타나고 "TestCommand 내에 Test Command. SubItemCallback ()" 라는 텍스트가 표시 됩니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
