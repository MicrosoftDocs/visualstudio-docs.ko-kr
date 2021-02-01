---
title: ASP.NET에 프로파일러를 연결하여 앱 통계 가져오기
description: Visual Studio 프로파일링 도구 명령줄 도구를 사용하여 ASP.NET 웹앱에 프로파일러를 연결하고 샘플링 방법을 통해 성능 통계를 가져옵니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: f79591c58865631b20aecb3554e9502a22f6c7b9
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801626"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>방법: 명령줄을 통해 ASP.NET 웹 애플리케이션에 프로파일러를 연결하여 애플리케이션 통계 수집
이 문서에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 프로파일러를 ASP.NET 웹 애플리케이션에 연결하고 샘플링 방법을 통해 성능 통계를 수집하는 방법에 대해 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.
>
> 프로파일링 실행에 계층 상호 작용 데이터를 추가하려면 명령줄 프로파일링 도구를 사용해서 특정 절차를 수행해야 합니다. [계층 상호 작용 데이터를 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)을 참조합니다.
>
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

 ASP.NET 웹 애플리케이션에서 성능 데이터를 수집하려면 적절한 환경 변수를 초기화해야 하고, ASP.NET 웹 애플리케이션을 호스팅하는 컴퓨터를 다시 시작하여 웹 서버에서 프로파일링하도록 구성해야 합니다.

 그런 다음 웹 사이트를 호스팅하는 ASP.NET 작업자 프로세스에 프로파일러를 연결합니다. 프로파일러가 애플리케이션에 연결되면 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다.

 프로파일링 세션을 종료하려면 프로파일러를 프로파일링된 애플리케이션에서 분리하고 명시적으로 종료해야 합니다. 대부분의 경우 세션 종료 시 프로파일링 환경 변수를 지우는 것이 좋습니다.

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>프로파일러 시작 및 ASP.NET 웹 애플리케이션에 연결

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>ASP.NET 웹 애플리케이션에 프로파일러를 연결하려면

1. 명령 프롬프트 창을 엽니다.

2. 프로파일링 환경 변수를 초기화합니다. 유형:

    **VSPerfClrEnv /globalsampleon** [ **/samplelineoff**]

   - **/globalsampleon** 을 선택하면 샘플링이 사용하도록 설정됩니다.

   - **/samplelineoff** 를 선택하면 수집된 데이터를 특정 소스 코드 줄에 할당하는 기능이 사용하지 않도록 설정됩니다. 이 옵션을 지정하면 데이터가 함수에만 할당됩니다.

3. 컴퓨터를 다시 시작합니다.

4. 프로파일러를 시작합니다. 다음을 입력합니다. **VSPerfCmd** [/start](../profiling/start.md) **:sample** [/output](../profiling/output.md) **:** `OutputFile`[`Options`]

   - **/start:sample** 옵션은 프로파일러를 초기화합니다.

   - **/start** 에는 **/output:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.vsp) 파일의 이름과 위치를 지정합니다.

     **/start:sample** 옵션과 함께 다음 옵션 중 하나를 사용할 수 있습니다.

   > [!NOTE]
   > **/user** 및 **/crosssession** 옵션은 대개 ASP.NET 애플리케이션에 필요합니다.

   | 옵션 | 설명 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | ASP.NET 작업자 프로세스를 소유한 계정의 도메인 및 사용자 이름을 지정합니다. 이 옵션은 프로세스가 로그온한 사용자 이외의 사용자로 실행 중인 경우 필요합니다. Windows 작업 관리자의 **프로세스** 탭에 있는 **사용자 이름** 열에 프로세스 소유자가 나열됩니다. |
   | [/crosssession](../profiling/crosssession.md) | 프로세스 프로파일링 기능을 다른 로그온 세션에서 사용하도록 설정합니다. 이 옵션은 ASP.NET 애플리케이션이 다른 세션에서 실행 중인 경우 필요합니다. Windows 작업 관리자의 프로세스 탭에 있는 세션 ID 열에 세션 식별자가 나열됩니다. **/CS** 를 **/crosssession** 에 대한 약어로 지정할 수 있습니다. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다. |
   | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter** 와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500ms입니다. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | 프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.etl)로 수집됩니다. |

5. 일반적인 방법으로 ASP.NET 웹 애플리케이션을 시작합니다.

6. 프로파일러를 ASP.NET 작업자 프로세스에 연결합니다. 다음을 입력합니다. **VSPerfCmd** [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md) **:** `Version`]

   - `PID`는 ASP.NET 작업자 프로세스의 프로세스 ID를 지정하고, `ProcName`은 작업자 프로세스의 이름을 지정합니다. Windows 작업 관리자에서 실행 중인 모든 프로세스의 프로세스 ID와 이름을 볼 수 있습니다.

   - 기본적으로 성능 데이터는 10,000,000번의 무중단 프로세서 클록 주기마다 샘플링됩니다. 이는 1GH 프로세서에서 초당 약 100회 정도 샘플링합니다. 다음 **VSPerfCmd** 옵션 중 하나를 지정하여 클록 주기 간격을 변경하거나 다른 샘플링 이벤트를 지정할 수 있습니다.

   |샘플 이벤트|설명|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:** `Interval`|샘플링 간격을 `Interval`로 지정된 무중단 클록 주기 수로 변경합니다.|
   |[/pf](../profiling/pf.md)[ **:** `Interval`]|샘플링 이벤트를 페이지 폴트로 변경합니다. `Interval`이 지정되면 샘플 간의 페이지 폴트 수를 설정합니다. 기본값은 10입니다.|
   |[/sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|샘플링 이벤트를 운영 체제 커널에 대한 프로세스의 시스템 호출로 변경합니다(syscalls). `Interval`이 지정되면 샘플 간의 호출 수를 설정합니다. 기본값은 10입니다.|
   |[/counter](../profiling/counter.md) **:** `Config`|샘플링 이벤트 및 간격을 `Config`에 지정된 프로세서 성능 카운터 및 간격으로 변경합니다.|
   |[/targetclr](../profiling/targetclr.md) **:** `Version`|한 애플리케이션에 두 개 이상의 런타임 버전이 로드된 경우 프로파일링할 CLR(공용 언어 런타임) 버전을 지정합니다.|

   - **targetclr:** `Version`은 한 애플리케이션에 둘 이상의 런타임 버전이 로드될 때 프로파일링할 CLR 버전을 지정합니다. 선택 사항입니다.

## <a name="control-data-collection"></a>데이터 수집 제어
 애플리케이션이 실행되는 동안 *VSPerfCmd.exe* 옵션을 사용하여 파일에 대한 데이터 쓰기를 시작하고 중지함으로써 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하면 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- **VSPerfCmd** 옵션의 다음 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:** `PID`|`PID`에 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detch](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach** 는 `PID` 또는 프로세스 이름(ProcName)으로 지정된 프로세스에 대한 데이터 수집을 시작합니다. **/detach** 는 지정된 프로세스 또는 모든 프로세스(특정 프로세스가 지정되지 않은 경우)에 대한 데이터 수집을 중지합니다.|

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 닫은 다음, IIS(인터넷 정보 서비스) **IISReset** 명령을 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 닫습니다. 그런 다음 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다.

 **VSPerfClrEnv /globaloff** 명령은 프로파일링 환경 변수를 지웁니다. 새 환경 설정을 적용하려면 컴퓨터를 다시 시작해야 합니다.

 **VSPerfClrEnv /globaloff** 명령은 프로파일링 환경 변수를 지우지만 컴퓨터가 다시 시작될 때까지 시스템 구성이 다시 설정되지 않습니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. 다음 중 하나를 수행하여 대상 애플리케이션에서 프로파일러를 분리합니다.

   - **VSPerfCmd /detach** 입력

      또는

   - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 닫습니다.

2. 프로파일러를 종료합니다. 다음을 입력합니다. **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

3. (선택 사항) 프로파일링 환경 변수를 지웁니다. 유형:

    **VSPerfCmd /globaloff**

4. 컴퓨터를 다시 시작합니다.

## <a name="see-also"></a>참조
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)
