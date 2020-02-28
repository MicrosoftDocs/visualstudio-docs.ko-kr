---
title: C#에서 WPF를 사용하는 Hello World 앱
description: WPF(Windows Presentation Foundation) UI 프레임워크를 사용하는 C#을 통해 Visual Basic으로 간단한 Windows 데스크톱 .NET 앱을 만듭니다.
ms.custom: seodec18, get-started
ms.date: 08/09/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8a29a75b21351d94c818837f07ff22785a07b5
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579983"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>자습서: C\#으로 간단한 애플리케이션 만들기

이 자습서를 완료하면 Visual Studio를 사용하여 애플리케이션을 개발할 때 사용할 수 있는 여러 도구, 대화 상자 및 디자이너에 익숙해집니다. [IDE](visual-studio-ide.md)(통합 개발 환경)의 작업에 대해 배우면서 “Hello, World” 애플리케이션을 만들고, UI를 디자인하고, 코드를 추가하고, 오류를 디버그하게 됩니다.

## <a name="prerequisites"></a>사전 요구 사항

::: moniker range="vs-2017"
아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?) 페이지로 이동하여 체험용으로 설치합니다.
::: moniker-end
::: moniker range=">=vs-2019"

- 아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/) 페이지로 이동하여 체험용으로 설치합니다.
- 이 자습서에서는 .NET Framework 또는 .NET Core를 사용할 수 있습니다. .NET Core가 더 현대적인 최신 프레임워크입니다. .NET Core의 경우 Visual Studio 2019 버전 16.3 이상이 필요합니다.
::: moniker-end

## <a name="configure-the-ide"></a>IDE 구성

::: moniker range="vs-2017"

Visual Studio를 처음 열면 로그인하라는 메시지가 표시됩니다. 이 단계는 이 자습서에 대한 옵션입니다. 다음으로 개발 설정과 색 테마를 선택하라는 대화 상자가 표시될 수 있습니다. 기본값을 유지하고 **Visual Studio 시작**을 선택합니다.

![설정 선택 대화 상자](../media/exploreide-settings.png)

Visual Studio를 시작하면 도구 창, 메뉴 및 도구 모음, 주 창 공간이 표시됩니다. **빠른 실행**, 메뉴 모음 및 상단의 표준 도구 모음이 포함된 도구 창은 애플리케이션 창 왼쪽과 오른쪽에 도킹되어 있습니다. 애플리케이션 창의 가운데에 **시작 페이지**가 있습니다. 솔루션이나 프로젝트를 로드하는 경우 편집기 및 디자이너가 **시작 페이지** 가 있는 공간에 나타납니다. 애플리케이션을 개발할 때 이 중앙 영역에서 대부분의 시간을 보냅니다.

![일반 설정이 적용된 Visual Studio 2017 IDE](../media/exploreide-idewithgeneralsettings.png "일반 설정이 적용된 Visual Studio 2017 IDE의 스크린샷")

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio를 시작하면 시작 창이 먼저 열립니다. **코드를 사용하지 않고 계속**을 선택하여 개발 환경을 엽니다. 도구 창, 메뉴 및 도구 모음, 주 창 공간이 표시됩니다. 검색 상자, 메뉴 모음 및 상단의 표준 도구 모음이 포함된 도구 창은 애플리케이션 창 왼쪽과 오른쪽에 도킹되어 있습니다. 솔루션이나 프로젝트를 로드하는 경우 편집기 및 디자이너가 애플리케이션 창의 중앙 공간에 나타납니다. 애플리케이션을 개발할 때 이 중앙 영역에서 대부분의 시간을 보냅니다.

::: moniker-end

## <a name="create-the-project"></a>프로젝트를 만듭니다.

Visual Studio에서 애플리케이션을 만들 때 먼저 프로젝트와 솔루션을 만들어야 합니다. 이 예제에서는 WPF(Windows Presentation Foundation) 프로젝트를 만듭니다.

::: moniker range="vs-2017"

1. 새 프로젝트를 만듭니다. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

     ![메뉴 모음에서 [파일], [새로 만들기], [프로젝트]를 선택합니다.](../media/exploreide-filenewproject.png "파일, 새로 만들기, 프로젝트를 선택하는 메뉴 모음의 스크린샷")

1. **새 프로젝트** 대화 상자에서 **설치** > **Visual C#**  > **Windows 데스크톱** 범주를 선택한 다음, **WPF 앱(.NET Framework)** 템플릿을 선택합니다. 프로젝트의 이름을 **HelloWPFApp**로 지정하고 **확인**을 선택합니다.

     ![Visual Studio 새 프로젝트 대화 상자의 WPF 앱 템플릿](media/exploreide-newprojectcsharp.png "새 프로젝트 대화 상자의 WPF 앱 템플릿 스크린샷")

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   ![‘새 프로젝트 만들기’ 창 보기](../../get-started/media/vs-2019/start-window-create-new-project.png "‘새 프로젝트 만들기’ 창의 스크린샷")

1. **새 프로젝트 만들기** 화면에서 “WPF”를 검색하고 **WPF 앱(.NET Core)** , **다음**을 차례로 선택합니다.

   ![‘새 프로젝트 만들기’ 대화 상자의 WPF 앱 템플릿](media/vs-2019/exploreide-newprojectcsharp-vs2019.png "‘새 프로젝트 만들기’ 대화 상자의 WPF 앱 템플릿 스크린샷")

   > [!NOTE]
   > 두 개의 WPF 바탕 화면 템플릿을 찾을 수 있습니다. 하나는 .NET Framework 용이고 다른 하나는 .NET Core 용입니다. .NET Core 템플릿은 Visual Studio 2019 버전 16.3 이상에서 사용할 수 있습니다. 이 자습서에서는 둘 중 하나를 사용할 수 있지만 새로운 개발인 경우에는 .NET Core를 사용하는 것이 좋습니다.

1. 다음 화면에서 프로젝트의 이름을 **HelloWPFApp**로 지정하고 **만들기**를 선택합니다.

   ![프로젝트 이름을 ‘HelloWPFApp’로 지정합니다.](./media/vs-2019/exploreide-nameproject.png "프로젝트 이름을 지정하는 창의 스크린샷")

::: moniker-end

HelloWPFApp 프로젝트 및 솔루션이 만들어지고 **솔루션 탐색기** 에 다양한 파일이 표시됩니다. **WPF Designer**는 분할 뷰에 디자인 뷰와 *MainWindow.xaml*의 XAML 뷰를 표시합니다. 분할자를 밀어 뷰를 더 많이 표시하거나 더 적게 표시할 수 있습니다. 시각적 뷰만 표시하거나 XAML 뷰만 표시하도록 선택할 수 있습니다.

![IDE의 WPF 프로젝트 및 솔루션](media/exploreide-wpfproject-cs.png "IDE에서 WPF 프로젝트 및 솔루션의 스크린샷")

> [!NOTE]
> XAML(eXtensible Application Markup Language)에 대한 자세한 내용은 [WPF에 대한 XAML 개요](/dotnet/framework/wpf/advanced/xaml-overview-wpf) 페이지를 참조하세요.

프로젝트를 만든 후 사용자 지정할 수 있습니다. 이렇게 하려면 **보기** 메뉴에서 **속성 창**을 선택하거나 **F4** 키를 누릅니다. 그런 다음, 프로젝트 항목, 컨트롤 및 애플리케이션의 기타 항목에 대한 옵션을 표시하고 변경할 수 있습니다.

   ![속성 창](../media/exploreide-hellowpfappfiles.png "WPF 파일 앱 이름을 표시하는 속성 창의 스크린샷")   

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow.xaml의 이름 변경

MainWindow에 보다 구체적인 이름을 지정하겠습니다. **솔루션 탐색기**에서 *MainWindow.xaml*을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다. 파일 이름을 *Greetings.xaml*로 바꿉니다.

## <a name="design-the-user-interface-ui"></a>사용자 인터페이스(UI) 디자인

디자이너가 열려 있지 않으면 *Greetings.xaml*을 선택하고 **Shift**+**F7**을 눌러 디자이너를 엽니다.

이 애플리케이션에 <xref:System.Windows.Controls.TextBlock> 컨트롤 1개, <xref:System.Windows.Controls.RadioButton> 컨트롤 2개 및 <xref:System.Windows.Controls.Button> 컨트롤 1개 등 세 가지 유형의 컨트롤을 추가합니다.

### <a name="add-a-textblock-control"></a>TextBlock 컨트롤 추가

1. **Ctrl**+**Q**를 눌러 검색 상자를 활성화하고 **도구 상자**를 입력합니다. 결과 목록에서 **보기 > 도구 상자**를 선택합니다.

1. **도구 상자**에서 **공용 WPF 컨트롤** 노드를 확장하여 TextBlock 컨트롤을 봅니다.

     ![TextBlock 컨트롤이 강조 표시된 도구 상자](../media/exploreide-textblocktoolbox.png "TextBlock 컨트롤이 강조 표시된 도구 상자 창의 스크린샷")

1. **TextBlock** 항목을 선택한 후 디자인 화면의 창으로 끌어와서 디자인 화면에 TextBlock 컨트롤을 추가합니다. 컨트롤을 창 상단의 가운데에 배치합니다. Visual Studio 2019 이상에서는 빨간색 지침을 사용하여 컨트롤을 가운데에 맞출 수 있습니다.

    해당 창은 다음 그림과 유사합니다.

    ![Greetings 양식의 TextBlock 컨트롤](../media/exploreide-greetingswithtextblockonly.png "Greetings 양식의 TextBlock 컨트롤 스크린샷")

   XAML 태그는 다음 예제와 유사합니다.

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>텍스트 블록의 텍스트 사용자 지정

1. XAML 뷰에서 **TextBlock**의 태그를 찾아 **Text** 특성을 `TextBox`에서 `Select a message option and then choose the Display button.`으로 변경합니다.

   XAML 태그는 다음 예제와 유사합니다.

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. 원할 경우 TextBlock의 가운데를 다시 맞추고 **Ctrl+S**를 누르거나 **파일** 메뉴 항목을 사용하여 변경 내용을 저장합니다.

다음에는 [RadioButton](/dotnet/framework/wpf/controls/radiobutton) 컨트롤 두 개를 폼에 추가합니다.

### <a name="add-radio-buttons"></a>라디오 단추 추가

1. **도구 상자**에서 **RadioButton** 컨트롤을 찾습니다.

     ![RadioButton 컨트롤이 선택된 도구 상자 창](../media/exploreide-radiobuttontoolbox.png "RadioButton 컨트롤이 선택된 도구 상자 창의 스크린샷")

1. **RadioButton** 항목을 선택한 후 디자인 화면의 창으로 끌어와서 디자인 화면에 두 개의 RadioButton 컨트롤을 추가합니다. 단추가 TextBlock 컨트롤 아래에 함께 표시되도록 단추를 이동합니다(선택하고 화살표 키를 사용하여). 빨간색 지침을 사용하여 컨트롤을 정렬합니다.

   창이 다음과 같이 나타납니다.

   ![TextBlock과 두 개의 라디오 단추가 있는 Greetings 양식](../media/exploreide-greetingswithradiobuttons.png "TextBlock 및 두 개의 라디오 단추가 있는 Greetings 양식 스크린샷")

1. 왼쪽 RadioButton 컨트롤의 **속성** 창에서 **속성** 창 맨 위에 있는 속성인 **Name** 속성을 `HelloButton`로 변경합니다.

    ![RadioButton 속성 창](../media/exploreide-buttonproperties.png "RadioButton 속성 창의 스크린샷")

1. 오른쪽 RadioButton 컨트롤의 **속성** 창에서 **Name** 속성을 `GoodbyeButton`으로 변경한 다음, 변경 사항을 저장합니다.

다음으로, 각 RadioButton 컨트롤에 대한 표시 텍스트를 추가합니다. 다음 절차는 RadioButton 컨트롤에 대한 **Content** 속성을 업데이트합니다.

### <a name="add-display-text-for-each-radio-button"></a>각 라디오 단추에 표시할 텍스트 추가

1. XAML에서 `HelloButton` 및 `GoodbyeButton`의 **콘텐츠** 특성을 `"Hello"` 및 `"Goodbye"`로 업데이트합니다. 이제 XAML 태그가 다음 예제와 유사하게 표시됩니다.

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>라디오 단추가 기본적으로 선택되도록 설정

이 단계에서는 두 개의 라디오 단추 중 하나가 항상 선택되도록 기본적으로 HelloButton이 선택되도록 설정합니다.

1. XAML 뷰에서 HelloButton의 태그를 찾습니다.

1. **IsChecked** 특성을 추가하고 **True**로 설정합니다. 구체적으로 `IsChecked="True"`를 추가합니다.

   이제 XAML 태그가 다음 예제와 유사하게 표시됩니다.

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

추가할 마지막 UI 요소는 [Button](/dotnet/framework/wpf/controls/button) 컨트롤입니다.

### <a name="add-the-button-control"></a>단추 컨트롤 추가

1. **도구 상자**에서 **Button** 컨트롤을 찾은 다음 디자인 뷰의 폼으로 끌어와 RadioButton 컨트롤 아래의 디자인 화면에 추가합니다. Visual Studio 2019 이상에서는 빨간색 선을 사용하여 컨트롤을 가운데에 맞출 수 있습니다.

1. XAML 뷰에서 Button 컨트롤의 **Content** 값을 `Content="Button"` 에서 `Content="Display"`로 변경한 다음 변경 내용을 저장합니다.

     해당 창은 다음 그림과 유사합니다.

     ![컨트롤 레이블이 있는 Greetings 양식](media/exploreide-greetingswithcontrollabels-cs.png "컨트롤 레이블이 있는 Greetings 양식의 스크린샷")

   이제 XAML 태그가 다음 예제와 유사하게 표시됩니다.

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>표시 단추에 코드 추가

이 애플리케이션을 실행하면 사용자가 라디오 단추를 선택한 다음 **표시** 단추를 선택하면 메시지 상자가 나타납니다. Hello에 대한 메시지 상자가 하나 나타나고 Goodbye에 대한 메시지 상자가 하나 나타납니다. 이 동작을 만들려면 *Greetings.xaml.cs*에서 `Button_Click` 이벤트에 코드를 추가합니다.

1. 디자인 화면에서 **표시** 단추를 두 번 클릭합니다.

     *Greetings.xaml.cs*는 `Button_Click` 이벤트에 커서가 있는 상태에서 열립니다.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {

    }
    ```

1. 다음 코드를 입력합니다.

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. 애플리케이션을 저장합니다.

## <a name="debug-and-test-the-application"></a>애플리케이션 디버깅 및 테스트

그런 다음 애플리케이션을 디버그하여 오류를 검색하고 두 메시지 상자가 모두 제대로 나타나는지 테스트합니다. 다음 지침에서는 디버거를 빌드하고 시작하는 방법을 설명하지만 나중에 [WPF 애플리케이션 빌드(WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) 및 [WPF 디버그](../../debugger/debugging-wpf.md)에서 추가 정보를 확인할 수 있습니다.

### <a name="find-and-fix-errors"></a>오류 찾기 및 수정

이 단계에서는 이전에 *MainWindow.xaml* 파일의 이름을 변경해서 발생시킨 오류를 찾습니다.

#### <a name="start-debugging-and-find-the-error"></a>디버깅 시작 및 오류 찾기

1. **F5** 키를 누르거나 **디버그**, **디버깅 시작**을 차례로 선택하여 디버거를 시작합니다.

   **중단 모드** 창이 나타나고 **출력** 창이 IOException이 발생했음을 나타냅니다. 'mainwindow.xaml' 리소스를 찾을 수 없습니다.

   ![IOException 메시지](../media/exploreide-ioexception.png "IOException 메시지 스크린샷")

1. **디버그** > **디버깅 중지**를 선택하여 디버거를 중지합니다.

이 자습서를 시작할 때 *MainWindow.xaml*의 이름을 *Greetings.xaml*로 바꾸었지만 코드가 여전히 애플리케이션의 시작 URI로 *MainWindow.xaml*을 나타내고 있으므로 프로젝트를 시작할 수 없습니다.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Greetings.xaml을 시작 URI로 지정

1. **솔루션 탐색기**에서 *App.xaml* 파일을 엽니다.

1. `StartupUri="MainWindow.xaml"`을 `StartupUri="Greetings.xaml"`로 변경한 다음 변경 내용을 저장합니다.

**F5** 키를 눌러 디버거를 다시 시작합니다. 애플리케이션의 **Greetings** 창이 표시됩니다.

::: moniker range="vs-2017"
![실행 중인 앱의 스크린샷](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![실행 중인 앱의 스크린샷](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

이제 애플리케이션 창을 닫아 디버깅을 중지합니다.

### <a name="debug-with-breakpoints"></a>중단점으로 디버깅

일부 중단점을 추가하여 디버깅하는 동안 코드를 테스트할 수 있습니다. **디버그** > **중단점 설정/해제**를 선택하거나 중단시킬 코드 줄 옆의 편집기 왼쪽 여백을 클릭하거나 **F9** 키를 눌러 중단점을 추가할 수 있습니다.

#### <a name="add-breakpoints"></a>중단점 추가

1. *Greetings.xaml.cs*를 열고 다음 줄을 선택합니다. `MessageBox.Show("Hello.")`

1. 메뉴에서 **디버그**를 선택한 다음 **중단점 설정/해제**를 선택하여 중단점을 추가합니다.

     편집기 창의 맨 왼쪽 여백 코드 줄 옆에 빨간색 원이 나타납니다.

1. `MessageBox.Show("Goodbye.")`줄을 선택합니다.

1. **F9** 키를 눌러 중단점을 추가한 다음 **F5** 키를 눌러 디버깅을 시작합니다.

1. **Greetings** 창에서 **Hello** 라디오 단추를 선택한 다음 **표시** 단추를 선택합니다.

    `MessageBox.Show("Hello.")` 줄이 노란색으로 강조 표시됩니다. IDE 하단에 있는 자동, 로컬 및 조사식 창은 모두 왼쪽에 도킹되고 호출 스택, 중단점, 예외 설정, 명령, 직접 실행 및 출력 창은 모두 오른쪽에 도킹됩니다.

    ![디버거의 중단점](media/exploreide-debugbreakpoint.png "디버거의 중단점 스크린샷")

1. 메뉴 모음에서 **디버그** > **프로시저 나가기**를 선택합니다.

     애플리케이션은 실행을 다시 시작하고 “Hello”라는 단어가 포함된 메시지 상자가 나타납니다.

1. 메시지 상자에서 **확인** 단추를 선택하여 닫습니다.

1. **Greetings** 창에서 **Goodbye** 라디오 단추를 선택한 다음 **표시** 단추를 선택합니다.

     `MessageBox.Show("Goodbye.")` 줄이 노란색으로 강조 표시됩니다.

1. **F5** 키를 선택하여 계속 디버깅합니다. 메시지 상자가 나타나면 메시지 상자에서 **확인** 단추를 선택하여 닫습니다.

1. 애플리케이션 창을 닫아 디버깅을 중지합니다.

1. 메뉴 모음에서 **디버그** > **모든 중단점 해제**를 선택합니다.

### <a name="view-a-representation-of-the-ui-elements"></a>UI 요소의 표현 보기

실행 중인 앱에서 창의 맨 위에 나타나는 위젯이 보여야 합니다. 이것은 몇 가지 유용한 디버깅 기능에 빠르게 액세스할 수 있도록 해 주는 런타임 도우미입니다. 첫 번째 단추를 클릭하고 **라이브 시각적 트리로 이동**합니다. 페이지의 모든 시각적 요소가 포함된 트리가 있는 창이 표시됩니다. 노드를 확장하여 추가한 단추를 찾습니다.

![라이브 시각적 트리 창의 스크린샷](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>애플리케이션 릴리스 버전 빌드

모든 것이 작동하는 것을 확인했으므로 애플리케이션의 릴리스 빌드를 준비할 수 있습니다.

1. 기본 메뉴에서 **빌드** > **솔루션 정리**를 선택하여 이전 빌드 과정에서 만들어진 중간 파일과 출력 파일을 삭제합니다. 꼭 필요한 작업은 아니지만 이 과정을 통해 디버그 빌드 출력이 정리됩니다.

1. 도구 모음에서 드롭다운 컨트롤(현재 “디버그”로 표시)을 사용하여 HelloWPFApp의 빌드 구성을 **디버그**에서 **릴리스**로 변경합니다.

1. **빌드** > **솔루션 빌드**를 선택하여 솔루션을 빌드합니다.

축하합니다. 이 자습서를 마쳤습니다. 솔루션 및 프로젝트 디렉터리( *...\HelloWPFApp\HelloWPFApp\bin\Release*)에서 빌드한 *.exe*를 찾을 수 있습니다.

## <a name="next-steps"></a>다음 단계

축하합니다. 이 자습서를 마쳤습니다. 자세히 알아보려면 다음 자습서를 계속 진행하세요.

> [!div class="nextstepaction"]
> [추가 WPF 자습서 계속 진행](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>참조

- [생산성 팁](../../ide/productivity-features.md)
