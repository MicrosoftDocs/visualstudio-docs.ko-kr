---
title: '1단계: 프로젝트 만들기 및 양식에 테이블 추가'
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1134fb5bb02bd8c78f347ef582f12da35074c36
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579926"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>1단계: 프로젝트 만들기 및 양식에 테이블 추가

일치 게임을 만들 때 첫 번째 단계에서는 프로젝트를 만들고 폼에 테이블을 추가합니다. 테이블을 사용하면 4x4 모눈에 순서대로 아이콘을 정렬할 수 있습니다. 또한 게임 보드의 모양을 개선하는 몇 가지 속성을 설정할 수 있습니다.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>프로젝트를 만들고 폼에 테이블을 추가하려면

::: moniker range="vs-2017"

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

1. **새 프로젝트** 대화 상자의 왼쪽에서 **Visual C#** 또는 **Visual Basic**을 선택한 다음 **Windows 데스크톱**을 선택합니다.

1. 템플릿 목록에서 **Windows Forms 앱(.NET Framework)** 템플릿을 선택하고 이름을 *MatchingGame*으로 지정한 다음 **확인** 단추를 선택합니다.

    선택한 프로그래밍 언어에 따라 *Form1.cs* 또는 *Form1.vb*라는 폼이 표시됩니다.

   > [!NOTE]
   > **Windows Forms 앱(.NET Framework)** 템플릿이 표시되지 않을 경우 Visual Studio 설치 관리자를 사용하여 **.NET 데스크톱 개발** 워크로드를 설치합니다.<br/><br/>![Visual Studio 설치 관리자의 .NET 데스크톱 개발 워크로드](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> 자세한 내용은 [Visual Studio 설치](../install/install-visual-studio.md) 페이지를 참조하세요.

::: moniker-end

::: moniker range="vs-2019"

1. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   !['새 프로젝트 만들기' 창 보기](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **새 프로젝트 만들기** 창의 검색 상자에 *Windows Forms*를 입력합니다. 그런 다음 **프로젝트 형식** 목록에서 **바탕 화면**을 선택합니다.

   **프로젝트 형식** 필터를 적용한 후 C# 또는 Visual Basic에 대한 **Windows Forms 앱(.NET Framework)** 템플릿을 선택하고 **다음**을 선택합니다.

   ![Windows Forms 앱(.NET Framework)용 C# 또는 Visual Basic 템플릿 선택](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms 앱(.NET Framework)** 템플릿이 표시되지 않는 경우 **새 프로젝트를 만들기** 창에서 설치할 수 있습니다. **원하는 항목을 찾을 수 없나요?** 메시지에서 **추가 도구 및 기능 설치** 링크를 선택합니다.
   >
   > !['새 프로젝트 만들기' 창의 '원하는 항목을 찾을 수 없음' 메시지에서 '추가 도구 및 기능 설치' 링크](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > 그런 다음, Visual Studio 설치 관리자에서 **.NET 데스크톱 개발** 워크로드를 선택합니다.
   >
   > ![Visual Studio 설치 관리자의 .NET Core 워크로드](../ide/media/install-dot-net-desktop-env.png)
   >
   > 그런 다음, Visual Studio 설치 관리자에서 **수정** 단추를 선택합니다. 작업 내용을 저장하라는 메시지가 나타날 수 있습니다. 그럴 경우 그렇게 하세요. 다음으로, **계속**을 선택하여 워크로드를 설치합니다.

1. **새 프로젝트 구성** 창에서 **프로젝트 이름** 상자에 *MatchingGame*을 입력합니다. 그런 다음, **만들기**를 선택합니다.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>양식의 속성을 설정하려면

1. **속성** 창에서 다음 폼 속성을 설정합니다.

   1. 폼의 **Text** 속성을 **Form1**에서 **일치 게임**으로 변경합니다. 이 텍스트는 게임 창 위쪽에 표시됩니다.

   2. 이 폼의 크기를 550*400픽셀로 설정합니다. 이렇게 하려면 **Size** 속성을 **550, 550**으로 설정하거나, IDE(통합 개발 환경)의 오른쪽 아래 모퉁이에 표시되는 크기가 원하는 크기가 될 때까지 폼의 모퉁이를 끌면 됩니다.

2. IDE의 왼쪽에 있는 **도구 상자** 탭을 선택하여 도구 상자를 표시합니다.

3. 도구 상자의 **컨테이너** 범주에서 <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤을 끌어와 이 컨트롤의 다음 속성을 설정합니다.

   1. **BackColor** 속성을 **CornflowerBlue**로 설정합니다. 이렇게 하려면 **속성** 창의 **BackColor** 속성 옆에 있는 드롭다운 화살표를 선택하여 **BackColor** 대화 상자를 엽니다.  그런 다음 **BackColor** 대화 상자의 **웹** 탭을 선택하여 사용할 수 있는 색이름 목록을 봅니다.

      > [!NOTE]
      > 색은 알파벳 순서가 아니며 **CornflowerBlue**는 목록 맨 아래 가까이에 있습니다.

   2. 속성 옆에 있는 드롭다운 단추를 선택한 다음, 가운데 있는 큰 단추를 선택하여 **Dock** 속성을 **Fill**로 설정합니다. 이렇게 하면 전체 폼을 덮도록 테이블이 확장됩니다.

   3. **CellBorderStyle** 속성을 **Inset**으로 설정합니다. 이렇게 하면 보드의 각 셀 사이에 시각적 테두리가 생깁니다.

   4. TableLayoutPanel의 오른쪽 위 모퉁이에 있는 삼각형 모양의 단추를 선택하여 해당 작업 메뉴를 표시합니다.

   5. 작업 메뉴에서 **행 추가**를 두 번 선택하여 행을 두 개 이상 추가한 다음, **열 추가**를 두 번 선택하여 열을 두 개 이상 추가합니다.

   6. 작업 메뉴에서 **행 및 열 편집**을 선택하여 **열 및 행 스타일** 창을 엽니다. 각 열을 선택하고 **백분율** 옵션 단추를 선택한 후 각 열의 너비를 전체 너비의 25%로 설정합니다. 그런 다음 창의 맨 위에 있는 드롭다운 상자에서 **행**을 선택하고 각 행의 높이를 25%로 설정합니다. 완료되면 **확인** 단추를 선택합니다.

      이제 TableLayoutPanel이 크기가 같은 사각형 셀이 16개 포함된 4x4 모눈이 됩니다. 이러한 행과 열은 나중에 아이콘 이미지가 표시될 위치입니다.

4. 폼 편집기에서 TableLayoutPanel이 선택되어 있어야 합니다. 이를 확인하려면 **속성** 창의 맨 위에 있는 **tableLayoutPanel1**을 확인합니다. 이 속성이 선택되어 있지 않은 경우 폼의 TableLayoutPanel을 선택하거나 **속성** 창 맨 위에 있는 드롭다운 컨트롤에서 이를 선택합니다.

    TableLayoutPanel이 선택된 상태에서 도구 상자를 열고 **공용 컨트롤** 범주에 있는 <xref:System.Windows.Forms.Label> 컨트롤을 TableLayoutPanel의 왼쪽 위 셀에 추가합니다. 이제 IDE에서 레이블 컨트롤이 선택되어 있어야 합니다. 여기에 다음 속성을 설정합니다.

   1. 레이블의 **BackColor** 속성이 **CornflowerBlue**로 설정되어 있는지 확인합니다.

   2. **AutoSize** 속성을 **False**로 설정합니다.

   3. **Dock** 속성을 **Fill**로 설정합니다.

   4. 속성 옆에 있는 드롭다운 단추를 선택한 다음, 가운데 단추를 선택하여 **TextAlign** 속성을 **MiddleCenter**로 설정합니다. 이렇게 하면 셀의 중앙에 아이콘이 나타납니다.

   5. **Font** 속성을 선택합니다. 그러면 줄임표( **...** ) 단추가 나타납니다.

   6. 줄임표 단추를 선택하고 **글꼴** 값을 **Webdings**로, **글꼴 스타일**에 **굵게**, **크기**에 **48**을 각각 설정합니다.

   7. 레이블의 **Text** 속성을 문자 **c**로 설정합니다.

        이제 TableLayoutPanel의 왼쪽 위 셀에는 파란색 배경의 가운데에 검은색 상자가 포함됩니다.

       > [!NOTE]
       > Webdings 글꼴은 Windows 운영 체제에 포함된 아이콘 글꼴입니다. 일치 게임에서 플레이어는 일치하는 아이콘 쌍을 찾아야 하므로 이 글꼴을 사용하여 일치시킬 아이콘을 표시합니다. **Text** 속성을 **c**로 설정하는 대신 다른 문자를 입력하여 아이콘이 어떻게 표시되는지 확인해 보세요. 느낌표는 거미, 대문자 N은 눈 모양, 쉼표는 고추를 각각 나타냅니다.

5. Label 컨트롤을 선택하고 TableLayoutPanel의 다음 셀에 이를 복사합니다. **Ctrl**+**C** 키를 선택하거나 메뉴 모음에서 **편집** > **복사**를 선택합니다. 그런 다음 이 컨트롤을 붙여넣습니다. **Ctrl**+**V** 키를 선택하거나 메뉴 모음에서 **편집** > **붙여넣기**를 선택합니다. TableLayoutPanel의 두 번째 셀에 첫 번째 Label의 복사본이 나타납니다. 이 Label을 다시 붙여넣으면 세 번째 셀에 다른 Label이 나타납니다. 모든 셀이 채워질 때까지 Label 컨트롤 붙여넣기를 계속합니다.

   > [!NOTE]
   > IDE에서 붙여넣기를 너무 많이 하면 TableLayoutPanel에 새 행이 추가되어 새 Label 컨트롤을 추가할 수 있는 위치가 생깁니다. 이를 실행 취소할 수 있습니다. 새 셀을 제거하려면 **Ctrl**+**Z** 키를 선택하거나 메뉴 모음에서 **편집** > **실행 취소**를 선택합니다.

    이제 폼이 배치됩니다. 다음 그림과 유사하게 나타납니다.

    ![초기 일치 게임 폼](../ide/media/express_tut4step1.png)<br/>*초기 일치 게임 폼*

## <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동하려면 [2단계: 임의의 개체 및 아이콘 목록 추가](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)를 참조하세요.

- 개요 항목으로 돌아가려면 [자습서 3: 맞추기 게임 만들기](../ide/tutorial-3-create-a-matching-game.md)를 참조하세요.
