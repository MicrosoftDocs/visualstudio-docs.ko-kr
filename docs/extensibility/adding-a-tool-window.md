---
title: 도구 창 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740258"
---
# <a name="add-a-tool-window"></a>도구 창 추가

이 연습에서는 도구 창을 만들고 다음과 같은 방법으로 Visual Studio에 통합하는 방법을 배웁니다.

- 도구 창에 컨트롤을 추가합니다.

- 도구 창에 도구 모음을 추가합니다.

- 도구 모음에 명령을 추가합니다.

- 명령을 구현합니다.

- 도구 창의 기본 위치를 설정합니다.

## <a name="prerequisites"></a>사전 요구 사항

비주얼 스튜디오 SDK는 비주얼 스튜디오 설정에서 선택적 기능으로 포함되어 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-tool-window"></a>도구 창 만들기

1. VSIX 템플릿을 사용하여 **FirstToolWin이라는** 프로젝트를 만들고 **FirstToolWindow라는**사용자 지정 도구 창 항목 템플릿을 추가합니다.

    > [!NOTE]
    > 도구 창을 사용하여 확장을 만드는 자세한 내용은 [도구 창을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오.

## <a name="add-a-control-to-the-tool-window"></a>도구 창에 컨트롤 추가

1. 기본 컨트롤을 제거합니다. *퍼스트툴윈도우컨트롤.xaml을* 열고 **나를 클릭합니다!** 단추를 선택합니다.

2. 도구 **상자에서**모든 **WPF 컨트롤** 섹션을 확장하고 **미디어 요소** 컨트롤을 **FirstToolWindowControl** 양식으로 드래그합니다. 컨트롤을 선택하고 **속성** 창에서 이 요소 **mediaElement1의**이름을 지정합니다.

## <a name="add-a-toolbar-to-the-tool-window"></a>도구 창에 도구 모음 추가
다음과 같은 방법으로 도구 모음을 추가하면 그라데이션과 색상이 나머지 IDE와 일치하게 됩니다.

1. **솔루션 탐색기에서** *FirstToolWindowPackage.vsct*를 엽니다. *.vsct* 파일은 XML을 사용하여 도구 창의 그래픽 사용자 인터페이스(GUI) 요소를 정의합니다.

2. 섹션에서 `<Symbols>` `<GuidSymbol>` `name` 특성이 있는 노드를 `guidFirstToolWindowPackageCmdSet`찾습니다. 이 노드의 `<IDSymbol>` `<IDSymbol>` 요소 목록에 다음 두 요소를 추가하여 도구 모음 및 도구 모음 그룹을 정의합니다.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. 단면 `<Buttons>` 바로 위에 `<Menus>` 다음과 유사한 섹션을 만듭니다.

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

    메뉴에는 여러 종류가 있습니다. 이 메뉴는 도구 창의 도구 모음으로, 해당 `type` 특성에 의해 정의됩니다. 및 `guid` `id` 설정은 도구 모음의 정규화된 ID를 구성합니다. 일반적으로 `<Parent>` 메뉴의 포함 그룹입니다. 그러나 도구 모음은 자체 부모로 정의됩니다. 따라서 `<Menu>` 동일한 식별자가 및 `<Parent>` 요소에 사용됩니다. 속성은 `priority` '0'입니다.

4. 도구 모음은 여러 가지 방법으로 메뉴와 유사합니다. 예를 들어 메뉴에 명령 그룹이 있을 수 있는 것처럼 도구 모음에는 그룹이 있을 수도 있습니다. (메뉴에서 명령 그룹은 가로 선으로 구분됩니다. 도구 모음에서 그룹은 시각적 분할로 구분되지 않습니다.

    요소가 `<Groups>` 포함된 섹션을 `<Group>` 추가합니다. 이 섹션에서 선언한 ID를 정의하는 그룹을 정의합니다. `<Symbols>` 단면 `<Groups>` 바로 다음의 섹션을 추가합니다. `<Menus>`

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    부모 GUID 및 ID를 도구 모음의 GUID 및 ID로 설정하면 도구 모음에 그룹을 추가합니다.

## <a name="add-a-command-to-the-toolbar"></a>도구 모음에 명령 추가

단추로 표시되는 도구 모음에 명령을 추가합니다.

1. 섹션에서 `<Symbols>` 도구 모음 및 도구 모음 그룹 선언 바로 직후에 다음 IDSymbol 요소를 선언합니다.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. 단면 내에 단추 `<Buttons>` 요소를 추가합니다. 이 요소는 **도구** 창의 도구 모음에 검색(돋보기) 아이콘이 표시됩니다.

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

3. *FirstToolWindowCommand.cs* 열고 기존 필드 바로 다음에 클래스에 다음 줄을 추가합니다.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    이렇게 하면 코드에서 명령을 사용할 수 있습니다.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>첫 번째 도구 창 컨트롤에 미디어 플레이어 속성을 추가
도구 모음 컨트롤에 대한 이벤트 처리기에서 코드는 FirstToolWindowControl 클래스의 자식인 Media Player 컨트롤에 액세스할 수 있어야 합니다.

**솔루션 탐색기에서** *FirstToolWindowControl.xaml을*마우스 오른쪽 단추로 클릭하고 **코드 보기를**클릭하고 다음 코드를 FirstToolWindowControl 클래스에 추가합니다.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>공구 창 및 도구 모음 인스턴스화
**파일 열기** 대화 상자를 호출하고 선택한 미디어 파일을 재생하는 도구 모음 및 메뉴 명령을 추가합니다.

1. *FirstToolWindow.cs* 열고 다음 `using` 지시문을 추가합니다.

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. FirstToolWindow 클래스 내에서 FirstToolWindowControl 컨트롤에 공용 참조를 추가합니다.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. 생성자의 끝에서 이 컨트롤 변수를 새로 만든 컨트롤에 설정합니다.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. 생성자 내부에 도구 모음을 인스턴스화합니다.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. 이 시점에서 FirstToolWindow 생성자는 다음과 같아야 합니다.

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

6. 도구 모음에 메뉴 명령을 추가합니다. FirstToolWindowCommand.cs 클래스에서 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using System.Windows.Forms;
    ```

7. FirstToolWindowCommand 클래스에서 ShowToolWindow() 메서드의 끝에 다음 코드를 추가합니다. ButtonHandler 명령은 다음 섹션에서 구현됩니다.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>도구 창에서 메뉴 명령을 구현하려면

1. FirstToolWindowCommand 클래스에서 파일 열기 대화 상자를 호출하는 ButtonHandler 메서드를 **추가합니다.** 파일을 선택하면 미디어 파일이 재생됩니다.

2. FirstToolWindowCommand 클래스에서 FindToolWindow() 메서드에서 만들어지는 FirstToolWindow 창에 개인 참조를 추가합니다.

    ```csharp
    private FirstToolWindow window;
    ```

3. ShowToolWindow() 메서드를 변경하여 위에서 정의한 창을 설정하여 ButtonHandler 명령 핸들러가 창 컨트롤에 액세스할 수 있도록 합니다. 다음은 전체 ShowToolWindow() 메서드입니다.

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

4. ButtonHandler 메서드를 추가합니다. 사용자가 재생할 미디어 파일을 지정할 수 있는 OpenFile Dialog를 만들고 선택한 파일을 재생합니다.

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

## <a name="set-the-default-position-for-the-tool-window"></a>공구 창의 기본 위치 설정

다음으로 도구 창에 대한 IDE에서 기본 위치를 지정합니다. 도구 창의 구성 정보는 *FirstToolWindowPackage.cs* 파일에 있습니다.

1. *FirstToolWindowPackage.cs*FirstToolWindow <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 형식을 `FirstToolWindowPackage` 생성자에게 전달하는 클래스의 특성을 찾습니다. 기본 위치를 지정하려면 다음 예제에 생성자에 더 많은 매개 변수를 추가해야 합니다.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    첫 번째 명명된 매개 `Tabbed`변수는 해당 값이며, `Style` 이는 창이 기존 창의 탭이 됨을 의미합니다. 도킹 위치는 `Window` 매개 변수, n 이 경우 솔루션 **탐색기의**GUID에 의해 지정됩니다.

    > [!NOTE]
    > IDE의 창 유형에 대한 자세한 내용은 <xref:EnvDTE.vsWindowType>을 참조하십시오.

## <a name="test-the-tool-window"></a>공구 창 테스트

1. **F5를** 눌러 Visual Studio 실험 빌드의 새 인스턴스를 엽니다.

2. **보기** 메뉴에서 다른 **창을** 가리킨 다음 **첫 번째 도구 창을**클릭합니다.

    미디어 플레이어 도구 창은 **솔루션 탐색기**와 동일한 위치에서 열립니다. 여전히 이전과 같은 위치에 나타나는 경우 창 레이아웃 **(창 / 창 레이아웃 재설정)을**재설정합니다.

3. 도구 창에서 **단추(검색** 아이콘이 있음)를 클릭합니다. 지원되는 사운드 또는 비디오 파일(예: *C:\windows\media\chimes.wav)을*선택한 다음 **열기를**누릅니다.

    차임벨소리가 들려야 합니다.

## <a name="see-also"></a>참조
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
