---
title: .NET 앱에 프로파일러를 연결하여 메모리 데이터 수집
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 04dcf800074476b285a07e36db5a85fa3a366585
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779131"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>방법: 명령줄을 통해 .NET Framework 독립 실행형 애플리케이션에 프로파일러를 연결하여 메모리 데이터 수집

이 문서에서는 Visual Studio 프로파일링 도구 명령줄 도구를 사용하여 프로파일러를 실행 중인 .NET Framework 독립 실행형(클라이언트) 애플리케이션에 연결하고 메모리 데이터를 수집하는 방법을 설명합니다.

> [!NOTE]
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

.NET Framework 애플리케이션에 연결하고 메모리 데이터를 수집하려면 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 도구를 사용하여 대상 애플리케이션이 시작되기 전에 적절한 환경 변수를 초기화해야 합니다. 프로파일러가 애플리케이션에 연결되면 *VSPerfCmd.exe* 도구를 사용하여 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다.

프로파일링 세션을 종료하려면 프로파일러가 모든 프로파일링된 프로세스에서 분리되어야 하고 프로파일러가 명시적으로 종료되어야 합니다. 대부분의 경우 세션 종료 시 프로파일링 환경 변수를 지우는 것이 좋습니다.

## <a name="attach-the-profiler"></a>프로파일러 연결

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>실행 중인 .NET Framework 애플리케이션에 프로파일러를 연결하려면

1. 명령 프롬프트 창을 엽니다.

2. 프로파일링 환경 변수를 초기화합니다. 유형:

     **VSPerfClrEnv** { **/samplegc** &#124; **/samplegclife**} [ **/samplelineoff**]

    - **/samplegc** 및 **/samplegclife** 옵션은 메모리 할당 데이터만을 수집할지, 아니면 메모리 할당 및 개체 수명 데이터를 둘 다 수집할지 지정합니다. 하나의 옵션만을 지정해야 합니다.

        |옵션|설명|
        |------------|------------------|
        |**/samplegc**|메모리 할당 데이터만 수집합니다.|
        |**/samplegclife**|메모리 할당 및 개체 수명 데이터를 둘 다 수집합니다.|

    - **/samplelineoff** 옵션은 소스 코드 줄 번호 데이터를 수집하지 않도록 합니다.

3. 프로파일러를 시작합니다. 유형:

     **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md) **:sample** 옵션은 프로파일러를 초기화합니다.

   - **/start**에는 [/output](../profiling/output.md) **:** `OutputFile` 옵션이 필요합니다. `OutputFile`은 프로파일링 데이터(.vsp) 파일의 이름과 위치를 지정합니다.

     **/start:sample** 옵션과 다음 옵션을 함께 사용할 수 있습니다.

     | 옵션 | 설명 |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | 프로파일링된 프로세스를 소유한 계정의 도메인 및 사용자 이름을 지정합니다. 이 옵션은 프로세스가 로그온한 사용자 이외의 사용자로 실행 중인 경우에만 필요합니다. [Windows 작업 관리자]의 [프로세스] 탭에 있는 [사용자 이름] 열에 프로세스 소유자가 나열됩니다. |
     | [/crosssession &#124; /cs](../profiling/crosssession.md) | 프로세스 프로파일링 기능을 다른 세션에서 사용하도록 설정합니다. 이 옵션은 애플리케이션이 다른 세션에서 실행 중인 경우 필요합니다. [Windows 작업 관리자]의 [프로세스] 탭에 있는 [세션 ID] 열에 세션 식별자가 나열됩니다. **/CS**를 **/crosssession**에 대한 약어로 지정할 수 있습니다. |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 프로파일링 중에 수집할 Windows 성능 카운터를 지정합니다. |
     | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter**와 함께 사용해야 합니다. Windows 성능 카운터 수집 이벤트 사이에 경과하는 시간(밀리초)을 지정합니다. 기본값은 500ms입니다. |

4. 필요한 경우 일반적인 방법으로 대상 프로그램을 시작합니다.

5. 대상 애플리케이션에 프로파일러를 연결합니다. 유형:

     **VSPerfCmd**  [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md) **:** `Version`]

    - `PID`는 대상 애플리케이션의 프로세스 ID를 지정합니다. `ProcessName`은 프로세스의 이름을 지정합니다. `ProcessName`을 지정하며 동일한 이름을 갖는 여러 프로세스가 실행되고 있으면 결과를 예측할 수 없습니다. [Windows 작업 관리자]에서 모든 실행 중인 프로세스의 프로세스 ID를 볼 수 있습니다.

    - **/targetclr:** `Version`은 한 애플리케이션에 두 개 이상의 런타임 버전이 로드된 경우 프로파일링할 CLR(공용 언어 런타임) 버전을 지정합니다. 선택 사항입니다.

## <a name="control-data-collection"></a>데이터 수집 제어

대상 애플리케이션이 실행 중이면 *VSPerfCmd.exe* 옵션을 사용하여 파일에 대한 데이터 쓰기를 시작하고 중지하는 방식으로 데이터 수집을 제어할 수 있습니다. 데이터 수집을 제어하면 애플리케이션의 시작 또는 종료와 같이 프로그램 실행의 특정 부분에 대한 데이터를 수집할 수 있습니다.

### <a name="to-start-and-stop-data-collection"></a>데이터 수집을 시작 및 중지하려면

- 다음 옵션 쌍을 사용하여 데이터 수집을 시작 및 중지합니다. 각 옵션을 개별 명령줄에서 지정합니다. 데이터 수집을 여러 번 켜고 끌 수 있습니다.

    |옵션|설명|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대한 데이터 수집을 시작( **/globalon**) 또는 중지( **/globaloff**)합니다.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|`PID`에 지정된 프로세스에 대한 데이터 수집을 시작( **/processon**) 또는 중지( **/processoff**)합니다.|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detch](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach**는 `PID` 또는 프로세스 이름(ProcName)으로 지정된 프로세스에 대한 데이터 수집을 시작합니다. **/detach**는 지정된 프로세스 또는 모든 프로세스(특정 프로세스가 지정되지 않은 경우)에 대한 데이터 수집을 중지합니다.|

## <a name="end-the-profiling-session"></a>프로파일링 세션 종료

프로파일링 세션을 종료하려면 프로파일러가 모든 프로파일링된 프로세스에서 분리되어야 하고 프로파일러가 명시적으로 종료되어야 합니다. 애플리케이션을 닫거나 **VSPerfCmd /detach** 옵션을 호출하여 샘플링 방법으로 프로파일링된 애플리케이션에서 프로파일러를 분리할 수 있습니다. 그러고 나서 **VSPerfCmd /shutdown** 옵션을 호출하여 프로파일러를 끄고 프로파일링 데이터 파일을 닫습니다. **VSPerfClrEnv /off** 명령은 프로파일링 환경 변수를 지웁니다.

### <a name="to-end-a-profiling-session"></a>프로파일링 세션을 종료하려면

1. 대상 애플리케이션에서 프로파일러를 분리하려면 다음 단계 중 하나를 수행합니다.

    - **VSPerfCmd /detach** 입력

         또는

    - 대상 애플리케이션을 닫습니다.

2. 프로파일러를 종료합니다. 유형:

     **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

3. (선택 사항) 프로파일링 환경 변수를 지웁니다. 유형:

     **VSPerfCmd /off**

## <a name="see-also"></a>참조

[독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
[.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md)
