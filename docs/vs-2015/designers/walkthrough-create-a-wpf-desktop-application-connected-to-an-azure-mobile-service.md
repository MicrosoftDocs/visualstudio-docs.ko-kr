---
title: '연습: Azure 모바일 서비스에 연결된 WPF 데스크톱 애플리케이션 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 624fffb9c86a7ad874f27797dfd5251c8585870f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664020"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>연습: Azure 모바일 서비스에 연결된 WPF 데스크톱 애플리케이션 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WPF(Windows Presentation Foundation)를 사용하여 Azure 모바일 서비스를 통해 데이터를 저장 및 제공하는 최신 데스크톱 애플리케이션을 신속하게 만들 수 있습니다.

## <a name="prerequisites"></a><a name="Requirements"></a> 필수 조건
 이 연습을 완료하려면 다음이 필요합니다.

- Visual Studio 2015 – WPF 개발을 지원하는 버전.

- 활성 Microsoft Azure 계정.

  - [여기](https://azure.microsoft.com/pricing/free-trial/)서 무료 평가판 계정을 등록할 수 있습니다.

  - [MSDN 구독자 혜택](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F)을 활성화할 수 있습니다. MSDN 구독은 유료 Azure 서비스에 사용할 수 있는 크레딧을 매달 제공합니다.

## <a name="create-a-project-and-add-references"></a>프로젝트 만들기 및 참조 추가
 첫 번째 단계는 WPF 프로젝트를 만들고 Azure 모바일 서비스에 연결할 수 있는 NuGet 패키지를 추가하는 것입니다.

#### <a name="to-create-the-project"></a>프로젝트를 만들려면

1. 메뉴 모음에서 **파일**, **새로 만들기**, **프로젝트**를 차례로 선택합니다.

2. **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 확장하고 **Windows** 노드를 선택한 다음 **Windows** 노드를 확장하고 **클래식 바탕 화면** 노드를 선택합니다.

3. 템플릿 목록에서 **WPF 애플리케이션** 템플릿을 선택합니다.

4. **이름** 텍스트 상자에 `WPFQuickStart`를 입력하고 **확인** 단추를 선택합니다.

     프로젝트가 생성되고 프로젝트 파일이 **솔루션 탐색기**에 추가된 다음 **MainWindow.xaml** 이라는 기본 애플리케이션 창에 대한 디자이너가 표시됩니다.

#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Microsoft Azure Mobile Services SDK에 대한 참조를 추가하려면

1. **솔루션 탐색기**에서 **참조** 노드에 대 한 바로 가기 메뉴를 열고 **NuGet 패키지 관리**를 선택 합니다.

2. **NuGet 패키지 관리자**에서 **검색** 필드를 선택하고 `mobileservices`를 입력합니다.

3. 왼쪽 창에서 **WindowsAzure.MobileServices**를 선택한 다음 오른쪽 창에서 **설치** 단추를 선택합니다.

    > [!NOTE]
    > **미리 보기** 대화 상자가 나타나면 제안된 변경 내용을 검토한 다음 **확인** 단추를 선택합니다.

4. **라이선스 승인** 대화 상자에서 사용 조건을 검토한 다음 **동의함** 단추를 선택하여 수락합니다.

     필요한 참조가 **솔루션 탐색기**에 추가됩니다.

    > [!NOTE]
    > 사용 조건에 동의 하지 않는 경우 **거부** 단추를 선택 합니다. 연습의 나머지 부분을 완료할 수 없습니다.

## <a name="create-the-user-interface"></a>사용자 인터페이스 만들기
 다음 단계는 애플리케이션에 대한 사용자 인터페이스를 만드는 것입니다. 먼저 두 개의 창이 나란히 표시되는 표준 레이아웃을 표시하는 재사용 가능한 사용자 정의 컨트롤을 만듭니다. 주 애플리케이션 창에 사용자 정의 컨트롤을 추가하고 데이터를 입력 및 표시하는 컨트롤을 추가한 다음 모바일 서비스 백 엔드와의 상호 작용을 정의하는 일부 코드를 작성합니다.

#### <a name="to-add-a-user-control"></a>사용자 컨트롤을 추가하려면

1. **솔루션 탐색기**에서 **WPFQuickStart** 노드의 바로 가기 메뉴를 열고 **추가**, **새 폴더**를 차례로 선택합니다.

2. 폴더 이름을 `Common`서 무료 평가판 계정을 등록할 수 있습니다.

3. **공통** 폴더에 대한 바로 가기 메뉴를 열고 **추가**, **사용자 정의 컨트롤**을 선택합니다.

4. **새 항목 추가** 대화 상자에서 이름 필드를 선택하고 `QuickStartTask`를 입력한 후 **추가** 단추를 선택합니다.

     사용자 정의 컨트롤이 프로젝트에 추가되고 **QuickStartTask.xaml** 파일이 디자이너에서 열립니다.

5. 디자이너의 아래쪽 창에서 `<Grid>` 및 `</Grid>` 태그를 선택하고 다음 XAML 코드로 바꿉니다.

    ```xaml
    <Grid VerticalAlignment="Top">
            <StackPanel Orientation="Horizontal">
                <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">
                    <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>
                </Border>
                <StackPanel>
                    <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />
                    <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />
                </StackPanel>
            </StackPanel>
        </Grid>
    ```

     이 XAML 코드는 번호, 제목 및 설명 필드에 자리 표시자를 사용하여 재사용할 수 있는 레이아웃을 만듭니다. 런타임에 자리 표시자는 다음 그림과 같이 텍스트로 대체될 수 있습니다.

     ![QuickStartTask 사용자 정의 컨트롤](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")

6. **솔루션 탐색기**에서 **QuickStartTask.xaml** 노드를 확장하고 **QuickStartTask.xaml.cs** 또는 **QuickStartTask.xaml.vb** 파일을 엽니다.

7. 코드 편집기에서 `namespace WPFQuickStart.Common` (C#) 네임스페이스 또는 `Public Class QuickStartTask` (VB) 메서드를 다음 코드로 바꿉니다.

    ```csharp
    namespace WPFQuickStart.Common
    {
        /// <summary>
        /// Interaction logic for QuickStartTask.xaml
        /// </summary>
        public partial class QuickStartTask : UserControl
        {
            public QuickStartTask()
            {
                this.InitializeComponent();
                this.DataContext = this;
            }

            public int Number
            {
                get { return (int)GetValue(NumberProperty); }
                set { SetValue(NumberProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty NumberProperty =
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));

            public string Title
            {
                get { return (string)GetValue(TitleProperty); }
                set { SetValue(TitleProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty TitleProperty =
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));

            public string Description
            {
                get { return (string)GetValue(DescriptionProperty); }
                set { SetValue(DescriptionProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty DescriptionProperty =
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));
        }
    }
    ```

    ```vb
    Partial Public Class QuickStartTask
            Inherits UserControl

            Public Sub New()
                Me.InitializeComponent()
                Me.DataContext = Me
            End Sub

            Public Property Number() As Integer
                Get
                    Return CInt(Fix(GetValue(NumberProperty)))
                End Get
                Set(ByVal value As Integer)
                    SetValue(NumberProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))

            Public Property Title() As String
                Get
                    Return CStr(GetValue(TitleProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(TitleProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))

            Public Property Description() As String
                Get
                    Return CStr(GetValue(DescriptionProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(DescriptionProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))
        End Class
    ```

     이 코드는 종속성 속성을 사용하여 런타임에 번호, 제목 및 설명 필드의 값을 설정합니다.

8. 메뉴 모음에서 **빌드**, **WPFQuickStart 빌드** 를 선택하여 사용자 정의 컨트롤을 빌드합니다.

#### <a name="to-create-and-modify-the-main-window"></a>주 창을 만들고 수정하려면

1. **솔루션 탐색기**에서 **MainWindow.xaml** 파일을 엽니다.

2. **중요**. 이 단계는 C#에만 해당합니다. Visual Basic을 사용하는 경우 다음 단계로 건너뜁니다. 디자이너의 아래쪽 창에서 `xmlns:local=”clr-namespace:WPFQuickStart”` 줄을 찾아 다음 XAML 코드로 바꿉니다.

    ```xaml
    xmlns:local=”clr-namespace:WPFQuickStart.Common”
    ```

3. **속성** 창에서 **Common** 범주 노드를 확장하고 **Title** 속성을 선택한 다음 `WPF Todo List` 를 입력하고 **Enter** 키를 누릅니다.

     XAML 창의 **Title** 요소가 새 값과 일치하도록 변경됩니다. XAML 창 또는 **속성** 창에서 XAML 속성을 수정할 수 있으며 변경 내용이 동기화됩니다.

4. XAML 창에서 **Height** 요소의 값을 `768`로 설정하고 **Width** 속성의 값을 `1280`서 무료 평가판 계정을 등록할 수 있습니다.

     이러한 요소는 **속성** 창의 **레이아웃** 범주에 있는 **Height** 및 **Width** 속성에 해당합니다.

5. `<Grid>` 및 `</Grid>` 태그를 선택하고 다음 XAML 코드로 바꿉니다.

    ```xaml
    <Grid>

            <Grid Margin="50,50,10,10">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="*" />
                </Grid.ColumnDefinitions>
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="*" />
                </Grid.RowDefinitions>

                <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">
                    <StackPanel>
                        <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>
                        <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>
                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1">
                    <StackPanel>

                        <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />

                        <StackPanel Orientation="Horizontal" Margin="72,0,0,0">
                            <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>
                            <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>
                        </StackPanel>

                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1" Grid.Column="1">
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto" />
                        <RowDefinition />
                    </Grid.RowDefinitions>
                    <StackPanel>
                        <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />
                        <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>
                    </StackPanel>

                    <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">
                        <ListView.ItemTemplate>
                            <DataTemplate>
                                <StackPanel Orientation="Horizontal">
                                    <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>
                                </StackPanel>
                            </DataTemplate>
                        </ListView.ItemTemplate>
                    </ListView>

                </Grid>

            </Grid>
        </Grid>
    ```

     디자인 창에 변경 내용이 반영됩니다. **도구 상자** 창에서 컨트롤을 추가하고 **속성** 창에서 속성을 설정하여 사용자 인터페이스를 정의할 수도 있습니다. 디자이너에서 수행할 수 있는 모든 작업은 XAML 코드로 수행할 수 있으며, 그 반대의 경우도 마찬가지입니다.

     이때 디자인은 다음 그림과 같아야 합니다.

     ![디자이너의 주 창](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")

    > [!NOTE]
    > 다음 몇 가지 절차를 수행하는 동안 **오류 목록** 에 오류가 표시될 수도 있습니다(열려 있는 경우). 걱정하지 마세요. 이러한 오류는 나머지 절차를 완료하면 사라집니다.

6. **솔루션 탐색기**에서 **MainWindow.xaml** 노드를 확장하고 **MainWindow.xaml.cs** 또는 **MainWindow.xaml.vb** 파일을 엽니다.

7. 코드 편집기에서 파일의 맨 위에 다음 `using` 또는 `Imports` 지시문을 추가합니다.

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    using Newtonsoft.Json;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    Imports Newtonsoft.Json
    ```

8. **WPFQuickStart** 네임스페이스(C#) 또는 **MainWindow** 클래스(VB)의 모든 코드를 다음 코드로 바꿉니다.

    ```csharp
    namespace WPFQuickStart
    {
        /// <summary>
        /// Interaction logic for MainWindow.xaml
        /// </summary>
        public class TodoItem
        {
            public string Id { get; set; }

            [JsonProperty(PropertyName = "text")]
            public string Text { get; set; }

            [JsonProperty(PropertyName = "complete")]
            public bool Complete { get; set; }
        }

        public partial class MainWindow : Window
        {
            private MobileServiceCollection<TodoItem, TodoItem> items;
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();

            public MainWindow()
            {
                InitializeComponent();
            }

            private async void InsertTodoItem(TodoItem todoItem)
            {
                // This code inserts a new TodoItem into the database. When the operation completes
                // and Mobile Services has assigned an Id, the item is added to the CollectionView
                await todoTable.InsertAsync(todoItem);
                items.Add(todoItem);
            }

            private async void RefreshTodoItems()
            {
                try
                {
                    // This code refreshes the entries in the list view by querying the TodoItem table.
                    // The query excludes completed TodoItems
                    items = await todoTable
                        .Where(todoItem => todoItem.Complete == false)
                        .ToCollectionAsync();
                    ListItems.ItemsSource = items;
                }
                catch (MobileServiceInvalidOperationException e)
                {
                    MessageBox.Show(e.Message, "Error loading items");
                }
            }

            private async void UpdateCheckedTodoItem(TodoItem item)
            {
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService
                // responds, the item is removed from the list
                await todoTable.UpdateAsync(item);
                items.Remove(item);
            }

            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)
            {
                RefreshTodoItems();
            }

            private void ButtonSave_Click(object sender, RoutedEventArgs e)
            {
                var todoItem = new TodoItem { Text = TodoInput.Text };
                InsertTodoItem(todoItem);
                TodoInput.Text = "";
            }

            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)
            {
                CheckBox cb = (CheckBox)sender;
                TodoItem item = cb.DataContext as TodoItem;
                UpdateCheckedTodoItem(item);
            }

            protected override void OnActivated(EventArgs e)
            {
                RefreshTodoItems();
            }
        }

    }
    ```

    ```vb
    Public Class TodoItem
        Public Property Id() As String

        <JsonProperty(PropertyName:="text")>
        Public Property Text() As String

        <JsonProperty(PropertyName:="complete")>
        Public Property Complete() As Boolean
    End Class

    Partial Public Class MainWindow
        Inherits Window

        Private items As MobileServiceCollection(Of TodoItem, TodoItem)
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()

        Public Sub New()
            InitializeComponent()
        End Sub

        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)
            ' This code inserts a new TodoItem into the database. When the operation completes
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView
            Await todoTable.InsertAsync(todoItem)
            items.Add(todoItem)
        End Sub

        Private Async Sub RefreshTodoItems()
            Dim exception As MobileServiceInvalidOperationException = Nothing
            Try
                ' This code refreshes the entries in the list view by querying the TodoItem table.
                ' The query excludes completed TodoItems
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()
            Catch e As MobileServiceInvalidOperationException
                exception = e
            End Try

            If exception IsNot Nothing Then
                MessageBox.Show(exception.Message, "Error loading items")
            Else
                ListItems.ItemsSource = items
            End If
        End Sub

        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService
            ' responds, the item is removed from the list
            Await todoTable.UpdateAsync(item)
            items.Remove(item)
        End Sub

        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            RefreshTodoItems()
        End Sub

        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}
            InsertTodoItem(todoItem)
            TodoInput.Text = ""
        End Sub

        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim cb As CheckBox = DirectCast(sender, CheckBox)
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)
            UpdateCheckedTodoItem(item)
        End Sub

        Protected Overrides Sub OnActivated(ByVal e As EventArgs)
            RefreshTodoItems()
        End Sub
    End Class
    ```

     이 코드는 비동기 메서드를 사용하여 모바일 서비스에서 사용자 인터페이스와 데이터베이스 간의 상호 작용을 정의합니다.

## <a name="create-the-azure-mobile-service"></a>Azure 모바일 서비스 만들기
 최종 단계는 Microsoft Azure에서 모바일 서비스를 만들고 사용자 데이터를 저장할 테이블을 추가한 다음 애플리케이션에서 서비스 인스턴스를 참조하는 것입니다.

#### <a name="to-create-a-mobile-service"></a>모바일 서비스를 만들려면

1. 웹 브라우저를 열고 Microsoft Azure 포털에 로그인한 다음 **모바일 서비스** 탭을 선택합니다.

2. **새로 만들기** 단추를 선택한 다음 팝업 대화 상자에서 **컴퓨팅**, **모바일 서비스, 만들기**를 차례로 선택합니다.

3. **새 모바일 서비스** 대화 상자에서 **URL** 텍스트 상자를 선택하고 `wpfquickstart01`을 입력합니다.

    > [!NOTE]
    > URL의 숫자 부분을 변경해야 할 수도 있습니다. Microsoft Azure에서는 각 모바일 서비스에 대한 고유한 URL이 필요합니다.

     이렇게 하면 서비스에 대 한 URL이로 설정 `https://wpfquickstart01.azure-mobile.net/` 됩니다.

4. **데이터베이스** 목록에서 데이터베이스 옵션을 선택합니다. 많은 사용량을 얻지 못하는 응용 프로그램 이므로 **무료 20MB SQL 데이터베이스 만들기** 옵션을 선택 하거나 구독과 이미 연결 되어 있는 무료 데이터베이스를 선택 하는 것이 좋습니다.

5. **지역** 목록에서 모바일 서비스를 배포할 데이터 센터를 선택한 후 **다음** (오른쪽 화살표) 단추를 선택합니다.

    > [!NOTE]
    > 이 서비스에 대해 기본 **백 엔드** 설정인 **JavaScript**를 사용합니다.

6. 새 데이터베이스를 만드는 경우 **데이터베이스 설정 지정** 페이지의 **서버** 목록에서 **새 SQL 데이터베이스 서버**를 선택하고 **SQL 로그인 이름** 및 **암호**를 입력한 다음 **완료** (확인 표시) 단추를 선택합니다.

7. 기존 데이터베이스를 선택한 경우 **데이터베이스 설정** 페이지에서 **로그인 암호** 를 입력하고 **완료** (확인 표시) 단추를 선택합니다.

     모바일 서비스를 만드는 프로세스가 시작됩니다. 프로세스가 완료되면 상태가 **준비** 로 변경되며 다음 단계로 이동할 수 있습니다.

8. 포털에서 새로 만든 모바일 서비스를 선택한 다음 **키 관리** 단추를 선택합니다.

9. **액세스 키 관리** 대화 상자에서 **애플리케이션 키**를 복사합니다.

     다음 절차에서 이 서비스를 사용합니다.

#### <a name="to-create-a-table"></a>테이블 형식 보고서를 만들려면

1. Microsoft Azure 포털에서 모바일 서비스 이름 옆에 있는 오른쪽 화살표를 선택한 다음 메뉴 모음에서 **데이터**, **테이블 추가** 링크를 차례로 선택합니다.

2. **새 테이블 만들기** 대화 상자의 **테이블 이름** 텍스트 상자에 `TodoItem`를 입력한 후 **완료** (확인 표시) 단추를 선택합니다.

     테이블이 생성될 때까지 기다린 후 최종 절차로 넘어갑니다.

#### <a name="to-add-a-declaration-for-the-mobile-service"></a>모바일 서비스에 대한 선언을 추가하려면

1. Visual Studio로 돌아갑니다. **솔루션 탐색기**에서 **App.xaml** (C#) 또는 **Application.xaml** (Visual Basic) 노드를 확장하고 **App.xaml.cs** 또는 **App.xaml.vb** 파일을 엽니다.

2. 코드 편집기에서 파일의 맨 위에 다음 `using` 또는 **Imports** 지시문을 추가합니다.

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    ```

3. *YOUR-SERVICE_HERE* 를 서비스의 URL 이름으로 바꾸고 *YOUR-KEY-HERE* 를 이전 절차에서 복사한 애플리케이션 키로 바꿔 다음 선언을 클래스에 추가합니다.

    ```csharp
    public static MobileServiceClient MobileService = new MobileServiceClient(
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",
                 "YOUR-KEY-HERE"
             );
    ```

    ```vb
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")
    ```

     이 코드는 애플리케이션이 Microsoft Azure에서 실행되는 모바일 서비스에 액세스할 수 있게 합니다.

## <a name="test-the-application"></a>애플리케이션 테스트
 모두 끝났습니다. Azure 모바일 서비스에 액세스하는 WPF 데스크톱 애플리케이션을 만들었습니다. 이제 애플리케이션을 실행하고 작동을 확인하는 것만 남았습니다.

#### <a name="to-run-the-application"></a>애플리케이션을 실행하려면

1. 메뉴 모음에서 **디버그**, **디버깅 시작** 을 선택 하거나 f5 키를 누릅니다.

2. **Insert a TodoItem** 텍스트 상자에 `Do something`를 입력한 후 **저장** 단추를 선택합니다.

3. Enter `Do something else`를 입력한 후 **저장** 단추를 다시 선택합니다.

     다음 그림과 같이 두 항목이 **Query and Update Data** 목록에 추가됩니다.

     ![할 일 항목이 목록에 추가됩니다.](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")

4. 목록에서 **Do something else** 항목에 대한 확인란을 선택합니다.

     이렇게 하면 **UpdateCheckedTodoItem** 메서드가 호출되고 목록 및 데이터베이스 둘 다에서 항목이 제거됩니다.

## <a name="next-steps"></a>다음 단계
 Azure 백 엔드를 사용한 WPF 데스크톱 애플리케이션의 매우 간단한 예제를 완료했습니다. 물론, 실제 애플리케이션은 훨씬 더 복잡할 수 있지만 동일한 기본 개념이 적용됩니다. [.NET Framework의 WPF](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx)를 참조하세요.

 색, 모양, 그래픽 및 심지어 애니메이션을 추가하여 사용자 인터페이스를 보다 매력적으로 만들 수 있습니다. [Visual Studio 및 Blend for Visual Studio에서 XAML 디자인](../designers/designing-xaml-in-visual-studio.md)을 참조하세요.

 Azure 모바일 서비스를 사용하여 기존 SQL 데이터베이스 또는 다른 데이터 원본에 연결할 수 있습니다. [모바일 서비스 설명서](https://azure.microsoft.com/services/app-service/mobile/)를 참조하세요.

## <a name="see-also"></a>관련 항목
 [연습: 내 첫 번째 WPF 데스크톱 응용 프로그램이](../designers/walkthrough-my-first-wpf-desktop-application2.md) [Windows Presentation Foundation를 사용 하 여 최신 데스크톱 응용 프로그램 만들기](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
