---
title: 이벤트(VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d24fc7a01a8eebe356f37704c1a821332f5dca1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850757"
---
# <a name="events-vsperfcmd"></a>이벤트(VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Events** 옵션은 ETW(Windows용 이벤트 추적) 로깅을 제어합니다. ETW 데이터는 프로파일러 데이터 파일에서 분리된 .etl 파일에 저장됩니다. [VSPerfReport](../profiling/vsperfreport.md) /summary:etw 명령을 사용하여 보고서에서 데이터를 볼 수 있습니다.  
  
 VSPerfCmd **Shutdown** 명령이 프로파일링을 중지하기 위해 호출되기 전에 언제든지 **Events** 옵션을 호출할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>매개 변수  
 **On**&#124;**Off**  
 이벤트 데이터 수집을 시작하거나 중지합니다.  
  
 `Guid`  
 공급자의 컨트롤의 GUID입니다.  
  
 `ProviderName`  
 WMI(Windows Management Instrumentation)로 등록된 공급자의 이름입니다.  
  
 `Flags`  
 이벤트 공급자에 의해 정의된 "0x" 접두사 16진수 플래그 값입니다.  
  
 `Level`  
 수집되는 데이터 양을 지정합니다. `Level`은 이벤트 공급자에 의해 정의됩니다.  
  
 **Events** 옵션은 다음 커널 키워드를 공급자 이름으로 인식합니다.  
  
 **처리**  
 이벤트 처리  
  
 **스레드**  
 스레드 이벤트  
  
 **이미지**  
 이벤트 로드 및 언로드 이벤트  
  
 **디스크**  
 디스크 I/O 이벤트  
  
 **파일**  
 파일 I/O 이벤트  
  
 **Hardfault**  
 하드 페이지 폴트  
  
 **Pagefault**  
 소프트 페이지 폴트  
  
 **네트워크**  
 네트워크 이벤트  
  
 **레지스트리**  
 레지스트리 액세스 이벤트  
  
 커널 공급자만 사용할 수 있습니다. 모니터가 종료될 때까지 비활성화되거나 해당 플래그를 수정할 수 없습니다.  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> CLR ETW 이벤트를 활성화하면 추가 시작 데이터도 추적 뷰 보고서에 수집됩니다. 시작 이벤트를 보고서 표시에서 제외하려면 다음 명령을 사용합니다.  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
> 시작 이벤트를 제외하지 않는 경우 이러한 이벤트는 MOF(Managed Object Format) 파일에 나열되지 않으므로 보고서에 GUID로 표시됩니다. 자세한 내용은 Microsoft 웹 사이트에서 [MOF (Sample MOF(Managed Object Format)) 파일](https://msdn.microsoft.com/library/default.aspx)페이지를 참조 하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
