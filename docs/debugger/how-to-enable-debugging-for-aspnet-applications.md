---
title: ASP.NET 앱에 디버깅 사용 | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: f23f5bb2588c179f47593b1ecbcf5d6cd7fa9f0d
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349759"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio에서 ASP.NET 또는 ASP.NET Core 앱 디버그

Visual Studio에서 ASP.NET 또는 ASP.NET Core 앱을 디버그할 수 있습니다. 프로세스는 ASP.NET과 ASP.NET Core 간에 다르고, IIS Express 또는 로컬 IIS 서버에서 실행하는지 여부에 따라서도 다릅니다.

>[!NOTE]
>다음 단계와 설정은 로컬 서버에서 앱을 디버깅하는 경우에만 적용됩니다. 원격 IIS 서버에서 앱을 디버깅하는 경우 **프로세스에 연결**이 사용되며, 이러한 설정은 무시됩니다. IIS의 ASP.NET 앱 원격 디버깅에 대한 자세한 내용 및 지침은 [IIS 컴퓨터의 ASP.NET 원격 디버그](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) 또는 [원격 IIS 컴퓨터의 ASP.NET Core 원격 디버그](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)를 참조하세요.

기본 제공되는 IIS Express 서버가 Visual Studio에 포함되어 있습니다. IIS Express는 ASP.NET 및 ASP.NET Core 프로젝트에 대한 기본 디버그 서버이며 미리 구성되어 있습니다. 이는 가장 쉬운 디버깅 방법으로, 초기 디버깅 및 테스트에 이상적입니다.

또한 앱을 실행하도록 구성된 로컬 IIS 서버(8.0 버전 이상)에서도 ASP.NET 또는 ASP.NET Core 앱을 디버그할 수 있습니다. 로컬 IIS에서 디버그를 수행하려면 다음 요구 사항을 충족해야 합니다.

<a name="iis"></a>
- Visual Studio를 설치할 때 **개발 시간 IIS 지원**을 선택합니다. (필요한 경우 Visual Studio 설치 관리자를 다시 실행하고 **수정**을 선택한 후, 이 구성 요소를 추가합니다.)
- 관리자 권한으로 Visual Studio를 실행합니다.
- IIS를 설치하고 적절한 ASP.NET 및/또는 ASP.NET Core 버전으로 올바르게 구성합니다. 자세한 내용 및 지침은 [ASP.NET 3.5 및 ASP.NET 4.5를 사용하는 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 또는 [IIS가 있는 Windows에서 ASP.NET Core 호스팅](/aspnet/core/host-and-deploy/iis/index)을 참조하세요.
- 앱이 오류 없이 IIS에서 실행되는지 확인합니다.

## <a name="debug-aspnet-apps"></a>ASP.NET 앱 디버그

IIS Express는 기본값이며 미리 구성되어 있습니다. 로컬 IIS에서 디버깅하는 경우 [로컬 IIS 디버깅에 대한 요구 사항](#iis)을 충족하는지 확인합니다.

1. Visual Studio **솔루션 탐색기**에서 ASP.NET 프로젝트를 선택하고 **속성** 아이콘을 클릭하고, **Alt**+**Enter** 키를 누르거나 **속성**을 마우스 오른쪽 단추로 클릭하여 선택합니다.

1. **웹** 탭을 선택합니다.

1. **속성** 창의 **서버**에서
   - IIS Express의 경우 드롭다운에서 **IIS Express**를 선택합니다.
   - 로컬 IIS의 경우
     1. 드롭다운에서 **로컬 IIS**를 선택합니다.
     1. IIS에서 앱을 아직 설정하지 않은 경우 **프로젝트 URL** 필드 옆에 **가상 디렉터리 만들기**를 선택합니다.

1. **디버거**에서 **ASP.NET**을 선택합니다.

   ![ASP.NET 디버거 설정](media/dbg-aspnet-enable-debugging2.png "ASP.NET 디버거 설정")

1. **파일** > **선택한 항목 저장** 또는 **Ctrl**+**S**를 사용하여 변경 내용을 저장합니다.

1. 앱을 디버그하려면 앱에서 일부 코드에서 중단점을 설정합니다. Visual Studio 도구 모음에서 구성이 **디버그**로 설정되어 있는지 확인하고, 원하는 브라우저가 에뮬레이터 필드에서 **IIS Express(\<Browser name>)** 또는 **로컬 IIS(\<Browser name>)** 에 표시되는지 확인합니다.

1. 디버깅을 시작하려면 도구 모음에서 **IIS Express(\<Browser name>)** 또는 **로컬 IIS(\<Browser name>)** 를 선택하고 **디버그** 메뉴에서 **디버깅 시작**을 선택하거나 **F5** 키를 누릅니다. 디버거가 중단점에서 일시 중지됩니다. 디버거가 중단점에 도달할 수 없는 경우 [디버깅 문제 해결](#troubleshoot-debugging)을 참조하세요.

## <a name="debug-aspnet-core-apps"></a>ASP.NET Core 앱 디버그

IIS Express는 기본값이며 미리 구성되어 있습니다. 로컬 IIS에서 디버깅하는 경우 [로컬 IIS 디버깅에 대한 요구 사항](#iis)을 충족하는지 확인합니다.

1. Visual Studio **솔루션 탐색기**에서 ASP.NET Core 프로젝트를 선택하고 **속성** 아이콘을 클릭하고, **Alt**+**Enter** 키를 누르거나 **속성**을 마우스 오른쪽 단추로 클릭하여 선택합니다.

1. **디버그** 탭을 선택합니다.

1. **속성** 창에서 **프로필** 옆에 있습니다.
   - IIS Express의 경우 드롭다운에서 **IIS Express**를 선택합니다.
   - 로컬 IIS의 경우 드롭다운에서 앱 이름을 선택하거나 **새로 만들기**를 선택하고 새 프로필 이름을 만든 후, **확인**을 선택합니다.

1. **시작** 옆에 있는 드롭다운 목록에서 **IIS Express** 또는 **IIS** 중 하나를 선택합니다.

1. **브라우저 시작**이 선택되어 있는지 확인합니다.

1. **환경 변수**에서 값이 **Development**인 **ASPNETCORE_ENVIRONMENT**가 있는지 확인합니다. 그렇지 않으면 **추가**를 선택하여 추가합니다.

   ![ASP.NET Core 디버거 설정](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core 디버거 설정")

1. **파일** > **선택한 항목 저장** 또는 **Ctrl**+**S**를 사용하여 변경 내용을 저장합니다.

1. 앱을 디버그하려면 앱에서 일부 코드에서 중단점을 설정합니다. Visual Studio 도구 모음에서 구성이 **디버그**로 설정되어 있는지 확인하고 **IIS Express** 또는 새 IIS 프로필 이름이 에뮬레이터 필드에 나타나는지 확인합니다.

1. 디버깅을 시작하려면 도구 모음에서 **IIS Express** 또는 **\<IIS profile name>** 을 선택하고 **디버그** 메뉴에서 **디버깅 시작**을 선택하거나 **F5** 키를 누릅니다. 디버거가 중단점에서 일시 중지됩니다. 디버거가 중단점에 도달할 수 없는 경우 [디버깅 문제 해결](#troubleshoot-debugging)을 참조하세요.

## <a name="troubleshoot-debugging"></a>디버깅 문제 해결

로컬 IIS 디버깅에서 중단점을 진행할 수 없는 경우 다음 단계에 따라 문제를 해결합니다.

1. IIS에서 웹앱을 시작하고 올바르게 실행되는지 확인합니다. 웹앱을 실행 상태로 둡니다.

2. Visual Studio에서 **디버그 > 프로세스에 연결**을 선택하거나 **Ctrl**+**Alt**+**P**를 누르고 ASP.NET 또는 ASP.NET Core 프로세스(일반적으로 **w3wp.exe** 또는 **dotnet.exe**)에 연결합니다. 자세한 내용은 [프로세스에 연결](attach-to-running-processes-with-the-visual-studio-debugger.md) 및 [ASP.NET 프로세스의 이름 찾기 방법](how-to-find-the-name-of-the-aspnet-process.md)을 참조하세요.

**프로세스에 연결**을 사용할 때는 중단점에 연결하여 도달할 수 있지만, **디버그** > **디버깅 시작** 또는 **F5**를 사용할 때는 수행할 수 없는 경우 프로젝트 속성의 설정이 잘못되었을 수 있습니다. HOSTS 파일을 사용하는 경우에도 올바르게 구성되었는지 확인합니다.

## <a name="configure-debugging-in-the-webconfig-file"></a>web.config 파일에서 디버깅 구성

ASP.NET 프로젝트에는 기본적으로 *web.config* 파일이 있습니다. 여기에는 디버그 설정을 포함한 앱 구성 및 시작 정보가 모두 포함됩니다. 디버깅을 위해서 *web.config* 파일을 올바르게 구성해야 합니다. 이전 섹션의 **속성** 설정에서 *web.config* 파일이 업데이트됩니다. 하지만 수동으로 구성할 수도 있습니다.

> [!NOTE]
> ASP.NET Core 프로젝트에는 처음에 *web.config* 파일이 없지만, 앱 구성 및 시작 정보에 *appsettings.json* 및 *launchSettings.json* 파일을 사용합니다. 앱을 배포하면 프로젝트에 *web.config* 파일이 만들어지지만 일반적으로 디버그 정보는 포함되지 않습니다.

> [!TIP]
> 배포 프로세스에서 *web.config* 설정이 업데이트되므로, 디버깅을 시도하기 전에 디버깅을 위해 *web.config*가 구성되었는지 확인해야 합니다.

**디버깅을 위해 *web.config* 파일을 수동으로 구성하려면 다음을 수행합니다.**

1. Visual Studio에서 ASP.NET 프로젝트의 *web.config* 파일을 엽니다.

2. *web.config*는 XML 파일이므로 태그로 표시된 중첩된 섹션을 포함합니다. `configuration/system.web/compilation` 섹션을 찾습니다. (`compilation` 요소가 존재하지 않는 경우 생성합니다.)

3. `compilation` 요소의 `debug` 특성이 `true`로 설정되었는지 확인합니다. (`compilation` 요소에 `debug` 특성이 포함되지 않은 경우 이를 추가하고 `true`로 설정합니다.)

   기본 IIS Express 서버 대신 로컬 IIS를 사용하는 경우 `compilation` 요소의 `targetFramework` 특성 값이 IIS 서버의 프레임워크와 일치하는지 확인합니다.

   *web.config* 파일의 `compilation` 요소는 다음 예제와 같습니다.

   > [!NOTE]
   > 이 예제는 *web.config* 파일의 일부입니다. 일반적으로 `configuration` 및 `system.web` 요소에 추가 XML 섹션이 있으며 `compilation` 요소에는 다른 특성 및 요소가 포함될 수도 있습니다.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]가 *web.config* 파일의 변경 내용을 자동으로 검색하고 새 구성 설정을 적용합니다. 변경 내용을 적용하기 위해 컴퓨터나 IIS 서버를 다시 시작할 필요가 없습니다.

웹 사이트에는 여러 개의 가상 디렉터리 및 하위 디렉터리가 포함될 수 있으며 각 디렉터리에 *web.config* 파일이 있을 수도 있습니다. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 앱은 URL 경로의 상위 수준에 있는 *web.config* 파일에서 설정을 상속합니다. 계층적 *web.config* 파일 설정은 계층 구조에서 아래에 있는 모든 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 앱에 적용됩니다. 계층 구조에서 하위 *web.config* 파일에 있는 다른 구성을 설정하면 상위 파일의 설정이 재정의됩니다.

예를 들어, <em>www.microsoft.com/aaa/web.config</em>에서 `debug="true"`를 지정하는 경우 *aaa* 폴더 또는 *aaa* 하위 폴더의 모든 앱은 해당 설정을 상속합니다. 단, 이러한 앱 중 하나가 자체 *web.config* 파일로 설정을 재정의하는 경우는 제외합니다.

## <a name="publish-in-debug-mode-using-the-file-system"></a>파일 시스템을 사용하여 디버그 모드로 게시

여러 방법으로 IIS에 앱을 게시할 수 있습니다. 이러한 단계에서는 파일 시스템을 사용하여 디버그 게시 프로필을 만들고 배포하는 방법을 보여 줍니다. 이를 수행하려면 관리자 권한으로 Visual Studio를 실행해야 합니다.

> [!IMPORTANT]
> 코드를 변경하거나 다시 빌드하는 경우 이러한 단계를 반복하여 다시 게시해야 합니다.

1. Visual Studio에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.

3. **IIS, FTP 등**을 선택하고 **게시**를 클릭합니다.

    ![IIS에 게시](media/dbg-aspnet-local-iis.png "IIS에 게시")

4. **CustomProfile** 대화 상자에서 **게시 방법**으로 **파일 시스템**을 선택합니다.

5. **대상 위치**에서 **찾아보기**( **...** )를 선택합니다.

   - ASP.NET의 경우 **로컬 IIS**를 선택하고 앱에 대해 만든 웹 사이트를 선택한 다음, **열기**를 선택합니다.

     ![IIS에 ASP.NET 게시](media/dbg-aspnet-local-iis1.png "IIS에 ASP.NET 게시")

   - ASP.NET Core의 경우 **파일 시스템**을 선택하고 앱에 대해 설정한 폴더를 선택한 다음, **열기**를 선택합니다.

1. **새로 만들기**를 선택합니다.

1. **구성**의 드롭다운에서 **디버그**를 선택합니다.

1. **저장**을 선택합니다.

1. **게시** 대화 상자에서 **CustomProfile**(또는 방금 만든 프로필 이름)이 표시되는지, **LastUsedBuildConfiguration**이 **디버그**로 설정되어 있는지 확인합니다.

1. **게시**를 선택합니다.

    ![IIS에 게시](media/dbg-aspnet-local-iis-select-site.png "IIS에 게시")

> [!IMPORTANT]
> 디버그 모드는 사용자 앱의 성능을 크게 저하시킵니다. 최상의 성능을 위해 *web.config*에서 `debug="false"`를 설정하고 프로덕션 앱을 배포하거나 성능 측정을 수행할 때 릴리스 빌드를 지정합니다.

## <a name="see-also"></a>참조
- [ASP.NET 디버깅: 시스템 요구 사항](aspnet-debugging-system-requirements.md)
- [방법: 사용자 계정으로 작업자 프로세스 실행](how-to-run-the-worker-process-under-a-user-account.md)
- [방법: ASP.NET 프로세스의 이름 찾기](how-to-find-the-name-of-the-aspnet-process.md)
- [배포된 웹 애플리케이션 디버그](debugging-deployed-web-applications.md)
- [연습: 웹 양식 디버그](walkthrough-debugging-a-web-form.md)
- [방법: ASP.NET 예외 디버그](how-to-debug-aspnet-exceptions.md)
- [웹 애플리케이션 디버그: 오류 및 문제 해결](debugging-web-applications-errors-and-troubleshooting.md)
