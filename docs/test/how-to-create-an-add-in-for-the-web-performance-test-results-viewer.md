---
title: 웹 성능 테스트 결과 뷰어에 대한 추가 기능 만들기
ms.date: 10/20/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 736c43a83a956c02b760b4909a427a82c6fa9e4c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287833"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>방법: 웹 성능 테스트 결과 뷰어에 대한 추가 기능 만들기

다음 네임스페이스를 사용하여 **웹 성능 테스트 결과 뷰어**의 UI를 확장할 수 있습니다.

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

또한 *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<version>\Enterprise\Common7\IDE\PrivateAssemblies* 폴더에 있는 LoadTestPackage DLL에 대한 참조를 추가해야 합니다.

**웹 성능 테스트 결과 뷰어**의 UI를 확장하려면 Visual Studio 추가 기능과 사용자 정의 컨트롤을 만들어야 합니다. 다음 절차에서는 추가 기능 및 사용자 정의 컨트롤을 만드는 방법과 **웹 성능 테스트 결과 뷰어**의 UI를 확장하는 데 필요한 클래스를 구현하는 방법에 대해 설명합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>ASP.NET 웹 애플리케이션과 웹 성능 및 부하 테스트 프로젝트를 포함하는 솔루션 만들기 또는 열기

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>웹 성능 테스트 결과 뷰어 확장을 준비하려면

과정을 따라 하는 데 사용할 수 있도록 ASP.NET 웹 애플리케이션과 이 ASP.NET 웹 애플리케이션에 대한 웹 성능 테스트가 하나 이상 들어 있는 웹 성능 및 부하 테스트 프로젝트를 포함하는 비프로덕션 솔루션을 만들거나 엽니다.

> [!NOTE]
> ASP.NET 웹 애플리케이션과 웹 성능 테스트가 포함된 웹 성능 및 부하 테스트 프로젝트를 [방법: 웹 서비스 테스트 만들기](../test/how-to-create-a-web-service-test.md) 및 [코딩된 웹 성능 테스트 생성 및 실행](../test/generate-and-run-a-coded-web-performance-test.md)의 절차에 따라 만들 수 있습니다.

## <a name="create-a-visual-studio-add-in"></a>Visual Studio 추가 기능 만들기

추가 기능은 Visual Studio IDE(통합 개발 환경)에서 실행되는 컴파일된 DLL입니다. 컴파일을 통해 지적 자산을 보호하고 성능을 향상시킬 수 있습니다. 추가 기능을 수동으로 만들 수도 있지만 **추가 기능 마법사**를 사용하는 편이 훨씬 더 쉽습니다. 추가 기능 마법사를 사용하면 기본 기능을 갖춘 추가 기능을 만들어서 바로 실행할 수 있습니다. **추가 기능 마법사**가 기본적인 프로그램을 생성한 후 코드를 추가하여 프로그램을 사용자 지정할 수 있습니다.

**추가 기능 마법사**를 사용하여 추가 기능의 표시 이름과 설명을 제공할 수 있습니다. 이 둘은 모두 **추가 기능 관리자**에 표시됩니다. 필요할 경우 마법사를 통해 추가 기능을 여는 명령을 **도구** 메뉴에 추가하는 코드를 생성할 수 있습니다. 또한 추가 기능에 대한 사용자 지정 **정보** 대화 상자를 표시하도록 선택할 수도 있습니다. 마법사가 완료되면 추가 기능을 구현하는 Connect라는 하나의 클래스만 있는 새 프로젝트가 생성됩니다.

이 아티클의 끝부분에서는 **추가 기능 관리자**를 사용해 봅니다.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>추가 기능 마법사를 사용하여 추가 기능을 만들려면

1. **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고, **추가**를 선택한 다음, **새 프로젝트**를 선택합니다.

2. 새 **Visual Studio Console 추가 기능** 프로젝트를 만듭니다.

    Visual Studio **추가 기능 마법사**가 시작됩니다.

3. **다음**을 선택합니다.

4. **프로그래밍 언어 선택** 페이지에서 추가 기능을 작성하는 데 사용할 프로그래밍 언어를 선택합니다.

   > [!NOTE]
   > 이 항목의 샘플 코드에서는 Visual C#을 사용합니다.

5. **애플리케이션 호스트 선택** 페이지에서 **Visual Studio**를 선택하고 **Visual Studio 매크로**의 선택을 취소합니다.

6. **다음**을 선택합니다.

7. **이름 및 설명 입력** 페이지에 추가 기능의 이름과 설명을 입력합니다.

     추가 기능을 만든 후 추가 기능 이름과 설명은 **추가 기능 관리자**의 **사용 가능한 추가 기능** 목록에 표시됩니다. 사용자가 추가 기능의 역할과 작동 방식 등을 쉽게 알 수 있도록 추가 기능에 대한 자세한 설명을 추가합니다.

8. **다음**을 선택합니다.

9. **추가 기능 옵션 선택** 페이지에서 **호스트 애플리케이션이 시작될 때 추가 기능을 로드합니다.** 를 선택합니다.

10. 나머지 확인란의 선택을 취소합니다.

11. **'도움말' 정보 선택** 페이지에서 추가 기능에 대한 정보를 **정보** 대화 상자에 표시할지 여부를 지정할 수 있습니다. 정보를 표시하려면 **예, 추가 기능에 '정보' 상자를 제공합니다.** 확인란을 선택합니다.

     Visual Studio **정보** 대화 상자에 추가할 수 있는 정보에는 버전 번호, 지원 세부 사항, 라이선스 데이터 등이 있습니다.

12. **다음**을 선택합니다.

13. 선택한 옵션은 검토를 위해 **요약** 페이지에 표시됩니다. 옵션이 올바르면 **마침**을 선택하여 추가 기능을 만듭니다. 옵션을 변경하려면 **다시** 단추를 선택합니다.

     새 솔루션과 프로젝트가 만들어지고 새 추가 기능에 대한 *Connect.cs* 파일이 **코드 편집기**에 표시됩니다.

     다음 절차에서 이 WebPerfTestResultsViewerAddin 프로젝트에서 참조할 사용자 정의 컨트롤을 만든 후에는 이 *Connect.cs* 파일에 코드를 추가합니다.

    추가 기능을 만든 후에는 먼저 Visual Studio에 등록해야 **추가 기능 관리자**에서 활성화할 수 있습니다. 이 작업은 파일 확장명이 *.addin*인 XML 파일을 사용하여 수행합니다.

    *.addin* 파일에서는 Visual Studio가 **추가 기능 관리자**에 추가 기능을 표시하는 데 필요한 정보를 설명합니다. Visual Studio가 시작되면 *.addin* 파일 위치에서 사용할 수 있는 모든 *.addin* 파일을 찾습니다. 이 파일이 발견되면 Visual Studio에서는 XML 파일을 읽고 사용자가 추가 기능을 클릭할 때 이를 시작하는 데 필요한 정보를 **추가 기능 관리자**에 제공합니다.

    **추가 기능 마법사**를 사용하여 추가 기능을 만들 때 *.addin* 파일이 자동으로 만들어집니다.

### <a name="add-in-file-locations"></a>추가 기능 파일 위치

다음과 같이 **추가 기능 마법사**를 통해 두 개의 *.addin* 파일 복사본이 자동으로 만들어집니다.

|**.Addin 파일 위치**|**설명**|
|-|----------------------------|-|
|루트 프로젝트 폴더|추가 기능 프로젝트의 배포에 사용됩니다. 간편한 편집을 위해 프로젝트에 포함되며 XCopy 방식의 배포를 위한 로컬 경로가 있습니다.|
|추가 기능 폴더|디버깅 환경에서 추가 기능을 실행하는 데 사용됩니다. 항상 현재 빌드 구성의 출력 경로를 가리켜야 합니다.|

## <a name="create-a-windows-form-control-library-project"></a>Windows Form 컨트롤 라이브러리 프로젝트 만들기

이전 절차에서 만든 Visual Studio 추가 기능은 Windows Forms 컨트롤 라이브러리 프로젝트를 참조하여 <xref:System.Windows.Forms.UserControl> 클래스의 인스턴스를 만듭니다.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>웹 테스트 결과 뷰어에 사용할 컨트롤을 만들려면

1. **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고, **추가**를 선택한 다음, **새 프로젝트**를 선택합니다.

2. 새 **Windows Forms 컨트롤 라이브러리** 프로젝트를 만듭니다.

3. **도구 상자**에서 <xref:System.Windows.Forms.DataGridView>를 userControl1의 화면으로 끌어옵니다.

4. <xref:System.Windows.Forms.DataGridView>의 오른쪽 위 모퉁이에서 작업 태그 문자 모양(![스마트 태그 문자 모양](../test/media/vs_winformsmttagglyph.gif))을 클릭합니다.

    1. **부모 컨테이너에서 도킹**을 선택합니다.

    2. **추가 사용**, **편집 사용**, **삭제 사용** 및 **열 다시 정렬 사용** 확인란의 선택을 취소합니다.

    3. **열 추가**를 선택합니다.

         **열 추가** 대화 상자가 표시됩니다.

    4. **형식** 드롭다운 목록에서 **DataGridViewTextBoxColumn**을 선택합니다.

    5. **머리글 텍스트**의 "Column1" 텍스트를 지웁니다.

    6. **추가**를 선택합니다.

    7. **닫기**를 선택합니다.

5. **속성** 창에서 <xref:System.Windows.Forms.DataGridView>의 **(이름)** 속성을 **resultControlDataGridView**로 변경합니다.

6. 디자인 화면을 마우스 오른쪽 단추로 클릭하고 **코드 보기**를 선택합니다.

     *UserControl1.cs* 파일이 **코드 편집기**에 표시됩니다.

7. 인스턴스화된 <xref:System.Windows.Forms.UserControl> 클래스의 이름을 UserContro1에서 resultControl로 바꿉니다.

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     다음 절차에서는 WebPerfTestResultsViewerAddin 프로젝트의 *Connect.cs* 파일에 resultControl 클래스를 참조하는 코드를 추가합니다.

     나중에 *Connect.cs* 파일에 코드를 좀 더 추가할 것입니다.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>WebPerfTestResultsViewerAddin에 코드 추가

1. **솔루션 탐색기**에서 WebPerfTestResultsViewerAddin 프로젝트의 **참조** 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

2. **참조 추가** 대화 상자에서 **.NET** 탭을 선택합니다.

3. 아래로 스크롤하여 **Microsoft.VisualStudio.QualityTools.WebTestFramework** 및 **System.Windows.Forms**를 선택합니다.

4. **확인**을 선택합니다.

5. **참조** 노드를 다시 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

6. **참조 추가** 대화 상자에서 **찾아보기** 탭을 선택합니다.

7. **찾는 위치**의 드롭다운을 선택하고, *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*로 이동하고, *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* 파일을 선택합니다.

8. **확인**을 선택합니다.

9. WebPerfTestResultsViewerAddin 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

10. **참조 추가** 대화 상자에서 **프로젝트** 탭을 선택합니다.

11. **프로젝트 이름**에서 **WebPerfTestResultsViewerControl** 프로젝트를 선택하고 **확인**을 선택합니다.

12. *Connect.cs* 파일이 아직 열려 있지 않으면 **솔루션 탐색기**에서 WebPerfTestResultsViewerAddin 프로젝트의 **Connect.cs** 파일을 마우스 오른쪽 단추로 클릭하고 **코드 보기**를 선택합니다.

13. *Connect.cs* 파일에 다음 Using 문을 추가합니다.

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. *Connect.cs* 파일의 맨 아래로 스크롤합니다. **웹 성능 테스트 결과 뷰어** 인스턴스가 둘 이상 열려 있는 경우에는 <xref:System.Windows.Forms.UserControl>에 대한 GUID 목록을 추가해야 합니다. 나중에 이 목록을 사용하는 코드를 추가합니다.

     문자열의 두 번째 목록은 나중에 코딩할 OnDiscconection 메서드에 사용됩니다.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. *Connect.cs* 파일은 <xref:Extensibility.IDTExtensibility2> 클래스에서 Connect라는 클래스를 인스턴스화하며, Visual Studio 추가 기능을 구현하기 위한 몇 가지 메서드도 포함합니다. 그 중 하나는 추가 기능이 로드되고 있다는 알림을 받는 OnConnection 메서드입니다. OnConnection 메서드에서 LoadTestPackageExt 클래스를 사용하여 **웹 성능 테스트 결과 뷰어**용 확장성 패키지를 만듭니다. OnConnection 메서드에 다음 코드를 추가합니다.

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Connect 클래스에 다음 코드를 추가하여 OnConnection 메서드에 추가한 loadTestPackageExt.WebTestResultViewerExt.WindowCreated 이벤트 처리기와 WebTestResultViewerExt_WindowCreated 메서드가 호출하는 WindowCreated 메서드에 대한 WebTestResultViewerExt_WindowCreated 메서드를 만듭니다.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Connect 클래스에 다음 코드를 추가하여 OnConnection 메서드에 추가한 loadTestPackageExt.WebTestResultViewerExt.SelectionChanged 이벤트 처리기에 대한 WebTestResultViewer_SelectedChanged 메서드를 만듭니다.

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Connect 클래스에 다음 코드를 추가하여 OnConnection 메서드에 추가한 loadTestPackageExt.WebTestResultViewerExt.WindowClosed 이벤트 처리기에 대한 WebTesResultViewer_WindowClosed 메서드를 만듭니다.

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     이제 Visual Studio 추가 기능에 대한 코드를 모두 작성했으므로 WebPerfTestResultsViewerControl 프로젝트의 resultControl에 Update 메서드를 추가해야 합니다.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>WebPerfTestResultsViewerControl에 코드 추가

1. **솔루션 탐색기**에서 WebPerfTestResultsViewerControl 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

2. **애플리케이션** 탭을 선택한 다음, **대상 프레임워크** 드롭다운 목록을 선택하고, **.NET Framework 4**(또는 이상)를 선택합니다. **속성** 창을 닫습니다.

   이 단계는 **웹 성능 테스트 결과 뷰어**를 확장하는 데 필요한 DLL 참조를 지원하는 데 필요합니다.

3. **솔루션 탐색기**에서 WebPerfTestResultsViewerControl 프로젝트의 **참조** 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

4. **참조 추가** 대화 상자에서 **.NET** 탭을 클릭합니다.

5. 아래로 스크롤하여 **Microsoft.VisualStudio.QualityTools.WebTestFramework**를 선택합니다.

6. **확인**을 선택합니다.

7. *UserControl1.cs* 파일에 다음 Using 문을 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. *Connect.cs* 파일에 WebPerfTestResultsViewerAddin의 WebTestResultViewer_SelectedChanged 메서드에서 호출되어 WebTestRequestResult를 전달받는 Update 메서드를 추가합니다. Update 메서드는 WebTestRequestResult에서 전달 받은 다양한 속성으로 DataGridView를 채웁니다.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-solution"></a>솔루션 빌드

- **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>WebPerfTestResultsViewerAddin 추가 기능 등록

1. **도구** 메뉴에서 **추가 기능 관리자**를 선택합니다.

2. **추가 기능 관리자** 대화 상자가 표시됩니다.

3. **사용 가능한 추가 기능** 열에서 WebPerfTestResultsViewerAddin 추가 기능의 확인란을 선택하고 **시작** 및 **명령줄** 열 아래에 있는 확인란의 선택을 취소합니다.

4. **확인**을 선택합니다.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>웹 테스트 결과 뷰어를 사용하여 웹 성능 테스트 실행

1. 웹 성능 테스트를 실행하면 **웹 성능 테스트 결과 뷰어**에 WebPerfTestResultsViewerAddin 추가 기능에 해당하는 새 탭이 샘플이라는 제목으로 표시됩니다.

2. 이 탭을 선택하여 DataGridView에 표시된 속성을 확인합니다.

## <a name="net-security"></a>.NET 보안

악의적인 추가 기능이 자동으로 활성화되지 않도록 방지하고 보안을 강화하기 위해 Visual Studio에서는 **추가 기능/매크로 보안**이라는 설정을 **도구 옵션** 페이지에 제공합니다.

또한 이 옵션 페이지에서는 Visual Studio에서 *.AddIn* 등록 파일을 검색할 폴더를 지정할 수 있습니다. 이 옵션으로 *.AddIn* 등록 파일을 읽을 수 있는 위치를 제한하여 보안을 강화할 수 있습니다. 이렇게 하면 악의적인 *.AddIn* 파일을 실수로 사용하는 것을 방지할 수 있습니다.

**추가 기능 보안 설정**

추가 기능 보안에 대한 옵션 페이지의 설정은 다음과 같습니다.

- **추가 기능 구성 요소 로드 허용.** 기본으로 선택됩니다. 이 옵션을 선택하면 Visual Studio에서 추가 기능을 로드할 수 있습니다. 이 옵션을 선택하지 않으면 추가 기능이 Visual Studio에서 로드되지 않습니다.

- **URL에서 추가 기능 구성 요소 로드 허용.** 기본적으로 선택되지 않습니다. 이 옵션을 선택하면 외부 웹 사이트에서 추가 기능을 로드할 수 있습니다. 이 옵션을 선택하지 않으면 원격 추가 기능이 Visual Studio에서 로드되지 않습니다. 다른 원인으로 인해 추가 기능을 로드할 수 없으면 웹에서도 이를 로드할 수 없습니다. 이 설정은 추가 기능 DLL의 로드만 제어합니다. *.Addin* 등록 파일은 항상 로컬 시스템에 있어야 합니다.

## <a name="see-also"></a>참조

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
