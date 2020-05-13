---
title: VSPerfCmd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 53378c3d210ef9666df251d68a3eec570f8caa2f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778000"
---
# <a name="vsperfcmd"></a>VSPerfCmd
*VSPerfCmd.exe* 도구는 성능 데이터 수집을 시작하고 중지하는 데 사용됩니다. 이 도구는 다음 구문을 사용합니다.

```cmd
VSPerfCmd [/U] [/options]
```

 다음 표에는 *VSPerfCmd.exe* 도구 옵션이 설명되어 있습니다.

|옵션|설명|
|------------|-----------------|
|**U**|리디렉션된 콘솔 출력이 유니코드로 기록됩니다. 이 옵션을 첫 번째 옵션으로 지정해야 합니다.|
|[Start](../profiling/start.md) **:** `mode`|지정된 모드로 프로파일링 서비스를 시작합니다.|
|[Output](../profiling/output.md) **:** `filename`|출력 파일 이름을 지정합니다. **Start**와 함께 사용하는 것만 가능합니다.|
|[CrossSession&#124;CS](../profiling/crosssession.md)|Windows 세션 전반에서 프로파일링을 사용합니다. **Start**, **Attach** 또는 **Launch**와 함께 사용하는 것만 가능합니다.|
|[User](../profiling/user-vsperfcmd.md) **:** [`domain\`]`username`|지정된 계정이 프로파일러 서비스에 액세스할 수 있도록 합니다. **Start**와 함께 사용하는 것만 가능합니다.|
|[WaitStart](../profiling/waitstart.md)[ **:** `n`]|데이터 수집 로거가 초기화될 때까지 대기합니다. `n`이 지정된 경우 **VSPerfCmd**에서 최대 `n`초를 대기합니다. `n`이 지정되지 않은 경우 **VSPerfCmd**에서 무기한으로 대기합니다. 이렇게 하면 보다 쉽게 **VSPerfCmd**를 일괄 처리 프로세스의 일부로 사용할 수 있습니다.|
|[Counter](../profiling/counter.md) **:** `cfg`|샘플 프로파일링 방법을 사용하는 경우 CPU 카운터와 샘플링 간격으로 사용할 이벤트 수를 지정합니다. 카운터 값은 하나만 샘플링할 수 있습니다.<br /><br /> 계측 프로파일링 방법을 사용하는 경우 각 계측 지점에서 수집할 CPU 카운터를 지정합니다. **Start:** `Trace`, **Attach** 또는 **Launch**와 함께 사용하는 것만 가능합니다.|
|[QueryCounters](../profiling/querycounters.md)|현재 컴퓨터의 유효한 CPU 카운터 목록이 표시됩니다.|
|[WinCounter](../profiling/wincounter.md) **:** *path*|프로필 표시 데이터와 함께 포함할 Windows 성능 카운터 이벤트를 지정합니다. **Start**와 함께 사용하는 것만 가능합니다.|
|[AutoMark](../profiling/automark.md) **:** *n*|Windows 성능 카운터 데이터 수집 이벤트 간 시간 간격(밀리초)을 지정합니다. **WinCounter**와 함께 사용합니다.|
|[Events](../profiling/events-vsperfcmd.md) **:** `option`|지정된 ETW(Windows용 이벤트 추적) 이벤트에 대한 수집을 제어합니다. ETW 데이터는 프로파일링 데이터(.*vsp*) 파일이 아닌 .*itl* 파일에 수집됩니다.|
|[Status](../profiling/status.md)|프로파일러 상태, 현재 프로파일링 중인 프로세스에 대한 정보 및 프로파일러 제어 권한이 있는 계정을 표시합니다.|
|[Shutdown](../profiling/shutdown.md)[ **:** `n`]|프로파일링 데이터 파일을 닫고 프로파일러를 해제합니다.|
|[GlobalOn](../profiling/globalon-and-globaloff.md)|**VSPerfCmdGlobalOff** 호출 후 데이터 수집을 다시 시작합니다.|
|[GlobalOff](../profiling/globalon-and-globaloff.md)|모든 데이터 수집을 중지하지만 프로파일링 세션을 종료하지 않습니다.|
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|**VSPerfCmdProcessOff** 호출로 프로파일링이 일시 중지된 후 지정된 프로세스에 대한 데이터 수집을 다시 시작합니다.|
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|지정된 프로세스에 대한 데이터 수집을 중지합니다.|
|[ThreadOn and ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|**VSPerfCmdThreadOff** 호출로 프로파일링이 일시 중지된 후 지정된 프로세스에 대한 프로파일링을 다시 시작합니다. 계측 방법으로 프로파일링하는 경우에만 **ThreadOn**을 사용합니다.|
|[ThreadOn and ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|지정된 스레드에 대한 프로파일링을 일시 중지합니다. 계측 방법으로 프로파일링하는 경우에만 **ThreadOff**를 사용합니다.|
|[Mark](../profiling/mark.md) **:** _MarkNum_[ **,** _MarkText_ **]**|선택적 텍스트와 함께 표시를 프로파일링 데이터 파일에 삽입합니다.|

## <a name="sample-method-options"></a>샘플 메서드 옵션
 다음 옵션은 샘플링 프로파일링 방법을 사용하는 경우에만 사용할 수 있습니다.

|옵션|설명|
|------------|-----------------|
|[Launch](../profiling/launch.md) **:** *실행 파일*|지정된 애플리케이션을 시작하고 프로파일링을 시작합니다.|
|[Args](../profiling/args.md) **:** *인수*|시작된 애플리케이션에 전달할 명령줄 인수를 지정합니다.|
|[콘솔](../profiling/console.md)|새 명령 프롬프트 창에서 지정된 명령을 시작합니다.|
|[Attach](../profiling/attach.md) **:** *PID*[ **,** _PID_]|지정된 프로세스의 프로파일링을 시작합니다. 프로세스는 프로세스 ID 또는 프로세스 이름으로 식별할 수 있습니다.|
|[Detach](../profiling/detach.md)[ **:** _PID_[,_PID_]]|지정된 프로세스의 프로파일링을 중지합니다. 프로세스는 프로세스 ID 또는 프로세스 이름으로 식별할 수 있습니다. 프로세스가 지정되지 않은 경우 모든 프로세스의 프로파일링이 중지됩니다.|
|[GC](../profiling/gc-vsperfcmd.md)[ **:** {**Allocation**`&#124;`**Lifetime**}]|.NET 메모리 할당 및 개체 수명 데이터를 수집합니다. **VSPerfCmdLaunch** 옵션과 함께 사용하는 것만 가능합니다.|

### <a name="sample-interval-options"></a>샘플 간격 옵션
 다음 옵션은 샘플링 간격의 형식과 기간을 지정합니다. 기본값은 **Timer**입니다. **Counter** 옵션을 사용하여 CPU 카운터를 간격으로 지정할 수도 있습니다. 이러한 옵션은 프로파일링 세션의 첫 번째 **Attach** 또는 **Launch**와 함께 사용하는 경우에만 지정할 수 있습니다.

|옵션|설명|
|------------|-----------------|
|[PF](../profiling/pf.md)[ **:** _n_]|n번째 페이지 폴트마다 샘플링합니다(기본값 = 10).|
|[Sys](../profiling/sys-vsperfcmd.md)[ **:** _n_]|n번째 시스템 호출마다 샘플링합니다(기본값 = 10).|
|[Timer](../profiling/timer.md)[ **:** _n_]|n번째 프로세서 주기마다 샘플링합니다(기본값 = 10000000).|

## <a name="service-component-and-kernel-mode-device-options"></a>서비스 구성 요소 및 커널 모드 디바이스 옵션
 다음 Admin 옵션은 프로파일링 서비스 구성 요소 또는 커널 모드 디바이스 드라이버를 지원합니다. Admin 옵션은 프로파일링 권한을 설정하고 프로파일링된 서비스 또는 디바이스 드라이버를 제어합니다.

 Admin 옵션은 관리 자격 증명으로 실행 중인 명령 프롬프트에서 실행되어야 합니다.

|옵션|설명|
|------------|-----------------|
|**Admin:Security**, \<**ALLOW&#124;DENY**>, *Right*[ *Right*], \<*User*&#124;*Group*>|지정된 사용자 또는 그룹이 프로파일링 서비스에 액세스하는 것을 허용하거나 거부합니다.<br /><br /> `Right`는 다음이 될 수 있습니다.<br /><br /> CrossSession - 사용자에게 서비스에 대해 상호 세션 프로파일링을 수행할 수 있는 액세스 권한을 부여합니다.<br /><br /> SampleProfiling - 사용자에게 드라이버에 대해 샘플링 프로파일링을 사용할 수 있는 액세스 권한을 부여합니다. 추적 프로파일링 중 커널 전환 정보에 액세스하는 데에도 사용됩니다.<br /><br /> FullAccess - 사용자에게 CrossSession 및 SampleProfiling 액세스 권한을 모두 부여합니다.|
|**Admin:Security, List**|프로파일링 서비스의 현재 상태 및 사용자 권한을 나열합니다.|
|**Admin:** \<*Service*&#124;*Driver*>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**>|프로파일링 서비스 구성 요소(서비스) 또는 커널 모드 디바이스 드라이버(드라이버)를 시작하거나, 중지하거나, 설치하거나, 제거합니다.|
|**Admin:** \<*Service*&#124;*Driver*>**AutoStart**\<**ON**&#124;**OFF**>|다시 시작 후 프로파일링 서비스(서비스) 또는 커널 모드 디바이스 드라이버(드라이버) 자동 시작을 사용하도록 설정하거나 사용하지 않도록 설정합니다.|

## <a name="vsperfcmd-driver"></a>VSPerfCmd /Driver
 **VSPerfCmd /Driver** 옵션은 이제 사용되지 않습니다. 해당 기능에는 **VsPerfCmd 관리자** 옵션을 사용합니다.

## <a name="see-also"></a>참조
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfReport](../profiling/vsperfreport.md)
