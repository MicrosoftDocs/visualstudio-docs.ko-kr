---
title: 프로젝트 속성 얻기 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711416"
---
# <a name="get-project-properties"></a>프로젝트 속성 받기

이 연습에서는 도구 창에 프로젝트 속성을 표시하는 방법을 보여 주며, 프로젝트 속성을 표시합니다.

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX 프로젝트를 만들고 도구 창을 추가하려면

1. 모든 Visual Studio 확장은 확장 에셋을 포함하는 VSIX 배포 프로젝트로 시작합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 라는 VSIX 프로젝트를 `ProjectPropertiesExtension`만듭니다. 새 프로젝트 대화 상자에서 "vsix"를 검색하여 VSIX **프로젝트** 템플릿을 찾을 수 있습니다.

2. .라는 사용자 지정 도구 창 항목 `ProjectPropertiesToolWindow`항목 템플릿을 추가하여 도구 창을 추가합니다. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 새 **항목 추가 대화 상자에서** **Visual C# 항목** > **확장성으로** 이동하여 **사용자 지정 도구 창을**선택합니다. 대화 상자 아래쪽에 있는 **이름** 필드에서 파일 이름을 `ProjectPropertiesToolWindow.cs`로 변경합니다. 사용자 지정 도구 창을 만드는 방법에 대한 자세한 내용은 [도구 창을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오.

3. 솔루션을 빌드하고 오류 없이 컴파일되는지 확인합니다.

### <a name="to-display-project-properties-in-a-tool-window"></a>도구 창에 프로젝트 속성을 표시하려면

1. ProjectPropertiesToolWindowCommand.cs 파일에서 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. *ProjectPropertiesToolWindowControl.xaml에서*기존 단추를 제거하고 도구 상자에서 TreeView를 추가합니다. *ProjectPropertiesToolWindowControl.xaml.cs* 파일에서 클릭 이벤트 처리기를 제거할 수도 있습니다.

3. *ProjectPropertiesToolWindowCommand.cs*메서드를 `ShowToolWindow()` 사용하여 프로젝트를 열고 해당 속성을 읽은 다음 TreeView에 속성을 추가합니다. ShowToolWindow의 코드는 다음과 같아야 합니다.

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

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타나야 합니다.

5. 실험적 인스턴스에서 프로젝트를 엽니다.

6. **보기** > **다른 창에서** **프로젝트속성을 클릭합니다.**

  첫 번째 프로젝트의 이름과 모든 프로젝트 속성의 함께 도구 창에서 트리 컨트롤이 표시됩니다.
