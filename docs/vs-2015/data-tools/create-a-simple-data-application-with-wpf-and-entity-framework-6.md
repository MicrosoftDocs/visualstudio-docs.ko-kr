---
title: WPF를 사용 하 여 간단한 데이터 응용 프로그램 만들기 및 Entity Framework 6 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 403415eaf8a882efdd63fdb9a73b5489b91f2529
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651081"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF 및 Entity Framework 6을 사용하여 간단한 데이터 애플리케이션 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습 SQL Server LocalDB, Northwind 데이터베이스 Entity Framework 6 및 Windows Presentation Foundation를 사용 하 여 Visual Studio에서 기본 "데이터 폼" 응용 프로그램을 만드는 방법을 보여 줍니다. 마스터-세부 보기를 사용 하 여 기본 데이터 바인딩을 수행 하는 방법을 보여 줍니다. 여기에는 "다음으로 이동", "이전으로 이동", "시작으로 이동", "" 끝으로 이동 "," 업데이트 "및" 삭제 "에 대 한 단추가 포함 된 사용자 지정" 바인딩 탐색기 "가 있습니다.

 이 문서에서는 Visual Studio에서 데이터 도구를 사용 하는 방법을 집중적으로 설명 하며, 기본 기술에 대해 설명 하지 않습니다. XAML, Entity Framework 및 SQL에 대 한 기본적인 지식이 있다고 가정 합니다. 또한이 예제에서는 WPF 응용 프로그램에 대 한 표준인 MVVM 아키텍처를 시연 하지 않습니다. 그러나이 코드를 거의 수정 하지 않아도 자신의 MVVM 응용 프로그램에 복사할 수 있습니다.

## <a name="install-and-connect-to-northwind"></a>Northwind에 설치 및 연결
 이 예에서는 SQL Server Express LocalDB 및 Northwind 샘플 데이터베이스를 사용 합니다. 해당 제품에 대 한 ADO.NET 데이터 공급자가 Entity Framework를 지 원하는 경우에도 다른 SQL database 제품과 함께 작동 해야 합니다.

1. 아직 설치 하지 않은 경우 [SQL Server 버전 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 SQL Server 2014 LocalDB Express 32 비트를 설치 합니다.

2. [SQL Server 예제 데이터베이스 설치](../data-tools/install-sql-server-sample-databases.md)를 참조 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

3. Northwind에 대 한 [새 연결을 추가](../data-tools/add-new-connections.md) 합니다.

## <a name="configure-the-project"></a>프로젝트 구성

1. Visual Studio에서 **파일 &#124; 새 프로젝트** 를 선택한 다음 새 c # WPF 응용 프로그램을 만듭니다.

2. 다음으로 Entity Framework 6 용 NuGet 패키지를 추가 합니다. 솔루션 탐색기에서 프로젝트 노드를 선택 합니다. 주 메뉴에서 **프로젝트 &#124; NuGet 패키지 관리** ...를 선택 합니다.

     ![NuGet 패키지 관리 메뉴 항목](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")

3. NuGet 패키지 관리자에서 **찾아보기** 링크를 클릭 합니다. Entity Framework은 목록의 맨 위 패키지인 것입니다. 오른쪽 창에서 **설치** 를 클릭 하 고 프롬프트를 따릅니다. 설치가 완료 되 면 출력 창에이를 알려 줍니다.

     ![NuGet 패키지 Entity Framework](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")

4. 이제 Visual Studio를 사용 하 여 Northwind 데이터베이스를 기반으로 모델을 만들 수 있습니다.

## <a name="create-the-model"></a>모델 만들기

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가 &#124; 새 항목**을 선택 합니다. 왼쪽 창의 c # 노드 아래에서 **데이터** 를 선택 하 고 가운데 창에서 **ADO.NET 엔터티 데이터 모델**를 선택 합니다.

    ![Entity Framework 모델 새 프로젝트 항목](../data-tools/media/raddata-ef-new-project-item.png "raddata EF 새 프로젝트 항목")

2. 모델을 호출 `Northwind_model` 하 고 확인을 선택 합니다. 그러면 **엔터티 데이터 모델 마법사**가 나타납니다. **데이터베이스에서 EF Designer** 를 선택 하 고 **다음**을 클릭 합니다.

    ![데이터베이스의 EF 모델](../data-tools/media/raddata-ef-model-from-database.png "데이터베이스의 raddata EF 모델")

3. 다음 화면에서 LocalDB Northwind 연결을 선택 하 고 **다음**을 클릭 합니다.

4. 마법사의 다음 페이지에서 Entity Framework 모델에 포함할 테이블, 저장 프로시저 및 기타 데이터베이스 개체를 선택 합니다. 트리 뷰에서 dbo 노드를 확장 하 고 고객, 주문 및 주문 세부 정보를 선택 합니다. 기본값을 선택 된 채로 두고 **마침**을 클릭 합니다.

    ![모델에 대 한 데이터베이스 개체 선택](../data-tools/media/raddata-choose-ef-objects.png "raddata EF 개체 선택")

5. 마법사는 Entity Framework 모델을 나타내는 c # 클래스를 생성 합니다. 이러한 클래스는 일반 c # 클래스 이며 WPF 사용자 인터페이스에 바인딩할 수 있습니다. .Edmx 파일은 클래스를 데이터베이스의 개체와 연결 하는 관계 및 기타 메타 데이터를 설명 합니다.  .Tt 파일은 모델에 대해 작동 하 고 변경 내용을 데이터베이스에 저장 하는 코드를 생성 하는 T4 템플릿입니다. Northwind_model 노드 아래 솔루션 탐색기에서 이러한 모든 파일을 볼 수 있습니다.

    ![EF 모델 파일 솔루션 탐색기](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata 솔루션 탐색기 EF model 파일")

    .Edmx 파일의 디자이너 화면에서는 모델의 일부 속성 및 관계를 수정할 수 있습니다. 이 연습에서는 디자이너를 사용 하지 않겠습니다.

6. .Tt 파일은 일반적인 용도로, 이러한 파일 중 하나를 조정 하 여 WPF 데이터 바인딩 작업을 수행 해야 합니다 .이 경우에는 ObservableCollections가 필요 합니다.  솔루션 탐색기에서 Northwind_model를 찾을 때까지 Northwind_model 노드를 확장 합니다. (*에 **있지** 않은지 확인 합니다. .Edmx 파일 바로 아래에 있는 .tt 파일입니다.

   - 의 두 항목을 <xref:System.Collections.ICollection> 로 바꿉니다 <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - 첫 번째 항목을 <xref:System.Collections.Generic.HashSet%601> <xref:System.Collections.ObjectModel.ObservableCollection%601> 51 줄로 바꿉니다. HashSet의 두 번째 항목을 바꾸지 않음

   - (334 줄)의만 발생 하는를 <xref:System.Collections.Generic> 로 바꿉니다 <xref:System.Collections.ObjectModel> .

7. **Ctrl + Shift + B** 를 눌러 프로젝트를 빌드합니다. 빌드가 완료 되 면 모델 클래스는 데이터 소스 마법사에 표시 됩니다.

   이제이 모델을 XAML 페이지에 연결 하 여 데이터를 보고, 탐색 하 고, 수정할 수 있습니다.

## <a name="databind-the-model-to-the-xaml-page"></a>모델을 XAML 페이지에 Databind
 사용자 고유의 데이터 바인딩 코드를 작성할 수 있지만 Visual Studio에서 사용자에 게 더 쉽게 수행할 수 있습니다.

1. 주 메뉴에서 **프로젝트 &#124; 새 데이터 소스 추가** 를 선택 하 여 **데이터 소스 구성 마법사**를 엽니다. 데이터베이스가 아니라 모델 클래스에 바인딩되어 있기 때문에 **개체** 를 선택 합니다.

     ![개체 원본을 사용 하는 데이터 소스 구성 마법사](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "개체 원본이 포함 된 raddata 데이터 소스 구성 마법사")

2. Customer를 선택 합니다.  (주문의 원본은 Customer의 Orders 탐색 속성에서 자동으로 생성 됩니다.)

     ![엔터티 클래스를 데이터 소스로 추가](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata 엔터티 클래스를 데이터 소스로 추가")

3. **마침**을 클릭합니다.

4. 코드 보기에서 Mainwindow.xaml로 이동 합니다. 이 예제의 목적을 위해 XAML을 매우 간단 하 게 유지할 예정입니다. Mainwindow.xaml의 제목을 좀 더 설명적인 이름으로 변경 하 고, 현재의 높이와 너비를 600 x 800로 늘립니다. 나중에 언제 든 지 변경할 수 있습니다. 이제이 세 개의 행 정의를 주 그리드에 추가 합니다. 즉, 탐색 단추에 대 한 행, 고객의 세부 정보에 대 한 한 행, 주문을 표시 하는 그리드를 위한 행을 추가 합니다.

    ```xaml
    <Grid.RowDefinitions>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="*"/>
           </Grid.RowDefinitions>
    ```

5. 이제 디자이너에서 볼 수 있도록 Mainwindow.xaml을 엽니다. 이렇게 하면 데이터 소스 창이 도구 상자 옆의 Visual Studio 창 여백에 옵션으로 표시 됩니다. 탭을 클릭 하 여 창을 열거나, **Shift + Alt + D** 를 누르거나 **다른 Windows &#124; 데이터 원본 &#124; 보기**를 선택 합니다. Customers 클래스의 각 속성을 자체의 개별 텍스트 상자에 표시할 예정입니다. 먼저 Customers 콤보 상자의 화살표를 클릭 하 고 **세부 정보**를 선택 합니다. 그런 다음 디자이너에서 가운데 행으로 이동 하려는 것을 알 수 있도록 노드를 디자인 화면의 가운데 부분으로 끕니다.  잃어버리지 경우 나중에 XAML에서 수동으로 행을 지정할 수 있습니다. 기본적으로 컨트롤은 grid 요소에 세로로 배치 되지만이 시점에서 폼에서 원하는 대로 정렬할 수 있습니다.  예를 들어 이름 텍스트 상자를 주소 위의 위쪽에 배치 하는 것이 적합할 수 있습니다. 이 문서의 샘플 응용 프로그램은 필드의 순서를 다시 정렬 하 고 두 개의 열로 다시 정렬 합니다.

     ![개별 컨트롤에 대 한 고객 데이터 원본 바인딩](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata Customers 데이터 원본 바인딩 개별 컨트롤")

     이제 코드 보기에서 `Grid` 부모 표의 행 1 (중간 행)에 새 요소를 볼 수 있습니다. 부모 표에는 `DataContext` 요소에 추가 된 CollectionViewSource를 참조 하는 특성이 있습니다 `Windows.Resources` . 해당 데이터 컨텍스트가 지정 된 경우 첫 번째 텍스트 상자가 `Address` CollectionViewSource의 현재 개체에 있는 속성에 매핑되는 "Address"에 바인딩되는 경우를 예로 들 수 `Customer` 있습니다.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. 고객이 창의 위쪽 절반에 표시 되 면 해당 주문을 아래쪽 절반에 표시 하려고 합니다. 단일 그리드 뷰 컨트롤에서 주문을 표시 합니다. 마스터-세부 데이터 바인딩이 예상 대로 작동 하려면 개별 Orders 노드가 아닌 Customers 클래스의 Orders 속성에 바인딩해야 합니다. 다음 그림에 주의 하세요. Customers 클래스의 Orders 속성을 폼의 아래쪽으로 끌어 놓으면 디자이너는 2 행에 배치 됩니다.

     ![Orders 클래스를 그리드로 끌기](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata Orders 클래스를 그리드로 끌기")

7. Visual Studio는 UI 컨트롤을 모델의 이벤트에 연결 하는 모든 바인딩 코드를 생성 했습니다. 일부 데이터를 확인 하려면 모델을 채우는 코드를 작성 해야 합니다. 먼저 MainWindow.xaml.cs로 이동 하 여 데이터 컨텍스트의 Mainwindow.xaml 클래스에 데이터 멤버를 추가 하겠습니다. 우리에 대해 생성 된이 개체는 모델의 변경 내용 및 이벤트를 추적 하는 컨트롤 처럼 동작 합니다. 여기서는 나중에 새 고객 또는 새 주문을 추가 하는 데 사용할 두 개의 구성원을 추가 합니다. 생성자 초기화 논리도 추가 합니다. 클래스의 맨 위는 다음과 같습니다.

    ```csharp
    public partial class MainWindow : Window
       {
           public Customer newCustomer { get; set; }
           public Order newOrder { get; set; }

           NorthwindEntities context = new NorthwindEntities();
           CollectionViewSource custViewSource;
           CollectionViewSource ordViewSource;

           public MainWindow()
           {
               InitializeComponent();
               newCustomer = new Customer();
               newOrder = new Order();
               custViewSource = ((CollectionViewSource)
                   (FindResource("customerViewSource")));
               ordViewSource = ((CollectionViewSource)
                   (FindResource("customerOrdersViewSource")));
               DataContext = this;
           }
    ```

     `using`Load 확장 메서드를 범위로 가져오기 위해 system.object에 대 한 지시문을 추가 합니다.

    ```csharp
    using System.Data.Entity;
    ```

     이제 아래로 스크롤하고 Window_Loaded 이벤트 처리기를 찾습니다. Visual Studio에는 microsoft에 대 한 CollectionViewSource 개체가 추가 되었습니다. 모델을 만들 때 선택한 창의 northwindentities 개체를 나타냅니다. 이제 전체 메서드가 다음과 같이 보이도록 Window_loaded에 코드를 추가 해 보겠습니다.

    ```csharp
    private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            // Load is an extension method on IQueryable,
            // defined in the System.Data.Entity namespace.
            // This method enumerates the results of the query,
            // similar to ToList but without creating a list.
            // When used with Linq to Entities this method
            // creates entity objects and adds them to the context.
            context.Customers.Load();

            // After the data is loaded call the DbSet<T>.Local property
            // to use the DbSet<T> as a binding source.
            custViewSource.Source = context.Customers.Local;
        }
    ```

8. **F5**키를 누릅니다. CollectionViewSource에 검색 된 첫 번째 고객에 대 한 세부 정보 및 데이터 표에서 해당 주문이 표시 됩니다. 서식 지정이 유용 하지 않으므로이를 해결 해 보겠습니다. 그리고 다른 레코드를 볼 수 있는 방법을 상자에 만들고 기본 CRUD 작업을 수행 합니다.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>새 고객과 주문에 대해 페이지 디자인 조정 및 그리드 추가
 Visual Studio에서 생성 되는 기본 정렬은 응용 프로그램에 적합 하지 않으므로 XAML에서 수동으로 일부 변경 작업을 수행 합니다. 또한 사용자가 새 고객 또는 새 주문을 추가할 수 있도록 일부 "양식" (실제로 그리드)이 필요 합니다.    새 고객과 주문을 추가할 수 있으려면에 데이터 바인딩되지 않은 별도의 텍스트 상자 집합이 필요 `CollectionViewSource` 합니다. 처리기 메서드에서 Visible 속성을 설정 하 여 지정 된 시간에 사용자에 게 표시 되는 그리드를 제어 합니다.

 마지막으로 주문 표에 있는 각 행에 삭제 단추를 추가 하 여 사용자가 개별 주문을 삭제할 수 있게 합니다.

 먼저 이러한 스타일을 Windows 리소스에 추가 합니다.

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

 다음으로 전체 외부 그리드를이 태그로 바꿉니다.

```xaml
<Grid >
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
     </StackPanel>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>탐색, 추가, 업데이트 및 삭제 단추 추가
 Windows Forms 응용 프로그램에서는 데이터베이스의 행을 탐색 하 고 기본 CRUD 작업을 수행 하는 단추가 포함 된 BindingNavigator 개체를 가져옵니다. WPF는 BindingNavigator를 제공 하지 않지만 쉽게 만들 수 있습니다. 페이지 표의 맨 아래 행에 있는 가로 StackPanel의 단추를 사용 하 여이 작업을 수행 하 고, 코드 숨김으로 된 메서드에 바인딩된 명령과 단추를 연결 합니다.

 명령 논리에는 (1) 명령, (2) 바인딩, (3) 단추 및 (4) 코드 숨김으로 된 명령 처리기가 fours 됩니다.

#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML에서 명령, 바인딩 및 단추 추가

1. 먼저 Mainwindow.xaml 요소 내에서 다음 명령을 추가 해 보겠습니다.

    ```xaml

     <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2. CommandBinding은 또 이벤트를 코드 숨김으로 메서드에 매핑합니다. 다음 CommandBindings 요소를 Windows .Resources closing 태그 뒤에 추가 합니다.

    ```xaml

        <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3. 이제 탐색, 추가, 삭제 및 업데이트 단추를 사용 하 여 StackPanel을 추가 해 보겠습니다. 먼저이 스타일을 Windows 리소스에 추가 합니다.

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     이제이 코드를 XAML 페이지 맨 위에 있는 외부 그리드 요소의 RowDefinitions 바로 뒤에 붙여 넣습니다.

    ```xaml
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Mainwindow.xaml 클래스에 명령 처리기 추가

1. 코드 숨김이 추가 및 삭제 메서드를 제외 하 고는 최소화 됩니다. 탐색은 CollectionViewSource의 View 속성에서 메서드를 호출 하 여 수행 합니다. DeleteOrderCommandHandler는 순서에 따라 하위 삭제를 수행 하는 방법을 보여 줍니다. 연결 된 Order_Details를 먼저 삭제 해야 합니다. UpdateCommandHandler는 컬렉션에 새 고객을 추가 하거나 텍스트 상자에서 사용자가 변경한 내용으로 기존 개체를 업데이트 합니다.

2. MainWindow.xaml.cs의 Mainwindow.xaml 클래스에 이러한 처리기 메서드를 추가 합니다. Customers 테이블의 CollectionViewSource에 다른 이름이 있는 경우 이러한 각 메서드에서 이름을 조정 해야 합니다.

    ```csharp
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToLast();
    }

    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToPrevious();
    }

    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToNext();
    }

    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToFirst();
    }

    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // If existing window is visible, then delete the customer and all their orders.
        // In a real application, you should add warnings and allow a user to cancel the operation.
        var cur = custViewSource.View.CurrentItem as Customer;

        var cust = (from c in context.Customers
                    where c.CustomerID == cur.CustomerID
                    select c).FirstOrDefault();

        if (cust != null)
        {
            foreach (var ord in cust.Orders.ToList())
            {
                Delete_Order(ord);
            }
            context.Customers.Remove(cust);
        }
        context.SaveChanges();
        custViewSource.View.Refresh();
    }

    // Commit changes from the new customer form, the new order form,
    // or edits made to the existing customer form.
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        if (newCustomerGrid.IsVisible)
        {
            // Create a new object because the old one
            // is being tracked by EF now.
            newCustomer = new Customer();
            newCustomer.Address = add_addressTextBox.Text;
            newCustomer.City = add_cityTextBox.Text;
            newCustomer.CompanyName = add_companyNameTextBox.Text;
            newCustomer.ContactName = add_contactNameTextBox.Text;
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;
            newCustomer.Country = add_countryTextBox.Text;
            newCustomer.CustomerID = add_customerIDTextBox.Text;
            newCustomer.Fax = add_faxTextBox.Text;
            newCustomer.Phone = add_phoneTextBox.Text;
            newCustomer.PostalCode = add_postalCodeTextBox.Text;
            newCustomer.Region = add_regionTextBox.Text;

            // Perform very basic validation
            if (newCustomer.CustomerID.Length == 5)
            {
                // Insert the new customer at correct position:
                int len = context.Customers.Local.Count();
                int pos = len;
                for (int i = 0; i < len; ++i)
                {
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)
                    {
                        pos = i;
                        break;
                    }
                }
                context.Customers.Local.Insert(pos, newCustomer);
                custViewSource.View.Refresh();
                custViewSource.View.MoveCurrentTo(newCustomer);
            }
            else
            {
                MessageBox.Show("CustomerID must have 5 characters.");
            }

            newCustomerGrid.Visibility = Visibility.Collapsed;
            existingCustomerGrid.Visibility = Visibility.Visible;
        }
        else if (newOrderGrid.IsVisible)
        {
            // Order ID is auto-generated so we don't set it here.
            // For CustomerID, address, etc we use the values from current customer.
            // User can modify these in the datagrid after the order is entered.

            newOrder.OrderDate = add_orderDatePicker.SelectedDate;
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;
            try
            {
                // Exercise for the reader if you are using Northwind:
                // Add the Northwind Shippers table to the model.
                // Acceptable ShipperID values are 1, 2, or 3.
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"
                    || add_ShipViaTextBox.Text == "3")
                {
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);
                }
                else
                {
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");
                    return;
                }
            }
            catch
            {
                MessageBox.Show("Ship Via must be convertible to int");
                return;
            }
            try
            {
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);
            }
            catch
            {
                MessageBox.Show("Freight must be convertible to decimal.");
                return;
            }

            // Add the order into the EF model
            context.Orders.Add(newOrder);
            ordViewSource.View.Refresh();
        }

        // Save the changes, either for a new customer, a new order
        // or an edit in an existing customer or order
        context.SaveChanges();
    }

    // Sets up the form so that user can enter data. Data is later
    // saved when user clicks Commit.
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Visible;

        // Clear all the text boxes before adding a new customer.
        foreach (var child in newCustomerGrid.Children)
        {
            var tb = child as TextBox;
            if (tb != null)
            {
                tb.Text = "";
            }
        }
    }

    private void NewOrder_click(object sender, RoutedEventArgs e)
    {
        var cust = custViewSource.View.CurrentItem as Customer;
        if (cust == null)
        {
            MessageBox.Show("No customer selected.");
            return;
        }

        newOrder.CustomerID = cust.CustomerID;

        // Get address and other mostly constant fields from
        // an existing order, if one exists
        var coll = custViewSource.Source as IEnumerable<Customer>;
        var lastOrder = (from c in coll
                         from ord in c.Orders
                         select ord).LastOrDefault();
        if (lastOrder != null)
        {
            newOrder.ShipAddress = lastOrder.ShipAddress;
            newOrder.ShipCity = lastOrder.ShipCity;
            newOrder.ShipCountry = lastOrder.ShipCountry;
            newOrder.ShipName = lastOrder.ShipName;
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;
            newOrder.ShipRegion = lastOrder.ShipRegion;
        }

        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.UpdateLayout();
        newOrderGrid.Visibility = Visibility.Visible;
    }

    // Cancels any input into the new customer form
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        add_addressTextBox.Text = "";
        add_cityTextBox.Text = "";
        add_companyNameTextBox.Text = "";
        add_contactNameTextBox.Text = "";
        add_contactTitleTextBox.Text = "";
        add_countryTextBox.Text = "";
        add_customerIDTextBox.Text = "";
        add_faxTextBox.Text = "";
        add_phoneTextBox.Text = "";
        add_postalCodeTextBox.Text = "";
        add_regionTextBox.Text = "";

        existingCustomerGrid.Visibility = Visibility.Visible;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
    }

    private void Delete_Order(Order order)
    {
        // Find the order in the EF model.
        var ord = (from o in context.Orders.Local
                   where o.OrderID == order.OrderID
                   select o).FirstOrDefault();

        // Delete all the order_details that have
        // this Order as a foreign key
        foreach (var detail in ord.Order_Details.ToList())
        {
            context.Order_Details.Remove(detail);
        }

        // Now it's safe to delete the order.
        context.Orders.Remove(ord);
        context.SaveChanges();

        // Update the data grid.
        ordViewSource.View.Refresh();
    }

    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // Get the Order in the row in which the Delete button was clicked.
        Order obj = e.Parameter as Order;
        Delete_Order(obj);
    }
    ```

3. **F5**키를 누릅니다. 데이터가 표시 되 고 탐색 단추가 예상 대로 작동 해야 합니다. 데이터를 입력 한 후 "커밋"을 클릭 하 여 새 고객 또는 주문을 모델에 추가 합니다.  "취소"를 클릭 하 여 새 고객이 나 새 주문 양식에서 저장 하지 않고 다시 백업 합니다. 텍스트 상자에서 기존 고객과 주문을 직접 편집할 수 있으며 이러한 변경 내용은 자동으로 모델에 기록 됩니다.

## <a name="see-also"></a>관련 항목
 [.Net 용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework 설명서](https://msdn.microsoft.com/data/ee712907.aspx)
