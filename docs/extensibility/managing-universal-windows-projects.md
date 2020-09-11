---
title: 유니버설 Windows 프로젝트 관리 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83e3b07bc3373070953709ffe913f37529e74bc7
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012310"
---
# <a name="manage-universal-windows-projects"></a>유니버설 Windows 프로젝트 관리

유니버설 Windows 앱은 Windows 8.1 및 Windows Phone 8.1를 모두 대상으로 하는 앱으로, 개발자가 두 플랫폼에서 코드와 기타 자산을 사용할 수 있도록 합니다. 공유 코드와 리소스는 공유 프로젝트에 유지 되는 반면 플랫폼별 코드와 리소스는 서로 다른 프로젝트에 유지 되 고, 다른 하나는 Windows 용으로 유지 되 고 다른 하나는 Windows Phone 합니다. 유니버설 Windows 앱에 대 한 자세한 내용은 [유니버설 windows 앱](/windows/uwp/get-started/create-uwp-apps)을 참조 하세요. 프로젝트를 관리 하는 Visual Studio 확장은 유니버설 Windows 앱 프로젝트에 단일 플랫폼 앱과 다른 구조가 있음을 인식 해야 합니다. 이 연습에서는 공유 프로젝트를 탐색 하 고 공유 항목을 관리 하는 방법을 보여 줍니다.

## <a name="prerequisites"></a>필수 구성 요소

Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

### <a name="navigate-the-shared-project"></a>공유 프로젝트 탐색

1. **TestUniversalProject**라는 c # VSIX 프로젝트를 만듭니다. (**파일**  >  **새**  >  **프로젝트** 및 **c #**  >  **확장성**  >  **Visual Studio 패키지**)를 차례로 클릭 합니다. **사용자 지정 명령** 프로젝트 항목 템플릿을 추가 합니다 ( **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목**추가를 선택한 다음, **확장성**으로 이동). 파일 이름을 **TestUniversalProject**로 합니다.

2. *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* 에 대 한 참조를 추가 하 고 **확장** 섹션에서 *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* 합니다.

3. *TestUniversalProject.cs* 를 열고 다음 지시문을 추가 합니다 `using` .

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

4. 클래스에서 `TestUniversalProject` **출력** 창을 가리키는 전용 필드를 추가 합니다.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. TestUniversalProject constructor 내에서 출력 창에 대 한 참조를 설정 합니다.

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

6. 메서드에서 기존 코드를 제거 합니다 `ShowMessageBox` .

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. 이 연습에서는 몇 가지 용도로 사용할 DTE 개체를 가져옵니다. 또한 메뉴 단추를 클릭할 때 솔루션이 로드 되는지 확인 합니다.

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

8. 공유 프로젝트를 찾습니다. 공유 프로젝트는 순수 컨테이너입니다. 출력을 빌드하거나 생성 하지 않습니다. 다음 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 공유 프로젝트 기능을 포함 하는 개체를 검색 하 여 솔루션의 첫 번째 공유 프로젝트를 찾습니다.

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

9. `ShowMessageBox`메서드에서 공유 프로젝트의 캡션 ( **솔루션 탐색기**에 표시 되는 프로젝트 이름)을 출력 합니다.

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

10. 활성 플랫폼 프로젝트를 가져옵니다. 플랫폼 프로젝트는 플랫폼 특정 코드 및 리소스가 포함 된 프로젝트입니다. 다음 메서드는 새 필드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> 활성 플랫폼 프로젝트를 가져옵니다.

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

11. `ShowMessageBox`메서드에서 활성 플랫폼 프로젝트의 캡션을 출력 합니다.

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
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. 플랫폼 프로젝트를 반복 합니다. 다음 메서드는 공유 프로젝트에서 가져오기 (플랫폼) 프로젝트를 모두 가져옵니다.

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
    > 사용자가 실험적 인스턴스에서 c + + 유니버설 Windows 앱 프로젝트를 연 경우 위의 코드에서 예외를 throw 합니다. 이것은 알려진 문제입니다. 예외를 방지 하려면 `foreach` 위의 블록을 다음으로 바꿉니다.

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. `ShowMessageBox`메서드에서 각 플랫폼 프로젝트의 캡션을 출력 합니다. 활성 플랫폼 프로젝트의 캡션을 출력 하는 줄 뒤에 다음 코드를 삽입 합니다. 이 목록에는 로드 된 플랫폼 프로젝트만 표시 됩니다.

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

14. 활성 플랫폼 프로젝트를 변경 합니다. 다음 메서드는를 사용 하 여 활성 프로젝트를 설정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. `ShowMessageBox`메서드에서 활성 플랫폼 프로젝트를 변경 합니다. 블록 내에이 코드 `foreach` 를 삽입 합니다.

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

16. 이제 사용해 보세요. F5 키를 눌러 실험적 인스턴스를 시작 합니다. **새 프로젝트** 대화 상자의 **Visual c #**  >  **windows**  >  **8**  >  **유니버설**  >  **허브 앱**에서 실험적 인스턴스에 c # 유니버설 허브 앱 프로젝트를 만듭니다. 솔루션이 로드 되 면 **도구** 메뉴로 이동 하 여 **TestUniversalProject 호출**을 클릭 한 다음 **출력** 창에서 텍스트를 확인 합니다. 다음과 유사한 출력이 표시됩니다.

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>플랫폼 프로젝트에서 공유 항목 관리

1. 플랫폼 프로젝트에서 공유 항목을 찾습니다. 공유 프로젝트의 항목은 플랫폼 프로젝트에 공유 항목으로 표시 됩니다. **솔루션 탐색기**에서 볼 수 없지만 프로젝트 계층 구조를 탐색 하 여 찾을 수 있습니다. 다음 메서드는 계층을 탐색 하 고 모든 공유 항목을 수집 합니다. 필요에 따라 각 항목의 캡션을 출력 합니다. 공유 항목은 새 속성으로 식별 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> .

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

2. `ShowMessageBox`메서드에서 플랫폼 프로젝트 계층 구조 항목을 탐색 하는 다음 코드를 추가 합니다. 블록 내에 삽입 `foreach` 합니다.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. 공유 항목을 읽습니다. 공유 항목은 플랫폼 프로젝트에 숨겨진 연결 된 파일로 나타나며 모든 속성을 일반 연결 된 파일로 읽을 수 있습니다. 다음 코드는 첫 번째 공유 항목의 전체 경로를 읽습니다.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. 이제 사용해 보세요. **F5** 키를 눌러 실험적 인스턴스를 시작 합니다. 실험적 인스턴스에서 c # 유니버설 허브 앱 프로젝트 만들기 ( **새 프로젝트** 대화 상자에서 **Visual c #**  >  **windows**  >  **8**  >  **유니버설**  >  **허브 앱**) **도구** 메뉴로 이동 하 여 **TestUniversalProject 호출**을 클릭 한 다음 **출력** 창에서 텍스트를 확인 합니다. 다음과 유사한 출력이 표시됩니다.

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>플랫폼 프로젝트 및 공유 프로젝트의 변경 내용 검색

1. 플랫폼 프로젝트의 경우와 마찬가지로 계층 및 프로젝트 이벤트를 사용 하 여 공유 프로젝트의 변경 내용을 검색할 수 있습니다. 그러나 공유 프로젝트의 프로젝트 항목은 표시 되지 않습니다. 즉, 공유 프로젝트 항목이 변경 될 때 특정 이벤트가 발생 하지 않습니다.

    프로젝트의 파일 이름을 바꿀 때 이벤트 시퀀스를 고려 합니다.

   1. 디스크에서 파일 이름이 변경 됩니다.

   2. 파일의 새 이름을 포함 하도록 프로젝트 파일이 업데이트 됩니다.

      계층 이벤트 (예: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> )는 일반적으로 **솔루션 탐색기**같이 UI에 표시 된 변경 내용을 추적 합니다. 계층 이벤트는 파일 이름 바꾸기 작업을 파일 삭제와 파일 추가로 구성 하는 것으로 간주 합니다. 그러나 보이지 않는 항목이 변경 되 면 계층 이벤트 시스템은 이벤트를 발생 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 하지만 이벤트는 발생 하지 않습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> . 따라서 플랫폼 프로젝트에서 파일의 이름을 바꾸면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 및가 모두 제공 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 되지만 공유 프로젝트에서 파일의 이름을 바꾸는 경우에만 표시 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 됩니다.

      프로젝트 항목의 변경 내용을 추적 하기 위해 DTE 프로젝트 항목 이벤트 (에 있음)를 처리할 수 있습니다 <xref:EnvDTE.ProjectItemsEventsClass> . 그러나 많은 수의 이벤트를 처리 하는 경우에서 이벤트를 처리 하는 더 나은 성능을 얻을 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> . 이 연습에서는 계층 이벤트 및 DTE 이벤트만 표시 합니다. 이 절차에서는 공유 프로젝트 및 플랫폼 프로젝트에 이벤트 수신기를 추가 합니다. 그런 다음 공유 프로젝트에서 한 파일의 이름을 바꾸고 플랫폼 프로젝트에서 다른 파일의 이름을 바꾸면 각 이름 바꾸기 작업에 대해 발생 하는 이벤트를 확인할 수 있습니다.

      이 절차에서는 공유 프로젝트 및 플랫폼 프로젝트에 이벤트 수신기를 추가 합니다. 그런 다음 공유 프로젝트에서 한 파일의 이름을 바꾸고 플랫폼 프로젝트에서 다른 파일의 이름을 바꾸면 각 이름 바꾸기 작업에 대해 발생 하는 이벤트를 확인할 수 있습니다.

2. 이벤트 수신기를 추가 합니다. 프로젝트에 새 클래스 파일을 추가 하 고 *HierarchyEventListener.cs*를 호출 합니다.

3. *HierarchyEventListener.cs* 파일을 열고 다음 using 지시문을 추가 합니다.

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. 클래스가을 `HierarchyEventListener` 구현 하도록 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> .

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>아래 코드에서와 같이의 멤버를 구현 합니다.

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

6. 동일한 클래스에서 DTE 이벤트에 대 한 또 다른 이벤트 처리기 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> 를 추가 합니다 .이 이벤트는 프로젝트 항목의 이름을 바꿀 때마다 발생 합니다.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. 계층 이벤트에 등록 합니다. 추적 하는 모든 프로젝트에 대해 별도로 등록 해야 합니다. 에 다음 코드를 추가 합니다 `ShowMessageBox` . 하나는 공유 프로젝트를 위한 것이 고 다른 하나는 플랫폼 프로젝트 중 하나입니다.

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

8. DTE 프로젝트 항목 이벤트에 등록 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> 합니다. 두 번째 수신기를 연결한 후 다음 코드를 추가 합니다.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. 공유 항목을 수정 합니다. 플랫폼 프로젝트에서는 공유 항목을 수정할 수 없습니다. 대신 이러한 항목의 실제 소유자 인 공유 프로젝트에서 수정 해야 합니다. 를 사용 하 여 공유 프로젝트의 해당 항목 ID를 가져와 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> 공유 항목의 전체 경로를 제공할 수 있습니다. 그런 다음 공유 항목을 수정할 수 있습니다. 변경 내용은 플랫폼 프로젝트로 전파 됩니다.

    > [!IMPORTANT]
    > 프로젝트 항목이 수정 되기 전에 공유 항목 인지 여부를 확인 해야 합니다.

     다음 메서드는 프로젝트 항목 파일의 이름을 수정 합니다.

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

10. 의 다른 모든 코드 뒤에이 메서드를 호출 `ShowMessageBox` 하 여 공유 프로젝트의 항목에 대 한 파일 이름을 수정 합니다. 공유 프로젝트에서 항목의 전체 경로를 가져오는 코드 뒤에이 코드를 삽입 합니다.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. 프로젝트를 빌드하고 실행합니다. 실험적 인스턴스에서 c # 유니버설 허브 앱을 만들고 **도구** 메뉴로 이동 하 여 **TestUniversalProject 호출**을 클릭 하 고 일반 출력 창에서 텍스트를 선택 합니다. 공유 프로젝트의 첫 번째 항목 이름 ( *app.xaml* 파일이 될 것으로 간주 됨)은 변경 해야 하며 이벤트가 발생 한 것을 확인 해야 합니다 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> . 이 경우 *.xaml* 의 이름을 바꾸면 *App.xaml.cs* 의 이름도 변경 되기 때문에 4 개의 이벤트 (각 플랫폼 프로젝트에 대해 2 개)가 표시 되어야 합니다. DTE 이벤트는 공유 프로젝트의 항목을 추적 하지 않습니다. 두 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 이벤트 (플랫폼 프로젝트 마다 하나씩)가 표시 되지만 이벤트는 표시 되지 않습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> .

12. 이제 플랫폼 프로젝트에서 파일 이름을 바꾸고, 발생 하는 이벤트의 차이를 확인할 수 있습니다. 를 호출한 후에 다음 코드를 추가 `ShowMessageBox` `ModifyFileName` 합니다.

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

13. 프로젝트를 빌드하고 실행합니다. 실험적 인스턴스에서 c # 유니버설 프로젝트를 만들고 **도구** 메뉴로 이동한 다음 **TestUniversalProject 호출**을 클릭 하 고 일반 출력 창에서 텍스트를 선택 합니다. 플랫폼 프로젝트의 파일 이름이 변경 되 면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 이벤트와 이벤트가 모두 표시 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> . 파일을 변경 해도 다른 파일은 변경 되지 않으며 플랫폼 프로젝트의 항목에 대 한 변경 내용이 어디에서 나 전파 되지 않기 때문에 각 이벤트는 하나만 있습니다.