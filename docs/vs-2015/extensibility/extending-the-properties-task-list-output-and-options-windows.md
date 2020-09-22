---
title: 속성, 작업 목록, 출력 및 옵션 창 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf42be1e62bfb4895d29a61fcadc221d5c14bec9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841731"
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>속성, 작업 목록, 출력 및 옵션 창 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 모든 도구 창에 액세스할 수 있습니다. 이 연습에서는 도구 창에 대 한 정보를 새 **옵션** 페이지 및 **속성** 페이지의 새 설정에 통합 하는 방법과 **작업 목록** 및 **출력** 창에 쓰는 방법을 보여 줍니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="create-an-extension-with-a-tool-window"></a>도구 창을 사용 하 여 확장 만들기  
  
1. VSIX 템플릿을 사용 하 여 **TodoList** 이라는 프로젝트를 만들고 **TodoWindow**라는 사용자 지정 도구 창 항목 템플릿을 추가 합니다.  
  
    > [!NOTE]
    > 도구 창을 사용 하 여 확장을 만드는 방법에 대 한 자세한 내용은 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요.  
  
## <a name="set-up-the-tool-window"></a>도구 창 설정  
 새 ToDo 항목을 입력할 텍스트 상자를 추가 하 고, 목록에 새 항목을 추가 하는 단추를 추가 하 고, 목록에 항목을 표시 하는 목록 상자를 추가 합니다.  
  
1. TodoWindow에서 UserControl의 Button, TextBox 및 StackPanel 컨트롤을 삭제 합니다.  
  
    > [!NOTE]
    > 이는 이후 단계에서 다시 사용 하는 **button1_Click** 이벤트 처리기를 삭제 하지 않습니다.  
  
2. **도구 상자**의 **모든 WPF 컨트롤** 섹션에서 **캔버스** 컨트롤을 그리드로 끌어 옵니다.  
  
3. **텍스트 상자**, **단추**및 **목록 상자** 를 캔버스로 끌어다 놓습니다. 텍스트 상자와 단추가 같은 수준에 있도록 요소를 정렬 하 고 ListBox는 아래 그림과 같이 해당 창의 나머지 부분을 채웁니다.  
  
     ![완료된 도구 창](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")  
  
4. XAML 창에서 단추를 찾고 콘텐츠 속성을 **추가**로 설정 합니다. 특성을 추가 하 여 단추 이벤트 처리기를 단추 컨트롤에 다시 연결 `Click="button1_Click"` 합니다. Canvas 블록은 다음과 같습니다.  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>생성자 사용자 지정  
  
1. TodoWindowControl.xaml.cs 파일에서 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using System;  
    ```  
  
2. TodoWindow에 대 한 공용 참조를 추가 하 고 TodoWindowControl 생성자가 TodoWindow 매개 변수를 사용 하도록 합니다. 코드는 다음과 같습니다.  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3. TodoWindow.cs에서 TodoWindow 매개 변수를 포함 하도록 TodoWindowControl 생성자를 변경 합니다. 코드는 다음과 같습니다.  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>옵션 페이지 만들기  
 사용자가 도구 창에 대 한 설정을 변경할 수 있도록 **옵션** 대화 상자에 페이지를 제공할 수 있습니다. 옵션 페이지를 만들려면 옵션과 TodoListPackage.cs 또는 TodoListPackage 파일의 항목을 설명 하는 클래스가 모두 필요 합니다.  
  
1. `ToolsOptions.cs`(이)라는 클래스를 추가합니다. ToolsOptions 클래스를에서 상속 하도록 <xref:Microsoft.VisualStudio.Shell.DialogPage> 합니다.  
  
   ```csharp  
   class ToolsOptions : DialogPage  
   {  
   }  
   ```  
  
2. 다음 using 문을 추가합니다.  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
3. 이 연습의 옵션 페이지에서는 DaysAhead 라는 하나의 옵션만 제공 합니다. **DaysAhead** 라는 private 필드와 **daysAhead** 라는 속성을 ToolsOptions 클래스에 추가 합니다.  
  
   ```csharp  
   private double daysAhead;  
  
   public double DaysAhead  
   {  
       get { return daysAhead; }  
       set { daysAhead = value; }  
   }  
   ```  
  
   이제 프로젝트에서이 옵션 페이지를 인식 하도록 해야 합니다.  
  
#### <a name="make-the-options-page-available-to-users"></a>사용자가 옵션 페이지를 사용할 수 있도록 설정  
  
1. TodoWindowPackage.cs에서 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> TodoWindowPackage 클래스에를 추가 합니다.  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2. ProvideOptionPage 생성자의 첫 번째 매개 변수는 이전에 만든 ToolsOptions 클래스의 형식입니다. 두 번째 매개 변수인 "ToDo"는 **옵션** 대화 상자의 범주 이름입니다. 세 번째 매개 변수인 "General"은 옵션 페이지를 사용할 수 있는 **옵션** 대화 상자의 하위 범주 이름입니다. 다음 두 매개 변수는 문자열에 대 한 리소스 Id입니다. 첫 번째는 범주의 이름이 고 두 번째는 하위 범주의 이름입니다. Final 매개 변수는 자동화를 사용 하 여이 페이지에 액세스할 수 있는지 여부를 결정 합니다.  
  
     사용자가 옵션 페이지를 열면 다음 그림과 같이 나타납니다.  
  
     ![옵션 페이지](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     **ToDo** 및 하위 범주 **일반**범주를 확인 합니다.  
  
## <a name="make-data-available-to-the-properties-window"></a>속성 창에서 데이터를 사용할 수 있도록 설정  
 할 일 목록에 개별 항목에 대 한 정보를 저장 하는 TodoItem 라는 클래스를 만들어 사용할 수 있는 목록 정보를 만들 수 있습니다.  
  
1. `TodoItem.cs`(이)라는 클래스를 추가합니다.  
  
     사용자가 도구 창을 사용할 수 있는 경우 ListBox의 항목은 TodoItems로 표시 됩니다. 사용자가 목록 상자에서 이러한 항목 중 하나를 선택 하면 **속성** 창에 항목에 대 한 정보가 표시 됩니다.  
  
     **속성** 창에서 데이터를 사용할 수 있도록 하려면 및 라는 두 가지 특수 한 특성이 있는 공용 속성으로 데이터를 변환 합니다 `Description` `Category` . `Description`**속성** 창의 맨 아래에 표시 되는 텍스트입니다. `Category`**속성 창이** **항목별** 보기에 표시 될 때 속성이 표시 되는 위치를 결정 합니다. 다음 그림에서 **속성** 창은 **범주화** 된 보기 이며 **ToDo 필드** 범주의 **이름** 속성을 선택 하 고 **이름** 속성에 대 한 설명이 창의 아래쪽에 표시 됩니다.  
  
     ![속성 창](../extensibility/media/t5properties.png "T5Properties")  
  
2. TodoItem.cs 파일에 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3. `public`액세스 한정자를 클래스 선언에 추가 합니다.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Name 및 DueDate 라는 두 속성을 추가 합니다. UpdateList () 및 CheckForErrors ()는 나중에 수행 합니다.  
  
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
  
4. 사용자 정의 컨트롤에 대 한 개인 참조를 추가 합니다. 사용자 정의 컨트롤과이 ToDo 항목의 이름을 사용 하는 생성자를 추가 합니다. DaysAhead에 대 한 값을 찾기 위해 옵션 페이지 속성을 가져옵니다.  
  
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
  
5. 클래스의 인스턴스는 `TodoItem` listbox에 저장 되 고 listbox는 함수를 호출 하므로 함수를 `ToString` 오버 로드 해야 합니다 `ToString` . 생성자 뒤에 클래스의 끝 앞에 TodoItem.cs에 다음 코드를 추가 합니다.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6. TodoWindowControl.xaml.cs에서 및 메서드에 대 한 TodoWindowControl 클래스에 스텁 메서드를 `CheckForError` 추가 `UpdateList` 합니다. ProcessDialogChar 뒤와 파일 끝 앞에 배치 합니다.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError`메서드는 부모 개체에서 이름이 같은 메서드를 호출 하 고,이 메서드는 오류가 발생 했는지 확인 하 고 올바르게 처리 합니다. `UpdateList`메서드는 부모 컨트롤의 ListBox를 업데이트 `Name` 합니다. `DueDate` 이 클래스의 및 속성이 변경 되 면 메서드가 호출 됩니다. 나중에 구현 됩니다.  
  
## <a name="integrate-into-the-properties-window"></a>속성 창에 통합  
 이제 **속성** 창에 연결 되는 ListBox를 관리 하는 코드를 작성 합니다.  
  
 텍스트 상자를 읽고 TodoItem을 만든 다음 ListBox에 추가 하려면 단추 클릭 처리기를 변경 해야 합니다.  
  
1. 기존 함수를 `button1_Click` 새 TodoItem을 만들고 ListBox에 추가 하는 코드로 바꿉니다. 이 메서드는 나중에 정의 되는 선택 영역 ()을 호출 합니다.  
  
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
  
2. 디자인 뷰에서 ListBox 컨트롤을 선택 합니다. **속성** 창에서 **이벤트 처리기** 단추를 클릭 하 고 selectionchanged 이벤트를 찾습니다. 텍스트 상자에 **listBox_SelectionChanged**을 입력 합니다. 이렇게 하면 SelectionChanged 처리기에 대 한 스텁이 추가 되어 이벤트에 할당 됩니다.  
  
3. 에서의 선택 () 메서드를 구현 합니다. 서비스를 가져와야 하므로 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> TodoWindowControl에서 액세스할 수 있도록 해야 합니다 <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> . TodoWindow 클래스에 다음 메서드를 추가 합니다.  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4. TodoWindowControl.xaml.cs에 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5. SelectionChanged 처리기를 다음과 같이 입력 합니다.  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6. 이제 속성 창과의 통합을 제공 하는 지 **속성** 선택 함수를 채웁니다. 이 함수는 사용자가 목록 상자에 항목을 추가 하거나 ListBox의 항목을 클릭할 때 호출 됩니다. ListBox의 내용을 SelectionContainer에 추가 하 고 SelectionContainer를 **속성** 창의 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 이벤트 처리기에 전달 합니다. 영역 선택 서비스는 UI (사용자 인터페이스)에서 선택한 개체를 추적 하 고 해당 속성을 표시 합니다.  
  
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
  
     이제 **속성** 창에서 사용할 수 있는 클래스가 있으므로 **속성** 창을 도구 창과 통합할 수 있습니다. 사용자가 도구 창에서 ListBox의 항목을 클릭 하면 **속성** 창이 적절 하 게 업데이트 됩니다. 마찬가지로 사용자가 **속성** 창에서 할 일 항목을 변경 하는 경우 연결 된 항목을 업데이트 해야 합니다.  
  
7. 이제 TodoWindowControl.xaml.cs에 나머지 UpdateList 함수 코드를 추가 합니다. ListBox에서 수정 된 TodoItem를 삭제 하 고 다시 추가 해야 합니다.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8. 코드를 테스트 합니다. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다.  
  
9. **도구/옵션** 페이지를 엽니다. 왼쪽 창에 ToDo 범주가 표시 됩니다. 범주는 사전순으로 나열 되므로 Ts 아래에서 확인 합니다.  
  
10. Todo 옵션 페이지에서 DaysAhead 속성이 **0**으로 설정 된 것을 볼 수 있습니다. **2**로 변경 합니다.  
  
11. 보기/기타 창 메뉴에서 **TodoWindow**을 엽니다. 텍스트 상자에 **EndDate** 를 입력 하 고 **추가**를 클릭 합니다.  
  
12. 목록 상자에 오늘 날짜를 이틀 이상 표시 해야 합니다.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>출력 창 및 항목에 텍스트를 작업 목록에 추가 합니다.  
 **작업 목록**에 대해 task 형식의 새 개체를 만든 다음 해당 add 메서드를 호출 하 여 해당 작업 개체를 **작업 목록** 에 추가 합니다. **출력** 창에 쓰려면 해당 getpane 메서드를 호출 하 여 창 개체를 가져온 다음 pane 개체의 outputstring 메서드를 호출 합니다.  
  
1. TodoWindowControl.xaml.cs의 `button1_Click` 메서드에서 코드를 추가 하 여 **출력** 창의 **일반** 창 (기본값)을 가져오고 여기에 씁니다. 메서드는 다음과 같습니다.  
  
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
  
2. 작업 목록에 항목을 추가 하려면 TodoWindowControl 클래스에 중첩 클래스를 추가 하기 위해가 필요 합니다. 중첩 된 클래스는에서 파생 되어야 <xref:Microsoft.VisualStudio.Shell.TaskProvider> 합니다. TodoWindowControl 클래스의 끝에 다음 코드를 추가 합니다.  
  
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
  
3. 그런 다음 TodoTaskProvider에 대 한 개인 참조와 CreateProvider () 메서드를 TodoWindowControl 클래스에 추가 합니다. 코드는 다음과 같습니다.  
  
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
  
4. 작업 목록을 지우는 ClearError () 및 작업 목록 항목을 TodoWindowControl 클래스에 추가 하는 ReportError ()를 추가 합니다.  
  
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
  
5. 이제 다음과 같이 CheckForErrors 메서드를 구현 합니다.  
  
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
  
## <a name="trying-it-out"></a>사용해 보십시오.  
  
1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다.  
  
2. TodoWindow (**View/Other Windows/TodoWindow**)를 엽니다.  
  
3. 텍스트 상자에 항목을 입력 한 다음 **추가**를 클릭 합니다.  
  
     오늘 1 일 후의 기한 날짜는 목록 상자에 추가 됩니다. 오류가 생성 되지 않으며 **작업 목록** (**보기/작업 목록**)에 항목이 없어야 합니다.  
  
4. 이제 **도구/옵션/ToDo** 페이지의 설정을 **2** 에서 다시 **0**으로 변경 합니다.  
  
5. **TodoWindow** 에 다른 항목을 입력 한 다음 **추가** 를 다시 클릭 합니다. 그러면 오류가 트리거되고 **작업 목록**항목도 트리거됩니다.  
  
     항목을 추가할 때 초기 날짜는 이제 2 일을 더한 값으로 설정 됩니다.  
  
6. **보기** 메뉴에서 **출력** 을 클릭 하 여 **출력** 창을 엽니다.  
  
     항목을 추가할 때마다 메시지는 **작업 목록** 창에 표시 됩니다.  
  
7. 목록 상자에 있는 항목 중 하나를 클릭 합니다.  
  
     **속성** 창에는 항목에 대 한 두 개의 속성이 표시 됩니다.  
  
8. 속성 중 하나를 변경 하 고 enter 키를 누릅니다.  
  
     항목이 ListBox에서 업데이트 됩니다.
