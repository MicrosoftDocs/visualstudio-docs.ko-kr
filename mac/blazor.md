---
title: Blazor 웹앱 만들기
description: Mac용 Visual Studio에 있는 ASP.NET Core 앱의 Blazor 지원에 대한 정보를 제공합니다.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75737302"
---
# <a name="create-blazor-web-apps"></a>Blazor 웹앱 만들기

이 가이드에서는 첫 번째 Blazor 웹앱을 만드는 방법을 설명합니다. 자세한 지침은 [ASP.NET Core Blazor 소개](/aspnet/core/blazor/index)를 참조하세요.

Mac용 Visual Studio(버전 8.4부터)에는 ASP.NET Core Blazor Server 애플리케이션 개발 및 게시에 대한 지원이 포함되어 있습니다. Blazor는 .NET을 사용하여 대화형 클라이언트 쪽 웹 UI를 빌드하기 위한 프레임워크으로, 웹 개발자에게 다음과 같은 이점을 제공합니다.

* JavaScript 대신 C#으로 코드를 작성합니다.
* .NET 라이브러리의 기존 .NET 에코시스템을 활용합니다.
* 서버 및 클라이언트에서 앱 논리를 공유합니다.
* .NET의 성능, 안정성 및 보안을 활용합니다.
* PC, Linux 및 macOS에서 Visual Studio를 사용하여 생산성을 유지합니다.
* 안정적이고, 기능이 풍부하고, 사용하기 쉬운 공통 언어, 프레임워크 및 도구 세트를 기반으로 빌드합니다.

## <a name="creating-a-new-blazor-project"></a>새 Blazor 프로젝트 만들기

1. **시작 창**에서 **새로 만들기**를 선택하여 새 프로젝트를 만듭니다.

   ![새 선택 영역이 강조 표시된 Mac용 Visual Studio 시작 창](media/blazor-new-project.png)
1. **새 프로젝트** 대화 상자에서 **.NET Core** > **앱** > **Blazor 서버 앱**을 선택하고 **다음**을 선택합니다. ![Blazor 서버 앱 템플릿이 선택된 새 프로젝트 템플릿 선택 대화 상자](media/blazor-project-template.png)

1. 대상 프레임워크로 .NET Core 3.1을 선택하고 **다음**을 선택합니다. 
   ![대상 프레임워크가 .NET Core 3.1로 선택된 새 Blazor 서버 앱 구성 대화](media/blazor-select-target-framework.png)

1. 프로젝트 이름을 선택하고 필요한 경우 Git 지원을 추가합니다. **만들기**를 선택하여 프로젝트를 만듭니다.
   ![프로젝트 이름을 입력하는 동안 표시되는 새 Blazor 서버 앱 구성 대화 상자](media/blazor-name-project.png)

   Mac용 Visual Studio에서 프로젝트가 코드 레이아웃 창에 열립니다.
1. **실행** > **디버깅하지 않고 시작**을 선택하여 앱을 실행합니다.

   Visual Studio에서 [Kestrel](/aspnet/core/fundamentals/servers/kestrel)을 시작하고 브라우저에서 `https://localhost:5001`을 열어 첫 번째 Blazor 웹앱을 표시합니다.

   ![Safari의 Blazor 웹앱](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Mac용 Visual Studio의 Blazor 지원

Mac용 Visual Studio(버전 8.4부터)에는 새 Blazor 서버 프로젝트를 만드는 데 도움이 되는 새로운 기능이 포함되어 있습니다. 또한 Blazor 프로젝트를 빌드, 실행 및 디버깅하는 것과 같은 표준 지원을 제공합니다. 

위의 연습에서는 Blazor 서버 앱 프로젝트 템플릿을 사용하여 새 Blazor 서버 앱 프로젝트를 만드는 방법을 살펴보았습니다. Mac용 Visual Studio에서 Blazor 서버 프로젝트 개발을 지원하기 위한 추가 기능 중 일부를 살펴보겠습니다.

### <a name="editor-support-for-razor-files"></a>*.razor* 파일에 대한 편집기 지원
Mac용 Visual Studio에는 Blazor 애플리케이션을 만들 때 사용하는 파일의 대부분을 편집하는 기능이 포함되어 있습니다. IDE의 Windows 및 Mac 버전은 .razor 파일에 대해 동일한 편집기를 공유합니다. 프로젝트에 선언된 Razor 구성 요소에 대한 완성을 포함하여 .razor 파일에 대한 전체 색 지정 및 완성 지원이 표시됩니다.

![Blazor에 대한 Intellisense를 보여 주는 Mac용 Visual Studio 편집기 창](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Azure App Service에 Blazor 애플리케이션 게시
Blazor 애플리케이션을 Azure App Service에 직접 게시할 수도 있습니다. Azure에서 Blazor 앱을 실행하기 위한 Azure 계정이 없는 경우 언제든지 [여기에서 무료로 가입](https://azure.microsoft.com/free)할 수 있습니다. 그러면 12개월 인기 서비스 무료 혜택, $200 무료 Azure 크레딧, 25개 이상의 상시 무료 서비스가 제공됩니다.

![Azure 게시 환경을 보여 주는 Mac용 Visual Studio](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>프로젝트 분석

Blazor 웹앱은 기본적으로 몇 가지 디렉터리와 파일을 포함합니다. 시작할 때 알아야 할 주요 항목은 다음과 같습니다.

### <a name="pages-folder"></a>페이지 폴더

이 폴더에는 *.razor* 파일 확장명을 사용하는 프로젝트의 웹 페이지가 포함됩니다.

### <a name="shared-folder"></a>공유 폴더

이 폴더에는 *.razor* 확장명을 사용하는 공유 구성 요소가 포함됩니다. 여기에는 애플리케이션 전체에서 공통 레이아웃을 정의하는 데 사용되는 *MainLayout.razor*가 포함됩니다. 또한 모든 페이지에서 사용되는 공유 *NavMenu.razor* 구성 요소도 포함됩니다. 재사용 가능한 구성 요소를 만들면 **공유** 폴더로 이동합니다.

### <a name="app-settings"></a>앱 설정

*appSettings.json* 파일에는 연결 문자열과 같은 구성 데이터가 포함되어 있습니다.

구성에 대한 자세한 내용은 [ASP.NET의 구성 가이드](/aspnet/core/fundamentals/configuration/index)를 참조하세요.

### <a name="wwwroot-folder"></a>wwwroot 폴더

이 폴더에는 HTML, JavaScript, CSS 파일과 같은 정적 파일이 포함되어 있습니다. 자세한 내용은 [ASP.NET Core의 정적 파일](/aspnet/core/fundamentals/static-files)을 참조하세요.

### <a name="programcs"></a>Program.cs

이 파일에는 프로그램 진입점이 포함되어 있습니다. 자세한 내용은 [ASP.NET Core 웹 호스트](/aspnet/core/fundamentals/host/web-host)를 참조하세요.

### <a name="startupcs"></a>Startup.cs

이 파일에는 앱에서 쿠키에 대한 동의 필요 여부 등의 앱 동작을 구성하는 코드가 포함되어 있습니다. 자세한 내용은 [ASP.NET Core에서 앱 시작](/aspnet/core/fundamentals/startup)을 참조하세요.

## <a name="summary"></a>요약
이 자습서에서는 Mac용 Visual Studio에서 새로운 Blazor 서버 앱을 만드는 방법과 Mac용 Visual Studio에서 Blazor 애플리케이션을 만드는 데 도움이 되도록 제공하는 기능 중 일부에 대해 알아보았습니다.

## <a name="see-also"></a>참조

Blazor 웹앱을 만드는 방법에 대한 종합적인 가이드는 [ASP.NET Core Blazor 소개](/aspnet/core/blazor/index)를 참조하세요.
