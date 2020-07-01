---
title: .NET 서비스에 프로파일러를 연결하여 동시성 데이터 수집
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 24c49015915b8a1d214a833c38c5550f51c50c13
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328697"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>방법: 명령줄을 통해 .NET 서비스에 프로파일러를 연결하여 동시성 데이터 수집
이 문서에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 프로파일러를 .NET Framework 서비스에 연결하고 샘플링 방법으로 프로세스 및 스레드 동시성 데이터를 수집하는 방법을 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

> [!NOTE]
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

 동시성 데이터를 수집하려면 프로파일러를 서비스 프로세스에 연결합니다. 프로파일러가 서비스에 연결되면 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다. 프로파일링 세션을 종료하려면 프로파일러가 서비스에 연결되어 있으면 안 되고 프로파일러가 명시적으로 종료되어야 합니다. 대부분의 경우 세션 종료 시 프로파일링 환경 변수를 지우는 것이 좋습니다.

## <a name="attach-the-profiler"></a>프로파일러 연결

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>.NET Framework 서비스에 프로파일러를 연결하려면

1. 서비스를 설치합니다.

2. 명령 창을 엽니다.

3. 프로파일링 환경 변수를 초기화합니다. 유형:

     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **/globalsampleon** [ **/samplelineoff**]

    - **/globalsampleon**을 선택하면 샘플링이 사용하도록 설정됩니다.

    - **/samplelineoff**를 선택하면 수집된 데이터를 특정 소스 코드 줄에 할당하는 기능이 사용하지 않도록 설정됩니다. 이 옵션을 지정하면 데이터가 함수에만 할당됩니다.

4. 컴퓨터를 다시 시작합니다.

5. 프로파일러를 시작합니다. 유형:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]

     **/start**에는 [/output](../profiling/output.md) **:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.vsp) 파일의 이름과 위치를 지정합니다.

     **/start** 옵션과 다음 옵션을 함께 사용할 수 있습니다.

    > [!NOTE]
    > **/user** 및 **/crosssession** 옵션은 대개 서비스에 필요합니다.

    |옵션|설명|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName`|프로파일링된 프로세스를 소유한 계정의 도메인 및 사용자 이름을 지정합니다. 이 옵션은 프로세스가 로그온한 사용자 이외의 사용자로 실행 중인 경우에만 필요합니다. Windows 작업 관리자의 **프로세스** 탭에 있는 **사용자 이름** 열에 프로세스 소유자가 나열됩니다.|
    |[/crosssession](../profiling/crosssession.md)|프로세스 프로파일링 기능을 다른 세션에서 사용하도록 설정합니다. 이 옵션은 서비스가 다른 세션에서 실행 중인 경우 필요합니다. Windows 작업 관리자의 **프로세스** 탭에 있는 **세션 ID** 열에 세션 ID가 나열됩니다. **/CS**를 **/crosssession**에 대한 약어로 지정할 수 있습니다.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다.|
    |[/automark](../profiling/automark.md) **:** `Interval`|**/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500ms입니다.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.*etl*)로 수집됩니다.|

6. 필요한 경우 서비스를 시작합니다.

7. 프로파일러를 서비스에 연결합니다. 유형:

     **VSPerfCmd /attach:** `PID` [[/targetclr](../profiling/targetclr.md) **:** `Version`]

    - `PID`는 서비스의 프로세스 ID 또는 프로세스 이름을 지정합니다. [Windows 작업 관리자]에서 모든 실행 중인 프로세스의 프로세스 ID를 볼 수 있습니다.

    - **targetclr:** `Version`은 한 애플리케이션에 두 개 이상의 런타임 버전이 로드된 경우 프로파일링할 CLR(공용 언어 런타임) 버전을 지정합니다. 선택 사항입니다.

## <a name="control-data-collection"></a>데이터 수집 제어
 서비스가 실행 중이면 *VSPerfCmd.exe* 옵션을 사용하여 파일에 대한 데이터 쓰기를 시작하고 중지하는 방식으로 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하면 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- **VSPerfCmd** 옵션의 다음 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|프로세스 ID(`PID`)로 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |**/attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach**는 프로세스 ID 또는 프로세스 이름으로 지정된 프로세스에 대한 데이터 수집을 시작합니다. **/detach**는 지정된 프로세스 또는 모든 프로세스(특정 프로세스가 지정되지 않은 경우)에 대한 데이터 수집을 중지합니다.|

- **VSPerfCmd.exe**[/mark](../profiling/mark.md) 옵션을 사용하여 프로파일링 표시를 데이터 파일에 삽입할 수 있습니다. **/mark** 명령은 식별자, 타임스탬프 및 선택적 사용자 정의 텍스트 문자열을 추가합니다. 표식을 사용하여 프로파일러 보고서 및 데이터 뷰에서 데이터를 필터링할 수 있습니다. VSPerfCmd 옵션의 다음 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 프로파일러가 데이터를 수집하고 있지 않아야 합니다. 서비스를 중지하거나 **VSPerfCmd /detach** 옵션을 호출하여 동시성 방법으로 프로파일링된 애플리케이션에서 데이터를 수집하는 작업을 중지할 수 있습니다. 그러고 나서 **VSPerfCmd /shutdown** 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다. **VSPerfClrEnv /globaloff** 명령은 프로파일링 환경 변수를 지우지만 컴퓨터가 다시 시작될 때까지 시스템 구성이 다시 설정되지 않습니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. 대상 애플리케이션에서 프로파일러를 분리하려면 다음 중 하나를 수행합니다.

    - 서비스를 중지합니다.

         또는

    - **VSPerfCmd /detach**를 입력합니다.

2. 프로파일러를 종료합니다. 형식:

     **VSPerfCmd**  [Shutdown](../profiling/shutdown.md)
