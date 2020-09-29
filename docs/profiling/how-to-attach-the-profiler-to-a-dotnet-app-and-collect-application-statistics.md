---
title: .NET 독립 실행형 앱에 프로파일러 연결, 앱 통계 가져오기
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 89c7f4141459f612f55a2253e37a6e56349fcb6a
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808053"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>방법: 명령줄을 통해 .NET Framework 독립 실행형 애플리케이션에 프로파일러를 연결하여 애플리케이션 통계 수집
이 문서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 실행 중인 .NET Framework 독립 실행형(클라이언트) 애플리케이션에 프로파일러를 연결하고 샘플링 방법을 사용하여 성능 통계를 수집하는 방법을 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.
>
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.
>
> 프로파일링 실행에 계층 상호 작용 데이터를 추가하려면 명령줄 프로파일링 도구를 사용해서 특정 절차를 수행해야 합니다. [계층 상호 작용 데이터를 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)을 참조합니다.

 .NET Framework 애플리케이션에서 성능 데이터를 수집하려면 대상 애플리케이션을 시작하기 전에 적절한 환경 변수를 초기화해야 합니다. 프로파일러가 애플리케이션에 연결되면 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다.

 프로파일링 세션을 종료하려면 프로파일러가 애플리케이션에 연결되어 있으면 안 되고 프로파일러가 명시적으로 종료되어야 합니다. 대부분의 경우 프로파일링 세션 종료 시 프로파일링 환경 변수를 지우는 것이 좋습니다.

## <a name="attach-the-profiler"></a>프로파일러 연결

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>실행 중인 .NET Framework 애플리케이션에 프로파일러를 연결하려면

1. 명령 프롬프트 창을 엽니다.

2. 프로파일링 환경 변수를 초기화합니다. 유형:

    **VSPerfClrEnv /sampleon** [ **/samplelineoff**]

   - **/samplelineoff** 옵션은 소스 코드 줄 번호 데이터를 수집하지 않도록 합니다.

3. 프로파일러를 시작합니다. 유형:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md) **:sample** 옵션은 프로파일러를 초기화합니다.

   - **/start**에는 [/output](../profiling/output.md) **:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.vsp) 파일의 이름과 위치를 지정합니다.

     **/start:sample** 옵션과 함께 다음 옵션 중 하나를 사용할 수 있습니다.

   | 옵션 | 설명 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | 프로파일링된 프로세스를 소유한 계정의 선택적 도메인 및 사용자 이름을 지정합니다. 이 옵션은 프로파일링된 애플리케이션이 로그온한 사용자 이외의 사용자로 시작된 경우에만 필요합니다. |
   | [/crosssession](../profiling/crosssession.md) | 프로세스 프로파일링 기능을 다른 로그온 세션에서 사용하도록 설정합니다. **/CS**를 **/crosssession**에 대한 약어로 지정할 수 있습니다. 이 옵션은 애플리케이션이 다른 세션에서 실행 중인 경우 필요합니다. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다. |
   | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500ms입니다. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | 프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.*etl*)로 수집됩니다. |

4. 필요한 경우 일반적인 방법으로 대상 프로그램을 시작합니다.

5. 대상 애플리케이션에 프로파일러를 연결합니다. 유형:

    **VSPerfCmd /attach:** {`PID`&#124;`ProcessName`} [`Sample Event`] [ **/targetclr:** `Version`]

   - `PID`는 대상 애플리케이션의 프로세스 ID를 지정합니다. `ProcessName`은 프로세스의 이름을 지정합니다. `ProcessName`을 지정하며 동일한 이름을 갖는 여러 프로세스가 실행되고 있으면 결과를 예측할 수 없습니다. [Windows 작업 관리자]에서 모든 실행 중인 프로세스의 프로세스 ID를 볼 수 있습니다.

   - [/targetclr](../profiling/targetclr.md) **:** `Version`은 한 애플리케이션에 두 개 이상의 런타임 버전이 로드된 경우 프로파일링할 CLR(공용 언어 런타임) 버전을 지정합니다. 선택 사항입니다.

   - 기본적으로 성능 데이터는 10,000,000번의 무중단 프로세서 클록 주기마다 샘플링됩니다. 1GH 프로세서의 경우 이는 대략 10초마다 한 번입니다. 다음 옵션 중 하나를 지정하여 클록 주기 간격을 변경하거나 다른 샘플링 이벤트를 지정할 수 있습니다. [/targetclr](../profiling/targetclr.md) **:** `Version` 애플리케이션에 둘 이상의 런타임 버전이 로드된 경우 프로파일링할 CLR의 버전을 지정합니다. 선택 사항입니다.

   |샘플 이벤트|설명|
   |-|-|
   |[/timer](../profiling/timer.md) **:** `Interval`|샘플링 간격을 `Interval`로 지정된 무중단 클록 주기 수로 변경합니다.|
   |[/pf](../profiling/pf.md) [ **:** `Interval`]|샘플링 이벤트를 페이지 폴트로 변경합니다. `Interval`이 지정되면 샘플 간의 페이지 폴트 수를 설정합니다. 기본값은 10입니다.|
   |[/sys](../profiling/sys-vsperfcmd.md) [ **:** `Interval`]|샘플링 이벤트를 운영 체제 커널에 대한 프로세스의 시스템 호출로 변경합니다(syscalls). `Interval`이 지정되면 샘플 간의 호출 수를 설정합니다. 기본값은 10입니다.|
   |[/counter](../profiling/counter.md) **:** `Config`|샘플링 이벤트 및 간격을 `Config`에 지정된 프로세서 성능 카운터 및 간격으로 변경합니다.|

## <a name="control-data-collection"></a>데이터 수집 제어
 대상 애플리케이션이 실행 중이면 *VSPerfCmd.exe* 옵션을 사용하여 프로파일러 데이터 파일에 대한 데이터 쓰기를 시작하고 중지하는 방식으로 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하면 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- 다음 옵션 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|`PID`에 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detch](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach**는 `PID` 또는 프로세스 이름(ProcName)으로 지정된 프로세스에 대한 데이터 수집을 시작합니다. **/detach**는 지정된 프로세스 또는 모든 프로세스(특정 프로세스가 지정되지 않은 경우)에 대한 데이터 수집을 중지합니다.|

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 프로파일러가 모든 프로파일링된 프로세스에서 분리되어야 하고 프로파일러가 명시적으로 종료되어야 합니다. 애플리케이션을 닫거나 **VSPerfCmd /detach** 옵션을 호출하여 샘플링 방법으로 프로파일링된 애플리케이션에서 프로파일러를 분리할 수 있습니다. 그러고 나서 **VSPerfCmd /shutdown** 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다. **VSPerfClrEnv /off** 명령은 프로파일링 환경 변수를 지웁니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. 대상 애플리케이션에서 프로파일러를 분리하려면 다음 단계 중 하나를 수행합니다.

    - **VSPerfCmd /detach** 입력

         또는

    - 대상 애플리케이션을 닫습니다.

2. 프로파일러를 종료합니다. 유형:

     **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

3. (선택 사항) 프로파일링 환경 변수를 지웁니다. 유형:

     **VSPerfClrEnv /off**

## <a name="see-also"></a>참조
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)
