---
title: 원격 디버깅 | Microsoft Docs
description: Visual Studio 원격 디버거를 사용하여 다른 컴퓨터에 배포된 Visual Studio 애플리케이션을 디버그합니다.
ms.custom:
- remotedebugging
- seodec18
- SEO-VS-2020
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f67035dc2f7a33fb436c0c51ba2214272ab2cf79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891425"
---
# <a name="remote-debugging"></a>Remote Debugging
다른 컴퓨터에 배포된 Visual Studio 애플리케이션을 디버그할 수 있습니다. 이렇게 하려면 Visual Studio 원격 디버거를 사용합니다.

원격 디버깅에 대한 자세한 지침은 다음 항목을 참조하세요.

|시나리오|링크|
|-|-|-|
|Azure App Service|[Azure의 원격 디버그 ASP.NET](../debugger/remote-debugging-azure.md) 또는 Visual Studio Enterprise의 경우 [스냅샷 디버거](../debugger/debug-live-azure-applications.md)|
|Azure VM|[Azure의 원격 디버그 ASP.NET](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Azure Service Fabric 애플리케이션 디버그](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[ASP.NET Core 원격 디버그](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) 또는 [ASP.NET 원격 디버그](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# 또는 Visual Basic|[C# 또는 Visual Basic 프로젝트](../debugger/remote-debugging-csharp.md) 원격 디버그|
|C++|[C++ 프로젝트 원격 디버그](../debugger/remote-debugging-cpp.md)|
|유니버설 Windows 앱(UWP)|[원격 컴퓨터에서 UWP 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md) 또는 [설치된 앱 패키지 디버그](../debugger/debug-installed-app-package.md)|

원격 디버거만 다운로드하여 설치하고 시나리오에 대한 추가 지침이 필요하지 않은 경우 이 문서의 단계를 수행합니다.

## <a name="download-and-install-the-remote-tools"></a>원격 도구 다운로드 및 설치

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> 요구 사항

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> (선택 사항) 파일 공유에서 원격 디버거를 실행하려면

Visual Studio Community, Professional 또는 Enterprise가 이미 설치되어 있는 컴퓨터에서는 원격 디버거(*msvsmon.exe*)가 있습니다. 일부 시나리오의 경우 원격 디버깅을 설정하는 가장 쉬운 방법은 파일 공유에서 원격 디버거(msvsmon.exe)를 실행하는 것입니다. 사용 제한 사항에 대한 자세한 내용은 원격 디버거의 도움말 페이지(원격 디버거의 **도움말 > 사용법**)를 참조하세요.

1. Visual Studio 버전과 일치하는 디렉터리에서 *msvsmon.exe* 를 찾습니다.

   ::: moniker range=">=vs-2019"

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Visual Studio 컴퓨터의 **Remote Debugger** 폴더를 공유합니다.

3. 원격 컴퓨터의 공유 폴더에서 *msvsmon.exe* 를 실행합니다. [설치 지침](#bkmk_setup)을 따릅니다.

> [!TIP]
> 명령줄 설치 및 명령줄 참조에 대해서는 Visual Studio가 설치된 컴퓨터의 명령줄에서 ``msvsmon.exe /?``를 입력하여(또는 원격 디버거에서 **도움말 > 사용법** 으로 이동하여) *msvsmon.exe* 에 대한 도움말 페이지를 참조하세요.

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> 원격 디버거 설정

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> 원격 디버거 구성
원격 디버거를 처음으로 시작한 후에 원격 디버거 구성의 일부 측면을 변경할 수 있습니다.

- 다른 사용자가 원격 디버거에 연결할 수 있는 권한을 추가해야 하는 경우 **도구 > 사용 권한** 을 선택합니다. 사용 권한을 부여하거나 거부하려면 관리자 권한이 있어야 합니다.

     > [!IMPORTANT]
     > Visual Studio 컴퓨터에서 사용하는 사용자 계정과 다른 사용자 계정으로 원격 디버거를 실행할 수 있지만 원격 디버거의 사용 권한에 다른 사용자 계정을 추가해야 합니다.

     또는 **/allow \<username>** 매개 변수를 사용하여 명령줄에서 원격 디버거를 시작할 수 있습니다(**msvsmon /allow \<username@computer>** ).

- 인증 모드 또는 포트 번호를 변경하거나 원격 도구의 시간 제한 값을 지정하려면 **도구 > 옵션** 을 선택합니다.

     기본적으로 사용되는 포트 번호 목록은 [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요.

     > [!WARNING]
     > 원격 도구를 인증 안 함 모드에서 실행할 수도 있지만 이 모드는 사용하지 않는 것이 좋습니다. 이 모드에서 실행할 때는 네트워크 보안이 없습니다. 네트워크에 악의적인 트래픽이나 유해 트래픽 위험이 확실히 없는 경우에만 인증 안 함 모드를 선택하세요.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> (선택 사항) 원격 디버거를 서비스로 구성
ASP.NET 및 기타 서버 환경에서 디버그하는 경우 원격 디버거를 관리자 권한으로 실행해야 하며, 항상 실행하려면 원격 디버거를 서비스로 실행해야 합니다.

 원격 디버거를 서비스로 구성하려면 다음 단계를 수행합니다.

1. **원격 디버거 구성 마법사** (rdbgwiz.exe)를 찾습니다. (원격 디버거와 별도의 애플리케이션입니다.) 해당 마법사는 원격 도구를 설치하는 경우에만 사용할 수 있으며 Visual Studio와 함께 설치되지 않습니다.

2. 구성 마법사 실행을 시작합니다. 첫 페이지가 표시되면 **다음** 을 클릭합니다.

3. **Visual Studio 2015 원격 디버거를 서비스로 실행** 확인란을 선택합니다.

4. 사용자 계정 및 암호의 이름을 추가합니다.

    이 계정에 **서비스로 로그온** 사용자 권한을 추가해야 할 수 있습니다(**시작** 페이지 또는 창에서 **로컬 보안 정책**(secpol.msc)을 찾거나 명령 프롬프트에서 **secpol** 을 입력함). 창이 나타나면 **사용자 권한 할당** 을 두 번 클릭한 다음 오른쪽 창에서 **서비스로 로그온** 을 찾습니다. 폴더를 두 번 클릭합니다. **속성** 창에 사용자 계정을 추가하고 **확인** 을 클릭합니다. **다음** 을 클릭합니다.

5. 원격 도구가 통신하는 데 사용할 네트워크 유형을 선택합니다. 하나 이상의 네트워크 형식을 선택해야 합니다. 컴퓨터가 도메인을 통해 연결된 경우 첫 번째 항목을 선택해야 합니다. 컴퓨터가 작업 그룹 또는 홈 그룹을 통해 연결된 경우 두 번째 또는 세 번째 항목을 선택해야 합니다. **다음** 을 클릭합니다.

6. 서비스를 시작할 수 있는 경우 **Visual Studio 원격 디버거 구성 마법사를 성공적으로 완료했습니다.** 가 표시됩니다. 서비스를 시작할 수 없는 경우 **Visual Studio 원격 디버거 구성 마법사 완료 실패** 가 표시됩니다. 이 페이지에서는 서비스를 시작하기 위해 수행할 몇 가지 팁도 제공합니다.

7. **마침** 을 클릭합니다.

   이제 원격 디버거가 서비스로 실행됩니다. **제어판 > 서비스** 로 이동하고 **Visual Studio 2015 원격 디버거** 를 찾아 이를 확인할 수 있습니다.

   **제어판 > 서비스** 에서 원격 디버거 서비스를 중지하고 시작할 수 있습니다.

## <a name="set-up-debugging-with-remote-symbols"></a>원격 기호를 사용한 디버깅 설정

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>참조

- [디버거 소개](../debugger/debugger-feature-tour.md)
- [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)
- [원격 IIS 컴퓨터의 ASP.NET Core 원격 디버깅](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)