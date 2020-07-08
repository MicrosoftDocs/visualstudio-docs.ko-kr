---
title: 자습서 - Docker Compose를 사용하여 다중 컨테이너 앱 만들기
description: Mac용 Visual Studio에서 둘 이상의 컨테이너를 관리하고 컨테이너 간에 통신하는 방법을 알아봅니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.topic: tutorial
ms.openlocfilehash: 03adc2385c202710425fbc8e6b12c832526b5f90
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85938953"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Docker Compose를 사용하여 다중 컨테이너 앱 만들기

이 자습서에서는 Mac용 Visual Studio에서 둘 이상의 컨테이너를 관리하고, Docker Compose를 사용할 때 컨테이너 간에 통신하는 방법을 알아봅니다.

## <a name="prerequisites"></a>사전 요구 사항

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac용 Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>ASP.NET Core 웹 애플리케이션을 만들고 Docker 지원 추가

1. **파일 > 새 솔루션**으로 이동하여 새 솔루션을 만듭니다.
1. **.NET Core > 앱**에서 **웹 애플리케이션** 템플릿을 선택합니다. ![새 ASP.NET 애플리케이션 만들기](media/docker-quickstart-1.png)
1. 대상 프레임워크를 선택합니다. 이 예제에서는 .NET Core 2.2를 사용합니다. ![대상 프레임워크 설정](media/docker-quickstart-2.png)
1. 프로젝트 이름(이 예제에서는 _DockerDemoFrontEnd_), 솔루션 이름(_DockerDemo_) 등의 프로젝트 정보를 입력합니다. 생성된 프로젝트에는 ASP.NET Core 웹 사이트를 빌드 및 실행하는 데 필요한 모든 기본 사항이 포함되어 있습니다.
1. Solution Pad에서 DockerDemoFrontEnd 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가 > Docker 지원 추가**를 선택합니다. ![Docker 지원 추가](media/docker-quickstart-3.png)

Mac용 Visual Studio에서 **docker-compose**라는 새 프로젝트를 솔루션에 자동으로 추가하고, 기존 프로젝트에 **Dockerfile**을 추가합니다.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>ASP.NET Core Web API를 만들고 Docker 지원 추가

다음으로, 백 엔드 API 역할을 할 두 번째 프로젝트를 만들겠습니다. **.NET Core API** 템플릿에는 RESTful 요청을 처리할 수 있는 컨트롤러가 포함되어 있습니다.

1. 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가 > 새 프로젝트 추가**를 선택하여 기존 솔루션에 새 프로젝트를 추가합니다.
1. **.NET Core > 앱**에서 **API** 템플릿을 선택합니다.
1. 대상 프레임워크를 선택합니다. 이 예제에서는 .NET Core 2.2를 사용합니다.
1. 프로젝트 이름(이 예제에서는 _DockerDemoAPI_) 등의 프로젝트 정보를 입력합니다.
1. 프로젝트가 생성되면, Solution Pad로 이동하여 DockerDemoAPI 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가 > Docker 지원 추가**를 선택합니다.

**docker-compose** 프로젝트의 **docker-compose.yml** 파일이 기존 웹앱 프로젝트와 함께 API 프로젝트를 포함하도록 자동으로 업데이트됩니다. **docker-compose** 프로젝트를 빌드 및 실행하는 경우, 각 프로젝트가 개별 Docker 컨테이너에 배포됩니다.

```
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  dockerdemoapi:
    image: ${DOCKER_REGISTRY-}dockerdemoapi
    build:
      context: .
      dockerfile: DockerDemoAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>두 개의 컨테이너 통합

이제 솔루션에 두 개의 ASP.NET 프로젝트가 있으며, 둘 다 Docker를 지원하도록 구성되었습니다. 다음으로, 일부 코드를 추가해야 합니다.

1. `DockerDemoFrontEnd` 프로젝트에서 *Index.cshtml.cs* 파일을 열고, `OnGet` 메서드를 다음 코드로 바꿉니다.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://dockerdemoapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

1. *Index.cshtml* 파일에 `ViewData["Message"]`를 표시할 줄을 추가하여 파일이 다음 코드와 같이 표시되도록 합니다.

      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }

      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. 이제 Web API 프로젝트의 값 컨트롤러에 코드를 추가하여 *webfrontend*에서 추가한 호출에 대해 API에서 반환되는 메시지를 사용자 지정합니다.

      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. `docker-compose` 프로젝트를 시작 프로젝트로 설정하고 **실행 > 디버깅 시작**으로 이동합니다. 모두 제대로 구성된 경우 “Hello from webfrontend and webapi (with value 1).” 메시지가 표시됩니다.

![Docker 다중 컨테이너 솔루션 실행](media/docker-multicontainer-debug.png)
