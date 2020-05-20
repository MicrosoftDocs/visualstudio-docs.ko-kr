---
title: 코딩된 UI 테스트 만들기
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f1e22a39035e5d3500f4dd45481319e1daecfa04
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592063"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>연습: 코딩된 UI 테스트 만들기, 편집 및 유지 관리

이 연습에서는 WPF(Windows Presentation Framework) 앱을 테스트하기 위해 코딩된 UI 테스트를 생성, 편집 및 유지 관리하는 방법에 대해 알아봅니다. 이 연습에서는 여러 타이밍 문제 및 컨트롤 리팩터링으로 인해 중단된 테스트를 해결하기 위한 솔루션을 제공합니다.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>WPF 앱 만들기

1. 새 **WPF 앱(.NET Framework)** 프로젝트를 만들고 이름을 **SimpleWPFApp**으로 지정합니다.

     **WPF Designer**가 열리고 프로젝트의 MainWindow가 표시됩니다.

2. 현재 도구 상자가 열려 있지 않으면 엽니다. **보기** 메뉴를 선택한 다음, **도구 상자**를 선택합니다.

3. **모든 WPF 컨트롤** 섹션에서 **Button**, **CheckBox** 및 **ProgressBar** 컨트롤을 디자인 화면의 MainWindow로 끌어옵니다.

4. **Button** 컨트롤을 선택합니다. **속성** 창에 **Name** 속성의 값을 \<이름 없음>에서 button1으로 변경합니다. 그런 다음 **Content** 속성 값을 Button에서 Start로 변경합니다.

5. **ProgressBar** 컨트롤을 선택합니다. **속성** 창에 **Name** 속성의 값을 \<이름 없음>에서 progressBar1로 변경합니다. 그런 다음 **Maximum** 속성 값을 **100**에서 **10000**으로 변경합니다.

6. **Checkbox** 컨트롤을 선택합니다. **속성** 창에서 **Name** 속성을 \<이름 없음>에서 checkBox1로 변경하고 **IsEnabled** 속성의 선택을 취소합니다.

     ![간단한 WPF 애플리케이션](../test/media/codedui_wpfapp.png)

7. 단추 컨트롤을 두 번 클릭하여 Click 이벤트 처리기를 추가합니다.

     *MainWindow.xmal.cs*가 새 button1_Click 메서드의 커서와 함께 코드 편집기에 표시됩니다.

8. MainWindow 클래스의 맨 위에 대리자를 추가합니다. 대리자는 진행률 표시줄에 사용됩니다. 대리자를 추가하려면 다음 코드 추가합니다.

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }
    ```

9. button1_Click 메서드에 다음 코드를 추가합니다.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        double progress = 0;

        ProgressBarDelegate updatePbDelegate =
            new ProgressBarDelegate(progressBar1.SetValue);

        do
        {
            progress ++;

            Dispatcher.Invoke(updatePbDelegate,
                System.Windows.Threading.DispatcherPriority.Background,
                new object[] { ProgressBar.ValueProperty, progress });
            progressBar1.Value = progress;
        }
        while (progressBar1.Value != progressBar1.Maximum);

        checkBox1.IsEnabled = true;
    }
    ```

10. 파일을 저장합니다.

### <a name="run-the-wpf-app"></a>WPF 앱 실행

1. **디버그** 메뉴에서 **디버깅 시작**을 선택하거나 **F5** 키를 누릅니다.

2. 확인란 컨트롤은 사용하지 않도록 설정되어 있습니다. **시작**을 선택합니다.

     몇 초 안에 진행률 표시줄이 100% 완료로 표시됩니다.

3. 이제 확인란 컨트롤을 선택할 수 있습니다.

4. SimpleWPFApp를 닫습니다.

## <a name="create-a-shortcut-to-the-wpf-app"></a>WPF 앱에 대한 바로 가기 만들기

1. 앞에서 만든 SimpleWPFApp 애플리케이션을 찾습니다.

2. SimpleWPFApp 애플리케이션에 대한 바탕 화면 바로 가기를 만듭니다. *SimpleWPFApp.exe*를 마우스 오른쪽 단추로 클릭한 다음, **복사**를 선택합니다. 바탕 화면에서 마우스 오른쪽 단추를 클릭하고 **바로 가기 붙여넣기**를 선택합니다.

    > [!TIP]
    > 애플리케이션 바로 가기를 사용하면 애플리케이션을 신속하게 시작할 수 있기 때문에 애플리케이션에 대해 코딩된 UI 테스트를 쉽게 추가하거나 수정할 수 있습니다.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>SimpleWPFApp에 대해 코딩된 UI 테스트 만들기

1. **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 차례로 선택합니다.

2. **코딩된 UI 테스트 프로젝트** 템플릿을 검색하여 선택하고 프로젝트가 생성될 때까지 단계를 계속 진행합니다.

   > [!NOTE]
   > **코딩된 UI 테스트 프로젝트** 템플릿이 표시되지 않으면, [코딩된 UI 테스트 구성 요소를 설치](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)해야 합니다.

     **CodedUITestProject1**이라는 새로 코딩된 UI 프로젝트가 솔루션에 추가되고 **코딩된 UI 테스트용 코드 생성** 대화 상자가 나타납니다.

1. **작업 기록, UI 맵 편집 또는 어설션 추가** 옵션을 선택하고 **확인**을 선택합니다.

     **UIMap – 코딩된 UI 테스트 빌더** 대화 상자가 나타나고 Visual Studio 창이 최소화됩니다.

     대화 상자의 옵션에 대한 자세한 내용은 [코딩된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md)를 참조하세요.

1. **UIMap – 코딩된 UI 테스트 빌더** 대화 상자에서 **기록 시작**을 선택합니다.

     ![녹화 시작](../test/media/cuit_builder_record.png)

     필요한 경우, 예를 들어 들어오는 메일을 처리해야 하는 경우 기록을 일시 중지할 수 있습니다.

     ![기록 일시 중지](../test/media/cuit_.png)

    > [!WARNING]
    > 데스크톱에서 수행된 모든 작업이 기록됩니다. 기록에 중요한 데이터가 포함될 수 있는 작업을 수행하는 경우에는 기록을 일시 중지합니다.

1. 바탕 화면 바로 가기를 사용하여 SimpleWPFApp을 시작합니다.

     이전처럼 확인란 컨트롤은 사용하지 않도록 설정되어 있습니다.

1. SimpleWPFApp에서 **시작**을 선택합니다.

     몇 초 안에 진행률 표시줄이 100% 완료로 표시됩니다.

1. 이제 사용하도록 설정된 확인란 컨트롤을 선택합니다.

1. SimpleWPFApp 애플리케이션을 닫습니다.

1. **UIMap – 코딩된 UI 테스트 빌더** 대화 상자에서 **코드 생성**을 선택합니다.

1. **메서드 이름** 상자에 **SimpleAppTest**를 입력하고 **추가 후 생성**을 선택합니다. 그러면 몇 초 안에 코딩된 UI 테스트가 나타나고 솔루션에 추가됩니다.

1. **UIMap – 코딩된 UI 테스트 빌더**를 닫습니다.

     *CodedUITest1.cs* 파일이 코드 편집기에 나타납니다.

1. 프로젝트를 저장합니다.

### <a name="run-the-test"></a>테스트 실행

1. **테스트** 메뉴에서 **창**을 선택한 다음, **테스트 탐색기**를 선택합니다.

2. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

3. *CodedUITest1.cs* 파일에서 **CodedUITestMethod** 메서드를 찾아 마우스 오른쪽 단추로 클릭한 다음, **테스트 실행**을 선택하거나 **테스트 탐색기**에서 테스트를 실행합니다.

   코딩된 UI 테스트가 실행되는 동안 SimpleWPFApp를 볼 수 있습니다. 이전 절차에서 수행한 단계가 실행됩니다. 그러나 테스트에서 확인란 컨트롤에 해당하는 확인란을 선택하려고 시도하면 **테스트 결과** 창에서 테스트가 실패했음을 보여 줍니다. 진행률 표시줄이 100% 완료 상태가 될 때까지 확인란 컨트롤을 사용할 수 없다는 사실을 모르고 테스트에서 해당 확인란을 선택하려고 시도했기 때문입니다. 이와 같은 문제는 코딩된 UI 테스트에 사용할 수 있는 다양한 `UITestControl.WaitForControlXXX()` 메서드를 사용하여 해결할 수 있습니다. 다음 절차에서는 `WaitForControlEnabled()` 메서드를 사용하여, 테스트 실패의 원인이 된 문제를 해결하는 방법을 보여 줍니다. 자세한 내용은 [코딩된 UI 테스트가 재생 중 특정 이벤트를 기다리도록 지정](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)을 참조하세요.

## <a name="edit-and-rerun-the-coded-ui-test"></a>코딩된 UI 테스트 편집 및 다시 실행

1. **테스트 탐색기** 창에서 실패한 테스트를 선택하고 **StackTrace** 섹션에서 **UIMap.SimpleAppTest()** 에 대한 첫 번째 링크를 선택합니다.

2. *UIMap.Designer.cs* 파일이 열리고 코드에서 오류 지점이 강조 표시되어 있습니다.

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. 이 문제를 해결하려면 `WaitForControlEnabled()` 메서드를 사용하여 이 줄을 계속하기 전에 UI 테스트에서 CheckBox 컨트롤을 기다릴 수 있도록 설정하면 됩니다.

    > [!WARNING]
    > *UIMap.Designer.cs 파일*은 수정하지 마세요. **UIMap - 코딩된 UI 테스트 빌더**를 사용하여 코드를 생성할 때마다 수정된 코드 변경 내용을 덮어씁니다. 기록된 메서드를 수정해야 하는 경우 해당 메서드를 *UIMap.cs* 파일에 복사하고 이름을 바꿉니다. *UIMap.cs* 파일을 사용하여 *UIMapDesigner.cs* 파일의 메서드와 속성을 재정의할 수 있습니다. *CodedUITest.cs* 파일에서 원래 메서드에 대한 참조를 제거하고 이름을 바꾼 메서드 이름으로 바꾸어야 합니다.

4. **솔루션 탐색기**에서 코딩된 UI 테스트 프로젝트의 *UIMap.uitest*를 찾습니다.

5. *UIMap.uitest*에 대한 바로 가기 메뉴를 열고 **열기**를 선택합니다.

     코딩된 UI 테스트가 코딩된 UI 테스트 편집기에 표시됩니다. 이제 코딩된 UI 테스트를 보고 편집할 수 있습니다.

6. **UI 작업** 창에서 *UIMap.cs* 또는 *UIMap.vb* 파일로 이동할 테스트 메서드(SimpleAppTest)를 선택합니다. 메서드를 다른 파일로 이동하면 테스트 코드를 다시 컴파일할 때 덮어쓰지 않는 사용자 지정 코드를 추가할 수 있습니다.

7. **코딩된 UI 테스트 편집기** 도구 모음에서 **코드 이동** 단추를 선택합니다.

8. Microsoft Visual Studio 대화 상자가 표시됩니다. 메서드가 *UIMap.uitest* 파일에서 *UIMap.cs* 파일로 이동하며 더 이상 코딩된 UI 테스트 편집기를 사용하여 메서드를 편집할 수 없다는 경고가 나타납니다. **예**를 선택합니다.

     테스트 메서드가 *UIMap.uitest* 파일에서 제거되고 더 이상 UI 작업 창에 표시되지 않습니다. 이동한 테스트 파일을 편집하려면 **솔루션 탐색기**에서 *UIMap.cs* 파일을 엽니다.

9. Visual Studio 도구 모음에서 **저장**을 선택합니다.

     테스트 메서드 업데이트가 *UIMap.Designer* 파일에 저장됩니다.

    > [!WARNING]
    > 메서드를 이동하면 더 이상 코딩된 UI 편집기를 사용하여 편집할 수 없습니다. 코드 편집기를 사용하여 사용자 지정 코드를 추가하고 유지 관리해야 합니다.

10. 메서드 이름을 `SimpleAppTest()`에서 `ModifiedSimpleAppTest()`로 바꿉니다.

11. 다음 using 문을 파일에 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. 이전에 식별된 잘못된 코드 줄 앞에 다음 `WaitForControlEnabled()` 메서드를 추가합니다.

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. *CodedUITest1.cs* 파일에서 **CodedUITestMethod** 메서드를 찾고 원래 SimpleAppTest() 메서드에 대한 참조를 주석으로 처리하거나 이름을 바꾼 다음, 새 ModifiedSimpleAppTest():로 바꿉니다.

    ```csharp
    [TestMethod]
            public void CodedUITestMethod1()
            {
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463
                //this.UIMap.SimpleAppTest();
                this.UIMap.ModifiedSimpleAppTest();
            }
    ```

14. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

15. **CodedUITestMethod** 메서드를 마우스 오른쪽 단추로 클릭하고 **테스트 실행**을 선택합니다.

16. 이번에는 코딩된 UI 테스트가 테스트의 모든 단계를 성공적으로 수행하며 **테스트 탐색기** 창에 **성공**으로 표시됩니다.

## <a name="refactor-a-control-in-simplewpfapp"></a>SimpleWPFApp의 컨트롤 리팩터링

1. 디자이너의 *MainWindow.xaml* 파일에서 단추 컨트롤을 선택합니다.

2. **속성** 창 상단에서 **Name** 속성 값을 **button1**에서 **buttonA**로 변경합니다.

3. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

4. **테스트 탐색기**에서 **CodedUITestMethod1**을 실행합니다.

     코딩된 UI 테스트가 원래 UIMap에서 button1으로 매핑된 Button 컨트롤을 찾을 수 없으므로 테스트가 실패합니다. 리팩터링은 코딩된 UI 테스트에 이러한 방식으로 영향을 줄 수 있습니다.

5. **테스트 탐색기**의 **StackTrace** 섹션에서 **UIMpa.ModifiedSimpleAppTest()** 옆의 첫 번째 링크를 선택합니다.

     *UIMap.cs* 파일이 열립니다. 코드에서 오류 지점이 강조 표시됩니다.

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     이 절차 앞부분의 코드 줄에서는 리팩터링되기 전의 UIMap 이름인 `UiStartButton`을 사용합니다.

     이 문제를 해결하려면 **코딩된 UI 테스트 빌더**를 사용하여 UIMap에 리팩터링된 컨트롤을 추가하면 됩니다. 다음 절차에서와 같이 코드를 사용하도록 테스트의 코드를 업데이트할 수 있습니다.

## <a name="map-refactored-control-rerun-the-test"></a>리팩터링된 컨트롤 테스트 다시 실행 매핑

1. *CodedUITest1.cs* 파일의 **CodedUITestMethod1()** 메서드에서 마우스 오른쪽 단추를 클릭하고 **코딩된 UI 테스트에 대한 코드 생성**을 선택한 다음, **코딩된 UI 테스트 빌더 사용**을 선택합니다.

     **UIMap – 코딩된 UI 테스트 빌더**가 나타납니다.

2. 앞에서 만든 바탕 화면 바로 가기를 사용하여, 앞에서 만든 SimpleWPFApp 애플리케이션을 실행합니다.

3. **UIMap – 코딩된 UI 테스트 빌더** 대화 상자에서 십자형 도구를 SimpleWPFApp의 **시작** 단추로 끌어옵니다.

     **시작** 단추는 파란색 상자로 둘러싸여 있습니다. **코딩된 UI 테스트 빌더**에서 선택된 컨트롤의 데이터를 처리하고 컨트롤 속성을 표시하는 데 몇 초가 걸립니다. **AutomationUId**의 값은 **buttonA**로 지정됩니다.

4. 컨트롤에 대한 속성에서 왼쪽 위 모퉁이의 화살표를 선택하여 UI 컨트롤 맵을 확장합니다. **UIStartButton1**이 선택되어 있습니다.

5. 도구 모음에서 **UI 컨트롤 맵에 컨트롤 추가**를 선택합니다.

     창 맨 아래에 **선택한 컨트롤이 UI 컨트롤 맵에 추가되었습니다.** 라는 상태가 표시되어 작업을 확인할 수 있습니다.

6. **UIMap – 코딩된 UI 테스트 빌더** 대화 상자에서 **코드 생성**을 선택합니다.

     새 메서드가 필요하지 않으며 UI 컨트롤 맵의 변경 내용에 대해서만 코드가 생성될 것이라는 메모와 함께 **코딩된 UI 테스트 빌더 – 코드 생성** 대화 상자가 나타납니다.

7. **생성**을 선택합니다.

8. SimpleWPFApp를 닫습니다.

9. **UIMap – 코딩된 UI 테스트 빌더**를 닫습니다.

10. **솔루션 탐색기**에서 *UIMap.Designer.cs* 파일을 엽니다.

11. *UIMap.Designer.cs* 파일에서 **UIStartButton1** 속성을 찾습니다. `SearchProperties`가 `"buttonA"`로 설정되어 있습니다.

    ```csharp
    public WpfButton UIStartButton1
            {
                get
                {
                    if ((this.mUIStartButton1 == null))
                    {
                        this.mUIStartButton1 = new WpfButton(this);
                        #region Search Criteria
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");
                        #endregion
                    }
                    return this.mUIStartButton1;
                }
            }
    ```

     이제 새로 매핑된 컨트롤을 사용하도록 코딩된 UI 테스트를 수정할 수 있습니다. 이전 프로시저에서 언급했듯이 코딩된 UI 테스트에서 메서드나 속성을 재정의하려는 경우에는 *UIMap.cs* 파일에서 재정의해야 합니다.

12. *UIMap.cs* 파일에서 생성자를 추가하고 `"buttonA":` 값을 가진 `AutomationID` 속성을 사용하도록 `UIStartButton` 속성의 `SearchProperties` 속성을 지정합니다.

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

14. **테스트 탐색기**에서 **CodedUITestMethod1**을 실행합니다.

     이번에는 코딩된 UI 테스트가 테스트의 모든 단계를 성공적으로 수행합니다. **테스트 결과** 창에서 **성공**의 상태가 표시됩니다.

## <a name="videos"></a>동영상

![비디오 링크](../data-tools/media/playvideo.gif) [코딩된 UI 테스트 시작](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>FAQ

[코딩된 UI 테스트 FAQ](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>참고 항목

- [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [코딩된 UI 테스트 편집기를 사용하여 코딩된 UI 테스트 편집](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
