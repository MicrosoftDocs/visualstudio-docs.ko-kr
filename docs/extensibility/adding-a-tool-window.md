---
title: 도구 창 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 169f386128ccdd79aef6b90a6703f50323b9b6f3
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904141"
---
# <a name="add-a-tool-window"></a>도구 창 추가

이 연습에서는 다음과 같은 방법으로 도구 창을 만들고 Visual Studio에 통합 하는 방법에 대해 알아봅니다.

- 도구 창에 컨트롤을 추가 합니다.

- 도구 창에 도구 모음을 추가 합니다.

- 도구 모음에 명령을 추가 합니다.

- 명령을 구현 합니다.

- 도구 창에 대 한 기본 위치를 설정 합니다.

## <a name="prerequisites"></a>사전 요구 사항

Visual studio SDK는 Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-tool-window"></a>도구 창 만들기

1. VSIX 템플릿을 사용 하 여 **Firsttoolwin** 이라는 프로젝트를 만들고 **FirstToolWindow**이라는 사용자 지정 도구 창 항목 템플릿을 추가 합니다.

    > [!NOTE]
    > 도구 창을 사용 하 여 확장을 만드는 방법에 대 한 자세한 내용은 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요.

## <a name="add-a-control-to-the-tool-window"></a>도구 창에 컨트롤 추가

1. 기본 컨트롤을 제거 합니다. *Firsttoolwindowcontrol* 을 열고 **Click Me** 를 삭제 합니다. 클릭합니다.

2. **도구 상자**에서 **모든 WPF 컨트롤** 섹션을 확장 하 고 **미디어 요소** 컨트롤을 **firsttoolwindowcontrol** 폼으로 끕니다. 컨트롤을 선택 하 고 **속성** 창에서이 요소 이름을 **mediaElement1**로 선택 합니다.

## <a name="add-a-toolbar-to-the-tool-window"></a>도구 창에 도구 모음 추가
다음과 같은 방법으로 도구 모음을 추가 하면 해당 그라데이션과 색이 IDE의 나머지 부분과 일치 하는 것을 보장할 수 있습니다.

1. **솔루션 탐색기**에서 *Firsttoolwindowpackage. vsct*를 엽니다. *. Vsct* 파일은 도구 창에서 XML을 사용 하 여 GUI (그래픽 사용자 인터페이스) 요소를 정의 합니다.

2. 섹션에서 `<Symbols>` `<GuidSymbol>` 특성이 인 노드를 찾습니다 `name` `guidFirstToolWindowPackageCmdSet` . `<IDSymbol>`이 노드의 요소 목록에 다음 두 요소를 추가 `<IDSymbol>` 하 여 도구 모음 및 도구 모음 그룹을 정의 합니다.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. 섹션 바로 위에 `<Buttons>` 다음과 같은 섹션을 만듭니다 `<Menus>` .

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    다양 한 종류의 메뉴가 있습니다. 이 메뉴는 특성으로 정의 된 도구 창의 도구 모음입니다 `type` . `guid`및 `id` 설정은 도구 모음의 정규화 된 ID를 구성 합니다. 일반적으로 `<Parent>` 메뉴의는 포함 하는 그룹입니다. 그러나 도구 모음은 자체 부모로 정의 됩니다. 따라서 및 요소에 동일한 식별자가 사용 됩니다 `<Menu>` `<Parent>` . `priority`특성은 ' 0 ' 뿐입니다.

4. 도구 모음은 여러 가지 측면에서 메뉴와 비슷합니다. 예를 들어 메뉴에 명령 그룹이 있을 수 있는 것 처럼 도구 모음에 그룹이 있을 수도 있습니다. 메뉴에서 명령 그룹은 가로 선으로 구분 됩니다. 도구 모음에서는 그룹이 시각적 분할자로 구분 되지 않습니다.

    `<Groups>`요소가 포함 된 섹션을 추가 `<Group>` 합니다. 이는 섹션에서 선언한 ID의 그룹을 정의 합니다 `<Symbols>` . 섹션을 `<Groups>` 섹션 바로 뒤에 추가 `<Menus>` 합니다.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    부모 GUID 및 ID를 도구 모음의 GUID 및 ID로 설정 하면 그룹을 도구 모음에 추가 합니다.

## <a name="add-a-command-to-the-toolbar"></a>도구 모음에 명령 추가

단추에 표시 되는 도구 모음에 명령을 추가 합니다.

1. 섹션에서 `<Symbols>` 도구 모음 및 도구 모음 그룹 선언 바로 뒤에 다음 IDSymbol 요소를 선언 합니다.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. 섹션 내에 Button 요소를 추가 `<Buttons>` 합니다. 이 요소는 도구 창의 도구 모음에서 **검색** (돋보기) 아이콘을 사용 하 여 표시 됩니다.

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. *FirstToolWindowCommand.cs* 를 열고 클래스에서 기존 필드 바로 뒤에 다음 줄을 추가 합니다.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    이렇게 하면 코드에서 명령을 사용할 수 있습니다.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>FirstToolWindowControl에 MediaPlayer 속성 추가
Toolbar 컨트롤에 대 한 이벤트 처리기에서 코드는 FirstToolWindowControl 클래스의 자식인 Media Player 컨트롤에 액세스할 수 있어야 합니다.

**솔루션 탐색기**에서 *firsttoolwindowcontrol*을 마우스 오른쪽 단추로 클릭 하 고 **코드 보기**를 클릭 한 후 firsttoolwindowcontrol 클래스에 다음 코드를 추가 합니다.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>도구 창 및 도구 모음 인스턴스화
**파일 열기** 대화 상자를 호출 하 고 선택한 미디어 파일을 재생 하는 메뉴 명령과 도구 모음을 추가 합니다.

1. *FirstToolWindow.cs* 를 열고 다음 지시문을 추가 합니다 `using` .

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. FirstToolWindow 클래스 내에서 FirstToolWindowControl 컨트롤에 대 한 공용 참조를 추가 합니다.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. 생성자의 끝에서이 컨트롤 변수를 새로 만든 컨트롤로 설정 합니다.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. 생성자 내에서 도구 모음을 인스턴스화합니다.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. 이 시점에서 FirstToolWindow 생성자는 다음과 같습니다.

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. 메뉴 명령을 도구 모음에 추가 합니다. FirstToolWindowCommand.cs 클래스에서 다음 using 지시문을 추가 합니다.

    ```csharp
    using System.Windows.Forms;
    ```

7. FirstToolWindowCommand 클래스에서 ShowToolWindow () 메서드의 끝에 다음 코드를 추가 합니다. ButtonHandler 명령은 다음 섹션에서 구현 됩니다.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>도구 창에서 메뉴 명령을 구현 하려면

1. FirstToolWindowCommand 클래스에서 **파일 열기** 대화 상자를 호출 하는 buttonhandler 메서드를 추가 합니다. 파일이 선택 된 경우 미디어 파일을 재생 합니다.

2. FirstToolWindowCommand 클래스에서 FindToolWindow () 메서드에서 만든 FirstToolWindow 창에 전용 참조를 추가 합니다.

    ```csharp
    private FirstToolWindow window;
    ```

3. ShowToolWindow () 메서드를 변경 하 여 위에서 정의한 창을 설정 합니다. 그러면 ButtonHandler 명령 처리기가 창 컨트롤에 액세스할 수 있습니다. 전체 ShowToolWindow () 메서드는 다음과 같습니다.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. ButtonHandler 메서드를 추가 합니다. 사용자가 재생할 미디어 파일을 지정 하는 OpenFileDialog를 만든 다음 선택한 파일을 재생 합니다.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>도구 창에 대 한 기본 위치 설정

그런 다음 도구 창에 대 한 IDE에서 기본 위치를 지정 합니다. 도구 창에 대 한 구성 정보는 *FirstToolWindowPackage.cs* 파일에 있습니다.

1. *FirstToolWindowPackage.cs*에서 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> `FirstToolWindowPackage` FirstToolWindow 형식을 생성자에 전달 하는 클래스의 특성을 찾습니다. 기본 위치를 지정 하려면 다음 예제와 같이 생성자에 더 많은 매개 변수를 추가 해야 합니다.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    첫 번째 명명 된 매개 변수는이 `Style` 고 해당 값은입니다 `Tabbed` . 즉, 창이 기존 창에서 탭이 됩니다. 도킹 위치는 매개 변수에서 지정 합니다 `Window` .이 경우에는 **솔루션 탐색기**의 GUID입니다.

    > [!NOTE]
    > IDE의 창 형식에 대 한 자세한 내용은를 참조 하십시오 <xref:EnvDTE.vsWindowType> .

## <a name="test-the-tool-window"></a>도구 창 테스트

1. **F5** 키를 눌러 Visual Studio 실험적 빌드의 새 인스턴스를 엽니다.

2. **보기** 메뉴에서 **다른 창** 을 가리킨 다음 **첫 번째 도구 창**을 클릭 합니다.

    미디어 플레이어 도구 창은 **솔루션 탐색기**와 동일한 위치에 열립니다. 이전과 동일한 위치에 계속 표시 되는 경우 창 레이아웃 (**창/다시 설정 창 레이아웃**)을 다시 설정 합니다.

3. 도구 창에서 단추 ( **검색** 아이콘 포함)를 클릭 합니다. 지원 되는 사운드 또는 비디오 파일 (예: *C:\windows\media\chimes.wav*)을 선택 하 고 **열기**를 누릅니다.

    Chime 소리가 들려야 합니다.

## <a name="see-also"></a>참조
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
