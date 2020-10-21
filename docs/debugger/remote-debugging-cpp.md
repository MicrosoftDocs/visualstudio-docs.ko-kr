---
title: C++ 프로젝트 원격 디버깅 | Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "92298730"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Visual Studio에서 C++ 프로젝트 원격 디버깅
다른 컴퓨터에서 Visual Studio 애플리케이션을 디버그하려면 앱을 배포할 컴퓨터에 원격 도구를 설치 및 실행하고 Visual Studio에서 원격 컴퓨터에 연결하도록 프로젝트를 구성한 후 앱을 배포하고 실행합니다.

![원격 디버거 구성 요소](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

유니버설 Windows 앱(UWP) 원격 디버깅에 대한 자세한 내용은 [설치된 앱 패키지 디버그](debug-installed-app-package.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

원격 디버거는 Windows 7 이상(Phone 아님) 및 Windows Server 버전 Windows Server 2008 서비스 팩 2 이상에서 지원됩니다. 요구 사항 전체 목록은 [요구 사항](../debugger/remote-debugging.md#requirements_msvsmon)을 참조하세요.

> [!NOTE]
> 프록시를 통해 연결된 두 컴퓨터 간의 디버깅은 지원되지 않습니다. 대기 시간이 길거나 대역폭이 낮은 연결(예: 전화 접속 인터넷) 또는 해외 인터넷을 통해 디버그하는 것은 오류가 발생하거나 지나치게 느릴 수 있으므로 권장하지 않습니다.

## <a name="download-and-install-the-remote-tools"></a>원격 도구 다운로드 및 설치

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 일부 시나리오에서는 파일 공유에서 원격 디버거를 실행하는 것이 가장 효율적일 수 있습니다. 자세한 내용은 [파일 공유에서 원격 디버거 실행](../debugger/remote-debugging.md#fileshare_msvsmon)을 참조하세요.

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> 원격 디버거 설정

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 추가 사용자를 위해 사용 권한을 추가하거나 원격 디버거의 인증 모드 또는 포트 번호를 변경해야 하는 경우 [원격 디버거 구성](../debugger/remote-debugging.md#configure_msvsmon)을 참조하세요.

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a> C++ 프로젝트 원격 디버그
 다음 절차에서 프로젝트의 이름 및 경로는 C:\remotetemp\MyMfc이고 원격 컴퓨터의 이름은 **MJO-DL**입니다.

1. **mymfc**라는 MFC 애플리케이션을 만듭니다.

2. `CMainFrame::OnCreate`의 시작 부분에서 쉽게 도달할 수 있는 애플리케이션의 임의 위치(예: **MainFrm.cpp**)에 중단점을 설정합니다.

3. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **디버깅** 탭을 엽니다.

4. **실행할 디버거**를 **원격 Windows 디버거**로 설정합니다.

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. 다음과 같이 속성을 변경합니다.

   |설정|값|
   |-|-|
   |원격 명령|C:\remotetemp\mymfc.exe|
   |작업 디렉터리|C:\remotetemp|
   |원격 서버 이름|MJO-DL:*portnumber*|
   |연결|Windows 인증을 사용한 원격|
   |디버거 형식|네이티브 전용|
   |배포 디렉터리|C:\remotetemp.|
   |배포할 추가 파일|C:\data\mymfcdata.txt.|

    추가 파일을 배포하는 경우(선택 사항) 두 컴퓨터 모두에 폴더가 있어야 합니다.

6. 솔루션 탐색기에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **Configuration Manager**를 선택합니다.

7. **디버그** 구성의 경우 **배포** 확인란을 선택합니다.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. 디버깅을 시작합니다(**디버그 / 디버깅 시작** 또는 **F5**).

9. 실행 파일이 원격 컴퓨터에 자동으로 배포됩니다.

10. 메시지가 표시되면 네트워크 자격 증명을 입력하여 원격 컴퓨터에 연결합니다.

     필요한 자격 증명은 네트워크의 보안 구성에 따라 다릅니다. 예를 들어 도메인 컴퓨터에서는 보안 인증서를 선택하거나 도메인 이름 및 암호를 입력할 수 있습니다. 도메인이 아닌 컴퓨터에서는 컴퓨터 이름, 올바른 사용자 계정 이름(예: <strong>MJO-DL\name@something.com</strong>)을 올바른 암호와 함께 입력할 수 있습니다.

11. Visual Studio 컴퓨터에서 실행이 중단점에서 중지된 것이 표시됩니다.

    > [!TIP]
    > 또는 별도의 단계로 파일을 배포할 수 있습니다. **솔루션 탐색기**에서 **mymfc** 노드를 마우스 오른쪽 단추로 클릭하고 **배포**를 선택합니다.

    애플리케이션에 필요한 비코드 파일이 있는 경우 **원격 Windows 디버거** 페이지의 **배포할 추가 파일**에서 해당 파일을 지정할 수 있습니다.

    또는 프로젝트에 파일을 포함하고 각 파일에 대한 **속성** 페이지에서 **콘텐츠** 속성을 **예**로 설정할 수 있습니다. 이러한 파일은 **원격 Windows 디버거** 페이지에 지정된 **배포 디렉터리**에 복사됩니다. 또한 **배포 디렉터리**의 하위 폴더에 파일을 복사해야 하는 경우 **항목 종류**를 **파일 복사**로 변경하고 여기에서 추가 속성을 지정할 수 있습니다.

## <a name="set-up-debugging-with-remote-symbols"></a>원격 기호를 사용한 디버깅 설정

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>참조
- [Visual Studio의 디버깅](../debugger/index.yml)
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)
- [원격 IIS 컴퓨터의 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)