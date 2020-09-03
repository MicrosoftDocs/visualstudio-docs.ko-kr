---
title: '연습: 내 첫 번째 WPF 데스크톱 애플리케이션2 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e800fe651d32435351b2338b4da2f9c55158b3a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664001"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>연습: 내 첫 WPF 데스크톱 애플리케이션
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

name = "소개" ></a> 이 연습에서는 WPF (Windows Presentation Foundation) 개발에 대해 소개 합니다. XAML 태그, 코드 숨김, 애플리케이션 정의, 컨트롤, 레이아웃, 데이터 바인딩, 스타일 등 대부분의 WPF 데스크톱 애플리케이션에 공통된 요소를 포함하는 기본 애플리케이션을 만듭니다.

## <a name="creating-the-application-project"></a><a name="Create_The_Application_Code_Files"></a> 응용 프로그램 프로젝트 만들기
 이 섹션에서는 프로젝트와 주 창 또는 폼을 포함하는 애플리케이션 인프라를 만듭니다.

#### <a name="to-create-the-project"></a>프로젝트를 만들려면

1. 메뉴 모음에서 **파일**, **새로 만들기**, **프로젝트**를 차례로 선택합니다.

2. **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 확장하고 **Windows** 노드를 선택한 다음 **Windows** 노드를 확장하고 **클래식 바탕 화면** 노드를 선택합니다.

3. 템플릿 목록에서 **WPF 애플리케이션** 템플릿을 선택합니다.

4. **이름** 텍스트 상자에 `ExpenseIt`를 입력하고 **확인** 단추를 선택합니다.

     프로젝트가 생성되고 프로젝트 파일이 **솔루션 탐색기**에 추가된 다음 **MainWindow.xaml** 이라는 기본 애플리케이션 창에 대한 디자이너가 표시됩니다.

#### <a name="to-modify-the-main-window"></a>주 창을 수정하려면

1. 디자이너에서 활성 디자이너 탭이 아닌 경우 **MainWindow.xaml** 탭을 선택합니다.

2. C#을 사용하는 경우 `<Window x:Class="ExpenseIt.MainWindow"` 줄을 찾아서 `<NavigationWindow x:Class="ExpenseIt.MainWindow"`로 바꿉니다.

     Visual Basic을 사용하는 경우 `<Window x:Class=" MainWindow"` 줄을 찾아서 `<NavigationWindow x:Class="MainWindow"`로 바꿉니다.

     `<Window` 태그를 `<NavigationWindow`로 변경하는 경우 Intellisense가 자동으로 닫는 태그를 `</NavigationWindow>` 로 변경합니다.

    > [!NOTE]
    > 태그를 변경한 후 **오류 목록** 창이 열려 있으면 여러 오류가 표시될 수도 있습니다. 다음 몇 단계의 변경 작업을 수행하면 이러한 오류가 사라집니다.

3. `<Grid>` 및 `</Grid>` 태그를 선택하고 삭제합니다.

     **NavigationWindow** 는 **Grid**와 같은 기타 UI 요소를 포함할 수 없습니다.

4. **속성** 창에서 **Common** 범주 노드를 확장하고 **Title** 속성을 선택한 다음 `ExpenseIt` 를 입력하고 **Enter** 키를 누릅니다.

     XAML 창의 **Title** 요소가 새 값과 일치하도록 변경됩니다. XAML 창 또는 **속성** 창에서 XAML 속성을 수정할 수 있으며 변경 내용이 동기화됩니다.

5. XAML 창에서 **Height** 요소의 값을 `375`로 설정하고 **Width** 속성의 값을 `500`서 무료 평가판 계정을 등록할 수 있습니다.

     이러한 요소는 **속성** 창의 **레이아웃** 범주에 있는 **Height** 및 **Width** 속성에 해당합니다.

     이제 C#에서 **MainWindow.xaml** 파일이 다음과 같이 표시됩니다.

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">

    </NavigationWindow>
    ```

     또는 Visual Basic에서 다음과 같이 표시됩니다.

    ```xaml
    <NavigationWindow x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">

    </NavigationWindow>
    ```

#### <a name="to-modify-the-code-behind-file-c"></a>코드 숨김 파일을 수정하려면(C#)

1. **솔루션 탐색기**에서 **MainWindow.xaml** 노드를 확장하고 **MainWindow.xaml.cs** 파일을 엽니다.

2. `public partial class MainWindow : Window` 줄을 찾아서 `public partial class MainWindow : NavigationWindow`로 바꿉니다.

     이렇게 하면 `MainWindow` 클래스가 `NavigationWindow`에서 파생되도록 변경됩니다. Visual Basic에서는 XAML에서 창을 변경할 때 이 작업이 자동으로 수행되므로 코드를 변경해야 합니다.

## <a name="adding-files-to-the-application"></a><a name="add_files_to_the_application"></a> 응용 프로그램에 파일 추가
 이 섹션에서는 애플리케이션에 두 페이지와 이미지를 추가합니다.

#### <a name="to-add-a-home-screen"></a>홈 화면을 추가하려면

1. **솔루션 탐색기**에서 **ExpenseIt** 노드의 바로 가기 메뉴를 열고 **추가**, **페이지**를 선택합니다.

2. **새 항목 추가** 대화 상자에서 **이름** 텍스트 상자를 선택하고 `ExpenseItHome`를 입력하고 **추가** 단추를 선택합니다.

     이 페이지는 애플리케이션을 시작할 때 표시되는 첫 번째 창입니다.

3. 디자이너에서 활성 디자이너 탭이 아닌 경우 **ExpenseItHome.xaml** 탭을 선택합니다.

4. `<Title>` 요소를 선택하고 제목을 **ExpenseIt – Home**으로 변경합니다.

     이제 C#에서 **ExpenseItHome.xaml** 파일이 다음과 같이 표시됩니다.

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">

        <Grid>

        </Grid>
    </Page>
    ```

     또는 Visual Basic에서 다음과 같이 표시됩니다.

    ```xaml
    <Page x:Class="ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid>

        </Grid>
    </Page>
    ```

5. 디자이너에서 **MainWindow.xaml** 탭을 선택합니다.

6. 줄 `Title="ExpenseIt" Height="375" Width="500">` 요소를 찾아서 `Source="ExpenseItHome.xaml"` 속성을 추가합니다.

     이렇게 하면 **expenseithome.xaml** 가 응용 프로그램이 시작 될 때 열리는 첫 페이지로 설정 됩니다. 이제 C#에서 **MainWindow.xaml** 파일이 다음과 같이 표시됩니다.

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">

    </NavigationWindow>
    ```

     또는 Visual Basic에서 다음과 같이 표시됩니다.

    ```xaml
    <NavigationWindow x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">

    </NavigationWindow>
    ```

     앞에서 설정한 속성과 마찬가지로 `Source` 속성 **창의** 기타 **범주에서** 속성을 설정했을 수 있습니다.

#### <a name="to-add-a-details-window"></a>세부 정보 창을 추가하려면

1. **솔루션 탐색기**에서 **ExpenseIt** 노드의 바로 가기 메뉴를 열고 **추가**, **페이지**를 선택합니다.

2. **새 항목 추가** 대화 상자에서 **이름** 텍스트 상자를 선택하고 `ExpenseReportPage`를 입력하고 **추가** 단추를 선택합니다.

     이 창에는 개별 경비 보고서가 표시됩니다.

3. 디자이너에서 활성 디자이너 탭이 아닌 경우 **ExpenseReportPage.xaml** 탭을 선택합니다.

4. `<Title>` 요소를 선택하고 제목을 **ExpenseIt – View Expense**로 변경합니다.

     이제 C#에서 ExpenseReportPage.xaml 파일이 다음과 같이 표시됩니다.

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseReportPage"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - View Expense">

        <Grid>

        </Grid>
    </Page>
    ```

     또는 Visual Basic에서 다음과 같이 표시됩니다.

    ```xaml
    <Page x:Class="ExpenseReportPage"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - View Expense">
        <Grid>

        </Grid>
    </Page>
    ```

5. 메뉴 모음에서 **디버그**, **디버깅 시작** 을 선택하거나 F5 키를 눌러 애플리케이션을 실행합니다.

     다음 그림에서는 탐색 창 단추가 포함된 애플리케이션을 보여 줍니다.

     ![ExpenseIt 샘플 스크린샷](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")

6. 디자인 모드로 돌아가려면 애플리케이션을 닫습니다.

## <a name="creating-the-user-interface"></a><a name="Add_Layout"></a> 사용자 인터페이스 만들기
 레이아웃은 요소를 배치하는 순서가 지정된 방법을 제공하며 폼의 크기를 조정할 때 해당 요소의 크기와 위치도 관리합니다. 이 섹션에서는 3개의 행이 있는 단일 열 그리드를 만듭니다. 두 페이지에 컨트롤을 추가하고, 일부 코드를 추가하고, 마지막으로 컨트롤에 대해 재사용 가능한 스타일을 정의합니다.

#### <a name="to-create-the-layout"></a>레이아웃을 만들려면

1. **Expenseithome.xaml** 을 열고 요소를 선택 합니다. `<Grid>`

2. **속성** 창에서 **Height** 범주 노드를 확장하고 **여백** 값을 왼쪽, 오른쪽, 위쪽 및 아래쪽 여백에 해당하는 `10`, `10`, `0`및 `10`으로 설정합니다.

     `Margin="10,0,10,10"` 요소가 XAML의 `<Grid>` 요소에 추가됩니다. **속성** 창이 아니라 XAML 코드에서 직접 이러한 값을 입력하여 동일한 결과를 얻을 수도 있습니다.

3. 다음 XAML 코드를 `Grid` 요소에 추가하여 행 및 열 정의를 만듭니다.

    ```xaml
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition />
        <RowDefinition Height="Auto"/>
    </Grid.RowDefinitions>
    ```

#### <a name="to-add-controls"></a>컨트롤을 추가하려면

1. **ExpenseItHome.xaml**을 엽니다.

2. 다음 XAML 코드를 `</Grid>` 태그 바로 위에 추가하여 `Border`, `ListBox` 및 `Button` 컨트롤을 만듭니다.

    ```xaml
    <!-- People list -->
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>
      </Border>
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">
          <ListBoxItem>Mike</ListBoxItem>
          <ListBoxItem>Lisa</ListBoxItem>
          <ListBoxItem>John</ListBoxItem>
          <ListBoxItem>Mary</ListBoxItem>
      </ListBox>

      <!-- View report button -->
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>

    ```

     컨트롤이 디자인 창에 나타납니다. 또한 **도구 상자** 창에서 디자인 창으로 끌고 **속성** 창에서 해당 속성을 설정하여 컨트롤을 만들었을 수도 있습니다.

3. 애플리케이션을 빌드 및 실행합니다. 다음 그림은 이 절차에서 XAML로 생성된 컨트롤의 런타임 모양을 보여 줍니다.

     ![ExpenseIt 샘플 스크린샷](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")

4. 디자인 모드로 돌아가려면 애플리케이션을 닫습니다.

#### <a name="to-add-a-background-image"></a>배경 이미지를 추가하려면

1. 다음 이미지를 선택하고 `watermark.png`를 차례로 선택합니다.

     ![연습에 대한 워터마크 이미지](../designers/media/wpf-watermark.png "WPF_watermark")

    > [!NOTE]
    > 또는 사용자 고유의 이미지를 만들고 `watermark.png`를 차례로 선택합니다.

2. **솔루션 탐색기**에서 **ExpenseIt** 노드의 바로 가기 메뉴를 열고 **추가**, **기존 항목**을 선택합니다.

3. **기존 항목 추가** 대화 상자에서 방금 추가한 **watermark.png** 이미지를 찾아서 선택한 다음 **추가** 단추를 선택합니다.

    > [!NOTE]
    > **파일 형식** 목록을 확장하고 **이미지 파일**을 선택해야 할 수도 있습니다.

4. **ExpenseItHome.xaml** 파일을 열고 다음 XAML 코드를 `</Grid>` 태그 바로 위에 추가하여 배경 이미지를 만듭니다.

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png"/>
    </Grid.Background>

    ```

#### <a name="to-add-a-title"></a>제목을 추가하려면

1. **ExpenseItHome.xaml**을 엽니다.

2. `<Grid.ColumnDefinitions>` 줄을 찾은 다음 바로 아래에 다음을 추가합니다.

    ```xaml
    <ColumnDefinition Width="230" />

    ```

     이렇게 하면 다른 열의 왼쪽에 고정 너비가 230픽셀인 열이 추가로 만들어집니다.

3. `<Grid.RowDefinitions>` 줄을 찾은 다음 바로 아래에 다음을 추가합니다.

    ```xaml
    <RowDefinition />

    ```

     이렇게 하면 그리드의 맨 위에 행이 추가됩니다.

4. `Grid.Column` 값을 1로 설정하여 컨트롤을 두 번째 열로 이동합니다. 각 `Grid.Row` 값을 1씩 증가하여 각 컨트롤을 한 행 아래로 이동합니다.

    1. `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`줄을 찾습니다. `Grid.Column="0"` 을 `Grid.Column="1"` 로 변경하고 `Grid.Row="0"` 을 `Grid.Row="1"`로 변경합니다.

    2. `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`줄을 찾습니다. `Grid.Column="0"` 을 `Grid.Column="1"` 로 변경하고 `Grid.Row="1"` 을 `Grid.Row="2"`로 변경합니다.

    3. `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`줄을 찾습니다. `Grid.Column="0"` 을 `Grid.Column="1"` 로 변경하고 `Grid.Row="2"` 을 `Grid.Row="3"`로 변경합니다.

5. `<Border` 요소 바로 앞에 다음 XAML 코드를 추가하여 제목을 표시합니다.

    ```xaml
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        View Expense Report
    </Label>

    ```

     이제 C#에서 **ExpenseItHome.xaml** 의 내용이 다음과 같이 표시됩니다.

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid Margin="10,0,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>
            </Border>
            <!-- People list -->
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
                View Expense Report
            </Label>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"/>
            </Grid.Background>
        </Grid>
    </Page>
    ```

     또는 Visual Basic에서 다음과 같이 표시됩니다.

    ```xaml
    <Page x:Class="ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home" >
        <Grid Margin="10,0,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>
            </Border>
            <!-- People list -->
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
                View Expense Report
            </Label>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"/>
            </Grid.Background>
        </Grid>
    </Page>
    ```

6. 이때 애플리케이션을 빌드 및 실행하는 경우 다음 그림과 같이 표시되어야 합니다.

     ![ExpenseIt 샘플 스크린샷](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")

#### <a name="to-add-code-to-the-button"></a>단추에 코드를 추가하려면

1. **ExpenseItHome.xaml**을 엽니다.

2. `<Button` 요소를 선택하고 다음 XAML 코드를 **HorizontalAlignment = "Right"** 요소 바로 뒤에 추가합니다. `Click="Button_Click"`.

     이렇게 하면 단추의 `Click` 이벤트에 대한 이벤트 처리기가 추가됩니다. 이제 **<Button** 요소 코드가 다음과 같이 표시 됩니다.

    ```
    <!-- View report button -->
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>
    ```

3. **ExpenseItHome.xaml.cs** 또는 **ExpenseItHome.xaml.vb** 파일을 엽니다.

4. `ExpenseItHome` 클래스에 다음 코드를 추가합니다.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        // View Expense Report
        ExpenseReportPage expenseReportPage = new ExpenseReportPage();
        this.NavigationService.Navigate(expenseReportPage);

    }
    ```

    ```vb
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
        ' View Expense Report
        Dim expenseReportPage As New ExpenseReportPage()
    Me.NavigationService.Navigate(expenseReportPage)
    End Sub
    ```

     이 이벤트 처리기는 단추를 클릭할 때 경비 보고서 페이지를 엽니다.

#### <a name="to-create-the-ui-for-the-report-page"></a>보고서 페이지에 대한 UI를 만들려면

1. **ExpenseReportPage.xaml**을 엽니다.

     이 페이지는 홈 페이지에서 선택된 사용자에 대한 경비 보고서를 표시합니다.

2. 다음 XAML 코드를 `<Grid>` 및 `</Grid>` 태그 사이에 추가합니다.

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>

    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">

        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.ColumnHeaderStyle>
                    <Style TargetType="{x:Type DataGridColumnHeader}">
                        <Setter Property="Height" Value="35" />
                        <Setter Property="Padding" Value="5" />
                        <Setter Property="Background" Value="#4E87D4" />
                        <Setter Property="Foreground" Value="White" />
                    </Style>
                </DataGrid.ColumnHeaderStyle>
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>
    ```

     이 UI는 홈 페이지에 대해 만들어진 UI와 유사하지만 보고서 데이터가 **DataGrid** 컨트롤에 표시됩니다.

3. 애플리케이션을 빌드 및 실행합니다.

4. **보기** 단추를 선택합니다.

     경비 보고서 페이지가 나타납니다.

     다음 그림에서는 경비 보고서 페이지를 보여 줍니다. 뒤로 탐색 단추를 사용할 수 있습니다.

     ![ExpenseIt 샘플 스크린샷](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")

#### <a name="to-style-controls"></a>컨트롤의 스타일을 지정하려면

1. **App.xaml** 파일(C#) 또는 **Application.xaml** 파일(Visual Basic)을 엽니다.

2. 다음 XAML을 `<Application.Resources>` 및 `</Application.Resources>` 태그 사이에 추가합니다.

    ```xaml
    <!-- Header text style -->
    <Style x:Key="headerTextStyle">
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>
        <Setter Property="Label.FontSize" Value="18"></Setter>
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>
    </Style>

    <!-- Label style -->
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">
        <Setter Property="VerticalAlignment" Value="Top" />
        <Setter Property="HorizontalAlignment" Value="Left" />
        <Setter Property="FontWeight" Value="Bold" />
        <Setter Property="Margin" Value="0,0,0,5" />
    </Style>

    <!-- DataGrid header style -->
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
        <Setter Property="Foreground" Value="White" />
    </Style>

    <!-- List header style -->
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
    </Style>

    <!-- List header text style -->
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">
        <Setter Property="Foreground" Value="White" />
        <Setter Property="VerticalAlignment" Value="Center" />
        <Setter Property="HorizontalAlignment" Value="Left" />
    </Style>

    <!-- Button style -->
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">
        <Setter Property="Width" Value="125" />
        <Setter Property="Height" Value="25" />
        <Setter Property="Margin" Value="0,10,0,0" />
        <Setter Property="HorizontalAlignment" Value="Right" />
    </Style>
    ```

     이 XAML은 다음 스타일을 추가합니다.

    - `headerTextStyle`: 페이지 제목 `Label`의 형식을 지정합니다.

    - `labelStyle`: `Label` 컨트롤의 형식을 지정합니다.

    - `columnHeaderStyle`: `DataGridColumnHeader`의 형식을 지정합니다.

    - `listHeaderStyle`: 목록 헤더 `Border` 컨트롤의 형식을 지정합니다.

    - `listHeaderTextStyle`: 목록 헤더 **레이블의**형식을 지정 합니다.

    - `buttonStyle`: `Button` **Expenseithome.xaml** pppage에 있는의 형식을 지정 합니다.

3. **Expenseithome.xaml** 을 열고 및 요소 사이에 있는 모든 `<Grid>` 내용을 `</Grid>` 다음 xaml로 바꿉니다.

    ```xaml
    <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>

            <Grid.RowDefinitions>
                <RowDefinition/>
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >
                View Expense Report
            </Label>
            <!-- People list -->
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>
            </Border>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"  />
            </Grid.Background>
    ```

     스타일을 적용하면 각 컨트롤의 모양을 정의하는 `VerticalAlignment` 및 `FontFamily` 와 같은 속성이 제거되고 바뀝니다.

4. **Expensereportpage.xaml** 을 열고 및 최종 요소 사이에 있는 모든 내용을 `<Grid>` `</Grid>` 다음 xaml로 바꿉니다.

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Name:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"
    Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Department:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"
                      AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>

    ```

     이렇게 하면 `<Label>` 및 `<Border>` 요소에 스타일이 추가됩니다.

## <a name="connecting-to-data"></a>데이터에 연결
 이 섹션에서는 데이터 공급자 및 데이터 템플릿을 만들고 컨트롤을 연결하여 데이터를 표시합니다.

#### <a name="to-bind-data-to-a-control"></a>데이터를 컨트롤에 바인딩하려면

1. **ExpenseItHome.xaml** 을 열고 `<Grid>` 요소를 선택합니다.

2. 다음 XAML 코드를 추가합니다.

    ```xaml

    <Grid.Resources>
    <!-- Expense Report Data -->
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">
        <x:XData>
            <Expenses xmlns="">
                <Person Name="Mike" Department="Legal">
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />
                </Person>
                <Person Name="Lisa" Department="Marketing">
                    <Expense ExpenseType="Document printing"
          ExpenseAmount="50"/>
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />
                </Person>
                <Person Name="John" Department="Engineering">
                    <Expense ExpenseType="Magazine subscription"
         ExpenseAmount="50"/>
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />
                    <Expense ExpenseType="Software" ExpenseAmount="500" />
                </Person>
                <Person Name="Mary" Department="Finance">
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />
                </Person>
            </Expenses>
        </x:XData>
    </XmlDataProvider>
    </Grid.Resources>
    ```

     이 코드에서는 각 사용자에 대한 데이터를 포함하는 `XmlDataProvider` 클래스를 만듭니다. 일반적으로 파일로 로드되지만 편의상 데이터가 인라인으로 추가됩니다.

3. `<Grid.Resources>` 요소 내에 다음 XAML 코드를 추가합니다.

    ```xaml
    <!-- Name item template -->
    <DataTemplate x:Key="nameItemTemplate">
        <Label Content="{Binding XPath=@Name}"/>
    </DataTemplate>
    ```

     이렇게 하면 `Data Template` ListBox **에 데이터를 표시하는 방법을 정의하는**이 추가됩니다.

4. 기존 `<ListBox>` 요소를 다음 XAML로 바꿉니다.

    ```xaml
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"
             ItemTemplate="{StaticResource nameItemTemplate}">
    </ListBox>
    ```

     이렇게 하면 `ItemsSource` 의 `ListBox` 속성이 데이터 원본에 바인딩되고 데이터 템플릿이 `ItemTemplate`으로 적용됩니다.

#### <a name="to-connect-data-to-controls"></a>데이터를 컨트롤에 연결하려면

1. **Expensereportpage.xaml** 또는 **ExpenseReportPage.xaml.cs**를 엽니다.

2. C#에서 다음 생성자를 **ExpenseReportPage** 클래스에 추가하거나 Visual Basic에서 기존 클래스를 다음으로 바꿉니다.

    ```csharp
    // Custom constructor to pass expense report data
        public ExpenseReportPage(object data):this()
        {
            // Bind to expense report data.
            this.DataContext = data;
        }
    ```

    ```vb
    Partial Public Class ExpenseReportPage
    Inherits Page
    Public Sub New()
    InitializeComponent()
    End Sub

    ' Custom constructor to pass expense report data
    Public Sub New(ByVal data As Object)
    Me.New()
    ' Bind to expense report data.
    Me.DataContext = data
    End Sub

    End Class
    ```

     이 생성자는 데이터 개체를 매개 변수로 사용합니다. 이 경우 데이터 개체에 선택한 사용자의 이름이 포함됩니다.

3. **Expenseithome.xaml** 또는 **ExpenseItHome.xaml.cs**를 엽니다.

4. `Click` 이벤트 처리기 코드를 다음으로 바꿉니다.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        // View Expense Report
        ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);
        this.NavigationService.Navigate(expenseReportPage);

    }
    ```

    ```vb
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
        ' View Expense Report
        Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)
        Me.NavigationService.Navigate(expenseReportPage)
    End Sub
    ```

     이 코드는 새 생성자를 호출합니다.

#### <a name="to-update-the-ui-with-data-templates"></a>데이터 템플릿을 사용하여 UI를 업데이트하려면

1. **ExpenseReportPage.xaml**을 엽니다.

2. **이름** 및 **Department**`<StackPanel` 요소에 대한 XAML 코드를 다음으로 바꿉니다.

    ```xaml
    <!-- Name -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Name:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>
    </StackPanel>

    <!-- Department -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Department:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>
    </StackPanel>

    ```

     이렇게 하면 **Label** 컨트롤이 해당 데이터 원본 속성에 바인딩됩니다.

3. `<Grid>` 요소 내에 다음 XAML 코드를 추가합니다.

    ```xaml
    <!--Templates to display expense report data-->
    <Grid.Resources>
        <!-- Reason item template -->
        <DataTemplate x:Key="typeItemTemplate">
            <Label Content="{Binding XPath=@ExpenseType}"/>
        </DataTemplate>
        <!-- Amount item template -->
        <DataTemplate x:Key="amountItemTemplate">
            <Label Content="{Binding XPath=@ExpenseAmount}"/>
        </DataTemplate>
    </Grid.Resources>

    ```

     이렇게 하면 경비 보고서 데이터를 표시하는 방법이 정의됩니다.

4. `<DataGrid>` 요소를 다음으로 바꿉니다.

    ```xaml
    <!-- Expense type and Amount table -->
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >

        <DataGrid.Columns>
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />
        </DataGrid.Columns>

    </DataGrid>
    ```

     이렇게 하면 **ItemSource** 가 추가되고 비용 항목에 대한 바인딩이 정의됩니다.

5. 애플리케이션을 빌드 및 실행합니다.

6. 사용자를 선택한 다음 **보기** 단추를 선택합니다.

     다음 그림에서는 컨트롤, 레이아웃, 스타일, 데이터 바인딩 및 데이터 템플릿이 적용된 ExpenseIt 애플리케이션의 페이지를 둘 다 보여 줍니다.

     ![ExpenseIt 샘플 스크린 샷](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")

## <a name="best-practices"></a><a name="Best_Practices"></a> 최선의 구현 방법
 이 샘플은 WPF의 기본 사항을 보여 주므로 애플리케이션 개발 모범 사례를 따르지 않습니다. WPF 및 .NET Framework 애플리케이션 개발 모범 사례에 대한 자세한 내용은 다음 항목을 적절하게 참조하세요.

- 접근성- [접근성 모범 사례](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)

- 보안 - [Windows Presentation Foundation 보안](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)

- 지역화- [WPF 전역화 및 지역화 개요](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)

- 성능- [WPF 응용 프로그램 성능 최적화](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)

## <a name="whats-next"></a><a name="Whats_Next"></a> 다음 단계
 이제 WPF를 사용하여 데스크톱 애플리케이션을 만들기 위한 다양한 기술을 사용할 수 있습니다. 데이터 바인딩된 WPF 애플리케이션의 구성 요소에 대해 기본적인 내용을 이해하고 있을 것입니다. 이 항목은 전체 목록이 아니며 이 항목에 설명된 기술 외의 가능성을 스스로 발견할 수도 있습니다.

 WPF 아키텍처 및 프로그래밍 모델에 대한 자세한 내용은 다음 항목을 참조하세요.

- [WPF 아키텍처](https://msdn.microsoft.com/library/ms750441\(v=vs.100\).aspx)

- [XAML 개요](https://msdn.microsoft.com/library/ms752059\(v=vs.100\).aspx)

- [종속성 속성 개요](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx)

- [레이아웃 시스템](https://msdn.microsoft.com/library/ms745058\(v=vs.100\).aspx)

- [스타일 및 템플릿](https://msdn.microsoft.com/library/bb613570\(v=vs.100\).aspx)

  애플리케이션을 만드는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.

- [애플리케이션 개발 개요](https://msdn.microsoft.com/library/bb613549\(v=vs.100\).aspx)

- [컨트롤 개요](https://msdn.microsoft.com/library/bb613551\(v=vs.100\).aspx)

- [데이터 바인딩 개요](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)

- [WPF 그래픽, 애니메이션 및 미디어 개요](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)

- [WPF의 문서](https://msdn.microsoft.com/library/ms748388\(v=vs.100\).aspx)

## <a name="see-also"></a>관련 항목
 [연습: Azure 모바일 서비스에 연결 된 WPF 데스크톱 응용 프로그램 만들기](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md) [Windows Presentation Foundation를 사용 하 여 최신 데스크톱 응용 프로그램 만들기](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
