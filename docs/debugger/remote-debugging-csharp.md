---
title: 원격 디버그 C# 또는 VB 프로젝트 | Microsoft Docs
ms.custom:
- remotedebugging"=
- seodec18
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
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f147acae956ad380c6e85984de29d5316394c0a
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301076"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>비주얼 스튜디오에서 C# 또는 비주얼 기본 프로젝트를 원격 디버깅
다른 컴퓨터에 배포된 Visual Studio 응용 프로그램을 디버깅하려면 앱을 배포한 컴퓨터에서 원격 도구를 설치하고 실행하고 프로젝트를 구성하여 Visual Studio에서 원격 컴퓨터에 연결한 다음 앱을 실행합니다.

![원격 디버거 구성 요소](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

원격 디버깅 유니버설 Windows 앱(UWP)에 대한 자세한 내용은 [설치된 앱 패키지 디버그를](debug-installed-app-package.md)참조하십시오.

## <a name="requirements"></a>요구 사항

원격 디버거는 Windows 7 및 최신(휴대폰이 아님) 및 Windows Server 2008 서비스 팩 2부터 시작하는 Windows 서버 버전에서 지원됩니다. 요구 사항의 전체 목록은 [요구 사항](../debugger/remote-debugging.md#requirements_msvsmon)을 참조하십시오.

> [!NOTE]
> 프록시를 통해 연결된 두 컴퓨터 간의 디버깅은 지원되지 않습니다. 전화 접속 인터넷과 같이 대기 시간이 많거나 대역폭이 낮은 연결을 통해 디버깅하거나 국가 간 인터넷을 통해 디버깅하는 것은 권장되지 않으며 실패하거나 허용할 수 없을 정도로 느릴 수 있습니다.

## <a name="download-and-install-the-remote-tools"></a>원격 도구 다운로드 및 설치

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 일부 시나리오에서는 파일 공유에서 원격 디버거를 실행하는 것이 가장 효율적일 수 있습니다. 자세한 내용은 [파일 공유에서 원격 디버거 실행을](../debugger/remote-debugging.md#fileshare_msvsmon)참조하십시오.

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>원격 디버거 설정

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 추가 사용자에 대한 권한을 추가하거나, 인증 모드를 변경하거나, 원격 디버거에 대한 포트 번호를 변경해야 하는 경우 [원격 디버거 구성](../debugger/remote-debugging.md#configure_msvsmon)을 참조하십시오.

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a>프로젝트 원격 디버그
디버거는 원격 컴퓨터에 Visual C# 또는 Visual Basic 데스크톱 애플리케이션을 배포할 수 없지만 다음과 같이 원격으로 계속 디버그할 수 있습니다. 다음 절차에서는 아래 그림과 같이 **MJO-DL이라는**컴퓨터에서 디버깅을 한다고 가정합니다.

1. **MyWpf**라는 WPF 프로젝트를 만듭니다.

2. 쉽게 도달할 수 있는 코드의 임의 위치에 중단점을 설정합니다.

    예를 들어 단추 처리기에 중단점을 설정할 수 있습니다. 이렇게 하려면 MainWindow.xaml을 열고 도구 상자에서 단추 컨트롤을 추가한 다음 단추를 두 번 클릭하여 처리기를 엽니다.

3. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

4. **속성** 페이지에서 **디버그** 탭을 선택합니다.

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. **작업 디렉터리** 텍스트 상자가 비어 있는지 확인합니다.

6. **원격 컴퓨터 사용을**선택하고 텍스트 상자에 기계 **이름:port를 입력합니다.** 포트 번호는 원격 디버거 창에 표시됩니다. 각 버전의 Visual Studio에서 포트 번호가 2씩 증가합니다.

    이 예제에서는 다음을 사용합니다.
    ::: moniker range=">=vs-2019"
    비주얼 스튜디오 **2019에서 MJO-DL:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    비주얼 스튜디오 **2017에서 MJO-DL:4022**
    ::: moniker-end

7. **네이티브 코드 디버깅 사용**이 선택되지 않았는지 확인합니다.

8. 프로젝트를 빌드합니다.

9. Visual Studio 컴퓨터의 **Debug** 폴더와 동일한 경로인 폴더를 원격 컴퓨터에 만듭니다(**\<source path>\MyWPF\MyWPF\bin\Debug**).

10. Visual Studio 컴퓨터에서 방금 빌드한 실행 파일을 원격 컴퓨터에서 새로 만든 폴더에 복사합니다.

    > [!CAUTION]
    > 코드를 변경하거나 다시 빌드하지 마십시오(또는 이 단계를 반복해야 합니다). 원격 컴퓨터에 복사한 실행 파일은 로컬 소스 및 기호와 정확히 일치해야 합니다.

    프로젝트를 수동으로 복사하거나 Xcopy, 로보카피, 파워셸 또는 기타 옵션을 사용할 수 있습니다.

11. 원격 디버거가 대상 컴퓨터에서 실행되고 있는지 확인합니다(그렇지 않은 경우 **시작** 메뉴에서 **원격 디버거를** 검색합니다). 원격 디버거 창은 다음과 같습니다.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. Visual Studio에서 디버깅을 시작합니다(**디버그 > 디버깅 시작** 또는 **F5** 키).

13. 메시지가 표시되면 네트워크 자격 증명을 입력하여 원격 컴퓨터에 연결합니다.

     필요한 자격 증명은 네트워크의 보안 구성에 따라 다릅니다. 예를 들어 도메인 컴퓨터에서 도메인 이름과 암호를 입력할 수 있습니다. 비 도메인 컴퓨터에서 는 올바른 암호와 함께 <strong>MJO-DL\name@something.com</strong>컴퓨터 이름과 올바른 사용자 계정 이름 등을 입력할 수 있습니다.

     WPF 애플리케이션의 주 창이 원격 컴퓨터에서 열려 있다고 표시됩니다.

14. 필요한 경우 중단점에 부딪히기 위한 조치를 취합니다. 중단점이 활성화된 것으로 표시되어야 합니다. 활성화되지 않은 경우 애플리케이션에 대한 기호가 로드되지 않은 것입니다. 다시 시도하고 문제가 작동하지 않으면 기호 로드및 [심볼 파일 이해 및 Visual Studio의 기호 설정에서 심볼](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)로드에 대한 정보를 얻을 수 있습니다.

15. Visual Studio 컴퓨터에서 실행이 중단점에서 중지된 것이 표시됩니다.

    응용 프로그램에서 사용해야 하는 비코드 파일이 있는 경우 Visual Studio 프로젝트에 포함해야 합니다. 추가 파일을 위한 프로젝트 폴더를 만듭니다(**솔루션 탐색기**에서 **추가 > 새 폴더** 클릭). 그런 다음, 폴더에 파일을 추가합니다(**솔루션 탐색기**에서 **추가 / 기존 항목**을 클릭한 다음, 파일 선택). 각 파일에 대한 **속성** 페이지에서 **출력 디렉터리에 복사**를 **항상 복사**로 설정합니다.

## <a name="set-up-debugging-with-remote-symbols"></a>원격 기호를 사용한 디버깅 설정

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>참고 항목
- [Visual Studio의 디버깅](../debugger/index.yml)
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)
- [원격 IIS 컴퓨터의 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)