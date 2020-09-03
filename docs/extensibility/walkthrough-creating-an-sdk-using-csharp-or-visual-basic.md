---
title: '연습: c # 또는 Visual Basic를 사용 하 여 SDK 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 73cd76445adb798be078461e5b209e35f8b8163c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904967"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>연습: c # 또는 Visual Basic를 사용 하 여 SDK 만들기
이 연습에서는 Visual c #을 사용 하 여 간단한 수학 라이브러리 SDK를 만든 다음 SDK를 VSIX (Visual Studio Extension)로 패키징하는 방법에 대해 알아봅니다. 다음 절차를 완료 합니다.

- [SimpleMath Windows 런타임 구성 요소를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [SimpleMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [클래스 라이브러리를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> SimpleMath Windows 런타임 구성 요소를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 목록에서 **Visual c #** 또는 **Visual Basic**을 확장 하 고 **Windows 스토어** 노드를 선택한 다음 **Windows 런타임 구성 요소** 템플릿을 선택 합니다.

3. **이름** 상자에서 **SimpleMath**를 지정 하 고 **확인** 단추를 선택 합니다.

4. **솔루션 탐색기**에서 **SimpleMath** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

5. **Class1.cs** 를 **Arithmetic.cs** 로 바꾸고 다음 코드와 일치 하도록 업데이트 합니다.

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. **솔루션 탐색기**에서 **솔루션 ' SimpleMath '** 노드에 대 한 바로 가기 메뉴를 열고 **Configuration Manager**를 선택 합니다.

    **Configuration Manager** 대화 상자가 열립니다.

7. **활성 솔루션 구성** 목록에서 **릴리스**를 선택 합니다.

8. **구성** 열에서 **SimpleMath** row가 **Release**로 설정 되었는지 확인 한 다음 **닫기** 단추를 선택 하 여 변경 내용을 적용 합니다.

   > [!IMPORTANT]
   > SimpleMath 구성 요소용 SDK에는 하나의 구성만 포함 됩니다. 이 구성은 릴리스 빌드 여야 하며, 구성 요소를 사용 하는 앱은에 대 한 인증을 통과 하지 못합니다 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] .

9. **솔루션 탐색기**에서 **SimpleMath** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **빌드**를 선택 합니다.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> SimpleMathVSIX 확장 프로젝트를 만들려면

1. **솔루션 ' SimpleMath '** 노드에 대 한 바로 가기 메뉴에서 **Add**  >  **새 프로젝트**추가를 선택 합니다.

2. 템플릿 목록에서 **Visual c #** 또는 **Visual Basic**을 확장 하 고 **확장성** 노드를 선택한 다음 **VSIX 프로젝트** 템플릿을 선택 합니다.

3. **이름** 상자에서 **SimpleMathVSIX**를 지정 하 고 **확인** 단추를 선택 합니다.

4. **솔루션 탐색기**에서 **source.extension.vsixmanifest** 항목을 선택 합니다.

5. 메뉴 모음에서 코드 **보기**를 선택  >  **Code**합니다.

6. 기존 XML을 다음 XML로 바꿉니다.

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트를 선택 합니다.

8. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

9. **공통 항목**목록에서 **데이터**를 확장 한 다음 **XML 파일**을 선택 합니다.

10. **이름** 상자에서을 지정 하 `SDKManifest.xml` 고 **추가** 단추를 선택 합니다.

11. **솔루션 탐색기**에서에 대 한 바로 가기 메뉴 `SDKManifest.xml` 를 열고 **속성**을 선택한 다음 **VSIX에 포함** 속성의 값을 **True**로 변경 합니다.

12. 파일의 내용을 다음 XML로 바꿉니다.

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 폴더**를 선택 합니다.

14. 폴더의 이름을로 바꿉니다 `references` .

15. **참조** 폴더의 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 폴더**를 선택 합니다.

16. 하위 폴더의 이름을로 바꾸고 `commonconfiguration` , 그 안에 하위 폴더를 만들고, 하위 폴더의 이름을로 바꿉니다 `neutral` .

17. 이번에는 위의 네 단계를 반복 하 여 이번에는 첫 번째 폴더의 이름을로 바꿉니다 `redist` .

     이제 프로젝트에 다음과 같은 폴더 구조가 포함 됩니다.

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. **솔루션 탐색기**에서 **SimpleMath** 프로젝트에 대 한 바로 가기 메뉴를 열고 **파일 탐색기에서 폴더 열기**를 선택 합니다.

19. **파일 탐색기**에서 *bin\Release* 폴더로 이동 하 고 **SimpleMath** 파일에 대 한 바로 가기 메뉴를 연 다음 **복사**를 선택 합니다.

20. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트의 *references\commonconfiguration\neutral* 폴더에 파일을 붙여넣습니다.

21. **SimpleMath** 파일을 **SimpleMathVSIX** 프로젝트의 *redist\commonconfiguration\neutral* 폴더에 붙여넣어 이전 단계를 반복 합니다.

22. **솔루션 탐색기**에서 **SimpleMath**을 선택 합니다.

23. 메뉴 모음에서 **View**  >  **속성** 보기 (키보드: **F4** 키 선택)를 선택 합니다.

24. **속성** 창에서 **빌드 작업** 속성을 **내용**으로 변경한 다음 **VSIX에서 포함** 속성을 **True**로 변경 합니다.

25. **솔루션 탐색기**에서 **SimpleMath**에 대해이 프로세스를 반복 합니다.

26. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트를 선택 합니다.

27. 메뉴 모음 **에서 빌드**  >  **빌드 SimpleMathVSIX**를 선택 합니다.

28. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트에 대 한 바로 가기 메뉴를 열고 **파일 탐색기에서 폴더 열기**를 선택 합니다.

29. **파일 탐색기**에서 *\bin\Release* 폴더로 이동한 다음 *SimpleMathVSIX* 를 실행 하 여 설치 합니다.

30. **설치** 단추를 선택 하 고 설치가 완료 될 때까지 기다린 후 Visual Studio를 다시 시작 합니다.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> 클래스 라이브러리를 사용 하는 샘플 앱을 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 목록에서 **Visual c #** 또는 **Visual Basic**을 확장 한 다음 **Windows 스토어** 노드를 선택 합니다.

3. 비어 있는 **앱** 템플릿을 선택 하 고 프로젝트 이름을 **ArithmeticUI**로 지정한 다음 **확인** 단추를 선택 합니다.

4. **솔루션 탐색기**에서 **ArithmeticUI** 프로젝트에 대 한 바로 가기 메뉴를 열고 참조 **추가**를 선택  >  **Reference**합니다.

5. 참조 형식 목록에서 **Windows**를 확장 하 고 **확장**을 선택 합니다.

6. 세부 정보 창에서 **WinRT 수학 라이브러리** 확장을 선택 합니다.

    SDK에 대 한 추가 정보가 표시 됩니다. 이 연습의 앞부분에 나오는 SDKManifest.xml 파일에서 지정한 대로 **추가 정보** 링크를 선택 하 여 열 수 있습니다 https://msdn.microsoft.com/ .

7. **참조 관리자** 대화 상자에서 **WinRT 수학 라이브러리** 확인란을 선택 하 고 **확인** 단추를 선택 합니다.

8. 메뉴 모음에서 개체 브라우저 **보기**를 선택  >  **Object Browser**합니다.

9. **찾아보기** 목록에서 **Simple Math**를 선택 합니다.

     이제 SDK의 기능을 탐색할 수 있습니다.

10. **솔루션 탐색기**에서 **mainpage**을 열고 내용을 다음 xaml로 바꿉니다.

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. **MainPage.xaml.cs** 을 다음 코드와 일치 하도록 업데이트 합니다.

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. **F5** 키를 선택 하 여 앱을 실행 합니다.

13. 앱에서 두 숫자를 입력 하 고 작업을 선택한 다음 단추를 선택 **=** 합니다.

     올바른 결과가 나타납니다.

    확장 SDK를 성공적으로 만들고 사용 했습니다.

## <a name="see-also"></a>추가 정보
- [연습: c + +를 사용 하 여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [연습: JavaScript를 사용 하 여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
