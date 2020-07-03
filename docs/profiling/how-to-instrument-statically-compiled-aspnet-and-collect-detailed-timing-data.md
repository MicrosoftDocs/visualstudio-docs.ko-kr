---
title: 프로파일러 명령줄 - 정적 ASP.NET 앱 계측, 타이밍 데이터 가져오기
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 97d8e18d68ecaf0abf2b3b94e6c22ea6ba3237de
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85327918"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>방법: 명령줄에서 프로파일러를 사용하여 정적으로 컴파일된 ASP.NET 웹 애플리케이션 계측 및 자세한 타이밍 데이터 수집
이 문서에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 미리 컴파일된 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 구성 요소 또는 웹 사이트를 계측하고 자세한 타이밍 데이터를 수집하는 방법을 설명합니다.

> [!NOTE]
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.
>
> 프로파일링 실행에 계층 상호 작용 데이터를 추가하려면 명령줄 프로파일링 도구를 사용해서 특정 절차를 수행해야 합니다. [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)을 참조하세요.

 계측 방법을 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 구성 요소에서 자세한 타이밍 데이터를 수집하려면 [VSInstr.exe](../profiling/vsinstr.md) 도구를 사용하여 계측된 구성 요소의 버전을 생성합니다. 구성 요소를 호스트하는 컴퓨터에서 구성 요소의 계측되지 않은 버전을 계측된 버전으로 바꿉니다. 그런 다음 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 도구를 사용하여 전역 프로파일링 환경 변수를 초기화하고 호스트 컴퓨터를 다시 시작합니다. 그런 다음 프로파일러를 시작합니다.

 계측된 구성 요소가 실행되면 자동으로 타이밍 데이터가 데이터 파일로 수집됩니다. 프로파일링 세션 중에 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다.

 프로파일링 세션을 종료하려면 구성 요소를 호스팅하는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 닫은 다음 프로파일러를 명시적으로 종료합니다. 대부분의 경우 세션 종료 시 프로파일링 환경 변수를 지우는 것이 좋습니다.

## <a name="start-to-profile"></a>프로파일링 시작

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>ASP.NET 웹 구성 요소 계측 및 프로파일링을 시작하려면

1. 명령 프롬프트 창을 엽니다.

2. **VSInstr** 도구를 사용하여 대상 애플리케이션의 계측된 버전을 생성합니다. 필요한 경우 ASP.NET 호스트 컴퓨터의 애플리케이션 이진 파일을 계측된 이진 파일로 바꿉니다.

3. .NET 프로파일링 환경 변수를 초기화합니다. 명령 프롬프트 창에서 다음을 입력합니다.

    **VSPerfClrEnv /globaltraceon**

4. 컴퓨터를 다시 시작합니다.

5. 명령 프롬프트 창을 엽니다. 필요한 경우 프로파일러 도구 경로를 설정합니다.

6. 프로파일러를 시작합니다. 유형:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md) **:trace** 옵션은 프로파일러를 초기화합니다.

   - **/start**에는 [/output](../profiling/output.md) **:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.vsp) 파일의 이름과 위치를 지정합니다.

     **/start:trace** 옵션과 다음 옵션을 함께 사용할 수 있습니다.

   > [!NOTE]
   > **/user** 및 **/crosssession** 옵션은 대개 ASP.NET 애플리케이션에 필요합니다.

   | 옵션 | 설명 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | ASP.NET 작업자 프로세스를 소유한 계정의 도메인 및 사용자 이름을 지정합니다. 프로세스가 로그온한 사용자 이외의 사용자로 실행 중인 경우 이 옵션이 필요합니다. Windows 작업 관리자의 **프로세스** 탭에 있는 **사용자 이름** 열에 프로세스 소유자가 나열됩니다. |
   | [/crosssession](../profiling/crosssession.md) | 프로세스 프로파일링 기능을 다른 로그온 세션에서 사용하도록 설정합니다. 이 옵션은 ASP.NET 애플리케이션이 다른 세션에서 실행 중인 경우 필요합니다. Windows 작업 관리자의 **프로세스** 탭에 있는 세션 ID 열에 세션 식별자가 나열됩니다. **/CS**를 **/crosssession**에 대한 약어로 지정할 수 있습니다. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다. |
   | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500ms입니다. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | 프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.*etl*)로 수집됩니다. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | 데이터 수집을 일시 중지하고 프로파일러를 시작하려면 **/globaloff** 옵션을 **/start** 명령줄에 추가합니다. **/globalon**을 사용하여 프로파일링을 다시 시작합니다. |

7. 계측된 구성 요소를 포함하는 웹 사이트를 엽니다.

## <a name="control-data-collection"></a>데이터 수집 제어
 대상 애플리케이션이 실행 중이면 *VSPerfCmd.exe* 옵션을 사용하여 파일에 대한 데이터 쓰기를 시작하고 중지하는 방식으로 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하면 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- 다음 옵션 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|프로세스 ID(`PID`)로 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|스레드 ID(`TID`)로 지정된 스레드에 대한 데이터 수집을 시작( **/threadon**) 또는 중지( **/threadoff**)합니다.|

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 닫은 다음, IIS(인터넷 정보 서비스) **IISReset** 명령을 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 닫습니다. 그런 다음 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다.

 **VSPerfClrEnv /globaloff** 명령은 프로파일링 환경 변수를 지웁니다. 새 환경 설정을 적용하려면 컴퓨터를 다시 시작해야 합니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 닫습니다.

2. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 닫습니다. 유형:

    **IISReset /stop**

3. 프로파일러를 종료합니다. 유형:

    **VSPerfCmd /shutdown**

4. (선택 사항) 프로파일링 환경 변수를 지웁니다. 유형:

    **VSPerfCmd /globaloff**

5. 컴퓨터를 다시 시작합니다.

## <a name="see-also"></a>참조
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [계측 방법 데이터 뷰](../profiling/instrumentation-method-data-views.md)
