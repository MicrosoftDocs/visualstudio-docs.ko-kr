---
title: 메뉴 명령의 텍스트 변경 | Microsoft Docs
description: 이 코드 예제를 검토 하 여 IMenuCommandService 서비스를 사용 하 여 메뉴 명령의 텍스트 레이블을 변경 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e2d812dbee833358f682b5227785c78322efe44a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911244"
---
# <a name="change-the-text-of-a-menu-command"></a>메뉴 명령의 텍스트를 변경 합니다.
다음 단계에서는 서비스를 사용 하 여 메뉴 명령의 텍스트 레이블을 변경 하는 방법을 보여 줍니다 <xref:System.ComponentModel.Design.IMenuCommandService> .

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>IMenuCommandService를 사용 하 여 메뉴 명령 레이블 변경

1. `MenuText` **ChangeMenuText** 라는 메뉴 명령을 사용 하 여 라는 VSIX 프로젝트를 만듭니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

2. *. Vsct* 파일에서 `TextChanges` 다음 예제와 같이 메뉴 명령에 플래그를 추가 합니다.

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

3. *ChangeMenuText.cs* 파일에서 메뉴 명령이 표시 되기 전에 호출 되는 이벤트 처리기를 만듭니다.

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

    <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>개체의, 및 속성을 변경 하 여이 메서드에서 메뉴 명령의 상태를 업데이트할 수도 있습니다 <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .

4. ChangeMenuText 생성자에서 원래 명령 초기화 및 배치 코드를 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 메뉴 명령을 나타내는 (대신)를 만드는 코드로 바꾸고 `MenuCommand` , 이벤트 처리기를 추가 하 고, 메뉴 명령 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 서비스에 메뉴 명령을 제공 합니다.

    예를 들면 다음과 같습니다.

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 나타납니다.

6. **도구** 메뉴에서 **Invoke ChangeMenuText** 라는 명령이 표시 되어야 합니다.

7. 명령을 클릭 합니다. **MenuItemCallback** 가 호출 되었음을 알리는 메시지 상자가 표시 됩니다. 메시지 상자를 해제할 때 도구 메뉴의 명령 이름이 **새 텍스트** 임을 확인할 수 있습니다.
