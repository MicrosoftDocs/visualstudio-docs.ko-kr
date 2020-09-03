---
title: 코딩된 UI 테스트로 UWP 앱 테스트
ms.date: 05/31/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: aad17d244d70051a363a4cde294c592968093ba0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286754"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>UWP 앱을 테스트하기 위한 코딩된 UI 테스트 만들기

이 문서에서는 UWP(유니버설 Windows 플랫폼) 앱을 위한 코딩된 UI 테스트를 만드는 방법을 설명합니다.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>테스트할 UWP 앱 만들기

첫 번째 단계는 테스트를 실행하기 위한 간단한 UWP 앱을 만드는 것입니다.

1. Visual Studio에서 Visual C# 또는 Visual Basic을 위한 **비어 있는 앱(유니버설 Windows)** 템플릿을 사용하여 새 프로젝트를 만듭니다.

   ::: moniker range="vs-2017"

   ![비어 있는 앱 유니버설 Windows 템플릿](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. **새 유니버설 Windows 플랫폼 프로젝트** 대화 상자에서 **확인**을 선택하여 기본 플랫폼 버전을 승인합니다.

1. **솔루션 탐색기**에서 *MainPage.xaml*을 엽니다.

   파일이 **XAML 디자이너**에서 열립니다.

1. 단추 컨트롤과 텍스트 상자 컨트롤을 **도구 상자**에서 디자인 화면으로 끕니다.

     ![UWP 앱 디자인](../test/media/toolbox-controls.png)

1. 컨트롤에 이름을 지정합니다. 텍스트 상자 컨트롤을 선택한 다음, **속성** 창의 **이름** 필드에 **textBox**를 입력합니다. 단추 컨트롤을 선택한 다음, **속성** 창의 **이름** 필드에 **단추**를 입력합니다.

1. 단추 컨트롤을 두 번 클릭하고 `Button_Click` 메서드의 본문에 다음 코드를 추가합니다. 이 코드는 텍스트 상자의 텍스트를 단추 컨트롤의 이름으로 설정하기만 하면, 나중에 작성할 코딩된 UI 테스트로 확인할 수 있는 사항을 제공합니다.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. **Ctrl**+**F5**를 눌러 앱을 실행합니다. 다음과 같은 정보가 표시됩니다.

   ![단추 및 텍스트 상자가 포함된 UWP 앱](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>코딩된 UI 테스트 만들기

1. 솔루션에 테스트 프로젝트를 추가하려면 **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

1. **코딩된 UI 테스트 프로젝트(유니버설 Windows)** 템플릿을 검색하여 선택합니다.

   ::: moniker range="vs-2017"

   ![새로운 코딩된 UI 테스트 프로젝트](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > **코딩된 UI 테스트 프로젝트(유니버설 Windows)** 템플릿이 표시되지 않으면 [코딩된 UI 테스트 구성 요소를 설치](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)해야 합니다.

1. **코딩된 UI 테스트에 대한 코드 생성** 대화 상자에서 **수동으로 테스트 편집**을 선택합니다.

   ![코딩된 UI 테스트에 대한 코드 생성 대화 상자](../test/media/manually-edit-the-test.png)

1. UWP 앱이 아직 실행되고 있지 않다면 **Ctrl**+**F5**를 눌러 앱을 시작합니다.

1. `CodedUITestMethod1` 메서드에 커서를 놓고 **테스트** > **코딩된 UI 테스트에 대한 코드 생성** > **코딩된 UI 테스트 빌더 사용**을 선택하여 **코딩된 UI 테스트 빌더** 대화 상자를 엽니다.

1. UI 컨트롤 맵에 컨트롤을 추가합니다. **코딩된 UI 테스트 빌더** 십자선 도구를 사용하여 UWP 앱에서 단추 컨트롤을 선택합니다. **어설션 추가** 대화 상자에서 필요한 경우 **UI 컨트롤 맵** 창을 확장한 다음, **UI 컨트롤 맵에 컨트롤 추가**를 선택합니다.

     ![UI 맵에 컨트롤 추가](../test/media/add-control-to-ui-control-map.png)

1. 이전 단계를 반복하여 UI 컨트롤 맵에 텍스트 상자 컨트롤을 추가합니다.

1. **코딩된 UI 테스트 빌더** 대화 상자에서 **코드 생성**을 선택하거나 **Ctrl**+**G**를 누릅니다. 그런 다음, **생성**을 선택하여 UI 컨트롤 맵을 변경할 코드를 생성합니다.

     ![UI 맵에 대한 코드 생성](../test/media/generate-code-dialog.png)

1. 단추를 클릭할 때 텍스트 상자의 텍스트가 **단추**로 변경되는지 확인하려면 단추를 클릭합니다.

     ![단추 컨트롤을 클릭하여 텍스트 상자 값 설정](../test/media/uwp-app-button-textbox.png)

1. 어설션을 추가하여 텍스트 상자 컨트롤의 텍스트를 확인합니다. 십자선 도구를 사용하여 텍스트 상자 컨트롤을 선택한 다음, **어설션 추가** 대화 상자에서 **텍스트** 속성을 선택합니다. 그런 다음, **어설션 추가**를 선택하거나 **Alt**+**A**를 누릅니다. **어설션 실패 메시지** 상자에서 **텍스트 상자 값이 올바르지 않음**을 입력한 다음, **확인**을 선택합니다.

     ![십자선으로 텍스트 상자를 선택하고 어설션 추가](../test/media/add-assertion-for-text.png)

1. 어설션에 대한 테스트 코드를 생성합니다. **코딩된 UI 테스트 빌더** 대화 상자에서 **코드 생성**을 선택합니다. **코드 생성** 대화 상자에서 **추가 및 생성**을 선택합니다.

     ![텍스트 상자 어설션에 대한 코드 생성](../test/media/add-and-generate-assert-method.png)

   **솔루션 탐색기**에서 *UIMap.Designer.cs*를 열어 assert 메서드 및 컨트롤에 대해 추가한 코드를 확인합니다.

   > [!TIP]
   > Visual Basic을 사용하는 경우 *CodedUITest1.vb*를 엽니다. 그런 다음, `CodedUITestMethod1()` 테스트 메서드 코드에서 assert 메서드 `Me.UIMap.AssertMethod1()`에 대한 호출을 마우스 오른쪽 단추로 클릭하고 **정의로 이동**을 선택합니다. *UIMap.Designer.vb*가 코드 편집기에서 열리고, assert 메서드와 컨트롤에 추가된 코드를 확인할 수 있습니다.

    > [!WARNING]
    > *UIMap.designer.cs* 또는 *UIMap.Designer.vb* 파일은 직접 수정하지 마세요. 그러면 테스트가 생성될 때 변경 내용이 덮어써집니다.

    이 assert 메서드는 다음과 같습니다.

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. 그런 다음, 테스트할 UWP [앱](#create-a-uwp-app-to-test)의 **AutomationId**를 가져와야 합니다. Windows **시작** 메뉴를 열어 앱의 타일을 확인합니다. 그런 다음, **코딩된 UI 테스트 빌더** 대화 상자에서 십자선 도구 ![대상 아이콘](media/target-icon.png)을 앱의 타일로 끕니다. 파란색 상자가 타일을 둘러싸면 마우스를 놓습니다.

   ![십자선 도구](media/cross-hair-tool.png)

   **어설션 추가** 대화 상자가 열리고 앱의 **AutomationId**가 표시됩니다. **AutomationId**를 마우스 오른쪽 단추로 클릭하고 **값을 클립보드로 복사**를 선택합니다.

   ![어설션 추가 대화 상자의 AutomationID](../test/media/automation-id.png)

1. 테스트 메서드에 코드를 추가하여 UWP 앱을 시작합니다. **솔루션 탐색기**에서 *CodedUITest1.cs* 또는 *CodedUITest1.vb*를 엽니다. `AssertMethod1`에 대한 호출 위에 UWP 앱을 실행하는 코드를 추가합니다.

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   예제 코드의 자동화 ID를 이전 단계에서 클립보드에 복사한 값으로 바꿉니다.

   > [!IMPORTANT]
   > 자동화 ID의 시작 부분을 잘라내어 **P~** 와 같은 문자를 제거합니다. 이러한 문자를 잘라내지 않으면 테스트에서 앱을 실행하려고 할 때 `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException`이 throw됩니다.

1. 그런 다음, 테스트 메서드에 코드를 추가하여 단추를 클릭합니다. `XamlWindow.Launch` 이후의 줄에 단추 컨트롤을 누르는 제스처를 추가합니다.

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   코드를 추가한 후 전체 `CodedUITestMethod1` 테스트 메서드가 다음과 같이 나타나야 합니다.

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. 테스트 프로젝트를 빌드한 다음, **테스트** > **Windows** > **테스트 탐색기**를 선택하여 **테스트 탐색기**를 엽니다.

1. **모두 실행**을 선택하여 테스트를 실행합니다.

   앱이 열리고 단추를 누르면 텍스트 상자의 **텍스트** 속성이 채워집니다. assert 메서드는 텍스트 상자의 **텍스트** 속성의 유효성을 검사합니다.

   테스트를 완료하면 **테스트 탐색기**에는 테스트를 통과했음이 표시됩니다.

   ![테스트 탐색기에 표시된 통과한 테스트](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Q&A

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Q: 코딩된 UI 테스트용으로 코드 생성 대화 상자에 내 코딩된 UI 테스트를 기록할 수 있는 옵션이 표시되지 않는 이유는 무엇인가요?

**A**: UWP 앱의 경우 기록 옵션이 지원되지 않습니다.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>Q: WinJS를 기반으로 UWP 스토어 앱용 코딩된 UI 테스트를 만들 수 있나요?

**A**: 아니요, XAML 기반 앱만 지원됩니다.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Q: UIMap.Designer 파일에서 코드를 수정할 수 없는 이유는 무엇인가요?

**A**: **코딩된 UI 테스트 빌더**를 사용하여 코드를 생성할 때마다 *UIMapDesigner.cs* 파일에서 수정된 코드 변경 내용을 덮어씁니다. 기록된 메서드를 수정해야 하는 경우 해당 메서드를 *UIMap.cs* 파일에 복사하고 이름을 바꿉니다. *UIMap.cs* 파일을 사용하여 *UIMapDesigner.cs* 파일의 메서드와 속성을 재정의할 수 있습니다. *CodedUITest.cs* 파일에서 원래 메서드에 대한 참조를 제거하고 이름을 바꾼 메서드 이름으로 바꿉니다.

## <a name="see-also"></a>참조

- [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [UWP 컨트롤에 대한 고유한 자동화 속성 설정](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
