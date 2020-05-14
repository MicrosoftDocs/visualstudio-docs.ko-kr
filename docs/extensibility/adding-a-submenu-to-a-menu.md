---
title: 메뉴에 하위 메뉴 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740275"
---
# <a name="add-a-submenu-to-a-menu"></a>메뉴에 하위 메뉴 추가
이 연습에서는 **TestMenu** 메뉴에 하위 메뉴를 추가하는 방법을 보여 줌으로써 [시각적 스튜디오 메뉴 모음에 메뉴 추가의](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 데모를 기반으로 합니다.

 하위 메뉴는 다른 메뉴에 나타나는 보조 메뉴입니다. 하위 메뉴는 이름 다음에 오는 화살표로 식별할 수 있습니다. 이름을 클릭하면 하위 메뉴와 해당 명령이 표시됩니다.

 이 연습에서는 Visual Studio 메뉴 모음의 메뉴에 하위 메뉴를 만들고 하위 메뉴에 새 명령을 넣습니다. 연습에서도 새 명령을 구현합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="add-a-submenu-to-a-menu"></a>메뉴에 하위 메뉴 추가

1. 시각적 스튜디오 [메뉴 모음에 메뉴 추가 모음의](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 단계를 수행하여 프로젝트 및 메뉴 항목을 만듭니다. 이 연습의 단계는 VSIX 프로젝트의 이름이 `TopLevelMenu`입니다.

2. *오픈 테스트명령 패키지.vsct*. `<Symbols>` 섹션에서 하위 메뉴에 `<IDSymbol>` 대한 요소, 하위 메뉴 그룹에 대한 요소, 명령에 대한 요소를 `<GuidSymbol>` 모두 "guidTopLevelMenuCmdSet"이라는 노드에 추가합니다. 최상위 메뉴의 `<IDSymbol>` 요소를 포함하는 노드와 동일한 노드입니다.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. 새로 만든 하위 메뉴를 `<Menus>` 섹션에 추가합니다.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     부모의 GUID/ID 쌍은 [시각적 스튜디오 메뉴 모음에 메뉴 추가에서](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)생성된 메뉴 그룹을 지정하며 최상위 메뉴의 자식입니다.

4. 2단계에서 정의된 메뉴 그룹을 섹션에 `<Groups>` 추가하고 하위 메뉴의 하위 그룹으로 만듭니다.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. 섹션에 `<Buttons>` `<Button>` 새 요소를 추가하여 2단계에서 만든 명령을 하위 메뉴의 항목으로 정의합니다.

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

6. 솔루션을 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 표시됩니다.

7. **테스트 메뉴를** 클릭하여 하위 메뉴라는 새 하위 메뉴를 **확인합니다.** **하위 메뉴를** 클릭하여 하위 메뉴를 열고 새 명령인 하위 **명령 테스트**가 표시됩니다. **하위 명령 테스트를** 클릭하면 아무 것도 수행되지 않습니다.

## <a name="add-a-command"></a>명령 추가

1. *TestCommand.cs* 열고 기존 명령 ID 다음에 다음 명령 ID를 추가합니다.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. 하위 명령을 추가합니다. 명령 생성자찾기 `AddCommand` 메서드에 대한 호출 직후에 다음 줄을 추가합니다.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    명령 `SubItemCallback` 처리기는 나중에 정의됩니다. 생성자는 이제 다음과 같이 보입니다.

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

3. `SubItemCallback()`를 추가합니다. 하위 메뉴의 새 명령을 클릭할 때 호출되는 메서드입니다.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
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

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타나야 합니다.

5. **TestMenu** 메뉴에서 **하위 메뉴를** 클릭한 다음 하위 **명령 테스트**를 클릭합니다. 메시지 상자가 나타나고 "TestCommand.SubItemCallback()" 내부 테스트 명령"이라는 텍스트가 표시되어야 합니다.

## <a name="see-also"></a>참조

- [비주얼 스튜디오 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
