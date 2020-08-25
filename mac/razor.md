---
title: Razor 웹앱 만들기
description: Mac용 Visual Studio에 있는 ASP.NET Core 앱의 Razor 지원에 대한 정보를 제공합니다.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.topic: how-to
ms.openlocfilehash: 26575367d7aff2b92c64dc5d07068b4900b24e7f
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249537"
---
# <a name="create-razor-web-apps"></a>Razor 웹앱 만들기

이 가이드에서는 첫 번째 Razor 웹앱을 만드는 방법을 설명합니다. 자세한 지침은 [ASP.NET Core의 Razor Pages 소개](/aspnet/core/razor-pages/index)를 참조하세요.

Mac용 Visual Studio는 IntelliSense 및 *.cshtml* 파일에서 구문 강조 표시를 비롯한 Razor 편집을 지원합니다. Mac용 Visual Studio 2019 8.3 이상에서는, Razor 파일 내에서 컨텍스트 인식 IntelliSense를 사용할 수 있으므로, 문서 내에서 현재 편집 중인 언어와 일치하는 IntelliSense가 제공됩니다.

![Mac용 Visual Studio의 Razor 편집](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>새 Razor 프로젝트 만들기

1. 시작 화면에서 **새로 만들기**를 선택하여 새 프로젝트를 만듭니다.

   ![Mac용 Visual Studio 새 프로젝트](media/razor-new.png)
1. **새 프로젝트** 대화 상자에서 **.NET Core** > **앱** > **웹 애플리케이션**으로 이동하여 **다음**을 선택합니다.

   ![Razor 프로젝트 템플릿](media/razor-new-project1.png)
1. .Net Core 대상 프레임워크(버전 2.2 이상 권장)를 선택하고 **다음**을 선택합니다. 프로젝트 이름을 선택하고, 필요한 경우 Git 지원을 추가합니다. **만들기**를 선택하여 프로젝트를 만듭니다.

   ![Razor 프로젝트 이름](media/razor-new-project2.png)

   Mac용 Visual Studio에서 프로젝트가 코드 레이아웃 창에 열립니다.
1. **Command+Option+F5**를 사용하여 디버그하지 않고 프로젝트를 실행합니다.

   Visual Studio에서 [Kestrel](/aspnet/core/fundamentals/servers/kestrel)을 시작하고 브라우저에서 `https://localhost:5001`을 열어 첫 번째 Razor 웹앱을 표시합니다.

   ![Safari의 Razor 웹앱](media/razor-webapp.png)

## <a name="project-anatomy"></a>프로젝트 분석

Razor 웹앱은 다음 구성 요소를 포함합니다.

### <a name="pages-folder"></a>페이지 폴더

이 폴더에는 프로젝트의 웹 페이지와 각 웹 페이지의 코드 숨김이 포함되어 있습니다.
- HTML 표시 및 Razor 구문의 경우 *\*.cshtml* 파일.
- 페이지 이벤트 처리를 위한 C# 코드 숨김의 경우 *\*.cshtml.cs* 파일.

지원 파일에는 밑줄로 시작하는 이름이 있습니다. 예를 들어 *\_Layout.cshtml* 파일은 모든 페이지에 공통되는 UI 요소를 구성합니다. 이 파일은 페이지 맨 위에 있는 탐색 메뉴와 맨 아래에 있는 저작권 표시를 설정합니다. 자세한 내용은 [ASP.NET Core의 레이아웃](/aspnet/core/mvc/views/layout)을 참조하세요.

### <a name="launch-settings"></a>시작 설정

*launchSettings.json* 파일에는 IIS 설정, 애플리케이션 URL 및 기타 관련 설정이 포함되어 있습니다.

### <a name="app-settings"></a>앱 설정

*appSettings.json* 파일에는 연결 문자열과 같은 구성 데이터가 포함되어 있습니다.

구성에 대한 자세한 내용은 [ASP.NET의 구성 가이드](/aspnet/core/fundamentals/configuration/index)를 참조하세요.

### <a name="wwwroot-folder"></a>wwwroot 폴더

이 폴더에는 HTML, JavaScript, CSS 파일과 같은 정적 파일이 포함되어 있습니다. 자세한 내용은 [ASP.NET Core의 정적 파일](/aspnet/core/fundamentals/static-files)을 참조하세요.

### <a name="programcs"></a>Program.cs

이 파일에는 프로그램 진입점이 포함되어 있습니다. 자세한 내용은 [ASP.NET Core 웹 호스트](/aspnet/core/fundamentals/host/web-host)를 참조하세요.

### <a name="startupcs"></a>Startup.cs

이 파일에는 앱에서 쿠키에 대한 동의 필요 여부 등의 앱 동작을 구성하는 코드가 포함되어 있습니다. 자세한 내용은 [ASP.NET Core에서 앱 시작](/aspnet/core/fundamentals/startup)을 참조하세요.

## <a name="see-also"></a>참조

Razor 웹앱을 만드는 방법에 대한 포괄적인 가이드는 [ASP.NET Core의 Razor Pages 소개](/aspnet/core/razor-pages/index)를 참조하세요.
