---
title: 모달 대화 상자 만들기 및 관리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739486"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>모달 대화 상자 만들기 및 관리
Visual Studio 내에서 모달 대화 상자를 만들 때 대화 상자가 표시되는 동안 대화 상자의 상위 창이 비활성화되었는지 확인한 다음 대화 상자를 닫은 후 부모 창을 다시 활성화해야 합니다. 이렇게 하지 않으면 *모달 대화 상자가 활성화되어 있으므로 Microsoft Visual Studio를 종료할 수 없다는 오류가 발생할 수 있습니다. 활성 대화 상자를 닫고 다시 시도하십시오.*

이 작업을 수행하는 방법에는 두 가지가 있습니다. WPF 대화 상자가 있는 경우 를 파생한 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>다음 호출하여 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> 대화 상자를 표시하는 것이 좋습니다. 이렇게 하면 상위 창의 모달 상태를 관리할 필요가 없습니다.

대화 상자가 WPF가 아니거나 다른 이유로 대화 상자 클래스를 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>파생시킬 수 없는 경우 대화 상자를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> 닫은 후 대화 상자를 표시하기 전에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> 메서드를 0(false)으로 메서드를 호출하고 직접 모달 상태를 관리하여 대화 상자의 부모를 가져옵니다.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>대화 상자창에서 파생된 대화 상자 만들기

1. **OpenDialogTest라는** VSIX 프로젝트를 만들고 **OpenDialog**라는 메뉴 명령을 추가합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

2. 클래스를 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 사용하려면 참조 **추가** 대화 상자의 프레임워크 탭에서 다음 어셈블리에 참조를 추가해야 합니다.

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. *OpenDialog.cs*다음 `using` 문을 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. 에서 파생되는 `TestDialogWindow` 클래스를 선언합니다. <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. 대화 상자를 최소화하고 최대화할 수 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> 있도록 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> 설정 및 true로 설정하려면 다음을 수행하십시오.

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. 메서드에서 `OpenDialog.ShowMessageBox` 기존 코드를 다음과 같은 것으로 바꿉니다.

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. 애플리케이션을 빌드 및 실행합니다. Visual Studio의 실험 인스턴스가 나타나야 합니다. 실험 인스턴스의 **도구** 메뉴에는 **OpenDialog 호출이라는**명령이 표시됩니다. 이 명령을 클릭하면 대화 상자 창이 표시됩니다. 창을 최소화하고 최대화할 수 있어야 합니다.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>대화 상자에서 파생되지 않은 대화 상자 만들기 및 관리

1. 이 절차에서는 동일한 어셈블리 참조와 함께 이전 절차에서 만든 **OpenDialogTest** 솔루션을 사용할 수 있습니다.

2. 다음 `using` 선언을 추가합니다.

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. 에서 파생되는 `TestDialogWindow2` 클래스를 만듭니다. <xref:System.Windows.Window>

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. 개인 참조를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>다음에 추가합니다.

    ```
    private IVsUIShell shell;
    ```

5. 다음으로 참조를 설정하는 생성자 추가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. 메서드에서 `OpenDialog.ShowMessageBox` 기존 코드를 다음과 같은 것으로 바꿉니다.

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. 애플리케이션을 빌드 및 실행합니다. **도구** 메뉴에는 **OpenDialog 호출이라는**명령이 표시됩니다. 이 명령을 클릭하면 대화 상자 창이 표시됩니다.
