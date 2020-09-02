---
title: 시작 페이지에 사용자 정의 컨트롤 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8000c6cc067f61a64c71b8c8ac4f5c0176504cd4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903392"
---
# <a name="add-user-control-to-the-start-page"></a>시작 페이지에 사용자 정의 컨트롤 추가

이 연습에서는 사용자 지정 시작 페이지에 DLL 참조를 추가 하는 방법을 보여 줍니다. 이 예제에서는 솔루션에 사용자 정의 컨트롤을 추가 하 고, 사용자 정의 컨트롤을 빌드한 다음, 시작 페이지 *.xaml* 파일에서 빌드된 어셈블리를 참조 합니다. 새 탭은 기본 웹 브라우저 역할을 하는 사용자 정의 컨트롤을 호스팅합니다.

동일한 프로세스를 사용 하 여 *.xaml* 파일에서 호출할 수 있는 어셈블리를 추가할 수 있습니다.

## <a name="add-a-wpf-user-control-to-the-solution"></a>솔루션에 WPF 사용자 정의 컨트롤 추가

먼저 시작 페이지 솔루션에 Windows Presentation Foundation (WPF) 사용자 정의 컨트롤을 추가 합니다.

1. [사용자 지정 시작 페이지 만들기](../extensibility/creating-a-custom-start-page.md)에서 만든을 사용 하 여 시작 페이지를 만듭니다.

2. **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭 하 고 **추가**를 클릭 한 다음 **새 프로젝트**를 클릭 합니다.

3. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual Basic** 또는 **Visual c #** 노드를 확장 하 고 **Windows**를 클릭 합니다. 가운데 창에서 **WPF 사용자 정의 컨트롤 라이브러리**를 선택 합니다.

4. 컨트롤의 이름을 `WebUserControl` 지정한 다음 **확인을**클릭 합니다.

## <a name="implement-the-user-control"></a>사용자 정의 컨트롤 구현

WPF 사용자 정의 컨트롤을 구현 하려면 XAML에서 UI (사용자 인터페이스)를 빌드한 다음 c # 또는 다른 .NET 언어로 코드 숨겨진 이벤트를 작성 합니다.

### <a name="to-write-the-xaml-for-the-user-control"></a>사용자 정의 컨트롤에 대 한 XAML을 작성 하려면

1. 사용자 정의 컨트롤에 대 한 XAML 파일을 엽니다. 요소에서 `<Grid>` 다음 행 정의를 컨트롤에 추가 합니다.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Main 요소에 `<Grid>` `<Grid>` 웹 주소를 입력 하기 위한 텍스트 상자와 새 주소를 설정 하는 단추를 포함 하는 다음과 같은 새 요소를 추가 합니다.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. `<Grid>` `<Grid>` 단추 및 텍스트 상자를 포함 하는 요소 바로 뒤에 있는 최상위 요소에 다음 프레임을 추가 합니다.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. 다음 예제에서는 사용자 정의 컨트롤에 대 한 완료 된 XAML을 보여 줍니다.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>사용자 정의 컨트롤에 대 한 코드 숨겨진 이벤트를 작성 하려면

1. XAML 디자이너에서 컨트롤에 추가한 **주소 설정** 단추를 두 번 클릭 합니다.

    *UserControl1.cs* 파일이 코드 편집기에서 열립니다.

2. 다음과 같이 SetButton_Click 이벤트 처리기를 채웁니다.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    이 코드는 텍스트 상자에 입력 한 웹 주소를 웹 브라우저의 대상으로 설정 합니다. 주소가 유효 하지 않으면 코드에서 오류를 throw 합니다.

3. 또한 WebFrame_Navigated 이벤트를 처리 해야 합니다.

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. 솔루션을 빌드합니다.

## <a name="add-the-user-control-to-the-start-page"></a>시작 페이지에 사용자 정의 컨트롤 추가

시작 페이지 프로젝트에서이 컨트롤을 사용할 수 있도록 하려면 시작 페이지 프로젝트 파일에서 새 컨트롤 라이브러리에 대 한 참조를 추가 합니다. 그런 다음 시작 페이지 XAML 태그에 컨트롤을 추가할 수 있습니다.

1. **솔루션 탐색기**의 시작 페이지 프로젝트에서 **참조** 를 마우스 오른쪽 단추로 클릭 한 다음 **참조 추가**를 클릭 합니다.

2. **프로젝트** 탭에서 **Webusercontrol** 을 선택 하 고 **확인**을 클릭 합니다.

3. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

    솔루션을 빌드하면 솔루션의 다른 파일에 대해 IntelliSense에서 사용자 컨트롤을 사용할 수 있습니다.

    시작 페이지 XAML 태그에 컨트롤을 추가 하려면 어셈블리에 네임 스페이스 참조를 추가한 다음 페이지에 컨트롤을 배치 합니다.

### <a name="to-add-the-control-to-the-markup"></a>태그에 컨트롤을 추가 하려면

1. **솔루션 탐색기**에서 시작 페이지 *.xaml* 파일을 엽니다.

2. **XAML** 창에서 최상위 요소에 다음 네임 스페이스 선언을 추가 합니다 <xref:System.Windows.Controls.Grid> .

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. **XAML** 창에서 섹션으로 스크롤합니다 \<Grid> .

    섹션에는 <xref:System.Windows.Controls.TabControl> 요소에 요소가 포함 되어 있습니다 <xref:System.Windows.Controls.Grid> .

4. \<TabControl> \<TabItem> 사용자 정의 컨트롤에 대 한 참조를 포함 하는을 포함 하는 요소를 추가 합니다.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    이제 컨트롤을 테스트할 수 있습니다.

## <a name="test-a-manually-created-custom-start-page"></a>수동으로 만든 사용자 지정 시작 페이지 테스트

1. XAML 파일, 지원 되는 텍스트 파일 또는 태그 파일을 *%USERPROFILE%\My Documents\Visual Studio 2015 \Startpages \\ * 폴더에 복사 합니다.

2. 시작 페이지에서 Visual Studio에서 설치 되지 않은 어셈블리의 컨트롤이 나 형식을 참조 하는 경우 어셈블리를 복사한 다음 _Visual studio 설치 폴더_**\Common7\IDE\PrivateAssemblies \\ **에 붙여넣습니다.

3. Visual Studio 명령 프롬프트에서 **devenv/rootsuffix Exp** 를 입력 하 여 visual studio의 실험적 인스턴스를 엽니다.

4. 실험적 인스턴스에서 **도구**  >  **옵션**  >  **환경**  >  **시작** 페이지로 이동 하 고 **사용자 지정 시작 페이지** 드롭다운에서 XAML 파일을 선택 합니다.

5. **보기** 메뉴에서 **시작 페이지**를 클릭합니다.

    사용자 지정 시작 페이지가 표시 됩니다. 모든 파일을 변경 하려면 실험적 인스턴스를 닫고 변경 내용을 적용 하 고 변경 된 파일을 복사 하 여 붙여넣은 다음 실험적 인스턴스를 다시 열어 변경 내용을 확인 해야 합니다.

## <a name="see-also"></a>추가 정보

- [WPF 컨테이너 컨트롤](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [연습: 시작 페이지에 사용자 지정 XAML 추가](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
