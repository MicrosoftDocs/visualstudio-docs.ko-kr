---
title: '프로파일러 명령줄: 네이티브 서비스 계측, 타이밍 데이터 가져오기'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: c738a5183a7708c967192cf201e38a4f9384710e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778871"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>방법: 프로파일러 명령줄을 사용하여 네이티브 서비스 계측 및 자세한 타이밍 데이터 수집
이 문서에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 네이티브(C/C++) 서비스를 계측하고 자세한 타이밍 데이터를 수집하는 방법을 설명합니다.

> [!NOTE]
> 서비스가 컴퓨터가 운영 체제가 시작되는 경우에만 시작하는 서비스를 시작한 후 다시 시작할 수 없는 경우 계측 방법으로 서비스를 프로파일링할 수 없습니다.
>
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

 계측 방법을 사용하여 네이티브 서비스에서 자세한 타이밍 데이터를 수집하려면 [VSInstr.exe](../profiling/vsinstr.md) 도구를 사용하여 계측된 구성 요소의 버전을 생성합니다. 그런 다음 계측되지 않은 버전의 서비스를 계측된 버전으로 바꿉니다. 서비스가 수동으로 시작되도록 구성되어 있는지 확인합니다. 그런 다음 프로파일러를 시작합니다.

 서비스가 시작되면 자동으로 타이밍 데이터가 데이터 파일로 수집됩니다. 프로파일링 세션 중에 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다.

 프로파일링 세션을 종료하려면 서비스를 끈 다음 프로파일러를 명시적으로 종료합니다.

## <a name="start-the-application-with-the-profiler"></a>프로파일러를 사용하여 애플리케이션 시작

#### <a name="to-start-profiling-a-native-service"></a>네이티브 서비스 프로파일링을 시작하려면

1. 명령 프롬프트 창을 엽니다.

2. **VSInstr** 도구를 사용하여 서비스 이진 파일의 계측된 버전을 생성합니다.

3. 원래 이진을 계측된 버전으로 바꿉니다. Windows 서비스 제어 관리자에서 서비스 시작 유형이 수동으로 설정되어 있는지 확인합니다.

4. 프로파일러를 시작합니다. 유형:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:trace** 옵션은 프로파일러를 초기화합니다.

   - **/start**에는 **/output:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.*vsp*) 파일의 이름과 위치를 지정합니다.

     **/start:trace** 옵션과 다음 옵션을 함께 사용할 수 있습니다.

   > [!NOTE]
   > **/user** 및 **/crosssession** 옵션은 대개 ASP.NET 애플리케이션에 필요합니다.

   | 옵션 | 설명 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | ASP.NET 작업자 프로세스를 소유한 계정의 도메인 및 사용자 이름을 지정합니다. 프로세스가 로그온한 사용자 이외의 사용자로 실행 중인 경우 이 옵션이 필요합니다. Windows 작업 관리자의 **프로세스** 탭에 있는 **사용자 이름** 열에 프로세스 소유자가 나열됩니다. |
   | [/crosssession](../profiling/crosssession.md) | 프로세스 프로파일링 기능을 다른 로그온 세션에서 사용하도록 설정합니다. 이 옵션은 ASP.NET 애플리케이션이 다른 세션에서 실행 중인 경우 필요합니다. [Windows 작업 관리자]의 [프로세스] 탭에 있는 [세션 ID] 열에 세션 ID가 나열됩니다. **/CS**를 **/crosssession**에 대한 약어로 지정할 수 있습니다. |
   | [/waitstart](../profiling/waitstart.md)[ **:** `Interval`] | 프로파일러가 오류를 반환하기 전에 초기화할 때까지 기다리는 시간(초)을 지정합니다. `Interval`을 지정하지 않으면 프로파일러에서 무기한 기다립니다. 기본적으로 **/start**는 즉시 반환합니다. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | 데이터 수집을 일시 중지하고 프로파일러를 시작하려면 **/globaloff** 옵션을 **/start** 명령줄에 추가합니다. **/globalon**을 사용하여 프로파일링을 다시 시작합니다. |
   | [/counter](../profiling/counter.md) **:** `Config` | 구성에 지정된 프로세서 성능 카운터에서 정보를 수집합니다. 카운터 정보는 각 프로파일링 이벤트에서 수집된 데이터에 추가됩니다. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다. |
   | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500ms입니다. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | 프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.*etl*)로 수집됩니다. |

5. 서비스 제어 관리자에서 서비스를 시작합니다.

## <a name="control-data-collection"></a>데이터 수집 제어
 서비스가 실행되는 동안 *VSPerfCmd.exe* 옵션을 사용하여 프로파일러 데이터 파일에 대한 데이터 쓰기를 시작하고 중지할 수 있습니다. 데이터 수집을 제어하면 서비스의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- **VSPerfCmd** 옵션의 다음 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|프로세스 ID(`PID`)로 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|스레드 ID(`TID`)로 지정된 스레드에 대한 데이터 수집을 시작( **/threadon**) 또는 중지( **/threadoff**)합니다.|

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 계측된 구성 요소를 실행하고 있는 서비스를 중지한 다음 **VSPerfCmd**[/shutdown](../profiling/shutdown.md) 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. 서비스 제어 관리자에서 서비스를 중지합니다.

2. 프로파일러를 종료합니다. 유형:

     **VSPerfCmd /shutdown**

3. 계측된 모듈을 원본으로 바꿉니다. 필요한 경우 서비스의 시작 유형을 다시 구성합니다.

## <a name="see-also"></a>참조
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
- [계측 방법 데이터 뷰](../profiling/instrumentation-method-data-views.md)
