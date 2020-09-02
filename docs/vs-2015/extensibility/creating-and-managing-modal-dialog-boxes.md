---
title: 모달 대화 상자 만들기 및 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b0066f201fbb791d471d5cfb433d9a335aa775
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431578"
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>모달 대화 상자 만들기 및 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 내에서 모달 대화 상자를 만들 때 대화 상자가 표시 되는 동안 대화 상자의 부모 창이 비활성화 되었는지 확인 한 다음 대화 상자를 닫은 후 부모 창을 다시 사용 하도록 설정 해야 합니다. 이렇게 하지 않으면 "Microsoft Visual Studio 모달 대화 상자가 활성화 되어 있으므로 종료할 수 없습니다. 활성 대화 상자를 닫고 다시 시도 하십시오. "  
  
 이 작업을 수행 하는 방법에는 두 가지가 있습니다. WPF 대화 상자가 있는 경우에서 파생 시킨 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 다음를 호출 하 여 대화 상자를 표시 하는 것이 좋습니다 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> . 이렇게 하면 부모 창의 모달 상태를 관리할 필요가 없습니다.  
  
 대화 상자가 WPF가 아니거나 다른 이유로에서 대화 상자 클래스를 파생할 수 없는 경우 대화 상자를 표시 하기 전에 매개 변수를 0으로 설정 하 고 메서드를 호출 하 고 대화 상자를 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> 닫은 후에 1 (true) 매개 변수를 사용 하 여 메서드를 다시 호출 하 여 모달 상태를 직접 호출 하 고 관리 하 여 대화 상자의 부모를 가져와야 합니다.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>DialogWindow에서 파생 된 대화 상자 만들기  
  
1. **Opendialogtest** 라는 VSIX 프로젝트를 만들고 **opendialog**라는 메뉴 명령을 추가 합니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.  
  
2. 클래스를 사용 하려면 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> **참조 추가** 대화 상자의 프레임 워크 탭에서 다음 어셈블리에 대 한 참조를 추가 해야 합니다.  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - WindowsBase  
  
    - System.Xaml  
  
3. OpenDialog.cs에서 다음 문을 추가 합니다 `using` .  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4. 에서 파생 되는 **Testdialogwindow** 라는 클래스를 선언 합니다 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> .  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5. 대화 상자를 최소화 하 고 최대화 하려면 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> 및 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> 를 true로 설정 합니다.  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6. **Opendialog. ShowMessageBox** 메서드에서 기존 코드를 다음 코드로 바꿉니다.  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7. 애플리케이션을 빌드 및 실행합니다. Visual Studio의 실험적 인스턴스가 표시 되어야 합니다. 실험적 인스턴스의 **도구** 메뉴에 **opendialog 호출**이라는 명령이 표시 되어야 합니다. 이 명령을 클릭 하면 대화 상자 창이 표시 됩니다. 창을 최소화 하 고 최대화할 수 있습니다.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>DialogWindow에서 파생 되지 않은 대화 상자 만들기 및 관리  
  
1. 이 절차에서는 이전 절차에서 만든 **Opendialogtest** 솔루션을 동일한 어셈블리 참조를 사용 하 여 사용할 수 있습니다.  
  
2. 다음 선언을 추가 합니다 `using` .  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3. 에서 파생 되는 **TestDialogWindow2** 라는 클래스를 만듭니다 <xref:System.Windows.Window> .  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4. 다음에 대 한 개인 참조를 추가 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> .  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5. 참조를 설정 하는 생성자를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 다음과 같이 추가 합니다.  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6. **Opendialog. ShowMessageBox** 메서드에서 기존 코드를 다음 코드로 바꿉니다.  
  
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
  
7. 애플리케이션을 빌드 및 실행합니다. **도구** 메뉴에 **opendialog 호출**이라는 명령이 표시 되어야 합니다. 이 명령을 클릭 하면 대화 상자 창이 표시 됩니다.
