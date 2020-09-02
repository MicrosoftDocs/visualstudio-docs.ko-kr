---
title: 동적으로 메뉴 항목 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45d435a9c77d63fbd1e92a7615df232c2a0cc117
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555519"
---
# <a name="dynamically-adding-menu-items"></a>메뉴 항목 동적 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`DynamicItemStart`Visual Studio 명령 테이블 (.vvsct) 파일의 자리 표시자 단추 정의에 명령 플래그를 지정 하 여 런타임에 메뉴 항목을 추가 하 고, 명령을 표시 하 고 처리할 메뉴 항목의 수를 정의할 수 있습니다. VSPackage가 로드 되 면 자리 표시 자가 동적 메뉴 항목으로 바뀝니다.  
  
 Visual Studio는 **가장 최근에 사용한** (MRU) 목록의 동적 목록을 사용 합니다 .이 목록에는 최근에 열었던 문서 이름이 표시 되 고 **windows** 목록에는 현재 열려 있는 창의 이름이 표시 됩니다.   `DynamicItemStart`명령 정의의 플래그는 VSPackage가 열릴 때까지 명령이 자리 표시자 임을 지정 합니다. VSPackage를 열면 자리 표시 자가 런타임에 생성 되어 동적 목록에 추가 되는 0 개 이상의 명령으로 바뀝니다. VSPackage가 열릴 때까지 동적 목록이 표시 되는 메뉴의 위치를 볼 수 없습니다.  동적 목록을 채우기 위해 Visual Studio는 VSPackage에서 첫 번째 문자가 자리 표시자의 ID와 동일한 ID를 사용 하 여 명령을 찾도록 요청 합니다. Visual Studio는 일치 하는 명령을 찾으면 동적 목록에 명령 이름을 추가 합니다. 그런 다음 동적 명령이 더 이상 없을 때까지 ID를 증가 시키고 동적 목록에 추가할 다른 일치 하는 명령을 찾습니다.  
  
 이 연습에서는 **솔루션 탐색기** 도구 모음에서 명령을 사용 하 여 Visual Studio 솔루션에서 시작 프로젝트를 설정 하는 방법을 보여 줍니다. 활성 솔루션에 있는 프로젝트의 동적 드롭다운 목록이 있는 메뉴 컨트롤러를 사용 합니다. 솔루션이 열려 있지 않거나 열려 있는 솔루션에 프로젝트가 하나만 있는 경우이 명령이 표시 되지 않도록 하려면 솔루션에 여러 프로젝트가 있는 경우에만 VSPackage이 로드 됩니다.  
  
 . Vsct 파일에 대 한 자세한 내용은 [Visual Studio 명령 테이블 (를 참조 하세요. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>메뉴 명령을 사용하여 확장 만들기  
  
1. 이라는 VSIX 프로젝트를 만듭니다 `DynamicMenuItems` .  
  
2. 프로젝트가 열리면 사용자 지정 명령 항목 템플릿을 추가 하 고 **Dynamicmenu**로 이름을 지정 합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>Vsct 파일의 요소 설정  
 도구 모음에서 동적 메뉴 항목을 사용 하 여 메뉴 컨트롤러를 만들려면 다음 요소를 지정 합니다.  
  
- 메뉴 컨트롤러를 포함 하는 명령 그룹과 드롭다운에서 메뉴 항목이 포함 된 명령 그룹 두 개  
  
- 형식의 한 메뉴 요소 `MenuController`  
  
- 메뉴 항목에 대 한 자리 표시자 역할을 하는 단추 및 도구 모음에 아이콘 및 도구 설명을 제공 하는 단추 두 개.  
  
1. DynamicMenuPackage에서 명령 Id를 정의 합니다. 기호 섹션으로 이동 하 여 **guidDynamicMenuPackageCmdSet** GuidSymbol 블록에서 idsymbol 요소를 바꿉니다. 두 그룹, 메뉴 컨트롤러, 자리 표시자 명령 및 앵커 명령에 대 한 IDSymbol 요소를 정의 해야 합니다.  
  
    ```csharp  
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
  
2. 그룹 섹션에서 기존 그룹을 삭제 하 고 방금 정의한 두 그룹을 추가 합니다.  
  
    ```  
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
  
     MenuController를 추가 합니다. DynamicVisibility 명령 플래그는 항상 표시 되지 않으므로 설정 합니다. ButtonText는 표시 되지 않습니다.  
  
    ```  
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
  
3. 하나는 동적 메뉴 항목에 대 한 자리 표시자로, 다른 하나는 MenuController의 앵커로 추가 합니다.  
  
     자리 표시자 단추의 부모는 **Mymenucontrollergroup**입니다. DynamicItemStart, DynamicVisibility 및 TextChanges 명령 플래그를 자리 표시자 단추에 추가 합니다. ButtonText는 표시 되지 않습니다.  
  
     앵커 단추는 아이콘과 도구 설명 텍스트를 포함 합니다. 앵커 단추의 부모는 **Mymenucontrollergroup**이기도 합니다. NoShowOnMenuController 명령 플래그를 추가 하 여 단추가 실제로 메뉴 컨트롤러 드롭다운에 표시 되지 않는지 확인 하 고 FixMenuController 명령 플래그를 사용 하 여 영구 앵커로 만듭니다.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
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
  
4. 프로젝트 (Resources 폴더)에 아이콘을 추가 하 고이 파일에 대 한 참조를 vsct 파일에 추가 합니다. 이 연습에서는 프로젝트 템플릿에 포함 된 화살표 아이콘을 사용 합니다.  
  
5. VisibilityConstraints 섹션을 기호 섹션 바로 앞에 있는 명령 섹션의 외부에 추가 합니다. 기호 뒤에 추가 하면 경고가 표시 될 수 있습니다. 이 섹션에서는 여러 프로젝트가 포함 된 솔루션이 로드 될 때만 메뉴 컨트롤러가 표시 되도록 합니다.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>동적 메뉴 명령 구현  
 에서 상속 되는 동적 메뉴 명령 클래스를 만듭니다 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> . 이 구현에서 생성자는 일치 하는 명령에 사용할 조건자를 지정 합니다. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>이 조건자를 사용 하 여 호출할 명령을 식별 하는 속성을 설정 하려면 메서드를 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> .  
  
1. DynamicItemMenuCommand.cs 라는 새 c # 클래스 파일을 만들고에서 상속 되는 **Dynamicitemmenucommand** 라는 클래스를 추가 합니다 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2. 다음 using 명령문을 추가합니다.  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3. 일치 조건자를 저장할 전용 필드를 추가 합니다.  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4. 생성자에서 상속 되 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 고 명령 처리기와 처리기를 지정 하는 생성자를 추가 합니다 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> . 명령과 일치 하는 조건자를 추가 합니다.  
  
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
  
5. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>일치 조건자를 호출 하 고 속성을 설정 하도록 메서드를 재정의 합니다 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> .  
  
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
  
## <a name="adding-the-command"></a>명령 추가  
 DynamicMenu 생성자는 동적 메뉴 및 메뉴 항목을 포함 하 여 메뉴 명령을 설정 하는 위치입니다.  
  
1. DynamicMenuPackageGuids.cs에서 명령 집합의 GUID와 명령 ID를 추가 합니다.  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2. DynamicMenu.cs 파일에서 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3. DynamicMenu 클래스에서 private 필드 **dte2**를 추가 합니다.  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4. Private rootItemId 필드를 추가 합니다.  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5. DynamicMenu 생성자에서 메뉴 명령을 추가 합니다. 다음 섹션에서는 명령 처리기, `BeforeQueryStatus` 이벤트 처리기 및 일치 조건자를 정의 합니다.  
  
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
  
## <a name="implementing-the-handlers"></a>처리기 구현  
 메뉴 컨트롤러에서 동적 메뉴 항목을 구현 하려면 동적 항목을 클릭할 때 명령을 처리 해야 합니다. 또한 메뉴 항목의 상태를 설정 하는 논리를 구현 해야 합니다. DynamicMenu 클래스에 처리기를 추가 합니다.  
  
1. **시작 프로젝트 설정** 명령을 구현 하려면 **OnInvokedDynamicItem** 이벤트 처리기를 추가 합니다. 호출 된 명령의 텍스트와 이름이 동일한 프로젝트를 찾은 다음 속성의 절대 경로를 설정 하 여 시작 프로젝트로 설정 합니다 <xref:EnvDTE.SolutionBuild.StartupProjects%2A> .  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
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
  
2. `OnBeforeQueryStatusDynamicItem`이벤트 처리기를 추가 합니다. 이 처리기는 이벤트 이전에 호출 됩니다 `QueryStatus` . 메뉴 항목이 "실제" 항목 인지 여부, 즉 자리 표시자 항목이 아니라 항목이 이미 선택 되었는지 여부를 확인 합니다. 즉, 프로젝트가 이미 시작 프로젝트로 설정 되어 있는지 여부를 확인 합니다.  
  
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
  
## <a name="implementing-the-command-id-match-predicate"></a>명령 ID 일치 조건자 구현  
  
1. 이제 match 조건자를 구현 합니다. 다음 두 가지 사항을 확인 해야 합니다. 첫 번째는 명령 ID가 유효한 지 여부 (선언 된 명령 ID 보다 크거나 같음)이 고 두 번째는 가능한 프로젝트를 지정 하는지 여부 (솔루션의 프로젝트 수보다 작음)입니다.  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>솔루션에 여러 프로젝트가 있는 경우에만 로드 되도록 VSPackage 설정  
 활성 솔루션에 프로젝트가 두 개 이상 포함 되어 있지 않으면 **시작 프로젝트 설정** 명령이 적합 하지 않기 때문에 VSPackage이 해당 경우에만 자동 로드 되도록 설정할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>UI 컨텍스트와 함께를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects> 합니다. DynamicMenuPackage.cs 파일에서 DynamicMenuPackage 클래스에 다음 특성을 추가 합니다.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>시작 프로젝트 설정 명령 테스트  
 이제 코드를 테스트할 수 있습니다.  
  
1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다.  
  
2. 실험적 인스턴스에서 둘 이상의 프로젝트를 포함 하는 솔루션을 엽니다.  
  
     **솔루션 탐색기** 도구 모음에 화살표 아이콘이 표시 됩니다. 확장 하는 경우 솔루션의 다른 프로젝트를 나타내는 메뉴 항목이 표시 됩니다.  
  
3. 프로젝트 중 하나를 선택 하면 시작 프로젝트가 됩니다.  
  
4. 솔루션을 닫거나 프로젝트가 하나만 있는 솔루션을 여는 경우 도구 모음 아이콘이 사라집니다.  
  
## <a name="see-also"></a>관련 항목  
 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
