---
title: Docker Compose 및 ASP.NET Core를 사용하는 다중 컨테이너 자습서
author: ghogen
description: Docker Compose에서 여러 컨테이너를 사용하는 방법을 알아봅니다.
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b9e1a2fc7c9027c34aeb8a0e0d1d44fdb0211e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027326"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>자습서: Docker Compose를 사용하여 다중 컨테이너 앱 만들기

이 자습서에서는 Visual Studio 컨테이너 도구를 사용할 때 둘 이상의 컨테이너를 관리하고 컨테이너 간에 통신하는 방법을 알아봅니다.  여러 컨테이너를 관리하려면 ‘컨테이너 오케스트레이션’이 필요하며 Docker Compose, Kubernetes 또는 Service Fabric과 같은 오케스트레이터가 필요합니다.  이 예제에서는 Docker Compose를 사용합니다. Docker Compose는 개발 주기 과정에서 로컬 디버깅 및 테스트에 유용합니다.

## <a name="prerequisites"></a>사전 요구 사항

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **웹 개발**, **Azure Tools** 워크로드 또는 **.NET Core 플랫폼 간 개발** 워크로드가 설치된 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **웹 개발**, **Azure 도구** 워크로드 및/또는 **.NET Core 플랫폼 간 개발** 워크로드가 설치된 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 2.2를 사용하여 개발하기 위한 [.NET Core 2.2 개발 도구](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* .NET Core 3.1을 사용하여 개발하기 위한 [.NET Core 3 개발 도구](https://dotnet.microsoft.com/download/dotnet-core/3.1)
::: moniker-end

## <a name="create-a-web-application-project"></a>웹 애플리케이션 프로젝트 만들기

Visual Studio에서 `WebFrontEnd`라는 **ASP.NET Core 웹 애플리케이션** 프로젝트를 만듭니다. **웹 애플리케이션**을 선택하여 Razor Pages로 웹 애플리케이션을 만듭니다. 
  
::: moniker range="vs-2017"

**Docker 지원 사용**을 선택하지 않습니다. Docker 지원은 나중에 추가하겠습니다.

![웹 프로젝트 만들기 스크린샷](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![웹 프로젝트 만들기 스크린샷](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

**Docker 지원 사용**을 선택하지 않습니다. Docker 지원은 나중에 추가하겠습니다.

![웹 프로젝트 만들기 스크린샷](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Web API 프로젝트 만들기

동일한 솔루션에 프로젝트를 추가하고 이름을 *MyWebAPI*로 지정합니다. 프로젝트 형식으로 **API**를 선택하고 **HTTPS에 대한 구성** 확인란의 선택을 취소합니다. 이 설계에서는 클라이언트와의 통신에만 SSL을 사용하고, 동일한 웹 애플리케이션의 컨테이너 간 통신에는 사용하지 않습니다. `WebFrontEnd`는 HTTPS만 필요하며 이 예제의 코드에서는 해당 확인란의 선택을 취소했다고 가정합니다.

::: moniker range="vs-2017"
   ![Web API 프로젝트 만들기 스크린샷](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Web API 프로젝트 만들기 스크린샷](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Web API를 호출하는 코드 추가

1. `WebFrontEnd` 프로젝트에서 *Index.cshtml.cs* 파일을 열고, `OnGet` 메서드를 다음 코드로 바꿉니다.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > 실제 코드에서는 모든 요청 후에 `HttpClient`를 삭제하면 안 됩니다. 모범 사례는 [HttpClientFactory를 사용하여 복원력 있는 HTTP 요청 구현](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)을 참조하세요.

   Visual Studio 2019 이상의 .NET Core 3.1에서는 Web API 템플릿에서 WeatherForecast API를 사용하므로 해당 줄의 주석 처리를 제거하고 ASP.NET 2.x에 대한 줄을 주석으로 처리합니다.

1. *Index.cshtml* 파일에 `ViewData["Message"]`를 표시할 줄을 추가하여 파일이 다음 코드와 같이 표시되도록 합니다.
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (ASP.NET 2.x만 해당) 이제 Web API 프로젝트의 값 컨트롤러에 코드를 추가하여 *webfrontend*에서 추가한 호출에 대해 API에서 반환되는 메시지를 사용자 지정합니다.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    .NET Core 3.1에서는 이미 있는 WeatherForecast API를 사용할 수 있기 때문에 필요하지 않습니다. 그러나 이 코드는 HTTPS가 아닌 HTTP를 사용하여 Web API를 호출하기 때문에 *Startup.cs*의 `Configure` 메서드에서 <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*>에 대한 호출을 주석 처리해야 합니다.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. `WebFrontEnd` 프로젝트에서 **추가 > 컨테이너 오케스트레이터 지원**을 선택합니다. **Docker 지원 옵션** 대화 상자가 나타납니다.

1. **Docker Compose**를 선택합니다.

1. 대상 OS(예: Linux)를 선택합니다.

   ![대상 OS 선택 스크린샷](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio에서 솔루션의 **docker-compose** 노드에 *docker-compose.yml* 파일과 *.dockerignore* 파일을 만들고, 해당 프로젝트가 굵은 글꼴로 표시되어 시작 프로젝트임을 나타냅니다.

   ![docker-compose 프로젝트가 추가된 솔루션 탐색기 스크린샷](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *docker-compose.yml*은 다음과 같이 표시됩니다.

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   *.dockerignore* 파일에는 Docker에서 컨테이너에 포함하지 않을 파일 형식과 확장명이 포함되어 있습니다. 이러한 파일은 일반적으로 개발 환경 및 소스 제어와 연결되며, 개발 중인 앱이나 서비스의 일부가 아닙니다.

   실행 중인 명령에 대한 자세한 내용은 출력 창의 **컨테이너 도구** 섹션을 참조하세요.  명령줄 도구 docker-compose가 런타임 컨테이너를 구성하고 만드는 데 사용되는 것을 확인할 수 있습니다.

1. Web API 프로젝트에서 다시 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **컨테이너 오케스트레이터 지원**을 선택합니다. **Docker Compose**를 선택하고 동일한 대상 OS를 선택합니다.  

    > [!NOTE]
    > 이 단계에서 Visual Studio는 Dockerfile을 만들도록 제안합니다. Docker 지원이 이미 포함된 프로젝트에서 이 작업을 수행하면, 기존 Dockerfile을 덮어쓸지 여부를 묻는 메시지가 표시됩니다. Dockerfile의 변경 내용을 유지하려면 아니요를 선택합니다.

    Visual Studio에서 docker compose YML 파일을 일부 변경합니다. 이제 두 서비스가 모두 포함되었습니다.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. 지금 로컬에서 사이트를 실행(F5 또는 Ctrl+F5)하여 예상대로 작동하는지 확인합니다. .NET Core 2.x 버전에서 모두 제대로 구성되었으면 "Hello from webfrontend and webapi (with value 1)" 메시지가 표시됩니다.  .NET Core 3을 사용하여 날씨 예측 데이터를 볼 수 있습니다.

   컨테이너 오케스트레이션을 추가할 때 사용하는 첫 번째 프로젝트는 실행하거나 디버그할 때 시작되도록 설정되었습니다. **프로젝트 속성**에서 docker-compose 프로젝트의 시작 작업을 구성할 수 있습니다.  docker-compose 프로젝트 노드에서 마우스 오른쪽 단추를 클릭하여 상황에 맞는 메뉴를 열고 **속성**을 선택하거나, Alt+Enter를 사용합니다.  다음 스크린샷은 여기서 사용된 솔루션에 대해 지정하려는 속성을 보여 줍니다.  예를 들어 **서비스 URL** 속성을 사용자 지정하여 로드되는 페이지를 변경할 수 있습니다.

   ![docker-compose 프로젝트 속성 스크린샷](media/tutorial-multicontainer/launch-action.png)

   시작될 때 표시되는 내용은 다음과 같습니다(.NET Core 2.x 버전).

   ![웹앱 실행 스크린샷](media/tutorial-multicontainer/webfrontend.png)

   .NET 3.1용 웹앱은 JSON 형식의 날씨 데이터를 표시합니다.

## <a name="next-steps"></a>다음 단계

[Azure에 컨테이너](/azure/containers)를 배포하는 옵션을 확인합니다.

## <a name="see-also"></a>참조
  
[Docker Compose](https://docs.docker.com/compose/)  
[컨테이너 도구](/visualstudio/containers/)
