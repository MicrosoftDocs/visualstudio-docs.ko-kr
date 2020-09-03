---
title: '자습서: Visual Basic 시작'
description: Visual Studio에서 Visual Basic 콘솔 앱을 만드는 방법을 단계별로 알아봅니다.
ms.custom: seodec18, get-started
ms.date: 09/11/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 279bfb00a2466120d21c5c868c0987ec19202acc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579942"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>자습서: Visual Studio에서 Visual Basic 시작

VB(Visual Basic)에 대한 이 자습서에서는 Visual Studio를 사용하여 몇 가지 콘솔 앱을 만들어 실행하고, 그 과정에서 [Visual Studio IDE(통합 개발 환경)](visual-studio-ide.md)의 일부 기능을 살펴봅니다.

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

## <a name="create-a-project"></a>프로젝트 만들기

먼저 Visual Basic 애플리케이션 프로젝트를 만들겠습니다. 아무 것도 추가하지 않아도 필요한 모든 템플릿 파일과 함께 프로젝트 형식이 제공됩니다.

::: moniker range="vs-2017"

1. Visual Studio 2017을 엽니다.

2. 상단 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual Basic**을 확장한 후 **.NET Core**를 선택합니다. 가운데 창에서 **콘솔 앱(.NET Core)** 을 선택합니다. 그런 다음 프로젝트 이름을 *WhatIsYourName*으로 지정합니다.

   ![Visual Studio IDE의 새 프로젝트 대화 상자의 콘솔 앱(.NET Core) 프로젝트 템플릿](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>(선택 사항) 워크로드 추가

**콘솔 앱(.NET Core)** 프로젝트 템플릿이 표시되지 않는 경우, **.NET Core 플랫폼 간 개발** 워크로드를 추가하여 얻을 수 있습니다. 컴퓨터에 Visual Studio 2017 업데이트가 설치되었는지 여부에 따라 다음 두 방법 중 하나로 이 워크로드를 추가할 수 있습니다.

#### <a name="option-1-use-the-new-project-dialog-box"></a>옵션 1: 새 프로젝트 대화 상자 사용

1. **새 프로젝트** 대화 상자에서 **Visual Studio 설치 관리자 열기** 링크를 클릭합니다.

   ![새 프로젝트 대화 상자에서 Visual Studio 설치 관리자 열기 링크를 클릭합니다.](../media/vs-open-visual-studio-installer-generic.png)

1. Visual Studio 설치 관리자가 시작됩니다. **.NET Core 플랫폼 간 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.

   ![Visual Studio Installer에서 .NET Core 플랫폼 간 개발 워크로드](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>옵션 2: 도구 메뉴 모음 사용

1. **새 프로젝트** 대화 상자를 취소하고 상단 메뉴 모음에서 **도구** > **도구 및 기능 가져오기**를 선택합니다.

1. Visual Studio 설치 관리자가 시작됩니다. **.NET Core 플랫폼 간 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> 이 자습서의 일부 스크린샷은 어두운 테마를 사용합니다. 어두운 테마를 사용하지 않지만 원하는 경우 [Visual Studio IDE 및 편집기 개인 설정](../../ide/quickstart-personalize-the-ide.md) 페이지에서 참조하여 방법을 알아봅니다.

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   !['새 프로젝트 만들기' 창 보기](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **새 프로젝트 만들기** 창에서 검색 상자에 *콘솔*을 입력합니다. 그런 다음, 언어 목록에서 **Visual Basic**을 선택한 다음, 플랫폼 목록에서 **Windows**를 선택합니다. 

   언어 및 플랫폼 필터를 적용한 후 **콘솔 앱(.NET Core)** 템플릿을 선택한 후, **다음**을 선택합니다.

   ![콘솔 앱(.NET Framework)에 대한 Visual Basic 템플릿을 선택합니다.](./media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **콘솔 앱(.NET Core)** 템플릿이 표시되지 않으면 **새 프로젝트를 만들기** 창에서 설치할 수 있습니다. **원하는 항목을 찾을 수 없나요?** 메시지에서 **추가 도구 및 기능 설치** 링크를 선택합니다.
   >
   > !['새 프로젝트 만들기' 창의 '원하는 항목을 찾을 수 없음' 메시지에서 '추가 도구 및 기능 설치' 링크](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > 그런 다음, Visual Studio 설치 관리자에서 **.NET Core 플랫폼 간 개발** 워크로드를 선택합니다.
   >
   > ![Visual Studio Installer에서 .NET Core 플랫폼 간 개발 워크로드](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > 그런 다음, Visual Studio 설치 관리자에서 **수정** 단추를 선택합니다. 작업 내용을 저장하라는 메시지가 나타날 수 있습니다. 그럴 경우 그렇게 하세요. 다음으로, **계속**을 선택하여 워크로드를 설치합니다. 그런 다음, 이 "[프로젝트 만들기](#create-a-project)" 프로시저의 2단계로 돌아갑니다.

1. **새 프로젝트 구성** 창에서 **프로젝트 이름** 상자에 *WhatIsYourName*을 입력합니다. 그런 다음, **만들기**를 선택합니다.

   !['새 프로젝트 구성' 창에서 프로젝트의 이름을 'WhatIsYourName'으로 지정합니다.](./media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio에서 새 프로젝트를 엽니다.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>"What Is Your Name" 애플리케이션 만들기

사용자 이름 입력을 요청한 다음 날짜 및 시간과 함께 해당 이름을 표시하는 앱을 만들어 보겠습니다. 방법은 다음과 같습니다.

 ::: moniker range="vs-2017"

1. *WhatIsYourName* 프로젝트가 열려 있지 않으면 엽니다.

1. `Sub Main(args As String())` 줄 다음, `End Sub` 줄 앞에 있는 여는 대괄호 바로 뒤에 다음 Visual Basic 코드를 입력합니다.

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    이 코드는 기존 <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> 및 <xref:System.Console.ReadKey%2A> 문을 대체합니다.

   ![What Is Your Name 코드를 표시하는 코드 창](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. 녹색 **시작** 단추를 사용하거나 **F5**를 눌러 첫 번째 앱을 빌드하고 실행합니다.

1. 콘솔 창이 열리면 자신의 이름을 입력합니다. 콘솔 창이 다음 스크린샷과 유사하게 표시될 것입니다.

   ![What Is Your Name, 날짜 및 시간, Press any key to continue message를 표시하는 콘솔 창](media/vb-console-what-name.png)

1. 콘솔 창을 닫으려면 아무 키나 누릅니다.

::: moniker-end

::: moniker range="vs-2019"

1. *WhatIsYourName* 프로젝트에서 `Sub Main(args As String())` 줄을 따르는 `End Sub` 줄 앞에 오는 여는 대괄호 바로 뒤에 다음 Visual Basic 코드를 입력합니다.

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    이 코드는 기존 <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> 및 <xref:System.Console.ReadKey%2A> 문을 대체합니다.

   ![What Is Your Name 코드를 표시하는 코드 창](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. 녹색 **시작** 단추를 사용하거나 **F5**를 눌러 첫 번째 앱을 빌드하고 실행합니다.

1. 콘솔 창이 열리면 자신의 이름을 입력합니다. 콘솔 창이 다음 스크린샷과 유사하게 표시될 것입니다.

   ![What Is Your Name, 날짜 및 시간, Press any key to continue message를 표시하는 콘솔 창](media/vb-console-what-name.png)

1. 콘솔 창을 닫으려면 아무 키나 누릅니다.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>"Calculate This" 애플리케이션 만들기

::: moniker range="vs-2017"

1. Visual Studio 2017을 열고 상단 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

1. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual Basic**을 확장한 후 **.NET Core**를 선택합니다. 가운데 창에서 **콘솔 앱(.NET Core)** 을 선택합니다. 그런 다음 파일 이름을 *CalculateThis*로 지정합니다.

1. `Module Program` 줄과 `End Module` 줄 사이에 다음 코드를 입력합니다.

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   코드 창은 다음 스크린샷과 유사하게 표시될 것입니다.

   ![CalculateThis 코드를 표시하는 코드 창](media/vb-codewindow-calculate-this.png)

1. **CalculateThis**를 클릭하여 프로그램을 실행합니다. 콘솔 창이 다음 스크린샷과 유사하게 표시될 것입니다.

    ![수행할 작업을 선택하는 프롬프트가 포함된 CalculateThis 앱이 표시된 콘솔 창.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. 시작 창에서 **새 프로젝트 만들기**를 선택합니다. 

1. **새 프로젝트 만들기** 창에서 검색 상자에 *콘솔*을 입력합니다. 그런 다음, 언어 목록에서 **Visual Basic**을 선택한 다음, 플랫폼 목록에서 **Windows**를 선택합니다. 

1. 언어 및 플랫폼 필터를 적용한 후 **콘솔 앱(.NET Core)** 템플릿을 선택한 후, **다음**을 선택합니다.

   그런 다음 **새 프로젝트 구성** 창에서 **프로젝트 이름** 상자에 *CalculateThis*를 입력합니다. 다음으로, **만들기**를 선택합니다.

1. `Module Program` 줄과 `End Module` 줄 사이에 다음 코드를 입력합니다.

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   코드 창은 다음 스크린샷과 유사하게 표시될 것입니다.

   ![CalculateThis 코드를 표시하는 코드 창](media/vb-codewindow-calculate-this.png)

1. **CalculateThis**를 클릭하여 프로그램을 실행합니다. 콘솔 창이 다음 스크린샷과 유사하게 표시될 것입니다.

    ![수행할 작업을 선택하는 프롬프트가 포함된 CalculateThis 앱이 표시된 콘솔 창.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>빠른 답변 FAQ

몇 가지 주요 개념을 강조 표시하는 빠른 FAQ는 다음과 같습니다.

### <a name="what-is-visual-basic"></a>Visual Basic이란?

Visual Basic은 쉽게 익히도록 설계된 형식이 안전한 프로그래밍 언어입니다. BASIC, 즉 Beginner's All-purpose Symbolic Instruction Code(초보자를 위한 범용 기호 명령 코드)에서 파생되었습니다.

### <a name="what-is-visual-studio"></a>Visual Studio란?

Visual Studio는 개발자를 위한 통합 개발 생산성 도구입니다. 프로그램과 애플리케이션을 만드는 데 사용할 수 있는 프로그램으로 생각하면 됩니다.

### <a name="what-is-a-console-app"></a>콘솔 앱이란?

콘솔 앱은 입력을 받고 명령줄 창, 즉 콘솔에 출력을 표시합니다.

### <a name="what-is-net-core"></a>.NET Core란?

.NET Core는 .NET Framework의 다음 진화 단계입니다. NET Framework는 프로그래밍 언어 전체에서 코드를 공유할 수 있게 했고 .NET Core는 플랫폼 간에 코드를 공유하는 기능을 더합니다. 게다가 오픈 소스입니다. .NET Framework와 .NET Core 모두에는 미리 작성된 기능과 CLR(공통 언어 런타임) 라이브러리가 포함되어 있어 코드를 실행하는 가상 머신 역할을 합니다.

## <a name="next-steps"></a>다음 단계

축하합니다. 이 자습서를 마쳤습니다. 자세히 알아보려면 계속 다음 자습서를 참조하세요.

> [!div class="nextstepaction"]
> [Visual Studio에서 Visual Basic 및 .NET Core SDK를 사용하여 라이브러리 빌드](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>추가 정보

* [Visual Basic 언어 연습](/dotnet/visual-basic/walkthroughs)
* [Visual Basic 언어 참조](/dotnet/visual-basic/language-reference/index)
* [Visual Basic 코드 파일에 대한 IntelliSense](../../ide/visual-basic-specific-intellisense.md)
