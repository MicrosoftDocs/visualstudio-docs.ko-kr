---
title: 디버깅 하는 동안 XAML 속성 검사 | Microsoft Docs
ms.date: 11/12/2019
ms.topic: how-to
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 1c8ac187f5602d1c422fe5699d36deee70341b0f
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331081"
---
# <a name="inspect-xaml-properties-while-debugging"></a>디버그하는 동안 XAML 속성 검사

**라이브 시각적 트리** 및 **라이브 속성 탐색기**를 사용하여 실행 중인 XAML 코드를 실시간으로 볼 수 있습니다. 이러한 도구는 실행 중인 XAML 애플리케이션의 UI 요소에 대한 트리 뷰를 제공하고 선택한 UI 요소의 런타임 속성을 보여 줍니다.

다음 구성에서 이러한 도구를 사용할 수 있습니다.

|앱 유형|운영 체제 및 도구|
|-----------------|--------------------------------|
|Windows Presentation Foundation(4.0 이상) 애플리케이션|Windows 7 이상|
|유니버설 Windows 앱|Windows 10 이상 ( [windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk) 포함)|

## <a name="look-at-elements-in-the-live-visual-tree"></a>라이브 시각적 트리의 요소 살펴보기

목록 보기 및 단추가 있는 매우 간단한 WPF 애플리케이션을 시작하겠습니다. 단추를 클릭할 때마다 다른 항목이 목록에 추가됩니다. 짝수 번호 항목은 회색으로 표시되고 홀수 번호 항목은 노란색으로 표시됩니다.

### <a name="create-the-project"></a>프로젝트 만들기

1. 새 c # wpf 응용 프로그램을 만들고 (**파일**  >  **새로**만들기)  >  **Project**"c # wpf"를 입력 한 다음 **wpf 앱 (.net Core)** 또는 **wpf 앱 (.NET Framework)** 을 선택 합니다. **TestXAML**로 이름을 지정합니다.

1. 다음과 같이 MainWindow.xaml을 변경합니다.

   ```xaml
   <Window x:Class="TestXAML.MainWindow"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:local="clr-namespace:TestXAML"
      mc:Ignorable="d"
      Title="MainWindow" Height="350" Width="525">
      <Grid>
         <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>
         <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>
      </Grid>
   </Window>
   ```

1. MainWindow.xaml.cs 파일에 다음 명령 처리기를 추가합니다.

   ```csharp
   int count;

   private void button_Click(object sender, RoutedEventArgs e)
   {
      ListBoxItem item = new ListBoxItem();
      item.Content = "Item" + ++count;
      if (count % 2 == 0)
      {
         item.Background = Brushes.LightGray;
      }
      else
      {
         item.Background = Brushes.LightYellow;
      }
      listBox.Items.Add(item);
   }
   ```

1. 프로젝트를 빌드하고 디버깅을 시작합니다. (빌드 구성은 릴리스가 아닌 디버그여야 합니다. 빌드 구성에 대 한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조 하세요.)

   창이 표시 되 면 실행 중인 응용 프로그램 내에 앱 내 도구 모음이 표시 됩니다.

   ::: moniker range=">= vs-2019"
   ![앱의 주 창](../debugger/media/vs-2019/livevisualtree-app.png "LiveVIsualTree-앱")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![앱의 주 창](../debugger/media/livevisualtree-app.png "LiveVIsualTree-앱")
   ::: moniker-end

1. 이제 **항목 추가** 단추를 몇 번 클릭 하 여 목록에 새 항목을 추가 합니다.

### <a name="inspect-xaml-properties"></a>XAML 속성 검사

1. 그런 다음 앱 내 도구 모음의 왼쪽 단추를 클릭 하거나 **디버그 > Windows > 라이브 시각적 트리**로 이동 하 여 **라이브 시각적 트리** 창을 엽니다. 열린 후에는이 창과 **라이브 속성** 창을 나란히 볼 수 있도록 도킹 위치에서 밖으로 끕니다.

1. **라이브 시각적 트리** 창에서 **ContentPresenter** 노드를 확장합니다. 단추와 목록 상자에 대한 노드가 있어야 합니다. 목록 상자와 **ScrollContentPresenter** 및 **ItemsPresenter**를 차례로 확장하여 목록 상자 항목을 찾습니다.

   ::: moniker range=">= vs-2019"
   **ContentPresenter** 노드가 표시 되지 않으면 도구 모음에서 **내 XAML만 표시** 아이콘을 설정/해제 합니다. Visual Studio 2019 버전 16.4부터 XAML 요소 뷰는 기본적으로 내 XAML 기능만 사용 하 여 간소화 됩니다. 모든 XAML 요소를 항상 표시 하는 옵션에서 [이 설정을 사용 하지 않도록](../debugger/general-debugging-options-dialog-box.md) 설정할 수도 있습니다.
   ::: moniker-end

   창이 다음과 같이 표시되어야 합니다.

   ::: moniker range=">= vs-2019"
   ![라이브 표시 트리의 Listboxitem](../debugger/media/vs-2019/livevisualtree-listboxitems.png "LiveVisualTree-Listboxitem")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![라이브 표시 트리의 Listboxitem](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-Listboxitem")
   ::: moniker-end

1. 애플리케이션 창으로 다시 이동하고 더 많은 항목을 추가합니다. 더 많은 목록 상자 항목이 **라이브 시각적 트리**에 나타나야 합니다.

1. 이제 목록 상자 항목 중 하나의 속성을 살펴보겠습니다.

   **라이브 시각적 트리**의 첫 번째 목록 상자 항목을 선택하고 도구 모음에서 **속성 표시** 아이콘을 클릭합니다. **라이브 속성 탐색기**가 표시됩니다. **콘텐츠** 필드는 "Item1"이 고, **배경색**  >  **Color** 필드는 **#FFFFFFE0**입니다.

1. **라이브 시각적 트리**로 돌아가서 두 번째 목록 상자 항목을 선택합니다. **라이브 속성 탐색기** 는 **내용** 필드가 "Item2"이 고 **배경색**  >  **Color** 필드가 **#FFD3D3D3** (테마에 따라) 임을 표시 합니다.

   > [!NOTE]
   > **라이브 속성 탐색기** 에서 속성 주위의 노란색 테두리는 속성 값이와 같은 바인딩을 통해 설정 됨을 의미 합니다 `Color = {BindingExpression}` . 녹색 테두리는와 같은 리소스를 사용 하 여 값을 설정 하는 것을 의미 합니다 `Color = {StaticResource MyBrush}` .

   XAML의 실제 구조에는 직접적으로 관련이 없는 많은 요소가 있습니다. 코드를 잘 모르면 트리에서 필요한 항목을 찾기가 어려울 수 있습니다. 따라서 **라이브 시각적 트리**에는 검사하려는 요소를 찾는 데 도움이 되는 애플리케이션 UI를 사용할 수 있는 몇 가지 방법이 있습니다.

   ::: moniker range=">= vs-2019"
   **실행 중인 응용 프로그램에서 요소를 선택**합니다. **라이브 시각적 트리** 도구 모음의 가장 왼쪽에 있는 단추를 선택하면 이 모드를 사용할 수 있습니다. 이 모드를 켜면 애플리케이션에서 UI 요소를 선택할 수 있고 **라이브 시각적 트리**(및 **라이브 속성 뷰어**)가 이 요소 및 해당 속성에 해당하는 트리에 노드를 표시하도록 자동으로 업데이트됩니다. Visual Studio 2019 버전 16.4부터 [요소 선택의 동작을 구성할](../debugger/general-debugging-options-dialog-box.md)수 있습니다.

   **실행 중인 애플리케이션에 레이아웃 표시기를 표시합니다**. 선택 사용 단추 바로 오른쪽에 있는 단추를 선택하면 이 모드를 사용할 수 있습니다. **레이아웃 표시기 표시**를 켜면 애플리케이션 창에 선택한 개체의 범위를 따라 가로 및 세로줄이 표시됩니다. 따라서 여백을 표시하는 사각형뿐만 아니라 어떤 항목이 정렬되는지 확인할 수 있습니다. 예를 들어 **요소 선택** 및 **레이아웃 표시** 를 모두 설정 하 고 응용 프로그램에서 항목 텍스트 블록 **추가** 를 선택 합니다. **라이브 시각적 트리**에 텍스트 블록 노드가 표시되고 **라이브 속성 뷰어**에 텍스트 블록 속성이 표시되어야 합니다. 또한 텍스트 블록의 범위에는 가로 및 세로줄이 표시되어야 합니다.

   ![DisplayLayout의 LivePropertyViewer](../debugger/media/vs-2019/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **선택 미리 보기**. 라이브 시각적 트리 도구 모음의 왼쪽에서 세 번째 단추를 선택하면 이 모드를 사용할 수 있습니다. 이 모드에서는 애플리케이션의 소스 코드에 액세스할 수 있는 경우 요소가 선언된 XAML을 보여 줍니다. **요소 선택** 및 선택 **영역 미리 보기**를 선택한 다음 테스트 응용 프로그램에서 단추를 선택 합니다. Visual Studio에서 MainWindow.xaml 파일이 열리고 커서가 단추가 정의된 줄에 위치합니다.
   ::: moniker-end

   ::: moniker range="vs-2017"
   **실행 중인 애플리케이션에서 선택을 사용합니다**. **라이브 시각적 트리** 도구 모음의 가장 왼쪽에 있는 단추를 선택하면 이 모드를 사용할 수 있습니다. 이 모드를 켜면 애플리케이션에서 UI 요소를 선택할 수 있고 **라이브 시각적 트리**(및 **라이브 속성 뷰어**)가 이 요소 및 해당 속성에 해당하는 트리에 노드를 표시하도록 자동으로 업데이트됩니다.

   **실행 중인 애플리케이션에 레이아웃 표시기를 표시합니다**. 선택 사용 단추 바로 오른쪽에 있는 단추를 선택하면 이 모드를 사용할 수 있습니다. **레이아웃 표시기 표시**를 켜면 애플리케이션 창에 선택한 개체의 범위를 따라 가로 및 세로줄이 표시됩니다. 따라서 여백을 표시하는 사각형뿐만 아니라 어떤 항목이 정렬되는지 확인할 수 있습니다. 예를 들어 **선택 사용** 및 **레이아웃 표시**를 모두 켜고 애플리케이션에서 **항목 추가** 텍스트 블록을 선택합니다. **라이브 시각적 트리**에 텍스트 블록 노드가 표시되고 **라이브 속성 뷰어**에 텍스트 블록 속성이 표시되어야 합니다. 또한 텍스트 블록의 범위에는 가로 및 세로줄이 표시되어야 합니다.

   ![DisplayLayout의 LivePropertyViewer](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **선택 미리 보기**. 라이브 시각적 트리 도구 모음의 왼쪽에서 세 번째 단추를 선택하면 이 모드를 사용할 수 있습니다. 이 모드에서는 애플리케이션의 소스 코드에 액세스할 수 있는 경우 요소가 선언된 XAML을 보여 줍니다. **선택 사용** 및 **선택 미리 보기**를 선택한 다음, 테스트 애플리케이션에서 단추를 선택합니다. Visual Studio에서 MainWindow.xaml 파일이 열리고 커서가 단추가 정의된 줄에 위치합니다.
   ::: moniker-end

## <a name="use-xaml-tools-with-running-applications"></a>응용 프로그램을 실행 하는 XAML 도구 사용

소스 코드가 없는 경우 이러한 XAML 도구를 사용할 수 있습니다. 실행 중인 XAML 애플리케이션에 연결하면 해당 애플리케이션의 UI 요소에서도 **라이브 시각적 트리**를 사용할 수 있습니다. 다음은 이전에 사용한 동일한 WPF 테스트 애플리케이션을 사용하는 예제입니다.

1. 릴리스 구성에서 **TestXaml** 애플리케이션을 시작합니다. **디버그** 구성으로 실행 중인 프로세스에는 연결할 수 없습니다.

2. Visual Studio의 두 번째 인스턴스를 열고 **디버그 > 프로세스에 연결**을 클릭합니다. 사용 가능한 프로세스 목록에서 **TestXaml.exe**를 찾고 **연결**을 클릭합니다.

3. 애플리케이션이 실행되기 시작합니다.

4. Visual Studio의 두 번째 인스턴스에서 **라이브 시각적 트리**(**디버그 > 창 > 라이브 시각적 트리**)를 엽니다. **TestXaml** UI 요소가 표시되어야 하고 애플리케이션을 직접 디버그하는 동안 했던 것처럼 해당 요소를 조작할 수 있어야 합니다.

## <a name="see-also"></a>참조

[XAML 핫 다시 로드를 사용 하 여 실행 중인 XAML 코드 작성 및 디버그](xaml-hot-reload.md)
