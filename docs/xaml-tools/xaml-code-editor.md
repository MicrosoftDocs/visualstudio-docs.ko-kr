---
title: XAML 코드 편집기
description: Visual Studio에서 XAML 코드 편집기 둘러보기
ms.date: 06/16/2020
ms.topic: overview
monikerRange: vs-2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6421fd0139b04262ac5f1e835f010c1372c034ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329182"
---
# <a name="xaml-code-editor"></a>XAML 코드 편집기

[Visual Studio IDE](../get-started/visual-studio-ide.md)의 XAML 코드 편집기에는 Windows 플랫폼용과 [Xamarin.Forms](/xamarin/xamarin-forms/user-interface/text/editor/)용 WPF 및 UWP 앱을 만드는 데 필요한 모든 도구를 포함합니다. 이 문서에서는 XAML 기반 앱을 개발할 때 코드 편집기에서 수행하는 역할과 Visual Studio 2019의 XAML 코드 편집기에 고유한 기능을 간략하게 설명합니다.

먼저 개방형 WPF 프로젝트를 포함한 IDE(통합 개발 환경)를 살펴보겠습니다. 다음 이미지는 XAML 코드 편집기와 함께 사용하는 몇 가지 주요 IDE 도구를 보여 줍니다.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="XAML의 개방형 WPF 프로젝트를 포함한 Visual Studio 2019 IDE" lightbox="media/xaml-code-editor-overview-lrg.png":::

이미지의 왼쪽 아래부터 시계 방향으로 다음과 같은 주요 IDE 도구가 있습니다.

- **[XAML 코드 편집기](#xaml-code-editor-ui)** 창은 이 문서의 제목이자 코드를 작성하고 편집할 수 있는 곳입니다.&mdash;&mdash;
- **[XAML 디자이너](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** 창에서는 UI를 설계합니다.
- **[도구 상자](../ide/reference/toolbox.md)** 는 도킹 가능한 창으로, UI에 컨트롤을 추가합니다.
- **[디버그](../debugger/debugger-feature-tour.md)** 버튼을 사용하여 코드를 실행하고 디버그합니다. <br>(또한 [XAML 핫 다시 로드](xaml-hot-reload.md)를 사용하여 디버그하는 도중 실시간으로 코드를 편집할 수 있습니다.)
- **[솔루션 탐색기](../ide/solutions-and-projects-in-visual-studio.md)** 창에서 파일, 프로젝트 및 솔루션을 관리합니다.
- **[속성](../ide/reference/properties-window.md)** 창에서 UI의 모양 및 작동 방식을 변경합니다.

이어서 XAML 코드 편집기에 대해 자세히 살펴보겠습니다.

## <a name="xaml-code-editor-ui"></a>XAML 코드 편집기 UI

XAML 앱에 대한 코드 편집기 창은 표준 IDE에도 표시되는 UI(사용자 인터페이스) 요소를 공유하지만 XAML 앱을 더욱 쉽게 개발할 수 있도록 하는 몇 가지 고유한 기능도 포함합니다.

다음은 XAML 코드 편집기 창의 모습입니다.

![Visual Studio의 XAML 코드 편집기 창](media/xaml-code-editor-window.png "Visual Studio 2019의 XAML 코드 편집기 창 스크린샷")

다음으로 코드 편집기의 각 UI 요소에 대한 함수를 살펴보겠습니다.

### <a name="first-row"></a>첫 번째 행

왼쪽에 있는 XAML 코드 창 상단의 첫 번째 행에는 **디자인** 탭, **창 바꾸기** 단추, **XAML** 탭, **XAML 팝아웃** 단추가 있습니다.

![Visual Studio의 XAML 코드 편집기 창 상단 2개 행 중 첫 번째, 첫 번째 행의 왼쪽이 강조되어 있음](media/xaml-code-editor-top-row-left.png "Visual Studio 2019의 XAML 코드 편집기 창 상단 2개 행 중 첫 번째의 스크린샷, 왼쪽의 UI 요소가 강조되어 있음")

작동 방법은 다음과 같습니다.

- **디자인** 탭은 XAML 코드 편집기에서 XAML 디자이너로 포커스를 변경합니다.
- **창 바꾸기** 단추는 IDE에서 XAML 디자이너와 XAML 코드 편집기의 위치를 반대로 바꿉니다.
- **XAML** 탭은 포커스를 XAML 코드 편집기로 다시 변경합니다.
- **XAML 팝아웃** 단추를 클릭하면 IDE 외부에 있는 별도의 XAML 코드 편집기 창이 생성됩니다.

이어서 오른쪽에는 **세로 분할** 단추, **가로 분할** 단추, **창 축소** 단추가 있습니다.

![Visual Studio의 XAML 코드 편집기 창 상단의 2개 행, 첫 번째 행의 오른쪽이 강조되어 있음](media/xaml-code-editor-top-row-right.png "Visual Studio 2019의 XAML 코드 편집기 창 상단 2개 행 중 첫 번째의 스크린샷, 오른쪽의 UI 요소가 강조되어 있음")

작동 방법은 다음과 같습니다.

- **세로 분할** 단추는 IDE에서 XAML 디자이너와 XAML 코드 편집기의 위치를 가로 맞춤에서 세로 맞춤으로 변경합니다.
- **가로 분할** 단추는 IDE에서 XAML 디자이너와 XAML 코드 편집기의 위치를 세로 맞춤에서 가로 맞춤으로 변경합니다.
- **창 축소** 단추를 사용하면 코드 편집기나 디자이너인지에 관계없이 하단 창에 있는 항목을 축소할 수 있습니다. (하단 창을 복원하려면 동일한 단추를 다시 선택합니다. 이제 이 단추의 이름은 **창 확장**으로 지정됩니다.)

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>두 번째 행

XAML 코드 창의 상단 두 번째 행에는 두 개의 창 드롭다운 목록이 있습니다. 하지만 해당 UI 요소의 도구 설명을 보면 “요소: 창”과 “멤버: 창”으로 식별됩니다.

![Visual Studio의 XAML 코드 편집기 창 상단 2개 행 중 두 번째, 두 개의 창 드롭다운 목록이 모두 표시되어 있음](media/xaml-code-editor-top-row-windows.png "Visual Studio 2019의 XAML 코드 편집기 창 상단 2개 행 중 두 번째의 스크린샷, 두 개의 창 드롭다운 목록이 모두 표시되어 있음")

창 드롭다운 목록은 다음과 같은 다양한 기능을 포함합니다.

- **요소: 창**은 왼쪽에 위치하며, 형제 또는 부모 요소를 보고 탐색할 수 있습니다.

  특히 코드의 태그 구조를 표시하는 개요와 유사한 뷰를 표시합니다. 목록에서 선택하면 코드 편집기의 포커스가 선택한 요소를 포함하는 코드 줄에 맞춰집니다.

    ![Visual Studio의 요소: 창 드롭다운 목록](media/xaml-element-window-dropdown.png "Visual Studio 2019의 요소: 창 드롭다운 목록 스크린샷")

- **멤버: 창**은 오른쪽에 위치하며, 특성 또는 자식 요소를 보고 탐색할 수 있습니다.

    특히 코드의 속성 목록이 표시됩니다. 목록에서를 선택하면 코드 편집기의 포커스가 선택한 속성을 포함하는 코드 줄에 맞춰집니다.

    ![멤버: 창 드롭다운 목록](media/xaml-member-window-dropdown.png "Visual Studio 2019의 멤버: 창 드롭다운 목록 스크린샷")

### <a name="middle-pane-code-editor"></a>중간 창, 코드 편집기

중간 창은 XAML 코드 편집기의 “코드” 부분입니다. 여기에는 [IDE 코드 편집기](../get-started/tutorial-editor.md)에서 찾을 수 있는 기능이 대체로 포함되어 있습니다. XAML 코드를 개발하는 데 도움이 될 수 있는 몇 가지 범용 IDE 기능을 살펴보겠습니다. 또한 IDE의 고유한 XAML 기능도 살펴보겠습니다.

![Visual Studio의 XAML 코드 편집기, 중간 창만](media/xaml-code-editor-middle.png "Visual Studio 2019의 XAML 코드 편집기의 스크린샷, 중간 창만")

#### <a name="quick-actions"></a>빠른 작업

[빠른 작업](../ide/quick-actions.md)을 사용하면 단일 작업으로 쉽게 코드를 리팩터링하거나, 생성하거나, 수정할 수 있습니다.

예를 들어 빠른 작업을 사용하여 수행할 수 있는 유용한 작업 중 하나는 **MainWindow.xaml.cs** 탭의 C# 코드에서 **불필요한 Using을 제거**하는 것입니다.

방법은 다음과 같습니다.

1. Using 문을 마우스로 가리키고 전구 아이콘을 선택한 다음 드롭다운 목록에서 **불필요한 Using 제거**를 선택합니다.

    ![IDE 편집기의 빠른 작업 메뉴에 있는 “불필요한 Using 제거” 옵션](media/xaml-code-editor-remove-usings.png "IDE 편집기의 빠른 작업 메뉴에 있는 “불필요한 Using 제거” 옵션 스크린샷")

1. **문서**, **프로젝트** 또는 **솔루션**에서 모든 발생을 수정할지 여부를 선택합니다.
1. **미리 보기** 대화 상자를 보고 **적용**을 선택합니다.

메뉴 모음에서 이 기능에 액세스할 수도 있습니다. 이렇게 하려면 **편집** > **IntelliSense** > **Using 제거 및 정렬**을 선택합니다.

Using 설정에 대한 자세한 내용은 [Using 정렬](../ide/reference/sort-usings.md) 페이지를 참조하세요. IntelliSense에 대한 자세한 내용은 [Visual Studio의 IntelliSense](../ide/using-intellisense.md) 페이지를 참조하세요. 개발자가 빠른 작업을 사용하는 일반적인 방법 중 일부에 대한 자세한 내용은 [일반적인 빠른 작업](../ide/common-quick-actions.md) 페이지를 참조하세요.

#### <a name="change-tracking"></a>변경 내용 추적

왼쪽 여백의 색을 사용하여 파일에서 수행한 변경을 계속 추적할 수 있습니다. 색이 수행하는 작업과 다음과 같이 연관됩니다.

- 파일이 열린 후 변경되었으나 저장되지 않은 내용은 왼쪽 여백(선택 여백)에 **노란색** 막대로 나타냅니다.

    ![노란색 막대가 있는 코드 편집기 편집](media/code-editor-edit-yellow.png "선택 영역 여백에서 변경 사항이 노란색 막대로 표시된 코드 편집기의 스크린샷.")

- 변경 내용을 저장하면(파일을 닫기 전) 막대가 **녹색**으로 바뀝니다.

    ![녹색 막대가 있는 코드 편집기 편집](media/code-editor-edit-green.png "선택 영역 여백에서 변경 사항이 녹색 막대로 표시된 코드 편집기의 스크린샷.")

이 기능을 해제 및 설정하려면 **텍스트 편집기** 설정(**도구** > **옵션** > **텍스트 편집기**)에서 **변경 내용 추적** 옵션을 변경합니다.

&mdash;코드 문자에 표시되는 물결선(오류 표시선)을 포함한&mdash; 변경 내용 추적에 대한 자세한 내용은 [Visual Studio 코드 편집기 기능](../ide/writing-code-in-the-code-and-text-editor.md) 페이지의 **[편집기 기능](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** 섹션을 참조하세요.

#### <a name="right-click-context-menu"></a>오른쪽 클릭 바로 가기 메뉴

XAML 코드 편집기에서 코드를 편집하는 경우 오른쪽 클릭 바로 가기 메뉴를 사용하여 액세스할 수 있는 여러 기능이 있습니다. 대부분의 해당 기능은 Visual Studio IDE에서 전체적으로 사용할 수 있지만 일부 기능은 디자인 창과 함께 코드 편집기를 사용하는 경우에만 적용됩니다.

![Visual Studio의 XAML 코드 편집기에 있는 오른쪽 클릭 바로 가기 메뉴](media/xaml-code-editor-right-click-menu.png "Visual Studio 2019의 XAML 코드 편집기에 있는 오른쪽 클릭 바로 가기 메뉴 스크린샷")

각 기능에서 수행하는 작업과 유용한 방법은 다음과 같습니다.

- **코드 뷰** - 디자인 창 및 XAML 코드 편집기를 포함하는 기본 뷰 옆의 탭으로 프로그래밍 언어 코드 창이 열립니다.
- **뷰 디자이너** - 디자인 창과 XAML 코드 편집기를 포함하는 기본 뷰가 열립니다. (이미 기본 뷰에 있는 경우에는 아무 작업도 수행하지 않습니다.)
- **빠른 작업 및 리팩터링** - 단일 작업으로 리팩터링, 생성 또는 코드를 수정합니다. 코드를 가리키면 빠른 작업이나 리팩터링을 사용할 수 있을 때 전구 아이콘이 표시됩니다. <br>참고 항목: [빠른 작업](../ide/quick-actions.md) 및 [코드 리팩터링](../ide/refactoring-in-visual-studio.md).
- **이름 바꾸기...** - 네임스페이스의 이름만 바꿉니다. 이름을 바꿀 네임스페이스가 없는 경우 “네임스페이스 접두사만 이름을 바꿀 수 있습니다”라는 오류 메시지가 표시됩니다.
- **네임스페이스 제거 및 정렬** - 사용하지 않는 네임스페이스를 제거한 다음 남은 네임스페이스를 정렬합니다.
- **정의 피킹** - 편집기에서 현재 위치를 벗어나지 않고 형식 정의를 미리 봅니다. <br>참고 항목: [정의 피킹](../ide/go-to-and-peek-definition.md#peek-definition) 및 [정의 피킹을 사용하여 코드 보기 및 편집](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **정의로 이동** - 형식 또는 멤버의 소스로 이동하고 새 탭에 결과를 엽니다. <br>참고 항목: [정의로 이동](../ide/go-to-and-peek-definition.md#go-to-definition).
- **코드 감싸기...** - 선택한 코드 블록 주위에 추가되는 코드 감싸기 코드 조각을 사용합니다. <br>참고 항목: [확장 조각 및 코드 감싸기 조각](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **코드 조각 삽입** - 커서 위치에 코드 조각을 삽입합니다.
- **잘라내기** - 자체 설명
- **복사** - 자체 설명
- **붙여넣기** - 자체 설명
- **개요** - 코드의 섹션을 확장 또는 축소합니다. <br>참고 항목: [개요](../ide/outlining.md).
- **소스 제어** - 오픈 소스 리포지토리에 대한 코드 기여 기록을 봅니다.

### <a name="middle-pane-scroll-bar"></a>중간 창, 스크롤 막대

스크롤 막대는 코드를 스크롤할 때보다 더 많은 작업을 수행할 수 있습니다. 이를 사용하여 다른 코드 편집기 창을 열 수도 있습니다. 또한 스크롤 막대를 사용하여 주석을 추가하거나 다른 디스플레이 모드를 사용하여 보다 효율적으로 코드를 만들 수 있습니다.

#### <a name="split-the-code-window"></a>코드 창 분할

코드 편집기의 스크롤 막대 오른쪽 상단에 **분할** 단추가 있습니다. 이를 선택하면 다른 코드 편집기 창을 열 수 있습니다. 이는 서로 독립적으로 작동하므로 다른 위치의 코드를 작업하는 데 사용할 수 있으므로 유용합니다.

![Visual Studio의 XAML 코드 편집기, 중간 창만](media/code-editor-split-window-button.png "Visual Studio 2019의 XAML 코드 편집기의 스크린샷, 중간 창만")

편집기 창을 분할하는 방법에 대한 자세한 내용은 [편집기 창 관리](../ide/how-to-manage-editor-windows.md) 페이지를 참조하세요.

#### <a name="use-annotations-or-map-mode"></a>주석 또는 지도 모드 사용

스크롤 막대의 모양과 포함된 추가 기능을 변경할 수도 있습니다. 예를 들어 코드 변경, 중단점, 책갈피, 오류 및 캐럿 위치와 같은 시각적 신호를 제공하는 ‘주석’을 스크롤 막대에 포함하고자 하는 경우가 많습니다.

스크롤 막대에 코드 줄이 작게 표시되는 ‘지도 모드’를 사용하는 경우도 있습니다. 파일에 코드가 많은 개발자는 지도 모드를 사용할 때 기본 스크롤 막대보다 더욱 효과적으로 코드 줄을 추적할 수 있습니다.

스크롤 막대의 기본 설정을 변경하는 방법에 대한 자세한 내용은 [스크롤 막대 사용자 지정](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) 페이지를 참조하세요.

## <a name="xaml-specific-features"></a>XAML 관련 기능

대부분의 다음 기능은 Visual Studio IDE 전체에서 사용할 수 있지만 XAML 개발자가 쉽게 코딩 작업을 할 수 있도록 몇 가지를 추가했습니다.

### <a name="xaml-code-snippets"></a>XAML 코드 조각

코드 조각은 오른쪽 클릭 바로 가기 메뉴 명령 **코드 조각 삽입** 또는 바로 가기 키의 조합(**Ctrl**+**K**, **Ctrl**+**X**)을 사용하여 코드 파일에 삽입할 수 있는 재사용 가능한 작은 코드 블록입니다. [IntelliSense](../ide/using-intellisense.md)가 XAML 조각 표시를 지원하도록 개선되었습니다. 이 기능은 기본 제공 코드 조각과 수동으로 추가하는 사용자 지정 코드 조각 모두에서 작동합니다. 일부 기본 XAML 코드 조각에는 `#region`, `Column definition`, `Row definition`, `Setter` 및 `Tag`가 있습니다.

![IntelliSense에서 XAML 코드 조각 옵션이 표시된 XAML 코드 편집기](media/xaml-code-snippets.png "IntelliSense에서 XAML 코드 조각 옵션이 표시된 XAML 코드 편집기 스크린샷")

자세한 내용은 [코드 조각](../ide/code-snippets.md) 및 [C# 코드 조각](../ide/visual-csharp-code-snippets.md) 페이지를 참조하세요.

### <a name="xaml-region-support"></a>XAML #region 지원

Visual Studio 2015부터 #region 지원을 WPF 및 UWP XAML 개발자가 사용할 수 있게 되었고, 최근에는 [Xamarin.Forms](/xamarin/xamarin-forms/user-interface/text/editor/) 개발자도 사용할 수 있게 되었습니다. Visual Studio 2019에서는 #region 지원에 대한 기능을 지속적으로 개선하고 있습니다. 예를 들어 [버전 16.4](/visualstudio/releases/2019/release-notes-v16.4/) 이상에서는 `<!` 입력 시작 시 #region 옵션이 표시됩니다.

![IntelliSense에서 #region 옵션이 표시된 XAML 코드 편집기](media/code-editor-xaml-region.png "IntelliSense에서 #region 옵션이 표시된 XAML 코드 편집기 스크린샷")

확장하거나 축소할 코드의 섹션을 그룹화하려는 경우 영역을 사용할 수 있습니다.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

영역에 대한 자세한 내용은 [#region(C# 참조)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) 페이지를 참조하세요. 코드 섹션을 확장하고 축소하는 방법에 대한 자세한 내용은 [개요](../ide/outlining.md) 페이지를 참조하세요.

### <a name="xaml-comments"></a>XAML 주석

개발자는 종종 주석을 사용하여 코드를 문서화하는 것을 선호합니다. 다음과 같은 방법으로 **MainWindow.xaml** 탭에 있는 XAML 코드에 주석을 추가할 수 있습니다.

- 주석 앞에 `<!--` 입력 후 주석 뒤에 `-->` 추가.
- `<!` 입력 후 옵션 목록에서 `!--` 선택.

  ![XAML 코드 편집기 오른쪽 클릭 주석 추가 대화 상자](media/xaml-code-editor-comments.png "XAML 코드 편집기에서 주석을 추가하는 오른쪽 클릭 바로 가기 메뉴 스크린샷")

- 주석을 추가하고자 하는 코드를 선택하고 IDE의 도구 모음에서 **주석** 단추를 선택합니다. 작업을 되돌리려면 **주석 처리 제거** 단추를 선택합니다.

  ![IDE 도구 모음의 주석 단추 및 주석 처리 제거 단추](media/comment-undo-comment-buttons.png "IDE 도구 모음의 주석 단추 및 주석 처리 제거 단추 스크린샷")

- 주석으로 묶을 코드를 선택하고 **Ctrl**+**K**, **Ctrl**+**C**를 누릅니다. 선택한 코드의 주석 처리를 제거하려면 **Ctrl**+**K**, **Ctrl**+**U**를 누릅니다.

**MainWindow.xaml.cs** 탭에 있는 C# 코드에서 주석을 사용하는 방법에 대한 자세한 내용은 [설명서 주석](/dotnet/csharp/language-reference/language-specification/documentation-comments/) 페이지를 참조하세요.

### <a name="xaml-lightbulbs"></a>XAML 전구

XAML 코드에 표시되는 전구 아이콘은 리팩터링, 생성 또는 코드 수정에 사용할 수 있는 [빠른 작업](../ide/quick-actions.md)의 일부분입니다.

다음은 XAML 코딩 환경에서 어떻게 도움이 되는지에 관한 예입니다.

- **불필요한 네임스페이스 제거**. XAML 코드 편집기에서 불필요한 네임스페이스는 흐리게 표시된 텍스트로 표시됩니다. 불필요한 using을 커서로 가리키면 전구가 표시됩니다. 드롭다운 목록에서 **불필요한 네임스페이스 제거** 옵션을 선택하면 제거할 수 있는 미리 보기가 표시됩니다.

  ![XAML 코드 편집기의 빠른 작업 전구에 있는 불필요한 네임스페이스 제거 옵션](media/xaml-code-editor-dimmed-namespaces-preview.png "빠른 작업 전구를 사용하면 표시되는 XAML 코드 편집기의 불필요한 네임스페이스 제거 옵션 스크린샷")

- **네임스페이스 이름 바꾸기**. 네임스페이스를 강조 표시한 후 오른쪽 클릭 바로 가기 메뉴에서 사용할 수 있는 이 기능을 통해 한 번에 여러 설정 인스턴스를 쉽게 변경할 수 있습니다. 메뉴 모음에서 **편집** > **리팩터링** > **이름 바꾸기**를 사용하거나 **Ctrl**+**R**을 누른 다음 **Ctrl**+**R**을 다시 눌러 이 기능을 이용할 수도 있습니다.

  ![XAML 코드 편집기의 오른쪽 클릭 바로 가기 메뉴에 있는 네임스페이스 이름 바꾸기 옵션](media/code-editor-rename-namespace.png "오른쪽 클릭 바로 가기 메뉴를 사용하면 표시되는 XAML 코드 편집기의 네임스페이스 이름 바꾸기 옵션 스크린샷")

  자세한 내용은 [코드 기호 이름 바꾸기 리팩터링](../ide/reference/rename.md) 페이지를 참조하세요.

### <a name="conditional-xaml-for-uwp"></a>UWP용 조건부 XAML

조건부 XAML은 XAML 태그에 [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) 메서드를 사용하는 방법을 제공합니다. 이를 통해 코드 숨김을 사용하지 않고도 API의 존재 여부를 기반으로 태그에서 속성을 설정하고 개체를 인스턴스화할 수 있습니다.

자세한 내용은 [조건부 XAML](/windows/uwp/debug-test-perf/conditional-xaml/) 페이지와 [데스크톱 앱의 호스트 UWP XAML 컨트롤(XAML Islands)](/windows/apps/desktop/modernize/xaml-islands/) 페이지를 참조하세요.

### <a name="xaml-structure-visualizer"></a>XAML 구조체 시각화 도우미

코드 편집기의 구조체 시각화 도우미는 코드에서 일치하는 열린 태그 및 닫힌 태그 요소를 나타내는 세로 파선인 구조체 안내선을 표시합니다. 이를 사용하면 논리 블록의 시작 및 끝 위치를 보다 쉽게 볼 수 있습니다.

자세한 내용은 [코드 탐색](../ide/navigating-code.md) 페이지를 참조하세요.

### <a name="intellicode-for-xaml"></a>XAML용 IntelliCode

코드에 XAML 태그를 추가하는 경우 일반적으로 왼쪽 꺾쇠괄호 `<`로 시작합니다. 이 꺾쇠괄호를 입력하면 인기 있는 여러 XAML 태그를 나열하는 IntelliCode 메뉴가 표시됩니다. 코드에 빠르게 추가하려는 항목을 선택합니다.

IntelliCode 선택은 목록의 맨 위에 표시되고 별표로 표시되기 때문에 인식할 수 있습니다.

![XAML 텍스트 편집기용 IntelliCode 목록](media/xaml-intellicode-selection.png "XAML 텍스트 편집기용 IntelliCode 목록 스크린샷")

자세한 내용은 [IntelliCode 개요](/visualstudio/intellicode/overview/) 페이지를 참조하세요.

### <a name="settings"></a>설정

Visual Studio IDE의 ‘모든’ 설정에 대한 자세한 내용은 [코드 편집기의 기능](../ide/writing-code-in-the-code-and-text-editor.md) 페이지를 참조하세요.

## <a name="xaml-optional-settings"></a>XAML 선택적 설정

[옵션](../ide/reference/options-dialog-box-visual-studio.md) 대화 상자를 사용하여 XAML 코드 편집기에 대한 기본 설정을 변경할 수 있습니다. 설정을 보려면 **도구** > **옵션** > **텍스트 편집기** > **XAML**을 선택합니다.

![XAML 텍스트 편집기용 옵션 목록](media/xaml-tools-options.png "XAML 텍스트 편집기용 옵션 목록 스크린샷")

> [!NOTE]
> 바로 가기 키를 사용하여 옵션 대화 상자에 액세스할 수도 있습니다. 방법은 다음과 같습니다. **Ctrl**+**Q**를 눌러 IDE를 검색하고 **옵션**을 입력한 다음 **Enter**를 누릅니다. 다음으로 **Ctrl**+**E**를 눌러 옵션 대화 상자를 검색하고 **텍스트 편집기**를 입력하고, **Enter**를 누르고 **XAML**을 입력한 다음 **Enter**를 누릅니다.
>  
> 바로 가기 키에 대한 자세한 내용은 [Visual Studio 바로 가기 팁](../ide/productivity-shortcuts.md#code-editor) 페이지를 참조하세요.

### <a name="universal-text-editor-options"></a>범용 텍스트 편집기 옵션

XAML에 대한 [옵션](../ide/reference/options-text-editor-xaml-formatting.md) 대화 상자에서 다음의 첫 3개 항목은 Visual Studio IDE에서 지원하는 모든 프로그래밍 언어에 범용입니다. 해당 옵션 및 사용 방법에 대한 자세한 내용은 다음 표의 연결된 정보를 참조하세요.

|Name  |추가 정보  |
|---------|---------|
|일반  | [옵션 대화 상자: 텍스트 편집기 > 모든 언어](../ide/reference/options-text-editor-all-languages.md) |
|스크롤 막대 | [옵션, 텍스트 편집기, 모든 언어, 스크롤 막대](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|탭  |  [옵션, 텍스트 편집기, 모든 언어, 탭](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>XAML 관련 텍스트 편집기 옵션

다음 표에서는 XAML 기반 앱을 개발할 때 편집 환경을 개선할 수 있는 [옵션](../ide/reference/options-text-editor-xaml-formatting.md) 대화 상자의 설정을 보여 줍니다. 해당 옵션 및 사용 방법에 대한 자세한 내용은 연결된 정보를 참조하세요.

|Name  |추가 정보  |
|---------|---------|
|서식 지정 | [옵션, 텍스트 편집기, XAML, 서식](../ide/reference/options-text-editor-xaml-formatting.md) |
|기타 |  [옵션, 텍스트 편집기, XAML, 기타](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> **기타** 섹션의 **이벤트 처리기 이름을 대문자로 시작** 설정은 XAML 개발자에게 특히 유용합니다. 이 설정은 기본적으로 ‘해제’되어 있지만 코드에서 적절한 대/소문자 구분을 지원하기 위해 ‘설정’하는 것이 좋습니다. 

## <a name="next-steps"></a>다음 단계

디버그 모드에서 앱을 실행하는 동안 실시간으로 코드를 편집하는 방법에 대한 자세한 내용은 [XAML 핫 다시 로드](xaml-hot-reload.md) 페이지를 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio 코드 편집기 기능](../ide/writing-code-in-the-code-and-text-editor.md)
- [UWP 앱의 XAML](/windows/uwp/xaml-platform/xaml-overview/)
- [Xamarin.Forms 앱의 XAML](/xamarin/xamarin-forms/xaml/)
- [Xamarin 모바일 앱 개발(Mac)](/visualstudio/mac/xamarin/)
- [Mac용 Visual Studio 2019 - IDE 둘러보기(Mac)](/visualstudio/mac/ide-tour/)
