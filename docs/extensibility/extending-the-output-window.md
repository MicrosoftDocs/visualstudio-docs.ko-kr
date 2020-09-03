---
title: 출력 창 확장 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711650"
---
# <a name="extend-the-output-window"></a>출력 창 확장
**출력** 창은 읽기/쓰기 텍스트 창의 집합입니다. Visual Studio에는 **빌드, 빌드**에 대 한 메시지를 전달 하는 프로젝트, 및에서 **General** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE에 대 한 메시지를 전달 하는 일반적인를 비롯 한 기본 제공 창이 있습니다. 프로젝트는 인터페이스 메서드를 통해 **빌드** 창에 대 한 참조를 자동으로 가져오며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> , Visual Studio는 서비스를 통해 **일반** 창에 직접 액세스할 수 있도록 <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> 합니다. 기본 제공 창 외에도 고유한 사용자 지정 창을 만들고 관리할 수 있습니다.

 및 인터페이스를 통해 **출력** 창을 직접 제어할 수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>서비스에서 제공 하는 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> **출력** 창의 생성, 검색 및 삭제를 위한 메서드를 정의 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>인터페이스는 창을 표시 하 고, 창을 숨기고, 텍스트를 조작 하기 위한 메서드를 정의 합니다. **출력** 창을 제어 하는 또 다른 방법은 <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> Visual Studio 자동화 개체 모델의 및 개체를 통하는 것입니다. 이러한 개체는 및 인터페이스의 거의 모든 기능을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 캡슐화 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 합니다. 또한 <xref:EnvDTE.OutputWindow> 및 <xref:EnvDTE.OutputWindowPane> 개체는 **출력** 창을 보다 쉽게 열거 하 고 창에서 텍스트를 검색 하기 위해 더 높은 수준의 기능을 추가 합니다.

## <a name="create-an-extension-that-uses-the-output-pane"></a>출력 창을 사용 하는 확장 만들기
 출력 창의 다양 한 측면을 나타내는 확장을 만들 수 있습니다.

1. `TestOutput` **Testoutput**이라는 메뉴 명령을 사용 하 여 라는 VSIX 프로젝트를 만듭니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

2. 다음 참조를 추가합니다.

    1. EnvDTE

    2. EnvDTE80

3. *TestOutput.cs*에서 다음 using 문을 추가 합니다.

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. *TestOutput.cs*에서 메서드를 삭제 `ShowMessageBox` 합니다. 다음 메서드 스텁을 추가 합니다.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. TestOutput 생성자에서 명령 처리기를 OutputCommandHandler로 변경 합니다. 명령을 추가 하는 부분은 다음과 같습니다.

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

6. 아래 섹션에는 출력 창을 처리 하는 다양 한 방법을 보여 주는 다양 한 방법이 있습니다. 메서드 본문에 이러한 메서드를 호출할 수 있습니다 `OutputCommandHandler()` . 예를 들어 다음 코드는 `CreatePane()` 다음 섹션에 지정 된 메서드를 추가 합니다.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>IVsOutputWindow를 사용 하 여 출력 창 만들기
 이 예제에서는 인터페이스를 사용 하 여 새 **출력** 창을 만드는 방법을 보여 줍니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> .

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

 이전 섹션에서 제공 하는 확장에이 메서드를 추가 하는 경우 **Testoutput 호출** 명령을 클릭 하면 **출력** 창에 출력 **표시: CreatedPane** 및이 창이 창 자체의 **만든 창** 이라는 단어가 표시 됩니다.

## <a name="create-an-output-window-with-outputwindow"></a>OutputWindow를 사용 하 여 출력 창 만들기
 이 예제에서는 개체를 사용 하 여 **출력** 창을 만드는 방법을 보여 줍니다 <xref:EnvDTE.OutputWindow> .

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

 컬렉션을 <xref:EnvDTE.OutputWindowPanes> 사용 하면 제목으로 **출력** 창을 검색할 수 있지만 창 제목은 고유 하지 않을 수도 있습니다. 제목의 고유성이 확실 하지 않은 경우 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> 해당 GUID로 올바른 창을 검색 합니다.

 이전 섹션에서 제공 하는 확장에이 메서드를 추가 하는 경우 **Testoutput 호출** 명령을 클릭 하면 출력 창에 출력 **표시: dtepane 표시** 하 고 창 자체에 **DTE 창** 이라는 단어가 추가 됩니다.

## <a name="delete-an-output-window"></a>출력 창을 삭제 합니다.
 이 예제에서는 **출력** 창을 삭제 하는 방법을 보여 줍니다.

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

 이전 섹션에서 제공 하는 확장에이 메서드를 추가 하는 경우 **Testoutput 호출** 명령을 클릭 하면 출력 창에 출력 **표시: 새로 만들기 창** 및 **만든** 단어를 창 자체에 표시 하는 헤더와 함께 출력 창이 표시 됩니다. **TestOutput 호출** 명령을 다시 클릭 하면 창이 삭제 됩니다.

## <a name="get-the-general-pane-of-the-output-window"></a>출력 창의 일반 창 가져오기
 이 예제에서는 **출력** 창의 기본 제공 **일반** 창을 가져오는 방법을 보여 줍니다.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 이전 섹션에서 제공 하는 확장에이 메서드를 추가 하는 경우 **Testoutput 호출** 명령을 클릭 하면 창에 **일반 단어 찾음** 창이 **표시** 됩니다.

## <a name="get-the-build-pane-of-the-output-window"></a>출력 창의 빌드 창 가져오기
 이 예제에서는 **빌드** 창을 찾고 여기에 쓰는 방법을 보여 줍니다. **빌드** 창이 기본적으로 활성화 되지 않으므로 활성화 합니다.

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
