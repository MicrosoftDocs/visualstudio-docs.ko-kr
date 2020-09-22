---
title: 'FAQ: VSPackage 확장으로 추가 기능 변환 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6ed31f96fc2021d0d9e104692f0440cfb78a5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842054"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>FAQ: VSPackage 확장으로 추가 기능 변환
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

추가 기능은 이제 사용되지 않습니다. 새 Visual Studio 확장을 만들려면 VSIX 확장을 만들어야 합니다. Visual Studio 추가 기능을 VSIX 확장으로 변환 하는 방법에 대 한 몇 가지 질문과 대답은 다음과 같습니다.  
  
> [!WARNING]
> Visual Studio 2015부터 c # 및 Visual Basic 프로젝트의 경우 VSIX 프로젝트를 사용 하 고 메뉴 명령, 도구 창 및 Vspackage에 대 한 항목 템플릿을 추가할 수 있습니다. 자세한 내용은 [Visual Studio 2015 SDK의 새로운 기능](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)을 참조 하세요.  
  
> [!IMPORTANT]
> 대부분의 경우 VSPackage 프로젝트 항목을 사용 하 여 추가 기능 코드를 VSIX 프로젝트로 전송 하기만 하면 됩니다. <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 메서드에서 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>를 호출하여 DTE 자동화 개체를 가져올 수 있습니다.  
>   
> `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
> 자세한 내용은 아래의 [VSPackage에서 추가 기능 코드를 실행 하려면 어떻게 해야 하나요?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) 를 참조 하세요.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>VSIX 확장을 개발 하는 데 필요한 소프트웨어는 무엇 인가요?  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="wheres-the-extension-documentation"></a>확장 설명서는 어디에 있나요?  
 먼저 [Visual Studio 확장 개발을](../extensibility/starting-to-develop-visual-studio-extensions.md)시작 합니다. MSDN의 서 수 진한 확장 개발에 대 한 다른 문서는 그 아래에 있습니다.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>추가 기능 프로젝트를 VSIX 프로젝트로 변환할 수 있나요?  
 VSIX 프로젝트에 사용 되는 메커니즘이 추가 기능 프로젝트의 메커니즘과 동일 하지 않으므로 추가 기능 프로젝트를 VSIX 프로젝트로 직접 변환할 수 없습니다. VSIX 프로젝트 템플릿과 올바른 프로젝트 항목 템플릿에는 VSIX 확장으로 쉽게 시작 하 고 실행할 수 있도록 하는 많은 코드가 있습니다.  
  
## <a name="how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a> VSIX 확장 개발을 시작할 어떻게 할까요? 있나요?  
 메뉴 명령이 있는 VSIX를 만드는 방법은 다음과 같습니다.  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>메뉴 명령이 있는 VSIX 확장을 만들려면  
  
1. VSIX 프로젝트를 만듭니다. (**파일**, **새로 만들기**, **프로젝트**또는 **빠른 실행** 창에 **프로젝트** 입력). **새 프로젝트** 대화 상자에서 **Visual c #/확장성** 또는 **Visual Basic/확장성** 을 확장 하 고 **VSIX 프로젝트**를 선택 합니다. 프로젝트의 이름을 **Testextension** 으로 지정 하 고 위치를 지정 합니다.  
  
2. **사용자 지정 명령** 프로젝트 항목 템플릿을 추가 합니다. **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택 합니다. Visual c # 또는 Visual Basic에 대 한 **새 프로젝트** 대화 상자에서 **확장성** 노드를 선택 하 고 **사용자 지정 명령**을 선택 합니다.  
  
3. F5 키를 눌러 디버그 모드에서 프로젝트를 빌드하고 실행합니다.  
  
     두 번째 Visual Studio 인스턴스가 표시됩니다. 이 두 번째 인스턴스는 실험적 인스턴스이며, 코드를 작성하는 데 사용하는 Visual Studio 인스턴스와 설정이 다를 수도 있습니다. 실험적 인스턴스를 처음 실행할 때는 VS Online에 로그인하고 테마와 프로필을 지정하라는 메시지가 표시됩니다.  
  
     실험적 인스턴스의 **도구** 메뉴에서 **내 명령 이름**이라는 단추가 표시 되어야 합니다. 이 단추를 선택 하면 **TestVSPackagePackage. MenuItemCallback () 내부**에 메시지가 표시 됩니다.  
  
## <a name="how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a> VSPackage에서 추가 기능 코드를 실행 하려면 어떻게 해야 하나요?  
 추가 기능 코드는 보통 두 가지 방법 중 하나로 실행됩니다.  
  
- 메뉴 명령을 통한 트리거. 코드는 `IDTCommandTarget.Exec` 메서드에 포함되어 있습니다.  
  
- 시작 시 자동으로 실행. 코드는 `OnConnection` 이벤트 처리기에 포함되어 있습니다.  
  
  VSPackage에서도 같은 방식을 사용할 수 있습니다. 콜백 메서드에 일부 추가 기능 코드를 추가하는 방법은 다음과 같습니다.  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>VSPackage에서 메뉴 명령을 구현하려면  
  
1. 메뉴 명령이 포함된 VSPackage를 만듭니다. (자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.)  
  
2. VSPackage 정의가 포함된 파일을 엽니다. (C # 프로젝트의 경우 <em>\<your project name></em> Package.cs)  
  
3. 다음 `using` 문을 파일에 추가합니다.  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. `MenuItemCallback` 메서드를 찾습니다. <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 호출을 추가하여 <xref:EnvDTE80.DTE2> 개체를 가져옵니다.  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. 추가 기능의 `IDTCommandTarget.Exec` 메서드에 포함되어 있었던 코드를 추가합니다. 예를 들어, 다음은 새 창을 **출력** 창에 추가 하 고 새 창에 "일부 텍스트"를 출력 하는 코드입니다.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. 이 프로젝트를 빌드하고 실행합니다. **디버그** 도구 모음에서 **시작** 을 선택 하거나 F5 키를 누릅니다. Visual Studio의 실험적 인스턴스에서 **도구** 메뉴에는 **내 명령 이름**이라는 단추가 있어야 합니다. 이 단추를 선택 하면 **일부 텍스트가** **출력** 창에 표시 됩니다. ( **출력** 창을 열어야 할 수도 있습니다.)  
  
   시작 시 코드가 실행되도록 할 수도 있습니다. 그러나 일반적으로 VSPackage 확장에는 이 방식을 사용하지 않는 것이 좋습니다. Visual Studio 시작 시 너무 많은 확장이 로드되면 시작 시간이 현저하게 길어질 수 있습니다. 따라서 솔루션을 열 때와 같이 일부 조건이 충족되는 경우에만 VSPackage를 자동으로 로드하는 것이 보다 효율적입니다.  
  
   아래 절차에서는 솔루션을 열 때 자동으로 로드되는 VSPackage의 추가 기능 코드를 실행하는 방법을 보여줍니다.  
  
#### <a name="to-autoload-a-vspackage"></a>VSPackage를 자동 로드하려면  
  
1. Visual Studio 패키지 프로젝트 항목을 사용 하 여 VSIX 프로젝트를 만듭니다. 이 작업을 수행 하는 단계는 [어떻게 할까요? VSIX 확장 개발 시작](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping)을 참조 하세요. 대신 **Visual Studio 패키지** 프로젝트 항목을 추가 하기만 하면 됩니다.) VSIX 프로젝트 이름을 **TestAutoload**로 합니다.  
  
2. TestAutoloadPackage.cs를 엽니다. 패키지 클래스가 선언된 줄을 찾습니다.  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. 이 줄 위에는 특성 집합이 있습니다. 다음 특성을 추가합니다.  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. 그런 다음 `Initialize()` 메서드에서 중단점을 설정하고 F5 키를 눌러 디버깅을 시작합니다.  
  
5. 실험적 인스턴스에서 프로젝트를 엽니다. VSPackage가 로드되고 중단점에 도달합니다.  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>의 필드를 사용하여 VSPackage를 로드할 다른 컨텍스트를 지정할 수 있습니다. 자세한 내용은 [Vspackage 로드](../extensibility/loading-vspackages.md)를 참조 하세요.  
  
## <a name="how-can-i-get-the-dte-object"></a>DTE 개체는 어떻게 가져오나요?  
 추가 기능에 메뉴 명령, 도구 모음 단추, 도구 창 등의 UI가 표시되지 않는 경우 VSPackage에서 DTE 자동화 개체를 가져오면 코드를 그대로 사용할 수 있습니다. 방법은 다음과 같습니다.  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>VSPackage에서 DTE 개체를 가져오려면  
  
1. Visual Studio 패키지 항목 템플릿을 사용 하는 VSIX 프로젝트에서 Package.cs 파일을 찾습니다 <em>\<project name></em> . 이 파일은 <xref:Microsoft.VisualStudio.Shell.Package>에서 파생되는 클래스로, Visual Studio와 상호 작용하는 데 사용할 수 있습니다. 여기서는 해당 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>를 사용하여 <xref:EnvDTE80.DTE2> 개체를 가져옵니다.  
  
2. 다음 `using` 문을 추가합니다.  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
3. `Initialize` 메서드를 찾습니다. 이 메서드는 패키지 마법사에서 지정한 명령을 처리합니다. <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 호출을 추가하여 DTE 개체를 가져옵니다.  
  
   ```csharp  
   DTE dte = (DTE)GetService(typeof(DTE));  
   ```  
  
   <xref:EnvDTE.DTE> 자동화 개체를 가져온 후에는 추가 기능 코드의 나머지 부분을 프로젝트에 추가할 수 있습니다. <xref:EnvDTE80.DTE2> 개체가 필요한 경우에도 같은 작업을 수행하면 됩니다.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>추가 기능의 메뉴 명령 및 도구 모음 단추를 VSPackage 스타일로 변경하려면 어떻게 하나요?  
 VSPackage 확장은 .vsct 파일을 사용하여 대부분의 메뉴 명령, 도구 모음, 도구 모음 단추 및 기타 UI를 만듭니다. **사용자 지정 명령** 프로젝트 항목 템플릿은 **도구** 메뉴에서 명령을 만들 수 있는 옵션을 제공 합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.  
  
 . Vsct 파일에 대 한 자세한 내용은 [How Vspackage Add User Interface Elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md)항목을 참조 하세요. . Vsct 파일을 사용 하 여 메뉴 항목, 도구 모음 및 도구 모음 단추를 추가 하는 방법을 보여 주는 연습은 메뉴 [및 명령 확장](../extensibility/extending-menus-and-commands.md)을 참조 하세요.  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>VSPackage 방식으로 사용자 지정 도구 창을 추가하려면 어떻게 하나요?  
 사용자 지정 도구 창 프로젝트 항목 템플릿은 도구 창을 만드는 옵션을 제공 합니다. 이 프로젝트 항목 템플릿에 대 한 자세한 내용은 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요. 도구 창에 대 한 자세한 내용은 도구 창 [확장 및 사용자 지정](../extensibility/extending-and-customizing-tool-windows.md) , 특히 [도구 창 추가](../extensibility/adding-a-tool-window.md)를 참조 하세요.  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>VSPackage 방식으로 Visual Studio 창을 관리하려면 어떻게 하나요?  
 추가 기능이 Visual Studio 창을 관리하는 경우 VSPackage에서도 추가 기능 코드가 작동합니다. 예를 들어이 절차에서는 **작업 목록** 를 관리 하는 코드를 VSPackage의 메서드에 추가 하는 방법을 보여 줍니다 `MenuItemCallback` .  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>창 관리 코드를 추가 기능에서 VSPackage로 삽입하려면  
  
1. [어떻게 할까요? VSIX 확장 개발 시작](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) 섹션에서와 같이 메뉴 명령이 포함 된 VSPackage를 만듭니다.  
  
2. VSPackage 정의가 포함된 파일을 엽니다. (C # 프로젝트의 경우 <em>\<your project name></em> Package.cs)  
  
3. 다음 `using` 문을 추가합니다.  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. `MenuItemCallback` 메서드를 찾습니다. <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 호출을 추가하여 <xref:EnvDTE80.DTE2> 개체를 가져옵니다.  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. 추가 기능의 코드를 추가합니다. 예를 들어 **작업 목록**에 새 작업을 추가 하 고 작업 수를 나열한 다음 작업을 삭제 하는 코드는 다음과 같습니다.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)   
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
       TaskList tl = (TaskList)dte.ToolWindows.TaskList;   
       askItem tlItem;   
  
       // Add a couple of tasks to the Task List.   
       tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",    
           vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,   
           true, "", 10, true, true);  
       tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",   
           vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);  
  
       // List the total number of task list items after adding the new task items.  
       System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);  
       System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
  
       // Remove the second task item. The items list in reverse numeric order.   
       System.Windows.Forms.MessageBox.Show("Deleting the second task item");  
       tl.TaskItems.Item(2).Delete();  
       System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
   }  
   ```  
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>VSPackage에서 프로젝트와 솔루션을 관리하려면 어떻게 하나요?  
 추가 기능이 프로젝트와 솔루션을 관리하는 경우 VSPackage에서도 추가 기능 코드가 작동합니다. 예를 들어 다음 절차에서는 시작 프로젝트를 가져오는 코드를 추가하는 방법을 보여줍니다.  
  
1. [어떻게 할까요? VSIX 확장 개발 시작](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) 섹션에서와 같이 메뉴 명령이 포함 된 VSPackage를 만듭니다.  
  
2. VSPackage 정의가 포함된 파일을 엽니다. (C # 프로젝트의 경우 <em>\<your project name></em> Package.cs)  
  
3. 다음 `using` 문을 추가합니다.  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. `MenuItemCallback` 메서드를 찾습니다. <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 호출을 추가하여 <xref:EnvDTE80.DTE2> 개체를 가져옵니다.  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. 추가 기능의 코드를 추가합니다. 예를 들어 다음 코드는 솔루션의 시작 프로젝트 이름을 가져옵니다. 이 패키지를 실행할 때는 다중 프로젝트 솔루션이 열려 있어야 합니다.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
       SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;   
       Project startupProj;   
       string msg = "";  
  
       foreach (String item in (Array)sb.StartupProjects)   
       {  
           msg += item;   
       }  
       System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);   
       startupProj = dte.Solution.Item(msg);   
       System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);   
   }  
   ```  
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>VSPackage에서 바로 가기 키를 설정하려면 어떻게 하나요?  
 .vsct 파일의 `<KeyBindings>` 요소를 사용합니다. 다음 예에서 `idCommand1` 명령의 바로 가기 키는 Alt+A이고 `idCommand2` 명령의 바로 가기 키는 Alt+Ctrl+A입니다. 키 이름의 구문을 확인하세요.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>VSPackage에서 자동화 이벤트를 처리하려면 어떻게 하나요?  
 VSPackage에서도 추가 기능에서와 같은 방식으로 자동화 이벤트를 처리합니다. 다음 코드에서는 `OnItemRenamed` 이벤트를 처리하는 방법을 보여줍니다. 이 예에서는 DTE 개체를 이미 가져왔다고 가정합니다.  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```
