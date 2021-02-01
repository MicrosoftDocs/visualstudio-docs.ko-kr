---
title: 네이티브 앱에 프로파일러를 연결하여 동시성 데이터 수집
description: Visual Studio 프로파일링 도구 명령줄 도구를 사용하여 실행 중인 네이티브(C/C++) 독립 실행형 애플리케이션에 프로파일러를 연결하고 스레드 경합 데이터를 가져옵니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: fd06783f50708e13c97f7bfe00a22be26739fd9c
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801645"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>방법: 명령줄을 통해 네이티브 독립 실행형 애플리케이션에 프로파일러를 연결하여 동시성 데이터 수집
이 문서에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 프로파일러를 실행 중인 네이티브(C/C++) 독립 실행형 애플리케이션에 연결하고 스레드 경합 데이터를 수집하는 방법을 설명합니다.

> [!NOTE]
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

 프로파일러가 애플리케이션에 연결되면 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다. 프로파일링 세션을 종료하려면 프로파일러가 애플리케이션에 연결되어 있으면 안 되고 프로파일러가 명시적으로 종료되어야 합니다.

## <a name="attach-the-profiler-to-a-running-native-application"></a>실행 중인 네이티브 애플리케이션에 프로파일러 연결

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>실행 중인 네이티브 애플리케이션에 프로파일러를 연결하려면

1. 명령 프롬프트에서 다음 명령을 입력합니다.

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**

     **/start:concurrency** 옵션과 다음 표의 모든 옵션을 함께 사용할 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`Username`|프로파일러에 대한 액세스 권한을 부여할 계정의 선택적 도메인 및 사용자 이름을 지정합니다.|
    |[/crosssession](../profiling/crosssession.md)|프로세스 프로파일링 기능을 다른 로그온 세션에서 사용하도록 설정합니다.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다.|
    |[/automark](../profiling/automark.md) **:** `Interval`|**/wincounter** 와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500입니다.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.etl)로 수집됩니다.|

2. 다음 명령을 입력하여 프로파일러를 대상 애플리케이션에 연결합니다.

     **VSPerfCmd**  [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`}

     `PID`는 대상 애플리케이션의 프로세스 ID를 지정합니다. [Windows 작업 관리자]에서 모든 실행 중인 프로세스의 프로세스 ID를 볼 수 있습니다.

## <a name="control-data-collection"></a>데이터 수집 제어
 대상 애플리케이션이 실행 중이면 *VSPerfCmd.exe* 옵션을 사용하여 파일에 대한 데이터 쓰기를 시작하고 중지하는 방식으로 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하여 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- 다음 표의 옵션 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|프로세스 ID(`PID`)로 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detch](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach** 는 프로세스 ID(`PID`) 또는 프로세스 이름(*ProcName*)으로 지정된 프로세스에 대한 데이터 수집을 시작합니다. **/detach** 는 지정된 프로세스 또는 모든 프로세스(프로세스가 지정되지 않은 경우)에 대한 데이터 수집을 중지합니다.|

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 프로파일러가 데이터를 수집하고 있지 않아야 합니다. 애플리케이션을 닫거나 **VSPerfCmd /detach** 옵션을 호출하여 샘플링 방법으로 프로파일링된 애플리케이션에서 데이터를 수집하는 작업을 중지할 수 있습니다. 그러고 나서 **VSPerfCmd /shutdown** 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. 프로파일러를 닫거나 다음 명령을 입력하여 대상 애플리케이션에서 프로파일러를 분리합니다.

     **VSPerfCmd /detach**

2. 다음 명령을 입력하여 프로파일러를 종료합니다.

     **VSPerfCmd** [/shutdown](../profiling/shutdown.md)
