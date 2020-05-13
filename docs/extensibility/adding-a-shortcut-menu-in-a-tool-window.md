---
title: 도구 창에 바로 가기 메뉴 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740286"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>도구 창에 바로 가기 메뉴 추가
이 연습에서는 도구 창에 바로 가기 메뉴를 넣습니다. 바로 가기 메뉴는 사용자가 단추, 텍스트 상자 또는 창 배경을 마우스 오른쪽 단추를 마우스 오른쪽 단추로 클릭할 때 나타나는 메뉴입니다. 바로 가기 메뉴의 명령은 다른 메뉴 또는 도구 모음의 명령과 동일하게 실행됩니다. 바로 가기 메뉴를 지원하려면 *.vsct* 파일에 지정하고 마우스 오른쪽 단추 클릭에 대한 응답으로 표시합니다.

도구 창은 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>에서 상속되는 사용자 지정 도구 창 클래스의 WPF 사용자 컨트롤로 구성됩니다.

이 연습에서는 *.vsct* 파일에서 메뉴 항목을 선언한 다음 관리되는 패키지 프레임워크를 사용하여 도구 창을 정의하는 클래스에서 구현하여 바로 가기 메뉴를 Visual Studio 메뉴로 만드는 방법을 보여 줍니다. 이 방법을 사용하면 Visual Studio 명령, UI 요소 및 자동화 개체 모델에 쉽게 액세스할 수 있습니다.

또는 바로 가기 메뉴가 Visual Studio 기능에 액세스하지 않는 <xref:System.Windows.FrameworkElement.ContextMenu%2A> 경우 사용자 컨트롤에서 XAML 요소의 속성을 사용할 수 있습니다. 자세한 내용은 [컨텍스트 메뉴](/dotnet/framework/wpf/controls/contextmenu)를 참조하십시오.

## <a name="prerequisites"></a>사전 요구 사항
Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-the-tool-window-shortcut-menu-package"></a>공구 창 바로 가기 메뉴 패키지 만들기

1. 명명된 `TWShortcutMenu` VSIX 프로젝트를 만들고 **바로 가기Menu라는** 도구 창 템플릿을 추가합니다. 도구 창 만들기에 대한 자세한 내용은 [도구 창을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오.

## <a name="specifying-the-shortcut-menu"></a>바로 가기 메뉴 지정
이 연습에 표시된 바로 가기 메뉴와 같은 바로 가기 메뉴를 사용하면 도구 창의 배경을 채우는 데 사용되는 색상 목록에서 선택할 수 있습니다.

1. *바로 가기MenuPackage.vsct에서*guid바로가기MenuPackageSet라는 GuidSymbol 요소를 찾아 바로 가기 메뉴, 바로 가기 메뉴 그룹 및 메뉴 옵션을 선언합니다. 이제 GuidSymbol 요소는 다음과 같이 표시됩니다.

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Buttons 요소 바로 앞에 메뉴 요소를 만든 다음 바로 가기 메뉴를 정의합니다.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    바로 가기 메뉴에는 메뉴 또는 도구 모음의 일부가 아니므로 부모가 없습니다.

3. 바로 가기 메뉴 항목을 포함하는 그룹 요소를 사용하여 그룹 요소를 만들고 그룹을 바로 가기 메뉴와 연결합니다.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Buttons 요소에서 바로 가기 메뉴에 나타날 개별 명령을 정의합니다. 단추 요소는 다음과 같아야 합니다.

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. *ShortcutMenuCommand.cs*명령 집합 GUID, 바로 가기 메뉴 및 메뉴 항목에 대한 정의를 추가합니다.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    다음은 *바로 가기MenuPackage.vsct* 파일의 기호 섹션에 정의된 것과 동일한 명령 아이디입니다. *.vsct* 파일에만 필요하기 때문에 컨텍스트 그룹은 여기에 포함되지 않습니다.

## <a name="implementing-the-shortcut-menu"></a>바로 가기 메뉴 구현
 이 섹션에서는 바로 가기 메뉴와 해당 명령을 구현합니다.

1. *ShortcutMenu.cs*도구 창에서 메뉴 명령 서비스를 얻을 수 있지만 포함된 컨트롤은 얻을 수 없습니다. 다음 단계는 사용자 컨트롤에서 메뉴 명령 서비스를 사용할 수 있도록 하는 방법을 보여 줍니다.

2. *ShortcutMenu.cs*지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. 도구 창의 Initialize() 메서드를 재정의하여 메뉴 명령 서비스를 받고 컨트롤을 추가하여 메뉴 명령 서비스를 생성자에게 전달합니다.

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. 바로 가기메뉴 도구 창 생성자에서 컨트롤을 추가하는 줄을 제거합니다. 생성자는 이제 다음과 같이 보입니다.

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. *ShortcutMenuControl.xaml.cs*메뉴 명령 서비스에 대한 전용 필드를 추가하고 컨트롤 생성기를 변경하여 메뉴 명령 서비스를 수행합니다. 그런 다음 메뉴 명령 서비스를 사용하여 컨텍스트 메뉴 명령을 추가합니다. 바로 가기MenuControl 생성자는 이제 다음과 같은 코드처럼 보입니다. 명령 처리기는 나중에 정의됩니다.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. *바로 가기MenuControl.xaml에서*최상위 <xref:System.Windows.UIElement.MouseRightButtonDown> <xref:System.Windows.Controls.UserControl> 요소에 이벤트를 추가합니다. XAML 파일은 이제 다음과 같이 표시됩니다.

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. *ShortcutMenuControl.xaml.cs*이벤트 처리기에 대한 스텁을 추가합니다.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. 지시문을 사용하여 다음을 동일한 파일에 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. 다음과 `MyToolWindowMouseRightButtonDown` 같이 이벤트를 구현합니다.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    이렇게 하면 <xref:System.ComponentModel.Design.CommandID> 바로 가기 메뉴에 대한 개체가 생성되고, 마우스 클릭 의 위치를 식별하고, <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> 메서드를 사용하여 해당 위치에서 바로 가기 메뉴를 엽니다.

10. 명령 처리기를 구현합니다.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    이 경우 한 가지 방법으로 모든 메뉴 항목에 대한 이벤트를 <xref:System.ComponentModel.Design.CommandID> 식별하고 그에 따라 배경 색을 설정하여 이벤트를 처리합니다. 메뉴 항목에 관련없는 명령이 포함되어 있는 경우 각 명령에 대해 별도의 이벤트 처리기를 만들었을 것입니다.

## <a name="test-the-tool-window-features"></a>공구 창 기능 테스트

1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

2. 실험적인 경우 **보기 / 기타 창을**클릭한 다음 바로 가기 **메뉴를**클릭합니다. 이렇게 하면 도구 창이 표시됩니다.

3. 도구 창 본문을 마우스 오른쪽 단추로 클릭합니다. 색상 목록이 있는 바로 가기 메뉴가 표시되어야 합니다.

4. 바로 가기 메뉴에서 색상을 클릭합니다. 도구 창 배경색을 선택한 색상으로 변경해야 합니다.

## <a name="see-also"></a>참조
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
- [서비스 이용 및 제공](../extensibility/using-and-providing-services.md)
