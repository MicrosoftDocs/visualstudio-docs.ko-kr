---
title: Sys (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 981b37fe1ebaad5e45f0308143ab0384ef1d559b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145600"
---
# <a name="sys-vsperfcmd"></a>Sys(VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Sys** 옵션은 시스템 호출 이벤트(프로파일링된 애플리케이션에서 운영 체제로 함수 호출)로 샘플링되는 프로파일링 이벤트를 설정하고 필요에 따라 기본값 10의 샘플링 간격에서 시스템 호출 수를 변경합니다.  
  
 **Sys**는 **Launch** 또는 **Attach** 옵션도 포함하는 명령줄에서만 사용할 수 있습니다.  
  
 기본적으로 프로파일러 샘플링 이벤트는 프로세스 클록 주기로 설정되어 있고 샘플링 간격은 10,000,000으로 설정되어 있습니다. **Timer**, **PF**, **Sys** 및 **Counter** 옵션을 사용하여 샘플링 이벤트와 샘플링 간격을 설정할 수 있습니다. **GC** 옵션은 각 할당 및 가비지 컬렉션 이벤트에서 .NET 메모리 데이터를 수집합니다. 명령줄에서는 이러한 옵션 중 하나만 지정할 수 있습니다.  
  
 샘플링 이벤트와 샘플링 간격은 **Launch** 또는 **Attach** 옵션이 포함된 첫 번째 명령줄에서만 설정할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### <a name="parameters"></a>매개 변수  
 `Events`  
 샘플링 간격에서 시스템 호출 이벤트 수를 지정하는 정수 값입니다. `Events`를 지정하지 않으면 간격은 10으로 설정됩니다.  
  
## <a name="required-options"></a>필수 옵션  
 **Sys**에 다음 옵션 중 하나가 필요합니다.  
  
 **시작:**`AppName`  
 프로파일러 및 `AppName`에서 지정한 애플리케이션을 시작합니다.  
  
 **연결:**`PID`  
 `PID`으로 지정한 프로세스에 프로파일러를 연결합니다.  
  
## <a name="invalid-options"></a>잘못된 옵션  
 다음 옵션은 **Sys**와 동일한 명령줄에서 지정할 수 없습니다.  
  
 **PF**[**:** `Events` ]  
 샘플링 이벤트를 페이지 폴트로 설정하고 경우에 따라 샘플링 간격을 `Events`로 설정합니다. 기본 PF 간격은 10입니다.  
  
 **타이머**[**:** `Cycles` ]  
 샘플링 이벤트를 프로세서 클록 주기로 설정하고 경우에 따라 샘플링 간격을 `Cycles`로 설정합니다. 기본 타이머 간격은 10,000,000입니다.  
  
 **카운터:** `Name` [`,Reload`[`,FriendlyName`]]  
 `Name`으로 지정한 CPU 성능 카운터로 샘플링 이벤트를 설정하고 샘플링 이벤트를 `Reload`로 설정합니다.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 .NET 메모리 데이터를 수집합니다. 기본적으로 (**할당**) 모든 메모리 할당 이벤트에서 데이터가 수집 됩니다. **Lifetime** 매개 변수가 지정 되 면 데이터는 각 가비지 수집 이벤트 에서도 수집 됩니다.  
  
## <a name="example"></a>예  
 이 예제는 프로파일러 샘플링 이벤트를 시스템 호출로 설정하는 방법 및 샘플링 간격을 샘플당 20 호출로 설정하는 방법을 보여 줍니다.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
