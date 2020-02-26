---
title: '2단계: 첫 번째 ASP.NET Core 웹앱 만들기'
description: 이 비디오 자습서 및 단계별 지침을 사용하여 첫 번재 ASP.NET Core 웹앱을 만듭니다.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1d382e83aa9672cfdcbdca64b89be79d090f2aac
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77580078"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>2단계: 첫 번째 ASP.NET Core 웹앱 만들기

이 비디오 자습서 및 단계별 지침을 사용하여 첫 번재 ASP.NET Core 웹앱을 만듭니다.

_이 비디오를 보고 따라서 첫 번째 ASP.NET Core 앱을 만듭니다._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Visual Studio 2019 시작 및 새 프로젝트 만들기

Visual Studio 2019를 시작하고 **새 프로젝트 만들기**를 클릭합니다. **새 ASP.NET Core 웹 애플리케이션**을 선택합니다. **웹 애플리케이션** 템플릿을 선택하고 기본 프로젝트 이름과 위치를 유지합니다. ASP.NET Core 버전을 사용하는 드롭다운에서, **ASP.NET Core 2.1** 또는 **ASP.NET Core 2.2**를 선택합니다. **만들기**를 클릭합니다. 자세한 지침은 [이 자습서 시리즈의 이전 비디오](tutorial-aspnet-core-ef-step-01.md)를 참조하세요.

![Visual Studio 2019 ASP.NET Core 프로젝트 옵션 선택](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> ASP .NET Core 2.1 또는 ASP.NET Core 2.2를 선택했는지 확인합니다. 이 자습서는 ASP.NET Core 3.x와 호환되지 않습니다.

## <a name="explore-the-new-project"></a>새 프로젝트 탐색

오른쪽의 솔루션 탐색기 창에서 새 프로젝트의 내용을 볼 수 있습니다. 여기에 설명되어 있습니다.

![Visual Studio 2019 ASP.NET Core 프로젝트](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

*wwwroot* 폴더에는 웹 애플리케이션에서 공개적으로 액세스할 수 있는 정적 파일이 저장됩니다. 일반적으로 스타일시트, 클라이언트 쪽 스크립트 파일 및 이미지를 저장합니다.

### <a name="pages"></a>Pages

*Pages* 폴더에는 사이트의 Razor Pages가 저장됩니다. 기본 템플릿은 애플리케이션 홈 페이지인 *Index.cshtml* 페이지를 포함하는 여러 페이지와 정보, 연락처 등을 제공합니다.

### <a name="appsettingsjson"></a>appsettings.json

이 파일은 사이트에 대한 구성 설정을 JSON 형식으로 저장합니다.

### <a name="programcs"></a>Program.cs

이 파일은 애플리케이션의 진입점 역할을 합니다. 앱이 실행될 때 Main 메서드가 실행되는 첫 번째 메서드이며, 애플리케이션을 포함할 웹 호스트를 만드는 것을 담당합니다.

### <a name="startupcs"></a>Startup.cs

*Program.cs*에서 생성된 웹 호스트는 Startup 클래스를 참조하고 애플리케이션을 구성하는 메서드를 호출합니다. ConfigureServices 메서드는 앱에서 사용할 서비스를 설정합니다. `Configure` 메서드는 앱의 HTTP 요청 파이프라인을 설정합니다. 각 요청은 *미들웨어*의 각 부분과의 상호 작용을 통해 파이프라인을 통과합니다.

### <a name="indexcshtml"></a>Index.cshtml

사이트의 홈 페이지에는 몇 가지 HTML 태그 및 서버 쪽 Razor 코드가 포함되어 있습니다. Razor를 사용하여 관련된 *Index.cshtml.cs* 파일에 있는 페이지 모델인 `IndexModel`을 지정합니다. 또한 ViewData에서 값을 설정하여 페이지 제목을 설정합니다. 이 ViewData 값은 Pages 페이지 폴더 내의 공유 폴더에 있는 *\_Layout.cshtml* 파일에서 읽습니다. 레이아웃 파일은 많은 Razor Pages에 의해 공유되며 애플리케이션에 대한 일반적인 모양과 느낌을 제공합니다. 각 페이지의 콘텐츠는 레이아웃 파일의 HTML 내에서 렌더링됩니다.

## <a name="run-the-application"></a>애플리케이션 실행

이제 애플리케이션을 실행하고 브라우저에서 확인합니다. **Ctrl**+**F5**를 사용하거나 Visual Studio의 메뉴에서 **디버그** > **디버깅하지 않고 시작**을 선택하여 애플리케이션을 실행할 수 있습니다.

## <a name="customize-the-application"></a>애플리케이션 사용자 지정

*Index.cshtml.cs* 파일에 속성을 추가하고 해당 값을 `OnGet` 처리기의 현재 시간으로 설정합니다.

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

*Index.cshtml*의 `<div>` 콘텐츠를 다음 태그로 바꿉니다.

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

애플리케이션을 다시 실행합니다. 이제 페이지에는 현재 시간이 표시되지만 항상 자정이란 것을 알아야 합니다. 올바르지 않습니다.

![브라우저의 Visual Studio 2019 ASP.NET Core 프로젝트](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>애플리케이션 디버그

`Time`에 값을 할당하는 `OnGet` 메서드에 중단점을 추가하고 이번에 애플리케이션 디버깅을 시작합니다.

실행이 줄에서 중지되고 `DateTime.Today`에 날짜가 포함되지만 시간 데이터가 포함되어 있지 않기 때문에 시간은 항상 자정입니다. 

![브라우저의 Visual Studio 2019 ASP.NET Core 프로젝트](media/vs-2019/vs2019-breakpoint.png)

`DateTime.Now`를 사용하도록 변경하고 계속 실행합니다. `OnGet`에 대한 새 코드는 다음과 같아야 합니다.

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

이제 앱으로 이동할 때 브라우저에서 실제 서버 시간이 표시되어야 합니다.

> [!NOTE]
> ToShortDateTimeString의 출력 형식은 현재 문화 설정에 따라 다르기 때문에 실제 출력은 이미지와 다를 수 있습니다. <xref:System.DateTime.ToShortTimeString>을 참조하세요.

![브라우저의 Visual Studio 2019 ASP.NET Core 프로젝트](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>다음 단계

다음 비디오에서는 앱에 데이터 지원을 추가하는 방법을 알아봅니다.

[자습서: ASP.NET Core 앱에서 데이터 작업](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>참조

- [자습서: ASP.NET Core를 사용하여 Razor Pages 웹앱 만들기](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
