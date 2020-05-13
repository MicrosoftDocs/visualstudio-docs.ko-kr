---
title: Windows 양식 도구 상자 컨트롤 만들기 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739587"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Windows 양식 도구 상자 컨트롤 만들기

시각적 스튜디오 확장성 도구(VS SDK)에 포함된 Windows Forms 도구 상자 제어 항목 템플릿을 사용하면 확장프로그램을 설치할 때 자동으로 추가되는 **도구 상자** 컨트롤을 만들 수 있습니다. 이 연습에서는 템플릿을 사용하여 다른 사용자에게 배포할 수 있는 간단한 카운터 컨트롤을 만드는 방법을 보여 주며 이 연습에서는

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-the-toolbox-control"></a>도구 상자 컨트롤 만들기

Windows Forms 도구 상자 컨트롤 템플릿은 정의되지 않은 사용자 컨트롤을 만들고 **도구를 도구 상자에**추가하는 데 필요한 모든 기능을 제공합니다.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Windows 양식 도구 상자 컨트롤을 사용하여 확장 만들기

1. 라는 VSIX 프로젝트를 `MyWinFormsControl`만듭니다. "vsix"를 검색하여 **새 프로젝트** 대화 상자에서 VSIX 프로젝트 템플릿을 찾을 수 있습니다.

2. 프로젝트가 열리면 **.라는 Windows Forms 도구** 상자 `Counter`컨트롤 항목 템플릿을 추가합니다. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 새 **항목 추가** 대화 상자에서 **시각적 C#** > **확장성으로** 이동하여 **Windows 양식 도구 상자 컨트롤을** 선택합니다.

3. 이렇게 하면 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 사용자 컨트롤, **도구 상자에**컨트롤을 배치할 수 있는 사용자 컨트롤 및 배포를 위한 VSIX 매니페스트에 **Microsoft.VisualStudio.ToolboxControl** 자산 항목이 추가됩니다.

### <a name="build-a-user-interface-for-the-control"></a>컨트롤을 위한 사용자 인터페이스 빌드

컨트롤에는 `Counter` 현재 개수를 <xref:System.Windows.Forms.Label> 표시하는 a와 개수를 <xref:System.Windows.Forms.Button> 0으로 재설정하는 두 개의 하위 컨트롤이 필요합니다. 호출자는 프로그래밍 방식으로 카운터를 증분하므로 다른 자식 컨트롤이 필요하지 않습니다.

#### <a name="to-build-the-user-interface"></a>사용자 인터페이스를 작성하려면

1. **솔루션 탐색기에서** *Counter.cs* 두 번 클릭하여 디자이너에서 엽니다.

2. **여기를 클릭하십시오!** Windows Forms 도구 상자 컨트롤 항목 템플릿을 추가할 때 기본적으로 포함 되는 단추입니다.

3. 도구 **상자에서**컨트롤을 `Label` 드래그한 `Button` 다음 컨트롤 아래를 디자인 표면으로 드래그합니다.

4. 전체 사용자 컨트롤의 크기를 150, 50픽셀로 조정하고 단추 컨트롤의 크기를 50, 20픽셀로 조정합니다.

5. **속성** 창에서 설계 표면의 컨트롤에 대한 다음 값을 설정합니다.

    |제어|속성|값|
    |-------------|--------------|-----------|
    |`Label1`|**텍스트**|""|
    |`Button1`|**이름**|btnReset|
    |`Button1`|**텍스트**|다시 설정|

### <a name="code-the-user-control"></a>사용자 컨트롤 코드

컨트롤은 `Counter` 카운터를 증분하는 방법, 카운터가 증분될 때마다 발생하는 이벤트, **리셋** 단추 및 현재 개수, 표시 텍스트를 저장하는 세 가지 속성 및 **재설정** 단추를 표시하거나 숨길지 여부를 노출합니다. `ProvideToolboxControl` 특성은 **도구 상자** 에서 `Counter` 컨트롤이 나타나는 위치를 결정합니다.

#### <a name="to-code-the-user-control"></a>사용자 컨트롤을 코딩하려면

1. 코드를 클릭하여 코드 창에서 로드 이벤트 처리기를 엽니다.

2. 이벤트 처리기 메서드 위에 컨트롤 클래스에서 카운터 값을 저장 하는 정수 및 다음 예제와 같이 표시 텍스트를 저장 하는 문자열을 만듭니다.

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

    발신자는 이러한 속성에 액세스하여 카운터의 표시 텍스트를 얻고 설정하고 **재설정** 버튼을 표시하거나 숨길 수 있습니다. 호출자는 read 전용 `Value` 속성의 현재 값을 가져올 수 있지만 값을 직접 설정할 수는 없습니다.

4. 컨트롤에 대 한 `Load` 이벤트에 다음 코드를 넣습니다.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    <xref:System.Windows.Forms.UserControl.Load> 이벤트에서 **Label** 텍스트를 설정하면 값이 적용되기 전에 대상 속성을 로드할 수 있습니다. 생성자에서 **레이블** 텍스트를 설정하면 **레이블이**비어 있습니다.

5. 카운터를 증분하는 다음 공용 메서드를 만듭니다.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. 컨트롤 클래스에 `Incremented` 이벤트에 대 한 선언을 추가 합니다.

    ```csharp
    public event EventHandler Incremented;
    ```

    호출자는 이 이벤트에 처리기를 추가하여 카운터 값의 변경 사항에 응답할 수 있습니다.

7. 디자인 보기로 돌아가서 **재설정** 단추를 두 `btnReset_Click` 번 클릭하여 이벤트 처리기를 생성한 다음 다음 예제와 같이 채웁니다.

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

 **도구 상자** 컨트롤을 테스트하려면 먼저 개발 환경에서 테스트한 다음 컴파일된 응용 프로그램에서 테스트합니다.

#### <a name="to-test-the-control"></a>컨트롤을 테스트하려면

1. **F5를** 눌러 **디버깅을 시작합니다.**

    이 명령은 프로젝트를 빌드하고 컨트롤이 설치된 Visual Studio의 두 번째 실험 인스턴스를 엽니다.

2. Visual Studio의 실험인스턴스에서 **Windows Forms 응용 프로그램** 프로젝트를 만듭니다.

3. **솔루션 탐색기에서** *Form1.cs* 두 번 클릭하여 아직 열려 있지 않은 경우 디자이너에서 열 수 있습니다.

4. 도구 **상자에서**컨트롤이 `Counter` **일반** 섹션에 표시되어야 합니다.

5. 컨트롤을 `Counter` 양식으로 드래그한 다음 선택합니다. 및 `Value` `Message` `ShowReset` 속성은 에서 상속되는 속성과 함께 **속성** 창에 <xref:System.Windows.Forms.UserControl>표시됩니다.

6. `Message` 속성을 `Count:`로 설정합니다.

7. 컨트롤을 <xref:System.Windows.Forms.Button> 양식으로 드래그한 다음 단추의 이름과 텍스트 속성을 `Test`로 설정합니다.

8. 단추를 두 번 클릭하여 코드 보기에서 *Form1.cs* 열고 클릭 처리기를 만듭니다.

9. 클릭 처리기에서 `counter1.Increment()`를 호출합니다.

10. 생성자 함수에서 `InitializeComponent`호출 후 를 `counter1``.``Incremented +=` 입력한 다음 **Tab을** 두 번 누릅니다.

    Visual Studio는 이벤트에 대한 양식 `counter1.Incremented` 수준 처리기를 생성합니다.

11. 이벤트 `Throw` 처리기에서 문을 강조 `mbox`표시하고 입력한 다음 **Tab을** 두 번 눌러 mbox 코드 조각에서 메시지 상자를 생성합니다.

12. 다음 줄에 다음 `if` / `else` 블록을 추가하여 **재설정** 단추의 가시성을 설정합니다.

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. **F5**키를 누릅니다.

    양식이 열립니다. 컨트롤에 `Counter` 다음 텍스트가 표시됩니다.

    **개수: 0**

14. **테스트**를 클릭합니다.

    카운터 증분 및 Visual Studio에는 메시지 상자가 표시됩니다.

15. 메시지 상자를 닫습니다.

    **리셋** 버튼이 사라집니다.

16. 카운터가 5에 **도달할** 때까지 **테스트를** 클릭하여 매번 메시지 상자를 닫습니다.

    **재설정** 버튼이 다시 나타납니다.

17. **재설정**을 클릭합니다.

    카운터가 **0으로**재설정됩니다.

## <a name="next-steps"></a>다음 단계

**도구 상자** 컨트롤을 빌드할 때 Visual Studio는 프로젝트의 \bin\debug\ 폴더에 *ProjectName.vsix라는* 파일을 만듭니다. *.vsix* 파일을 네트워크 또는 웹 사이트에 업로드하여 컨트롤을 배포할 수 있습니다. 사용자가 *.vsix* 파일을 열면 컨트롤이 설치되고 사용자 컴퓨터의 Visual Studio **도구 상자에** 추가됩니다. **Tools** > 또는 *.vsix* 파일을 Visual Studio [마켓플레이스에](https://marketplace.visualstudio.com/) 업로드하여 도구 확장**및 업데이트** 대화 상자를 탐색하여 찾을 수 있습니다.

## <a name="see-also"></a>참조

- [비주얼 스튜디오의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)
- [WPF 도구 상자 컨트롤 만들기](../extensibility/creating-a-wpf-toolbox-control.md)
- [비주얼 스튜디오의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)
- [Windows Forms 제어 개발 기본 사항](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
