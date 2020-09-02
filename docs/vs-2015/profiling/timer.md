---
title: Timer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e5f6c6db903b3ecced2ac3ebc4aaa0a3e60910c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145494"
---
# <a name="timer"></a>Timer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Timer** 옵션은 프로세서 클록 주기로 샘플링되는 프로파일링 이벤트를 설정하고 경우에 따라 샘플링 간격의 주기 수를 기본값 10,000,000에서 변경합니다. 1GH(1기가헤르츠) 프로세서에서 10,000,000 클록 주기는 초당 샘플 100개입니다. 지정할 수 있는 최소 주기 수는 50,000입니다.  
  
 **Timer**는 샘플링 프로파일링 메서드를 사용하는 경우에만 사용할 수 있고 **Launch** 또는 **Attach** 옵션도 포함하는 명령줄에서만 사용할 수 있습니다.  
  
 기본적으로 프로파일러 샘플링 이벤트는 프로세스 클록 주기로 설정되어 있고 샘플링 간격은 10,000,000으로 설정되어 있습니다. **Timer**, **PF**, **Sys** 및 **Counter** 옵션을 사용하여 샘플링 이벤트와 샘플링 간격을 설정할 수 있습니다. **GC** 옵션은 각 할당 및 가비지 컬렉션 이벤트에서 .NET 메모리 데이터를 수집합니다. 명령줄에서는 이러한 옵션 중 하나만 지정할 수 있습니다.  
  
 샘플링 이벤트와 샘플링 간격은 **Launch** 또는 **Attach** 옵션이 포함된 첫 번째 명령줄에서만 설정할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### <a name="parameters"></a>매개 변수  
 `Cycles`  
 샘플링 간격에서 프로세서 클록 주기 수를 지정하는 정수 값입니다. `Cycles`를 지정하지 않으면 간격은 10,000,000으로 설정됩니다. 쉼표 없이 값을 지정합니다.  
  
## <a name="required-options"></a>필수 옵션  
 **Timer**는 다음 옵션 중 하나가 포함된 명령줄에서만 지정할 수 있습니다.  
  
 **시작:**`AppName`  
 프로파일러 및 `AppName`에서 지정한 애플리케이션을 시작합니다.  
  
 **연결:**`PID`  
 프로세스 ID(`PID`)로 지정한 프로세스에 프로파일러를 연결합니다.  
  
## <a name="invalid-options"></a>잘못된 옵션  
 다음 옵션은 **Timer**와 동일한 명령줄에서 지정할 수 없습니다.  
  
 **PF**[**:** `Events` ]  
 샘플링 이벤트를 페이지 폴트로 설정하고 경우에 따라 샘플링 간격을 `Events`로 설정합니다. 기본 PF 간격은 10입니다.  
  
 **Sys**[**:** `Events` ]  
 샘플링 이벤트를 운영 체제 호출로 설정하고 필요한 경우 샘플링 간격을 `Events`로 설정합니다. 기본 시스템 간격은 10입니다.  
  
 **Counter**[**:** `Name,Reload,FriendlyName` ]  
 `Name`으로 지정한 CPU 성능 카운터로 샘플링 이벤트를 설정하고 샘플링 이벤트를 `Reload`로 설정합니다.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 .NET 메모리 데이터를 수집합니다. 기본적으로 (**할당**) 모든 메모리 할당 이벤트에서 데이터가 수집 됩니다. **Lifetime** 매개 변수가 지정 되 면 데이터는 각 가비지 수집 이벤트 에서도 수집 됩니다.  
  
## <a name="example"></a>예  
 다음 예제는 프로파일러 샘플링 간격을 1,000,000 프로세서 주기로 설정하는 방법을 보여줍니다.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
