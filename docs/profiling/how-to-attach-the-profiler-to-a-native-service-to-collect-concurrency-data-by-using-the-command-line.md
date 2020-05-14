---
title: 'VSPerfCmd: 네이티브 서비스에 프로파일러를 연결하여 동시성 데이터 가져오기'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 705e55363f4f8657da20fe66cd4369188f133cdb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776610"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>방법: 명령줄을 통해 네이티브 서비스에 프로파일러를 연결하여 동시성 데이터 수집
이 문서에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 프로파일러를 네이티브 (C/C++) 서비스에 연결하고 샘플링 방법으로 프로세스 및 스레드 동시성 데이터를 수집하는 방법을 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

> [!NOTE]
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

 프로파일러가 서비스에 연결되면 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다. 프로파일링 세션을 종료하려면 프로파일러가 서비스에 연결되어 있으면 안 되고 Profiler가 명시적으로 종료되어야 합니다.

## <a name="attach-the-profiler"></a>프로파일러 연결
 프로파일러를 네이티브 서비스에 연결하려면 **VSPerfCmd/start** 및 **/attach** 옵션을 사용하여 프로파일러를 초기화하고 대상 애플리케이션에 연결합니다. **/start** 및 **/attach**와 해당 개별 옵션을 단일 명령줄에서 지정할 수 있습니다. **/globaloff** 옵션을 추가하여 대상 애플리케이션 시작 시 데이터 수집을 일시 중지할 수도 있습니다. 그런 다음 **/globalon**을 사용하여 데이터 수집을 시작합니다.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>네이티브 서비스에 프로파일러를 연결하려면

1. 서비스가 실행되고 있지 않으면 서비스를 시작합니다.

2. 명령 프롬프트에서 다음을 입력하여 프로파일러를 시작합니다.

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency   /output:** `OutputFile` [`Options`]

   - **/start**에는 [/output](../profiling/output.md) **:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.vsp) 파일의 이름과 위치를 지정합니다.

     **/start** 옵션과 다음 표의 모든 옵션을 함께 사용할 수 있습니다.

   > [!NOTE]
   > 대부분 서비스에는 **/user** 및 **/crosssession** 옵션이 필요합니다.

   | 옵션 | 설명 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`UserName` | 프로파일러에 대한 액세스 권한을 부여할 계정의 선택적 도메인 및 사용자 이름을 지정합니다. |
   | [/crosssession](../profiling/crosssession.md) | 프로세스 프로파일링 기능을 다른 로그온 세션에서 사용하도록 설정합니다. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다. |
   | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500입니다. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | 프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.etl)로 수집됩니다. |

3. 명령 프롬프트에서 다음 명령을 입력하여 프로파일러를 서비스에 연결합니다.

    **VSPerfCmd /attach:** `PID`

    `PID`는 대상 애플리케이션의 프로세스 ID 또는 프로세스 이름을 지정합니다. [Windows 작업 관리자]에서 모든 실행 중인 프로세스의 프로세스 ID를 볼 수 있습니다.

## <a name="control-data-collection"></a>데이터 수집 제어
 대상 애플리케이션이 실행 중이면 *VSPerfCmd.exe* 옵션을 사용하여 파일에 대한 데이터 쓰기를 시작하고 중지하는 방식으로 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하여 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- 다음 표의 옵션 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|프로세스 ID(`PID`)로 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detch](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach**는 프로세스 ID(`PID`) 또는 프로세스 이름(*ProcName*)으로 지정된 프로세스에 대한 데이터 수집을 시작합니다. **/detach**는 지정된 프로세스 또는 모든 프로세스(프로세스가 지정되지 않은 경우)에 대한 데이터 수집을 중지합니다.|

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 프로파일러가 데이터를 수집하고 있지 않아야 합니다. 서비스를 중지하거나 **VSPerfCmd /detach** 옵션을 호출하여 동시성 방법으로 프로파일링되고 있는 네이티브 서비스에서 데이터를 수집하는 작업을 중지할 수 있습니다. 그러고 나서 **VSPerfCmd /shutdown** 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. 서비스를 중지하거나 명령 프롬프트에서 다음 명령을 입력하여 대상 애플리케이션에서 프로파일러를 분리합니다.

     **VSPerfCmd /detach** 입력

2. 명령 프롬프트에서 다음 명령을 입력하여 프로파일러를 종료합니다.

     **VSPerfCmd** [/shutdown](../profiling/shutdown.md)
