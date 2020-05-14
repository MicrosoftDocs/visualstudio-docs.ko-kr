---
title: ASP.NET Core 시작
description: 이 문서에서는 설치 및 새 프로젝트 만들기를 포함하여 Mac용 Visual Studio에서 ASP.NET을 시작하는 방법을 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: 5f1a617c5562c4f95fec94ae449f48b681fcb7ef
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543751"
---
# <a name="getting-started-with-aspnet-core"></a>ASP.NET Core 시작

 Mac용 Visual Studio를 사용하면 최신 ASP.NET Core 웹 개발 플랫폼 지원을 통해 앱 서비스를 쉽게 개발할 수 있습니다. ASP.NET Core는 .NET Framework와 런타임의 최신 형태인 .NET Core에서 실행됩니다. 빠른 성능을 위해 조정되고, 작은 설치 크기에 맞게 팩터링되고, Windows뿐 아니라 Linux 및 macOS에서도 실행되도록 다시 빌드되었습니다.

## <a name="installing-net-core"></a>.NET Core 설치

.NET Core 1.1은 Mac용 Visual Studio를 설치할 때 자동으로 설치됩니다.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 ASP.NET Core 앱 만들기

Mac용 Visual Studio를 엽니다. 시작 페이지에서 **새 프로젝트...** 를 선택합니다.

![새 프로젝트 대화 상자](media/asp-net-core-image1.png)

그러면 애플리케이션을 만들 템플릿을 선택할 수 있는 새 프로젝트 대화 상자가 표시됩니다.

ASP.NET Core 애플리케이션 빌드를 시작하기 위해 미리 작성된 템플릿을 제공하는 많은 프로젝트가 있습니다. 이러한 항목은 다음과 같습니다.

- **.NET Core &gt; ASP.NET Core 빈 웹 애플리케이션**
- **.NET Core > ASP.NET Core 웹앱**
- **.NET Core > ASP.NET Core Web API**
- **다중 플랫폼 > 앱 > 연결된 앱**

![ASP.NET 프로젝트 옵션](media/asp-net-core-image11.png)

**ASP.NET Core 빈 웹 애플리케이션**을 선택하고 **다음**을 누릅니다. 프로젝트에 이름을 지정하고 **만들기**를 누릅니다. 그러면 아래 이미지와 비슷하게 표시되는 새로운 ASP.NET Core 앱이 생성됩니다.

![새로운 ASP.NET Core 빈 프로젝트 보기](media/asp-net-core-image4.png)

ASP.NET Core 빈 웹 애플리케이션은 두 개의 기본 파일 **Program.cs** 및 **Startup.cs**가 포함된 웹 애플리케이션을 만듭니다. 또한 ASP.NET Core, .NET Core 프레임워크, 프로젝트를 빌드하는 MSBuild 대상 등 프로젝트의 NuGet 패키지 종속성을 포함하는 종속성 폴더를 만듭니다.

![종속성을 표시하는 Solution Pad](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

프로젝트에서 **Program.cs** 파일을 열고 검사합니다. 앱의 진입점인 `Main` 메서드에서 다음 두 가지 작업이 수행됨을 확인합니다.

```csharp
public static void Main(string[] args)
{
    var host = new WebHostBuilder()
        .UseKestrel()
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

    host.Run();
}
```

ASP.NET Core 앱이 [`WebHostBuilder`](/aspnet/core/fundamentals/hosting) 인스턴스를 통해 호스트를 구성 및 시작하여 main 메서드에서 웹 서버를 만듭니다. 이 작성기는 호스트를 구성할 수 있는 메서드를 제공합니다. 템플릿 앱에서는 다음과 같은 구성이 사용됩니다.

* `UseKestrel`: 앱에서 Kestrel 서버를 사용하도록 지정합니다.
* `UseContentRoot(Directory.GetCurrentDirectory())`: 이 폴더에서 앱을 시작할 때 웹 프로젝트의 루트 폴더를 앱의 콘텐츠 루트로 사용합니다.
* `.UseIISIntegration()`: 앱이 IIS에서 작동하도록 지정합니다. ASP.NET Core와 함께 IIS를 사용하려면 `UseKestrel` 및 `UseIISIntegration`을 지정해야 합니다.
* `.UseStartup<Startup>()`: 시작 클래스를 지정합니다.

  빌드 및 실행 메서드는 앱을 호스트할 IWebHost를 빌드하고 시작하여 들어오는 HTTP 요청을 수신 대기합니다.

### <a name="startupcs"></a>Startup.cs

앱의 시작 클래스는 `WebHostBuilder`의 `UseStartup()` 메서드에서 지정됩니다. 이 클래스에서 요청 처리 파이프라인을 지정하고 모든 서비스를 구성합니다.

프로젝트에서 **Startup.cs** 파일을 열고 검사합니다.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddConsole();

        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            await context.Response.WriteAsync("Hello World!");
        });
    }
}
```

시작 클래스는 항상 다음 규칙을 따라야 합니다.

- 항상 public이어야 합니다.
- 두 개의 public 메서드 `ConfigureServices` 및 `Configure`가 포함되어야 합니다.

`ConfigureServices` 메서드는 앱에서 사용될 서비스를 정의합니다.

`Configure`를 사용하면 [미들웨어](/aspnet/core/fundamentals/middleware)를 통해 요청 파이프라인을 구성할 수 있습니다. ASP.NET 애플리케이션 파이프라인 내에서 요청과 응답을 처리하는 데 사용되는 구성 요소입니다. HTTP 파이프라인은 순서대로 호출되는 많은 요청 대리자로 구성됩니다. 각 대리자는 요청을 직접 처리하거나 다음 대리자에 전달하도록 선택할 수 있습니다.

`IApplicationBuilder`의 `Run`, `Map`, `Use` 메서드를 사용하여 대리자를 구성할 수 있지만, `Run` 메서드는 다음 대리자를 호출하지 않으며 항상 파이프라인의 끝에 사용해야 합니다.

미리 작성된 템플릿의 `Configure` 메서드는 몇 가지 작업을 수행하도록 빌드되었습니다. 첫째, 개발하는 동안 사용할 예외 처리 페이지를 구성합니다. 그런 다음 간단한 “Hello World”를 사용하여 요청하는 웹 페이지에 응답을 보냅니다.

이제 추가 코드 없이 이 간단한 Hello, World 프로젝트를 실행할 수 있습니다. 앱을 실행하고 브라우저에서 보려면 도구 모음에서 재생(삼각형) 단추를 누릅니다.

![앱 실행](media/asp-net-core-image5.png)

Mac용 Visual Studio는 임의 포트를 사용하여 웹 프로젝트를 시작합니다. 해당 포트를 확인하려면 **보기 &gt; 패드** 아래에 나열된 애플리케이션 출력을 엽니다. 아래에 표시된 것과 비슷한 출력이 나타납니다.

![수신 대기 포트를 표시하는 애플리케이션 출력](media/asp-net-core-image6.png)

선택한 브라우저를 열고 `http://localhost:5000/`을 입력합니다. 여기서 `5000`을 Visual Studio 애플리케이션 출력에 출력된 포트로 바꿉니다. `Hello World!` 텍스트가 표시됩니다.

![텍스트를 표시하는 브라우저](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>컨트롤러 추가

ASP.NET Core 앱은 MVC(모델-뷰-컨트롤러) 디자인 패턴을 사용하여 앱의 각 부분에 대한 책임을 논리적으로 구분합니다. MVC는 다음과 같이 구성됩니다.

- **모델**: 앱의 데이터를 나타내는 클래스입니다.
- **보기**: 앱의 사용자 인터페이스(대개 모델 데이터임)를 표시합니다.
- **컨트롤러**: 브라우저 요청을 처리하고 사용자 입력 및 상호 작용에 응답하는 클래스입니다.

MVC 사용 방법에 대한 자세한 내용은 [ASP.NET Core MVC 개요](/aspnet/core/mvc/overview) 가이드를 참조하세요.

컨트롤러를 추가하려면 다음을 수행합니다.

1. 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **추가 > 새 파일**을 선택합니다. **일반 > 빈 클래스**를 선택하고 컨트롤러 이름을 입력합니다.

    ![새 파일 대화 상자](media/asp-net-core-image8.png)

2. 새 컨트롤러에 다음 코드를 추가합니다.

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. **종속성** 폴더를 마우스 오른쪽 단추로 클릭하고 **패키지 추가...** 를 선택하여 `Microsoft.AspNetCore.Mvc` 종속성을 프로젝트에 추가합니다.

4. 검색 상자를 사용하여 `Microsoft.AspNetCore.Mvc`의 NuGet 라이브러리를 찾은 다음 **패키지 추가**를 선택합니다. 설치하는 데 몇 분 정도 걸릴 수 있으며, 필수 종속성에 대한 다양한 라이선스에 동의하라는 메시지가 표시될 수도 있습니다.

    ![Nuget 추가](media/asp-net-core-image9.png)

5. 시작 클래스에서 `app.Run` 람다를 제거하고 MVC에서 호출해야 하는 코드를 확인하는 데 사용되는 URL 라우팅 논리를 다음과 같이 설정합니다.

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    `app.Run` 람다는 라우팅 논리를 재정의하므로 제거해야 합니다.

    MVC는 다음 형식을 사용하여 실행할 코드를 확인합니다.

    `/[Controller]/[ActionName]/[Parameters]`

    위의 코드 조각을 추가하면 앱이 기본적으로 `HelloWorld` 컨트롤러 및 `Index` 동작 메서드로 설정됩니다.

6. 아래 그림과 같이 `services.AddMvc();` 호출을 `ConfigureServices` 메서드에 추가합니다.

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    URL의 매개 변수 정보를 컨트롤러에 전달할 수도 있습니다.

7. 아래 그림과 같이 HelloWorldController에 다른 메서드를 추가합니다.

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. 이제 앱을 실행하면 자동으로 브라우저가 열립니다.

    ![브라우저에서 앱 실행](media/asp-net-core-image13.png)

9. `xxxx`를 올바른 포트로 바꿔 `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy`로 이동하면 다음이 같이 표시됩니다.

    ![인수를 사용하여 브라우저에서 앱 실행](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>문제 해결

Mac OS 10.11(El Capitan) 이상에 .NET Core를 수동으로 설치해야 하는 경우 다음을 수행합니다.

1. .NET Core 설치를 시작하기 전에 모든 OS 업데이트를 안정적인 최신 버전으로 업데이트했는지 확인합니다. 앱 스토어 애플리케이션으로 이동한 다음 업데이트 탭을 선택하면 확인할 수 있습니다.

2. [.NET Core 사이트](https://www.microsoft.com/net/core#macos)에 나열된 단계를 따르세요.

.NET Core가 성공적으로 설치되도록 네 단계를 모두 완료해야 합니다.

## <a name="summary"></a>요약

이 가이드에서는 ASP.NET Core를 소개했습니다. ASP.NET Core란 무엇이고 언제 사용해야 하는지를 설명하고, Mac용 Visual Studio에서 사용하는 방법에 대한 정보를 제공했습니다.
이후 단계에 대한 자세한 내용은 다음 가이드를 참조하세요.
- [ASP.NET Core](/aspnet/core/) 문서
- [네이티브 모바일 애플리케이션용 백 엔드 서비스 만들기](/aspnet/core/mobile/native-mobile-backend) - Xamarin.Forms 앱용 ASP.NET Core를 사용하여 REST 서비스를 빌드하는 방법을 보여 줍니다.
- [ASP.NET Core 실습 교육](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]