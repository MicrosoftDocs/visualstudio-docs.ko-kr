---
title: ThreadOn 및 ThreadOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 906629eb24f6be097f3e24dfca3e6a231f42357f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778156"
---
# <a name="threadon-and-threadoff"></a>ThreadOn 및 ThreadOff
*VSPerfCmd.exe* **ThreadOff** 및 **ThreadOn** 하위 명령은 계측 방법을 사용하는 명령줄 프로파일링 세션에서만 사용할 수 있습니다. **ThreadOff** 및 **ThreadOn**은 지정된 스레드에 대한 프로파일링을 일시 중지하고 다시 시작합니다. **ThreadOff**는 스레드 프로파일링을 중지하고 **ThreadOn**은 스레드 프로파일링을 시작합니다.

 대부분의 경우에서 **ThreadOn** 또는 **ThreadOff**를 *VSPerfCmd.exe* 명령줄의 유일한 옵션으로 지정하지만 **GlobalOn**, **GlobalOff**, **ProcessOn** 및 **ProcessOff** 하위 명령과 함께 결합될 수도 있습니다.

 **ThreadOn** 및 **ThreadOff** 하위 명령은 명령줄 프로파일링 세션에서 모든 프로세스에 대한 데이터 컬렉션을 제어하는 **GlobalOn** 및 **GlobalOff** 하위 명령 및 지정된 프로세스에 대한 데이터 수집을 제어하는 **ProcessOn** 및 **ProcessOff** 하위 명령과 상호 작용합니다.

 **ThreadOff** 및 **ThreadOn** 하위 명령은 프로파일러 API 함수에 의해 조작되는 스레드 시작/중지에도 영향을 줍니다.

- **ThreadOff**는 스레드 Start/Stop 카운트를 즉시 0으로 설정하므로 프로파일링이 일시 중지됩니다.

- **ThreadOn**은 스레드 Start/Stop 카운트를 즉시 1로 설정하므로 프로파일링을 다시 시작합니다.

  자세한 내용은 [프로파일링 도구 API](../profiling/profiling-tools-apis.md)를 참조하세요.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>매개 변수
 `TID` 시작하거나 중지할 스레드의 정수 식별자입니다.

## <a name="valid-options"></a>유효한 옵션
 **ThreadOn** 및 **ThreadOff**를 다음 하위 명령도 포함하는 명령줄에서 지정할 수 있습니다.

 **시작:** `Method` 명령줄 프로파일링 세션을 초기화하고 지정된 프로파일링 방법을 설정합니다.

 **GlobalOff**&#124;**GlobalOn** 명령줄 프로파일링 세션에서 모든 프로세스에 대한 프로파일링을 중지하거나 시작합니다.

 {**ProcessOff**&#124;**ProcessOn**}**:**`TID` 지정된 프로세스에 대한 프로파일링을 중지하거나 시작합니다.

## <a name="example"></a>예제
 이 예제에서 **ThreadOff** 하위 명령은 애플리케이션 시작 데이터만 수집될 수 있도록 프로파일링 데이터 수집을 중지하는 데 사용됩니다.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the thread after startup.
VSPerfCmd.exe /ThreadOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
