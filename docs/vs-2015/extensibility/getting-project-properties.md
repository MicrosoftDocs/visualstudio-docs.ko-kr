---
title: 프로젝트 속성을 가져오는 중 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d0557d08c318eda47853ec69c6204739cbece560
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204328"
---
# <a name="getting-project-properties"></a>프로젝트 속성 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 도구 창에 프로젝트 속성을 표시 하는 방법을 보여 줍니다.  
  
## <a name="prerequisites"></a>사전 준비 사항  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX 프로젝트를 만들고 도구 창을 추가 하려면  
  
1. 모든 Visual Studio 확장은 확장 자산을 포함 하는 VSIX 배포 프로젝트로 시작 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]이라는 VSIX 프로젝트를 만듭니다 `ProjectPropertiesExtension` . **새 프로젝트** 대화 상자의 **Visual c #/확장성**에서 VSIX 프로젝트 템플릿을 찾을 수 있습니다.  
  
2. 이라는 사용자 지정 도구 창 항목 템플릿을 추가 하 여 도구 창을 추가 `ProjectPropertiesToolWindow` 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택 합니다. **새 항목 추가 대화 상자**에서 **Visual c # 항목/확장성** 으로 이동 하 고 **사용자 지정 도구 창**을 선택 합니다. 대화 상자의 맨 아래에 있는 **이름** 필드에서 파일 이름을으로 변경 합니다 `ProjectPropertiesToolWindow.cs` . 사용자 지정 도구 창을 만드는 방법에 대 한 자세한 내용은 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요.  
  
3. 솔루션을 빌드하고 오류 없이 컴파일되는지 확인합니다.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>도구 창에 프로젝트 속성을 표시 하려면  
  
1. ProjectPropertiesToolWindowCommand.cs 파일에서 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2. ProjectPropertiesToolWindowControl에서 기존 단추를 제거 하 고 도구 상자에서 TreeView를 추가 합니다. ProjectPropertiesToolWindowControl.xaml.cs 파일에서 클릭 이벤트 처리기를 제거할 수도 있습니다.  
  
3. ProjectPropertiesToolWindowCommand.cs에서 ShowToolWindow () 메서드를 사용 하 여 프로젝트를 열고 해당 속성을 읽은 다음 TreeView에 속성을 추가 합니다. ShowToolWindow에 대 한 코드는 다음과 같습니다.  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다.  
  
5. 실험적 인스턴스에서 프로젝트를 엽니다.  
  
6. **보기/기타 창** 에서 **ProjectPropertiesToolWindow**를 클릭 합니다.  
  
     도구 창에 첫 번째 프로젝트 이름 및 모든 프로젝트 속성의 트리 컨트롤이 표시 됩니다.
