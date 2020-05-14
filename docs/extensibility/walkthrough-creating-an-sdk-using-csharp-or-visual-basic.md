---
title: '연습: C# 또는 시각적 기본을 사용하여 SDK 만들기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697553"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>연습: C# 또는 시각적 기본을 사용하여 SDK 만들기
이 연습에서는 Visual C#을 사용하여 간단한 수학 라이브러리 SDK를 만든 다음 SDK를 시각적 스튜디오 확장(VSIX)으로 패키징하는 방법을 배웁니다. 다음 절차를 완료합니다.

- [SimpleMath 윈도우 런타임 구성 요소를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [SimpleMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [클래스 라이브러리를 사용하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>SimpleMath 윈도우 런타임 구성 요소를 만들려면

1. 메뉴 모음에서**새** > **프로젝트** **파일** > 을 선택합니다.

2. 템플릿 목록에서 **Visual C#** 또는 **Visual Basic을**확장하고 **Windows 스토어** 노드를 선택한 다음 **Windows 런타임 구성 요소** 템플릿을 선택합니다.

3. **이름** 상자에서 **SimpleMath를**지정한 다음 **확인** 단추를 선택합니다.

4. **솔루션 탐색기에서** **SimpleMath** 프로젝트 노드의 바로 가기 메뉴를 연 다음 **속성을**선택합니다.

5. **Class1.cs** 이름을 Arithmetic.cs **다음** 코드와 일치하도록 업데이트합니다.

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. **솔루션 탐색기에서** **솔루션 'SimpleMath'** 노드의 바로 가기 메뉴를 열고 **구성 관리자를**선택합니다.

    **구성 관리자** 대화 상자가 열립니다.

7. 활성 **솔루션 구성** 목록에서 **릴리스를**선택합니다.

8. **구성** 열에서 **SimpleMath** 행이 **Release로**설정되어 있는지 확인한 다음 **닫기** 단추를 선택하여 변경을 수락합니다.

   > [!IMPORTANT]
   > SimpleMath 구성 요소의 SDK에는 하나의 구성만 포함됩니다. 이 구성은 릴리스 빌드이거나 구성 요소를 사용하는 앱이 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]에 대한 인증을 통과하지 못할 수 있어야 합니다.

9. **솔루션 탐색기에서** **SimpleMath** 프로젝트 노드의 바로 가기 메뉴를 연 다음 **빌드를**선택합니다.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>SimpleMathVSIX 확장 프로젝트를 만들려면

1. **솔루션 'SimpleMath'** 노드의 바로 가기 메뉴에서**새 프로젝트** **추가를** > 선택합니다.

2. 템플릿 목록에서 **Visual C#** 또는 **Visual Basic을**확장하고 **확장성** 노드를 선택한 다음 **VSIX 프로젝트** 템플릿을 선택합니다.

3. **이름** 상자에서 **SimpleMathVSIX를**지정한 다음 **확인** 단추를 선택합니다.

4. **솔루션 탐색기에서** **source.extension.vsixmanifest** 항목을 선택합니다.

5. 메뉴 모음에서**코드** **보기를** > 선택합니다.

6. 기존 XML을 다음 XML로 바꿉꿉입니다.

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. **솔루션 탐색기에서** **SimpleMathVSIX** 프로젝트를 선택합니다.

8. 메뉴 모음에서**새 항목 추가** **프로젝트를** > 선택합니다.

9. **공통 항목**목록에서 **데이터를**확장한 다음 **XML 파일을**선택합니다.

10. **이름** 상자에서 을 `SDKManifest.xml`지정한 다음 **추가** 단추를 선택합니다.

11. **솔루션 탐색기에서**다음에 대한 `SDKManifest.xml`바로 가기 메뉴를 열고 **속성**에 대한 값을 선택한 다음 **VSIX에 Include** 속성의 값을 **True로**변경합니다.

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

13. **솔루션 탐색기에서** **SimpleMathVSIX** 프로젝트의 바로 가기 메뉴를 열고 **추가를**선택한 다음 **새 폴더를**선택합니다.

14. 폴더 이름을 로 `references`변경합니다.

15. **참조** 폴더의 바로 가기 메뉴를 열고 **에 추가를**선택한 다음 **새 폴더를**선택합니다.

16. 하위 폴더의 이름을 `commonconfiguration`"로 이름을 `neutral`바꿉니다.

17. 이번에는 첫 번째 폴더의 이름을 로 바꾸는 `redist`이전 네 단계를 반복합니다.

     이제 프로젝트에 다음 폴더 구조가 포함되어 있습니다.

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. **솔루션 탐색기에서** **SimpleMath** 프로젝트의 바로 가기 메뉴를 연 다음 **파일 탐색기에서 폴더 열기를**선택합니다.

19. **파일 탐색기에서** *bin\Release* 폴더로 이동하여 **SimpleMath.winmd** 파일의 바로 가기 메뉴를 연 다음 **복사를**선택합니다.

20. **솔루션 탐색기에서** **SimpleMathVSIX** 프로젝트의 *참조\commonconfiguration\중립* 폴더에 파일을 붙여넣습니다.

21. SimpleMath.pri 파일을 **SimpleMathVSIX** 프로젝트의 *일반 구성\중립* 폴더에 붙여 넣기 를 반복합니다. **SimpleMath.pri**

22. **솔루션 탐색기에서** **SimpleMath.winmd를**선택합니다.

23. 메뉴 모음에서**속성** **보기(키보드:** >  **F4** 키 선택)를 선택합니다.

24. **속성** 창에서 빌드 **작업** 속성을 **콘텐츠로**변경한 다음 **VSIX에 포함** 속성을 **True로**변경합니다.

25. **솔루션 탐색기에서** **SimpleMath.pri**에 대해 이 프로세스를 반복합니다.

26. **솔루션 탐색기에서** **SimpleMathVSIX** 프로젝트를 선택합니다.

27. 메뉴 모음에서 간단한 **빌드 빌드를** > **선택합니다.**

28. **솔루션 탐색기에서** **SimpleMathVSIX** 프로젝트의 바로 가기 메뉴를 연 다음 **파일 탐색기에서 폴더 열기를**선택합니다.

29. **파일 탐색기에서** *\bin\Release* 폴더로 이동한 다음 *SimpleMathVSIX.vsix를* 실행하여 설치합니다.

30. **설치** 단추를 선택하고 설치가 완료될 때까지 기다린 다음 Visual Studio를 다시 시작합니다.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>클래스 라이브러리를 사용하는 샘플 앱을 만들려면

1. 메뉴 모음에서**새** > **프로젝트** **파일** > 을 선택합니다.

2. 템플릿 목록에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **Windows 스토어** 노드를 선택합니다.

3. 빈 **앱** 템플릿을 선택하고 프로젝트 **산술 UI의**이름을 지정한 다음 **확인** 단추를 선택합니다.

4. **솔루션 탐색기에서** **산술 UI** 프로젝트의 바로 가기 메뉴를 연 다음**참조** **추가를** > 선택합니다.

5. 참조 유형 목록에서 **Windows를**확장한 다음 **확장을 선택합니다.**

6. 세부 정보 창에서 **WinRT 수학 라이브러리** 확장을 선택합니다.

    SDK에 대한 추가 정보가 나타납니다. 이 연습의 **More Information** 앞에서 SDKManifest.xml 파일에 지정한 대로 열 https://msdn.microsoft.com/추가 정보 링크를 선택할 수 있습니다.

7. 참조 **관리자** 대화 상자에서 **WinRT 수학 라이브러리** 확인란을 선택한 다음 **확인** 단추를 선택합니다.

8. 메뉴 모음에서**개체 브라우저** **보기를** > 선택합니다.

9. **찾아보기** 목록에서 **간단한 수학을**선택합니다.

     이제 SDK의 내용을 탐색할 수 있습니다.

10. **솔루션 탐색기에서** **MainPage.xaml을**열고 내용을 다음 XAML로 바꿉습니다.

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

11. 다음 코드와 일치하도록 **MainPage.xaml.cs** 업데이트합니다.

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. 앱을 실행하려면 **F5** 키를 선택합니다.

13. 앱에서 두 숫자를 입력하고 작업을 선택한 다음 단추를 **=** 선택합니다.

     올바른 결과가 나타납니다.

    확장 SDK를 성공적으로 만들고 사용했습니다.

## <a name="see-also"></a>참조
- [연습: C++를 사용하여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [연습: 자바스크립트를 사용하여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
