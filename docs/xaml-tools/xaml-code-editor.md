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
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329182"
---
# <a name="xaml-code-editor"></a>XAML 코드 편집기

[Visual STUDIO IDE](../get-started/visual-studio-ide.md) 의 XAML 코드 편집기에는 Windows 플랫폼 및 [xamarin.ios](/xamarin/xamarin-forms/user-interface/text/editor/)용 WPF 및 UWP 앱을 만드는 데 필요한 모든 도구가 포함 되어 있습니다. 이 문서에서는 XAML 기반 앱을 개발할 때 코드 편집기에서 수행 하는 역할 및 Visual Studio 2019의 XAML 코드 편집기에 고유한 기능에 대해 간략하게 설명 합니다.

먼저 오픈 WPF 프로젝트를 사용 하 여 IDE (통합 개발 환경)를 살펴보겠습니다. 다음 이미지는 XAML 코드 편집기와 함께 사용 하는 몇 가지 주요 IDE 도구를 보여 줍니다.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="XAML에서 열린 WPF 프로젝트를 사용 하는 Visual Studio 2019 IDE" lightbox="media/xaml-code-editor-overview-lrg.png":::

이미지의 왼쪽 아래에서 시계 방향으로 키 IDE 도구는 다음과 같습니다.

- **[XAML 코드 편집기](#xaml-code-editor-ui)** 창에서 &mdash; 코드를 만들고 편집 하는이 문서의 제목입니다 &mdash; .
- UI를 디자인할 **[XAML 디자이너](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** 창
- UI에 컨트롤을 추가 하는 **[도구 상자](../ide/reference/toolbox.md)** 도킹 가능한 창
- **[디버그](../debugger/debugger-feature-tour.md)** 단추로 코드를 실행 하 고 디버그 합니다. <br>[XAML 핫 다시 로드](xaml-hot-reload.md)를 사용 하 여 디버그 하는 동안 코드를 실시간으로 편집할 수도 있습니다.
- 파일, 프로젝트 및 솔루션을 관리 하는 **[솔루션 탐색기](../ide/solutions-and-projects-in-visual-studio.md)** 창
- **[속성](../ide/reference/properties-window.md)** 창-ui의 모양과 ui 컨트롤이 작동 하는 방식을 변경할 수 있습니다.

계속 하려면 XAML 코드 편집기에 대해 자세히 살펴보겠습니다.

## <a name="xaml-code-editor-ui"></a>XAML 코드 편집기 UI

XAML 앱에 대 한 코드 편집기 창은 표준 IDE에도 표시 되는 UI (사용자 인터페이스) 요소를 공유 하지만 XAML 앱을 보다 쉽게 개발할 수 있도록 하는 몇 가지 고유한 기능도 포함 하 고 있습니다.

다음은 XAML 코드 편집기 창 자체를 살펴보는 것입니다.

![Visual Studio의 XAML 코드 편집기 창](media/xaml-code-editor-window.png "Visual Studio 2019의 XAML 코드 편집기 창 스크린샷")

다음으로 코드 편집기의 각 UI 요소에 대 한 함수를 살펴보겠습니다.

### <a name="first-row"></a>첫 번째 행

XAML 코드 창의 맨 위에 있는 첫 번째 행의 왼쪽에는 **디자인** 탭, **창 바꾸기** 단추, **xaml** 탭 및 **팝아웃 xaml** 단추가 있습니다.

![첫 번째 행의 왼쪽이 강조 표시 된 Visual Studio에서 XAML 코드 편집기 창의 맨 위 두 행 중 첫 번째 행입니다.](media/xaml-code-editor-top-row-left.png "왼쪽의 UI 요소가 강조 표시 되는 Visual Studio 2019의 XAML 코드 편집기 창에서 맨 위 두 개 행의 스크린샷")

작업 방법은 다음과 같습니다.

- **디자인** 탭은 XAML 코드 편집기에서 XAML 디자이너 포커스를 변경 합니다.
- **창 바꾸기** 단추는 IDE의 XAML 디자이너 및 XAML 코드 편집기의 위치를 반대로 바꿉니다.
- **Xaml** 탭은 포커스를 xaml 코드 편집기로 다시 변경 합니다.
- **팝아웃 xaml** 단추를 클릭 하면 IDE 외부에 있는 별도의 xaml 코드 편집기 창이 만들어집니다.

오른쪽에서 **세로 분할** 단추, **가로 분할** 단추 및 **창 축소** 단추가 있습니다.

![첫 번째 행의 오른쪽이 강조 표시 된 Visual Studio에서 XAML 코드 편집기 창의 맨 위 두 행 중 첫 번째 행입니다.](media/xaml-code-editor-top-row-right.png "오른쪽의 UI 요소가 강조 표시 된 Visual Studio 2019의 XAML 코드 편집기 창에서 맨 위 두 개 행의 스크린샷")

작업 방법은 다음과 같습니다.

- **세로 분할** 단추를 클릭 하면 XAML 디자이너의 위치와 IDE의 XAML 코드 편집기가 가로 맞춤에서 세로 맞춤으로 변경 됩니다.
- **가로 분할** 단추는 XAML 디자이너 위치와 IDE의 XAML 코드 편집기를 세로 맞춤에서 가로 맞춤으로 변경 합니다.
- **축소 창** 단추를 사용 하면 코드 편집기나 디자이너 인지 여부에 관계 없이 아래쪽 창에 있는 항목을 축소할 수 있습니다. 아래쪽 창을 복원 하려면 동일한 단추를 다시 선택 합니다 .이 단추는 이제 **확장 창** 단추 라고 합니다.

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>두 번째 행

XAML 코드 창의 맨 위에 있는 두 번째 행에는 두 개의 창 드롭다운 목록이 있습니다. 그러나 이러한 UI 요소에 대 한 도구 설명을 보면 "Element: Window" 및 "Member: Window"로 더 쉽게 식별할 수 있습니다.

![두 창 드롭다운 목록이 모두 표시 되는 Visual Studio의 XAML 코드 편집기 창에서 두 개의 상위 행 중 두 번째](media/xaml-code-editor-top-row-windows.png "두 창 드롭다운 목록이 모두 표시 되는 Visual Studio 2019의 XAML 코드 편집기 창에서 맨 위 두 번째 행의 스크린샷")

창 드롭다운 목록은 다음과 같은 다양 한 기능을 포함 합니다.

- 왼쪽의 **요소: 창** 에서는 형제 또는 부모 요소를 보고 탐색할 수 있습니다.

  특히 코드의 태그 구조를 표시 하는 개요와 유사한 뷰를 표시 합니다. 목록에서를 선택 하면 코드 편집기의 포커스가 선택한 요소를 포함 하는 코드 줄에 맞춰집니다.

    ![요소: Visual Studio의 창 드롭다운 목록](media/xaml-element-window-dropdown.png "요소의 스크린샷: Visual Studio 2019의 창 드롭다운 목록")

- 오른쪽의 **멤버: 창** 에서는 특성 또는 자식 요소를 보고 탐색할 수 있습니다.

    특히 코드의 속성 목록이 표시 됩니다. 목록에서 선택 하는 경우 코드 편집기에 포커스가 선택한 속성을 포함 하는 코드 줄에 맞춰집니다.

    ![Visual Studio의 멤버: 창 드롭다운 목록](media/xaml-member-window-dropdown.png "멤버의 스크린샷: Visual Studio 2019의 창 드롭다운 목록")

### <a name="middle-pane-code-editor"></a>중간 창, 코드 편집기

가운데 창은 XAML 코드 편집기의 "코드" 부분입니다. [IDE 코드 편집기](../get-started/tutorial-editor.md)에서 찾을 수 있는 대부분의 기능을 포함 합니다. XAML 코드를 개발 하는 데 도움이 될 수 있는 몇 가지 유니버설 IDE 기능에 대해 살펴보겠습니다. 또한 IDE에서 고유한-XAML 기능도 강조 표시 합니다.

![Visual Studio의 XAML 코드 편집기, 가운데 창만](media/xaml-code-editor-middle.png "Visual Studio 2019의 XAML 코드 편집기, 가운데 창만의 스크린샷")

#### <a name="quick-actions"></a>빠른 작업

[빠른 작업](../ide/quick-actions.md) 을 사용 하 여 단일 작업으로 코드를 리팩터링, 생성 또는 수정할 수 있습니다.

예를 들어 빠른 작업을 사용 하 여 수행할 수 있는 한 가지 유용한 작업은 **MainWindow.xaml.cs** 탭의 c # 코드에서 **불필요 한 using을 제거** 하는 것입니다.

방법은 다음과 같습니다.

1. Using 문을 마우스로 가리키고 전구 아이콘을 선택한 다음 드롭다운 목록에서 **불필요 한 Using 제거** 를 선택 합니다.

    ![빠른 작업 메뉴에서 IDE 편집기의 "불필요 한 Using 제거" 옵션](media/xaml-code-editor-remove-usings.png "빠른 작업 메뉴에서 IDE 편집기의 불필요 한 Using 제거 옵션 스크린샷")

1. **문서**, **프로젝트**또는 **솔루션**에서 발생 하는 모든 항목을 수정할지 여부를 선택 합니다.
1. **미리 보기** 대화 상자를 표시 한 다음 **적용**을 선택 합니다.

메뉴 모음에서이 기능에 액세스할 수도 있습니다. 이렇게 하려면 **편집**  >  **IntelliSense**  >  **제거 및 using 정렬**을 선택 합니다.

Using 설정에 대 한 자세한 내용은 [Using 정렬](../ide/reference/sort-usings.md) 페이지를 참조 하세요. IntelliSense에 대 한 자세한 내용은 [Visual Studio의 intellisense](../ide/using-intellisense.md) 페이지를 참조 하세요. 개발자가 빠른 작업을 사용 하는 일반적인 방법 중 일부에 대 한 자세한 내용은 [일반 빠른 작업](../ide/common-quick-actions.md) 페이지를 참조 하세요.

#### <a name="change-tracking"></a>Change tracking

왼쪽 여백의 색을 사용하여 파일에서 수행한 변경을 계속 추적할 수 있습니다. 색이 수행 하는 작업과 관련 된 방법은 다음과 같습니다.

- 파일이 열려 있지만 저장 되지 않은 이후에 변경한 내용은 왼쪽 여백의 **노란색** 막대로 표시 됩니다 (선택 여백 이라고 함).

    ![노란색 막대로 코드 편집기 편집](media/code-editor-edit-yellow.png "선택 영역 여백에서 노란색 막대로 표시 된 변경 내용이 포함 된 코드 편집기의 스크린샷")

- 변경 내용을 저장 한 후 (파일을 닫기 전) 막대가 **녹색**으로 바뀝니다.

    ![녹색 막대를 사용 하 여 코드 편집기 편집](media/code-editor-edit-green.png "선택 영역 여백에서 녹색 막대로 표시 된 변경 내용이 있는 코드 편집기의 스크린샷")

이 기능을 해제 및 설정하려면 **텍스트 편집기** 설정(**도구** > **옵션** > **텍스트 편집기**)에서 **변경 내용 추적** 옵션을 변경합니다.

&mdash;코드 문자열 아래에 표시 되는 물결선 ("물결선"이 라고도 함)을 포함 하는 변경 내용 추적에 대 한 자세한 내용은 &mdash; [Visual Studio 코드 편집기 페이지의 기능](../ide/writing-code-in-the-code-and-text-editor.md) 에 포함 된 **[편집기 기능](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** 섹션을 참조 하세요.

#### <a name="right-click-context-menu"></a>마우스 오른쪽 단추 클릭 상황에 맞는 메뉴

XAML 코드 편집기에서 코드를 편집 하는 경우 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴를 사용 하 여 액세스할 수 있는 몇 가지 기능이 있습니다. 이러한 기능 중 대부분은 Visual Studio IDE에서 전체적으로 사용할 수 있지만 일부는 디자인 창과 함께 코드 편집기를 사용 하는 경우에만 적용 됩니다.

![Visual Studio에서 XAML 코드 편집기의 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴](media/xaml-code-editor-right-click-menu.png "Visual Studio 2019의 XAML 코드 편집기 오른쪽 클릭 상황에 맞는 메뉴 스크린샷")

각 기능에서 수행 하는 작업과 유용한 방법은 다음과 같습니다.

- **코드 보기** -디자인 창 및 XAML 코드 편집기를 포함 하는 기본 뷰 옆의 탭으로 프로그래밍 언어 코드 창을 엽니다.
- **뷰 디자이너** -디자인 창 및 XAML 코드 편집기를 포함 하는 기본 뷰를 엽니다. (이미 기본 뷰에 있는 경우에는 아무 작업도 수행 하지 않습니다.)
- **빠른 작업 및 리팩터링** 는 단일 작업을 사용 하 여 코드를 생성 하거나 수정 합니다. 코드를 가리키면 빠른 작업이 나 리팩터링을 사용할 수 있을 때 전구 아이콘이 표시 됩니다. <br>참고 항목: [빠른 작업](../ide/quick-actions.md) 및 [리팩터링 코드](../ide/refactoring-in-visual-studio.md)
- **이름 바꾸기** ... -네임 스페이스의 이름만 바꿉니다. 이름을 바꿀 네임 스페이스가 없으면 "네임 스페이스 접두사만 이름을 바꿀 수 있습니다." 라는 오류 메시지가 표시 됩니다.
- **네임 스페이스 제거 및 정렬** -사용 하지 않는 네임 스페이스를 제거한 다음 남은 네임 스페이스를 정렬 합니다.
- **정의 피킹 (peeking** )-편집기에서 현재 위치를 벗어나지 않고 형식 정의를 미리 봅니다. <br>참고 [항목: 정의 피킹 (](../ide/go-to-and-peek-definition.md#peek-definition) peeking)을 사용 하 [여 코드 보기 및 보기 및 편집](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
- **정의로 이동** -형식 또는 멤버의 소스로 이동 하 고 새 탭에서 결과를 엽니다. <br>참고 항목: [정의로 이동](../ide/go-to-and-peek-definition.md#go-to-definition)
- **코드 감싸기** ... -선택한 코드 블록 주위에 추가 되는 코드 감싸기 코드 조각을 사용 합니다. <br>참고 항목: [확장 조각 및 코드 감싸기 조각](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets)
- **조각 삽입** -커서 위치에 코드 조각을 삽입 합니다.
- **잘라내기** -자체 설명
- **복사** -자체 설명
- **붙여넣기** -자체 설명
- **개요** -코드 섹션을 확장 하 고 축소 합니다. <br>참고 항목: [개요](../ide/outlining.md)
- **소스 제어** -오픈 소스 리포지토리에 대 한 코드 기여 기록을 봅니다.

### <a name="middle-pane-scroll-bar"></a>가운데 창, 스크롤 막대

스크롤 막대는 코드를 스크롤할 때 보다 더 많은 작업을 수행할 수 있습니다. 이를 사용 하 여 다른 코드 편집기 창을 열 수도 있습니다. 또한 스크롤 막대를 사용 하 여 주석을 추가 하거나 다른 디스플레이 모드를 사용 하 여 보다 효율적으로 코드를 만들 수 있습니다.

#### <a name="split-the-code-window"></a>코드 창 분할

코드 편집기의 스크롤 막대에는 오른쪽 위에 **분할** 단추가 있습니다. 이를 선택 하면 다른 코드 편집기 창을 열 수 있습니다. 이는 서로 독립적으로 작동 하므로 다른 위치의 코드에서 작업 하는 데 사용할 수 있기 때문에 유용 합니다.

![Visual Studio의 XAML 코드 편집기, 가운데 창만](media/code-editor-split-window-button.png "Visual Studio 2019의 XAML 코드 편집기, 가운데 창만의 스크린샷")

편집기 창을 분할 하는 방법에 대 한 자세한 내용은 편집기 창 [관리](../ide/how-to-manage-editor-windows.md) 페이지를 참조 하세요.

#### <a name="use-annotations-or-map-mode"></a>주석 또는 지도 모드 사용

스크롤 막대의 모양과 그에 포함 된 추가 기능을 변경할 수도 있습니다. 예를 들어 코드 변경, 중단점, 책갈피, 오류 및 캐럿 위치와 같은 시각적 신호를 제공 하는 스크롤 막대에 *주석을* 포함 하는 경우가 많습니다.

다른 사람들은 스크롤 막대에 코드 줄을 축소 하는 *맵 모드*를 사용 하 여 감사 합니다. 파일에 코드가 많은 개발자는 맵 모드가 기본 스크롤 막대 보다 더 효과적으로 코드 줄에 추적 하는 것을 알 수 있습니다.

스크롤 막대의 기본 설정을 변경 하는 방법에 대 한 자세한 내용은 [스크롤 막대 사용자 지정](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) 페이지를 참조 하세요.

## <a name="xaml-specific-features"></a>XAML 관련 기능

다음 기능 중 대부분은 Visual Studio IDE에서 전체적으로 사용할 수 있지만 XAML 개발자에 게 코딩을 용이 하 게 하는 몇 가지 차원을 추가 했습니다.

### <a name="xaml-code-snippets"></a>XAML 코드 조각

코드 조각은 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴 명령을 사용 하 여 코드 파일에 삽입할 수 있는 작은 재사용 가능한 코드 블록으로, 코드 **조각 삽입** 또는 바로 가기 키 조합 (**ctrl** + **K**, **ctrl** + **X**)을 사용 합니다. [IntelliSense](../ide/using-intellisense.md) 는 기본 제공 코드 조각과 수동으로 추가 하는 모든 사용자 지정 코드 조각에 대해 작동 하는 XAML 조각 표시를 지원 하도록 향상 되었습니다. 기본 XAML 코드 조각 `#region` 에는,, `Column definition` `Row definition` , 및가 `Setter` `Tag` 있습니다.

![IntelliSense에 표시 되는 XAML 코드 조각 옵션이 있는 XAML 코드 편집기](media/xaml-code-snippets.png "IntelliSense에 표시 되는 XAML 코드 조각 옵션이 있는 XAML 코드 편집기의 스크린샷")

자세한 내용은 [코드 조각](../ide/code-snippets.md) 및 [c # 코드 조각](../ide/visual-csharp-code-snippets.md) 페이지를 참조 하세요.

### <a name="xaml-region-support"></a>XAML #region 지원

Visual Studio 2015부터 WPF 및 UWP의 XAML 개발자가 사용할 수 있도록 지원 하 고 더 최근에 [xamarin.ios](/xamarin/xamarin-forms/user-interface/text/editor/)에서도 지원 #region 했습니다. Visual Studio 2019에서는 #region 지원에 대 한 향상 된 기능을 지속적으로 개선 하 고 있습니다. 예를 들어 [버전 16.4](/visualstudio/releases/2019/release-notes-v16.4/) 이상에서는 입력을 시작할 때 #region 옵션이 표시 `<!` 됩니다.

![IntelliSense에 표시 되는 #region 옵션을 포함 하는 XAML 코드 편집기](media/code-editor-xaml-region.png "IntelliSense에 표시 되는 #region 옵션을 포함 하는 XAML 코드 편집기의 스크린샷")

확장 하거나 축소할 코드의 섹션을 그룹화 하려는 경우 영역을 사용할 수 있습니다.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

영역에 대 한 자세한 내용은 [#region (c # 참조)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) 페이지를 참조 하세요. 코드 섹션을 확장 하 고 축소 하는 방법에 대 한 자세한 내용은 [개요](../ide/outlining.md) 페이지를 참조 하세요.

### <a name="xaml-comments"></a>XAML 주석

개발자는 종종 주석을 사용 하 여 코드를 문서화 하는 것을 선호 합니다. 다음과 같은 방법으로 **mainwindow.xaml** 탭에 있는 xaml 코드에 주석을 추가할 수 있습니다.

- 주석 앞에를 입력 한 `<!--` 다음 `-->` 주석 뒤에를 추가 합니다.
- `<!`을 입력 한 다음 `!--` 옵션 목록에서 선택 합니다.

  ![XAML 코드 편집기 주석 추가 대화 상자를 마우스 오른쪽 단추로 클릭](media/xaml-code-editor-comments.png "XAML 코드 편집기에서 주석을 추가 하는 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴의 스크린샷")

- 주석으로 감쌀 코드를 선택 하 고 IDE의 도구 모음에서 **주석** 단추를 선택 합니다. 작업을 반대로 하려면 **주석 제거** 단추를 선택 합니다.

  ![IDE 도구 모음의 주석 단추와 주석 제거 단추](media/comment-undo-comment-buttons.png "IDE 도구 모음의 주석 단추 및 주석 제거 단추 스크린샷")

- 주석으로 묶을 코드를 선택 하 고 **ctrl** + **K**, **ctrl** + **C**를 누릅니다. 선택한 코드의 주석 처리를 제거 하려면 **ctrl** + **K**, **ctrl** + **U**를 누릅니다.

**MainWindow.xaml.cs** 탭에 있는 c # 코드에서 주석을 사용 하는 방법에 대 한 자세한 내용은 [설명서 주석](/dotnet/csharp/language-reference/language-specification/documentation-comments/) 페이지를 참조 하세요.

### <a name="xaml-lightbulbs"></a>XAML 전구

XAML 코드에 표시 되는 전구 아이콘은 코드를 리팩터링, 생성 또는 수정 하는 데 사용할 수 있는 [빠른 작업](../ide/quick-actions.md) 의 일부입니다.

다음은 XAML 코딩 환경에 어떤 도움이 될 수 있는지에 대 한 몇 가지 예입니다.

- **불필요 한 네임 스페이스를 제거**합니다. XAML 코드 편집기에서 불필요 한 네임 스페이스는 흐리게 표시 된 텍스트로 표시 됩니다. 불필요 한를 사용 하 여 커서를 가리키면 전구가 표시 됩니다. 드롭다운 목록에서 **불필요 한 네임 스페이스 제거** 옵션을 선택 하면 제거할 수 있는 미리 보기가 표시 됩니다.

  ![빠른 작업 전구에서 XAML 코드 편집기의 불필요 한 네임 스페이스 제거 옵션](media/xaml-code-editor-dimmed-namespaces-preview.png "빠른 작업 전구를 사용 하 여 나타나는 XAML 코드 편집기의 불필요 한 네임 스페이스 제거 옵션의 스크린샷")

- **네임 스페이스의 이름을 바꿉니다**. 네임 스페이스를 강조 표시 한 후 오른쪽 클릭 상황에 맞는 메뉴에서 사용할 수 있는이 기능을 통해 한 번에 여러 설정 인스턴스를 쉽게 변경할 수 있습니다. 메뉴 모음을 사용 하 여이 기능에 액세스 하거나, **Edit**  >  **리팩터링**  >  **이름 바꾸기**를 편집 하거나, **ctrl** + **r**, **ctrl** + **r** 을 차례로 눌러이 기능에 액세스할 수도 있습니다.

  ![오른쪽 클릭 상황에 맞는 메뉴의 XAML 코드 편집기의 네임 스페이스 이름 바꾸기 옵션](media/code-editor-rename-namespace.png "오른쪽 클릭 상황에 맞는 메뉴를 사용 하 여 표시 되는 XAML 코드 편집기의 네임 스페이스 이름 바꾸기 옵션의 스크린샷")

  자세한 내용은 [코드 기호 이름 바꾸기 리팩터링](../ide/reference/rename.md) 페이지를 참조 하세요.

### <a name="conditional-xaml-for-uwp"></a>UWP 용 조건부 XAML

조건부 XAML은 XAML 태그에 [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) 메서드를 사용하는 방법을 제공합니다. 이를 통해 코드 숨김을 사용하지 않고도 API의 존재 여부를 기반으로 태그에서 속성을 설정하고 개체를 인스턴스화할 수 있습니다.

자세한 내용은 [조건부 XAML](/windows/uwp/debug-test-perf/conditional-xaml/) 페이지 및 [데스크톱 앱의 호스트 UWP XAML 컨트롤 (XAML 아일랜드)](/windows/apps/desktop/modernize/xaml-islands/) 페이지를 참조 하세요.

### <a name="xaml-structure-visualizer"></a>XAML 구조 시각화 도우미

코드 편집기의 구조 시각화 도우미 기능에는 코드에서 열린 태그와 닫힌 태그 요소 일치를 나타내는 세로 파선 인 구조 안내선이 표시 됩니다. 이러한 세로줄을 사용 하면 논리 블록의 시작 및 종료 위치를 쉽게 확인할 수 있습니다.

자세한 내용은 [코드 탐색](../ide/navigating-code.md) 페이지를 참조 하세요.

### <a name="intellicode-for-xaml"></a>XAML에 대 한 IntelliCode

코드에 XAML 태그를 추가 하는 경우 일반적으로 왼쪽 꺾쇠 괄호를 사용 하 여 시작 `<` 합니다. 이 꺾쇠 괄호를 입력 하면 인기 있는 여러 XAML 태그를 나열 하는 IntelliCode 메뉴가 나타납니다. 코드에 신속 하 게 추가 하려는 항목을 선택 합니다.

IntelliCode 선택 항목은 목록의 맨 위에 표시 되 고 별표 표시 되기 때문에 인식할 수 있습니다.

![XAML 텍스트 편집기에 대 한 IntelliCode 목록입니다.](media/xaml-intellicode-selection.png "XAML 텍스트 편집기에 대 한 IntelliCode list의 스크린샷")

자세한 내용은 [IntelliCode 개요](/visualstudio/intellicode/overview/) 페이지를 참조 하세요.

### <a name="settings"></a>설정

Visual Studio IDE의 *모든* 설정에 대 한 자세한 내용은 [코드 편집기 페이지의 기능](../ide/writing-code-in-the-code-and-text-editor.md) 을 참조 하세요.

## <a name="xaml-optional-settings"></a>XAML 선택적 설정

[옵션](../ide/reference/options-dialog-box-visual-studio.md) 대화 상자를 사용 하 여 XAML 코드 편집기에 대 한 기본 설정을 변경할 수 있습니다. 설정을 보려면 **도구**  >  **옵션**  >  **텍스트 편집기**  >  **XAML**을 선택 합니다.

![XAML 텍스트 편집기에 대 한 옵션 목록](media/xaml-tools-options.png "XAML 텍스트 편집기에 대 한 옵션 목록의 스크린샷")

> [!NOTE]
> 바로 가기 키를 사용 하 여 옵션 대화 상자에 액세스할 수도 있습니다. 방법: **Ctrl** + **Q** 를 눌러 IDE를 검색 하 고, **옵션**을 입력 한 다음 **enter**키를 누릅니다. 그런 다음 **ctrl** + **E** 를 눌러 옵션 대화 상자를 검색 하 고 **텍스트 편집기**를 입력 **Enter**한 다음 enter 키를 누르고 **XAML**을 입력 한 다음 **enter**키를 누릅니다.
>  
> 바로 가기 키에 대 한 자세한 내용은 [Visual Studio에 대 한 바로 가기 팁](../ide/productivity-shortcuts.md#code-editor) 페이지를 참조 하세요.

### <a name="universal-text-editor-options"></a>유니버설 텍스트 편집기 옵션

XAML에 대 한 [옵션](../ide/reference/options-text-editor-xaml-formatting.md) 대화 상자에서 다음 처음 세 항목은 VISUAL Studio IDE에서 지 원하는 모든 프로그래밍 언어로 유니버설 됩니다. 이러한 옵션 및 사용 방법에 대 한 자세한 내용을 보려면 다음 표의 연결 된 정보를 참조 하세요.

|이름  |추가 정보  |
|---------|---------|
|일반  | [옵션 대화 상자: 모든 언어 > 텍스트 편집기](../ide/reference/options-text-editor-all-languages.md) |
|스크롤 막대 | [옵션, 텍스트 편집기, 모든 언어, 스크롤 막대](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|탭  |  [옵션, 텍스트 편집기, 모든 언어, 탭](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>XAML 관련 텍스트 편집기 옵션

다음 표에서는 XAML 기반 앱을 개발할 때 편집 환경을 개선할 수 있는 [옵션](../ide/reference/options-text-editor-xaml-formatting.md) 대화 상자의 설정을 보여 줍니다. 이러한 옵션 및 사용 방법에 대 한 자세한 내용을 보려면 연결 된 정보를 참조 하세요.

|이름  |추가 정보  |
|---------|---------|
|서식 | [옵션, 텍스트 편집기, XAML, 서식](../ide/reference/options-text-editor-xaml-formatting.md) |
|기타 |  [옵션, 텍스트 편집기, XAML, 기타](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> **기타** 섹션의 **대문자화 이벤트 처리기 메서드 이름** 설정은 XAML 개발자에 게 특히 유용 합니다. 이 설정은 새로운 기능 이기 때문에 기본적으로 *해제* 되어 있지만, 코드에서 적절 한 대/소문자 구분을 *지원 하도록 설정* 하는 것이 좋습니다.

## <a name="next-steps"></a>다음 단계

디버그 모드에서 앱을 실행 하는 동안 실시간으로 코드를 편집 하는 방법에 대해 자세히 알아보려면 [XAML 핫 다시 로드](xaml-hot-reload.md) 페이지를 참조 하세요.

## <a name="see-also"></a>참조

- [Visual Studio code 편집기 기능](../ide/writing-code-in-the-code-and-text-editor.md)
- [UWP 앱의 XAML](/windows/uwp/xaml-platform/xaml-overview/)
- [Xamarin.Forms 앱의 XAML](/xamarin/xamarin-forms/xaml/)
- [Xamarin 모바일 앱 개발 (Mac)](/visualstudio/mac/xamarin/)
- [Mac 용 Visual Studio 2019-IDE 둘러보기 (Mac)](/visualstudio/mac/ide-tour/)
