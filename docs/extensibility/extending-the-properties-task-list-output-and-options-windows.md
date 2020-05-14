---
title: 속성, 작업 목록, 출력, 옵션 창 확장
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711632"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>속성, 작업 목록, 출력 및 옵션 창 확장
Visual Studio의 모든 도구 창에 액세스할 수 있습니다. 이 연습에서는 도구 창에 대한 정보를 새 **옵션** 페이지와 **속성** 페이지의 새 설정에 통합하는 방법과 **작업 목록** 및 **출력** 창에 쓰는 방법을 보여 줍니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-an-extension-with-a-tool-window"></a>도구 창을 사용하여 확장 만들기

1. VSIX 템플릿을 사용하여 **TodoList라는** 프로젝트를 만들고 TodoWindow 라는 사용자 지정 도구 창 항목 **템플릿을 추가합니다.**

    > [!NOTE]
    > 도구 창을 사용하여 확장을 만드는 자세한 내용은 [도구 창을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오.

## <a name="set-up-the-tool-window"></a>도구 창 설정
 새 할 일 항목을 입력할 TextBox, 목록에 새 항목을 추가할 단추 및 목록에 항목을 표시하는 ListBox를 추가합니다.

1. *TodoWindow.xaml에서*사용자 컨트롤에서 단추, 텍스트 상자 및 스택패널 컨트롤을 삭제합니다.

    > [!NOTE]
    > 이렇게 해도 **button1_Click** 이벤트 처리기가 삭제되지 않으므로 이후 단계에서 다시 사용할 수 있습니다.

2. **도구 상자의** **모든 WPF 컨트롤** 섹션에서 **캔버스** 컨트롤을 그리드로 끕니다.

3. 텍스트 **상자,** **단추**및 **목록 상자를** 캔버스로 끕니다. 텍스트 상자와 버튼이 같은 수준에 있도록 요소를 정렬하고 ListBox는 아래 그림과 같이 아래 창의 나머지 부분을 채웁니다.

     ![완료된 도구 창](../extensibility/media/t5-toolwindow.png "T5-툴윈도우")

4. XAML 창에서 단추를 찾아 해당 콘텐츠 속성을 **추가하도록**설정합니다. 특성을 추가하여 단추 이벤트 처리기를 Button `Click="button1_Click"` 컨트롤에 다시 연결합니다. 캔버스 블록은 다음과 같아야 합니다.

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>생성자 사용자 지정

1. *TodoWindowControl.xaml.cs* 파일에서 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using System;
    ```

2. TodoWindow에 대한 공용 참조를 추가하고 TodoWindowControl 생성자가 TodoWindow 매개 변수를 사용하도록 합니다. 코드는 다음과 같아야 합니다.

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. *TodoWindow.cs*TodoWindow Control 생성기를 TodoWindow 매개 변수를 포함하도록 변경합니다. 코드는 다음과 같아야 합니다.

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>옵션 만들기 페이지
 사용자가 도구 창에 대한 설정을 변경할 수 있도록 **옵션** 대화 상자에 페이지를 제공할 수 있습니다. 옵션 페이지를 만들려면 옵션을 설명하는 클래스와 *TodoListPackage.cs* 또는 *TodoListPackage.vb* 파일의 항목이 모두 필요합니다.

1. `ToolsOptions.cs`(이)라는 클래스를 추가합니다. 클래스를 `ToolsOptions` <xref:Microsoft.VisualStudio.Shell.DialogPage>상속합니다.

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. 다음 using 지시문을 추가합니다.

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. 이 연습의 옵션 페이지에는 DaysAhead라는 하나의 옵션만 제공됩니다. **daysAhead라는** 개인 필드와 **DaysAhead라는** 속성을 `ToolsOptions` 클래스에 추가합니다.

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   이제 이 옵션 페이지를 프로젝트에 알려야 합니다.

### <a name="make-the-options-page-available-to-users"></a>사용자가 옵션 페이지를 사용할 수 있도록 만들기

1. *TodoWindowPackage.cs*클래스에 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a를 `TodoWindowPackage` 추가합니다.

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. ProvideOptionPage 생성자의 첫 번째 매개 변수는 `ToolsOptions`이전에 만든 클래스의 형식입니다. 두 번째 매개 변수인 "Do"는 **옵션** 대화 상자의 범주 이름입니다. 세 번째 매개 변수인 "일반"은 옵션 페이지를 사용할 수 있는 **옵션** 대화 상자의 하위 범주의 이름입니다. 다음 두 매개 변수는 문자열에 대한 리소스 아이디입니다. 첫 번째는 범주의 이름이고 두 번째는 하위 범주의 이름입니다. 최종 매개 변수는 자동화를 사용하여 이 페이지에 액세스할 수 있는지 여부를 결정합니다.

     사용자가 옵션 페이지를 열면 다음 그림과 유사해야 합니다.

     ![옵션 페이지](../extensibility/media/t5optionspage.gif "T5옵션페이지")

     **할 일** 범주와 하위 범주 **일반**.

## <a name="make-data-available-to-the-properties-window"></a>속성 창에서 데이터를 사용할 수 있도록 만들기
 할 일 목록에 개별 항목에 대한 정보를 `TodoItem` 저장하는 클래스를 만들어 할 일 목록 정보를 사용할 수 있도록 할 수 있습니다.

1. `TodoItem.cs`(이)라는 클래스를 추가합니다.

     사용자가 도구 창을 사용할 수 있으면 ListBox의 항목은 TodoItems로 표시됩니다. 사용자가 ListBox에서 이러한 항목 중 하나를 선택하면 **속성** 창에 항목에 대한 정보가 표시됩니다.

     **속성** 창에서 데이터를 사용할 수 있도록 하려면 데이터를 두 개의 특수 `Description` 특성이 있는 공용 속성으로 변환 하 고 `Category`. `Description`은 **속성** 창의 맨 아래에 나타나는 텍스트입니다. `Category`속성 창이 **분류된** 보기에 표시될 때 **속성이** 표시될 위치를 결정합니다. 다음 그림에서는 **속성** 창이 **분류된** 뷰에 있고, **할 일 필드** 범주의 **Name** 속성이 선택되고 **Name** 속성에 대한 설명이 창 아래쪽에 표시됩니다.

     ![속성 창](../extensibility/media/t5properties.png "T5속성")

2. *TodoItem.cs* 파일을 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. 클래스 `public` 선언에 액세스 수정자를 추가합니다.

    ```csharp
    public class TodoItem
    {
    }
    ```

     두 속성을 `Name` 추가하고 `DueDate`. 우리는 `CheckForErrors()` 나중에 할 `UpdateList()` 수 있습니다.

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. 사용자 컨트롤에 개인 참조를 추가합니다. 사용자 컨트롤을 수행하는 생성자와 이 Do 항목의 이름을 추가합니다. 에 대한 `daysAhead`값을 찾으려면 옵션 페이지 속성을 가져옵니다.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. `TodoItem` 클래스의 인스턴스는 ListBox에 저장되고 ListBox가 함수를 `ToString` 호출하므로 함수를 `ToString` 오버로드해야 합니다. 생성자 후 와 클래스가 끝나기 전에 다음 코드를 추가하여 *TodoItem.cs*추가합니다.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. *TodoWindowControl.xaml.cs* `CheckForError` 및 `UpdateList` 메서드에 대한 `TodoWindowControl` 스텁 메서드를 클래스에 추가합니다. ProcessDialogChar 후 파일이 끝나기 전에 넣습니다.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     메서드는 `CheckForError` 부모 개체에 이름이 같은 메서드를 호출 하고 해당 메서드는 오류가 발생 했는지 여부를 확인 하 고 올바르게 처리 합니다. 메서드는 `UpdateList` 상위 컨트롤에서 ListBox를 업데이트합니다. 메서드는 이 `Name` 클래스의 `DueDate` 및 속성이 변경될 때 호출됩니다. 나중에 구현됩니다.

## <a name="integrate-into-the-properties-window"></a>속성 창에 통합
 이제 **속성** 창에 연결될 ListBox를 관리하는 코드를 작성합니다.

 단추 클릭 처리기를 변경하여 TextBox를 읽고 TodoItem을 만들고 ListBox에 추가해야 합니다.

1. 기존 `button1_Click` 함수를 새 TodoItem을 만들고 ListBox에 추가하는 코드로 바꿉니다. 나중에 `TrackSelection()`정의될 호출합니다.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. 디자인 보기에서 ListBox 컨트롤을 선택합니다. **속성** 창에서 **이벤트 처리기 단추를** 클릭 하 고 **선택 변경** 된 이벤트를 찾을 수 있습니다. 텍스트 상자에 **listBox_SelectionChanged**입력합니다. 이렇게 하면 SelectionChanged 처리기에 대한 스텁이 추가되고 이벤트에 할당됩니다.

3. `TrackSelection()` 메서드를 구현합니다. 서비스를 받아야 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 하므로 TodoWindowControl에서 <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> 액세스할 수 있도록 해야 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> `TodoWindow` 클래스에 다음 메서드를 추가합니다.

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. 지시문을 사용하여 다음을 추가하여 *TodoWindowControl.xaml.cs.*

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. 다음과 같이 선택 변경 처리기를 입력합니다.

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. 이제 **속성** 창과의 통합을 제공하는 TrackSelection 함수를 입력합니다. 이 함수는 사용자가 ListBox에 항목을 추가하거나 ListBox에서 항목을 클릭할 때 호출됩니다. ListBox의 내용을 선택 컨테이너에 추가하고 선택 컨테이너를 **속성** 창의 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 이벤트 처리기에 전달합니다. TrackSelection 서비스는 사용자 인터페이스(UI)에서 선택된 개체를 추적하고 해당 속성을 표시합니다.

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     **속성** 창에서 사용할 수 있는 클래스가 있으므로 **속성** 창을 도구 창과 통합할 수 있습니다. 사용자가 도구 창에서 ListBox에서 항목을 클릭하면 **속성** 창이 그에 따라 업데이트되어야 합니다. 마찬가지로 사용자가 **속성** 창에서 Do 항목을 변경하면 관련 항목이 업데이트되어야 합니다.

7. 이제 *TodoWindowControl.xaml.cs*UpdateList 함수 코드의 나머지 부분을 추가합니다. ListBox에서 수정된 TodoItem을 삭제하고 다시 추가해야 합니다.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. 코드를 테스트합니다. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타나야 합니다.

9. **도구** > 옵션 페이지를**엽니다.** 왼쪽 창에 할 일 범주가 표시됩니다. 범주는 알파벳 순으로 나열되므로 Ts 아래를 보십시오.

10. **Todo** 옵션 페이지에서 속성이 `DaysAhead` **0으로**설정되어 있습니다. **2로**변경합니다.

11. 보기 **/ 기타 Windows** 메뉴에서 **TodoWindow를**엽니다. 텍스트 상자에 **EndDate를** 입력하고 **추가**를 클릭합니다.

12. 목록 상자에 오늘보다 이틀 늦게 날짜가 표시됩니다.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>출력 창에 텍스트 추가 및 작업 목록에 항목
 작업 **목록의**경우 작업 형식의 새 개체를 만든 다음 해당 메서드를 호출하여 **작업 목록에** 해당 작업 개체를 `Add` 추가합니다. **Output** 창에 쓰려면 해당 `GetPane` 메서드를 호출하여 창 개체를 얻은 `OutputString` 다음 창 개체의 메서드를 호출합니다.

1. *TodoWindowControl.xaml.cs* `button1_Click` 메서드에서 코드를 추가하여 **출력** 창(기본값)의 **일반** 창을 얻고 쓰기합니다. 메서드는 다음과 같습니다.

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. 작업 목록에 항목을 추가하려면 TodoWindowControl 클래스에 중첩된 클래스를 추가해야 합니다. 중첩된 클래스는 에서 <xref:Microsoft.VisualStudio.Shell.TaskProvider>파생되어야 합니다. 클래스의 끝에 다음 코드를 `TodoWindowControl` 추가합니다.

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. 다음으로 클래스에 개인 `TodoTaskProvider` 참조와 메서드를 `CreateProvider()` `TodoWindowControl` 추가합니다. 코드는 다음과 같아야 합니다.

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. 작업 `ClearError()`목록을 지우는 및 작업 `ReportError()`목록에 항목을 추가하는 을 클래스에 `TodoWindowControl` 추가합니다.

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. 이제 다음과 `CheckForErrors` 같이 메서드를 구현합니다.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>체험

1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

2. **TodoWindow를** 엽니다(다른**Windows** > **토도윈도우****보기).** > 

3. 텍스트 상자에 무언가를 입력한 다음 **추가 를**클릭합니다.

     오늘 이후 2일 후의 기한이 목록 상자에 추가됩니다. 오류가 생성되지 않으며 **작업 목록(작업** **목록****보기)에** > 항목이 없어야 합니다.

4. 이제 **도구** > **옵션** > **할 일** 페이지의 설정을 **2에서** **0으로**변경합니다.

5. **TodoWindow에서** 다른 내용을 입력한 다음 다시 **추가를** 클릭합니다. 이렇게 하면 오류와 **작업 목록의**항목도 트리거됩니다.

     항목을 추가하면 초기 날짜가 이제 2일로 설정됩니다.

6. **보기** 메뉴에서 **출력을** 클릭하여 출력 창을 **엽니다.**

     항목을 추가할 때마다 **작업 목록** 창에 메시지가 표시됩니다.

7. ListBox의 항목 중 하나를 클릭합니다.

     **속성** 창에는 항목에 대한 두 속성이 표시됩니다.

8. 속성 중 하나를 변경한 다음 **Enter**를 누릅니다.

     항목이 ListBox에서 업데이트됩니다.
