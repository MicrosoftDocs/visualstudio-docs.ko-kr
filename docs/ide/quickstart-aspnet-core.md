---
title: C#에서 ASP.NET Core 웹앱 만들기
description: C# 및 ASP.NET Core를 사용하여 단계별로 Visual Studio에서 간단한 Hello World 웹앱을 만드는 방법을 알아봅니다.
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1873c11d8f2e6243a0dc0f867e579f1927cd1607
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579967"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>빠른 시작: Visual Studio를 사용하여 첫 번째 ASP.NET Core 웹앱 만들기

이 5~10분 진행되는 Visual Studio를 사용하는 방법에 대한 소개에서 ASP.NET 프로젝트 템플릿과 C# 프로그래밍 언어를 사용하여 간단한 "Hello World" 웹앱을 만듭니다.

## <a name="before-you-begin"></a>시작하기 전 주의 사항

### <a name="install-visual-studio"></a>Visual Studio 설치

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

### <a name="choose-your-theme-optional"></a>테마 선택(선택 사항)

이 빠른 시작 자습서에는 어두운 테마를 사용하는 스크린샷이 포함되어 있습니다. 어두운 테마를 사용하지 않지만 원하는 경우 [Visual Studio IDE 및 편집기 개인 설정](quickstart-personalize-the-ide.md) 페이지에서 참조하여 방법을 알아봅니다.

## <a name="create-a-project"></a>프로젝트 만들기

시작하려면 ASP.NET Core 웹 애플리케이션 프로젝트를 만듭니다. 또한 프로젝트 형식에는 어떤 것을 추가하기도 전에 웹앱을 만들 수 있는 모든 템플릿 파일이 함께 제공됩니다!

::: moniker range="vs-2017"

1. Visual Studio 2017을 엽니다.

1. 상단 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

1. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#** 을 확장하고 **.NET Core**를 선택합니다. 가운데 창에서 **ASP.NET Core 웹 애플리케이션**을 선택합니다. <br/><br/>그런 다음, 파일 이름을 `HelloWorld`로 지정하고 **확인**을 선택합니다.

   ![C#용 새 ASP.NET Core 웹 애플리케이션 프로젝트 만들기](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > **.NET Core** 프로젝트 템플릿 범주가 표시되지 않으면 왼쪽 창에서 **Visual Studio 설치 관리자 열기** 링크를 선택합니다. (표시 설정에 따라 스크롤해야 볼 수 있습니다.)
   >
   > ![새 프로젝트 대화 상자에서 Visual Studio 설치 관리자 열기](../ide/media/open-visual-studio-installer.png)
   >
   > Visual Studio 설치 관리자가 시작됩니다. **ASP.NET 및 웹 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.
   >
   > ![VS 설치 관리자에서 ASP.NET 워크로드](../ide/media/quickstart-aspnet-workload.png)
   >
   > (새 워크로드를 계속 설치하려면 먼저 Visual Studio를 닫아야 할 수 있습니다.)

1. **새 ASP.NET Core 웹 애플리케이션** 대화 상자의 상단 드롭다운 메뉴에서 **ASP.NET Core 2.1**을 선택합니다. 그런 다음, **웹 애플리케이션**을 선택한 후, **확인**을 선택합니다.

   ![새 ASP.NET Core 웹 애플리케이션 대화 상자](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > **ASP.NET Core 2.1**이 보이지 않을 경우 Visual Studio의 최신 릴리스를 실행하고 있는지 확인합니다. 설치를 업데이트하는 방법에 대한 자세한 내용은 [Visual Studio를 최신 릴리스로 업데이트](../install/update-visual-studio.md) 페이지를 참조하세요.

곧 Visual Studio에서 프로젝트 파일이 열립니다.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio를 엽니다.

1. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   !['새 프로젝트 만들기' 창 보기](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **새 프로젝트 만들기** 창에서 검색 상자에 *ASP.NET*을 입력합니다. 그런 다음, 언어 목록에서 **C#** 을 선택한 다음, 플랫폼 목록에서 **Windows**를 선택합니다.

   언어 및 플랫폼 필터를 적용한 후 **ASP.NET Core 웹 애플리케이션** 템플릿을 선택한 후, **다음**을 선택합니다.

   ![ASP.NET Core 웹 애플리케이션에 대한 C# 템플릿을 선택합니다.](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > **ASP.NET Core 웹 애플리케이션** 템플릿이 표시되지 않으면 **새 프로젝트를 만들기** 창에서 설치할 수 있습니다. **원하는 항목을 찾을 수 없나요?** 메시지에서 **추가 도구 및 기능 설치** 링크를 선택합니다.
   >
   > !['새 프로젝트 만들기' 창의 '원하는 항목을 찾을 수 없음' 메시지에서 '추가 도구 및 기능 설치' 링크](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > 그런 다음, Visual Studio 설치 관리자에서 **ASP.NET 및 웹 개발** 워크로드를 선택합니다.
   >
   > ![Visual Studio 설치 관리자의 ASP.NET Core 웹 애플리케이션 워크로드](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > 그런 다음, Visual Studio 설치 관리자에서 **수정** 단추를 선택합니다. 작업 내용을 저장하라는 메시지가 나타날 수 있습니다. 그럴 경우 그렇게 하세요. 다음으로, **계속**을 선택하여 워크로드를 설치합니다. 그런 다음, 이 "[프로젝트 만들기](#create-a-project)" 프로시저의 2단계로 돌아갑니다.

1. **새 프로젝트 구성** 창에서 **프로젝트 이름** 상자에 *HelloWorld*를 입력합니다. 그런 다음, **만들기**를 선택합니다.

   !['새 프로젝트 구성' 창에서 프로젝트의 이름을 'HelloWorld'로 지정합니다.](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. **새 ASP.NET Core 웹 애플리케이션 만들기** 창의 위쪽 드롭다운 메뉴에 **ASP.NET Core 3.0**이 표시되는지 확인합니다. 그런 다음, 예제 Razor Pages가 포함된 **웹 애플리케이션**을 선택합니다. 다음으로, **만들기**를 선택합니다.

   !['새 ASP.NET Core 웹 애플리케이션 만들기' 창](../get-started/csharp/media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio에서 새 프로젝트를 엽니다.

::: moniker-end

## <a name="create-and-run-the-app"></a>앱 만들기 및 실행

::: moniker range="vs-2017"

1. **솔루션 탐색기**에서 **Pages** 폴더를 확장한 다음, **About.cshtml**을 선택합니다.

   ![솔루션 탐색기에서 About.cshtml 파일 선택](../ide/media/csharp-aspnet-about-page-html-file.png)

   이 파일은 웹 브라우저에서 실행되는 웹앱에서 **정보**라는 페이지에 해당합니다.

   ![웹앱의 정보 페이지](../ide/media/csharp-aspnet-about-page.png)

   **정보** 페이지의 “추가 정보” 영역에 대한 HTML 코드가 편집기에 표시됩니다.

   ![Visual Studio 편집기의 추가 정보 영역에 대한 HTML 코드](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. “추가 정보” 텍스트를 “**Hello World!** ”로 변경합니다.

   ![Visual Studio 편집기에서 추가 정보 영역의 기본 HTML 코드를 변경합니다.](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. **솔루션 탐색기**에서 **About.cshtml**을 확장한 다음, **About.cshtml.cs**를 선택합니다. (이 파일은 웹 브라우저의 **정보** 페이지와도 일치합니다.)

   ![솔루션 탐색기에서 About.cshtml 파일 선택](../ide/media/csharp-aspnet-about-page-code-file.png)

   **정보** 페이지의 “애플리케이션 설명” 영역에 대한 텍스트를 포함하는 C# 코드가 편집기에 표시됩니다.

   ![Visual Studio 편집기의 애플리케이션 설명 영역에 대한 C# 코드](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. “애플리케이션 설명” 메시지 텍스트를 “**내 메시지란?** ”으로 변경합니다.

   ![Visual Studio 편집기에서 애플리케이션 설명 영역의 기본 메시지 텍스트 변경](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. **IIS Express**를선 택하거나 **Ctrl**+**F5**를 눌러 앱을 실행하고 웹 브라우저에서 엽니다.

   ![Visual Studio에서 IIS Express 단추 선택](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > **웹 서버 'IIS Express'에 연결할 수 없음**이라는 오류 메시지 또는 SSL 인증서를 언급하는 오류 메시지를 받는 경우 Visual Studio를 닫습니다. 다음으로, 마우스 오른쪽 단추 컨텍스트 메뉴에서 **관리자 권한으로 실행** 옵션을 사용하여 Visual Studio를 엽니다. 그런 다음 애플리케이션을 다시 실행합니다.

1. 웹 브라우저에서 **정보** 페이지에 업데이트된 텍스트가 포함되는지 확인합니다.

   ![변경 내용이 포함된 업데이트된 정보 페이지 표시](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. 웹 브라우저를 닫습니다.

### <a name="review-your-work"></a>작업 검토

다음 애니메이션을 보고 이전 섹션에서 완료한 작업을 확인합니다.

  ![Visual Studio에서 간단한 C# ASP.NET Core 웹앱을 만들고 실행하는 방법을 보여주는 애니메이션 처리된 .gif 파일 보기](../ide/media/csharp-aspnet-animated-hello-world.gif)

이 빠른 시작을 완료한 것을 축하 드립니다! C#, ASP.NET Core 및 Visual Studio IDE(통합 개발 환경)를 이해하는 데 도움이 되었기를 바랍니다.

::: moniker-end

::: moniker range="vs-2019"

1. **솔루션 탐색기**에서 **Pages** 폴더를 확장한 다음, **Index.cshtml**을 선택합니다.

   ![솔루션 탐색기에서 Index.cshtml 파일 선택](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   이 파일은 웹 브라우저에서 실행되는 웹앱에서 **홈**이라는 페이지에 해당합니다.

   ![웹앱의 정보 페이지](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   편집기에 **홈** 페이지에 표시되는 텍스트에 대한 HTML 코드가 표시됩니다.

   ![Visual Studio 편집기의 홈 페이지에 대한 Index.cshtml 파일의 HTML 코드](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. "Welcome"이라는 텍스트를 "**Hello World!** "로 변경합니다.

   ![Visual Studio 편집기에서 기본 HTML 코드를 Welcome이라고 말하는 대신 Hello World라고 말하도록 변경](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. **IIS Express**를선 택하거나 **Ctrl**+**F5**를 눌러 앱을 실행하고 웹 브라우저에서 엽니다.

   ![Visual Studio에서 IIS Express 단추 선택](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > **웹 서버 'IIS Express'에 연결할 수 없음**이라는 오류 메시지 또는 SSL 인증서를 언급하는 오류 메시지를 받는 경우 Visual Studio를 닫습니다. 다음으로, 마우스 오른쪽 단추 컨텍스트 메뉴에서 **관리자 권한으로 실행** 옵션을 사용하여 Visual Studio를 엽니다. 그런 다음 애플리케이션을 다시 실행합니다.

1. 웹 브라우저에서 **홈** 페이지에 업데이트된 텍스트가 포함되는지 확인합니다.

   ![변경 내용이 포함된 업데이트된 홈 페이지 표시](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. 웹 브라우저를 닫습니다.

::: moniker-end

## <a name="next-steps"></a>다음 단계

자세히 알아보려면 계속 다음 자습서를 사용하세요.

> [!div class="nextstepaction"]
> [Visual Studio에서 C# 및 ASP.NET 시작](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>참조

[Visual Studio를 사용하여 Azure App Service에 웹앱 게시](../deployment/quickstart-deploy-to-azure.md)
