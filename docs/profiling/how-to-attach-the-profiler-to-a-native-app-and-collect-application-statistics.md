---
title: 프로파일러를 네이티브 앱에 연결하여 앱 통계 수집
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 9d463413833ad476b8d6ad90369f53267e3f7cff
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328667"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>방법: 명령줄을 통해 네이티브 독립 실행형 애플리케이션에 프로파일러를 연결하여 애플리케이션 통계 수집
이 문서에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 실행 중인 네이티브 독립 실행형(클라이언트) 애플리케이션에 프로파일러를 연결하고 샘플링 방법을 사용하여 성능 통계를 수집하는 방법을 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.
>
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

 프로파일러가 애플리케이션에 연결되면 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다. 프로파일링 세션을 종료하려면 프로파일러가 애플리케이션에 연결되어 있으면 안 되고 프로파일러가 명시적으로 종료되어야 합니다.

## <a name="attach-the-profiler"></a>프로파일러 연결
 프로파일러를 사용하여 프로파일러를 대상 애플리케이션에 연결하려면 **VSPerfCmd/start** 및 **/attach** 옵션을 사용하여 프로파일러를 초기화하고 대상 애플리케이션에 연결합니다. **/start** 및 **/attach**와 해당 개별 옵션을 단일 명령줄에서 지정할 수 있습니다. **/globaloff** 옵션을 추가하여 대상 애플리케이션 시작 시 데이터 수집을 일시 중지할 수도 있습니다. 그런 다음 **/globalon**을 사용하여 데이터 수집을 시작합니다.

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>실행 중인 .NET Framework 애플리케이션에 프로파일러를 연결하려면

1. 명령 프롬프트 창을 엽니다.

2. 프로파일러를 시작합니다. 유형:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md) **:sample** 옵션은 프로파일러를 초기화합니다.

   - **/start**에는 [/output](../profiling/output.md) **:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.vsp) 파일의 이름과 위치를 지정합니다.

     **/start:sample** 옵션과 다음 옵션을 함께 사용할 수 있습니다.

   | 옵션 | 설명 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | 프로파일링된 프로세스를 소유한 계정의 도메인 및 사용자 이름을 지정합니다. 이 옵션은 프로세스가 로그온한 사용자 이외의 사용자로 실행 중인 경우에만 필요합니다. [Windows 작업 관리자]의 [프로세스] 탭에 있는 [사용자 이름] 열에 프로세스 소유자가 나열됩니다. |
   | [/crosssession](../profiling/crosssession.md) | 프로세스 프로파일링 기능을 다른 세션에서 사용하도록 설정합니다. 이 옵션은 ASP.NET 애플리케이션이 다른 세션에서 실행 중인 경우 필요합니다. Windows 작업 관리자의 프로세스 탭에 있는 세션 ID 열에 세션 식별자가 나열됩니다. **/CS**를 **/crosssession**에 대한 약어로 지정할 수 있습니다. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다. |
   | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500ms입니다. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | 프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.*etl*)로 수집됩니다. |

3. 대상 애플리케이션에 프로파일러를 연결합니다. 유형:

    **VSPerfCmd**  [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [`Sample Event`]

    `PID`는 대상 애플리케이션의 프로세스 ID를 지정합니다. `ProcessName`은 프로세스의 이름을 지정합니다. `ProcessName`을 지정하며 동일한 이름을 갖는 여러 프로세스가 실행되고 있으면 결과를 예측할 수 없습니다. [Windows 작업 관리자]에서 모든 실행 중인 프로세스의 프로세스 ID를 볼 수 있습니다.

    기본적으로 성능 데이터는 10,000,000번의 무중단 프로세서 클록 주기마다 샘플링됩니다. 이 크기는 1GH 프로세서에서 초당 약 100번 정도가 됩니다. 다음 옵션 중 하나를 지정하여 클록 주기 간격을 변경하거나 다른 샘플링 이벤트를 지정할 수 있습니다.

   |샘플 이벤트|설명|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:** `Interval`|샘플링 간격을 `Interval`로 지정된 무중단 클록 주기 수로 변경합니다.|
   |[/pf](../profiling/pf.md)[ **:** `Interval`]|샘플링 이벤트를 페이지 폴트로 변경합니다. `Interval`이 지정되면 샘플 간의 페이지 폴트 수를 설정합니다. 기본값은 10입니다.|
   |[/sys](../profiling/sys-vsperfcmd.md) [ **:** `Interval`]|샘플링 이벤트를 운영 체제 커널에 대한 프로세스의 시스템 호출로 변경합니다(syscalls). `Interval`이 지정되면 샘플 간의 호출 수를 설정합니다. 기본값은 10입니다.|
   |[/counter](../profiling/counter.md) **:** `Config`|샘플링 이벤트 및 간격을 `Config`에 지정된 프로세서 성능 카운터 및 간격으로 변경합니다.|

## <a name="control-data-collection"></a>데이터 수집 제어
 대상 애플리케이션이 실행 중이면 *VSPerfCmd.exe* 옵션을 사용하여 프로파일러 데이터 파일에 대한 데이터 쓰기를 시작하고 중지할 수 있습니다. 데이터 수집을 제어하면 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- **VSPerfCmd** 옵션의 다음 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|`PID`로 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach**는 `PID`로 지정된 프로세스에 대한 데이터 수집을 시작합니다. **/detach**는 모든 프로세스에 대한 데이터 수집을 중지합니다.|

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
