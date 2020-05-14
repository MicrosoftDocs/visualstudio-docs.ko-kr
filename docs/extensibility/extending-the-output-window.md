---
title: 출력 창 확장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711650"
---
# <a name="extend-the-output-window"></a>출력 창 확장
**출력** 창은 읽기/쓰기 텍스트 창 의 집합입니다. Visual Studio에는 이러한 기본 제공 창이 있습니다: 빌드에 대 한 메시지를 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 전달 하는 프로젝트 빌드 및 **일반**, IDE에 대 한 메시지를 통신 하는 **빌드입니다.** 프로젝트는 인터페이스 메서드를 통해 **자동으로 빌드** <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 창에 대한 참조를 얻고 Visual **General** Studio는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> 서비스를 통해 일반 창에 직접 액세스할 수 있습니다. 기본 제공 창 외에도 사용자 지정 창을 만들고 관리할 수 있습니다.

 및 인터페이스를 통해 직접 출력 창을 제어할 수 있습니다. **Output** <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 서비스에서 제공하는 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Output 창 창을 생성, 검색 및 파괴하는 방법을 정의합니다. **Output** <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 창을 표시하고, 창을 숨기고, 텍스트를 조작하는 메서드를 정의합니다. **출력** 창을 제어하는 또 다른 방법은 <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> Visual Studio Automation 개체 모델의 및 개체를 통과하는 것입니다. 이러한 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 인터페이스의 거의 모든 기능을 캡슐화합니다. 또한 및 <xref:EnvDTE.OutputWindowPane> <xref:EnvDTE.OutputWindow> 개체는 **출력** 창을 쉽게 등록하고 창에서 텍스트를 검색할 수 있도록 몇 가지 상위 수준 기능을 추가합니다.

## <a name="create-an-extension-that-uses-the-output-pane"></a>출력 창을 사용하는 확장 만들기
 출력 창의 다양한 측면을 연습하는 확장을 만들 수 있습니다.

1. **테스트 출력이라는**메뉴 `TestOutput` 명령으로 명명된 VSIX 프로젝트를 만듭니다. 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

2. 다음 참조를 추가합니다.

    1. EnvDTE

    2. EnvDTE80

3. *TestOutput.cs*다음 문을 사용하여 다음을 추가합니다.

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. *TestOutput.cs*메서드를 `ShowMessageBox` 삭제합니다. 다음 메서드 스텁을 추가합니다.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. 테스트 출력 생성자에서 명령 처리기를 OutputCommandHandler로 변경합니다. 다음은 명령을 추가하는 부분입니다.

    ```csharp
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    if (commandService != null)
    {
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
        EventHandler eventHandler = OutputCommandHandler;
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

6. 아래 섹션에는 출력 창을 처리하는 다양한 방법을 보여 주는 여러 가지 방법이 있습니다. 이러한 메서드를 `OutputCommandHandler()` 메서드의 본문에 호출할 수 있습니다. 예를 들어 다음 코드는 `CreatePane()` 다음 섹션에 지정된 메서드를 추가합니다.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>IVs출력창으로 출력 창 만들기
 이 예제에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 인터페이스를 사용하여 새 **출력** 창을 만드는 방법을 보여 줍니다.

```csharp
void CreatePane(Guid paneGuid, string title,
    bool visible, bool clearWithSolution)
{
    IVsOutputWindow output =
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));
    IVsOutputWindowPane pane;

    // Create a new pane.
    output.CreatePane(
        ref paneGuid,
        title,
        Convert.ToInt32(visible),
        Convert.ToInt32(clearWithSolution));

    // Retrieve the new pane.
    output.GetPane(ref paneGuid, out pane);

     pane.OutputString("This is the Created Pane \n");
}
```

 이전 섹션에 제공된 확장에 이 메서드를 추가하면 **TestOutput 호출** 호출 명령을 클릭하면 **출력 표시: CreatedPane** 및 창 자체에서 **만든 창이라는** 헤더가 있는 출력 **창이** 표시됩니다.

## <a name="create-an-output-window-with-outputwindow"></a>출력 창으로 출력 창 만들기
 이 예제에서는 개체를 사용하여 **출력** 창을 <xref:EnvDTE.OutputWindow> 만드는 방법을 보여 주며 있습니다.

```csharp
void CreatePane(string title)
{
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;

    try
    {
        // If the pane exists already, write to it.
        panes.Item(title);
    }
    catch (ArgumentException)
    {
        // Create a new pane and write to it.
        panes.Add(title);
    }
}
```

 컬렉션에서 <xref:EnvDTE.OutputWindowPanes> 제목으로 **출력** 창을 검색할 수 있지만 창 제목이 고유하다고 보장할 수는 없습니다. 제목의 고유성을 의심하는 경우 이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> 메서드를 사용하여 GUID로 올바른 창을 검색합니다.

 이전 섹션에 제공된 확장에 이 메서드를 추가하면 **TestOutput 호출** 명령을 클릭하면 **출력 표시라는** 헤더가 있는 출력 창이 표시됩니다. **Added DTE Pane**

## <a name="delete-an-output-window"></a>출력 창 삭제
 이 예제에서는 **출력** 창을 삭제하는 방법을 보여 주며,

```csharp
void DeletePane(Guid paneGuid)
{
    IVsOutputWindow output =
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));

    IVsOutputWindowPane pane;
    output.GetPane(ref paneGuid, out pane);

    if (pane == null)
    {
        CreatePane(paneGuid, "New Pane\n", true, true);
    }
     else
    {
        output.DeletePane(ref paneGuid);
    }
}
```

 이전 섹션에 제공된 확장에 이 메서드를 추가하면 **TestOutput 호출** 호출 명령을 클릭하면 **출력 표시라는** 헤더가 있는 출력 창이 표시됩니다. **Added Created Pane** **테스트출력 호출** 명령을 다시 클릭하면 창이 삭제됩니다.

## <a name="get-the-general-pane-of-the-output-window"></a>출력 창의 일반 창 받기
 이 예제에서는 **출력** 창의 기본 제공 **일반** 창을 얻는 방법을 보여 주었습니다.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 이전 섹션에 제공된 확장에 이 메서드를 추가하면 **TestOutput 호출** 명령을 클릭하면 **출력** 창에 창에서 **일반 창발견이라는** 단어가 표시됩니다.

## <a name="get-the-build-pane-of-the-output-window"></a>출력 창의 빌드 창 받기
 이 예제에서는 **빌드** 창을 찾고 창에 쓰는 방법을 보여 주며, 이 창에 쓰는 방법을 보여 주시고 있습니다. **빌드** 창은 기본적으로 활성화되지 않으므로 활성화됩니다.

```csharp
void OutputTaskItemStringExExample(string buildMessage)
{
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));

    EnvDTE.OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;
    foreach (EnvDTE.OutputWindowPane pane in panes)
        {
            if (pane.Name.Contains("Build"))
            {
                pane.OutputString(buildMessage + "\n");
                pane.Activate();
                return;
             }
        }
}
```
