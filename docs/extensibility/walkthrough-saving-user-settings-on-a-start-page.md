---
title: '연습: 시작 페이지에 사용자 설정 저장 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8dd20513defd1db8848cf6a80a29e04c127c9dd4
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903171"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>연습: 시작 페이지에 사용자 설정 저장

시작 페이지에 대 한 사용자 설정을 유지할 수 있습니다. 이 연습을 수행 하면 사용자가 단추를 클릭할 때 레지스트리에 설정을 저장 하는 컨트롤을 만든 다음 시작 페이지가 로드 될 때마다 해당 설정을 검색할 수 있습니다. 시작 페이지 프로젝트 템플릿에는 사용자 지정 가능한 사용자 컨트롤이 포함 되어 있고 기본 시작 페이지 XAML은 해당 컨트롤을 호출 하기 때문에 시작 페이지 자체를 수정할 필요가 없습니다.

이 연습에서 인스턴스화된 설정 저장소는 인터페이스의 인스턴스이고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> , 호출 될 때 다음 레지스트리 위치를 읽고 씁니다. **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName> **

Visual Studio의 실험적 인스턴스에서 실행 되는 경우 설정은 HKCU\Software\Microsoft\VisualStudio\14.0Exp에 대 한 읽기 및 쓰기를 저장 ** \\ \<CollectionName> 합니다.**

설정을 유지 하는 방법에 대 한 자세한 내용은 [사용자 설정 및 옵션 확장](../extensibility/extending-user-settings-and-options.md)을 참조 하세요.

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.
>
> **확장 관리자**를 사용 하 여 시작 페이지 프로젝트 템플릿을 다운로드할 수 있습니다.

## <a name="set-up-the-project"></a>프로젝트 설정

1. [사용자 지정 시작 페이지 만들기](creating-a-custom-start-page.md)에서 설명한 대로 시작 페이지 프로젝트를 만듭니다. 프로젝트 이름을 **Savemysettings로 설정**합니다.

2. **솔루션 탐색기**에서 StartPageControl 프로젝트에 다음 어셈블리 참조를 추가 합니다.

    - EnvDTE

    - EnvDTE80

    - VisualStudio.

    - VisualStudio입니다.

3. *Mycontrol.xaml*를 엽니다.

4. XAML 창의 최상위 <xref:System.Windows.Controls.UserControl> 요소 정의에서 네임 스페이스 선언 뒤에 다음 이벤트 선언을 추가 합니다.

    ```xml
    Loaded="OnLoaded"
    ```

5. 디자인 창에서 컨트롤의 기본 영역을 클릭 한 다음 **delete**키를 누릅니다.

     이 단계에서는 <xref:System.Windows.Controls.Border> 요소와 요소를 모두 제거 하 고 최상위 요소만 남겨 둡니다 <xref:System.Windows.Controls.Grid> .

6. **도구 상자**에서 컨트롤을 표로 끌어 옵니다 <xref:System.Windows.Controls.StackPanel> .

7. 이제 <xref:System.Windows.Controls.TextBlock> , <xref:System.Windows.Controls.TextBox> 및 단추를로 끌어 옵니다 <xref:System.Windows.Controls.StackPanel> .

8. 다음 예제와 같이에 대 한 **x:Name** 특성과에 <xref:System.Windows.Controls.TextBox> `Click` 대 한 이벤트를 추가 합니다 <xref:System.Windows.Controls.Button> .

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>사용자 정의 컨트롤 구현

1. XAML 창에서 요소의 특성을 마우스 오른쪽 단추로 클릭 한 `Click` <xref:System.Windows.Controls.Button> 다음 **이벤트 처리기로 이동**을 클릭 합니다.

     이 단계에서는 *MyControl.xaml.cs*를 열고 이벤트에 대 한 스텁 처리기를 만듭니다 `Button_Click` .

2. 다음 지시문을 `using` 파일의 맨 위에 추가 합니다.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. `SettingsStore`다음 예제와 같이 private 속성을 추가 합니다.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     이 속성은 먼저 <xref:EnvDTE80.DTE2> 사용자 컨트롤의에서 자동화 개체 모델을 포함 하는 인터페이스에 대 한 참조를 가져온 <xref:System.Windows.FrameworkElement.DataContext%2A> 다음 DTE를 사용 하 여 인터페이스의 인스턴스를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> . 그런 다음이 인스턴스를 사용 하 여 현재 사용자 설정을 반환 합니다.

4. `Button_Click`다음과 같이 이벤트를 입력 합니다.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     그러면 텍스트 상자의 내용이 레지스트리의 "Mysetting" 컬렉션에 있는 "MySetting" 필드에 기록 됩니다. 컬렉션이 존재 하지 않는 경우 만들어집니다.

5. 사용자 정의 컨트롤의 이벤트에 대해 다음 처리기를 추가 합니다 `OnLoaded` .

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     이 코드는 텍스트 상자의 텍스트를 "MySetting"의 현재 값으로 설정 합니다.

6. 사용자 정의 컨트롤을 빌드합니다.

7. **솔루션 탐색기**에서 *source.extension.vsixmanifest*을 엽니다.

8. 매니페스트 편집기에서 **제품 이름** 을 설정 하 여 **설정 시작 페이지를 저장**합니다.

     이 기능은 **옵션** 대화 상자의 **시작 페이지 사용자 지정** 목록에 표시 되는 시작 페이지의 이름을 설정 합니다.

9. 빌드 *StartPage*.

## <a name="test-the-control"></a>컨트롤 테스트

1. **F5**키를 누릅니다.

     Visual Studio의 실험적 인스턴스가 열립니다.

2. 실험적 인스턴스의 **도구** 메뉴에서 **옵션**을 클릭 합니다.

3. **환경** 노드에서 **시작**을 클릭 한 다음 **시작 페이지 사용자 지정** 목록에서 **[설치 된 확장] 내 설정 저장 시작 페이지**를 선택 합니다.

     **확인**을 클릭합니다.

4. 시작 페이지가 열려 있으면 닫은 다음 **보기** 메뉴에서 **시작 페이지**를 클릭 합니다.

5. 시작 페이지에서 **mycontrol.xaml** 탭을 클릭 합니다.

6. 텍스트 상자에 **Cat**을 입력 한 후 **내 설정 저장**을 클릭 합니다.

7. 시작 페이지를 닫은 다음 다시 엽니다.

     텍스트 상자에 "Cat" 이라는 단어가 표시 되어야 합니다.

8. "Cat" 단어를 "Dog" 라는 단어로 바꿉니다. 단추를 클릭 하지 마십시오.

9. 시작 페이지를 닫은 다음 다시 엽니다.

     Visual Studio가 닫힌 경우에도 Visual studio 자체가 닫힐 때까지 Visual Studio에서 도구 창을 메모리에 유지 하기 때문에 "Dog" 라는 단어는 텍스트 상자에 표시 되어야 합니다.

10. Visual Studio의 실험적 인스턴스를 닫습니다.

11. **F5** 키를 눌러 실험적 인스턴스를 다시 엽니다.

12. 텍스트 상자에 "Cat" 이라는 단어가 표시 되어야 합니다.

## <a name="next-steps"></a>다음 단계

다른 이벤트 처리기의 다른 값을 사용 하 여 속성을 가져오고 설정 하 여 원하는 수의 사용자 지정 설정을 저장 하 고 검색 하도록이 사용자 정의 컨트롤을 수정할 수 있습니다 `SettingsStore` . `propertyName`에 대 한 각 호출에 다른 매개 변수를 사용 하는 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , 값은 레지스트리의 다른 매개 변수를 덮어쓰지 않습니다.

## <a name="see-also"></a>참조

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [시작 페이지에 Visual Studio 명령 추가](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
