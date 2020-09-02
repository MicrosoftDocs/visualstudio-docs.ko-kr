---
title: WPF 소개 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b33c558187fd32ef7cbd420dce8d627ddc944d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664342"
---
# <a name="introduction-to-wpf"></a>WPF 소개
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WPF(Windows Presentation Foundation)를 사용하면 시각적으로 뛰어난 사용자 환경을 통해 Windows용 데스크톱 클라이언트 애플리케이션을 만들 수 있습니다.

 ![Contoso Healthcare UI 샘플](../designers/media/wpfintrofigure24.png "WPFIntroFigure24")

 WPF의 핵심은 최신 그래픽 하드웨어를 활용하도록 작성된 해상도 독립적인 벡터 기반 렌더링 엔진입니다. WPF는 XAML(Extensible Application Markup Language), 컨트롤, 데이터 바인딩, 레이아웃, 2차원 및 3차원 그래픽, 애니메이션, 스타일, 템플릿, 문서, 미디어, 텍스트 및 입력 체계를 포함하는 포괄적인 애플리케이션 개발 기능을 사용하여 핵심을 확장합니다. WPF는 .NET Framework에 포함되어 있으므로 .NET Framework 클래스 라이브러리의 다른 요소를 통합하는 애플리케이션을 빌드할 수 있습니다.

 이 개요는 초보자를 위한 것이며 WPF의 주요 기능 및 개념에 대해 설명합니다.

## <a name="programming-with-wpf"></a><a name="Programming_with_WPF"></a> WPF를 사용한 프로그래밍
 WPF는 대부분 <xref:System.Windows> 네임스페이스에 있는 .NET Framework 형식의 하위 집합으로 존재합니다. 이전에 ASP.NET 및 Windows Forms와 같은 관리되는 기술을 사용하여 .NET Framework로 애플리케이션을 빌드한 적이 있는 경우 기본적인 WPF 프로그래밍 환경이 친숙할 것입니다. 모두 C# 또는 Visual Basic과 같은 원하는 .NET 프로그래밍 언어를 사용하여 클래스를 인스턴스화하고, 속성을 설정하고, 메서드를 호출하고, 이벤트를 처리합니다.

 WPF에는 속성 및 이벤트를 향상시키는 [종속성 속성](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx) 및 [라우트된 이벤트](https://msdn.microsoft.com/library/ms742806\(v=vs.100\).aspx)와 같은 추가 프로그래밍 구문이 포함되어 있습니다.

## <a name="markup-and-code-behind"></a><a name="Markup_And_Codebehind"></a> 태그 및 코드 숨김
 WPF를 사용하면 ASP.NET 개발자에게 익숙한 환경인 *태그* 및 *코드 숨김*둘 다를 통해 애플리케이션을 개발할 수 있습니다. 일반적으로 XAML 태그를 사용하여 애플리케이션의 모양을 구현하고 관리되는 프로그래밍 언어(코드 숨김)를 사용하여 해당 동작을 구현합니다. 모양 및 동작의 이러한 분리는 다음과 같은 이점이 있습니다.

- 모양 관련 태그가 동작 관련 코드와 밀접하게 결합되지 않으므로 개발 및 유지 관리 비용이 줄어듭니다.

- 디자이너가 애플리케이션의 동작을 구현하는 개발자와 동시에 애플리케이션의 모양을 구현할 수 있으므로 개발이 보다 효율적입니다.

- WPF 애플리케이션에 대한[전역화 및 지역화](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx) 가 간소화됩니다.

  다음은 WPF 태그 및 코드 숨김에 대한 간략한 소개입니다.

### <a name="markup"></a>태그
 XAML은 선언적으로 애플리케이션의 모양을 구현하는 데 사용되는 XML 기반 태그 언어입니다. 일반적으로 창, 대화 상자, 페이지 및 사용자 정의 컨트롤을 만들고 컨트롤, 도형 및 그래픽으로 채우는 데 사용됩니다.

 다음 예제에서는 XAML을 사용하여 단일 단추가 포함된 창의 모양을 구현합니다.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

 특히, 이 XAML은 각각 `Window` 및 `Button` 요소를 사용하여 창과 단추를 정의합니다. 각 요소는 창의 제목 표시줄 텍스트를 지정하는 `Window` 요소의 `Title` 특성과 같은 특성으로 구성됩니다. 런타임에 WPF는 태그에 정의된 요소와 특성을 WPF 클래스 인스턴스로 변환합니다. 예를 들어 `Window` 요소는 <xref:System.Windows.Window.Title%2A> 속성이 `Title` 특성의 값인 <xref:System.Windows.Window> 클래스 인스턴스로 변환됩니다.  

 다음 그림은 이전 예제에서 XAML로 정의된 UI(사용자 인터페이스)를 보여 줍니다.

 ![단추가 있는 창](../designers/media/wpfintrofigure10.png "WPFIntroFigure10")

 XAML은 XML 기반이기 때문에 XAML로 작성한 UI는 [요소 트리](https://msdn.microsoft.com/library/ms753391\(v=vs.100\).aspx)라고 하는 중첩된 요소 계층 구조로 어셈블됩니다. 요소 트리는 UI를 만들고 관리하는 논리적이고 직관적인 방법을 제공합니다.

### <a name="code-behind"></a>코드 숨김
 애플리케이션의 기본 동작은 이벤트 처리(예: 메뉴, 도구 모음 또는 단추 클릭) 및 응답으로 비즈니스 논리 및 데이터 액세스 논리 호출을 포함하여 사용자 조작에 응답하는 기능을 구현하는 것입니다. WPF에서 이 동작은 일반적으로 태그와 연결된 코드에서 구현됩니다. 이러한 종류의 코드를 코드 숨김이라고 합니다. 다음 예제에서는 이전 예제의 업데이트된 태그 및 코드 숨김을 보여 줍니다.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox 

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI 
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace

```

 이 예제에서 코드 숨김은 <xref:System.Windows.Window> 클래스에서 파생된 클래스를 구현합니다. `x:Class` 특성은 태그를 코드 숨김 클래스와 연결하는 데 사용됩니다. `InitializeComponent`는 코드 숨김 클래스를 사용하여 태그에서 정의된 UI를 병합하기 위해 코드 숨김 클래스의 생성자에서 호출됩니다. `InitializeComponent`응용 프로그램을 빌드할 때이 생성 됩니다 .이 경우에는를 수동으로 구현 하지 않아도 됩니다. 및를 조합 `x:Class` 하면 `InitializeComponent` 생성 될 때마다 구현이 올바르게 초기화 됩니다. 코드 숨김 클래스는 단추의 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트에 대한 이벤트 처리기도 구현합니다. 단추를 클릭하면 이벤트 처리기가 <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> 메서드를 호출하여 메시지 상자를 표시합니다.

 다음 그림은 단추를 클릭할 때의 결과를 보여 줍니다.

 ![MessageBox](../designers/media/wpfintrofigure25.png "WPFIntroFigure25")

## <a name="controls"></a><a name="Controls"></a> 제어가
 애플리케이션 모델에서 제공하는 사용자 환경은 생성된 컨트롤입니다. WPF에서 "컨트롤"은 창이나 페이지에서 호스트되고 사용자 인터페이스가 있으며 일부 동작을 구현하는 WPF 클래스의 한 범주에 적용되는 포괄적인 용어입니다.

 자세한 내용은 [컨트롤](https://msdn.microsoft.com/library/3f255a8a-35a8-4712-9065-472ff7d75599)을 참조 하세요.

### <a name="wpf-controls-by-function"></a>기능별 WPF 컨트롤
 기본 제공 WPF 컨트롤은 다음과 같습니다.

- **단추**: <xref:System.Windows.Controls.Button> 및 <xref:System.Windows.Controls.Primitives.RepeatButton>

- **데이터 표시**: <xref:System.Windows.Controls.DataGrid> , <xref:System.Windows.Controls.ListView> 및 <xref:System.Windows.Controls.TreeView>

- **날짜 표시 및 선택**: <xref:System.Windows.Controls.Calendar> 및 <xref:System.Windows.Controls.DatePicker>

- **대화 상자**: <xref:Microsoft.Win32.OpenFileDialog> , <xref:System.Windows.Controls.PrintDialog> 및 <xref:Microsoft.Win32.SaveFileDialog>

- **디지털 잉크**: <xref:System.Windows.Controls.InkCanvas> 및 <xref:System.Windows.Controls.InkPresenter>

- **문서**: <xref:System.Windows.Controls.DocumentViewer> , <xref:System.Windows.Controls.FlowDocumentPageViewer> , <xref:System.Windows.Controls.FlowDocumentReader> , <xref:System.Windows.Controls.FlowDocumentScrollViewer> 및 <xref:System.Windows.Controls.StickyNoteControl>

- **입력**: <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.RichTextBox> 및 <xref:System.Windows.Controls.PasswordBox>

- **레이아웃**: <xref:System.Windows.Controls.Border> , <xref:System.Windows.Controls.Primitives.BulletDecorator> , <xref:System.Windows.Controls.Canvas> , <xref:System.Windows.Controls.DockPanel> , <xref:System.Windows.Controls.Expander> , <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox> <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.ResizeGrip> <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.Primitives.ScrollBar> <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Primitives.Thumb> <xref:System.Windows.Controls.Viewbox> <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window> <xref:System.Windows.Controls.WrapPanel> ,,,,,,,,,,,,, 및

- **미디어**: <xref:System.Windows.Controls.Image> , <xref:System.Windows.Controls.MediaElement> 및 <xref:System.Windows.Controls.SoundPlayerAction>

- **메뉴**: <xref:System.Windows.Controls.ContextMenu> , <xref:System.Windows.Controls.Menu> 및 <xref:System.Windows.Controls.ToolBar>

- **탐색**: <xref:System.Windows.Controls.Frame> , <xref:System.Windows.Documents.Hyperlink> , <xref:System.Windows.Controls.Page> , <xref:System.Windows.Navigation.NavigationWindow> 및 <xref:System.Windows.Controls.TabControl>

- **선택**: <xref:System.Windows.Controls.CheckBox> , <xref:System.Windows.Controls.ComboBox> , <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.RadioButton> 및 <xref:System.Windows.Controls.Slider>

- **사용자 정보**: <xref:System.Windows.Controls.AccessText> ,,,,, <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.ProgressBar> <xref:System.Windows.Controls.Primitives.StatusBar> <xref:System.Windows.Controls.TextBlock> 및 <xref:System.Windows.Controls.ToolTip>

## <a name="input-and-commanding"></a><a name="Input_And_Commanding"></a> 입력 및 명령
 컨트롤은 대체로 사용자 입력을 감지하고 응답합니다. [WPF 입력 시스템](https://msdn.microsoft.com/library/ms754010\(v=vs.100\).aspx) 은 직접 및 라우트된 이벤트를 사용하여 텍스트 입력, 포커스 관리 및 마우스 위치 지정을 지원합니다.

 애플리케이션에 복잡한 입력 요구 사항이 있는 경우가 많습니다. WPF는 사용자 입력 작업을 이러한 작업에 응답하는 코드에서 분리하는 [명령 시스템](https://msdn.microsoft.com/library/ms752308\(v=vs.100\).aspx) 을 제공합니다.

## <a name="layout"></a><a name="Layout"></a> 윤곽
 사용자 인터페이스를 만들 때 위치 및 크기별로 컨트롤을 정렬하여 레이아웃을 구성합니다. 모든 레이아웃의 주요 요구 사항은 창 크기와 표시 설정의 변경 내용에 맞게 조정되는 것입니다. 이러한 상황에서 레이아웃을 조정하는 코드를 작성하도록 요구하는 대신 WPF는 확장 가능한 뛰어난 레이아웃 시스템을 제공합니다.

 이 레이아웃 시스템의 토대는 상대 위치 지정으로, 변화하는 창과 표시 조건에 맞게 조정하는 기능을 향상시킵니다. 또한 이 레이아웃 시스템은 레이아웃을 결정하기 위한 컨트롤 간의 협상을 관리합니다. 협상은 2단계 프로세스입니다. 첫 번째로, 컨트롤이 필요한 위치 및 크기를 부모에게 알립니다. 두 번째로, 부모가 사용할 수 있는 공간을 컨트롤에 알립니다.

 이 레이아웃 시스템은 기본 WPF 클래스를 통해 자식 컨트롤에 노출됩니다. 그리드, 스택 및 도킹과 같은 일반적인 레이아웃을 위해 WPF는 여러 레이아웃 컨트롤을 포함합니다.

- <xref:System.Windows.Controls.Canvas>: 자식 컨트롤이 자체 레이아웃을 제공합니다.

- <xref:System.Windows.Controls.DockPanel>: 자식 컨트롤이 패널 가장자리에 맞춰집니다.

- <xref:System.Windows.Controls.Grid>: 자식 컨트롤이 행 및 열별로 배치됩니다.

- <xref:System.Windows.Controls.StackPanel>: 자식 컨트롤이 가로 또는 세로로 포개집니다.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: 자식 컨트롤이 가상화되고 가로 또는 세로 방향인 한 줄에 정렬됩니다.

- <xref:System.Windows.Controls.WrapPanel>: 자식 컨트롤이 왼쪽에서 오른쪽 순서로 배치되고 공간에 허용되는 것보다 더 많은 컨트롤이 현재 줄에 있는 경우 다음 줄로 줄 바꿈됩니다.

  다음 예제에서는 <xref:System.Windows.Controls.DockPanel> 하나를 사용하여 여러 <xref:System.Windows.Controls.TextBox> 컨트롤을 레이아웃합니다.

  [!code-xml[IntroToWPFSnippets#LayoutMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/LayoutWindow.xaml#layoutmarkup)]

  <xref:System.Windows.Controls.DockPanel> 을 사용하면 자식 <xref:System.Windows.Controls.TextBox> 컨트롤이 정렬 방법을 알려줄 수 있습니다. 이 작업을 수행하기 위해 <xref:System.Windows.Controls.DockPanel> 은 각각 도킹 스타일을 지정할 수 있도록 자식 컨트롤에 노출되는 <xref:System.Windows.Controls.DockPanel.Dock%2A> 속성을 구현합니다.

> [!NOTE]
> 자식 컨트롤에서 사용할 수 있도록 부모 컨트롤이 구현하는 속성은 [연결된 속성](https://msdn.microsoft.com/library/ms749011\(v=vs.100\).aspx)이라는 WPF 구문입니다.

 다음 그림에서는 이전 예제의 XAML 태그 결과를 보여 줍니다.

 ![DockPanel 페이지](../designers/media/wpfintrofigure11.png "WPFIntroFigure11")

## <a name="data-binding"></a><a name="Data_Binding"></a> 데이터 바인딩
 대부분의 애플리케이션은 데이터를 보고 편집할 수 있는 수단을 사용자에게 제공하기 위해 생성됩니다. WPF 애플리케이션의 경우 데이터를 저장 및 액세스하는 작업이 SQL Server 및 ADO .NET과 같은 기술에 의해 이미 제공됩니다. 데이터에 액세스하고 애플리케이션의 관리되는 개체에 로드한 후 WPF 애플리케이션에 대한 힘든 작업이 시작됩니다. 기본적으로 다음 두 가지가 포함됩니다.

1. 관리되는 개체에서 데이터를 표시 및 편집할 수 있는 컨트롤로 데이터 복사

2. 컨트롤을 사용한 데이터 변경 내용이 관리되는 개체에 다시 복사되는지 확인

   애플리케이션 개발을 간소화하기 위해 WPF는 이러한 단계를 자동으로 수행하는 데이터 바인딩 엔진을 제공합니다. 데이터 바인딩 엔진의 핵심 단위는 <xref:System.Windows.Data.Binding> 클래스로, 컨트롤(바인딩 대상)을 데이터 개체(바인딩 소스)에 바인딩하는 작업을 수행합니다. 이 관계는 다음 그림에 나와 있습니다.

   ![기본 데이터 바인딩 다이어그램](../designers/media/databindingmostbasic.png "DataBindingMostBasic")

   다음 예제에서는 <xref:System.Windows.Controls.TextBox>를 사용자 지정 `Person` 개체의 인스턴스에 바인딩하는 방법을 보여 줍니다. `Person` 구현은 다음 코드에 나와 있습니다.

   [!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/Person.cs#personclasscode)]
   [!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/Person.vb#personclasscode)]

   다음 태그는 <xref:System.Windows.Controls.TextBox>를 사용자 지정 `Person` 개체의 인스턴스에 바인딩합니다.

   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP1](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup1)]
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP2](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup2)]
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP3](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup3)]

   [!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml.cs#databindingcodebehind)]
   [!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/DataBindingWindow.xaml.vb#databindingcodebehind)]

   이 예제에서 `Person` 클래스는 코드 숨김에서 인스턴스화되고 `DataBindingWindow`에 대한 데이터 컨텍스트로 설정됩니다. 태그에서 <xref:System.Windows.Controls.TextBox>의 <xref:System.Windows.Controls.TextBox.Text%2A> 속성은 "`{Binding ... }`" XAML 구문을 사용하는 `Person.Name` 속성에 바인딩됩니다. 이 XAML은 WPF가 <xref:System.Windows.Controls.TextBox> 컨트롤을 해당 창의 <xref:System.Windows.FrameworkElement.DataContext%2A> 속성에 저장된 `Person` 개체에 바인딩되도록 합니다.

   WPF 데이터 바인딩 엔진은 유효성 검사, 정렬, 필터링 및 그룹화를 포함하는 추가 지원을 제공합니다. 또한 데이터 바인딩은 표준 WPF 컨트롤에 의해 표시되는 사용자 인터페이스가 적절하지 않은 경우 데이터 템플릿을 사용하여 바인딩된 데이터에 대한 사용자 지정 사용자 인터페이스를 만들 수 있도록 지원합니다.

   자세한 내용은 [데이터 바인딩 개요](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)를 참조 하세요.

## <a name="graphics"></a><a name="Graphics"></a> Graphics
 WPF는 다음과 같은 이점이 있는 광범위하고 확장 가능하며 유연한 그래픽 집합을 도입합니다.

- **해상도 및 디바이스 독립적인 그래픽**. WPF 그래픽 시스템의 기본 측정 단위는 실제 화면 해상도에 관계없이 1/96인치인 디바이스 독립적 픽셀이며, 해상도 및 디바이스 독립적인 렌더링을 위한 토대를 제공합니다. 각 디바이스 독립적 픽셀은 렌더링되는 시스템의 dpi(인치당 도트 수) 설정에 맞게 자동으로 확장됩니다.

- **향상된 정밀도**. WPF 좌표계는 단정밀도 대신 배정밀도 부동 소수점 숫자로 측정됩니다. 변환 및 불투명도 값도 배정밀도로 표현됩니다. 또한 WPF는 광범위한 색 영역(scRGB)을 지원하며 여러 색 공간의 입력을 관리하기 위한 통합 지원을 제공합니다.

- **고급 그래픽 및 애니메이션 지원**. WPF는 애니메이션 장면을 관리하여 그래픽 프로그래밍을 간소화합니다. 장면 처리, 렌더링 루프 및 쌍선형 보간에 대해 걱정할 필요가 없습니다. 또한 WPF는 적중 테스트 및 전체 알파 합치기를 지원합니다.

- **하드웨어 가속**. WPF 그래픽 시스템은 그래픽 하드웨어를 활용하여 CPU 사용량을 최소화합니다.

### <a name="2-d-shapes"></a>2차원 도형
 WPF는 다음 그림에 표시된 사각형 및 타원과 같은 일반적인 벡터 기반의 2차원 도형 라이브러리를 제공합니다.

 ![타원 및 사각형](../designers/media/wpfintrofigure4.PNG "WPFIntroFigure4")

 도형의 흥미로운 기능은 표시에 사용되는 것뿐 아니라 키보드 및 마우스 입력을 비롯하여 컨트롤에서 기대하는 기능을 대부분 구현한다는 것입니다. 다음 예제에서는 <xref:System.Windows.Shapes.Ellipse>의 <xref:System.Windows.UIElement.MouseUp> 이벤트가 처리되는 과정을 보여 줍니다.

 [!code-xml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml#handleellipsemouseupeventmarkup)]

 [!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml.cs#handleellipsemouseupeventcodebehind)]
 [!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/EllipseEventHandlingWindow.xaml.vb#handleellipsemouseupeventcodebehind)]

 다음 그림은 위의 코드에서 생성되는 내용을 보여 줍니다.

 !["타원이&#33; 클릭 했습니다." 라는 텍스트가 있는 창](../designers/media/wpfintrofigure12.png "WPFIntroFigure12")

 자세한 내용은 [WPF에서 Shape 및 기본 그리기 개요](https://msdn.microsoft.com/library/ms747393\(v=vs.100\).aspx)를 참조하세요.

### <a name="2-d-geometries"></a>2차원 기하 도형
 WPF에서 제공하는 2차원 도형은 기본 도형의 표준 집합을 다룹니다. 그러나 사용자 지정 사용자 인터페이스의 디자인이 용이하도록 사용자 지정 도형을 만들어야 할 수도 있습니다. 이 용도로 WPF는 기하 도형을 제공합니다. 다음 그림은 기하 도형을 사용하여 직접 그리거나, 브러시로 사용하거나, 다른 도형 및 컨트롤을 자르는 데 사용할 수 있는 사용자 지정 도형을 만드는 과정을 보여 줍니다.

 <xref:System.Windows.Shapes.Path> 개체는 닫혔거나 열린 도형, 여러 도형 및 곡선 도형을 그리는 데 사용할 수 있습니다.

 <xref:System.Windows.Media.Geometry> 개체는 자르기, 적중 테스트 및 2차원 그래픽 데이터 렌더링에 사용할 수 있습니다.

 ![경로를 사용 하는 다양 한 용도](../designers/media/wpfintrofigure5.PNG "WPFIntroFigure5")

 자세한 내용은 [Geometry 개요](https://msdn.microsoft.com/library/ms751808\(v=vs.100\).aspx) 를 참조 하세요.

### <a name="2-d-effects"></a>2차원 효과
 WPF 2차원 기능의 하위 집합에는 그라데이션, 비트맵, 그리기, 비디오로 그리기, 회전, 크기 조정 및 기울이기와 같은 시각 효과가 포함됩니다. 브러시를 통해 이러한 모든 효과를 얻을 수 있습니다. 다음 그림에서는 몇 가지 예를 보여 줍니다.

 ![여러 브러시의 설명](../designers/media/wpfintrofigure6.PNG "WPFIntroFigure6")

 자세한 내용은 [WPF 브러시 개요](https://msdn.microsoft.com/library/aa970904\(v=vs.100\).aspx)를 참조 하세요.

### <a name="3-d-rendering"></a>3차원 렌더링
 WPF에는 더 흥미로운 사용자 인터페이스를 만들 수 있도록 2차원 그래픽을 통합하는 3차원 렌더링 기능도 포함되어 있습니다. 예를 들어 다음 그림에서는 3차원 도형에 렌더링된 2차원 이미지를 보여 줍니다.

 ![Visual3D 샘플 스크린 샷](../designers/media/wpfintrofigure13.png "WPFIntroFigure13")

 자세한 내용은 [3 차원 그래픽 개요](https://msdn.microsoft.com/library/ms747437\(v=vs.100\).aspx)를 참조 하세요.

## <a name="animation"></a><a name="Animation"></a> 에니메이션
 WPF 애니메이션 지원을 사용하면 컨트롤이 커지거나, 흔들리거나, 회전하거나, 사라지도록 하여 흥미로운 페이지 전환 등을 만들 수 있습니다. 사용자 지정 클래스를 비롯한 대부분의 WPF 클래스에 애니메이션 효과를 줄 수 있습니다. 다음 그림에서는 간단한 애니메이션의 작동을 보여 줍니다.

 ![애니메이션 효과가 적용된 큐브의 이미지](../designers/media/wpfintrofigure7.png "WPFIntroFigure7")

 자세한 내용은 [애니메이션 개요](https://msdn.microsoft.com/library/ms752312\(v=vs.100\).aspx)를 참조 하세요.

## <a name="media"></a><a name="Media"></a> 미디어만
 풍부한 콘텐츠를 전달하는 한 가지 방법은 시청각 미디어를 사용하는 것입니다. WPF는 이미지, 비디오 및 오디오에 대한 특별한 지원을 제공합니다.

### <a name="images"></a>이미지
 이미지는 대부분의 애플리케이션에서 공통적으로 사용되며 WPF는 이미지를 사용하는 여러 방법을 제공합니다. 다음 그림에서는 미리 보기 이미지를 포함하는 목록 상자가 있는 사용자 인터페이스를 보여 줍니다. 미리 보기를 선택하면 이미지가 전체 크기로 표시됩니다.

 ![축소판 이미지 및 전체&#45;크기 이미지](../designers/media/wpfintrofigure8.PNG "WPFIntroFigure8")

 자세한 내용은 [이미징 개요](https://msdn.microsoft.com/library/ms748873\(v=vs.100\).aspx)를 참조 하세요.

### <a name="video-and-audio"></a>비디오 및 오디오
 <xref:System.Windows.Controls.MediaElement> 컨트롤은 비디오와 오디오를 둘 다 재생할 수 있으며 사용자 지정 미디어 플레이어의 토대가 될 수 있을 정도로 유연합니다. 다음 XAML 태그는 미디어 플레이어를 구현합니다.

 [!code-xml[IntroToWPFSnippets#MediaElementMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/MediaElementWindow.xaml#mediaelementmarkup)]

 다음 그림의 창에서는 <xref:System.Windows.Controls.MediaElement> 컨트롤의 작동을 보여 줍니다.

 ![오디오와 비디오가 있는 MediaElement 컨트롤](../designers/media/wpfintrofigure1.png "WPFIntroFigure1")

 자세한 내용은 [WPF 그래픽, 애니메이션 및 미디어 개요](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)를 참조하세요.

## <a name="text-and-typography"></a><a name="Text_and_Typography"></a> 텍스트 및 입력 체계
 고품질 텍스트 렌더링이 용이하도록 WPF는 다음 기능을 제공합니다.

- OpenType 글꼴 지원

- ClearType 향상

- 하드웨어 가속을 활용하는 고성능

- 미디어, 그래픽 및 애니메이션과 텍스트 통합

- 국가별 글꼴 지원 및 대체(fallback) 메커니즘

  텍스트와 그래픽 통합의 데모로, 다음 그림에서는 텍스트 장식의 응용을 보여 줍니다.

  ![다양한 텍스트 장식이 적용된 텍스트](../designers/media/wpfintrofigure23.png "WPFIntroFigure23")

  자세한 내용은 [Windows Presentation Foundation의 입력 체계](https://msdn.microsoft.com/library/ms742190\(v=vs.100\).aspx)를 참조하세요.

## <a name="customizing-wpf-applications"></a><a name="WPF_Customization"></a> WPF 애플리케이션 사용자 지정
 지금까지 애플리케이션을 개발하기 위한 핵심 WPF 구성 요소를 살펴봤습니다. 애플리케이션 모델을 사용하여 주로 컨트롤로 구성된 애플리케이션 콘텐츠를 호스트 및 제공합니다. 사용자 인터페이스에서 컨트롤 정렬을 간소화하고 창 크기 및 디스플레이 설정이 변경되어도 정렬이 유지되도록 하기 위해 WPF 레이아웃 시스템을 사용합니다. 대부분의 애플리케이션은 사용자의 데이터 조작을 허용하므로 데이터 바인딩을 사용하여 사용자 인터페이스와 데이터 통합 작업을 줄입니다. 애플리케이션의 시각적 모양을 개선하려면 WPF에서 제공하는 광범위한 그래픽, 애니메이션 및 미디어 지원을 사용합니다.

 하지만 기본 사항이 고유하고 시각적으로 멋진 사용자 환경을 만들고 관리하는 데 충분하지 않은 경우도 많습니다. 표준 WPF 컨트롤이 원하는 애플리케이션 모양과 통합되지 않을 수 있습니다. 데이터가 가장 효율적인 방식으로 표시되지 않을 수도 있습니다. 애플리케이션의 전반적인 사용자 환경이 Windows 테마의 기본 모양과 느낌에 적합하지 않을 수 있습니다. 여러 측면에서 프레젠테이션 기술은 다른 종류의 확장성만큼 시각적 확장성을 필요로 합니다.

 이런 이유로 WPF는 컨트롤, 트리거, 컨트롤 및 데이터 템플릿, 스타일, 사용자 인터페이스 리소스, 테마 및 스킨에 대한 풍부한 콘텐츠 모델을 포함하여 고유한 사용자 환경을 만들기 위한 다양한 메커니즘을 제공합니다.

### <a name="content-model"></a>콘텐츠 모델
 대부분의 WPF 컨트롤은 주로 콘텐츠를 표시하는 데 사용됩니다. WPF에서 컨트롤의 콘텐츠를 구성할 수 있는 항목의 유형과 개수를 컨트롤의 *콘텐츠 모델*이라고 합니다. 일부 컨트롤은 단일 항목 및 유형의 콘텐츠를 포함할 수 있습니다. 예를 들어 <xref:System.Windows.Controls.TextBox> 의 콘텐츠는 <xref:System.Windows.Controls.TextBox.Text%2A> 속성에 할당되는 문자열 값입니다. 다음 예제에서는 <xref:System.Windows.Controls.TextBox>의 콘텐츠를 설정합니다.

 [!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup1)]
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup2)]
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup3)]

 다음 그림은 결과를 보여 줍니다.

 ![텍스트가 포함된 TextBox 컨트롤](../designers/media/wpfintrofigure21.png "WPFIntroFigure21")

 그러나 다른 컨트롤은 다양한 콘텐츠 형식의 여러 항목을 포함할 수 있습니다. <xref:System.Windows.Controls.ContentControl.Content%2A> 속성으로 지정된 <xref:System.Windows.Controls.Button>의 콘텐츠에는 레이아웃 컨트롤, 텍스트, 이미지 및 도형을 포함하여 다양한 항목이 포함될 수 있습니다. 다음 예제에서는 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border> 및 <xref:System.Windows.Controls.MediaElement>를 포함하는 콘텐츠가 있는 <xref:System.Windows.Controls.Button>을 보여 줍니다.

 [!code-xml[IntroToWPFSnippets#ButtonContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup1)]
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup2)]
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup3)]

 다음 그림에서는 이 단추의 콘텐츠를 보여 줍니다.

 ![여러 형식의 콘텐츠가 포함된 단추](../designers/media/wpfintrofigure22.png "WPFIntroFigure22")

 다양 한 컨트롤에서 지 원하는 콘텐츠 종류에 대 한 자세한 내용은 [WPF 콘텐츠 모델](https://msdn.microsoft.com/library/bb613548\(v=vs.100\).aspx)을 참조 하세요.

### <a name="triggers"></a>트리거
 XAML 태그의 주요 용도는 애플리케이션의 모양을 구현하는 것이지만 XAML을 사용하여 애플리케이션 동작의 일부 측면을 구현할 수도 있습니다. 한 가지 예는 트리거를 사용하여 사용자 조작에 따라 애플리케이션의 모양을 변경하는 것입니다. 자세한 내용은 [스타일 지정 및 템플릿](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx)을 참조 하세요.

### <a name="control-templates"></a>컨트롤 템플릿
 WPF 컨트롤의 기본 사용자 인터페이스는 일반적으로 다른 컨트롤 및 도형에서 구성됩니다. 예를 들어 <xref:System.Windows.Controls.Button> 은 <xref:Microsoft.Windows.Themes.ButtonChrome> 및 <xref:System.Windows.Controls.ContentPresenter> 컨트롤 둘 다로 구성됩니다. <xref:Microsoft.Windows.Themes.ButtonChrome> 은 표준 단추 모양을 제공하는 반면, <xref:System.Windows.Controls.ContentPresenter> 는 <xref:System.Windows.Controls.ContentControl.Content%2A> 속성에 지정된 대로 단추의 콘텐츠를 표시합니다.

 컨트롤의 기본 모양이 애플리케이션의 전반적인 모양에 맞지 않을 수도 있습니다. 이 경우 <xref:System.Windows.Controls.ControlTemplate> 을 사용하여 해당 콘텐츠 및 동작을 변경하지 않고 컨트롤의 사용자 인터페이스 모양을 변경할 수 있습니다.

 예를 들어 다음 예제에서는 <xref:System.Windows.Controls.ControlTemplate>을 사용하여 <xref:System.Windows.Controls.Button>의 모양을 변경하는 방법을 보여 줍니다.

 [!code-xml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml#buttoncontroltemplatewindowmarkup)]

 [!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml.cs#buttoncontroltemplatewindowcodebehind)]
 [!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/ControlTemplateButtonWindow.xaml.vb#buttoncontroltemplatewindowcodebehind)]

 이 예제에서는 기본 단추 사용자 인터페이스가 진한 파란색 테두리가 있는 <xref:System.Windows.Shapes.Ellipse>로 대체되고 <xref:System.Windows.Media.RadialGradientBrush>를 사용하여 채워집니다. <xref:System.Windows.Controls.ContentPresenter> 컨트롤은 <xref:System.Windows.Controls.Button>의 콘텐츠인 "Click Me!"를 표시합니다. <xref:System.Windows.Controls.Button> 을 클릭하면 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트가 <xref:System.Windows.Controls.Button> 컨트롤의 기본 동작의 일부로 여전히 발생합니다. 결과는 다음 그림에 나와 있습니다.

 ![타원형 단추 및 두 번째 창](../designers/media/wpfintrofigure2.png "WPFIntroFigure2")

### <a name="data-templates"></a>데이터 템플릿
 컨트롤 템플릿을 사용하면 컨트롤의 모양을 지정할 수 있는 반면 데이터 템플릿을 사용하면 컨트롤 콘텐츠의 모양을 지정할 수 있습니다. 데이터 템플릿은 바인딩된 데이터가 표시되는 방식을 개선하는 데 자주 사용됩니다. 다음 그림은 각 작업에 이름, 설명 및 우선 순위가 있는 `Task` 개체의 컬렉션에 바인딩된 <xref:System.Windows.Controls.ListBox>의 기본 모양을 보여 줍니다.

 ![기본 모양의 목록 상자](../designers/media/wpfintrofigure18.png "WPFIntroFigure18")

 기본 모양은 <xref:System.Windows.Controls.ListBox>에서 예상되는 모양입니다. 그러나 각 작업의 기본 모양은 작업 이름만 포함합니다. 작업 이름, 설명 및 우선 순위를 표시하려면 <xref:System.Windows.DataTemplate>을 사용하여 <xref:System.Windows.Controls.ListBox> 컨트롤의 바인딩된 목록 항목에 대한 기본 모양을 변경해야 합니다. 다음 XAML은 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 특성을 사용하여 각 작업에 적용되는 이러한 <xref:System.Windows.DataTemplate>을 정의합니다.

 [!code-xml[IntroToWPFSnippets#DataTemplateMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup1)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup2)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup3)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup4)]

 다음 그림에서는 이 코드의 영향을 보여 줍니다.

 ![데이터 템플릿을 사용하는 목록 상자](../designers/media/wpfintrofigure19.png "WPFIntroFigure19")

 <xref:System.Windows.Controls.ListBox> 의 동작과 전반적인 모양은 유지되고 목록 상자에 표시되는 콘텐츠의 모양만 변경되었습니다.

 자세한 내용은 [데이터 템플릿 개요](https://msdn.microsoft.com/library/ms742521\(v=vs.100\).aspx)를 참조 하세요.

### <a name="styles"></a>스타일
 스타일을 사용하면 개발자와 디자이너가 해당 제품에 대해 특정 모양을 표준화할 수 있습니다. WPF는 <xref:System.Windows.Style> 요소를 기반으로 하는 강력한 스타일 모델을 제공합니다. 다음 예제에서는 창에 있는 모든 <xref:System.Windows.Controls.Button>의 배경색을 `Orange`로 설정하는 스타일을 만듭니다.

 [!code-xml[IntroToWPFSnippets#StyleMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup1)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup2)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup3)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup4)]

 이 스타일은 모든 <xref:System.Windows.Controls.Button> 컨트롤을 대상으로 하기 때문에 다음 그림과 같이 창에 있는 모든 단추에 스타일이 자동으로 적용됩니다.

 ![두 개의 주황색 단추](../designers/media/wpfintrofigure20.png "WPFIntroFigure20")

 자세한 내용은 [스타일 지정 및 템플릿](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx)을 참조 하세요.

### <a name="resources"></a>리소스
 애플리케이션의 컨트롤은 글꼴 및 배경색부터 컨트롤 템플릿, 데이터 템플릿 및 스타일까지 모든 항목을 포함할 수 있는 동일한 모양을 공유해야 합니다. 사용자 인터페이스 리소스에 대한 WPF 지원을 사용하여 재사용을 위해 이러한 리소스를 단일 위치에 캡슐화할 수 있습니다.

 다음 예제에서는 <xref:System.Windows.Controls.Button> 및 <xref:System.Windows.Controls.Label>에서 공유하는 공통 배경색을 정의합니다.

 [!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup1)]
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup2)]
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup3)]

 이 예제에서는 `Window.Resources` 속성 요소를 사용하여 배경색 리소스를 구현합니다. 이 리소스는 <xref:System.Windows.Window>의 모든 자식에서 사용할 수 있습니다. 다음을 포함하여 다양한 리소스 범위가 있습니다(확인되는 순서대로 나열됨).

1. 개별 컨트롤(상속된 <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> 속성 사용)

2. <xref:System.Windows.Window> 또는 <xref:System.Windows.Controls.Page> (또한 상속된 <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> 속성 사용)

3. <xref:System.Windows.Application> ( <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> 속성 사용)

   다양한 범위는 리소스를 정의 및 공유하는 방법과 관련해서 유연성을 제공합니다.

   리소스를 특정 범위에 직접 연결하는 대신, 애플리케이션의 다른 부분에서 참조할 수 있는 별도 <xref:System.Windows.ResourceDictionary> 를 사용하여 하나 이상의 리소스를 패키지할 수 있습니다. 예를 들어 다음 예제에서는 리소스 사전의 기본 배경색을 정의합니다.

   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup1)]
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup2)]

   다음 예제에서는 애플리케이션 간에 공유되도록 이전 예제에서 정의된 리소스 사전을 참조합니다.

   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup1)]
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup2)]

   리소스 및 리소스 사전은 테마 및 스킨에 대한 WPF 지원의 기반이 됩니다.

   자세한 내용은 [리소스 개요](https://msdn.microsoft.com/library/ms750613\(v=vs.100\).aspx)를 참조하세요.

### <a name="custom-controls"></a>사용자 지정 컨트롤
 WPF는 다양한 사용자 지정 지원을 제공하지만 기존 WPF 컨트롤이 애플리케이션 또는 해당 사용자의 요구를 충족하지 않는 경우가 발생할 수 있습니다. 이 오류는 다음과 같은 경우에 발생할 수 있습니다.

- 사용자가 요구하는 사용자 인터페이스가 기존 WPF 가 구현하는 모양이나 느낌으로 만들 수 없는 경우

- 필요한 동작이 기존 WPF 구현에서 지원되지 않는 경우(또는 쉽게 지원되지 않는 경우)

  그러나 이제 세 가지 WPF 모델 중 하나를 활용하여 새 컨트롤을 만들 수 있습니다. 각 모델은 특정 시나리오를 대상으로 하며, 특정 WPF 기본 클래스에서 사용자 지정 컨트롤을 파생시켜야 합니다. 세 가지 모델은 다음과 같습니다.

- **사용자 정의 컨트롤 모델**. 사용자 지정 컨트롤은 <xref:System.Windows.Controls.UserControl> 에서 파생되며 하나 이상의 다른 컨트롤로 구성됩니다.

- **컨트롤 모델**. 사용자 지정 컨트롤은 <xref:System.Windows.Controls.Control> 에서 파생되며 대부분의 WPF 컨트롤과 마찬가지로 템플릿을 사용하여 모양과 동작을 구분하는 구현을 작성하는 데 사용됩니다. <xref:System.Windows.Controls.Control> 에서 파생시키는 경우 사용자 정의 컨트롤보다 더 자유롭게 사용자 지정 사용자 인터페이스를 만들 수 있지만 더 많은 노력이 필요할 수 있습니다.

- **프레임워크 요소 모델**. 사용자 지정 컨트롤은 모양이 사용자 지정 렌더링 논리(템플릿 아님)에 의해 정의되는 경우 <xref:System.Windows.FrameworkElement> 에서 파생됩니다.

  다음 예제에서는 <xref:System.Windows.Controls.UserControl>에서 파생되는 사용자 지정 숫자 위로/아래로 컨트롤을 보여 줍니다.

  [!code-xml[IntroToWPFSnippets#UserControlMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml#usercontrolmarkup)]

  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind1)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind1)]
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind2)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind2)]

 다음 예제에서는 사용자 정의 컨트롤을 <xref:System.Windows.Window>에 통합하는 데 필요한 XAML을 보여 줍니다.

 [!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup1)]
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup2)]
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup3)]

 다음 그림에서는 <xref:System.Windows.Window>에 호스트된 `NumericUpDown` 컨트롤을 보여 줍니다.

 ![사용자 지정 UserControl](../designers/media/wpfintrofigure3.png "WPFIntroFigure3")

 사용자 지정 컨트롤에 대 한 자세한 내용은 [컨트롤 제작 개요](https://msdn.microsoft.com/library/ms745025\(v=vs.100\).aspx)를 참조 하세요.

## <a name="wpf-best-practices"></a><a name="WPF_Best_Practices"></a> WPF 모범 사례
 모든 개발 플랫폼과 마찬가지로 WPF를 다양한 방법으로 사용하여 원하는 결과를 얻을 수 있습니다. WPF 애플리케이션이 필요한 사용자 환경을 제공하고 일반적인 사용자 요구를 충족하도록 하는 한 가지 방법으로 접근성, 전역화 및 지역화, 성능에 대한 권장 모범 사례가 있습니다. 자세한 내용은 다음을 참조하세요.

- [접근성 모범 사례](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)접근성 모범 사례

- [WPF 전역화 및 지역화 개요](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)

- [WPF 애플리케이션 성능 최적화](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)

- [Windows Presentation Foundation 보안](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)

## <a name="summary"></a><a name="Summary"></a> 요약
 WPF는 시각적으로 멋진 다양한 클라이언트 애플리케이션을 빌드하기 위한 포괄적인 프레젠테이션 기술입니다. 이 소개에서는 WPF의 주요 기능을 살펴봤습니다.

 다음 단계는 WPF 애플리케이션을 빌드하는 것입니다.

 빌드하는 동안 이 소개로 돌아와서 주요 기능을 복습하고 이 소개에 포함된 기능의 자세한 설명에 대한 참조를 찾을 수 있습니다.

## <a name="see-also"></a>관련 항목
 [WPF 시작](../designers/getting-started-with-wpf.md) [Windows Presentation Foundation Windows Presentation Foundation를 사용 하 여 최신 데스크톱 응용 프로그램 만들기](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md) [Windows Presentation Foundation](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx)
