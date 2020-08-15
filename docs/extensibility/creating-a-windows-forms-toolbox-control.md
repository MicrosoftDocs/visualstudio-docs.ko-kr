---
title: Windows Forms 도구 상자 컨트롤 만들기 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb0f0e66d623f53c641126f1e07edaa476d831ae
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248602"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Windows Forms 도구 상자 컨트롤 만들기

Visual Studio 확장성 도구에 포함 된 Windows Forms 도구 상자 컨트롤 항목 템플릿 (VS SDK)을 사용 하면 확장을 설치할 때 자동으로 추가 되는 **도구 상자** 컨트롤을 만들 수 있습니다. 이 연습에서는 템플릿을 사용 하 여 다른 사용자에 게 배포할 수 있는 간단한 카운터 컨트롤을 만드는 방법을 보여 줍니다.

## <a name="prerequisites"></a>필수 구성 요소

Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-the-toolbox-control"></a>도구 상자 컨트롤 만들기

Windows Forms 도구 상자 컨트롤 템플릿은 정의 되지 않은 사용자 정의 컨트롤을 만들고 **도구 상자**에 컨트롤을 추가 하는 데 필요한 모든 기능을 제공 합니다.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Windows Forms 도구 상자 컨트롤을 사용 하 여 확장 만들기

1. 이라는 VSIX 프로젝트를 만듭니다 `MyWinFormsControl` . **새 프로젝트** 대화 상자에서 "vsix"를 검색 하 여 vsix 프로젝트 템플릿을 찾을 수 있습니다.

2. 프로젝트가 열리면 이라는 **Windows Forms 도구 상자 컨트롤** 항목 템플릿을 추가 합니다 `Counter` . **솔루션 탐색기**에서 프로젝트 노드를 선택 하 고 길게 클릭 하 고 **추가**  >  **새 항목**을 선택 합니다. **새 항목 추가** 대화 상자에서 **Visual c #**  >  **확장성** 으로 이동 하 고 **Windows Forms 도구 상자 컨트롤** 을 선택 합니다.

3. 그러면 사용자 정의 컨트롤이 추가 되 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 고, **도구 상자**에 컨트롤을 배치 하 고, 배포를 위한 VSIX 매니페스트의 **VisualStudio. ToolboxControl** Asset 항목이 추가 됩니다.

### <a name="build-a-user-interface-for-the-control"></a>컨트롤의 사용자 인터페이스를 빌드합니다.

컨트롤에는 `Counter` 두 개의 자식 컨트롤이 필요 합니다. <xref:System.Windows.Forms.Label> 현재 개수를 표시 하려면이 고, <xref:System.Windows.Forms.Button> 개수를 0으로 다시 설정 하려면입니다. 호출자가 카운터를 프로그래밍 방식으로 증가 시키므로 다른 자식 컨트롤이 필요 하지 않습니다.

#### <a name="to-build-the-user-interface"></a>사용자 인터페이스를 작성하려면

1. **솔루션 탐색기**에서 *Counter.cs* 를 두 번 누르거나 두 번 클릭 하 여 디자이너에서 엽니다.

2. 여기를 **클릭 하세요.** Windows Forms 도구 상자 컨트롤 항목 템플릿을 추가할 때 기본적으로 포함 되는 단추입니다.

3. **도구 상자**에서 컨트롤을 끌어 오고 `Label` `Button` 그 아래에 있는 컨트롤을 디자인 화면으로 끌어 옵니다.

4. 전체 사용자 정의 컨트롤의 크기를 150, 50 픽셀로 조정 하 고 단추 컨트롤의 크기를 50, 20 픽셀으로 조정 합니다.

5. **속성** 창에서 디자인 화면의 컨트롤에 대해 다음 값을 설정 합니다.

    |제어|속성|값|
    |-------------|--------------|-----------|
    |`Label1`|**텍스트**|""|
    |`Button1`|**이름**|btnReset|
    |`Button1`|**텍스트**|다시 설정|

### <a name="code-the-user-control"></a>사용자 정의 컨트롤 코딩

`Counter`컨트롤은 카운터를 증가 시키는 메서드, 카운터가 증가 될 때마다 발생 하는 이벤트, **다시 설정** 단추, 현재 개수를 저장 하는 세 가지 속성, 표시 텍스트 및 **다시 설정** 단추를 표시 하거나 숨길지 여부를 노출 합니다. `ProvideToolboxControl` 특성은 **도구 상자** 에서 `Counter` 컨트롤이 나타나는 위치를 결정합니다.

#### <a name="to-code-the-user-control"></a>사용자 정의 컨트롤을 코딩 하려면

1. 폼을 두 번 클릭 하거나 두 번 클릭 하 여 코드 창에서 해당 로드 이벤트 처리기를 엽니다.

2. 다음 예제와 같이 이벤트 처리기 메서드 위에 있는 컨트롤 클래스에서 카운터 값을 저장 하는 정수와 표시 텍스트를 저장할 문자열을 만듭니다.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. 다음 공용 속성 선언을 만듭니다.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    호출자는 이러한 속성에 액세스 하 여 카운터의 표시 텍스트를 가져오고 설정 하 고 **다시 설정** 단추를 표시 하거나 숨길 수 있습니다. 호출자는 읽기 전용 속성의 현재 값을 가져올 수 `Value` 있지만 값을 직접 설정할 수는 없습니다.

4. 컨트롤의 이벤트에 다음 코드를 추가 `Load` 합니다.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    이벤트의 **레이블** 텍스트를 설정 하면 <xref:System.Windows.Forms.UserControl.Load> 해당 값이 적용 되기 전에 대상 속성을 로드할 수 있습니다. 생성자에서 **레이블** 텍스트를 설정 하면 빈 **레이블이**생성 됩니다.

5. 카운터를 증가 시키는 다음 공용 메서드를 만듭니다.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. 이벤트에 대 한 선언을 `Incremented` 컨트롤 클래스에 추가 합니다.

    ```csharp
    public event EventHandler Incremented;
    ```

    호출자는이 이벤트에 처리기를 추가 하 여 카운터 값의 변경 내용에 응답할 수 있습니다.

7. 디자인 뷰로 돌아가서 **다시 설정** 단추를 두 번 클릭 하거나 다시 설정 단추를 두 번 클릭 하 여 `btnReset_Click` 이벤트 처리기를 생성 합니다. 그런 다음, 다음 예제와 같이 입력 합니다.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. 클래스 정의 바로 위의 `ProvideToolboxControl` 특성 선언에서 첫 번째 매개 변수 값을 `"MyWinFormsControl.Counter"` 에서 `"General"`로 변경합니다. **도구 상자**에서 컨트롤을 호스트할 항목 그룹의 이름이 설정됩니다.

    다음 예제에서는 `ProvideToolboxControl` 특성 및 조정된 클래스 정의를 보여 줍니다.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>컨트롤 테스트

 **도구 상자** 컨트롤을 테스트 하려면 먼저 개발 환경에서 테스트 한 다음 컴파일된 응용 프로그램에서 테스트 합니다.

#### <a name="to-test-the-control"></a>컨트롤을 테스트하려면

1. **F5** 키를 눌러 **디버깅을 시작**합니다.

    이 명령은 프로젝트를 빌드하고 컨트롤이 설치 된 Visual Studio의 두 번째 실험적 인스턴스를 엽니다.

2. Visual Studio의 실험적 인스턴스에서 **Windows Forms 응용 프로그램** 프로젝트를 만듭니다.

3. **솔루션 탐색기**에서 *Form1.cs* 를 두 번 누르거나 두 번 클릭 하 여 디자이너에서 엽니다 (아직 열려 있지 않은 경우).

4. **도구 상자**에서 `Counter` 컨트롤이 **일반** 섹션에 표시 되어야 합니다.

5. 컨트롤을 `Counter` 폼으로 끈 다음 선택 합니다. `Value`, `Message` 및 속성은 `ShowReset` 에서 상속 되는 속성과 함께 **속성** 창에 표시 됩니다 <xref:System.Windows.Forms.UserControl> .

6. `Message` 속성을 `Count:`으로 설정합니다.

7. 컨트롤을 <xref:System.Windows.Forms.Button> 폼으로 끈 다음 단추의 이름 및 텍스트 속성을로 설정 `Test` 합니다.

8. 단추를 두 번 클릭 하거나 두 번 클릭 하 여 코드 보기에서 *Form1.cs* 을 열고 클릭 처리기를 만듭니다.

9. 클릭 처리기에서를 호출 `counter1.Increment()` 합니다.

10. 생성자 함수에서에 대 한 호출 후을 `InitializeComponent` 입력 한 `counter1``.``Incremented +=` 다음 **tab** 키를 두 번 누릅니다.

    Visual Studio에서는 이벤트에 대 한 폼 수준 처리기를 생성 `counter1.Incremented` 합니다.

11. `Throw`이벤트 처리기에서 문을 강조 표시 하 `mbox` 고를 입력 한 다음 **tab** 키를 두 번 눌러 mbox 코드 조각에서 메시지 상자를 생성 합니다.

12. 다음 줄에서 다음 블록을 추가 `if` / `else` 하 여 **다시 설정** 단추의 표시 여부를 설정 합니다.

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. **F5**키를 누릅니다.

    양식이 열립니다. `Counter`컨트롤은 다음 텍스트를 표시 합니다.

    **개수: 0**

14. **테스트**를 선택합니다.

    카운터가 증가 하 고 Visual Studio는 메시지 상자를 표시 합니다.

15. 메시지 상자를 닫습니다.

    **다시 설정** 단추가 사라집니다.

16. 매번 메시지 상자를 닫을 때까지 카운터가 **5** 에 도달할 때까지 **테스트** 를 선택 합니다.

    **다시 설정 단추가 다시** 나타납니다.

17. **재설정**을 선택합니다.

    카운터가 **0**으로 다시 설정 됩니다.

## <a name="next-steps"></a>다음 단계

**도구 상자** 컨트롤을 빌드할 때 Visual Studio는 프로젝트의 \bin\debug\ 폴더에 *ProjectName .vsix* 라는 파일을 만듭니다. 네트워크 또는 웹 사이트에 *.vsix* 파일을 업로드 하 여 컨트롤을 배포할 수 있습니다. 사용자가 *.vsix* 파일을 열면 컨트롤이 설치 되 고 사용자 컴퓨터의 Visual Studio **도구 상자** 에 추가 됩니다. 또는 사용자가 **도구** *.vsix* [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  >  **확장 및 업데이트** 대화 상자에서 검색 하 여 찾을 수 있도록 Visual Studio Marketplace에 .vsix 파일을 업로드할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)
- [WPF 도구 상자 컨트롤 만들기](../extensibility/creating-a-wpf-toolbox-control.md)
- [Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)
- [Windows Forms 컨트롤 개발 기본 사항](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
