---
title: '빠른 시작: F#에서 ASP.NET Core 웹 서비스 만들기'
description: F#을 사용하여 단계별로 Visual Studio에서 ASP.NET Core 웹 서비스를 만드는 방법을 알아봅니다.
ms.date: 08/24/2018
ms.topic: quickstart
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 990106f7f3ca97ae38a20170ca6ed2e1d699d4e4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180320"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>빠른 시작: Visual Studio를 사용하여 F\#에서 첫 번째 ASP.NET Core 웹 서비스 만들기

Visual Studio의 F#에 대한 5~10분 분량의 소개에서 F# ASP.NET Core 웹 애플리케이션을 만듭니다.

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

## <a name="create-a-project"></a>프로젝트 만들기

먼저, ASP.NET Core Web API 프로젝트를 만듭니다. 프로젝트 형식에는 무엇인가 추가하기 전에 기능 웹 서비스를 구성하는 템플릿 파일이 포함되어 있습니다.

::: moniker range="vs-2017"

1. Visual Studio를 엽니다.

2. 상단 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자의 왼쪽 차에서 **Visual F#** 을 확장한 다음, **Web**를 선택합니다. 가운데 창에서 **ASP.NET Core 웹 애플리케이션**을 선택한 후 **확인**을 선택합니다.

     **.NET Core** 프로젝트 템플릿 범주가 표시되지 않으면 왼쪽 창에서 **Visual Studio 설치 관리자 열기** 링크를 선택합니다. Visual Studio 설치 관리자가 시작됩니다. **ASP.NET 및 웹 개발** 워크로드를 선택한 후 **수정**을 선택합니다.

     ![VS 설치 관리자에서 ASP.NET 워크로드](../ide/media/quickstart-aspnet-workload.png)

4. **새 ASP.NET Core 웹 애플리케이션** 대화 상자의 상단 드롭다운 메뉴에서 **ASP.NET Core 2.1**을 선택합니다. (목록에 **ASP.NET Core 2.1**이 표시되지 않으면 대화 상자 맨 위에 있는 노란색 표시줄에 나타나는 **다운로드** 링크에 따라 설치합니다.) **확인**을 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio를 엽니다.

2. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

3. **새 프로젝트 만들기** 페이지에서 검색 상자에 **f# web**을 입력하고 **ASP.NET Core 웹 애플리케이션** 프로젝트 템플릿을 선택합니다. **다음**을 선택합니다.

4. **새 프로젝트 구성** 페이지에서 이름을 입력하고 **만들기**를 선택합니다.

5. **새 ASP.NET Core 웹 애플리케이션 만들기** 페이지에서 상단 드롭다운 메뉴의 **ASP.NET Core 2.1**을 선택한 후 **만들기**를 선택합니다.

::: moniker-end

## <a name="explore-the-ide"></a>IDE 탐색

1. **솔루션 탐색기** 도구 모음에서 **컨트롤러** 폴더를 확장한 다음, **ValuesController.fs**를 선택하여 편집기에서 엽니다.

   ![F# Web API 프로젝트에서 확장된 컨트롤러 폴더가 있는 솔루션 탐색기](../ide/media/hello-world-fs-sln-explorer.png)

2. 그런 다음, `Get()` 멤버를 다음과 같이 수정합니다.

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

코드는 간단합니다. F# 값의 배열은 `values` 이름에 바인딩된 다음, ASP.NET Core MVC 프레임워크에 `ActionResult`로 전달됩니다. ASP.NET Core가 나머지 작업을 처리합니다.

편집기에서 다음과 같이 표시됩니다.

![수정된 Get 멤버](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>애플리케이션 실행

1. **Ctrl**+**F5**를 눌러 애플리케이션을 실행하고 웹 브라우저에서 엽니다.

2. 페이지는 `/api/values` 경로로 이동해야 하지만, 그렇지 않은 경우 브라우저에 `https://localhost:44396/api/values`를 입력합니다.

이제 웹 브라우저는 이전에 입력한 내용과 일치하는 JSON을 표시합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작을 완료한 것을 축하 드립니다! F#, ASP.NET Core 및 Visual Studio IDE를 이해하는 데 도움이 되었기를 바랍니다. 공용 서버에서 실행 중인 앱을 보려면 다음 단추를 선택합니다.

> [!div class="nextstepaction"]
> [앱을 Azure App Service에 배포](../deployment/quickstart-deploy-to-azure.md)

F#에 대해 자세히 알아보려면 공식 [F# 가이드](/dotnet/fsharp/index)를 확인하세요.