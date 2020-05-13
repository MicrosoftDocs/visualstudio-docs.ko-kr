---
title: 시작 페이지에 사용자 컨트롤 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740133"
---
# <a name="add-user-control-to-the-start-page"></a>시작 페이지에 사용자 컨트롤 추가

이 연습에서는 사용자 지정 시작 페이지에 DLL 참조를 추가하는 방법을 보여 주며, 이 연습에서는 DLL 참조를 추가하는 방법을 보여 주며, 이 연습에서는 DLL 참조를 추가하는 방법을 보여 주며, 이 연습에서는 DLL 참조를 추가하는 방법을 보여 이 예제에서는 솔루션에 사용자 컨트롤을 추가하고 사용자 컨트롤을 빌드한 다음 시작 페이지 *.xaml* 파일에서 빌드된 어셈블리를 참조합니다. 새 탭은 기본 웹 브라우저로 작동하는 사용자 컨트롤을 호스팅합니다.

동일한 프로세스를 사용하여 *.xaml* 파일에서 호출할 수 있는 어셈블리를 추가할 수 있습니다.

## <a name="add-a-wpf-user-control-to-the-solution"></a>솔루션에 WPF 사용자 컨트롤 추가

먼저 시작 페이지 솔루션에 WPF(Windows 프레젠테이션 파운데이션) 사용자 컨트롤을 추가합니다.

1. 사용자 지정 시작 페이지 만들기에서 만든 사용하여 [시작 페이지 만들기.](../extensibility/creating-a-custom-start-page.md)

2. **솔루션 탐색기에서**솔루션을 마우스 오른쪽 단추로 클릭하고 **에서 추가를**클릭한 다음 **새 프로젝트**를 클릭합니다.

3. **새 프로젝트** 대화 상자의 왼쪽 창에서 시각적 **기본** 또는 **시각적 C#** 노드를 확장하고 **Windows**를 클릭합니다. 중간 창에서 **WPF 사용자 제어 라이브러리를**선택합니다.

4. 컨트롤의 `WebUserControl` 이름을 지정한 다음 **확인을**클릭합니다.

## <a name="implement-the-user-control"></a>사용자 컨트롤 구현

WPF 사용자 컨트롤을 구현하려면 XAML에서 사용자 인터페이스(UI)를 빌드한 다음 C# 또는 다른 .NET 언어로 코드 숨결 이벤트를 작성합니다.

### <a name="to-write-the-xaml-for-the-user-control"></a>사용자 컨트롤에 대한 XAML을 작성하려면

1. 사용자 컨트롤에 대한 XAML 파일을 엽니다. 요소에서 `<Grid>` 컨트롤에 다음 행 정의를 추가합니다.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. 기본 `<Grid>` 요소에서 웹 주소를 `<Grid>` 입력하기 위한 텍스트 상자와 새 주소를 설정하기 위한 단추를 포함하는 다음 새 요소를 추가합니다.

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

3. 단추와 텍스트 상자가 포함된 `<Grid>` `<Grid>` 요소 바로 다음에 다음 프레임을 최상위 요소에 추가합니다.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. 다음 예제에서는 사용자 컨트롤에 대해 완료된 XAML을 보여 주며, 이 예제에서는

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>사용자 컨트롤에 대한 코드 숨결 이벤트를 작성하려면

1. XAML 디자이너에서 컨트롤에 추가한 **주소 설정** 단추를 두 번 클릭합니다.

    *UserControl1.cs* 파일은 코드 편집기에서 열립니다.

2. 다음과 같이 SetButton_Click 이벤트 처리기를 입력합니다.

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

    이 코드는 텍스트 상자에 입력된 웹 주소를 웹 브라우저의 대상으로 설정합니다. 주소가 유효하지 않으면 코드에서 오류가 발생합니다.

3. 또한 WebFrame_Navigated 이벤트를 처리해야 합니다.

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. 솔루션을 빌드합니다.

## <a name="add-the-user-control-to-the-start-page"></a>시작 페이지에 사용자 컨트롤 추가

시작 페이지 프로젝트에서 이 컨트롤을 사용할 수 있도록 하려면 시작 페이지 프로젝트 파일에서 새 컨트롤 라이브러리에 대한 참조를 추가합니다. 그런 다음 시작 페이지 XAML 태그에 컨트롤을 추가할 수 있습니다.

1. **솔루션 탐색기에서**시작 페이지 프로젝트에서 **참조를** 마우스 오른쪽 단추로 클릭한 다음 **참조 추가를**클릭합니다.

2. **프로젝트** 탭에서 **WebUserControl을** 선택한 다음 **확인을**클릭합니다.

3. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

    솔루션을 빌드하면 솔루션의 다른 파일에 대해 IntelliSense에서 사용자 컨트롤을 사용할 수 있습니다.

    시작 페이지 XAML 태그에 컨트롤을 추가하려면 어셈블리에 네임스페이스 참조를 추가한 다음 컨트롤을 페이지에 배치합니다.

### <a name="to-add-the-control-to-the-markup"></a>태그를 추가하려면

1. **솔루션 탐색기에서**시작 페이지 *.xaml* 파일을 엽니다.

2. **XAML** 창에서 최상위 <xref:System.Windows.Controls.Grid> 요소에 다음 네임스페이스 선언을 추가합니다.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. **XAML** 창에서 그리드> \<섹션으로 스크롤합니다.

    섹션에는 <xref:System.Windows.Controls.TabControl> <xref:System.Windows.Controls.Grid> 요소의 요소가 포함되어 있습니다.

4. 사용자 \<컨트롤에 대한 참조가 \<포함된 TabItem> 포함하는 TabControl> 요소를 추가합니다.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    이제 컨트롤을 테스트할 수 있습니다.

## <a name="test-a-manually-created-custom-start-page"></a>수동으로 만든 사용자 지정 시작 페이지 테스트

1. XAML 파일 및 지원 텍스트 파일 또는 마크업 파일을 *%USERPROFILE%\My 문서\Visual Studio 2015\StartPages\\ * 폴더에 복사합니다.

2. 시작 페이지에서 Visual Studio에서 설치하지 않은 어셈블리의 컨트롤이나 형식을 참조하는 경우 어셈블리를 복사한 다음 _Visual Studio 설치 폴더_**\Common7\IDE\PrivateAssemblies에\\**붙여넣습니다.

3. Visual Studio 명령 프롬프트에서 **devenv /rootsuffix Exp를** 입력하여 Visual Studio의 실험 인스턴스를 엽니다.

4. 실험적인 인스턴스에서 **도구** > **옵션** > **환경** > **시작** 페이지로 이동하여 사용자 **지정 시작 페이지** 드롭다운에서 XAML 파일을 선택합니다.

5. **보기** 메뉴에서 **시작 페이지**를 클릭합니다.

    사용자 지정 시작 페이지가 표시되어야 합니다. 파일을 변경하려면 실험 인스턴스를 닫고 변경한 파일을 복사하여 붙여넣은 다음 실험 인스턴스를 다시 열어 변경 내용을 확인해야 합니다.

## <a name="see-also"></a>참조

- [WPF 컨테이너 컨트롤](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [연습: 시작 페이지에 사용자 지정 XAML 추가](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
