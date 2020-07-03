---
title: 프로파일러 명령줄 - 네이티브 클라이언트 앱 열기, 동시성 데이터 가져오기
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 0aeebe82e3c7b574b65ab463a7bfd986d43d46ef
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85327656"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>방법: 명령줄을 통해 프로파일러와 함께 독립 실행형 네이티브 애플리케이션을 시작하여 동시성 데이터 수집
이 항목은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 네이티브 독립 실행형(클라이언트) 애플리케이션을 시작하고 프로세스 및 스레드 동시성 데이터를 수집하는 방법을 설명합니다.

 프로파일링 세션은 다음과 같은 부분으로 구성됩니다.

- 프로파일러를 사용하여 애플리케이션 시작

- 데이터 수집 제어

- 프로파일링 세션 종료

> [!NOTE]
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

## <a name="start-the-application-with-the-profiler"></a>프로파일러를 사용하여 애플리케이션 시작
 프로파일러를 사용하여 대상 애플리케이션을 시작하려면 [VSPerfCmd.exe](../profiling/vsperfcmd.md) **/start** 및 **/launch** 옵션을 사용하여 프로파일러를 초기화하고 애플리케이션을 시작합니다. **/start** 및 **/launch**와 해당 개별 옵션을 지정할 수 있습니다. **/globaloff** 옵션을 추가하여 대상 애플리케이션 시작 시 데이터 수집을 일시 중지할 수도 있습니다. 그런 다음 **/globalon**을 사용하여 데이터 수집을 시작합니다.

#### <a name="to-start-an-application-with-the-profiler"></a>프로파일러를 사용하여 애플리케이션을 시작하려면

1. 명령 프롬프트에서 다음 명령을 입력합니다.

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]

     **/start**에는 [/output](../profiling/output.md) **:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.vsp) 파일의 이름과 위치를 지정합니다.

     **/start:concurrency** 옵션과 다음 표의 모든 옵션을 함께 사용할 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다.|
    |[/automark](../profiling/automark.md) **:** `Interval`|**/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500입니다.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.etl)로 수집됩니다.|

2. 다음을 입력하여 대상 애플리케이션을 시작합니다.

     **VSPerfCmd** [/launch](../profiling/launch.md) **:** `AppName` [`Options`]

     **/launch** 옵션과 다음 표의 모든 옵션을 함께 사용할 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:** `Arguments`|대상 애플리케이션에 전달할 명령줄 인수가 포함된 문자열을 지정합니다.|
    |[/console](../profiling/console.md)|대상 명령줄 애플리케이션을 별도의 창에서 시작합니다.|
    |[/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|한 애플리케이션이 두 개 이상의 CLR(공용 언어 런타임) 버전을 로드할 경우 프로파일링할 CLR 버전을 지정합니다.|

## <a name="control-data-collection"></a>데이터 수집 제어
 대상 애플리케이션이 실행 중이면 *VSPerfCmd.exe* 옵션을 사용하여 파일에 대한 데이터 쓰기를 시작하고 중지하는 방식으로 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하여 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- 다음 표의 옵션 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|프로세스 ID(`PID`)로 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detch](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach**는 프로세스 ID(`PID`) 또는 프로세스 이름(*ProcName*)으로 지정된 프로세스에 대한 데이터 수집을 시작합니다. **/detach**는 지정된 프로세스 또는 모든 프로세스(프로세스가 지정되지 않은 경우)에 대한 데이터 수집을 중지합니다.|

- **VSPerfCmd.exe**[/mark](../profiling/mark.md) 옵션을 사용하여 프로파일링 표시를 데이터 파일에 삽입할 수 있습니다. **/mark** 명령은 식별자, 타임스탬프 및 선택적 사용자 정의 텍스트 문자열을 추가합니다. 표식을 사용하여 프로파일러 보고서 및 데이터 뷰에서 데이터를 필터링할 수 있습니다.

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 프로파일러가 데이터를 수집하고 있지 않아야 합니다. 프로파일링된 애플리케이션을 닫거나 **VSPerfCmd /detach** 옵션을 호출하여 동시성 데이터 수집을 중지할 수 있습니다. 그러고 나서 **VSPerfCmd /shutdown** 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. 프로파일러를 닫거나 명령 프롬프트에서 다음 명령을 입력하여 대상 애플리케이션에서 프로파일러를 분리합니다.

     **VSPerfCmd /detach**

2. 명령 프롬프트에서 다음 명령을 입력하여 프로파일러를 종료합니다.

     **VSPerfCmd** [/shutdown](../profiling/shutdown.md)