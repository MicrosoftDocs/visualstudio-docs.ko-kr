---
title: ASP.NET 앱에 프로파일러를 연결하여 메모리 데이터 수집
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: f2b9ea7799656b0dd7dacd35bde62dc84aea08dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779066"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>방법: 명령줄을 통해 ASP.NET 웹 애플리케이션에 프로파일러를 연결하여 메모리 데이터 수집
이 문서에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구를 사용하여 프로파일러를 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션에 연결하고 .NET Framework 메모리 할당의 수와 크기에 대한 데이터를 수집하는 방법을 설명합니다. .NET Framework 메모리 개체의 수명에 대한 데이터를 수집할 수도 있습니다.

> [!NOTE]
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션에서 성능 데이터를 수집하려면 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 도구를 사용해서 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 호스팅하는 컴퓨터에서 적합한 환경 변수를 초기화해야 합니다. 그런 다음 컴퓨터를 다시 시작해서 프로파일링용으로 웹 서버를 구성해야 합니다.

 그런 다음 [VSPerfCmd.exe](../profiling/vsperfcmd.md) 도구를 사용하여 프로파일러를 웹 사이트를 호스팅하는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스에 연결합니다. 프로파일러가 애플리케이션에 연결되면 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다.

 프로파일링 세션을 종료하려면 프로파일러가 애플리케이션에 연결되어 있으면 안 되고 프로파일러가 명시적으로 종료되어야 합니다. 대부분의 경우 세션 종료 시 프로파일링 환경 변수를 지우는 것이 좋습니다.

## <a name="attach-the-profiler"></a>프로파일러 연결

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>ASP.NET 웹 애플리케이션에 프로파일러를 연결하려면

1. 명령 프롬프트 창을 엽니다.

2. 프로파일링 환경 변수를 초기화합니다. 유형:

    **VSPerfClrEnv** { **/globalsamplegc** &#124; **/globalsamplegclife**} [ **/samplelineoff**]

   - 옵션 **/globalsamplegc** 및 **/globalsamplegclife**는 수집할 메모리 데이터의 유형을 지정합니다.

        다음 옵션 중 하나만 지정합니다.

       |옵션|설명|
       |------------|-----------------|
       |**/globalsamplegc**|메모리 할당 데이터를 수집하도록 합니다.|
       |**/globalsamplegclife**|메모리 할당 데이터 및 개체 수명 데이터를 둘 다 수집하도록 합니다.|

   - 옵션 **/samplelineoff**를 선택하면 수집된 데이터를 특정 소스 코드 줄에 할당하는 기능이 사용하지 않도록 설정됩니다. 이 옵션을 지정하면 데이터가 함수 수준에서 할당됩니다.

3. 컴퓨터를 다시 시작하여 새 환경 구성을 설정합니다.

4. 명령 프롬프트 창을 엽니다. 필요에 따라 프로파일러 경로 환경 변수를 설정합니다.

5. 프로파일러를 시작합니다. 유형:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:sample** 옵션은 프로파일러를 초기화합니다.

   - **/start**에는 **/output:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.vsp) 파일의 이름과 위치를 지정합니다.

     **/start:sample** 옵션과 다음 옵션을 함께 사용할 수 있습니다.

   > [!NOTE]
   > **/user** 및 **/crosssession** 옵션은 대개 ASP.NET 애플리케이션에 필요합니다.

   | 옵션 | 설명 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | ASP.NET 작업자 프로세스를 소유한 계정의 도메인 및 사용자 이름을 지정합니다. 이 옵션은 프로세스가 로그온한 사용자 이외의 사용자로 실행 중인 경우 필요합니다. [Windows 작업 관리자]의 [프로세스] 탭에 있는 [사용자 이름] 열에 프로세스 소유자가 나열됩니다. |
   | [/crosssession](../profiling/crosssession.md) | 프로세스 프로파일링 기능을 다른 로그온 세션에서 사용하도록 설정합니다. 이 옵션은 ASP.NET 애플리케이션이 다른 세션에서 실행 중인 경우 필요합니다. Windows 작업 관리자의 프로세스 탭에 있는 세션 ID 열에 세션 식별자가 나열됩니다. **/CS**를 **/crosssession**에 대한 약어로 지정할 수 있습니다. |
   | [/waitstart](../profiling/waitstart.md) [ **:** `Interval`] | 프로파일러가 오류를 반환하기 전에 초기화될 때까지 기다리는 시간(초)을 지정합니다. `Interval`을 지정하지 않으면 프로파일러에서 무기한 기다립니다. 기본적으로 **/start**는 즉시 반환합니다. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다. |
   | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500ms입니다. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | 프로파일링 중에 수집할 ETW(Windows용 이벤트 추적) 이벤트를 지정합니다. ETW 이벤트는 별도의 파일(.etl)로 수집됩니다. |

6. 일반적인 방법으로 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 시작합니다.

7. 프로파일러를 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스에 연결합니다. 유형:

    **VSPerfCmd**  [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md) **:** `Version`]

   - 프로세스 ID `(PID)`는 프로세스 ID 또는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스의 프로세스 이름을 지정합니다. [Windows 작업 관리자]에서 모든 실행 중인 프로세스의 프로세스 ID를 볼 수 있습니다.

   - **/targetclr:** `Version`은 한 애플리케이션에 두 개 이상의 런타임 버전이 로드된 경우 프로파일링할 CLR(공용 언어 런타임) 버전을 지정합니다.

## <a name="control-data-collection"></a>데이터 수집 제어
 애플리케이션이 실행 중이면 **VSPerfCmd.exe** 옵션을 사용하여 프로파일러 데이터 파일에 대한 데이터 쓰기를 시작하고 중지하는 방식으로 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하면 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

#### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- **VSPerfCmd** 옵션의 다음 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|`PID`로 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |**/attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;:`ProcName`}]|**/attach**는 프로세스 ID 또는 프로세스 이름으로 지정된 프로세스에 대한 데이터 수집을 시작합니다. **/detach**는 지정된 프로세스 또는 모든 프로세스(특정 프로세스가 지정되지 않은 경우)에 대한 데이터 수집을 중지합니다.|

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료
 프로파일링 세션을 종료하려면 웹 애플리케이션에서 프로파일러를 분리해야 합니다. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 다시 시작하거나 **VSPerfCmd /detach** 옵션을 호출하여 샘플링 방법으로 프로파일링된 애플리케이션에서 데이터 수집을 중지할 수 있습니다. 그러고 나서 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다. **VSPerfClrEnv /globaloff** 명령은 프로파일링 환경 변수를 지우지만 컴퓨터가 다시 시작될 때까지 시스템 구성이 다시 설정되지 않습니다.

#### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. 대상 애플리케이션에서 프로파일러를 분리하려면 다음 단계 중 하나를 수행합니다.

   - Type **VSPerfCmd** [/detach](../profiling/detach.md)

      또는

   - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 닫습니다. 유형:

     **IISReset /stop**

2. 프로파일러를 종료합니다. 유형:

    **VSPerfCmd /shutdown**

3. (선택 사항) 프로파일링 환경 변수를 지웁니다. 유형:

    **VSPerfCmd /globaloff**

4. 컴퓨터를 다시 시작합니다. 필요에 따라 IIS(인터넷 정보 서비스)를 다시 시작합니다. 유형:

    **IISReset /start**

## <a name="see-also"></a>참조
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md)
