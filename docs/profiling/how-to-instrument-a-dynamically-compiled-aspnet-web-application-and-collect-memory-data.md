---
title: 프로파일러 명령줄 - 동적 ASP.NET 앱 계측, 메모리 데이터 가져오기
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 7c1fafd3b21dd40da1215e7864c6d66090589d03
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328069"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>방법: 프로파일러 명령줄을 통해 동적으로 컴파일된 ASP.NET 웹 애플리케이션 계측 및 메모리 데이터 수집
이 항목에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구의 명령줄 도구를 사용하여 계측 프로파일링 방법으로 동적으로 컴파일된 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 애플리케이션에 대한 자세한 .NET 메모리 할당 및 개체 수명 데이터를 수집하는 방법을 설명합니다.

> [!NOTE]
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션에서 성능 데이터를 수집하려면 [VSInstr.exe](../profiling/vsinstr.md) 도구를 통해 동적으로 컴파일된 애플리케이션 파일을 계측하도록 대상 애플리케이션의 *web.config* 파일을 수정합니다. 적절한 환경 변수를 설정하여 .NET 메모리 프로파일링을 사용하도록 설정하고 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 호스팅하는 서버를 구성하려면 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 도구를 사용한 다음, 컴퓨터를 다시 시작합니다.

 데이터를 수집하려면 프로파일러를 시작한 다음, 대상 애플리케이션을 실행합니다. 프로파일러는 애플리케이션에 연결된 경우 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다. 적절한 데이터를 수집한 경우 애플리케이션을 닫고 인터넷 정보 서비스(IIS) 작업자 프로세스를 닫은 다음, 프로파일러를 종료합니다.

 프로파일링 작업을 마치면 *web.config* 파일 및 웹 서버를 원래 상태로 복원합니다.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET 웹 애플리케이션 및 웹 서버 구성

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET 웹 애플리케이션 및 웹 서버를 구성하려면

1. 대상 애플리케이션의 *web.config* 파일을 수정합니다. [방법: 계측할 web.config 파일 수정 및 동적으로 컴파일된 ASP.NET 웹 애플리케이션 프로파일링](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md)을 참조하세요.

2. 웹 애플리케이션을 호스팅하는 컴퓨터에서 명령 프롬프트 창을 엽니다.

3. 프로파일링 환경 변수를 초기화합니다. 유형:

     **VSPerfClrEnv /globaltracegc**

     또는

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc**는 메모리 할당 데이터를 수집하도록 설정합니다.

    - **/globaltracegclife**는 메모리 할당 데이터 및 개체 수명 데이터를 수집하도록 설정합니다.

4. 컴퓨터를 다시 시작합니다.

## <a name="run-the-profiling-session"></a>프로파일링 세션 실행

#### <a name="to-profile-the-aspnet-web-application"></a>ASP.NET 웹 애플리케이션을 프로파일링하려면

1. 프로파일러를 시작합니다. 유형:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:trace** 옵션은 프로파일러를 초기화합니다.

   - **/start**에는 **/output:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.*vsp*) 파일의 이름과 위치를 지정합니다.

     **/start:trace** 옵션과 다음 옵션을 함께 사용할 수 있습니다.

   > [!NOTE]
   > **/user** 및 **/crosssession** 옵션은 대개 ASP.NET 애플리케이션에 필요합니다.

   | 옵션 | 설명 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 소유한 계정의 선택적 도메인 및 사용자 이름을 지정합니다. 프로세스가 로그온한 사용자 이외의 사용자로 실행 중인 경우 이 옵션이 필요합니다. Windows 작업 관리자의 **프로세스** 탭에 있는 **사용자 이름** 열에 이름이 나열됩니다. |
   | [/crosssession](../profiling/crosssession.md) | 프로세스 프로파일링 기능을 다른 세션에서 사용하도록 설정합니다. 이 옵션은 애플리케이션이 다른 세션에서 실행 중인 경우 필요합니다. Windows 작업 관리자의 **프로세스** 탭에 있는 **세션 ID** 열에 세션 ID가 나열됩니다. **/CS**를 **/crosssession**에 대한 약어로 지정할 수 있습니다. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | 데이터 수집을 일시 중지한 상태로 프로파일러를 시작합니다. [/globalon](../profiling/globalon-and-globaloff.md)을 사용하여 프로파일링을 다시 시작합니다. |
   | [/counter](../profiling/counter.md) **:** `Config` | `Config`에 지정된 프로세서 성능 카운터에서 정보를 수집합니다. 카운터 정보는 각 프로파일링 이벤트에서 수집된 데이터에 추가됩니다. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다. |
   | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500ms입니다. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | 프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.*etl*)로 수집됩니다. |

2. 일반적인 방법으로 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 시작합니다.

## <a name="control-data-collection"></a>데이터 수집 제어
 대상 애플리케이션이 실행 중이면 *VSPerfCmd.exe* 옵션을 사용하여 프로파일러 데이터 파일에 대한 데이터 쓰기를 시작하고 중지하는 방식으로 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하면 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- 다음 옵션 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|프로세스 ID(`PID`)로 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|스레드 ID(`TID`)로 지정된 스레드에 대한 데이터 수집을 시작( **/threadon**) 또는 중지( **/threadoff**)합니다.|

- **VSPerfCmd.exe**[/mark](../profiling/mark.md) 옵션을 사용하여 프로파일링 표시를 데이터 파일에 삽입할 수 있습니다. **/mark** 명령은 식별자, 타임스탬프 및 선택적 사용자 정의 텍스트 문자열을 추가합니다. 표식을 사용하여 프로파일러 보고서 및 데이터 뷰에서 데이터를 필터링할 수 있습니다.

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 대상 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 닫고, IIS(인터넷 정보 서비스)를 중지하여 프로파일링된 프로세스를 중지하고, 프로파일러를 종료합니다. 그런 다음, IIS를 다시 시작합니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 닫습니다.

2. IIS(인터넷 정보 서비스)를 다시 설정하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 닫습니다. 유형:

    **IISReset /stop**

3. 프로파일러를 종료합니다. 유형:

    **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

4. IIS를 다시 시작합니다. 유형:

    **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>애플리케이션 및 컴퓨터 구성 복원
 모든 프로파일링을 완료한 후 *web.config* 파일을 바꾸고, 프로파일링 환경 변수를 지우고, 컴퓨터를 다시 시작하여 서버 및 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 애플리케이션을 원래 상태로 복원합니다.

#### <a name="to-restore-the-application-and-computer-configuration"></a>애플리케이션 및 컴퓨터 구성을 복원하려면

1. *web.config* 파일을 원본 파일의 복사본으로 바꿉니다.

2. (선택 사항) 프로파일링 환경 변수를 지웁니다. 유형:

     **VSPerfCmd /globaloff**

3. 컴퓨터를 다시 시작합니다.

## <a name="see-also"></a>참조
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md)
