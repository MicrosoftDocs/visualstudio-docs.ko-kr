---
title: '연습: 시작 페이지에서 사용자 설정 저장 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697085"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>연습: 시작 페이지에 사용자 설정 저장

시작 페이지에 대한 사용자 설정을 지속할 수 있습니다. 이 연습에 따라 사용자가 단추를 클릭할 때 레지스트리에 설정을 저장하는 컨트롤을 만든 다음 시작 페이지가 로드될 때마다 해당 설정을 검색할 수 있습니다. 시작 페이지 프로젝트 템플릿에는 사용자 지정 가능한 사용자 컨트롤과 기본 시작 페이지 XAML 이 컨트롤을 호출하므로 시작 페이지 자체를 수정할 필요가 없습니다.

이 연습에서 인스턴스화되는 설정 저장소는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> 다음 레지스트리 위치에 읽고 쓰는 인터페이스의 인스턴스입니다 **>.\\\<**

Visual Studio의 실험인스턴스에서 실행되는 경우 설정 저장소는 **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<컬렉션이름>** 읽혀씁니다.

설정을 유지하는 방법에 대한 자세한 내용은 [사용자 설정 및 옵션 확장을](../extensibility/extending-user-settings-and-options.md)참조하십시오.

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.
>
> **확장 관리자를**사용하여 시작 페이지 프로젝트 템플릿을 다운로드할 수 있습니다.

## <a name="set-up-the-project"></a>프로젝트 설정

1. 사용자 지정 시작 페이지 [만들기에](creating-a-custom-start-page.md)설명된 대로 시작 페이지 프로젝트 만들기. 프로젝트 **이름 SaveMySettings**.

2. **솔루션 탐색기에서**StartPageControl 프로젝트에 다음 어셈블리 참조를 추가합니다.

    - EnvDTE

    - EnvDTE80

    - 마이크로소프트.비주얼스튜디오.올레.인터롭

    - 마이크로소프트.비주얼스튜디오.쉘.인터롭.11.0

3. *마이컨트롤.xaml*열기 .

4. XAML 창에서 최상위 <xref:System.Windows.Controls.UserControl> 요소 정의에서 네임스페이스 선언 다음에 다음 이벤트 선언을 추가합니다.

    ```xml
    Loaded="OnLoaded"
    ```

5. 디자인 창에서 컨트롤의 기본 영역을 클릭한 다음 **삭제**를 누릅니다.

     이 단계는 <xref:System.Windows.Controls.Border> 요소와 요소의 모든 요소를 제거하고 <xref:System.Windows.Controls.Grid> 최상위 요소만 남깁니다.

6. 도구 **상자에서**컨트롤을 <xref:System.Windows.Controls.StackPanel> 그리드로 드래그합니다.

7. 이제 <xref:System.Windows.Controls.TextBlock>에서 를 <xref:System.Windows.Controls.TextBox>및 단추를 <xref:System.Windows.Controls.StackPanel>로 드래그합니다.

8. 다음 예제와 같이 의 <xref:System.Windows.Controls.TextBox>및 `Click` <xref:System.Windows.Controls.Button>에 대한 이벤트에 대한 **x:Name** 특성을 추가합니다.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>사용자 컨트롤 구현

1. XAML 창에서 `Click` <xref:System.Windows.Controls.Button> 요소의 특성을 마우스 오른쪽 단추로 클릭한 다음 이벤트 **처리기로 이동을 클릭합니다.**

     이 단계는 *MyControl.xaml.cs*열고 `Button_Click` 이벤트에 대한 스텁 처리기를 만듭니다.

2. 파일 맨 `using` 위에 다음 지시문을 추가합니다.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. 다음 예제와 같이 개인 `SettingsStore` 속성을 추가합니다.

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

     이 속성은 먼저 사용자 <xref:EnvDTE80.DTE2> <xref:System.Windows.FrameworkElement.DataContext%2A> 컨트롤의 자동화 개체 모델을 포함 하는 인터페이스에 대 한 참조를 가져옵니다., <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 다음 인터페이스의 인스턴스를 가져옵니다 DTE를 사용 하 여. 그런 다음 해당 인스턴스를 사용하여 현재 사용자 설정을 반환합니다.

4. `Button_Click` 다음과 같이 이벤트를 입력합니다.

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

     이렇게 하면 텍스트 상자의 내용을 레지스트리의 "MySettings" 컬렉션의 "MySetting" 필드에 기록합니다. 컬렉션이 없으면 만들어집니다.

5. 사용자 컨트롤의 `OnLoaded` 이벤트에 대해 다음 처리기를 추가합니다.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     이 코드는 텍스트 상자의 텍스트를 "MySetting"의 현재 값으로 설정합니다.

6. 사용자 컨트롤을 빌드합니다.

7. **솔루션 탐색기에서**오픈 *소스.extension.vsixmanifest*.

8. 매니페스트 편집기에서 내 **설정 시작 페이지를 저장하도록** **제품 이름을** 설정합니다.

     이 기능은 **옵션** 대화 상자의 시작 페이지 사용자 **지정** 목록에 표시되는 시작 페이지의 이름을 설정합니다.

9. *빌드 시작 페이지.xaml*.

## <a name="test-the-control"></a>컨트롤 테스트

1. **F5**키를 누릅니다.

     Visual Studio의 실험 인스턴스가 열립니다.

2. 실험 인스턴스에서 **도구** 메뉴에서 **옵션을**클릭합니다.

3. **환경** 노드에서 **시작을**클릭한 다음 사용자 지정 **시작 페이지** 목록에서 **[설치된 확장] 내 설정 시작 페이지 저장을**선택합니다.

     **확인**을 클릭합니다.

4. 시작 페이지가 열려 있으면 닫은 다음 **보기** 메뉴에서 **시작 페이지를**클릭합니다.

5. 시작 페이지에서 **MyControl** 탭을 클릭합니다.

6. 텍스트 상자에서 **[를**입력한 다음 **내 설정 저장을**클릭합니다.

7. 시작 페이지를 닫은 다음 다시 엽니다.

     "Cat"이라는 단어는 텍스트 상자에 표시되어야 합니다.

8. "고양이"라는 단어를 "개"라는 단어로 바꿉습니다. 단추를 클릭하지 마십시오.

9. 시작 페이지를 닫은 다음 다시 엽니다.

     Visual Studio가 닫혀 있더라도 Visual Studio 자체가 닫혀도 닫혀 있더라도 설정을 저장하지 않았더라도 텍스트 상자에 "Dog"라는 단어가 표시되어야 합니다.

10. Visual Studio의 실험적 인스턴스를 닫습니다.

11. 실험 인스턴스를 다시 열려면 **F5를** 누릅니다.

12. "Cat"이라는 단어는 텍스트 상자에 표시되어야 합니다.

## <a name="next-steps"></a>다음 단계

이 사용자 컨트롤을 수정하여 다른 이벤트 처리기의 다른 값을 사용하여 `SettingsStore` 속성을 가져와서 설정하여 원하는 수의 사용자 지정 설정을 저장하고 검색할 수 있습니다. 각 호출에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>대해 `propertyName` 다른 매개 변수를 사용하는 한 값은 레지스트리에서 서로를 덮어쓰지 않습니다.

## <a name="see-also"></a>참조

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [시작 페이지에 시각적 스튜디오 명령 추가](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
