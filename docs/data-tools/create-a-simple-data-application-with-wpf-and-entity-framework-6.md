---
title: WPF 및 Entity Framework 6을 사용 하는 간단한 데이터 응용 프로그램
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4aa978098c459d9e55ef0dc1423080357e067a5b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282763"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF 및 Entity Framework 6을 사용하여 간단한 데이터 애플리케이션 만들기

이 연습에서는 Visual Studio에서 기본 "데이터 폼" 응용 프로그램을 만드는 방법을 보여 줍니다. 앱은 SQL Server LocalDB, Northwind 데이터베이스 Entity Framework 6 (Entity Framework Core 아님)을 사용 하 고 .NET Framework에 대해 Windows Presentation Foundation를 사용 합니다 (.NET Core 아님). 마스터-세부 보기를 사용 하 여 기본 데이터 바인딩을 수행 하는 방법을 보여 줍니다. 또한 **다음으로 이동**, **이전**으로 이동, **처음으로**이동, **끝으로 이동**, **업데이트** 및 **삭제**단추가 포함 된 사용자 지정 바인딩 탐색기가 있습니다.

이 문서에서는 Visual Studio에서 데이터 도구를 사용 하는 방법을 집중적으로 설명 하며, 기본 기술에 대해 설명 하지 않습니다. XAML, Entity Framework 및 SQL에 대 한 기본적인 지식이 있다고 가정 합니다. 또한이 예제에서는 WPF 응용 프로그램의 표준인 MVVM (모델-뷰-ViewModel) 아키텍처를 보여 주지 않습니다. 그러나이 코드를 수정 하지 않은 사용자 고유의 MVVM 응용 프로그램으로 복사할 수 있습니다.

## <a name="install-and-connect-to-northwind"></a>Northwind에 설치 및 연결

이 예에서는 SQL Server Express LocalDB 및 Northwind 샘플 데이터베이스를 사용 합니다. 해당 제품에 대 한 ADO.NET 데이터 공급자가 Entity Framework를 지 원하는 경우 다른 SQL 데이터베이스 제품과 함께 작동 해야 합니다.

1. LocalDB SQL Server Express 없는 경우 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 또는 **Visual Studio 설치 관리자**를 통해 설치 합니다. **Visual Studio 설치 관리자**에서 **.NET 데스크톱 개발** 워크로드의 일부로 또는 개별 구성 요소로서 SQL Server Express LocalDB를 설치할 수 있습니다.

2. 다음 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 **SQL Server 개체 탐색기** 창을 엽니다. **SQL Server 개체 탐색기** 는 **데이터 저장소 및 처리** 워크 로드의 일부로 **Visual Studio 설치 관리자**에 설치 됩니다. **SQL Server** 노드를 확장 합니다. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 **새 쿼리**를 선택 합니다.

       쿼리 편집기 창이 열립니다.

    2. [Northwind transact-sql 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 를 클립보드에 복사 합니다. 이 T-sql 스크립트는 Northwind 데이터베이스를 처음부터 만들어 데이터로 채웁니다.

    3. T-sql 스크립트를 쿼리 편집기에 붙여 넣은 다음 **실행** 단추를 선택 합니다.

       잠시 후 쿼리 실행이 완료 되 고 Northwind 데이터베이스가 만들어집니다.

3. Northwind에 대 한 [새 연결을 추가](../data-tools/add-new-connections.md) 합니다.

## <a name="configure-the-project"></a>프로젝트 구성

1. Visual Studio에서 새 c # **WPF 앱** 프로젝트를 만듭니다.

2. Entity Framework 6 용 NuGet 패키지를 추가 합니다. **솔루션 탐색기**에서 프로젝트 노드를 선택 합니다. 주 메뉴에서 **프로젝트**  >  **NuGet 패키지 관리**를 선택 합니다.

     ![NuGet 패키지 관리 메뉴 항목](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. **NuGet 패키지 관리자**에서 **찾아보기** 링크를 클릭 합니다. Entity Framework은 목록의 맨 위 패키지인 것입니다. 오른쪽 창에서 **설치** 를 클릭 하 고 프롬프트를 따릅니다. 설치가 완료 되 면 출력 창에 사용자에 게 알려 줍니다.

     ![NuGet 패키지 Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. 이제 Visual Studio를 사용 하 여 Northwind 데이터베이스를 기반으로 모델을 만들 수 있습니다.

## <a name="create-the-model"></a>모델 만들기

1. **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목**추가를 선택 합니다. 왼쪽 창의 c # 노드 아래에서 **데이터** 를 선택 하 고 가운데 창에서 **ADO.NET 엔터티 데이터 모델**를 선택 합니다.

   ![Entity Framework 모델 새 항목](../data-tools/media/raddata-ef-new-project-item.png)

2. 모델을 호출 `Northwind_model` 하 고 **확인을**선택 합니다. **엔터티 데이터 모델 마법사** 가 열립니다. **데이터베이스에서 EF Designer** 를 선택 하 고 **다음**을 클릭 합니다.

   ![데이터베이스의 EF 모델](../data-tools/media/raddata-ef-model-from-database.png)

3. 다음 화면에서 LocalDB Northwind 연결 (예: (localdb) \MSSQLLocalDB)을 입력 하거나 선택 하 고 Northwind 데이터베이스를 지정한 후 **다음**을 클릭 합니다.

4. 마법사의 다음 페이지에서 Entity Framework 모델에 포함할 테이블, 저장 프로시저 및 기타 데이터베이스 개체를 선택 합니다. 트리 뷰에서 dbo 노드를 확장 하 고 **고객**, **주문**및 **주문 세부 정보**를 선택 합니다. 기본값을 선택 된 채로 두고 **마침**을 클릭 합니다.

    ![모델에 대 한 데이터베이스 개체 선택](../data-tools/media/raddata-choose-ef-objects.png)

5. 마법사는 Entity Framework 모델을 나타내는 c # 클래스를 생성 합니다. 클래스는 일반 c # 클래스 이며 WPF 사용자 인터페이스에 바인딩하는 것입니다. *.Edmx* 파일은 클래스를 데이터베이스의 개체와 연결 하는 관계 및 기타 메타 데이터를 설명 합니다. *.Tt* 파일은 모델에서 작동 하는 코드를 생성 하 고 변경 내용을 데이터베이스에 저장 하는 T4 템플릿입니다. Northwind_model 노드 아래 **솔루션 탐색기** 에서 이러한 모든 파일을 볼 수 있습니다.

      ![EF 모델 파일 솔루션 탐색기](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    *.Edmx* 파일의 디자이너 화면에서는 모델의 일부 속성 및 관계를 수정할 수 있습니다. 이 연습에서는 디자이너를 사용 하지 않겠습니다.

6. *.Tt* 파일은 일반적인 용도로, 이러한 파일 중 하나를 조정 하 여 WPF 데이터 바인딩 작업을 수행 해야 합니다 .이 경우에는 ObservableCollections가 필요 합니다. **솔루션 탐색기**에서 *Northwind_model*를 찾을 때까지 Northwind_model 노드를 확장 합니다. (에 있지 않은지 확인 *합니다. Context.tt* 파일은 *.edmx* 파일 바로 아래에 있습니다.

   - 의 두 항목을 <xref:System.Collections.ICollection> 로 바꿉니다 <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - 첫 번째 항목을 <xref:System.Collections.Generic.HashSet%601> <xref:System.Collections.ObjectModel.ObservableCollection%601> 51 줄로 바꿉니다. HashSet의 두 번째 항목을 바꾸지 마십시오.

   - (431 줄)의만 발생 하는를 <xref:System.Collections.Generic> 로 바꿉니다 <xref:System.Collections.ObjectModel> .

7. **Ctrl** + **Shift** + **B** 를 눌러 프로젝트를 빌드합니다. 빌드가 완료 되 면 모델 클래스는 데이터 소스 마법사에 표시 됩니다.

이제이 모델을 XAML 페이지에 연결 하 여 데이터를 보고, 탐색 하 고, 수정할 수 있습니다.

## <a name="databind-the-model-to-the-xaml-page"></a>모델을 XAML 페이지에 Databind

사용자 고유의 데이터 바인딩 코드를 작성할 수 있지만 Visual Studio에서 사용자에 게 더 쉽게 수행할 수 있습니다.

1. 주 메뉴에서 **프로젝트**  >  **새 데이터 소스 추가** 를 선택 하 여 **데이터 소스 구성 마법사**를 엽니다. 데이터베이스가 아니라 모델 클래스에 바인딩되어 있기 때문에 **개체** 를 선택 합니다.

     ![개체 원본을 사용 하는 데이터 소스 구성 마법사](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. 프로젝트에 대 한 노드를 확장 하 고 **Customer**를 선택 합니다. 주문의 원본은 Customer의 Orders 탐색 속성에서 자동으로 생성 됩니다.

     ![엔터티 클래스를 데이터 소스로 추가](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. **마침**을 클릭합니다.

4. 코드 보기에서 *mainwindow.xaml* 로 이동 합니다. 이 예제의 목적을 위해 XAML을 간단 하 게 유지 합니다. Mainwindow.xaml의 제목을 좀 더 설명적인 이름으로 변경 하 고, 현재의 높이와 너비를 600 x 800로 늘립니다. 나중에 언제 든 지 변경할 수 있습니다. 이제 다음 세 개의 행 정의를 주 그리드에 추가 하 고, 탐색 단추를 위한 행 하나, 고객 세부 정보에 대 한 행, 주문을 표시 하는 그리드에 대 한 행을 추가 합니다.

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. 이제 디자이너에서 볼 수 있도록 *mainwindow.xaml* 을 엽니다. 이렇게 하면 **데이터 소스** 창이 **도구 상자**옆의 Visual Studio 창 여백에 옵션으로 표시 됩니다. 탭을 클릭 하 여 창을 열거나 **Shift** + **Alt** + **D** 를 누르거나 **View**  >  **다른 Windows**  >  **데이터 원본**보기를 선택 합니다. Customers 클래스의 각 속성을 자체의 개별 텍스트 상자에 표시할 예정입니다. 먼저 **Customers** 콤보 상자의 화살표를 클릭 하 고 **세부 정보**를 선택 합니다. 그런 다음 디자이너에서 가운데 행으로 이동할 것임을 알 수 있도록 노드를 디자인 화면의 가운데 부분으로 끕니다. 잃어버리지 경우 나중에 XAML에서 수동으로 행을 지정할 수 있습니다. 기본적으로 컨트롤은 grid 요소에 세로로 배치 되지만이 시점에서 폼에서 원하는 대로 정렬할 수 있습니다. 예를 들어 **이름** 텍스트 상자를 주소 위의 위쪽에 배치 하는 것이 적합할 수 있습니다. 이 문서의 샘플 응용 프로그램은 필드의 순서를 다시 정렬 하 고 두 개의 열로 다시 정렬 합니다.

     ![개별 컨트롤에 대 한 고객 데이터 원본 바인딩](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     이제 코드 보기에서 `Grid` 부모 표의 행 1 (중간 행)에 새 요소를 볼 수 있습니다. 부모 표에는 `DataContext` 요소에 추가 된 CollectionViewSource를 참조 하는 특성이 있습니다 `Windows.Resources` . 해당 데이터 컨텍스트가 지정 된 경우 첫 번째 텍스트 상자를 **Address**에 바인딩하면 해당 이름이 `Address` `Customer` collectionviewsource의 현재 개체의 속성에 매핑됩니다.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. 고객이 창의 위쪽 절반에 표시 되 면 해당 주문을 아래쪽 절반에 표시 하려고 합니다. 단일 그리드 뷰 컨트롤에 주문을 표시 합니다. 마스터-세부 데이터 바인딩이 예상 대로 작동 하려면 별도의 Orders 노드가 아닌 Customers 클래스의 Orders 속성에 바인딩해야 합니다. Customers 클래스의 Orders 속성을 폼의 아래쪽으로 끌어 놓으면 디자이너는 2 행에 배치 됩니다.

     ![Orders 클래스를 그리드로 끌기](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio는 UI 컨트롤을 모델의 이벤트에 연결 하는 모든 바인딩 코드를 생성 했습니다. 일부 데이터를 확인 하려면 모델을 채우는 코드를 작성 해야 합니다. 먼저 *MainWindow.xaml.cs* 로 이동 하 여 데이터 컨텍스트의 mainwindow.xaml 클래스에 데이터 멤버를 추가 합니다. 사용자를 위해 생성 된이 개체는 모델의 변경 내용 및 이벤트를 추적 하는 컨트롤 처럼 동작 합니다. 또한 고객과 주문의 CollectionViewSource 데이터 멤버와 관련 생성자 초기화 논리를 추가 합니다. 클래스의 맨 위는 다음과 같습니다.

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     `using`Load 확장 메서드를 범위로 가져오기 위해 system.object에 대 한 지시문을 추가 합니다.

     ```csharp
     using System.Data.Entity;
     ```

     이제 아래로 스크롤하고 이벤트 처리기를 찾습니다 `Window_Loaded` . Visual Studio에서 CollectionViewSource 개체를 추가 했습니다. 모델을 만들 때 선택한 창의 northwindentities 개체를 나타냅니다. 이를 이미 추가 했으므로 여기에 필요 하지 않습니다. 이제 메서드가 다음과 같이 표시 되도록에서 코드를 바꿉니다 `Window_Loaded` .

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. **F5**키를 누릅니다. CollectionViewSource로 검색 된 첫 번째 고객에 대 한 세부 정보가 표시 됩니다. 또한 데이터 표에 해당 주문이 표시 되어야 합니다. 서식 지정이 유용 하지 않으므로이를 해결 해 보겠습니다. 다른 레코드를 보고 기본 CRUD 작업을 수행 하는 방법도 만들 수 있습니다.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>새 고객과 주문에 대해 페이지 디자인 조정 및 그리드 추가

Visual Studio에서 생성 되는 기본 정렬은 응용 프로그램에 적합 하지 않으므로 코드에 복사할 최종 XAML을 여기에 제공 합니다. 사용자가 새 고객 또는 주문을 추가할 수 있도록 일부 "양식" (실제로는 그리드)도 필요 합니다. 새 고객과 주문을 추가할 수 있으려면에 데이터 바인딩되지 않은 별도의 텍스트 상자 집합이 필요 `CollectionViewSource` 합니다. 처리기 메서드에서 Visible 속성을 설정 하 여 언제 든 지 사용자가 볼 수 있는 그리드를 제어 합니다. 마지막으로 주문 표에 있는 각 행에 삭제 단추를 추가 하 여 사용자가 개별 주문을 삭제할 수 있게 합니다.

먼저 Mainwindow.xaml의 요소에 이러한 스타일을 추가 `Windows.Resources` *합니다*.

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
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
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
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>탐색, 추가, 업데이트 및 삭제 단추를 추가 합니다.

Windows Forms 응용 프로그램에서는 데이터베이스의 행을 탐색 하 고 기본 CRUD 작업을 수행 하는 단추가 포함 된 BindingNavigator 개체를 가져옵니다. WPF는 BindingNavigator를 제공 하지 않지만 쉽게 만들 수 있습니다. 이 작업을 수행 하려면 가로 StackPanel 내의 단추를 사용 하 고 단추를 코드의 메서드에 바인딩된 명령과 연결 합니다.

명령 논리에는 (1) 명령, (2) 바인딩, (3) 단추 및 (4) 코드 숨김으로 된 명령 처리기의 네 부분이 있습니다.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML에서 명령, 바인딩 및 단추 추가

1. 먼저 *mainwindow.xaml* 파일의 요소 내에 명령을 추가 합니다 `Windows.Resources` .

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

2. CommandBinding은 이벤트를 `RoutedUICommand` 코드 숨김으로 메서드에 매핑합니다. `CommandBindings`닫는 태그 뒤에이 요소를 추가 합니다 `Windows.Resources` .

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

3. 이제 `StackPanel` 탐색, 추가, 삭제 및 업데이트 단추를 사용 하 여를 추가 합니다. 먼저이 스타일을에 추가 합니다 `Windows.Resources` .

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     그런 다음이 코드를 `RowDefinitions` 외부 요소에 대 한 바로 뒤에 `Grid` XAML 페이지의 맨 위에 붙여넣습니다.

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Mainwindow.xaml 클래스에 명령 처리기 추가

코드 숨김이 추가 및 삭제 메서드를 제외 하 고는 최소화 됩니다. 탐색은 CollectionViewSource의 View 속성에서 메서드를 호출 하 여 수행 됩니다. 는 `DeleteOrderCommandHandler` 순서에 따라 하위 삭제를 수행 하는 방법을 보여 줍니다. 연결 된 Order_Details를 먼저 삭제 해야 합니다. 는 `UpdateCommandHandler` 컬렉션에 새 고객 또는 주문을 추가 하거나 사용자가 텍스트 상자에서 변경한 내용으로 기존 고객 또는 주문을 업데이트 합니다.

*MainWindow.xaml.cs*의 mainwindow.xaml 클래스에 이러한 처리기 메서드를 추가 합니다. Customers 테이블의 CollectionViewSource에 다른 이름이 있는 경우 다음 각 방법에서 이름을 조정 해야 합니다.

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>애플리케이션 실행

디버깅을 시작하려면 **F5** 키를 누릅니다. 표에서 customer 및 order 데이터를 채우고 탐색 단추가 예상 대로 작동 해야 합니다. 데이터를 입력 한 후 새 고객 또는 주문을 모델에 추가 하려면 **커밋** 을 클릭 합니다. 데이터를 저장 하지 않고 새 고객 또는 새 주문 양식으로 돌아가려면 **취소** 를 클릭 합니다. 텍스트 상자에서 기존 고객과 주문을 직접 편집할 수 있으며 이러한 변경 내용은 자동으로 모델에 기록 됩니다.

## <a name="see-also"></a>참조

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework 설명서](/ef/)
