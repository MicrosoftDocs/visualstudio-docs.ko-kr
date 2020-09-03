---
title: MenuCommands 및 OleMenuCommands | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
manager: jillfra
ms.openlocfilehash: 42c471ca924bfded62db32a956a26c07240459eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67624449"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands와 OleMenuCommands 비교
메뉴 명령은에서 파생 하거나 개체에서 파생 하 <xref:System.ComponentModel.Design.MenuCommand> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 고 적절 한 이벤트 처리기를 구현 하 여 만들 수 있습니다. 대부분의 경우 <xref:System.ComponentModel.Design.MenuCommand>를 VSPackage 프로젝트 템플릿으로 사용할 수 있지만 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>를 사용해야 할 때가 있습니다.  
  
 사용자가 VSPackage를 사용하려면 IDE에서 VSPackage를 사용할 수 있는 명령이 표시되어야 하고 사용하도록 설정되어야 합니다. Visual Studio Package 프로젝트 템플릿을 사용하여 .vsct 파일에서 명령이 만들어지면 기본적으로 표시되고 사용하도록 설정됩니다. `DynamicItemStart`등의 일부 명령 플래그를 설정하면 기본 동작을 변경할 수 있습니다. 표시 여부, 사용 설정 상태 및 명령의 기타 속성은 명령과 관련된 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 개체에 액세스하여 런타임 시 코드에서 변경할 수도 있습니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Visual Studio 패키지 템플릿의 템플릿 위치  
 **새 프로젝트** 대화 상자의 **Visual Basic/확장성**, **C#/확장성**또는 **기타 프로젝트 형식/확장성**에서 Visual Studio 패키지 템플릿을 찾을 수 있습니다.  
  
## <a name="creating-a-command"></a>명령 만들기  
 모든 명령, 명령 그룹, 메뉴, 도구 모음 및 도구 창은 .vsct 파일에서 정의됩니다. 자세한 내용은 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)을 참조하세요.  
  
 패키지 템플릿을 사용하여 VSPackage를 만드는 경우 **메뉴 명령** 을 선택하여 .vsct 파일을 만들고 기본 메뉴 명령을 정의합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.  
  
#### <a name="to-add-a-command-to-the-ide"></a>IDE에 명령을 추가하려면  
  
1. .vsct 파일을 엽니다.  
  
2. `Symbols` 섹션에서 그룹 및 명령이 포함된 [GuidSymbol](../extensibility/guidsymbol-element.md) 요소를 찾습니다.  
  
3. 다음 예제와 같이 추가하려는 각 메뉴, 그룹 또는 명령에 대한 [IDSymbol](../extensibility/idsymbol-element.md) 요소를 만듭니다.  
  
   ```xml
   <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
     <IDSymbol name="MyMenuGroup" value="0x1020" />
     <IDSymbol name="cmdidMyCommand" value="0x0100" />
   </GuidSymbol>
   ```
      
    `name` 및 `GuidSymbol` 요소의 `IDSymbol` 특성은 각 새 메뉴, 그룹 또는 명령에 대한 GUID:ID 쌍을 제공합니다. `guid` 는 VSPackage에 대해 정의된 명령 집합을 나타냅니다. 여러 명령 집합을 정의할 수 있습니다. 각 GUID:ID 쌍은 고유해야 합니다.  
  
4. 다음 예제에서처럼 [Buttons](../extensibility/buttons-element.md) 섹션에 [Button](../extensibility/button-element.md) 요소를 만들어 명령을 정의합니다.  
  
   ```xml
   <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
     <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
       <CommandName>cmdidMyCommand</CommandName>
       <ButtonText>My Command name</ButtonText>
     </Strings>
   </Button>
   ``` 
     
   1. `guid` 및 `id` 필드를 새 명령의 GUID:ID와 일치하도록 설정합니다.  
  
   2. `priority` 특성을 설정합니다.  
  
        `priority` 특성은 .vsct에서 해당 부모 그룹의 다른 개체 간에 단추 위치를 결정하는 데 사용됩니다.  
  
        우선 순위 값이 낮은 명령은 우선 순위 값이 높은 명령의 위 또는 왼쪽에 표시됩니다. 중복 우선 순위 값이 허용되지만 우선 순위가 같은 명령의 상대적 위치는 런타임 시 VSPackage가 처리되는 순서에 의해 결정되므로 순서를 미리 결정할 수 없습니다.  
  
        `priority` 특성을 생략하면 값이 0으로 설정됩니다.  
  
   3. `type` 특성을 설정합니다. 대부분의 경우 값은 `"Button"`으로 설정됩니다. 다른 유효한 단추 형식에 대한 설명은 [Button Element](../extensibility/button-element.md)를 참조하세요.  
  
5. 단추 정의에서 [ButtonText](../extensibility/strings-element.md) 요소가 포함된 [Strings](../extensibility/buttontext-element.md) 요소를 만들어 IDE에 나타나는 메뉴 이름을 포함하고, [CommandName](../extensibility/commandname-element.md) 요소를 만들어 **명령** 창에서 메뉴에 액세스하는 데 사용되는 명령 이름을 포함합니다.  
  
    단추 텍스트 문자열에 '&' 문자가 포함된 경우 Alt 키와 '&' 바로 뒤의 문자를 눌러 메뉴를 열 수 있습니다.  
  
    `Tooltip` 요소를 추가하면 사용자가 해당 단추를 포인터로 가리킬 때 포함된 텍스트가 표시됩니다.  
  
6. 명령으로 아이콘(있는 경우)을 표시하려면 [Icon](../extensibility/icon-element.md) 요소를 추가하여 해당 아이콘을 지정합니다. 아이콘은 도구 모음의 단추에는 필요하지만 메뉴 항목에는 필요하지 않습니다. `guid` 요소의 `id` 및 `Icon` 는 [섹션에 정의된](../extensibility/bitmap-element.md) Bitmap `Bitmaps` 요소와 일치해야 합니다.  
  
7. 명령 플래그를 적절하게 추가하여 단추의 모양 및 동작을 변경합니다. 이 작업을 수행하려면 메뉴 정의에 [CommandFlag](../extensibility/command-flag-element.md) 요소를 추가합니다.  
  
8. 명령의 부모 그룹을 설정합니다. 부모 그룹은 직접 만든 그룹, 다른 패키지의 그룹 또는 IDE의 그룹이 될 수 있습니다. 예를 들어 Visual Studio 편집 도구 모음의 **주석** 및 **주석 제거** 단추 옆에 명령을 추가하려면 부모를 guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT로 설정합니다. 부모가 사용자 정의 그룹인 경우 IDE에 나타나는 메뉴, 도구 모음 또는 도구 창의 자식이어야 합니다.  
  
    디자인에 따라 두 가지 방법 중 하나로 이 작업을 수행할 수 있습니다.  
  
   - `Button` 요소에서 [Parent](../extensibility/parent-element.md) 요소를 만들고 해당 `guid` 및 `id` 필드를 명령을 호스트할 그룹( *기본 부모 그룹*)의 GUID 및 ID로 설정합니다.  
  
        다음 예제에서는 사용자 정의 메뉴에 표시될 명령을 정의합니다.  
  
       ```xml
       <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
         <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
         <Icon guid="guidImages" id="bmpPic1" />
         <Strings>
           <CommandName>cmdidTestCommand</CommandName>
           <ButtonText>Test Command</ButtonText>
             </Strings>
       </Button>
       ```
      
   - 명령 배치를 사용하여 명령을 배치할 경우 `Parent` 요소를 생략할 수 있습니다. 다음 예제와 같이 [섹션 전에](../extensibility/commandplacements-element.md) CommandPlacements `Symbols` 요소를 만들고 명령의 [및](../extensibility/commandplacement-element.md) , `guid` 및 부모를 포함하는 `id` CommandPlacement `priority`요소를 추가합니다.  
  
   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
       <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     </CommandPlacement>
   </CommandPlacements>
   ```
      
      GUID:ID가 동일하고 부모가 서로 다른 명령 배치를 여러 개 만들면 메뉴가 여러 위치에 나타납니다. 자세한 내용은 [CommandPlacements](../extensibility/commandplacements-element.md) 요소를 참조하세요.  
  
    명령 그룹 및 부모에 대 한 자세한 내용은 [다시 사용할 수 있는 단추 그룹 만들기](../extensibility/creating-reusable-groups-of-buttons.md)를 참조 하세요.  
  
   이 시점에서는 명령이 IDE에 표시되지만 작동하지는 않습니다. 명령이 패키지 템플릿에 의해 만들어진 경우 기본적으로 클릭 처리기에 메시지가 표시됩니다.  
  
## <a name="handling-the-new-command"></a>새 명령 처리  
 관리 코드의 명령은 대부분 <xref:System.ComponentModel.Design.MenuCommand> 개체 또는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 개체와 명령을 연결하고 해당 이벤트 처리기를 구현하여 MPF(관리되는 패키지 프레임워크)를 통해 처리할 수 있습니다.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 사용하여 직접 명령을 처리하는 코드의 경우 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스 및 해당 메서드를 구현해야 합니다. 두 개의 가장 중요한 메서드는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 및 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>입니다.  
  
1. 다음 예제와 같이 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 인스턴스를 가져옵니다.  
  
     [!code-csharp[ButtonGroup#21](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#21)]  
  
2. 다음 예제와 같이 처리할 명령의 GUID 및 ID를 해당 매개 변수로 사용하는 <xref:System.ComponentModel.Design.CommandID> 개체를 만듭니다.  
  
     [!code-csharp[ButtonGroup#22](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#22)]  
  
     Visual Studio 패키지 템플릿은 명령의 GUID 및 ID를 저장하는 `GuidList` 및 `PkgCmdIDList`컬렉션을 제공합니다. 이러한 컬렉션은 템플릿을 통해 추가된 명령에 자동으로 채워지지만 수동으로 추가한 명령의 경우 ID 항목을 `PkgCmdIdList` 클래스에 추가해야 합니다.  
  
     또는 GUID의 원시 문자열 값 및 ID의 정수 값을 사용하여 <xref:System.ComponentModel.Design.CommandID> 개체를 채울 수 있습니다.  
  
3. 다음 예제에서처럼 <xref:System.ComponentModel.Design.MenuCommand> 또는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 개체를 인스턴스화합니다. 이 개체들은 <xref:System.ComponentModel.Design.CommandID>와 함께 명령을 처리하는 메서드를 지정합니다.  
  
     [!code-csharp[ButtonGroup#23](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#23)]  
  
     <xref:System.ComponentModel.Design.MenuCommand> 는 정적 명령에 적합합니다. 동적 메뉴 항목 표시에는 QueryStatus 이벤트 처리기가 필요합니다. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 는 명령의 호스트 메뉴가 열릴 때 발생하는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 이벤트와 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>등의 다른 일부 속성을 추가합니다.  
  
     패키지 템플릿으로 만든 명령은 기본적으로 패키지 클래스에 있는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 메서드의 `Initialize()` 개체에 전달됩니다.  
  
4. <xref:System.ComponentModel.Design.MenuCommand> 는 정적 명령에 적합합니다. 동적 메뉴 항목 표시에는 QueryStatus 이벤트 처리기가 필요합니다. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 는 명령의 호스트 메뉴가 열릴 때 발생하는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 이벤트와 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>등의 다른 일부 속성을 추가합니다.  
  
     패키지 템플릿으로 만든 명령은 기본적으로 패키지 클래스에 있는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 메서드의 `Initialize()` 개체에 전달됩니다. Visual Studio 마법사는 `Initialize` 를 사용하여 `MenuCommand`메서드를 구현합니다. 동적 메뉴 항목 표시의 경우 다음 단계와 같이 `OleMenuCommand`로 변경해야 합니다. 또한 메뉴 항목의 텍스트를 변경하려면 다음 예제와 같이 .vsct 파일의 메뉴 명령 단추에 TextChanges 명령 플래그를 추가해야 합니다.  
  
    ```xml
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
      
5. 새 메뉴 명령을 <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> 인터페이스의 <xref:System.ComponentModel.Design.IMenuCommandService> 메서드에 전달합니다. 이 작업은 다음 예제와 같이 패키지 템플릿으로 만든 명령에 대해 기본적으로 수행됩니다.  
  
     [!code-csharp[ButtonGroup#24](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#24)]  
  
6. 명령을 처리하는 메서드를 구현합니다.  
  
#### <a name="to-implement-querystatus"></a>QueryStatus를 구현하려면  
  
1. QueryStatus 이벤트는 명령이 표시되기 전에 발생합니다. 이렇게 하면 사용자에게 전달되기 전에 이벤트 처리기에서 해당 명령의 속성을 설정할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 개체로 추가된 명령만 이 메서드에 액세스할 수 있습니다.  
  
    다음 예제와 같이 명령 처리를 위해 만든 `EventHandler` 개체의 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 이벤트에 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 개체를 추가합니다(`menuItem` 은 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 인스턴스임).  
  
    [!code-csharp[MenuText#14](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#14)]
    [!code-vb[MenuText#14](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#14)]  
  
    `EventHandler` 개체에 메뉴 명령의 상태를 쿼리할 때 호출되는 메서드의 이름을 지정합니다.  
  
2. 명령에 대한 쿼리 상태 처리기 메서드를 구현합니다. `object` `sender` 매개 변수를 개체로 캐스팅할 수 있으며 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ,이는 텍스트를 포함 하 여 메뉴 명령의 다양 한 특성을 설정 하는 데 사용 됩니다. 다음 표에서는 <xref:System.ComponentModel.Design.MenuCommand> 플래그에 해당하는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 클래스(MPF 클래스 <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 가 파생됨)의 속성을 보여 줍니다.  
  
   |MenuCommand 속성|OLECMDF 플래그|  
   |--------------------------|------------------|  
   |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
    메뉴 명령의 텍스트를 변경하려면 다음 예제와 같이 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> 개체에 대해 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 속성을 사용합니다.  
  
    [!code-csharp[MenuText#11](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#11)]
    [!code-vb[MenuText#11](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#11)]  
  
   MPF는 지원되지 않거나 알 수 없는 그룹의 사례를 자동으로 처리합니다. <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 메서드를 사용하여 <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> 에 추가하지 않는 한 명령은 지원되지 않습니다.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>IOleCommandTarget 인터페이스를 사용하여 명령 처리  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 직접 사용하는 코드의 경우 VSPackage는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 인터페이스의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 및 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 의 메서드를 모두 구현해야 합니다. VSPackage가 프로젝트 계층 구조를 구현하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 인터페이스의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 메서드를 대신 구현해야 합니다.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 및 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드는 모두 단일 명령 집합 `GUID` 및 명령 ID의 배열을 입력으로 사용하도록 디자인되었습니다. Vspackage에서 한 번의 호출로 여러 ID를 제공하는 이 개념을 완벽하게 지원하는 것이 좋습니다. 그러나 다른 VSPackage에서 Vspackage를 호출하지 않으면 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 및 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드가 잘 정의된 순서대로 실행되므로 명령 배열에 하나의 명령 ID만 포함된 것으로 간주할 수 있습니다. 라우팅에 대 한 자세한 내용은 [vspackage의 명령 라우팅](../extensibility/internals/command-routing-in-vspackages.md)을 참조 하세요.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 사용하여 직접 명령을 처리하는 코드의 경우 VSPackage에서 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드를 구현하여 다음과 같이 명령을 처리해야 합니다.  
  
##### <a name="to-implement-the-querystatus-method"></a>QueryStatus 메서드를 구현하려면  
  
1. 유효한 명령에 대해 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 를 반환합니다.  
  
2. `cmdf` 매개 변수의 `prgCmds` 요소를 설정합니다.  
  
    `cmdf` 요소의 값은 논리적 OR( <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> ) 연산자를 사용하여 결합한`|`열거형 값의 논리적 공용 구조체입니다.  
  
    명령 상태를 기반으로 적절한 열거형을 사용합니다.  
  
   - 명령이 지원되는 경우:  
  
      `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
   - 현재 명령이 표시되지 않아야 하는 경우:  
  
      `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
   - 명령이 설정되어 클릭한 것처럼 나타나는 경우:  
  
      `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
      `MenuControllerLatched`형식의 메뉴에서 호스트되는 처리 명령의 경우 `OLECMDF_LATCHED` 플래그로 표시된 첫 번째 명령이 시작 시 메뉴에 표시되는 기본 명령입니다. 메뉴 형식에 대 한 자세한 내용은 `MenuController` [menu 요소](../extensibility/menu-element.md)를 참조 하세요.  
  
   - 명령이 현재 사용되는 경우:  
  
      `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
   - 명령이 바로 가기 메뉴의 일부이고 기본적으로 숨겨져 있는 경우:  
  
      `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
   - 명령에서 `TEXTCHANGES` 플래그를 사용하는 경우 `rgwz` 매개 변수의 `pCmdText` 요소를 명령의 새 텍스트로 설정하고 `cwActual` 매개 변수의 `pCmdText` 요소를 명령 문자열의 크기로 설정합니다.  
  
     오류 조건의 경우 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드는 다음과 같은 오류 사례를 처리해야 합니다.  
  
   - GUID를 알 수 없거나 지원되지 않는 경우 `OLECMDERR_E_UNKNOWNGROUP`을 반환합니다.  
  
   - GUID를 알 수 있지만 명령 ID를 알 수 없거나 지원되지 않는 경우 `OLECMDERR_E_NOTSUPPORTED`을 반환합니다.  
  
   <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드의 VSPackage 구현은 명령이 지원되는지 여부와 성공적으로 처리되었는지 여부에 따라 특정 오류 코드도 반환해야 합니다.  
  
##### <a name="to-implement-the-exec-method"></a>Exec 메서드를 구현하려면  
  
- `GUID` 명령을 알 수 없는 경우 `OLECMDERR_E_UNKNOWNGROUP`을 반환합니다.  
  
- `GUID` 가 알려졌지만 명령 ID를 알 수 없는 경우 `OLECMDERR_E_NOTSUPPORTED`를 반환합니다.  
  
- `GUID` 및 명령 ID가 .vsct 파일의 명령에 사용되는 GUID:ID 쌍과 일치하는 경우 명령과 연결된 코드를 실행하고 <xref:Microsoft.VisualStudio.VSConstants.S_OK>를 반환합니다.  
  
## <a name="see-also"></a>관련 항목  
 [VSCT XML 스키마 참조](../extensibility/vsct-xml-schema-reference.md)   
 [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
