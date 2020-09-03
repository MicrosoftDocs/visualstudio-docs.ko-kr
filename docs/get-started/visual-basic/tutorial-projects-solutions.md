---
title: 자습서 프로젝트 및 솔루션 Visual Basic
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 48b3f2c9aae099e3ae5f2cf2d8c438fb0f9062a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590217"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Visual Basic을 사용하여 프로젝트 및 솔루션에 대해 알아보기

이 소개 아티클에서는 Visual Studio에서 *솔루션* 및 *프로젝트* 만들기를 살펴봅니다. 솔루션은 하나 이상의 관련된 코드 프로젝트를 구성하는 데 사용되는 컨테이너입니다(예: 클래스 라이브러리 프로젝트 및 해당 테스트 프로젝트). 프로젝트의 속성 및 포함될 수 있는 일부 파일을 살펴봅니다. 또한 하나의 프로젝트에서 다른 프로젝트에 대한 참조를 만듭니다.

::: moniker range="vs-2017"

> [!TIP]
> 아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> 아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

프로젝트의 개념을 이해하는 교육 연습으로 솔루션 및 프로젝트를 처음부터 구성하겠습니다. 일반적으로 Visual Studio를 사용하는 경우 새 프로젝트를 만들 때 Visual Studio에서 제공하는 다양한 프로젝트 *템플릿*을 사용합니다.

> [!NOTE]
> Visual Studio에서 앱을 개발하는 데 솔루션과 프로젝트는 필요하지 않습니다. 또한 코드, 시작 코딩, 빌드 및 디버깅을 포함하는 폴더를 열 수 있습니다. 예를 들어 [GitHub](https://github.com/) 리포지토리를 복제하면 Visual Studio 프로젝트와 솔루션이 포함되지 않을 수 있습니다. 자세한 내용은 [프로젝트 또는 솔루션 없이 Visual Studio에서 코드 개발](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)을 참조하세요.

## <a name="solutions-and-projects"></a>솔루션 및 프로젝트

이름과 달리 솔루션은 "답변"이 아닙니다. 솔루션은 Visual Studio에서 하나 이상의 관련 프로젝트를 구성하는 데 사용되는 간단한 컨테이너입니다. Visual Studio에서 솔루션을 열면 솔루션에 포함된 모든 프로젝트가 자동으로 로드됩니다.

### <a name="create-a-solution"></a>솔루션 만들기

빈 솔루션을 만들어 탐색을 시작합니다. Visual Studio에 대해 알게 되면 너무 자주 빈 솔루션을 만들지 않게 됩니다. 새 프로젝트를 만들 때 Visual Studio에서는 솔루션이 아직 열려 있지 않은 경우 자동으로 솔루션을 만들어서 프로젝트를 보관합니다.

::: moniker range="vs-2017"

1. Visual Studio를 엽니다.

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

   **새 프로젝트** 대화 상자가 열립니다.

1. 왼쪽 창에서 **기타 프로젝트 형식**을 확장하고 **Visual Studio 솔루션**을 선택합니다. 가운데 창에서 **빈 솔루션** 템플릿을 선택합니다. 솔루션 이름을 **QuickSolution**으로 지정하고 **확인**을 선택합니다.

   ![Visual Studio의 빈 솔루션 템플릿](../media/tutorial-projects-new-solution.png)

   **시작 페이지**가 닫히고 솔루션이 Visual Studio 창 오른쪽에 있는 **솔루션 탐색기**에 표시됩니다. 자주 **솔루션 탐색기**를 사용하여 프로젝트의 내용을 탐색할 수 있습니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio를 엽니다.

2. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

3. **새 프로젝트 만들기** 페이지에서 검색 상자에 **빈 솔루션**을 입력하고 **빈 솔루션** 템플릿, **다음**을 차례로 선택합니다.

   ![Visual Studio 2019의 빈 솔루션 템플릿](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. 솔루션 이름을 **QuickSolution**으로 지정하고 **만들기**를 선택합니다.

   솔루션이 Visual Studio 창 오른쪽에 있는 **솔루션 탐색기**에 표시됩니다. 자주 **솔루션 탐색기**를 사용하여 프로젝트의 내용을 탐색할 수 있습니다.

::: moniker-end

### <a name="add-a-project"></a>프로젝트 추가

이제 첫 번째 프로젝트를 솔루션에 추가해 보겠습니다. 빈 프로젝트를 시작하고 프로젝트에 필요한 항목을 추가합니다.

::: moniker range="vs-2017"

1. **솔루션 탐색기**의 **솔루션 'QuickSolution'** 을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

   **새 프로젝트 추가** 대화 상자가 열립니다.

1. 왼쪽 창에서 **Visual Basic**을 확장하고 **Windows 데스크톱**을 선택합니다. 그런 다음, 가운데 창에서 **빈 프로젝트(.NET Framework)** 템플릿을 선택합니다. 프로젝트 이름을 **QuickDate**로 지정한 다음, **확인** 단추를 선택합니다.

   QuickDate라는 프로젝트는 **솔루션 탐색기**의 솔루션 아래에 표시됩니다. 현재 *App.config*라는 단일 파일이 포함됩니다.

   > [!NOTE]
   > 대화 상자의 왼쪽 창에서 **Visual Basic**이 표시되지 않으면 **.NET 데스크톱 개발** Visual Studio *워크로드*를 설치해야 합니다. Visual Studio에서는 워크로드 기반 설치를 사용하여 개발할 형식에 필요한 구성 요소만을 설치합니다. 새로운 워크로드를 설치하는 쉬운 방법은 **새 프로젝트 추가** 대화 상자의 왼쪽 아래에 있는 **Visual Studio 설치 관리자 열기** 링크를 선택하는 것입니다. Visual Studio 설치 관리자가 실행되면 **.NET 데스크톱 개발** 워크로드를 선택한 다음, **수정** 단추를 선택합니다.
   >
   > ![Visual Studio 설치 관리자 열기 링크](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. **솔루션 탐색기**의 **솔루션 'QuickSolution'** 을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

   **새 프로젝트 추가**라고 표시된 대화 상자가 열립니다.

1. 상단의 검색 상자에 **empty**라는 텍스트를 입력한 다음 **언어** 아래에서 **Visual Basic**을 선택합니다.

1. **빈 프로젝트(.NET Framework)** 템플릿을 선택한 후에 **다음**을 선택합니다.

1. 프로젝트 이름을 **QuickDate**로 지정한 다음, **만들기**를 선택합니다.

   QuickDate라는 프로젝트는 **솔루션 탐색기**의 솔루션 아래에 표시됩니다. 현재 *App.config*라는 단일 파일이 포함됩니다.

   > [!NOTE]
   > **빈 프로젝트(.NET Framework)** 템플릿이 표시되지 않는 경우 **.NET 데스크톱 개발** Visual Studio *워크로드*를 설치해야 합니다. Visual Studio에서는 워크로드 기반 설치를 사용하여 개발할 형식에 필요한 구성 요소만을 설치합니다. 새 프로젝트를 만들 때 **원하는 내용을 찾을 수 없습니까?** 로 표시된 텍스트 아래에서 **추가 도구 및 기능 설치** 링크를 선택하면 새 워크로드를 간편히 설치할 수 있습니다. Visual Studio 설치 관리자가 실행되면 **.NET 데스크톱 개발** 워크로드를 선택한 다음, **수정** 단추를 선택합니다.
   >
   > ![Visual Studio 2019의 설치 관리자 링크](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>프로젝트에 새 항목 추가

빈 프로젝트가 있습니다. 코드 파일을 추가하겠습니다.

1. **솔루션 탐색기**의 **QuickDate** 프로젝트를 마우스 오른쪽 단추로 클릭하거나 상황에 맞는 메뉴에서 **추가** > **새 항목**을 선택합니다.

   **새 항목 추가** 대화 상자가 열립니다.

1. **공통 항목**을 확장한 다음, **코드**를 선택합니다. 가운데 창에서 **클래스** 항목 템플릿을 선택합니다. 클래스 이름을 **Calendar**로 지정한 다음, **추가** 단추를 선택합니다.

   *Calendar.vb*라는 파일을 프로젝트에 추가합니다. 끝에 있는 *.vb*는 Visual Basic 코드 파일에 지정된 파일 확장명입니다. **솔루션 탐색기**의 Visual 프로젝트 계층 구조에 파일이 표시되고 해당 내용이 편집기에서 열립니다.

1. *Calendar.vb* 파일의 콘텐츠를 다음 코드로 바꿉니다.

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   `Calendar` 클래스는 현재 날짜를 반환하는 단일 함수 `GetCurrentDate`를 포함하고 있습니다.

1. **솔루션 탐색기**에서 **내 프로젝트**를 두 번 클릭하여 프로젝트 속성을 엽니다. **애플리케이션** 탭에서 **애플리케이션 유형**을 **클래스 라이브러리**로 변경합니다. 이 단계는 프로젝트를 성공적으로 빌드하는 데 필요합니다.

1. **솔루션 탐색기**에서 **QuickDate**를 마우스 오른쪽 단추로 클릭하고 **빌드**를 선택하여 프로젝트를 빌드합니다. **출력** 창에 성공적인 빌드 메시지가 표시되어야 합니다.

## <a name="add-a-second-project"></a>두 번째 프로젝트 추가

일반적으로 솔루션에 둘 이상의 프로젝트 및 종종 이러한 프로젝트 참조가 서로 포함됩니다. 솔루션의 프로젝트는 클래스 라이브러리, 실행 가능한 애플리케이션 및 일부 단위 테스트 프로젝트 또는 웹 사이트일 수 있습니다.

솔루션에 단위 테스트 프로젝트를 추가해 보겠습니다. 이번에는 프로젝트에 추가 코드 파일을 추가하지 않아도 되도록 프로젝트 템플릿으로 시작하겠습니다.

1. **솔루션 탐색기**의 **솔루션 'QuickSolution'** 을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

::: moniker range="Vs-2017"

2. 왼쪽 창에서 **Visual Basic**을 확장하고 **테스트** 범주를 선택합니다. 가운데 창에서 **단위 테스트 프로젝트(.NET Framework)** 프로젝트 템플릿을 선택합니다. 프로젝트 이름을 **QuickTest**로 지정한 다음, **확인** 단추를 선택합니다.

   두 번째 프로젝트가 **솔루션 탐색기**에 추가되고 *UnitTest1.vb*라는 파일이 편집기에서 열립니다.

   ![두 개의 프로젝트를 포함한 Visual Studio 솔루션 탐색기](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **새 프로젝트 추가** 대화 상자에서 **단위 테스트**라는 텍스트를 상단의 검색 상자에 입력한 다음 **언어** 아래의 **Visual Basic**을 선택합니다.

3. **단위 테스트 프로젝트(.NET Framework)** 프로젝트 템플릿을 선택한 후, **다음**을 선택합니다.

4. 프로젝트 이름을 **QuickTest**로 지정한 다음, **만들기**를 선택합니다.

   두 번째 프로젝트가 **솔루션 탐색기**에 추가되고 *UnitTest1.vb*라는 파일이 편집기에서 열립니다.

::: moniker-end

## <a name="add-a-project-reference"></a>프로젝트 참조 추가

해당 프로젝트에 대한 참조를 추가하기 위해 새 단위 테스트 프로젝트를 사용하여 **QuickDate** 프로젝트에서 이 메서드를 테스트하려고 합니다. 그러면 두 개의 프로젝트 간에 *빌드 종속성*을 만듭니다. 즉, 솔루션을 빌드할 때 **QuickTest** 전에 **QuickDate**가 빌드됩니다.

1. **QuickTest** 프로젝트에서 **참조** 노드를 선택하고 마우스 오른쪽 단추로 클릭하거나 상황에 맞는 메뉴에서 **참조 추가**를 선택합니다.

   ![참조 메뉴 추가](media/tutorial-projects-add-reference-vb.png)

   **참조 관리자** 대화 상자가 열립니다.

1. 왼쪽 창에서 **프로젝트**를 확장하고 **솔루션**을 선택합니다. 가운데 창에서 **QuickDate** 옆에 있는 확인란을 선택한 후 **확인** 단추를 선택합니다.

   **QuickDate** 프로젝트에 대한 참조가 추가됩니다.

## <a name="add-test-code"></a>테스트 코드 추가

1. 이제 Visual Basic 코드 파일에 테스트 코드를 추가합니다. *UnitTest1.vb*의 내용을 다음 코드로 바꿉니다.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   일부 코드에서 빨간색 물결선이 표시됩니다. 테스트 프로젝트를 [friend 어셈블리](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies)에서 **QuickDate** 프로젝트로 만들어서 이 오류를 수정합니다.

1. **QuickDate** 프로젝트로 돌아와서 아직 열지 않은 *Calendar.vb* 파일을 열고, 다음 [Import 문](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) 및 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성을 추가하여 테스트 프로젝트에서 오류를 해결합니다.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   코드 파일이 다음과 같이 나타납니다.

   ![Visual Basic 코드](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>프로젝트 속성

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성이 포함된 *Calendar.vb* 파일의 줄은 **QuickTest** 프로젝트의 어셈블리 이름(파일 이름)을 참조합니다. 어셈블리 이름은 프로젝트 이름과 동일하지 않을 수 있습니다. 프로젝트의 어셈블리 이름을 찾으려면 프로젝트 속성을 엽니다.

1. **솔루션 탐색기**에서 **QuickTest** 프로젝트를 선택합니다. 마우스 오른쪽 단추로 클릭하거나 상황에 맞는 메뉴에서 **속성**을 선택하거나 **Alt**+**Enter** 키를 누릅니다. (**솔루션 탐색기**에서 **내 프로젝트**를 두 번 클릭할 수도 있습니다.)

   프로젝트의 *속성 페이지*가 **애플리케이션** 탭에서 열립니다. 속성 페이지에는 프로젝트에 대한 다양한 설정이 포함됩니다. **QuickTest** 프로젝트의 어셈블리의 이름은 실제로 "QuickTest"입니다. 변경하려는 경우 여기에서 변경할 수 있습니다. 그런 다음, 테스트 프로젝트를 빌드할 때 결과 이진 파일의 이름이 *QuickTest.dll*에서 선택한 이름으로 변경됩니다.

   ![프로젝트 속성](../media/tutorial-projects-properties.png)

1. **컴파일** 및 **설정**과 같은 프로젝트 속성 페이지의 일부 다른 탭을 탐색합니다. 이러한 탭은 다양한 형식의 프로젝트에 따라 달라집니다.

## <a name="optional-run-the-test"></a>(선택 사항) 테스트 실행

단위 테스트가 작동하는지 확인하려면 메뉴 모음에서 **테스트** > **실행** > **모든 테스트**를 선택합니다. **테스트 탐색기**라는 창이 열리면 **TestGetCurrentDate** 테스트에 통과했다고 표시됩니다.

![테스트 통과를 보여주는 Visual Studio의 텍스트 탐색기](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> **테스트 탐색기**가 자동으로 열리지 않는 경우 메뉴 모음에서 **테스트** > **Windows** > **테스트탐색기**를 선택하여 테스트 탐색기를 엽니다.

## <a name="next-steps"></a>다음 단계

Visual Studio를 추가로 탐색하려면 [Visual Basic 자습서](index.yml) 중 하나를 따라 앱을 만드는 것이 좋습니다.

## <a name="see-also"></a>추가 정보

- [프로젝트 및 솔루션 만들기](../../ide/creating-solutions-and-projects.md)
- [프로젝트 및 솔루션 속성 관리](../../ide/managing-project-and-solution-properties.md)
- [프로젝트에서 참조 관리](../../ide/managing-references-in-a-project.md)
- [프로젝트 또는 솔루션 없이 Visual Studio에서 코드 개발](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE 개요](../../get-started/visual-studio-ide.md)
