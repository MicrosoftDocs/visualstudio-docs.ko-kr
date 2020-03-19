---
title: 로컬 Docker 컨테이너에서 앱 디버그 | Microsoft Docs
description: 로컬 Docker 컨테이너에서 실행 중인 앱을 수정하고, 편집 및 새로 고침을 통해 컨테이너를 새로 고치고, 디버깅 중단점을 설정하는 방법을 알아봅니다.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 9f1d80d540e9a25a3ef62ee0819c6f6655b9b3ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916527"
---
# <a name="debug-apps-in-a-local-docker-container"></a>로컬 Docker 컨테이너에서 앱 디버그

Visual Studio는 애플리케이션을 Docker 컨테이너에서 개발하고 로컬로 유효성을 검사하는 일관된 방법을 제공합니다. Docker가 설치된 로컬 Windows 데스크톱에서 실행되는 Linux 또는 Windows 컨테이너에서 앱을 실행하고 디버그할 수 있으며, 코드를 변경할 때마다 컨테이너를 다시 시작하지 않아도 됩니다.

이 문서에서는 Visual Studio를 사용하여 로컬 Docker 컨테이너에서 앱을 시작하고 변경한 다음, 브라우저를 새로 고쳐 변경 내용을 확인하는 방법을 설명합니다. 또한 이 문서에서는 컨테이너화된 앱의 디버깅을 위한 중단점 설정 방법도 보여 줍니다. 지원되는 프로젝트 형식에는 .NET Framework 및 .NET Core 웹 및 콘솔 앱이 포함됩니다. 이 문서에서는 ASP.NET Core 웹앱 및 .NET Framework 콘솔 앱을 사용합니다.

지원되는 형식의 프로젝트가 이미 있는 경우 Visual Studio가 Dockerfile을 만들고 프로젝트를 컨테이너에서 실행되도록 구성할 수 있습니다. [Visual Studio의 컨테이너 도구](overview.md)를 참조하세요.

## <a name="prerequisites"></a>사전 요구 사항

로컬 Docker 컨테이너에서 앱을 디버그하려면 다음 도구를 설치해야 합니다.

::: moniker range="vs-2017"

* 웹 개발 워크로드가 설치된 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

* 웹 개발 워크로드가 설치된 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

로컬에서 Docker 컨테이너를 실행하려면 로컬 Docker 클라이언트가 있어야 합니다. Hyper-V를 사용하지 않도록 설정해야 하는 [Docker 도구 상자](https://www.docker.com/products/docker-toolbox)를 사용할 수 있습니다. Hyper-V를 사용하고 Windows 10이 필요한 [Windows용 Docker](https://www.docker.com/get-docker)를 사용할 수도 있습니다.

Docker 컨테이너는 .NET Framework 및 .NET Core 프로젝트에 사용할 수 있습니다. 두 가지 예제를 살펴보겠습니다. 먼저 .NET Core 웹앱을 살펴본 다음, .NET Framework 콘솔 앱을 살펴봅시다.

## <a name="create-a-web-app"></a>웹앱 만들기

프로젝트가 있고 [개요](overview.md)에 설명된 대로 Docker 지원을 추가한 경우 이 섹션을 건너뜁니다.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>코드 편집 및 새로 고침

변경 작업을 빠르게 반복하기 위해 컨테이너에서 애플리케이션을 시작할 수 있습니다. 그런 다음, IIS Express에서와같이 계속 변경하면서 변경 내용을 확인합니다.

1. Docker가 사용 중인 컨테이너 유형(Linux 또는 Windows)을 사용하도록 설정되어 있는지 확인합니다. 작업 표시줄에서 Docker 아이콘을 마우스 오른쪽 단추로 클릭하고 **Linux 컨테이너로 전환** 또는 **Windows 컨테이너로 전환**을 적절히 선택합니다.

1. (.NET Core 3 이상에만 해당) 이 섹션에 설명된 대로 코드를 편집하고 실행 중인 사이트를 새로 고치는 기능은 .NET Core > = 3.0의 기본 템플릿에서 사용할 수 없습니다. 이 기능을 사용하도록 설정하려면 NuGet 패키지 [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)를 추가해야 합니다. *Startup.cs*에서 `IMvcBuilder.AddRazorRuntimeCompilation` 메서드의 코드에 `ConfigureServices` 확장 메서드에 대한 호출을 추가합니다. DEBUG 모드에서만 이 기능을 사용할 수 있으므로 다음과 같이 코딩하세요.

    ```csharp
    public IWebHostEnvironment Env { get; set; }
    
    public void ConfigureServices(IServiceCollection services)
    {
        IMvcBuilder builder = services.AddRazorPages();
    
    #if DEBUG
        if (Env.IsDevelopment())
        {
            builder.AddRazorRuntimeCompilation();
        }
    #endif
    
        // code omitted for brevity
    }
    ```

   자세한 내용은 [ASP.NET Core의 Razor 파일 컴파일](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1)을 참조하세요.

1. **솔루션 구성**을 **디버그**로 설정합니다. **Ctrl**+**F5**를 눌러 Docker 이미지를 빌드하고 로컬에서 실행합니다.

    컨테이너 이미지가 빌드되고 Docker 컨테이너에서 실행되면 Visual Studio가 기본 브라우저에서 웹앱을 시작합니다.

1. ‘인덱스’ 페이지로 이동합니다.  이 페이지를 변경하겠습니다.
1. Visual Studio로 돌아가서 *Index.cshtml*을 엽니다.
1. 파일의 끝에 다음 HTML 콘텐츠를 추가하고 변경 내용을 저장합니다.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. 출력 창에서 .NET 빌드가 완료되고 다음 줄이 표시되면, 브라우저로 다시 전환하고 페이지를 새로 고칩니다.

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

변경 내용이 적용되었습니다.

### <a name="debug-with-breakpoints"></a>중단점으로 디버깅

변경 시 추가 검사가 필요한 경우가 많습니다. 이 작업을 위해 Visual Studio의 디버깅 기능을 사용할 수 있습니다.

1. Visual Studio에서 *Index.cshtml.cs*를 엽니다.
2. `OnGet` 메서드의 내용을 다음 코드로 바꿉니다.

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. 코드 줄의 왼쪽에 중단점을 설정합니다.
4. 디버깅을 시작하고 중단점에 적중하려면 F5 키를 누릅니다.
5. Visual Studio로 전환하여 중단점을 살펴봅니다. 값을 검사합니다.

   ![중단점](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>.NET Framework 콘솔 앱 만들기

.NET Framework 콘솔 앱 프로젝트를 사용하는 경우, 오케스트레이션 없이 Docker 지원을 추가하는 옵션이 지원되지 않습니다. 단일 Docker 프로젝트만 사용하는 경우에도 다음 프로시저를 사용할 수 있습니다.

1. .NET Framework 콘솔 앱 프로젝트를 새로 만듭니다.
1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **컨테이너 오케스트레이션 지원**을 선택합니다.  표시되는 대화 상자에서 **Docker Compose**를 선택합니다. Dockerfile이 프로젝트에 추가되고, 관련 지원 파일을 포함하는 Docker Compose 프로젝트가 추가됩니다.

### <a name="debug-with-breakpoints"></a>중단점으로 디버깅

1. 솔루션 탐색기에서 *Program.cs*를 엽니다.
2. `Main` 메서드의 내용을 다음 코드로 바꿉니다.

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. 코드 줄의 왼쪽에 중단점을 설정합니다.
4. F5 키를 눌러 디버깅을 시작하고 중단점에 적중합니다.
5. Visual Studio로 전환하여 중단점을 살펴보고 값을 검사합니다.

   ![중단점](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>컨테이너 재사용

개발 주기 중에 Dockerfile을 변경하는 경우에만 Visual Studio에서 컨테이너 이미지와 컨테이너 자체를 다시 빌드합니다. Dockerfile을 변경하지 않으면 Visual Studio는 이전 실행의 컨테이너를 재사용합니다.

컨테이너를 수동으로 수정했으며 새 컨테이너 이미지로 다시 시작하려면, Visual Studio에서 **빌드** > **정리** 명령을 사용하고 일반적인 방법으로 빌드합니다.

## <a name="troubleshoot"></a>문제 해결

[Visual Studio Docker 개발 문제 해결](troubleshooting-docker-errors.md) 방법을 알아봅니다.

## <a name="next-steps"></a>다음 단계

[Visual Studio에서 컨테이너화된 앱을 빌드하는 방법](container-build.md)을 읽어 자세한 내용을 확인하세요.

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Visual Studio, Windows 및 Azure와 함께 Docker에 대해 자세히 알아보기

* [Visual Studio를 사용한 컨테이너 개발](/visualstudio/containers)에 대해 자세히 알아봅니다.
* Docker 컨테이너를 빌드하고 배포하려면 [Azure Pipelines용 Docker 통합](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker)을 참조하세요.
* Windows Server 및 Nano Server 문서의 인덱스는 [Windows 컨테이너 정보](/virtualization/windowscontainers/)를 참조하세요.
* [Azure Container Service](https://azure.microsoft.com/services/kubernetes-service/)에 대해 알아보고 [Azure Kubernetes Service 설명서](/azure/aks)를 검토합니다.
