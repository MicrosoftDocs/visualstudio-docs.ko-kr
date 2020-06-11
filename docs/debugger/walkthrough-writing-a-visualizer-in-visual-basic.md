---
title: Visual Basic에서 시각화 도우미 작성 | Microsoft Docs
ms.custom: seodec18
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25720f31c721cae44ed5425631a86b3a41bf475e
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180534"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>연습: Visual Basic에서 시각화 도우미 작성

이 연습에서는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]을 사용하여 간단한 시각화 도우미를 작성하는 방법을 보여 줍니다. 이 연습에서 만들 시각화 도우미는 Windows Forms 메시지 상자를 사용하여 문자열의 내용을 표시합니다. 이 간단한 문자열 시각화 도우미는 프로젝트에 더 유용하게 사용할 수 있는 다른 형식에 대한 시각화 도우미를 만드는 방법을 보여 주는 기본 예제입니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 실제 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴로 이동하여 **가져오기 및 내보내기**를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

시각화 도우미 코드는 디버거에서 읽을 DLL에 배치해야 합니다. 따라서 가장 먼저 할 일은 DLL의 클래스 라이브러리 프로젝트를 만드는 것입니다.

## <a name="create-and-prepare-a-class-library-project"></a>클래스 라이브러리 프로젝트 만들기 및 준비

### <a name="to-create-a-class-library-project"></a>클래스 라이브러리 프로젝트를 만들려면

1. 새 클래스 라이브러리 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl + Q**를 입력하여 검색 상자를 열고 **visual basic**을 입력한 다음 **템플릿**, **새 클래스 라이브러리 만들기(.NET Framework)** 를 차례로 선택합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual Basic** 아래의 **.NET Standard**를 선택한 다음, 가운데 창에서 **클래스 라이브러리(.NET Standard)** 를 선택합니다.
    ::: moniker-end

2. 클래스 라이브러리의 적절한 이름(예: `MyFirstVisualizer`)을 입력한 다음 **만들기** 또는 **확인**을 클릭합니다.

   클래스 라이브러리를 만든 후에는 Microsoft.VisualStudio.DebuggerVisualizers.DLL에 대한 참조를 추가하여 여기에서 정의한 클래스를 사용할 수 있도록 해야 합니다. 그 전에 프로젝트에 의미 있는 이름을 부여해야 합니다.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1.vb의 이름을 바꾸고 Microsoft.VisualStudio.DebuggerVisualizers를 추가하려면

1. **솔루션 탐색기**에서 **Class1.vb**를 마우스 오른쪽 단추로 클릭하고, 바로 가기 메뉴에서 **이름 바꾸기**를 클릭합니다.

2. 이름을 Class1.vb에서 DebuggerSide.vb 같은 의미 있는 이름으로 변경합니다.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 새 파일 이름과 일치하도록 DebuggerSide.vb의 클래스 선언이 자동으로 변경됩니다.

3. **솔루션 탐색기**에서 **내 첫 번째 시각화 도우미**를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **참조 추가**를 클릭합니다.

4. **참조 추가** 대화 상자의 **찾아보기** 탭에서 **찾아보기**를 선택하고 Microsoft.VisualStudio.DebuggerVisualizers.DLL을 찾습니다.

    Visual Studio 설치 디렉터리의 *\<Visual Studio Install Directory>\Common7\IDE\PublicAssemblies* 하위 디렉터리에서 DLL을 찾을 수 있습니다.

5. **확인**을 클릭합니다.

6. DebuggerSide.vb에서 다음 문을 `Imports` 문에 추가합니다.

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>디버거 쪽 코드 추가
 이제 디버거 쪽 코드를 만들 준비가 되었습니다. 이는 시각화하려는 정보를 표시하기 위해 디버거 내에서 실행되는 코드입니다. 먼저 `DebuggerSide` 개체의 선언을 변경하여 `DialogDebuggerVisualizer` 기본 클래스에서 상속하도록 해야 합니다.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer에서 상속하려면

1. DebuggerSide.vb에서 다음 코드 줄로 이동합니다.

   ```vb
   Public Class DebuggerSide
   ```

2. 코드를 다음과 같이 편집합니다.

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer`에는 재정의해야 할 한 가지 추상 메서드 `Show`가 있습니다.

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer.Show 메서드를 재정의하려면

- `public class DebuggerSide`에서 다음 메서드를 추가합니다.

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  `Show` 메서드에는 시각화 도우미 대화 상자나 기타 사용자 인터페이스를 실제로 만들고 디버거에서 시각화 도우미로 전달된 정보를 표시하는 코드가 들어 있습니다. 대화 상자를 만들고 정보를 표시하는 코드를 추가해야 합니다. 이 연습에서는 Windows Forms 메시지 상자를 사용하여 이 작업을 수행합니다. 먼저 `Imports`에 대한 참조와 <xref:System.Windows.Forms> 문을 추가해야 합니다.

### <a name="to-add-systemwindowsforms"></a>System.Windows.Forms을 추가하려면

1. **솔루션 탐색기**에서 **참조**를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **참조 추가**를 클릭합니다.

2. **참조 추가** 대화 상자의 **찾아보기** 탭에서 **찾아보기**를 선택하고, System.Windows.Forms.DLL을 찾습니다.

    *C:\Windows\Microsoft.NET\Framework\v4.0.30319*에서 이 DLL을 찾을 수 있습니다.

3. **확인**을 클릭합니다.

4. DebuggerSide.cs에서 다음 문을 `Imports` 문에 추가합니다.

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>시각화 도우미의 사용자 인터페이스 만들기
 이제 시각화 도우미의 사용자 인터페이스를 만들고 표시하는 코드를 추가합니다. 이 연습에서는 처음으로 시각화 도우미를 만드는 것이므로 사용자 인터페이스를 간단하게 유지하고 메시지 상자를 사용합니다.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>시각화 도우미 출력을 대화 상자에 표시하려면

1. `Show` 메서드에 다음 코드 줄을 추가합니다.

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     이 예제 코드에는 오류 처리 기능이 포함되어 있지 않습니다. 실제 시각화 도우미나 기타 유형의 애플리케이션을 만들 때는 오류 처리 기능을 포함해야 합니다.

2. **빌드** 메뉴에서 **MyFirstVisualizer 빌드**를 클릭합니다. 프로젝트가 성공적으로 빌드되어야 합니다. 빌드 오류가 발생하면 계속 진행하기 전에 이를 수정합니다.

## <a name="add-the-necessary-attribute"></a>필수 특성 추가
 이제 디버거(debugger) 쪽 코드를 모두 작성했습니다. 그러나 여기에서 한 단계를 추가로 수행해야 합니다. 시각화 도우미를 구성하는 클래스 컬렉션을 디버기 쪽에 알리는 특성이 필요합니다.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>디버기 측 코드에 대해 시각화할 형식을 추가하려면

디버거 쪽 코드에서 <xref:System.Diagnostics.DebuggerVisualizerAttribute> 특성을 사용하여 디버기에 대해 시각화할 형식(개체 소스)을 지정합니다. `Target` 속성은 시각화할 형식을 설정합니다.

1. DebuggerSide.vb의 `Imports` 문과 `namespace MyFirstVisualizer` 문 사이에 다음 특성 코드를 추가합니다.

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2. **빌드** 메뉴에서 **MyFirstVisualizer 빌드**를 클릭합니다. 프로젝트가 성공적으로 빌드되어야 합니다. 빌드 오류가 발생하면 계속 진행하기 전에 이를 수정합니다.

## <a name="create-a-test-harness"></a>테스트 도구 만들기
 이제 첫 번째 시각화 도우미가 완성되었습니다. 각 단계를 올바르게 수행했으면 시각화 도우미를 빌드하고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 설치할 수 있을 것입니다. 그러나 시각화 도우미를 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 설치하기 전에 이를 테스트하여 올바르게 실행되는지 확인해야 합니다. 이제 시각화 도우미를 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 설치하지 않고 실행하는 테스트 환경을 만듭니다.

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>시각화 도우미를 표시하기 위한 테스트 메서드를 추가하려면

1. `public DebuggerSide` 클래스에 다음 메서드를 추가합니다.

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. **빌드** 메뉴에서 **MyFirstVisualizer 빌드**를 클릭합니다. 프로젝트가 성공적으로 빌드되어야 합니다. 빌드 오류가 발생하면 계속 진행하기 전에 이를 수정합니다.

   이제 시각화 도우미 DLL을 호출하기 위한 실행 파일 프로젝트를 만들어야 합니다. 작업을 간소화하기 위해 콘솔 애플리케이션 프로젝트를 사용합니다.

### <a name="to-add-a-console-application-project-to-the-solution"></a>솔루션에 콘솔 애플리케이션 프로젝트를 추가하려면

1. 솔루션 탐색기에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가**를 선택한 후 **새 프로젝트**를 선택합니다.

    ::: moniker range=">=vs-2019"
    검색 상자에 **visual basic**을 입력하고 **템플릿**을 선택한 다음 **새 콘솔 앱 만들기(.NET Framework)** 를 선택합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual Basic** 아래에 **Windows 데스크톱**을 선택한 다음, 가운데 창에서 **콘솔 앱(.NET Framework)** 을 선택합니다.
    ::: moniker-end

2. 클래스 라이브러리의 적절한 이름(예: `MyTestConsole`)을 입력한 다음 **만들기** 또는 **확인**을 클릭합니다.

   이제 MyTestConsole에서 MyFirstVisualizer를 호출하는 데 필요한 참조를 추가해야 합니다.

### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole에 필요한 참조를 추가하려면

1. **솔루션 탐색기**에서 **MyTestConsole**을 마우스 오른쪽 단추로 클릭하고, 바로 가기 메뉴에서 **참조 추가**를 클릭합니다.

2. **참조 추가** 대화 상자의 **찾아보기** 탭에서 Microsoft.VisualStudio.DebuggerVisualizers를 클릭합니다.

3. **확인**을 클릭합니다.

4. **MyTestConsole**을 마우스 오른쪽 단추로 클릭한 다음, **참조 추가**를 다시 클릭합니다.

5. **참조 추가** 대화 상자에서 **프로젝트** 탭을 클릭한 다음, MyFirstVisualizer를 선택합니다.

6. **확인**을 클릭합니다.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>테스트 도구 끝내기 및 시각화 도우미 테스트
 이제 테스트 환경을 끝내기 위한 코드를 추가합니다.

### <a name="to-add-code-to-mytestconsole"></a>MyTestConsole에 코드를 추가하려면

1. **솔루션 탐색기**에서 **Program.vb**를 마우스 오른쪽 단추로 클릭하고, 바로 가기 메뉴에서 **이름 바꾸기**를 클릭합니다.

2. 이름을 Module1.vb에서 **TestConsole.vb** 같은 적절한 이름으로 변경합니다.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서는 새 파일 이름과 일치하도록 TestConsole.vb의 클래스 선언이 자동으로 변경된다는 점에 유의해야 합니다.

3. TestConsole. vb에서 다음 `Imports` 문을 추가합니다.

   ```vb
   Imports MyFirstVisualizer
   ```

4. `Main` 메서드에 다음 코드를 추가합니다.

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   이제 첫 번째 시각화 도우미를 테스트할 준비가 되었습니다.

### <a name="to-test-the-visualizer"></a>시각화 도우미를 테스트하려면

1. **솔루션 탐색기**에서 **MyTestConsole**를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **시작 프로젝트로 설정**을 선택합니다.

2. **디버그** 메뉴에서 **시작**을 클릭합니다.

    콘솔 애플리케이션이 시작됩니다. 시각화 도우미가 나타나고 "Hello, World."라는 문자열이 표시됩니다.

   이로써 첫 번째 시각화 도우미를 빌드하고 테스트했습니다.

   시각화 도우미를 테스트 환경에서 호출하는 대신 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 사용하려면 이를 설치해야 합니다. 자세한 내용은 [방법: 시각화 도우미 설치](../debugger/how-to-install-a-visualizer.md)를 참조하세요.

## <a name="see-also"></a>참조

- [시각화 도우미 아키텍처](../debugger/visualizer-architecture.md)
- [방법: 시각화 도우미 설치](../debugger/how-to-install-a-visualizer.md)
- [Create Custom Visualizers of Data](../debugger/create-custom-visualizers-of-data.md)(데이터의 사용자 지정 시각화 도우미 만들기)