---
title: 도구 창에서 바로 가기 메뉴 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 60ac63be54c235187e66a85c541f925e1e34cafd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689860"
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>도구 창의 바로 가기 메뉴 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 도구 창에 바로 가기 메뉴를 배치 합니다. 바로 가기 메뉴는 사용자가 단추, 텍스트 상자 또는 창 배경을 마우스 오른쪽 단추로 클릭할 때 나타나는 메뉴입니다. 바로 가기 메뉴의 명령은 다른 메뉴 또는 도구 모음의 명령과 동일 하 게 동작 합니다. 바로 가기 메뉴를 지원 하려면. vsct 파일에서 지정 하 고 마우스 오른쪽 단추 클릭에 대 한 응답으로 표시 합니다.  
  
 도구 창은에서 상속 되는 사용자 지정 도구 창 클래스의 WPF 사용자 정의 컨트롤로 구성 됩니다 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .  
  
 이 연습에서는 vsct 파일에서 메뉴 항목을 선언 하 고 관리 되는 패키지 프레임 워크를 사용 하 여 도구 창을 정의 하는 클래스에서 구현 하는 방법으로 Visual Studio 메뉴로 바로 가기 메뉴를 만드는 방법을 보여 줍니다. 이 방법을 사용 하면 Visual Studio 명령, UI 요소 및 자동화 개체 모델에 쉽게 액세스할 수 있습니다.  
  
 또는 바로 가기 메뉴에서 Visual Studio 기능에 액세스 하지 않는 경우 <xref:System.Windows.FrameworkElement.ContextMenu%2A> 사용자 정의 컨트롤에서 XAML 요소의 속성을 사용할 수 있습니다. 자세한 내용은 [ContextMenu](https://msdn.microsoft.com/library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d)를 참조 하세요.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>도구 창 바로 가기 메뉴 패키지 만들기  
  
1. 이라는 VSIX 프로젝트를 만들고 `TWShortcutMenu` **ShortCutMenu** 라는 도구 창 템플릿을 추가 합니다. 도구 창을 만드는 방법에 대 한 자세한 내용은 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요.  
  
## <a name="specifying-the-shortcut-menu"></a>바로 가기 메뉴 지정  
 이 연습에 표시 된 것과 같은 바로 가기 메뉴를 사용 하면 사용자가 도구 창의 배경을 채우는 데 사용 되는 색 목록에서 선택할 수 있습니다.  
  
1. ShortcutMenuPackage에서 guidShortcutMenuPackageCmdSet 라는 GuidSymbol 요소를 찾고 바로 가기 메뉴, 바로 가기 메뉴 그룹 및 메뉴 옵션을 선언 합니다. 이제 GuidSymbol 요소가 다음과 같이 표시 됩니다.  
  
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
  
2. Buttons 요소 바로 앞에 메뉴 요소를 만든 다음 바로 가기 메뉴를 정의 합니다.  
  
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
  
     바로 가기 메뉴는 메뉴 또는 도구 모음의 일부가 아니므로 부모를 포함 하지 않습니다.  
  
3. 바로 가기 메뉴 항목이 포함 된 Group 요소를 사용 하 여 Groups 요소를 만들고 해당 그룹을 바로 가기 메뉴에 연결 합니다.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4. Buttons 요소에서 바로 가기 메뉴에 표시 될 개별 명령을 정의 합니다. Buttons 요소는 다음과 같습니다.  
  
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
  
5. ShortcutMenuPackageGuids.cs에서 명령 집합 GUID, 바로 가기 메뉴 및 메뉴 항목에 대 한 정의를 추가 합니다.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     이러한 파일은 ShortcutMenuPackage 파일의 기호 섹션에 정의 된 것과 동일한 명령 Id입니다. 컨텍스트 그룹은. vsct 파일에만 필요 하기 때문에 여기에 포함 되지 않습니다.  
  
## <a name="implementing-the-shortcut-menu"></a>바로 가기 메뉴 구현  
 이 섹션에서는 바로 가기 메뉴와 해당 명령을 구현 합니다.  
  
1. ShortcutMenu.cs에서는 도구 창에서 메뉴 명령 서비스를 가져올 수 있지만 포함 하는 컨트롤은 사용할 수 없습니다. 다음 단계에서는 사용자 정의 컨트롤에서 메뉴 명령 서비스를 사용 하도록 설정 하는 방법을 보여 줍니다.  
  
2. ShortcutMenu.cs에서 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3. 도구 창의 Initialize () 메서드를 재정의 하 여 메뉴 명령 서비스를 가져오고 컨트롤을 추가 하 여 메뉴 명령 서비스를 생성자에 전달 합니다.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4. ShortcutMenu tool window 생성자에서 컨트롤을 추가 하는 줄을 제거 합니다. 이제 생성자는 다음과 같습니다.  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5. ShortcutMenuControl.xaml.cs에서 메뉴 명령 서비스에 대 한 전용 필드를 추가 하 고 메뉴 명령 서비스를 사용 하도록 컨트롤 생성자를 변경 합니다. 그런 다음 메뉴 명령 서비스를 사용 하 여 상황에 맞는 메뉴 명령을 추가 합니다. ShortcutMenuControl 생성자는 이제 다음 코드와 같습니다. 명령 처리기는 나중에 정의 됩니다.  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6. ShortcutMenuControl에서 <xref:System.Windows.UIElement.MouseRightButtonDown> 최상위 요소에 이벤트를 추가 합니다 <xref:System.Windows.Controls.UserControl> . 이제 XAML 파일이 다음과 같이 표시 됩니다.  
  
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
  
7. ShortcutMenuControl.xaml.cs에서 이벤트 처리기에 대 한 스텁을 추가 합니다.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8. 동일한 파일에 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. `MyToolWindowMouseRightButtonDown`다음과 같이 이벤트를 구현 합니다.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     이렇게 하면 <xref:System.ComponentModel.Design.CommandID> 바로 가기 메뉴에 대 한 개체를 만들고 마우스 클릭 위치를 식별 하 고 메서드를 사용 하 여 해당 위치에서 바로 가기 메뉴를 엽니다 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> .  
  
10. 명령 처리기를 구현 합니다.  
  
    ```csharp  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     이 경우에는를 식별 하 고 배경색을 적절 하 게 설정 하 여 한 가지 방법으로 모든 메뉴 항목에 대 한 이벤트를 처리 <xref:System.ComponentModel.Design.CommandID> 합니다. 메뉴 항목에 관련 없는 명령이 포함 된 경우 각 명령에 대 한 별도의 이벤트 처리기를 만들었습니다.  
  
## <a name="testing-the-tool-window-features"></a>도구 창 기능 테스트  
  
1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다.  
  
2. 실험적 인스턴스에서 **보기/기타 창**을 클릭 한 다음 **ShortcutMenu**를 클릭 합니다. 이렇게 하면 도구 창이 표시 됩니다.  
  
3. 도구 창의 본문을 마우스 오른쪽 단추로 클릭 합니다. 색 목록을 포함 하는 바로 가기 메뉴가 표시 되어야 합니다.  
  
4. 바로 가기 메뉴에서 색을 클릭 합니다. 도구 창의 배경색을 선택한 색으로 변경 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)   
 [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)
