---
title: 도구 모음에 메뉴 컨트롤러 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32cbbbc7784c112b33b5f720b306b8c93269bb82
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903531"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>도구 모음에 메뉴 컨트롤러 추가
이 연습은 도구 [창에 도구 모음 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md) 연습을 기반으로 하며 도구 창 도구 모음에 메뉴 컨트롤러를 추가 하는 방법을 보여 줍니다. 여기에 표시 된 단계는 [도구 모음 추가](../extensibility/adding-a-toolbar.md) 연습에서 만든 도구 모음에도 적용할 수 있습니다.

메뉴 컨트롤러는 분할 컨트롤입니다. 메뉴 컨트롤러의 왼쪽에는 마지막으로 사용한 명령이 표시 되며 클릭 하 여 실행할 수 있습니다. 메뉴 컨트롤러의 오른쪽은 클릭 하면 추가 명령 목록을 열 때 표시 되는 화살표입니다. 목록에서 명령을 클릭 하면 명령이 실행 되 고 메뉴 컨트롤러의 왼쪽에 있는 명령이 바뀝니다. 이러한 방식으로 메뉴 컨트롤러는 항상 목록에서 마지막으로 사용 된 명령을 표시 하는 명령 단추 처럼 작동 합니다.

메뉴 컨트롤러는 메뉴에 표시 될 수 있지만 도구 모음에서 가장 자주 사용 됩니다.

## <a name="prerequisites"></a>사전 요구 사항
Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-menu-controller"></a>메뉴 컨트롤러 만들기

1. 도구 모음을 도구 [창에 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md) 에 설명 된 절차에 따라 도구 모음을 포함 하는 도구 창을 만듭니다.

2. *Twtestcommandpackage. vsct*에서 기호 섹션으로 이동 합니다. **GuidTWTestCommandPackageCmdSet**라는 GuidSymbol 요소에서 메뉴 컨트롤러, 메뉴 컨트롤러 그룹 및 3 개의 메뉴 항목을 선언 합니다.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. 메뉴 섹션에서 마지막 메뉴 항목 뒤에 메뉴 컨트롤러를 메뉴로 정의 합니다.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    `TextChanges` `TextIsAnchorCommand` 메뉴 컨트롤러에서 마지막으로 선택한 명령을 반영 하도록 하려면 및 플래그를 포함 해야 합니다.

4. 그룹 섹션에서 마지막 그룹 항목 뒤에 메뉴 컨트롤러 그룹을 추가 합니다.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    메뉴 컨트롤러를 부모로 설정 하면이 그룹에 배치 된 모든 명령이 메뉴 컨트롤러에 표시 됩니다. `priority`특성은 메뉴 컨트롤러의 유일한 그룹 이므로 기본값 0으로 설정 하는 생략 됩니다.

5. 단추 섹션에서 마지막 단추 항목 뒤에 각 메뉴 항목에 대 한 단추 요소를 추가 합니다.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. 이 시점에서 메뉴 컨트롤러를 살펴볼 수 있습니다. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다.

   1. **보기/기타 창** 메뉴에서 **테스트 ToolWindow**을 엽니다.

   2. 메뉴 컨트롤러가 도구 창의 도구 모음에 나타납니다.

   3. 메뉴 컨트롤러의 오른쪽에 있는 화살표를 클릭 하 여 가능한 세 가지 명령을 표시 합니다.

      명령을 클릭 하면 메뉴 컨트롤러의 제목이 변경 되어 해당 명령이 표시 됩니다. 다음 섹션에서는 이러한 명령을 활성화 하는 코드를 추가 합니다.

## <a name="implement-the-menu-controller-commands"></a>메뉴 컨트롤러 명령 구현

1. *TWTestCommandPackageGuids.cs*에서 기존 명령 id 뒤에 세 개의 메뉴 항목에 대 한 명령 id를 추가 합니다.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. *TWTestCommand.cs*에서 클래스 맨 위에 다음 코드를 추가 `TWTestCommand` 합니다.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. TWTestCommand 생성자에서 메서드를 마지막으로 호출한 후 `AddCommand` 동일한 처리기를 통해 각 명령에 대 한 이벤트를 라우팅하는 코드를 추가 합니다.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. **Twtestcommand** 클래스에 이벤트 처리기를 추가 하 여 선택한 명령을 선택 된 상태로 표시 합니다.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. 사용자가 메뉴 컨트롤러에서 명령을 선택할 때 MessageBox를 표시 하는 이벤트 처리기를 추가 합니다.

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>메뉴 컨트롤러 테스트

1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다.

2. **보기/기타 창** 메뉴에서 **테스트 ToolWindow** 을 엽니다.

    메뉴 컨트롤러가 도구 창의 도구 모음에 표시 되 고 **MC 항목 1**이 표시 됩니다.

3. 화살표 왼쪽에 있는 메뉴 컨트롤러 단추를 클릭 합니다.

    세 개의 항목이 표시 되 고이 중 첫 번째 항목이 선택 되며 아이콘 주위에 강조 상자가 표시 됩니다. **MC 항목 3**을 클릭 합니다.

    **사용자가 선택한 메뉴 컨트롤러 항목 3**에 대화 상자가 나타납니다. 이 메시지는 메뉴 컨트롤러 단추의 텍스트에 해당 합니다. 이제 메뉴 컨트롤러 단추에 **MC 항목 3**이 표시 됩니다.

## <a name="see-also"></a>참조
- [도구 창에 도구 모음 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [도구 모음 추가](../extensibility/adding-a-toolbar.md)
