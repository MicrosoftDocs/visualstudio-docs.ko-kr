---
title: Visual Studio를 사용하여 첫 번째 C# 콘솔 앱 만들기
titleSuffix: ''
description: Visual Studio에서 C#을 사용하여 간단한 Hello World 콘솔 앱을 만드는 방법을 단계별로 알아봅니다.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 20b2cf2bf12e9b24ca12d0a73b43e4a56e8246f4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579483"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>빠른 시작: Visual Studio를 사용하여 첫 번째 C# 콘솔 앱 만들기

Visual Studio IDE(통합 개발 환경)에 대한 소개는 이 5~10분 분량으로 여기서 콘솔에서 실행되는 간단한 C# 앱을 만듭니다.

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 평가판을 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 평가판을 설치합니다.

::: moniker-end

## <a name="create-a-project"></a>프로젝트 만들기

먼저 C# 애플리케이션 프로젝트를 만듭니다. 아무 것도 추가하지 않아도 필요한 모든 템플릿 파일과 함께 프로젝트 형식이 제공됩니다.

::: moniker range="vs-2017"

1. Visual Studio 2017을 엽니다.

2. 상단 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자의 왼쪽 창에서 **C#** 을 확장한 후 **.NET Core**를 선택합니다. 가운데 창에서 **콘솔 앱(.NET Core)** 을 선택합니다. 프로젝트의 이름을 *HelloWorld*로 지정합니다.

   ![Visual Studio IDE의 새 프로젝트 대화 상자의 콘솔 앱(.NET Core) 프로젝트 템플릿](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     **콘솔 앱(.NET Core)** 템플릿 프로젝트가 표시되지 않으면 **새 프로젝트** 대화 상자의 왼쪽 창에서 **Open Visual Studio 설치 관리자** 링크를 선택합니다.

   ![새 프로젝트 대화 상자에서 Visual Studio 설치 관리자 열기 링크 선택](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Visual Studio 설치 관리자가 시작됩니다. **.NET Core 플랫폼 간 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.

     ![Visual Studio Installer에서 .NET Core 플랫폼 간 개발 워크로드](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   !['새 프로젝트 만들기' 창](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **새 프로젝트 만들기** 창에서 검색 상자에 *콘솔*을 입력합니다. 그런 다음, 언어 목록에서 **C#** 을 선택한 다음, 플랫폼 목록에서 **Windows**를 선택합니다. 

   언어 및 플랫폼 필터를 적용한 후 **콘솔 앱(.NET Core)** 템플릿을 선택한 후, **다음**을 선택합니다.

   ![콘솔 앱(.NET Framework)에 대한 C# 템플릿을 선택합니다.](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **콘솔 앱(.NET Core)** 템플릿이 표시되지 않으면 **새 프로젝트를 만들기** 창에서 설치할 수 있습니다. **원하는 항목을 찾을 수 없나요?** 메시지에서 **추가 도구 및 기능 설치** 링크를 선택합니다.
   >
   > !['새 프로젝트 만들기' 창의 '원하는 항목을 찾을 수 없음' 메시지에서 '추가 도구 및 기능 설치' 링크](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > 그런 다음, Visual Studio 설치 관리자에서 **.NET Core 플랫폼 간 개발** 워크로드를 선택합니다.
   >
   > ![Visual Studio Installer에서 .NET Core 플랫폼 간 개발 워크로드](./media/dot-net-core-xplat-dev-workload.png)
   >
   > 그런 다음, Visual Studio 설치 관리자에서 **수정** 단추를 선택합니다. 작업 내용을 저장하라는 메시지가 나타날 수 있습니다. 그럴 경우 그렇게 하세요. 다음으로, **계속**을 선택하여 워크로드를 설치합니다. 그런 다음, 이 "[프로젝트 만들기](#create-a-project)" 프로시저의 2단계로 돌아갑니다.

1. **새 프로젝트 구성** 창에서 *프로젝트 이름* 상자에 **HelloWorld**를 입력합니다. 그런 다음, **만들기**를 선택합니다.

   !['새 프로젝트 구성' 창에서 프로젝트의 이름을 'HelloWorld'로 지정합니다.](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio에서 새 프로젝트를 엽니다.
   
::: moniker-end

## <a name="create-the-application"></a>애플리케이션 만들기

::: moniker range="vs-2017"

C# 프로젝트 템플릿을 선택하고 프로젝트 이름을 지정한 후에 Visual Studio에서 간단한 “Hello World” 애플리케이션을 만듭니다.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio에는 프로젝트에 기본 "Hello World" 코드가 포함되어 있습니다.

::: moniker-end

(이렇게 하려면 <xref:System.Console.WriteLine%2A> 메서드를 호출하여 리터럴 문자열 "Hello World!"를 콘솔 창에 표시합니다.

   ![템플릿에서 기본 Hello World 코드 보기](../ide/media/csharp-console-helloworld-template.png)

**F5** 키를 누르면 디버그 모드에서 프로그램을 실행할 수 있습니다. 그러나 콘솔 창은 잠깐만 표시되었다가 닫힙니다.

(단일 명령문을 실행한 후에 애플리케이션이 완료되도록 `Main` 메서드가 종료되기 때문에 이 동작이 발생합니다.)

### <a name="add-some-code"></a>일부 코드를 추가합니다.

**Enter** 키를 누를 때까지 콘솔 창이 닫히지 않도록 애플리케이션을 일시 중지하는 일부 코드를 추가하겠습니다.

1. <xref:System.Console.WriteLine%2A> 메서드 호출 바로 다음에 아래 코드를 추가합니다.

   ```csharp
   Console.ReadLine();
   ```

1. 코드 편집기에서 다음과 같이 표시되는지 확인합니다.

   ![Hello World 앱을 일시 중지하는 코드 추가](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>애플리케이션 실행

1. 도구 모음에서 **HelloWorld** 단추를 선택하여 애플리케이션을 디버그 모드로 실행합니다. 또는 **F5** 키를 누르면 됩니다.

   ![Hello World 단추를 선택하여 도구 모음에서 앱을 실행합니다.](../ide/media/csharp-console-hello-world-button.png)

1. 콘솔 창에 앱을 표시합니다.

   ![Hello World!를 표시하는 콘솔 창](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>애플리케이션 닫기

1. **Enter** 키를 눌러 콘솔 창을 닫습니다.

1. Visual Studio에서 **출력** 창을 닫습니다.

   ![Visual Studio에서 출력 창 닫기](../ide/media/csharp-hello-world-close-output-pane.png)

1. Visual Studio를 닫습니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작을 완료한 것을 축하 드립니다! C# 및 Visual Studio IDE를 이해하는 데 도움이 되었기를 바랍니다. 자세히 알아보려면 다음 자습서를 계속 진행하세요.

> [!div class="nextstepaction"]
> [Visual Studio에서 C# 콘솔 앱 시작](../get-started/csharp/tutorial-console.md)
