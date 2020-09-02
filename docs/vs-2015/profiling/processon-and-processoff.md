---
title: ProcessOn 및 ProcessOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 77e21a280700520b6861dd42e01a4aefa4faa704
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180200"
---
# <a name="processon-and-processoff"></a>ProcessOn 및 ProcessOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **ProcessOff** 및 **ProcessOn** 하위 명령은 명령줄 프로파일링 세션에서 지정된 프로세스에 대한 프로파일링을 일시 중지하고 다시 시작합니다. **ProcessOff**는 프로세스 프로파일링을 중지하고 **ProcessOn**은 프로세스를 프로파일링을 시작합니다.  
  
 대부분의 경우에서 **ProcessOn** 또는 **ProcessOff**를 VSPerfCmd.exe 명령줄의 유일한 옵션으로 지정하지만 **GlobalOn**, **GlobalOff**, **ThreadOn** 및 **ThreadOff** 하위 명령과 함께 결합될 수도 있습니다.  
  
 **ProcessOn** 및 **ProcessOff** 하위 명령은 명령줄 프로파일링 세션에서 모든 프로세스에 대한 데이터 컬렉션을 제어하는 **GlobalOn** 및 **GlobalOff** 하위 명령 및 지정된 스레드에 대한 데이터 수집을 제어하는 **ThreadOn** 및 **ThreadOff**와 상호 작용합니다.  
  
 **ProcessOff** 및 **ProcessOn** 하위 명령은 프로파일러 API 함수에 의해 조작되는 프로세스 시작/중지에도 영향을 줍니다.  
  
- **ProcessOff**는 프로세스 시작/중지 카운트를 즉시 0으로 설정하므로 프로파일링이 일시 중지됩니다.  
  
- **ProcessOn**은 프로세스 시작/중지 카운트를 즉시 1로 설정하므로 프로파일링이 다시 시작됩니다.  
  
  자세한 내용은 [프로파일링 도구 API](../profiling/profiling-tools-apis.md)를 참조하세요.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### <a name="parameters"></a>매개 변수  
 `PID`  
 시작하거나 중지할 프로세스의 정수 식별자입니다. 프로세스 ID는 Windows 작업 관리자의 프로세스 탭에 나열됩니다.  
  
## <a name="required-subcommands"></a>필수 하위 명령  
 없음  
  
## <a name="valid-subcommands"></a>유효한 하위 명령  
 **ProcessOn** 및 **ProcessOff**를 다음 하위 명령도 포함하는 명령줄에서 지정할 수 있습니다.  
  
 **시작:**`Method`  
 명령줄 프로파일링 세션을 초기화하고 지정된 프로파일링 방법을 설정합니다.  
  
 **시작:**`AppName`  
 지정된 애플리케이션을 시작하고 샘플링 방법으로 프로파일링을 시작합니다.  
  
 **연결:**`PID`  
 지정된 프로세스의 프로파일링을 시작합니다.  
  
 **GlobalOff**&#124;**GlobalOn**  
 명령줄 프로파일링 세션에서 모든 프로세스에 대한 프로파일링을 중지하거나 시작합니다.  
  
 {**Threadoff**&#124;**threadoff**} **:**`TID`  
 지정된 스레드에 대한 프로파일링을 중지 또는 시작합니다(계측 방법만 해당).  
  
## <a name="example"></a>예  
 이 예제에서 **ProcessOff** 하위 명령은 애플리케이션 시작에 대한 프로파일링 데이터를 수집하는 데 사용됩니다.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
