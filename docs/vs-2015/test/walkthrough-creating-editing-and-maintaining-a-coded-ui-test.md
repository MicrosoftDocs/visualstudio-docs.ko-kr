---
title: '연습: 코딩된 UI 테스트 만들기, 편집 및 유지 관리 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 900a241549cd499437ee25d8f57ed66c0c958a17
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586909"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>연습: 코딩된 UI 테스트 만들기, 편집 및 유지 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 간단한 WPF(Windows Presentation Foundation) 웹 애플리케이션을 만들어, 코딩된 UI 테스트를 만들고 편집하고 유지 관리하는 방법을 보여 줍니다. 이 연습에서는 여러 타이밍 문제 및 제어 리팩터링으로 인해 중단된 테스트를 해결하기 위한 방법을 제공합니다.

## <a name="prerequisites"></a>전제 조건
 이 연습을 수행하려면 다음이 필요합니다.

- Visual Studio Enterprise

### <a name="create-a-simple-wpf-application"></a>간단한 WPF 애플리케이션 만들기

1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 선택 합니다.

     **새 프로젝트** 대화 상자가 나타납니다.

2. **설치됨** 창에서 **Visual C#** 을 확장한 다음 **Windows 데스크톱**을 선택합니다.

3. 가운데 창 위에서 대상 프레임워크 드롭다운 목록이 **.NET Framework 4.5**로 설정되어 있는지 확인합니다.

4. 가운데 창에서 **WPF 애플리케이션** 템플릿을 선택합니다.

5. **이름** 텍스트 상자에 **SimpleWPFApp**을 입력합니다.

6. 프로젝트를 저장할 폴더를 선택합니다. **위치** 텍스트 상자에 폴더 이름을 입력합니다.

7. **확인**을 선택합니다.

     Visual Studio용 WPF Designer가 열리고 프로젝트의 MainWindow가 표시됩니다.

8. 현재 도구 상자가 열려 있지 않으면 엽니다. **보기** 메뉴를 선택한 다음 **도구 상자**를 선택 합니다.

9. **모든 WPF 컨트롤** 섹션에서 **Button**, **CheckBox** 및 **ProgressBar** 컨트롤을 디자인 화면의 MainWindow로 끌어옵니다.

10. Button 컨트롤을 선택합니다. 속성 창에 **Name** 속성의 값을 \<이름 없음>에서 button1으로 변경합니다. 그런 다음 **Content** 속성 값을 Button에서 Start로 변경합니다.

11. ProgressBar 컨트롤을 선택합니다. 속성 창에 **Name** 속성의 값을 \<이름 없음>에서 progressBar1로 변경합니다. 그런 다음 **Maximum** 속성 값을 **100**에서 **10000**으로 변경합니다.

12. Checkbox 컨트롤을 선택합니다. 속성 창에서 **Name** 속성을 \<이름 없음>에서 checkBox1로 변경하고 **IsEnabled** 속성의 선택을 취소합니다.

     ![간단한 WPF 애플리케이션](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")

13. 단추 컨트롤을 두 번 클릭하여 Click 이벤트 처리기를 추가합니다.

     MainWindow.xmal.cs가 새 button1_Click 메서드의 커서와 함께 코드 편집기에 표시됩니다.

14. MainWindow 클래스의 맨 위에 대리자를 추가합니다. 대리자는 진행률 표시줄에 사용됩니다. 대리자를 추가하려면 다음 코드 추가합니다.

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }

    ```

15. button1_Click 메서드에 다음 코드를 추가합니다.

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

16. 파일을 저장합니다.

### <a name="verify-the-wpf-application-runs-correctly"></a>WPF 애플리케이션이 제대로 실행되는지 확인

1. **디버그** 메뉴에서 **디버깅 시작** 을 선택 하거나 **f5**키를 누릅니다.

2. 확인란 컨트롤은 사용하지 않도록 설정되어 있습니다. **시작**을 선택합니다.

     몇 초 안에 진행률 표시줄이 100% 완료로 표시됩니다.

3. 이제 확인란 컨트롤을 선택할 수 있습니다.

4. SimpleWPFApp를 닫습니다.

### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>SimpleWPFApp에 대해 코딩된 UI 테스트 만들기 및 실행

1. 앞에서 만든 SimpleWPFApp 애플리케이션을 찾습니다. 기본적으로 애플리케이션은 C:\Users\\&lt;사용자 이름\>\Documents\Visual Studio \<버전&gt;\Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe에 있습니다.

2. SimpleWPFApp 애플리케이션에 대한 바탕 화면 바로 가기를 만듭니다. SimpleWPFApp.exe를 마우스 오른쪽 단추로 클릭한 다음 **복사**를 선택합니다. 바탕 화면에서 마우스 오른쪽 단추를 클릭하고 **바로 가기 붙여넣기**를 선택합니다.

    > [!TIP]
    > 애플리케이션 바로 가기를 사용하면 애플리케이션을 신속하게 시작할 수 있기 때문에 애플리케이션에 대해 코딩된 UI 테스트를 쉽게 추가하거나 수정할 수 있습니다.

3. 솔루션 탐색기에서 솔루션을 마우스 오른쪽 단추로 클릭 하 고 **추가** 를 선택한 다음 **새 프로젝트**를 선택 합니다.

     **새 프로젝트 추가** 대화 상자가 나타납니다.

4. **설치됨** 창에서 **Visual C#** 을 확장한 다음 **테스트**를 선택합니다.

5. 가운데 창에서 **코딩된 UI 테스트 프로젝트** 템플릿을 선택합니다.

6. **확인**을 선택합니다.

     솔루션 탐색기에서 **CodedUITestProject1**이라는 새로 코딩된 UI 테스트 프로젝트가 솔루션에 추가됩니다.

     **코딩된 UI 테스트에 대한 코드 생성** 대화 상자가 나타납니다.

7. **작업 기록, UI 맵 편집 또는 어설션 추가** 옵션을 선택하고 **확인**을 선택합니다.

     UIMap – 코딩된 UI 테스트 빌더가 나타나고 Visual Studio 창이 최소화됩니다.

     대화 상자의 옵션에 대한 자세한 내용은 [코딩된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)를 참조하세요.

8. UIMap – 코딩된 UI 테스트 빌더에서 **기록 시작**을 선택합니다.

     ![녹화 시작](../test/media/cuit-builder-record.png "CUIT_Builder_Record")

     필요한 경우, 예를 들어 들어오는 메일을 처리해야 하는 경우 기록을 일시 중지할 수 있습니다.

     ![기록 일시 중지](../test/media/cuit.png "CUIT_")

    > [!WARNING]
    > 데스크톱에서 수행된 모든 작업이 기록됩니다. 기록에 중요한 데이터가 포함될 수 있는 작업을 수행하는 경우에는 기록을 일시 중지합니다.

9. 바탕 화면 바로 가기를 사용하여 SimpleWPFApp을 시작합니다.

     이전처럼 확인란 컨트롤은 사용하지 않도록 설정되어 있습니다.

10. SimpleWPFApp에서 **시작**을 선택합니다.

     몇 초 안에 진행률 표시줄이 100% 완료로 표시됩니다.

11. 이제 사용하도록 설정된 확인란 컨트롤을 선택합니다.

12. SimpleWPFApp 애플리케이션을 닫습니다.

13. UIMap-코딩 된 UI 테스트 빌더에서 **코드 생성**을 선택 합니다.

14. 메서드 이름에 **SimpleAppTest**를 입력하고 **추가 후 생성**을 선택합니다. 그러면 몇 초 안에 코딩된 UI 테스트가 나타나고 솔루션에 추가됩니다.

15. UIMap – 코딩된 UI 테스트 빌더를 닫습니다.

     CodedUITest1.cs 파일이 코드 편집기에 나타납니다.

16. 프로젝트를 저장합니다.

### <a name="run-the-coded-ui-test"></a>코딩된 UI 테스트 실행

1. **테스트** 메뉴에서 **창** 을 선택한 다음 **테스트 탐색기**를 선택 합니다.

2. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

3. CodedUITest1.cs 파일에서 **CodedUITestMethod** 메서드를 찾아 마우스 오른쪽 단추로 클릭한 다음 **테스트 실행**을 선택하거나 테스트 탐색기에서 테스트를 실행합니다.

     코딩된 UI 테스트가 실행되는 동안 SimpleWPFApp를 볼 수 있습니다. 이전 절차에서 수행한 단계가 실행됩니다. 그러나 테스트에서 확인란 컨트롤에 해당하는 확인란을 선택하려고 시도하면 테스트 결과 창에서 테스트가 실패했음을 보여 줍니다. 진행률 표시줄이 100% 완료 상태가 될 때까지 확인란 컨트롤을 사용할 수 없다는 사실을 모르고 테스트에서 해당 확인란을 선택하려고 시도했기 때문입니다. 이와 같은 문제는 코딩된 UI 테스트에 사용할 수 있는 다양한 `UITestControl.WaitForControlXXX()` 메서드를 사용하여 해결할 수 있습니다. 다음 절차에서는 `WaitForControlEnabled()` 메서드를 사용하여, 테스트 실패의 원인이 된 문제를 해결하는 방법을 보여 줍니다. 자세한 내용은 [코딩 된 UI 테스트가 재생 중 특정 이벤트를 기다리도록 설정](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)을 참조 하세요.

### <a name="edit-and-rerun-the-coded-ui-test"></a>코딩된 UI 테스트 편집 및 다시 실행

1. 테스트 탐색기 창에서 실패한 테스트를 선택하고 **StackTrace** 섹션에서 **UIMap.SimpleAppTest()** 에 대한 첫 번째 링크를 선택합니다.

2. UIMap.Designer.cs 파일이 열리고 코드에서 오류 지점이 강조 표시되어 있습니다.

    ```csharp

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. 이 문제를 해결하려면 `WaitForControlEnabled()` 메서드를 사용하여 이 줄을 계속하기 전에 UI 테스트에서 CheckBox 컨트롤을 기다릴 수 있도록 설정하면 됩니다.

    > [!WARNING]
    > UIMap.Designer.cs 파일은 수정하지 마세요. UIMap - 코딩된 UI 테스트 빌더를 사용하여 코드를 생성할 때마다 UIMapDesigner.cs 파일에서 수정된 코드 변경 내용을 덮어씁니다. 기록된 메서드를 수정해야 하는 경우에는 해당 메서드를 UIMap.cs 파일에 복사한 후 이름을 바꾸어야 합니다. UIMap.cs 파일을 사용하여 UIMapDesigner.cs 파일의 메서드와 속성을 재정의할 수 있습니다. 코딩된 UITest.cs 파일에서 원래 메서드에 대한 참조를 제거하고 이름을 바꾼 메서드 이름으로 바꾸어야 합니다.

4. 솔루션 탐색기에서 코딩된 UI 테스트 프로젝트의 **UIMap.uitest**를 찾습니다.

5. **UIMap.uitest**에 대한 바로 가기 메뉴를 열고 **열기**를 선택합니다.

     코딩된 UI 테스트가 코딩된 UI 테스트 편집기에 표시됩니다. 이제 코딩된 UI 테스트를 보고 편집할 수 있습니다.

6. **UI 작업** 창에서 UIMap.cs 또는 UIMap.vb 파일로 이동할 테스트 메서드(SimpleAppTest)를 선택하면 테스트 코드를 다시 컴파일할 때 덮어쓰이지 않는 사용자 지정 코드 기능이 더 쉬워집니다.

7. 코딩된 UI 테스트 편집기 도구 모음에서 **코드 이동** 단추를 선택합니다.

8. Microsoft Visual Studio 대화 상자가 표시됩니다. 메서드가 UIMap.uitest 파일에서 UIMap.cs 파일로 이동하며 더 이상 코딩된 UI 테스트 편집기를 사용하여 메서드를 편집할 수 없다는 경고가 나타납니다. **예**를 선택합니다.

     테스트 메서드가 UIMap.uitest 파일에서 제거되고 더 이상 UI 작업 창에 표시되지 않습니다. 이동한 테스트 파일을 편집하려면 솔루션 탐색기에서 UIMap.cs 파일을 엽니다.

9. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 도구 모음에서 **저장**을 선택 합니다.

     테스트 메서드 업데이트가 UIMap.Designer 파일에 저장됩니다.

    > [!CAUTION]
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

13. CodedUITest1.cs 파일에서 **CodedUITestMethod** 메서드를 찾고 원래 SimpleAppTest() 메서드에 대한 참조를 주석으로 처리하거나 이름을 바꾼 다음 새 ModifiedSimpleAppTest():로 바꿉니다.

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

14. **빌드** 메뉴에서 **솔루션 빌드**를 선택 합니다.

15. **CodedUITestMethod** 메서드를 마우스 오른쪽 단추로 클릭하고 **테스트 실행**을 선택합니다.

16. 이번에는 코딩된 UI 테스트가 테스트의 모든 단계를 성공적으로 수행하며 테스트 탐색기 창에 **성공**으로 표시됩니다.

### <a name="refactor-a-control-in-the-simplewpfapp"></a>SimpleWPFApp의 컨트롤 리팩터링

1. Designer의 MainWindow.xaml 파일에서 Button 컨트롤을 선택합니다.

2. 속성 창 상단에서 **Name** 속성 값을 button1에서 buttonA로 변경합니다.

3. **빌드** 메뉴에서 **솔루션 빌드**를 선택 합니다.

4. 테스트 탐색기에서 **CodedUITestMethod1**를 실행 합니다.

     코딩된 UI 테스트가 원래 UIMap에서 button1으로 매핑된 Button 컨트롤을 찾을 수 없으므로 테스트가 실패합니다. 리팩터링은 코딩된 UI 테스트에 이러한 방식으로 영향을 줄 수 있습니다.

5. 테스트 탐색기 창의 **StackTrace** 섹션에서 **UIMpa.ModifiedSimpleAppTest()** 옆의 첫 번째 링크를 선택합니다.

     UIMap.cs 파일이 열립니다. 코드에서 오류 지점이 강조 표시됩니다.

    ```csharp

    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     이 절차 앞부분의 코드 줄에서는 리팩터링되기 전의 UIMap 이름인 `UiStartButton`을 사용합니다.

     이 문제를 해결하려면 코딩된 UI 테스트 빌더를 사용하여 UIMap에 리팩터링된 컨트롤을 추가하면 됩니다. 다음 절차에서와 같이 코드를 사용하도록 테스트의 코드를 업데이트할 수 있습니다.

### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>리팩터링된 컨트롤 매핑 및 코딩된 UI 테스트 편집 및 다시 실행

1. CodedUITest1.cs 파일의 **CodedUITestMethod1()** 메서드에서 마우스 오른쪽 단추를 클릭하고 **코딩된 UI 테스트에 대한 코드 생성**을 선택한 다음 **코딩된 UI 테스트 빌더 사용**을 선택합니다.

     UIMap – 코딩된 UI 테스트 빌더가 나타납니다.

2. 앞에서 만든 바탕 화면 바로 가기를 사용하여, 앞에서 만든 SimpleWPFApp 애플리케이션을 실행합니다.

3. UIMap – 코딩된 UI 테스트 빌더에서 십자형 도구를 SimpleWPFApp의 **시작** 단추로 끌어옵니다.

     **시작** 단추가 파랑 상자 안에 포함되며 코딩된 UI 테스트 빌더에서 몇 초 안에 선택한 컨트롤의 데이터가 처리되고 컨트롤 속성이 표시됩니다. **AutomationUId**의 이름은 **buttonA**로 지정됩니다.

4. 컨트롤에 대한 속성에서 왼쪽 위 모퉁이의 화살표를 선택하여 UI 컨트롤 맵을 확장합니다. **UIStartButton1**이 선택되어 있습니다.

5. 도구 모음에서 **UI 컨트롤 맵에 컨트롤 추가**를 선택합니다.

     창 맨 아래에 **선택한 컨트롤이 UI 컨트롤 맵에 추가되었습니다.** 라는 상태가 표시되어 작업을 확인할 수 있습니다.

6. UIMap – 코딩된 UI 테스트 빌더에서 **코드 생성**을 선택합니다.

     새 메서드가 필요하지 않으며 UI 컨트롤 맵의 변경 내용에 대해서만 코드가 생성될 것이라는 메모와 함께 코딩된 UI 테스트 빌더 – 코드 생성이 나타납니다.

7. **생성**을 선택합니다.

8. SimpleWPFApp.exe를 닫습니다.

9. UIMap – 코딩된 UI 테스트 빌더를 닫습니다.

     UIMap – 코딩된 UI 테스트 빌더에서 몇 초 안에 UI 컨트롤 맵 변경 내용이 처리됩니다.

10. 솔루션 탐색기에서 UIMap.Designer.cs 파일을 엽니다.

11. UIMap.Designer.cs 파일에서 UIStartButton1 속성을 찾습니다. `SearchProperties`가 `"buttonA"`로 설정되어 있습니다.

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

     이제 새로 매핑된 컨트롤을 사용하도록 코딩된 UI 테스트를 수정할 수 있습니다. 이전 절차에서 언급했듯이 코딩된 UI 테스트에서 메서드나 속성을 재정의하려는 경우에는 UIMap.cs 파일에서 재정의해야 합니다.

12. UIMap.cs 파일에서 생성자를 추가하고 `SearchProperties` 값을 가진 `UIStartButton` 속성을 사용하도록 `AutomationID` 속성의 `"buttonA":` 속성을 지정합니다.

    ```csharp

    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }

    ```

13. **빌드** 메뉴에서 **솔루션 빌드**를 선택 합니다.

14. 테스트 탐색기에서 CodedUITestMethod1을 실행합니다.

     이번에는 코딩된 UI 테스트가 테스트의 모든 단계를 성공적으로 수행합니다.  테스트 결과 창에 상태가 **성공**으로 표시됩니다.

## <a name="external-resources"></a>외부 리소스

### <a name="videos"></a>동영상
 비디오 코딩 된 UI 테스트 ![에 대 한 링크](../data-tools/media/playvideo.gif "링크 playvideo 보려면") [-DeepDive-Deepdive-episode1-gettingstarted-get started](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21118)

 비디오 코딩 된 UI 테스트 ![에 대 한 링크](../data-tools/media/playvideo.gif "링크 playvideo 보려면") [-DeepDive-Episode2-deepdive-episode2-maintainenceanddebugging](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21116)

 비디오 코딩 된 UI 테스트 ![에 대 한 링크](../data-tools/media/playvideo.gif "링크 playvideo 보려면") [-DeepDive-Episode3-핸드 코딩](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21117)

### <a name="hands-on-lab"></a>실습
 [MSDN 가상 랩: Visual Studio 2010을 사용하여 코딩된 UI 테스트 만들기 소개](https://windows.microsoft.com/en-US/windows/products/windows-media-player)

### <a name="faq"></a>FAQ
 [코딩된 UI 테스트 FAQ - 1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [코딩된 UI 테스트 FAQ - 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>포럼
 [Visual Studio UI 자동화 테스트(CodedUI 포함)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>참고 항목
 [UI 자동화를 사용 하 여 코드 테스트](../test/use-ui-automation-to-test-your-code.md) 코딩 [된](https://msdn.microsoft.com/18e61d03-b96a-4058-a166-8ec6b3f6116b) [ui 테스트 및 작업 기록에 대해 지원 되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) 코딩 된 Ui 테스트 [편집기를 사용 하 여 코딩 된 ui 테스트 편집](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
