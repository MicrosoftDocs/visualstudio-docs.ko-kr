---
title: L2DBForm.xaml 소스 코드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc0ec53c35f87751efe78359f582e5f4297143c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664272"
---
# <a name="l2dbformxaml-source-code"></a>L2DBForm.xaml 원본 코드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 [LINQ to XML 예제를 사용한 WPF 데이터 바인딩](../designers/wpf-data-binding-using-linq-to-xml-example.md)에 대한 XAML 소스 파일인 L2DBForm.xaml을 제공하며 이 파일에 대해 설명합니다.

## <a name="overall-ui-structure"></a>전체적인 UI 구조
 WPF 프로젝트에 일반적이듯이 이 파일에는 부모 요소가 하나 포함되어 있습니다. 이 부모 요소는 <xref:System.Windows.Window> 네임스페이스의 파생된 클래스 `L2XDBFrom` 과 연결된 `LinqToXmlDataBinding` XML 요소입니다.

 클라이언트 영역은 연한 파랑색 배경이 제공되는 <xref:System.Windows.Controls.StackPanel> 에 포함되어 있습니다. 이 패널에는 <xref:System.Windows.Controls.DockPanel> 표시줄로 구분된 <xref:System.Windows.Controls.Separator> UI 섹션이 4개 포함되어 있습니다. 이러한 섹션의 목적은 **이전 항목** 의 [설명](../designers/walkthrough-linqtoxmldatabinding-example.md)에 설명되어 있습니다.

 각 섹션에는 해당 섹션을 식별하는 레이블이 포함되어 있습니다. 처음 두 섹션에서 이 레이블은 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>을 사용하여 90도 회전됩니다. 섹션의 나머지 부분에는 해당 섹션의 목적에 적합한 텍스트 블록, 텍스트 상자, 단추 등의 UI 요소가 포함되어 있습니다. 때때로 자식 <xref:System.Windows.Controls.StackPanel> 이 이러한 자식 컨트롤을 정렬하는 데 사용됩니다.

## <a name="window-resource-section"></a>창 리소스 섹션
 9번째 줄의 여는 `<Window.Resources>` 태그는 창 리소스 섹션의 시작을 나타냅니다. 창 리소스 섹션은 35번째 줄의 닫는 태그에서 끝납니다.

 11-25번째 줄에 있는 `<ObjectDataProvider>` 태그는 <xref:System.Windows.Data.ObjectDataProvider>를 소스로 사용하는 `LoadedBooks`라는 <xref:System.Xml.Linq.XElement> 를 선언합니다. 이 <xref:System.Xml.Linq.XElement> 는 포함된 XML 문서( `CDATA` 요소)의 구문을 분석하여 초기화됩니다. 포함된 XML 문서를 선언하는 경우와 이 문서의 구문을 분석하는 경우에도 공백이 유지됩니다. 이 작업은 원시 XML을 표시하는 데 사용되는 <xref:System.Windows.Controls.TextBlock> 컨트롤에 특별한 XML 서식 지정 기능이 없기 때문에 수행되었습니다.

 마지막으로 <xref:System.Windows.DataTemplate> 이라는 `BookTemplate` 이 28-34번째 줄에 정의되어 있습니다. 이 템플릿은 **Book List** UI 섹션에 항목을 표시하는 데 사용됩니다. 이 템플릿에서는 데이터 바인딩과 LINQ to XML 동적 속성을 사용하여 다음 할당을 통해 책 ID와 책 이름을 검색합니다.

```
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a>데이터 바인딩 코드
 <xref:System.Windows.DataTemplate> 요소 외에도 데이터 바인딩이 이 파일의 여러 위치에서 사용됩니다.

 38번째 줄의 여는 `<StackPanel>` 태그에서 이 패널의 <xref:System.Windows.FrameworkElement.DataContext%2A> 속성은 `LoadedBooks` 데이터 공급자로 설정됩니다.

```
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

 이를 통해(46번째 줄) <xref:System.Windows.Controls.TextBlock> 이라는 `tbRawXml` 이 이 데이터 공급자의 `Xml` 속성에 바인딩하여 원시 XML을 표시할 수 있습니다.

```
Text="{Binding Path=Xml}"
```

 58-62번째 줄의 <xref:System.Windows.Controls.ListBox> Book List **UI 섹션에 있는** 는 표시 항목에 대한 템플릿을 창 리소스 섹션에 정의된 `BookTemplate` 으로 설정합니다.

```
ItemTemplate ="{StaticResource BookTemplate}"
```

 그런 다음 59-62번째 줄에서 책의 실제 값이 이 목록 상자에 바인딩됩니다.

```
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

 세 번째 UI 섹션인 **Edit Selected Book**은 먼저 부모 <xref:System.Windows.FrameworkElement.DataContext%2A> 의 <xref:System.Windows.Controls.StackPanel> 를 **Book List** UI 섹션(82번째 줄)에서 현재 선택된 항목에 바인딩합니다.

```
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

 그런 다음 양방향 데이터 바인딩을 사용하므로 책 요소의 현재 값이 이 패널의 두 텍스트 상자에서 표시되고 업데이트됩니다. 동적 속성에 대한 데이터 바인딩은 `BookTemplate` 데이터 템플릿에서 사용되는 것과 유사합니다.

```
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

 마지막 UI 섹션인 **Add New Book**에서는 XAML 코드에서 데이터 바인딩을 사용하지 않습니다. 이러한 코드는 L2DBForm.xaml.cs 파일의 이벤트 처리 코드에 있습니다.

## <a name="example"></a>예제

### <a name="description"></a>설명

> [!NOTE]
> 줄 번호를 추적하기 쉽도록 아래의 코드를 Visual Studio의 C# 소스 코드 편집기와 같은 코드 편집기에 복사하는 것이 좋습니다.

### <a name="code"></a>코드

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>

```

### <a name="comments"></a>주석
 WPF UI 요소와 연결된 이벤트 처리기의 C# 소스 코드는 [L2DBForm.xaml.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md)를 참조하세요.

## <a name="see-also"></a>관련 항목
 [연습: LinqToXmlDataBinding 예제](../designers/walkthrough-linqtoxmldatabinding-example.md) [L2DBForm.xaml.cs 소스 코드](../designers/l2dbform-xaml-cs-source-code.md)
