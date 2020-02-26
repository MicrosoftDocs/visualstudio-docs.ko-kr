---
title: '1단계: Windows Forms 앱 프로젝트 만들기'
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d5e34d825d2a4d296a8a394105b412195b4e3fb
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579906"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>1단계: Windows Forms 앱 프로젝트 만들기

사진 뷰어를 만드는 첫 번째 단계는 Windows Forms 앱 프로젝트를 만드는 것입니다.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Visual Studio 2017을 엽니다.

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다. 대화 상자가 다음 스크린샷과 유사하게 표시될 것입니다.

     ![새 프로젝트 대화 상자](../ide/media/newprojectdialogcallouts.png)<br/>***새 프로젝트*** *대화 상자*

2. **새 프로젝트** 대화 상자의 왼쪽에서 **Visual C#** 또는 **Visual Basic**을 선택한 다음 **Windows 데스크톱**을 선택합니다.

3. 프로젝트 템플릿 목록에서 **Windows Forms 앱(.NET Framework)** 을 선택합니다. 새 폼의 이름을 *PictureViewer*로 지정한 후 **확인** 단추를 선택합니다.

    >[!NOTE]
    >**Windows Forms 앱(.NET Framework)** 템플릿이 표시되지 않을 경우 Visual Studio 설치 관리자를 사용하여 **.NET 데스크톱 개발** 워크로드를 설치합니다.<br/><br/>![Visual Studio 설치 관리자의 .NET 데스크톱 개발 워크로드](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> 자세한 내용은 [Visual Studio 설치](../install/install-visual-studio.md) 페이지를 참조하세요.

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Visual Studio 2019 열기

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

1. **새 프로젝트 구성** 창의 **프로젝트 이름** 상자에 *PictureViewer*를 입력합니다. 그런 다음, **만들기**를 선택합니다.

::: moniker-end

Visual Studio에서 앱의 솔루션이 생성됩니다. 솔루션은 앱에 필요한 모든 프로젝트 및 파일의 컨테이너 역할을 합니다. 이러한 용어에 대해서는 이 자습서의 뒷부분에서 자세히 설명합니다.

## <a name="about-the-windows-forms-app-project"></a>Windows Forms 앱 프로젝트 정보

1. 개발 환경에는 주 창, **솔루션 탐색기** 및 **속성** 창의 세 가지 창이 포함되어 있습니다.

     이러한 창 중 하나라도 없는 경우 기본 창 레이아웃을 복원할 수 있습니다. 메뉴 모음에서 **창** > **창 레이아웃 다시 설정**을 선택합니다.

     메뉴 명령을 사용하여 창을 표시할 수도 있습니다. 메뉴 모음에서 **보기** > **속성 창** 또는 **솔루션 탐색기**를 선택합니다.

     다른 창이 열려 있는 경우 오른쪽 위 모서리에서 **닫기**(x) 단추를 선택하여 해당 창을 닫습니다.

    ::: moniker range="vs-2017"

    * **주 창** 이 창에서는 폼 작업, 코드 편집 등 대부분의 작업을 수행합니다. 창에는 **폼 편집기**의 폼이 표시되어 있습니다. 창의 맨 위에 **시작 페이지** 탭과 **Form1.cs[디자인]** 탭이 나타납니다. Visual Basic에서는 탭 이름이 *.cs*가 아닌 *.vb*로 끝납니다.

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **주 창** 이 창에서는 폼 작업, 코드 편집 등 대부분의 작업을 수행합니다. 창에는 **폼 편집기**의 폼이 표시되어 있습니다.

    ::: moniker-end

    * **솔루션 탐색기 창** 이 창에서는 솔루션의 모든 항목을 보고 탐색할 수 있습니다.

    파일을 선택하면 **속성** 창의 내용이 변경됩니다. C#에서는 *.cs*로 끝나고 Visual Basic에서는 *.vb*로 끝나는 코드 파일을 열면 코드 파일이나 코드 파일의 디자이너가 나타납니다. 디자이너는 단추, 목록 등의 컨트롤을 추가할 수 있는 시각적 화면입니다. Visual Studio 폼의 디자이너를 **Windows Forms 디자이너**라고 합니다.

    * **속성 창** 이 창에서는 다른 창에서 선택한 항목의 속성을 변경할 수 있습니다. 예를 들어 Form1을 선택하는 경우 **Text** 속성을 설정하여 제목을 변경하고 **Backcolor** 속성을 설정하여 배경색을 변경할 수 있습니다.

      > [!NOTE]
      > **솔루션 탐색기**의 가장 위쪽 줄에는 Visual Studio에서 솔루션이 생성되었음을 의미하는 **솔루션 'PictureViewer'(프로젝트 1개)** 가 표시됩니다. 솔루션에 둘 이상의 프로젝트를 포함할 수는 있지만, 지금은 하나의 프로젝트만 포함된 솔루션으로 작업하겠습니다.

1. 메뉴 모음에서 **파일** > **모두 저장**을 차례로 선택합니다.

     또는 다음 이미지와 같이 도구 모음에서 **모두 저장** 단추를 선택합니다.

     ![모두 저장 도구 모음 단추](../ide/media/express_iconsaveall.png)<br/>
     ***모두 저장*** *도구 모음 단추*

     Visual Studio에서 자동으로 폴더 이름과 프로젝트 이름이 채워진 후 프로젝트 폴더에 프로젝트가 저장됩니다.

## <a name="next-steps"></a>다음 단계

* 다음 자습서 단계로 이동하려면 **[2단계: 앱 실행](../ide/step-2-run-your-program.md)** 을 참조하세요.

* 개요 항목으로 돌아가려면 [자습서 1: 사진 뷰어 만들기](../ide/tutorial-1-create-a-picture-viewer.md)를 참조하세요.

## <a name="see-also"></a>참조

* [자습서 2: 시간이 지정된 수학 퀴즈 만들기](tutorial-2-create-a-timed-math-quiz.md)
* [자습서 3: 맞추기 게임 만들기](tutorial-3-create-a-matching-game.md)
