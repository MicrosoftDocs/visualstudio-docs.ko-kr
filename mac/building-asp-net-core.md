---
title: ASP.NET Core 애플리케이션 빌드
description: 이 문서에서는 설치 및 새 프로젝트 만들기를 포함하여 Mac용 Visual Studio에서 ASP.NET을 시작하는 방법을 설명합니다.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: 5600fd2f0b6d83a3bd27350a4d4f0137ea44ced2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75398274"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 ASP.NET Core 애플리케이션 빌드

ASP.NET Core는 웹앱 및 웹 서비스, IoT 앱, 모바일 백 엔드처럼 최신 클라우드 기반의 인터넷으로 연결된 애플리케이션을 빌드하기 위한 오픈 소스의 플랫폼 간 프레임워크입니다. ASP.NET Core 앱은 [.NET Core](https://www.microsoft.com/net/core/platform) 또는 .NET Framework 런타임에서 실행할 수 있습니다. 클라우드에 배포되거나 온-프레미스 실행되는 앱에 최적화된 개발 프레임워크를 제공하도록 설계되었습니다. 이 앱에는 최소 오버헤드의 모듈식 구성 요소로 구성되어 있어 솔루션을 구축하는 동안 유연성을 유지합니다. Windows, Mac 및 Linux에서 ASP.NET Core 앱을 플랫폼 간에 개발하여 실행할 수 있습니다. ASP.NET Core는 [GitHub](https://github.com/aspnet/home)에서 오픈 소스로 제공됩니다.

이 랩에서는 Mac용 Visual Studio 애플리케이션을 사용하여 ASP.NET Core 애플리케이션을 만들고 살펴보려고 합니다.

## <a name="objectives"></a>목표

> [!div class="checklist"]
> * ASP.NET Core 웹앱 만들기
> * ASP.NET Core 호스팅, 구성 및 미들웨어 모델 살펴보기
> * ASP.NET Core 웹앱 디버깅

## <a name="prerequisites"></a>사전 요구 사항

- [Mac용 Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>대상 독자

이 랩은 심층적인 경험이 요구되지는 않지만, C#에 능숙한 개발자를 대상으로 합니다.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>작업 1: 새 ASP.NET Core 애플리케이션 만들기

1. **Mac용 Visual Studio**를 시작합니다.

2. **파일 > 새 솔루션**을 선택합니다.

3. **.NET Core > 앱** 범주와 **ASP.NET Core 웹앱(C#)** 템플릿을 선택합니다. **다음**을 클릭합니다.

    ![](media/netcore-image1.png)

4. 이름을 **"CoreLab"** 으로 입력하고 **만들기**를 클릭하여 프로젝트를 만듭니다. 완료하는 데 잠시 시간이 걸립니다.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>작업 2: 솔루션 둘러보기

1. 기본 템플릿은 **CoreLab**이라는 단일 ASP.NET Core 프로젝트의 솔루션을 만듭니다. 프로젝트 노드를 확장하면 그 안의 콘텐츠가 표시됩니다.

    ![](media/netcore-image3.png)

2. 이 프로젝트는 MVC(Model-View-Controller) 패러다임을 따라 데이터(모델), 프레젠테이션(뷰)와 기능성(컨트롤러) 간 책임을 분명히 구분합니다. **컨트롤러** 폴더에서 **HomeController.cs** 파일을 엽니다.

    ![](media/netcore-image4.png)

3. **HomeController** 클래스는 규칙에 따라, **/Home**으로 시작하는 모든 들어오는 요청을 처리합니다. **Index** 메서드는 디렉터리 루트(예: `http://site.com/Home`)에 대한 요청을 처리하고, 다른 메서드는 규칙에 따라 명명된 경로에 대한 요청을 처리합니다(예: **About()** 에서 `http://site.com/Home/About`에 대한 요청 처리). 물론, 모두 구성 가능합니다. 한 가지 주목할 만한 사항은 **HomeController**가 새 프로젝트의 기본 컨트롤러이므로, 사이트 루트(`http://site.com`)에 대한 요청이 `http://site.com/Home` 또는 `http://site.com/Home/Index`에 대한 요청과 마찬가지로 **HomeController**의 **Index()** 를 통해 처리된다는 것입니다.

    ![](media/netcore-image5.png)

4. 이 프로젝트에는 각 컨트롤러에 매핑되는 다른 폴더를 포함하는 **Views** 폴더도 있습니다(**Shared** 뷰에 대한 폴더 1개 포함). 예를 들어 **/Home/About** 경로에 대한 뷰 CSHTML 파일(HTML 확장)은 **Views/Home/About.cshtml**에 있습니다. 해당 파일을 엽니다.

    ![](media/netcore-image6.png)

5. 이 CSHTML 파일은 표준 태그와 인라인 C# 조합을 기준으로 HTML을 렌더링하기 위해 Razor 구문을 사용합니다. [온라인 설명서](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)에서 자세히 알아볼 수 있습니다.

    ![](media/netcore-image7.png)

6. 솔루션에는 웹 사이트의 루트가 될 **wwwroot** 폴더도 포함됩니다. CSS, 이미지 및 JavaScript 라이브러리 같은 정적 사이트 콘텐츠를 사이트 배포 시점에 놓으려는 경로에 직접 배치할 수 있습니다.

    ![](media/netcore-image8.png)

7. 런타임 시 프로젝트, 그 패키지 및 애플리케이션의 관리를 지원하는 다양한 구성 파일도 있습니다. 예를 들어 기본 애플리케이션 [구성](/aspnet/core/fundamentals/configuration)은 **appsettings.json**에 저장됩니다. appsettings.json 파일 아래에 **appsettings.Development.json** 파일이 중첩됩니다. 여기서 환경별로 이러한 설정의 일부/전체를 재정의할 수 있습니다. Mac용 Visual Studio는 Windows용 Visual Studio와 동일한 논리를 사용하여 이러한 방식으로 파일을 중첩하므로 더 자주 액세스해야 하는 파일이 맨 앞에 있습니다. 

    ![](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>작업 3: 애플리케이션이 호스팅되는 방법 이해

1. **솔루션 탐색기**에서 **Program.cs**를 엽니다. 애플리케이션을 실행하는 부트스트래퍼입니다.

    ![](media/netcore-image10.png)

2. 여기에는 두 줄의 코드만 있지만 상당히 중요합니다. 자세히 살펴 보겠습니다. 먼저, 새 **WebHostBuilder**가 만들어집니다. ASP.NET Core 앱은 실행할 호스트가 필요합니다. 호스트는 기능 및 서비스 컬렉션을 노출하는 **IWebHost** 인터페이스와 **Start** 메서드를 구현해야 합니다. 호스트는 일반적으로 **WebHost** 인스턴스를 빌드하고 반환하는 **WebHostBuilder** 인스턴스를 사용하여 만들어집니다. **WebHost**는 요청을 처리할 서버를 참조합니다.

    ![](media/netcore-image11.png)

3. **WebHostBuilder**가 앱에 대한 서버를 부트스트랩할 호스를 만드는 것을 담당하는 동안 사용자는 **IServer**를 구현하는 서버를 제공해야 합니다. 기본적으로 **[Kestrel](/aspnet/core/fundamentals/servers/kestrel)** 은 플랫폼 간 비동기 I/O 라이브러리인 **libuv**를 기반으로 하는 ASP.NET Core용 플랫폼 간 웹 서버입니다.

    ![](media/netcore-image12.png)

4. 다음으로, 서버의 콘텐츠 루트가 설정됩니다. 이것은 MVC 뷰 파일과 같은 콘텐츠 파일의 검색 위치를 결정합니다. 기본 콘텐츠 루트는 애플리케이션이 실행되는 폴더입니다.

    ![](media/netcore-image13.png)

5. 앱이 IIS(인터넷 정보 서비스) 웹 서버와 작동해야 한다면 **UseIISIntegration**은 호스트를 빌드하는 부분으로 호출되어야 합니다. 즉 이 앱은 **UseKestrel**과 달리 서버를 구성하지 않습니다. ASP.NET Core에서 IIS를 사용하려면 **UseKestrel**과 **UseIISIntegration**을 둘 다 지정해야 합니다. **Kestrel**은 프록시 뒤에서 실행되도록 설계되었으므로 인터넷과 직접 연결되도록 배포해서는 안 됩니다. **UseIISIntegration**은 역 프록시 서버로 IIS를 지정하지만 IIS가 있는 머신에서 실행 중일 때에만 관련성이 있습니다. Windows에 앱을 배포할 경우에는 그대로 두세요. 그렇지 않으면 성능이 저하되지 않습니다.

    ![](media/netcore-image14.png)

6. 이것이 애플리케이션 부트스트래핑에서 설정 로딩을 구분하는 보다 깨끗한 방법입니다. 이 작업을 쉽게 수행하기 위해 **UseStartup**이 호출되어 **Startup** 클래스가 설정은 물론, HTTP 파이프라인으로 미들웨어 삽입 등, 기타 시작 작업 로딩에 호출되도록 지정합니다. 필요에 따라 각 설정이 이전 설정을 덮어쓴다는 예상과 함께 여러 **UseStartup** 호출이 있을 수 있습니다.

    ![](media/netcore-image15.png)

7. **IWebHost**를 만드는 마지막 단계는 **Build**를 호출하는 것입니다.

    ![](media/netcore-image16.png)

8. 비차단 방식의 **Start**를 구현하는 데 **IWebHost** 클래스가 필요하지만, ASP.NET Core 프로젝트는 **Start**를 차단 코드로 둘러싸는 **Run**이라고 하는 확장 메서드가 있어 메서드가 즉시 종료되지 못하게 수동으로 막을 필요가 없습니다.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>작업 4: 애플리케이션 실행 및 디버깅

1. **솔루션 탐색기**에서 **CoreLab** 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **옵션**을 선택합니다.

    ![](media/netcore-image18.png)

2. **프로젝트 옵션** 대화 상자에는 애플리케이션이 구축 및 실행되는 방식을 조정하는 데 필요한 모든 것이 포함되어 있습니다. 왼쪽 패널에서 **실행 > 구성 > 기본** 노드를 선택합니다.

3. **외부 콘솔에서 실행**을 선택하고 **콘솔 출력 일시 중지**를 선택 해제합니다. 일반적으로 자체 호스팅 애플리케이션에는 콘솔이 보이지 않지만, 대신 결과를 **출력** 패드로 로깅합니다. 이 랩의 목적을 위해, 일반적인 개발 중에는 수행할 필요가 없더라도 별도의 창에서 살펴 보겠습니다.

4. **확인**을 클릭합니다.

    ![](media/netcore-image19.png)

5. **F5** 키를 눌러 애플리케이션을 빌드하고 실행합니다. 또는 **실행 > 디버깅 시작**을 선택할 수 있습니다.

6. Mac용 Visual Studio는 두 개의 창을 시작합니다. 첫 번째는 셀프 호스팅 서버 애플리케이션에 대한 뷰를 제공하는 콘솔 창입니다.

    ![](media/netcore-image20.png)

7. 두 번째는 사이트를 테스트할 일반적인 브라우저 창입니다. 브라우저가 파악하는 한, 이 애플리케이션은 어디에서나 호스팅할 수 있습니다. **About**을 클릭하여 해당 페이지로 이동합니다.

    ![](media/netcore-image21.png)

8. 무엇보다 About 페이지는 컨트롤러에서 일부 텍스트 세트를 렌더링합니다.

    ![](media/netcore-image22.png)

9. 두 개의 창을 열어 두고 Mac용 Visual Studio로 돌아갑니다. 아직 열려 있지 않으면 **Controllers/HomeController.cs**를 엽니다.

    ![](media/netcore-image23.png)

10. **About** 메서드의 첫 줄에 중단점을 설정합니다. 여백을 클릭하거나 라인에 커서를 두고 **F9**를 누르면 수행할 수 있습니다. 이 줄은 **Views/Home/About.cshtml**의 CSHTML 페이지에서 렌더링되는 **ViewData** 컬렉션에 일부 데이터를 설정합니다.

    ![](media/netcore-image24.png)

11. 브라우저로 돌아가 About 페이지를 새로 고칩니다. 이렇게 하면 Mac용 Visual Studio에서 중단점이 트리거됩니다.

12. **ViewData** 멤버 위에 마우스를 가져가 해당 데이터를 확인합니다. 자식 멤버를 확장하여 중첩된 데이터를 볼 수도 있습니다.

    ![](media/netcore-image25.png)

13. 중단점을 추가하는 데 사용한 것과 같은 방법으로 애플리케이션 중단점을 제거합니다.

14. **Views/Home/About.cshtml**을 엽니다.

15. **"additional"** 텍스트를 **"changed"** 으로 변경하여 파일을 저장합니다.

    ![](media/netcore-image26.png)

16. **계속** 단추를 눌러 실행을 계속합니다.

    ![](media/netcore-image27.png)

17. 브라우저 창으로 돌아가 업데이트된 텍스트를 확인합니다. 이 변경 사항은 언제든지 수행할 수 있으며 디버거 중단점이 반드시 필요하지는 않았습니다. 반영한 변경 사항이 즉시 보이지 않으면 브라우저를 새로 고칩니다.

    ![](media/netcore-image28.png)

18. 테스트 브라우저 창 및 애플리케이션 콘솔을 닫습니다. 그러면 디버깅 작업도 중지됩니다.

## <a name="task-5-application-startup-configuration"></a>작업 5: 애플리케이션 시작 구성

1. **솔루션 탐색기**에서 **Startup.cs**를 엽니다. 백그라운드에서 NuGet 패키지가 복원되고 Roslyn 컨파일러가 프로젝트 종속성의 전체 그림을 빌드할 때 처음에는 빨강 오류 표시선이 보일 수 있습니다.

    ![](media/netcore-image29.png)

2. **Startup** 메서드를 찾습니다. 이 섹션에서는 애플리케이션에 대한 초기 구성을 정의하고 밀도 있게 구성되어 있습니다. 자세히 알아 보겠습니다.

    ![](media/netcore-image30.png)

3. 이 메서드는 **ConfigurationBuilder**를 초기화하고 기본 경로를 설정하면 시작합니다.

    ![](media/netcore-image31.png)

4. 다음으로, 필요한 **appsettings.json** 파일을 로드합니다.

    ![](media/netcore-image32.png)

5. 그런 다음, 기존 설정을 덮어쓸 환경 특정 **appsettings.json** 파일을 로드하려고 합니다. 예를 들어, 해당 특정 환경에 사용하는 제공된 **appsettings.Development.json** 파일입니다. ASP.NET Core에서 구성에 대해 자세히 알아보려면 [설명서](/aspnet/core/fundamentals/configuration)를 확인하세요.

    ![](media/netcore-image34.png)

6. 마지막으로, 구성 작성기에 환경 변수가 추가되고 해당 구성이 용도에 맞게 빌드 및 설정됩니다.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>작업 6: 애플리케이션 미들웨어 삽입

1. **Startup** 클래스에서 **Configure** 메서드를 찾습니다. HTTP 파이프라인에 삽입하여 서버에 대한 모든 요청을 처리하는 데 사용할 수 있도록 모든 미들웨어가 구성되는 곳입니다. 이 메서는 단 한번만 호출되지만, 메서드의 콘텐츠(**UseStaticFiles** 등)는 모든 요청에 대해 실행될 수 있습니다.

    ![](media/netcore-image36.png)

2. 또한 파이프라인의 일부로 실행할 추가 미들웨어를 추가할 수도 있습니다. **app.UseStaticFiles** 다음에 아래 코드를 추가하여 모든 나가는 응답에 **X-Test** 헤더를 자동 추가합니다. IntelliSense는 입력 시 코드를 완성해 줍니다.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. **F5**를 눌러 프로젝트를 빌드하고 실행합니다.

4. 브라우저를 사용하여 헤더가 추가되었는지 검사할 수 있습니다. 아래 지침은 Safari에 관한 내용이지만, [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) 또는 [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console)에서 동일하게 수행할 수 있습니다.

5. 브라우저가 사이트를 로드하면 **Safari > Preferences**를 선택합니다.

6. **Advanced** 탭에서 **Show Develop menu in menu bar**를 선택하고 대화 상자를 닫습니다.

    ![](media/netcore-image37.png)

7. **Develop > Show Page Resources**를 선택합니다.

8. 새로 열린 개발자 도구가 트래픽 및 콘텐츠를 추적하고 분석할 수 있도록 브라우저 창을 새로 고침합니다.

9. 서버에서 렌더링하는 로컬호스트 HTML 페이지는 기본적으로 선택되는 항목입니다.

    ![](media/netcore-image38.png)

10. **Details sidebar**를 확장합니다.

    ![](media/netcore-image39.png)

11. 사이드바 맨 아래로 스크롤하여 이전에 코드에 추가한 응답 헤더를 확인합니다.

    ![](media/netcore-image40.png)

12. 만족스러우면 브라우저 창과 콘솔을 닫습니다.

## <a name="summary"></a>요약

이 랩에서는 Mac용 Visual Studio를 사용하여 ASP.NET Core 앱 개발을 시작하는 방법을 살펴보았습니다. 보다 완벽한 동영상 데이터베이스 애플리케이션 개발에 대해 살펴보고 싶다면 [ASP.NET Core MVC 시작](/aspnet/core/tutorials/first-mvc-app/start-mvc) 자습서를 참조하세요.
