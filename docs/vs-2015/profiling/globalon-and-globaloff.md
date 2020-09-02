---
title: GlobalOn 및 GlobalOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eae720bdd904c7b904c906022cea700512167617
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434230"
---
# <a name="globalon-and-globaloff"></a>GlobalOn 및 GlobalOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **GlobalOff** 및 **GlobalOn** 옵션은 명령줄 프로파일링 세션에서 모든 프로세스 및 스레드에 대한 프로파일링을 일시 중지 및 재개합니다.  
  
 VSPerfCmd.exe 명령줄에서 **GlobalOn** 및 **GlobalOff**를 유일한 옵션으로 지정하거나, **Start**, **Launch** 또는 **Attach** 옵션도 포함하는 명령줄에 포함할 수 있습니다.  
  
 **GlobalOn** 및 **GlobalOff**를 **ProcessOn**, **ProcessOff**, **ThreadOn** 및 **ThreadOff** 옵션과 함께 사용할 수도 있습니다.  
  
 **GlobalOn** 및 **GlobalOff** 옵션은 지정된 프로세스에 대한 데이터 수집을 제어하는 **ProcessOn** 및 **ProcessOff** 옵션, 지정된 스레드에 대한 데이터 수집을 제어하는 **ThreadOn** 및 **ThreadOff** 옵션과 상호 작용합니다.  
  
 **GlobalOff** 및 **GlobalOn** 옵션은 프로파일러 API 함수에 의해 조작되는 전역 Start/Stop 카운트에도 영향을 줍니다.  
  
- **GlobalOff**는 전역 Start/Stop 카운트를 즉시 0으로 설정하므로 프로파일링이 일시 중지됩니다.  
  
- **GlobalOn**은 전역 Start/Stop 카운트를 즉시 1로 설정하므로 프로파일링이 재개됩니다.  
  
  자세한 내용은 [프로파일링 도구 api](../profiling/profiling-tools-apis.md)를 참조 하세요.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]  
```  
  
#### <a name="parameters"></a>매개 변수  
 없음  
  
## <a name="valid-options"></a>유효한 옵션  
 **GlobalOn** 및 **GlobalOff**를 다음 옵션도 포함하는 명령줄에서 지정할 수 있습니다.  
  
 **시작:**`Method`  
 명령줄 프로파일러 세션을 초기화하고 지정된 프로파일링 방법을 설정합니다.  
  
 **시작:**`AppName`  
 지정된 애플리케이션을 시작하고 샘플링 방법으로 프로파일링을 시작합니다.  
  
 **연결:**`PID`  
 지정된 프로세스의 프로파일링을 시작합니다.  
  
 {**ProcessOff**&#124;**processon**} **:**`PID`  
 지정된 프로세스에 대한 프로파일링을 중지하거나 시작합니다.  
  
 {**Threadoff**&#124;**threadoff**} **:**`TID`  
 지정된 프로세스에 대한 프로파일링을 중지 또는 시작합니다(계측 방법만 해당).  
  
## <a name="example"></a>예  
 이 예제에서는 애플리케이션 시작 및 종료에 대한 프로파일링 데이터가 수집되지 않도록 하기 위해 **GlobalOff** 및 **GlobalOn** 옵션이 사용됩니다.  
  
```  
; Initialize the profiler with profiling stopped.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff  
; Start an instrumented application and wait for it to warm up.  
; Start profiling.  
VSPerfCmd.exe /GlobalOn  
; Exercise the application functionality that you want to profile.  
; Stop profiling.  
VSPerfCmd.exe /GlobalOff  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
