---
title: Counter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5da78c33af599accf5ff3a2e09a9afb52982573a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149283"
---
# <a name="counter"></a>카운터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Counter** 옵션은 프로세서(하드웨어) 성능 카운터에서 데이터를 수집합니다.  
  
- 샘플링 프로파일링 방법을 사용하는 경우 **Counter**는 온칩 성능 카운터와 샘플링 간격으로 사용할 카운터 이벤트의 수를 지정합니다. 샘플링을 사용하는 경우 카운터를 하나만 지정할 수 있습니다.  
  
- 계측 프로파일링 방법을 사용하는 경우 이전 및 현재 컬렉션 이벤트 중간에 발생한 카운터 이벤트의 수가 프로파일러 보고서에 별도의 필드로 나열됩니다. 계측을 사용하는 경우 여러 **Counter** 옵션을 지정할 수 있습니다.  
  
  각 프로세서 유형에는 고유한 하드웨어 성능 카운터 집합이 있습니다. 프로파일러는 거의 모든 프로세서에서 공통되는 일반 성능 카운터 집합을 정의합니다. 컴퓨터의 일반 및 프로세서별 카운터를 나열하려면 VSPerfCmd **QueryCounters** 명령을 사용합니다.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>매개 변수  
 `Name`  
 카운터의 이름입니다. VSPerfCmd.exe **/QueryCounters** 옵션을 사용하여 컴퓨터에서 사용할 수 있는 카운터의 이름을 나열합니다.  
  
 `Reload`  
 샘플링 간격의 카운터 이벤트 수입니다. 계측 방법에는 사용하지 마세요.  
  
 `FriendlyName`  
 (선택 사항) 프로파일러 보고서 및 뷰의 열 머리글에서 `Name` 대신 사용할 문자열입니다.  
  
## <a name="required-options"></a>필수 옵션  
 Counter 옵션은 반드시 다음 옵션 중 하나와 함께 사용해야 합니다.  
  
 **시작:**`Trace`  
 프로파일러를 초기화하여 계측 방법을 사용합니다.  
  
 **시작:**`AppName`  
 지정한 애플리케이션 및 프로파일러를 시작합니다. 샘플링 방법을 사용하려면 프로파일러를 초기화해야 합니다.  
  
 **연결:**`PID`  
 프로파일러를 시작하고 프로세스 ID로 지정한 프로세스에 연결합니다. 샘플링 방법을 사용하려면 프로파일러를 초기화해야 합니다.  
  
## <a name="example"></a>예  
 샘플링 방법 예제는 일반 프로파일러 카운터 NonHaltedCycles가 1000번 발생할 때마다 애플리케이션을 샘플링하는 방법을 보여 줍니다.  
  
 계측 방법 예제는 프로파일러를 초기화하여 L2InstructionFetches 카운터 이벤트를 수집하는 방법을 보여 줍니다. L2InstructionFetches 카운터 이름은 프로세서마다 고유합니다.  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
