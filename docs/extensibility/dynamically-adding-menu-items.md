---
title: 동적으로 메뉴 항목 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4387c1930e09e49c0ec5c36ccedc1bb83dc273f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712061"
---
# <a name="dynamically-add-menu-items"></a>메뉴 항목 동적으로 추가
Visual Studio 명령 테이블 `DynamicItemStart` *(.vsct)* 파일의 자리 표시자 단추 정의에 명령 플래그를 지정한 다음 명령어를 표시하고 처리할 메뉴 항목 수를 (코드에서) 정의하여 런타임에 메뉴 항목을 추가할 수 있습니다. VSPackage가 로드되면 자리 표시자가 동적 메뉴 항목으로 바뀝습니다.

 Visual Studio는 최근에 열린 문서의 이름을 표시하는 가장 최근에 사용한(MRU) 목록과 현재 열려 있는 창의 이름을 표시하는 **Windows** 목록의 동적 목록을 사용합니다. **Most Recently Used**   명령 `DynamicItemStart` 정의의 플래그는 VSPackage가 열릴 때까지 명령이 자리 표시자임을 지정합니다. VSPackage가 열리면 자리 표시자는 런타임에 생성되고 동적 목록에 추가되는 0개 이상의 명령으로 바뀝습니다. VSPackage를 열 때까지 동적 목록이 표시되는 메뉴의 위치를 볼 수 없습니다.  동적 목록을 채우기 위해 Visual Studio는 VSPackage에 첫 번째 문자가 자리 표시자의 ID와 동일한 ID가 있는 명령을 찾도록 요청합니다. Visual Studio에서 일치하는 명령을 찾으면 동적 목록에 명령 이름을 추가합니다. 그런 다음 ID를 증분하고 더 이상 동적 명령이 없을 때까지 동적 목록에 추가할 다른 일치 명령을 찾습니다.

 이 연습에서는 **솔루션 탐색기** 도구 모음에 명령을 사용하여 Visual Studio 솔루션에서 시작 프로젝트를 설정하는 방법을 보여 주십니다. 활성 솔루션의 프로젝트의 동적 드롭다운 목록이 있는 메뉴 컨트롤러를 사용합니다. 솔루션이 열려 있지 않거나 열려 있는 솔루션에 프로젝트가 하나만 있는 경우 이 명령이 나타나지 않도록 하려면 솔루션에 여러 프로젝트가 있는 경우에만 VSPackage가 로드됩니다.

 *.vsct* 파일에 대한 자세한 내용은 [Visual Studio 명령 테이블(.vsct) 파일을](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)참조하십시오.

## <a name="create-an-extension-with-a-menu-command"></a>메뉴 명령으로 확장 만들기

1. 라는 VSIX 프로젝트를 `DynamicMenuItems`만듭니다.

2. 프로젝트가 열리면 사용자 지정 명령 항목 템플릿을 추가하고 **DynamicMenu**의 이름을 지정합니다. 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

## <a name="setting-up-the-elements-in-the-vsct-file"></a>*.vsct* 파일의 요소 설정
 도구 모음에 동적 메뉴 항목이 있는 메뉴 컨트롤러를 만들려면 다음 요소를 지정합니다.

- 두 명령 그룹( 메뉴 컨트롤러가 포함된 명령 그룹 과 드롭다운에 메뉴 항목 포함)이 포함됩니다.

- 형식의 메뉴 요소 1개`MenuController`

- 두 개의 단추, 하나는 메뉴 항목의 자리 표시자 역할을 하는 단추와 도구 모음에 아이콘과 도구 설명이 제공 되는 단추입니다.

1. *DynamicMenuPackage.vsct에서*명령 암호를 정의합니다. 기호 섹션으로 이동하여 **guidDynamicMenuPackageCmdSet** GuidSymbol 블록의 ID 기호 요소를 대체합니다. 두 그룹, 메뉴 컨트롤러, 자리 표시자 명령 및 앵커 명령에 대한 IDSymbol 요소를 정의해야 합니다.

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. 그룹 섹션에서 기존 그룹을 삭제하고 방금 정의한 두 그룹을 추가합니다.

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     메뉴컨트롤러를 추가합니다. 항상 표시되지는 않으므로 Dynamic가시성 명령 플래그를 설정합니다. ButtonText가 표시되지 않습니다.

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. 두 개의 단추를 추가합니다(하나는 동적 메뉴 항목의 자리 표시자로, 다른 하나는 MenuController의 앵커로)

     자리 표시자 단추의 상위 는 **MyMenuControllerGroup**입니다. 자리 표시자 단추에 DynamicItemStart, 동적 표시 및 TextChange 명령 플래그를 추가합니다. ButtonText가 표시되지 않습니다.

     앵커 버튼에는 아이콘과 도구 설명 텍스트가 있습니다. 앵커 단추의 부모는 **MyMenuControllerGroup입니다.** NoShowOnMenuController 명령 플래그를 추가하여 버튼이 메뉴 컨트롤러 드롭다운에 실제로 나타나지 않도록 하고 FixMenuController 명령 플래그를 추가하여 영구 앵커로 만듭니다.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. *리소스* 폴더에 프로젝트에 아이콘을 추가한 다음 *.vsct* 파일에 참조를 추가합니다. 이 연습에서는 프로젝트 템플릿에 포함된 화살표 아이콘을 사용합니다.

5. 기호 섹션 바로 앞에 명령 섹션 외부에 가시성 제약 조건 섹션을 추가합니다. (기호 후에 추가하면 경고가 나타날 수 있습니다.) 이 섹션에서는 여러 프로젝트가 있는 솔루션이 로드된 경우에만 메뉴 컨트롤러가 표시되는지 확인합니다.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>동적 메뉴 명령 구현
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>에서 상속하는 동적 메뉴 명령 클래스를 만듭니다. 이 구현에서 생성자는 명령 일치에 사용할 조건어를 지정합니다. 호출할 명령을 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> 식별하는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> 속성을 설정하려면 이 조건어를 사용하는 메서드를 재정의해야 합니다.

1. *DynamicItemMenuCommand.cs*라는 새 C# 클래스 파일을 만들고 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>에서 상속 하는 **DynamicItemMenuCommand** 라는 클래스를 추가 합니다.

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. 다음 using 지시문을 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. 개인 필드를 추가하여 일치 조건자 저장:

    ```csharp
    private Predicate<int> matches;

    ```

4. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 생성자에서 상속 하 고 명령 처리기 및 처리기를 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 지정 하는 생성자 추가 합니다. 명령 일치를 위한 술어를 추가합니다.

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. 일치 조건자 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> 호출 하 고 속성을 설정 되도록 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> 메서드를 재정의 합니다.

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>명령 추가
 DynamicMenu 생성자는 동적 메뉴 및 메뉴 항목을 포함하여 메뉴 명령을 설정하는 곳입니다.

1. *DynamicMenuPackage.cs*명령 집합의 GUID와 명령 ID를 추가합니다.

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. *DynamicMenu.cs* 파일에서 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. 클래스에서 `DynamicMenu` 개인 필드 **dte2를**추가합니다.

    ```csharp
    private DTE2 dte2;
    ```

4. 개인 루트ItemId 필드 추가:

    ```csharp
    private int rootItemId = 0;
    ```

5. DynamicMenu 생성자에서 메뉴 명령을 추가합니다. 다음 섹션에서는 명령 처리기, `BeforeQueryStatus` 이벤트 처리기 및 일치 조건자입니다.

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>처리기 구현
 메뉴 컨트롤러에서 동적 메뉴 항목을 구현하려면 동적 항목을 클릭할 때 명령을 처리해야 합니다. 또한 메뉴 항목의 상태를 설정하는 논리를 구현해야 합니다. 클래스에 처리기를 `DynamicMenu` 추가합니다.

1. **시작 프로젝트 설정** 명령을 구현하려면 **OnInvokedDynamicItem** 이벤트 처리기를 추가합니다. 이름이 호출된 명령의 텍스트와 동일한 프로젝트를 찾고 <xref:EnvDTE.SolutionBuild.StartupProjects%2A> 속성에서 절대 경로를 설정하여 시작 프로젝트로 설정합니다.

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. `OnBeforeQueryStatusDynamicItem` 이벤트 처리기를 추가합니다. 이벤트 전에 호출되는 `QueryStatus` 처리기입니다. 메뉴 항목이 "실제" 항목인지, 즉 자리 표시자 항목이 아닌지, 항목이 이미 선택되어 있는지 여부(프로젝트가 시작 프로젝트로 이미 설정되어 있음)를 결정합니다.

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>명령 ID 일치 조건자 구현

이제 일치 조건자 구현합니다. 먼저 명령 ID가 유효한지 여부(선언된 명령 ID보다 크거나 같음)와 가능한 프로젝트를 지정하는지 여부(솔루션의 프로젝트 수보다 적음)를 결정해야 합니다.

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>솔루션에 여러 프로젝트가 있는 경우에만 VSPackage를 로드하도록 설정합니다.
 활성 솔루션에 두 개 이상의 프로젝트가 있는 경우가 아니면 **시작 프로젝트 설정** 명령은 의미가 없으므로 VSPackage를 이 경우에만 자동 로드하도록 설정할 수 있습니다. UI <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 컨텍스트와 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>함께 사용합니다. *DynamicMenuPackage.cs* 파일에서 DynamicMenuPackage 클래스에 다음 특성을 추가합니다.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>설정 시작 프로젝트 명령 테스트
 이제 코드를 테스트할 수 있습니다.

1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타나야 합니다.

2. 실험 인스턴스에서 둘 이상의 프로젝트가 있는 솔루션을 엽니다.

     **솔루션 탐색기** 도구 모음에 화살표 아이콘이 표시됩니다. 확장하면 솔루션의 다른 프로젝트를 나타내는 메뉴 항목이 나타납니다.

3. 프로젝트 중 하나를 선택하면 시작 프로젝트가 됩니다.

4. 솔루션을 닫거나 프로젝트가 하나만 있는 솔루션을 열면 도구 모음 아이콘이 사라집니다.

## <a name="see-also"></a>참조
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
