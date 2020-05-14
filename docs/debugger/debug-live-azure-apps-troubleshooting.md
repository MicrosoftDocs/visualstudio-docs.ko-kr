---
title: 스냅샷 디버깅 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc0d5ce27c3241b89a1baaf540cab4f1f56d24b5
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911592"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio의 스냅샷 디버깅에 대한 문제 해결 및 알려진 문제

이 문서에 설명된 단계를 수행해도 문제가 해결되지 않으면 [개발자 커뮤니티](https://developercommunity.visualstudio.com/spaces/8/index.html)에서 문제를 검색하거나 Visual Studio에서 **도움말** > **의견 보내기** > **문제 보고**를 선택하여 새 문제를 보고합니다.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>문제: "스냅샷 디버거 연결"에서 HTTP 상태 코드 오류 발생

연결을 시도하는 동안 **출력** 창에 다음 오류가 표시되는 경우 아래에 나열된 알려진 문제일 수 있습니다. 제안된 솔루션을 시도해 보고 문제가 계속되면 이전 별칭에 연결합니다.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) 권한 없음

이 오류는 Visual Studio에서 Azure로 발급한 REST 호출이 잘못된 자격 증명을 사용함을 나타냅니다. Azure Active Directory Easy OAuth 모듈의 알려진 버그로 인해 이 오류가 발생할 수 있습니다.

다음 단계를 수행하세요.

* Visual Studio 개인 설정 계정에 연결할 Azure 구독 및 리소스에 대한 권한이 있는지 확인합니다. 이를 확인하는 빠른 방법은 **디버그** > **스냅샷 디버거 연결...**  > **Azure 리소스** > **기존 선택**의 대화 상자 또는 클라우드 탐색기에서 리소스를 사용할 수 있는지 확인하는 것입니다.
* 이 오류가 계속 지속되면 이 문서의 시작 부분에 설명된 피드백 채널 중 하나를 사용합니다.

### <a name="403-forbidden"></a>(403) 사용할 수 없음

이 오류는 권한이 거부되었음을 나타냅니다. 이는 여러 가지 문제로 인해 발생할 수 있습니다.

다음 단계를 수행하세요.

* Visual Studio 계정에 리소스에 대해 필요한 RBAC(역할 기반 Access Control) 권한이 있는 유효한 Azure 구독이 있는지 확인합니다. AppService의 경우 앱을 호스팅하는 App Service 플랜을 [쿼리](/rest/api/appservice/appserviceplans/get)할 수 있는 권한이 있는지 확인합니다.
* 클라이언트 머신의 타임스탬프가 올바르고 최신 상태인지 확인합니다. 15분을 초과하여 요청 타임스탬프가 꺼진 타임스탬프가 있는 서버는 일반적으로 이 오류를 생성합니다.
* 이 오류가 계속 지속되면 이 문서의 시작 부분에 설명된 피드백 채널 중 하나를 사용합니다.

### <a name="404-not-found"></a>(404) 찾을 수 없음

이 오류는 서버에서 웹 사이트를 찾을 수 없음을 나타냅니다.

다음 단계를 수행하세요.

* 연결하려는 App Service 리소스에서 웹 사이트를 배포하고 실행하고 있는지 확인합니다.
* https://\<resource\>.azurewebsites.net에서 사이트를 사용할 수 있는지 확인합니다.
* https://\<resource\>.azurewebsites.net에서 액세스할 때 올바르게 실행 중인 사용자 지정 웹 애플리케이션이 상태 코드 404를 반환하지 않는지 확인합니다.
* 이 오류가 계속 지속되면 이 문서의 시작 부분에 설명된 피드백 채널 중 하나를 사용합니다.

### <a name="406-not-acceptable"></a>(406) 허용되지 않음

이 오류는 서버가 요청의 Accept 헤더에 설정된 형식에 응답할 수 없음을 나타냅니다.

다음 단계를 수행하세요.

* https://\<resource\>.azurewebsites.net에서 사이트를 사용할 수 있는지 확인합니다.
* 사이트가 새 인스턴스로 마이그레이션되지 않았는지 확인합니다. 스냅샷 디버거는 이 오류를 일시적으로 생성할 수 있는 특정 인스턴스로 요청을 라우팅하기 위해 ARRAffinity 개념을 사용합니다.
* 이 오류가 계속 지속되면 이 문서의 시작 부분에 설명된 피드백 채널 중 하나를 사용합니다.

### <a name="409-conflict"></a>(409) 충돌

이 오류는 요청이 현재 서버 상태와 충돌함을 나타냅니다.

이는 사용자가 ApplicationInsights를 사용하도록 설정한 AppService에 대해 스냅샷 디버거를 연결하려고 할 때 발생하는 알려진 문제입니다. ApplicationInsights는 AppSettings를 Visual Studio와 다른 대/소문자로 설정하여 이 문제가 발생합니다.

::: moniker range=">= vs-2019"
Visual Studio 2019에서 이 문제를 해결했습니다.
::: moniker-end

다음 단계를 수행하세요.

::: moniker range="vs-2017"

* Azure Portal에서 SnapshotDebugger(SNAPSHOTDEBUGGER_EXTENSION_VERSION) 및 InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION)의 AppSettings가 대문자인지 확인합니다. 그렇지 않은 경우 사이트를 다시 시작하도록 설정을 수동으로 업데이트합니다.
::: moniker-end
* 이 오류가 계속 지속되면 이 문서의 시작 부분에 설명된 피드백 채널 중 하나를 사용합니다.

### <a name="500-internal-server-error"></a>(500) 내부 서버 오류

이 오류는 사이트가 완전히 다운되었거나 서버에서 요청을 처리할 수 없음을 나타냅니다. 스냅샷 디버거는 실행 중인 애플리케이션에서만 작동합니다. [Application Insights 스냅샷 디버거](/azure/azure-monitor/app/snapshot-debugger)는 예외에 대한 스냅샷을 제공하며 요구 사항에 가장 적합한 도구일 수 있습니다.

### <a name="502-bad-gateway"></a>(502) 잘못된 게이트웨이

이 오류는 서버 쪽 네트워킹 문제를 나타내며 일시적일 수 있습니다.

다음 단계를 수행하세요.

* 스냅샷 디버거를 다시 연결하기 전에 몇 분 정도 기다립니다.
* 이 오류가 계속 지속되면 이 문서의 시작 부분에 설명된 피드백 채널 중 하나를 사용합니다.

## <a name="issue-snappoint-does-not-turn-on"></a>문제: Snappoint가 설정되지 않음

일반 snappoint 아이콘 대신 snappoint가 있는 경고 아이콘(![Snappoint 경고 아이콘](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Snappoint 경고 아이콘"))이 표시되면 snappoint가 설정되지 않은 것입니다.

![Snappoint가 설정되지 않음](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint가 설정되지 않음")

다음 단계를 수행하세요.

1. 앱을 빌드하고 배포하는 데 사용된 것과 동일한 버전의 소스 코드가 있는지 확인합니다. 사용자의 배포에 맞게 올바른 기호를 로드하는지 확인합니다. 이렇게 하려면 스냅샷 디버그 중에 **모듈** 창을 보고 디버그하는 모듈에 대해 로드된 .pdb 파일이 기호 파일 열에 표시되는지 확인합니다. 스냅샷 디버거는 자동으로 사용자의 배포에 맞게 기호를 다운로드하여 사용하려고 합니다.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>문제: 스냅샷을 열 때 기호가 로드되지 않음

다음 창이 표시되면 기호가 로드되지 않은 것입니다.

![기호가 로드되지 않음](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "기호가 로드되지 않음")

다음 단계를 수행하세요.

- 이 페이지에서 **기호 설정 변경...** 링크를 클릭합니다. **디버깅 > 기호** 설정에서 기호 캐시 디렉터리를 추가합니다. 기호 경로가 설정되면 스냅샷 디버깅을 다시 시작합니다.

   프로젝트에서 사용할 수 있는 기호 또는 .pdb 파일은 App Service 배포와 일치해야 합니다. 대부분의 배포(Visual Studio를 통한 배포, Azure Pipelines 또는 Kudu를 통한 CI/CD 등)는 사용자의 App Service에 기호 파일을 게시합니다. 기호 캐시 디렉터리를 설정하면 Visual Studio에서 해당 기호를 사용할 수 있습니다.

   ![기호 설정](../debugger/media/snapshot-troubleshooting-symbol-settings.png "기호 설정")

- 조직이 기호 서버를 사용하거나 다른 경로에 기호를 드롭하는 경우 기호 설정을 사용하여 배포에 맞게 올바른 기호를 로드하세요.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>문제: 클라우드 탐색기에 "스냅샷 디버거 연결" 옵션이 표시되지 않음

다음 단계를 수행하세요.

- 스냅샷 디버거 구성 요소가 설치되어 있는지 확인합니다. Visual Studio 설치 관리자를 열고 Azure 워크로드에서 **스냅샷 디버거** 구성 요소를 확인합니다.
::: moniker range="< vs-2019"
- 앱이 지원되는지 확인합니다. 현재 Azure App Services에 배포된 ASP.NET(4.6.1 이상) 및 ASP.NET Core(2.0 이상) 앱만 지원됩니다.
::: moniker-end
::: moniker range=">= vs-2019"
- 앱이 지원되는지 확인합니다.
  - Azure App Services - .NET Framework 4.6.1 이상에서 실행되는 ASP.NET 애플리케이션
  - Azure App Services - Windows의 .NET Core 2.0 이상에서 실행되는 ASP.NET Core 애플리케이션
  - Azure Virtual Machines(및 가상 머신 확장 집합) - .NET Framework 4.6.1 이상에서 실행되는 ASP.NET 애플리케이션
  - Azure Virtual Machines(및 가상 머신 확장 집합) - Windows의 .NET Core 2.0 이상에서 실행되는 ASP.NET Core 애플리케이션
  - Azure Kubernetes Service - Debian 9의 .NET Core 2.2 이상에서 실행되는 ASP.NET Core 애플리케이션
  - Azure Kubernetes Service - Alpine 3.8의 .NET Core 2.2 이상에서 실행되는 ASP.NET Core 애플리케이션
  - Azure Kubernetes Service - Ubuntu 18.04의 .NET Core 2.2 이상에서 실행되는 ASP.NET Core 애플리케이션
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>문제: 진단 도구에 제한된 스냅샷만 표시됨

![제한된 snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "제한된 snappoint")

다음 단계를 수행하세요.

- 스냅샷은 메모리를 거의 차지하지 않지만 할당된 메모리를 차지합니다. 스냅샷 디버거는 서버의 메모리가 과도하게 사용되는 것을 감지하면 스냅샷을 생성하지 않습니다. 스냅샷 디버거 세션을 중지하고 다시 시도하여 이미 캡처된 스냅샷을 삭제할 수 있습니다.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>문제: 여러 버전의 Visual Studio를 사용한 스냅샷 디버깅에서 오류가 발생함

Visual Studio 2019를 사용하려면 Azure App Service에 최신 버전의 스냅샷 디버거 사이트 확장이 있어야 합니다.  이 버전은 Visual Studio 2017에서 사용하는 이전 버전의 스냅샷 디버거 사이트 확장과 호환되지 않습니다.  이전에 Visual Studio 2017의 스냅샷 디버거가 디버그했던 Azure App Service에 Visual Studio 2019의 스냅샷 디버거를 연결하려고 하면 다음 오류가 발생합니다.

![호환되지 않는 스냅샷 디버거 사이트 확장 Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "호환되지 않는 스냅샷 디버거 사이트 확장 Visual Studio 2019")

반대로 이전에 Visual Studio 2019의 스냅샷 디버거가 디버그했던 Azure App Service에 Visual Studio 2017을 사용하여 스냅샷 디버거를 연결하면 다음 오류가 발생합니다.

![호환되지 않는 스냅샷 디버거 사이트 확장 Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "호환되지 않는 스냅샷 디버거 사이트 확장 Visual Studio 2017")

이 문제를 해결하려면 Azure Portal에서 다음 앱 설정을 삭제하고 스냅샷 디버거를 다시 연결하세요.

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>문제: 스냅샷 디버깅에 문제가 있으며 더 많은 로깅을 사용하도록 설정해야 함

### <a name="enable-agent-logs"></a>에이전트 로그 사용

에이전트 로깅을 사용하거나 사용하지 않도록 설정하려면 Visual Studio를 열고 ‘도구&gt;옵션&gt;스냅샷 디버거&gt;에이전트 로깅 사용’으로 이동합니다.  ‘세션을 시작할 때 오래된 에이전트 로그 삭제’도 사용하도록 설정되어 있는 경우 Visual Studio 연결이 성공할 때마다 이전 에이전트 로그가 삭제됩니다. 

에이전트 로그는 다음 위치에 있습니다.

- App Services:
  - App Service의 Kudu 사이트(yourappservice.**scm**.azurewebsites.net)로 이동한 후 디버그 콘솔로 이동합니다.
  - 에이전트 로그는 다음 디렉터리에 저장됩니다.  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - VM에 로그인하면 에이전트 로그가 다음과 같이 저장됩니다.  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - /tmp/diag/AgentLogs/* 디렉터리로 이동합니다.

### <a name="enable-profilerinstrumentation-logs"></a>프로파일러/계측 로그 사용

계측 로그는 다음 위치에 있습니다.

- App Services:
  - 오류 로깅은 자동으로 D:\Home\LogFiles\eventlog.xml로 전송되며, 이벤트는 `<Provider Name="Instrumentation Engine" />` 또는 "프로덕션 중단점"으로 표시됩니다.
- VM/VMSS:
  - VM에 로그인하고 이벤트 뷰어를 엽니다.
  - 다음 보기를 엽니다. *Windows Logs>Application*.
  - ‘프로덕션 중단점’ 또는 ‘계측 엔진’을 사용하여 ‘이벤트 원본’별로 ‘현재 로그를 필터링’합니다.    
- AKS
  - 계측 엔진 로깅은 /tmp/diag/log.txt(DockerFile의 MicrosoftInstrumentationEngine_FileLogPath 설정)에서 수행됩니다.
  - 프로덕션 중단점 로그는 /tmp/diag/shLog.txt에 있습니다.

## <a name="known-issues"></a>알려진 문제

- 동일한 App Service에 대해 여러 Visual Studio 클라이언트를 사용하는 스냅샷 디버깅은 현재 지원되지 않습니다.
- ASP.NET Core 프로젝트에서는 Roslyn IL 최적화가 일부만 지원됩니다. 일부 ASP.NET Core 프로젝트의 경우 일부 변수를 볼 수 없거나 조건문에 사용할 수 없습니다.
- *$FUNCTION* 또는 *$CALLER*와 같은 특수 변수는 ASP.NET Core 프로젝트의 조건문이나 logpoint에서 평가할 수 없습니다.
- 스냅샷 디버깅은 [로컬 캐싱](/azure/app-service/app-service-local-cache)이 켜져 있는 App Services에서 작동하지 않습니다.
- 스냅샷 디버깅 API Apps는 현재 지원되지 않습니다.

## <a name="site-extension-upgrade"></a>사이트 확장 업그레이드

스냅샷 디버깅 및 Application Insights에 영향을 미치는 ICorProfiler는 업그레이드하는 동안 사이트 프로세스에 로드되어 파일 잠금 문제를 일으킵니다. 프로덕션 사이트에 가동 중지 시간이 발생하지 않도록 다음 프로세스를 사용하는 것이 좋습니다.

- App Service 내에 [배포 슬롯](/azure/app-service/web-sites-staged-publishing)을 만들고 이 슬롯에 사이트를 배포합니다.
- 이 슬롯을 Visual Studio에 있는 클라우드 탐색기 또는 Azure Portal의 프로덕션과 교환합니다.
- 슬롯 사이트를 중지합니다. 모든 인스턴스의 사이트 w3wp.exe 프로세스를 종료하는 데는 몇 초가 걸립니다.
- Kudu 사이트 또는 Azure Portal(‘App Service 블레이드 > 개발 도구 > 확장 > 업데이트’)에서 슬롯 사이트 확장을 업그레이드합니다. 
- 슬롯 사이트를 시작합니다. 사이트를 방문하여 다시 사이트를 준비하는 것이 좋습니다.
- 슬롯을 프로덕션과 교환합니다.

## <a name="see-also"></a>참조

- [Visual Studio의 디버깅](../debugger/index.yml)
- [스냅샷 디버거를 사용하여 라이브 ASP.NET 앱 디버그](../debugger/debug-live-azure-applications.md)
- [스냅샷 디버거를 사용하여 라이브 ASP.NET Azure Virtual Machines\Virtual Machines Scale Sets 디버그](../debugger/debug-live-azure-virtual-machines.md)
- [스냅샷 디버거를 사용하여 라이브 ASP.NET Azure Kubernetes 디버그](../debugger/debug-live-azure-kubernetes.md)
- [스냅샷 디버깅 FAQ](../debugger/debug-live-azure-apps-faq.md)
