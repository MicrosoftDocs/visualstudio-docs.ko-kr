---
title: '자습서: C# 및 ASP.NET Core 시작'
titleSuffix: ''
description: C#을 사용하여 단계별로 Visual Studio에서 ASP.NET Core 웹앱을 만드는 방법을 알아봅니다.
ms.custom: seodec18, get-started
ms.date: 05/29/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: ef41e28d994f27f66f616623d1b2c9798b65ede4
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77580055"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>자습서: Visual Studio에서 C# 및 ASP.NET Core 시작

Visual Studio를 사용하여 ASP.NET Core로 C#을 개발하기 위한 이 자습서에서는 C# ASP.NET Core 웹앱을 만들고, 해당 앱을 변경하며, IDE의 일부 기능을 살펴본 후, 앱을 실행합니다.

## <a name="before-you-begin"></a>시작하기 전 주의 사항

### <a name="install-visual-studio"></a>Visual Studio 설치

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

### <a name="update-visual-studio"></a>Visual Studio 업데이트

Visual Studio를 이미 설치한 경우 최신 릴리스를 실행하고 있는지 확인합니다. 설치를 업데이트하는 방법에 대한 자세한 내용은 [Visual Studio를 최신 릴리스로 업데이트](../../install/update-visual-studio.md) 페이지를 참조하세요.

### <a name="choose-your-theme-optional"></a>테마 선택(선택 사항)

이 자습서에는 어두운 테마를 사용하는 스크린샷이 포함되어 있습니다. 어두운 테마를 사용하지 않지만 원하는 경우 [Visual Studio IDE 및 편집기 개인 설정](../../ide/quickstart-personalize-the-ide.md) 페이지에서 참조하여 방법을 알아봅니다.

## <a name="create-a-project"></a>프로젝트 만들기

먼저 ASP.NET Core 프로젝트를 만들 것입니다. 아무것도 추가하지 않아도 모든 기능을 갖춘 웹 사이트에 필요한 모든 템플릿 파일과 함께 프로젝트 형식이 제공됩니다.

::: moniker range="vs-2017"

1. Visual Studio 2017을 엽니다.

2. 상단 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. 왼쪽 창의 **새 프로젝트** 대화 상자에서 **Visual C#** , **Web**을 차례로 확장한 후 **.NET Core**를 선택합니다. 가운데 창에서 **ASP.NET Core 웹 애플리케이션**을 선택합니다. 그런 다음, 파일 이름을 *MyCoreApp*으로 지정하고, **확인**을 선택합니다.

   ![Visual Studio IDE의 새 프로젝트 대화 상자의 ASP.NET Core 웹 애플리케이션 프로젝트 템플릿](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>(선택 사항) 워크로드 추가

**ASP.NET Core 웹 애플리케이션** 프로젝트 템플릿이 표시되지 않는 경우, **ASP.NET 및 웹 개발** 워크로드를 추가하여 얻을 수 있습니다. 컴퓨터에 Visual Studio 2017 업데이트가 설치되었는지 여부에 따라 다음 두 방법 중 하나로 이 워크로드를 추가할 수 있습니다.

#### <a name="option-1-use-the-new-project-dialog-box"></a>옵션 1: 새 프로젝트 대화 상자 사용

1. **새 프로젝트** 대화 상자에서 **Visual Studio 설치 관리자 열기** 링크를 선택합니다. (표시 설정에 따라 스크롤해야 볼 수 있습니다.)

   ![새 프로젝트 대화 상자에서 Visual Studio 설치 관리자 열기 링크 선택](../media/open-visual-studio-installer-mycoreapp.png)

1. Visual Studio 설치 관리자가 시작됩니다. **ASP.NET 및 웹 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.

   ![Visual Studio Installer에서 .NET Core 플랫폼 간 개발 워크로드](../media/tutorial-aspnet-workload.png)

   (새 워크로드를 계속 설치하려면 먼저 Visual Studio를 닫아야 할 수 있습니다.)

#### <a name="option-2-use-the-tools-menu-bar"></a>옵션 2: 도구 메뉴 모음 사용

1. **새 프로젝트** 대화 상자에서 취소합니다. 그런 다음, 상단 메뉴 모음에서 **도구** > **도구 및 기능 가져오기**를 선택합니다.

1. Visual Studio 설치 관리자가 시작됩니다. **ASP.NET 및 웹 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.

   (새 워크로드를 계속 설치하려면 먼저 Visual Studio를 닫아야 할 수 있습니다.)

### <a name="add-a-project-template"></a>프로젝트 템플릿 추가

1. **새 ASP.NET Core 웹 애플리케이션** 대화 상자에서 **웹 애플리케이션** 프로젝트 템플릿을 선택합니다.

1. 위쪽 드롭다운 메뉴에 **ASP.NET Core 2.1**이 표시되는지 확인합니다. 그런 다음, **확인**을 선택합니다.

   ![새 ASP.NET Core 웹 애플리케이션 대화 상자](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > 맨 위 드롭다운 메뉴에서 **ASP.NET Core 2.1**을 볼 수 없는 경우 Visual Studio의 최신 릴리스를 실행하고 있는지 확인합니다. 설치를 업데이트하는 방법에 대한 자세한 내용은 [Visual Studio를 최신 릴리스로 업데이트](../../install/update-visual-studio.md) 페이지를 참조하세요.

::: moniker-end

::: moniker range="vs-2019"

1. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   !['새 프로젝트 만들기' 창 보기](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **새 프로젝트 만들기** 창에서 검색 상자에 *ASP.NET*을 입력합니다. 그런 다음, 언어 목록에서 **C#** 을 선택한 다음, 플랫폼 목록에서 **Windows**를 선택합니다.

   언어 및 플랫폼 필터를 적용한 후 **ASP.NET Core 웹 애플리케이션** 템플릿을 선택한 후, **다음**을 선택합니다.

   ![ASP.NET Core 웹 애플리케이션에 대한 C# 템플릿을 선택합니다.](./media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > **ASP.NET Core 웹 애플리케이션** 템플릿이 표시되지 않으면 **새 프로젝트를 만들기** 창에서 설치할 수 있습니다. **원하는 항목을 찾을 수 없나요?** 메시지에서 **추가 도구 및 기능 설치** 링크를 선택합니다.
   >
   > !['새 프로젝트 만들기' 창의 '원하는 항목을 찾을 수 없음' 메시지에서 '추가 도구 및 기능 설치' 링크](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > 그런 다음, Visual Studio 설치 관리자에서 **ASP.NET 및 웹 개발** 워크로드를 선택합니다.
   >
   > ![Visual Studio Installer에서 .NET Core 플랫폼 간 개발 워크로드](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > 그런 다음, Visual Studio 설치 관리자에서 **수정** 단추를 선택합니다. 작업을 저장하라는 메시지가 표시되면 저장합니다. 다음으로, **계속**을 선택하여 워크로드를 설치합니다. 그런 다음, 이 "[프로젝트 만들기](#create-a-project)" 프로시저의 2단계로 돌아갑니다.

1. **새 프로젝트 구성** 창에서 **프로젝트 이름** 상자에 *MyCoreApp*을 입력합니다. 그런 다음, **만들기**를 선택합니다.

   !['새 프로젝트 구성' 창에서 프로젝트의 이름을 'MyCoreApp'으로 지정합니다.](./media/vs-2019/csharp-name-your-aspnet-mycoreapp-project.png)

1. **새 ASP.NET Core 웹 애플리케이션 만들기** 창의 위쪽 드롭다운 메뉴에 **ASP.NET Core 3.0**이 표시되는지 확인합니다. 그런 다음, 예제 Razor Pages가 포함된 **웹 애플리케이션**을 선택합니다. 다음으로, **만들기**를 선택합니다.

   !['새 ASP.NET Core 웹 애플리케이션 만들기' 창](./media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio에서 새 프로젝트를 엽니다.

::: moniker-end

### <a name="about-your-solution"></a>솔루션 정보

이 솔루션은 **Razor 페이지** 디자인 패턴을 따릅니다. 이는 Razor 페이지 자체 내에 모델 및 컨트롤러 코드를 포함하도록 간소화된 [MVC(Model-View-Controller)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x) 디자인 패턴과 다릅니다.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>솔루션 둘러보기

 1. 프로젝트 템플릿은 _MyCoreApp_이라는 단일 ASP.NET Core 프로젝트와 솔루션을 만듭니다. 해당 콘텐츠를 보려면 **솔루션 탐색기** 탭을 선택합니다.

    ![Visual Studio for Razor Pages 솔루션에서 MyCoreApp으로 이름이 지정된 ASP.NET 솔루션 탐색기](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. **Pages** 폴더를 확장한 후 *About.cshtml*을 확장합니다.

     ![Visual Studio 솔루션 탐색기의 About.cshtml 파일](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. 코드 편집기에서 **About.cshtml** 파일을 봅니다.

     ![Visual Studio 코드 편집기에서 About.cshtml 파일 보기](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. **About.cshtml.cs** 파일을 선택합니다.

     ![Visual Studio 코드 편집기에서 About.cshtml.cs 파일 선택](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. 코드 편집기에서 **About.cshtml.cs** 파일을 봅니다.

     ![Visual Studio 코드 편집기에서 About.cshtml 파일 보기](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. 프로젝트에는 웹 사이트의 루트인 **wwwroot** 폴더가 포함됩니다. 내용을 보려면 폴더를 확장합니다.

     ![Visual Studio 솔루션 탐색기의 wwwroot 폴더](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    원하는 경로에 직접 &mdash;CSS, 이미지 및 JavaScript 라이브러리와 같은&mdash; 정적 사이트 콘텐츠를 배치할 수 있습니다.

 1. 프로젝트에는 런타임에 웹앱을 관리하는 구성 파일도 포함되어 있습니다. 기본 애플리케이션 [구성](/aspnet/core/fundamentals/configuration)은 *appsettings.json*에 저장됩니다. 하지만 *appsettings.Development.json*을 사용하여 이러한 설정을 재정의할 수 있습니다. **appsettings.json** 파일을 확장하여 **appsettings.Development.json** 파일을 봅니다.

     ![Visual Studio 솔루션 탐색기의 구성 파일](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>실행, 디버그 및 변경

1. IDE에서 **IIS Express** 단추를 선택하여 디버그 모드에서 앱을 빌드 및 실행합니다. 또는 **F5** 키를 누르거나 메뉴 모음에서 **디버그** > **디버깅 시작**을 선택합니다.

     ![Visual Studio에서 IIS Express 단추 선택](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' 웹 서버에 연결할 수 없습니다**라는 오류 메시지가 발생하면 Visual Studio를 닫은 후 마우스 오른쪽 단추 클릭 또는 상황에 맞는 메뉴에서 **관리자 권한으로 실행** 옵션을 사용하여 엽니다. 그런 다음 애플리케이션을 다시 실행합니다.
     >
     > IIS SSL Express 인증서를 허용할 것인지를 묻는 메시지가 표시될 수도 있습니다. 웹 브라우저에서 코드를 보려면 **예**를 선택한 다음, 후속 보안 경고 메시지가 표시되면 **예**를 선택합니다.

1. Visual Studio가 브라우저 창을 시작합니다. 메뉴 모음에 **홈**, **정보** 및 **연락처** 페이지가 표시됩니다. 표시되지 않으면 “햄버거” 메뉴 항목을 선택하여 표시합니다.

    ![웹앱의 메뉴 모음에서 “햄버거” 메뉴 항목 선택](media/csharp-aspnet-razor-browser-page.png)

1. 메뉴 모음에서 **정보**를 선택합니다.

   ![앱의 브라우저 창 메뉴 모음에서 정보 선택](media/csharp-aspnet-razor-browser-page-about-menu.png)

   무엇보다 브라우저의 **정보** 페이지는 *About.cshtml* 파일에서 설정된 텍스트를 렌더링합니다.

   ![About 페이지에서 텍스트 보기](media/csharp-aspnet-razor-browser-page-about.png)

1. Visual Studio로 돌아가서 **Shift+F5**를 눌러 디버그 모드를 중지합니다. 그러면 브라우저 창의 프로젝트도 닫힙니다.

1. Visual Studio에서 **About.cshtml**을 선택합니다. 그런 다음, _additional_ 단어를 삭제하고 이 위치에 _file and directory_ 단어를 추가합니다.

    ![About.cshtml 파일에서 텍스트 변경](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. **About.cshtml.cs**를 선택합니다. 그런 다음, 다음 바로 가기를 사용하여 파일 맨 위에서 `using` 지시문을 정리합니다.

   회색으로 표시된 `using` 지시문을 선택하면 [빠른 작업](../../ide/quick-actions.md) 전구 메뉴가 캐럿 바로 아래 또는 왼쪽 여백에 나타납니다. 전구 메뉴를 선택한 후 **불필요한 Using 제거**를 선택합니다.

   ![About.cshtml.cs 파일에서 불필요한 Using 제거](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio가 파일에서 불필요한 `using` 지시문을 삭제합니다.

1. 그런 다음, `OnGet()` 메서드에서 본문을 다음 코드로 변경합니다.

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. **환경** 및 **문자열** 아래에 두 개의 물결선 밑줄이 표시됩니다. 이러한 형식은 범위에 없으므로 물결선 밑줄이 표시됩니다.

   ![OnGet 메서드에 물결선 밑줄로 표시된 오류](media/csharp-aspnet-razor-add-new-on-get-method.png)

    **오류 목록** 도구 모음을 열고 같은 오류가 나열되는지 확인합니다. (**오류 목록** 도구 모음이 표시되지 않으면 메뉴 모음에서 **보기** > **오류 목록**을 선택합니다.)

   ![Visual Studio의 오류 목록](media/csharp-aspnet-razor-error-list.png)

1. 이 문제를 해결해 보겠습니다. 코드 편집기에서 오류가 있는 줄에 커서를 놓고 왼쪽 여백에서 [빠른 작업] 전구 메뉴를 선택합니다. 그런 다음, 드롭다운 메뉴에서 **using System;** 을 선택하여 이 지시문을 파일 맨 위에 추가하고 오류를 해결합니다.

   ![“using System;” 지시문 추가](media/csharp-aspnet-razor-add-usings.png)

1. **Ctrl**+**S**를 눌러 변경 내용을 저장한 다음 **F5**를 눌러 웹 브라우저에 프로젝트를 엽니다.

1. 웹 사이트 위쪽에서 **정보**를 선택하여 변경 내용을 확인합니다.

   ![변경 내용이 포함된 업데이트된 정보 페이지 표시](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. 웹 브라우저를 닫고, **Shift**+**F5**를 눌러 디버그 모드를 중지한 다음, Visual Studio를 닫습니다.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>솔루션 둘러보기

 1. 프로젝트 템플릿은 _MyCoreApp_이라는 단일 ASP.NET Core 프로젝트와 솔루션을 만듭니다. 해당 콘텐츠를 보려면 **솔루션 탐색기** 탭을 선택합니다.

    ![Visual Studio for Razor Pages 솔루션에서 MyCoreApp으로 이름이 지정된 ASP.NET 솔루션 탐색기](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. **Pages** 폴더를 펼칩니다.

     ![솔루션 탐색기의 Pages 폴더](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. 코드 편집기에서 **Index.cshtml** 파일을 살펴봅니다.

     ![Visual Studio 코드 편집기에서 Index.cshtml 파일 보기](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. 각 .cshtml 파일에는 연결된 코드 파일이 있습니다. 편집기에서 코드 파일을 열려면, 솔루션 탐색기에서 **Index.cshtml** 노드를 펼치고 **Index.cshtml.cs** 파일을 선택합니다.

     ![Visual Studio 코드 편집기에서 Index.cshtml.cs 파일 선택](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. 코드 편집기에서 **Index.cshtml.cs** 파일을 살펴봅니다.

     ![Visual Studio 코드 편집기에서 About.cshtml 파일 보기](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. 프로젝트에는 웹 사이트의 루트인 **wwwroot** 폴더가 포함됩니다. 내용을 보려면 폴더를 확장합니다.

     ![Visual Studio 솔루션 탐색기의 wwwroot 폴더](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    원하는 경로에 직접 &mdash;CSS, 이미지 및 JavaScript 라이브러리와 같은&mdash; 정적 사이트 콘텐츠를 배치할 수 있습니다.

 1. 프로젝트에는 런타임에 웹앱을 관리하는 구성 파일도 포함되어 있습니다. 기본 애플리케이션 [구성](/aspnet/core/fundamentals/configuration)은 *appsettings.json*에 저장됩니다. 하지만 *appsettings.Development.json*을 사용하여 이러한 설정을 재정의할 수 있습니다. **appsettings.json** 파일을 확장하여 **appsettings.Development.json** 파일을 봅니다.

     ![Visual Studio 솔루션 탐색기의 구성 파일](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>실행, 디버그 및 변경

1. IDE에서 **IIS Express** 단추를 선택하여 디버그 모드에서 앱을 빌드 및 실행합니다. 또는 **F5** 키를 누르거나 메뉴 모음에서 **디버그** > **디버깅 시작**을 선택합니다.

     ![Visual Studio에서 IIS Express 단추 선택](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' 웹 서버에 연결할 수 없습니다**라는 오류 메시지가 발생하면 Visual Studio를 닫은 후 마우스 오른쪽 단추 클릭 또는 상황에 맞는 메뉴에서 **관리자 권한으로 실행** 옵션을 사용하여 엽니다. 그런 다음 애플리케이션을 다시 실행합니다.
     >
     > IIS SSL Express 인증서를 허용할 것인지를 묻는 메시지가 표시될 수도 있습니다. 웹 브라우저에서 코드를 보려면 **예**를 선택한 다음, 후속 보안 경고 메시지가 표시되면 **예**를 선택합니다.

1. Visual Studio가 브라우저 창을 시작합니다. 메뉴 모음에 **홈** 및 **개인 정보** 페이지가 표시됩니다.

1. 메뉴 모음에서 **개인 정보**를 선택합니다.

   브라우저의 **개인 정보** 페이지에는 *Privacy.cshtml* 파일에 설정된 텍스트가 렌더링됩니다.

   ![개인 정보 페이지의 텍스트 보기](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Visual Studio로 돌아가서 **Shift+F5**를 눌러 디버그 모드를 중지합니다. 그러면 브라우저 창의 프로젝트도 닫힙니다.

1. Visual Studio에서 편집을 위해 **Privacy.cshtml**을 엽니다. _Use this page to detail your site's privacy policy_ 단어를 삭제하고, 대신 _This page is under construction as of @ViewData["TimeStamp"]_ 단어를 추가합니다.

    ![Privacy.cshtml 파일의 텍스트 변경](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. 이제 코드를 변경합시다. **Privacy.cshtml.cs**를 선택합니다. 그런 다음, 다음 바로 가기를 사용하여 파일 맨 위에서 `using` 지시문을 정리합니다.

   회색으로 표시된 `using` 지시문을 선택하면 [빠른 작업](../../ide/quick-actions.md) 전구 메뉴가 캐럿 바로 아래 또는 왼쪽 여백에 나타납니다. 전구 메뉴를 선택하고 **불필요한 using 제거**를 마우스로 가리킵니다.

   ![Privacy.cshtml.cs 파일에서 불필요한 using 제거](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   이제 **변경 내용 미리 보기**를 선택하여 변경 내용을 확인합니다.

   ![변경 내용 미리 보기](media/vs-2019/csharp-aspnet-preview-changes.png)

   **적용**을 선택합니다. Visual Studio가 파일에서 불필요한 `using` 지시문을 삭제합니다.

1. 그런 다음, `OnGet()` 메서드에서 본문을 다음 코드로 변경합니다.

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. **날짜/시간** 아래에 두 개의 물결선 밑줄이 표시됩니다. 물결선 밑줄이 표시되는 이유는 해당 형식이 범위에 없기 때문입니다.

   ![OnGet 메서드에 물결선 밑줄로 표시된 오류](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    **오류 목록** 도구 모음을 열고 같은 오류가 나열되는지 확인합니다. (**오류 목록** 도구 모음이 표시되지 않으면 메뉴 모음에서 **보기** > **오류 목록**을 선택합니다.)

   ![Visual Studio의 오류 목록](media/vs-2019/csharp-aspnet-error-list.png)

1. 이 문제를 해결해 보겠습니다. 코드 편집기에서 오류가 있는 줄에 커서를 놓고 왼쪽 여백에서 [빠른 작업] 전구 메뉴를 선택합니다. 그런 다음, 드롭다운 메뉴에서 **using System;** 을 선택하여 이 지시문을 파일 맨 위에 추가하고 오류를 해결합니다.

   ![“using System;” 지시문 추가](media/vs-2019/csharp-aspnet-add-usings.png)

1. **F5** 키를 눌러 웹 브라우저에서 프로젝트를 엽니다.

1. 웹 사이트의 맨 위에서 **개인 정보**를 선택하여 변경 내용을 살펴봅니다.

   ![변경 내용을 포함하는 업데이트된 개인 정보 페이지 보기](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. 웹 브라우저를 닫고, **Shift**+**F5**를 눌러 디버그 모드를 중지한 다음, Visual Studio를 닫습니다.
::: moniker-end

## <a name="quick-answers-faq"></a>빠른 답변 FAQ

몇 가지 주요 개념을 강조 표시하는 빠른 FAQ는 다음과 같습니다.

### <a name="what-is-c"></a>C#이란?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework)은 강력하면서도 쉽게 배울 수 있게 설계된 형식이 안전한 개체 지향 프로그래밍 언어입니다.

### <a name="what-is-aspnet-core"></a>ASP.NET Core란?

ASP.NET Core는 웹앱 및 서비스처럼 인터넷으로 연결된 애플리케이션을 빌드하기 위한 오픈 소스의 플랫폼 간 프레임워크입니다. ASP.NET Core 앱은 .NET Framework 또는.NET Core에서 실행할 수 있습니다. Windows, Mac 및 Linux에서 ASP.NET Core 앱을 플랫폼 간에 개발하여 실행할 수 있습니다. ASP.NET Core는 [GitHub](https://github.com/aspnet/home)에서 오픈 소스로 제공됩니다.

### <a name="what-is-visual-studio"></a>Visual Studio란?

Visual Studio는 개발자를 위한 통합 개발 생산성 도구입니다. 프로그램과 애플리케이션을 만드는 데 사용할 수 있는 프로그램으로 생각하면 됩니다.

## <a name="next-steps"></a>다음 단계

축하합니다. 이 자습서를 마쳤습니다. C#, ASP.NET Core 및 Visual Studio IDE를 이해하는 데 도움이 되었기를 바랍니다. C# 및 ASP.NET을 사용하여 웹앱 또는 웹 사이트를 만드는 방법에 대한 자세한 내용은 다음 자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [ASP.NET Core를 사용하여 Razor 페이지 웹앱 만들기](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)를 참조하세요.

## <a name="see-also"></a>참조

[Visual Studio를 사용하여 Azure App Service에 웹앱 게시](../../deployment/quickstart-deploy-to-azure.md)
