---
title: 범용 Windows 프로젝트 관리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbbf9b6aaf983bb36291611a7b9b50f7886915b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702693"
---
# <a name="manage-universal-windows-projects"></a>범용 Windows 프로젝트 관리

유니버설 Windows 앱은 Windows 8.1과 Windows Phone 8.1을 모두 대상으로 하는 앱으로, 개발자가 두 플랫폼에서 코드 및 기타 자산을 사용할 수 있습니다. 공유 코드와 리소스는 공유 프로젝트에 보관되고 플랫폼별 코드와 리소스는 Windows용 및 Windows Phone용 다른 프로젝트에 대해 별도의 프로젝트에 보관됩니다. 범용 Windows 앱에 대한 자세한 내용은 [유니버설 Windows 앱을](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx)참조하십시오. 프로젝트를 관리하는 Visual Studio 확장은 유니버설 Windows 앱 프로젝트에 단일 플랫폼 앱과 다른 구조를 가지고 있다는 점에 유의해야 합니다. 이 연습에서는 공유 프로젝트를 탐색하고 공유 항목을 관리하는 방법을 보여 주며, 이 연습에서는 공유 프로젝트를 탐색할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

### <a name="navigate-the-shared-project"></a>공유 프로젝트 탐색

1. **테스트유니버설 프로젝트라는**C# VSIX 프로젝트를 만듭니다. (파일**File** > **새** > **프로젝트** 다음 **C#** > **확장성** > 비주얼 스튜디오**패키지).** 사용자 **지정 명령** 프로젝트 항목 템플릿을 추가합니다(솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택한 다음 **확장성으로**이동). 파일 테스트유니버설 프로젝트의 이름을 **지정합니다.**

2. *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* 및 *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll(확장* 섹션)에 대한 **참조를 추가합니다.**

3. *TestUniversalProject.cs* 열고 다음 `using` 지시문을 추가합니다.

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. 클래스에서 `TestUniversalProject` **출력** 창을 가리키는 전용 필드를 추가합니다.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. TestUniversalProject 생성자 내부의 출력 창에 대한 참조를 설정합니다.

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }
        // get a reference to the Output window
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. `ShowMessageBox` 메서드에서 기존 코드를 제거합니다.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. 이 연습에서 여러 가지 용도로 사용할 DTE 개체를 가져옵니다. 또한 메뉴 단추를 클릭할 때 솔루션이 로드되었는지 확인합니다.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. 공유 프로젝트를 찾습니다. 공유 프로젝트는 순수 컨테이너입니다. 출력을 빌드하거나 생성하지 않습니다. 다음 메서드는 공유 프로젝트 기능이 있는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 개체를 검색하여 솔루션에서 첫 번째 공유 프로젝트를 찾습니다.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. 메서드에서 공유 프로젝트의 **캡션(솔루션 탐색기에**나타나는 프로젝트 이름)을 출력합니다. `ShowMessageBox`

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
                }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. 활성 플랫폼 프로젝트를 가져옵니다. 플랫폼 프로젝트는 플랫폼별 코드와 리소스를 포함하는 프로젝트입니다. 다음 메서드는 새 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> 필드를 사용 하 여 활성 플랫폼 프로젝트를 가져옵니다.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. 메서드에서 `ShowMessageBox` 활성 플랫폼 프로젝트의 캡션을 출력합니다.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
            {
                MessageBox.Show("No solution is open");
                return;
            }
        }
    }
    ```

12. 플랫폼 프로젝트를 반복합니다. 다음 메서드는 공유 프로젝트에서 모든 가져오기(플랫폼) 프로젝트를 가져옵니다.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > 사용자가 실험 인스턴스에서 C++ 유니버설 Windows 앱 프로젝트를 연 경우 위의 코드에서 예외를 throw합니다. 이것은 알려진 문제이며 예외를 방지하려면 위의 `foreach` 블록을 다음으로 바꿉을 참조하십시오.

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. 메서드에서 `ShowMessageBox` 각 플랫폼 프로젝트의 캡션을 출력합니다. 활성 플랫폼 프로젝트의 캡션을 출력하는 줄 다음에 다음 코드를 삽입합니다. 로드된 플랫폼 프로젝트만 이 목록에 나타납니다.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. 활성 플랫폼 프로젝트를 변경합니다. 다음 메서드는 을 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>활성 프로젝트를 설정합니다.

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. 메서드에서 `ShowMessageBox` 활성 플랫폼 프로젝트를 변경합니다. 블록 내부에 이 `foreach` 코드를 삽입합니다.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. 이제 그것을 밖으로 시도. F5를 눌러 실험 인스턴스를 시작합니다. 실험 인스턴스에서 C# 유니버설 허브 앱 프로젝트를 만듭니다(새 **프로젝트** 대화 상자, **Visual C#** > **Windows** > **8** > **유니버설** > **허브 앱).** 솔루션이 로드된 후 **도구** 메뉴로 이동하여 **TestUniversalProject 호출을**클릭한 다음 **출력** 창에서 텍스트를 확인합니다. 다음과 유사한 출력이 표시됩니다.

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>플랫폼 프로젝트에서 공유 항목 관리

1. 플랫폼 프로젝트에서 공유 항목을 찾습니다. 공유 프로젝트의 항목은 플랫폼 프로젝트에 공유 항목으로 나타납니다. **솔루션 탐색기에서는**볼 수 없지만 프로젝트 계층 구조를 탐색하여 찾을 수 있습니다. 다음 메서드는 계층 구조를 안내 하고 모든 공유 항목을 수집 합니다. 선택적으로 각 항목의 캡션을 출력합니다. 공유 항목은 새 속성으로 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>식별됩니다.

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
                    }
    }
    ```

2. 메서드에서 `ShowMessageBox` 다음 코드를 추가하여 플랫폼 프로젝트 계층 구조 항목을 이동합니다. 블록 내부에 `foreach` 삽입합니다.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. 공유 항목을 읽습니다. 공유 항목은 플랫폼 프로젝트에 숨겨진 연결된 파일로 표시되며 모든 속성을 일반 링크된 파일로 읽을 수 있습니다. 다음 코드는 첫 번째 공유 항목의 전체 경로를 읽습니다.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. 이제 그것을 밖으로 시도. **F5를** 눌러 실험 인스턴스를 시작합니다. 실험 인스턴스에서 C# 범용 허브 앱 프로젝트를 만듭니다(새 **프로젝트** 대화 상자, **Visual C#** > **Windows** > **8** > **유니버설** > **허브 앱)** **도구** 메뉴로 이동하여 **TestUniversalProject 호출을**클릭한 다음 **출력** 창에서 텍스트를 선택합니다. 다음과 유사한 출력이 표시됩니다.

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>플랫폼 프로젝트 및 공유 프로젝트의 변경 사항 감지

1. 계층 구조 및 프로젝트 이벤트를 사용하여 플랫폼 프로젝트에서와 마찬가지로 공유 프로젝트의 변경 내용을 검색할 수 있습니다. 그러나 공유 프로젝트의 프로젝트 항목이 표시되지 않으므로 공유 프로젝트 항목이 변경될 때 특정 이벤트가 발생하지 않습니다.

    프로젝트의 파일 이름이 바뀌는 이벤트 순서를 고려합니다.

   1. 파일 이름이 디스크에서 변경됩니다.

   2. 프로젝트 파일이 업데이트되어 파일의 새 이름이 포함됩니다.

      계층 구조 이벤트(예: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>일반적으로 솔루션 **탐색기**에서와 같이 UI에 표시되는 변경 내용을 추적합니다. 계층 구조 이벤트는 파일 이름 바꾸기 작업을 파일 삭제및 파일 추가로 간주합니다. 그러나 보이지 않는 항목이 변경되면 계층 구조 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 이벤트 시스템은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 이벤트가 아닌 이벤트를 발생시게 됩니다. 따라서 플랫폼 프로젝트에서 파일의 이름을 바꾸면 둘 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>얻을 수 있지만 공유 프로젝트에서 파일의 이름을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>바꾸면 .만 얻을 수 있습니다.

      프로젝트 항목의 변경 내용을 추적하려면 DTE 프로젝트 항목 이벤트(에 <xref:EnvDTE.ProjectItemsEventsClass>있는 항목)를 처리할 수 있습니다. 그러나 많은 수의 이벤트를 처리하는 경우 에서 이벤트를 처리하는 성능을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>향상시킬 수 있습니다. 이 연습에서는 계층 구조 이벤트와 DTE 이벤트만 보여 드립니다. 이 절차에서는 공유 프로젝트 및 플랫폼 프로젝트에 이벤트 리스너를 추가합니다. 그런 다음 공유 프로젝트의 한 파일과 플랫폼 프로젝트의 다른 파일의 이름을 바꾸면 각 이름 바꾸기 작업에 대해 발생되는 이벤트를 볼 수 있습니다.

      이 절차에서는 공유 프로젝트 및 플랫폼 프로젝트에 이벤트 리스너를 추가합니다. 그런 다음 공유 프로젝트의 한 파일과 플랫폼 프로젝트의 다른 파일의 이름을 바꾸면 각 이름 바꾸기 작업에 대해 발생되는 이벤트를 볼 수 있습니다.

2. 이벤트 리스너를 추가합니다. 프로젝트에 새 클래스 파일을 추가하고 *HierarchyEventListener.cs*호출합니다.

3. *HierarchyEventListener.cs* 파일을 열고 지시문을 사용하여 다음을 추가합니다.

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. 클래스 `HierarchyEventListener` 구현: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. 아래 코드에서와 같이 의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>멤버를 구현합니다.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. 동일한 클래스에서 프로젝트 항목의 이름이 바뀌때마다 발생하는 DTE 이벤트에 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>대한 다른 이벤트 처리기를 추가합니다.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. 계층 구조 이벤트에 등록합니다. 추적하는 모든 프로젝트에 대해 별도로 등록해야 합니다. `ShowMessageBox`에 다음 코드를 추가 합니다 .

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. DTE 프로젝트 항목 이벤트에 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>등록합니다. 두 번째 수신기를 연결한 후 다음 코드를 추가합니다.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. 공유 항목을 수정합니다. 플랫폼 프로젝트에서공유 항목을 수정할 수 없습니다. 대신 이러한 항목의 실제 소유자인 공유 프로젝트에서 수정해야 합니다. 공유 프로젝트에서 해당 항목 ID를 얻을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>수 있습니다. 그런 다음 공유 항목을 수정할 수 있습니다. 변경 사항은 플랫폼 프로젝트에 전파됩니다.

    > [!IMPORTANT]
    > 프로젝트 항목을 수정하기 전에 프로젝트 항목이 공유 항목인지 여부를 확인해야 합니다.

     다음 메서드는 프로젝트 항목 파일의 이름을 수정합니다.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. 다른 모든 코드 가 공유 `ShowMessageBox` 프로젝트의 항목의 파일 이름을 수정하려면 이 메서드를 호출합니다. 공유 프로젝트에서 항목의 전체 경로를 얻는 코드 후에 삽입합니다.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. 프로젝트를 빌드하고 실행합니다. 실험 인스턴스에서 C# 범용 허브 앱을 만들고 **도구** 메뉴로 이동하여 **TestUniversalProject 호출을**클릭하고 일반 출력 창에서 텍스트를 확인합니다. 공유 프로젝트의 첫 번째 항목 이름(App.xaml *App.xaml* 파일로 예상)은 변경되어야 하며 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> 이벤트가 발생했는지 확인해야 합니다. 이 경우 *App.xaml의* 이름을 바꾸면 *App.xaml.cs* 이름이 바뀌므로 네 개의 이벤트(각 플랫폼 프로젝트에 대해 2개)가 표시됩니다. DTE 이벤트는 공유 프로젝트의 항목을 추적하지 않습니다. 두 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 개의 이벤트(각 플랫폼 프로젝트에 대해 하나씩)가 표시되지만 이벤트는 표시되지 않습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>

12. 이제 플랫폼 프로젝트에서 파일 이름을 바꾸면 발생되는 이벤트의 차이를 확인할 수 있습니다. 호출 후 에서 `ShowMessageBox` 다음 코드를 `ModifyFileName`추가합니다.

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. 프로젝트를 빌드하고 실행합니다. 실험 인스턴스에서 C# 유니버설 프로젝트를 만들고 **도구** 메뉴로 이동하여 **TestUniversalProject 호출을**클릭하고 일반 출력 창에서 텍스트를 확인합니다. 플랫폼 프로젝트의 파일 이름이 변경된 후에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 이벤트와 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 이벤트가 모두 표시됩니다. 파일을 변경하면 다른 파일이 변경되지 않으며 플랫폼 프로젝트의 항목 변경 내용이 아무 데도 전파되지 않으므로 이러한 이벤트는 각각 하나만 있습니다.
