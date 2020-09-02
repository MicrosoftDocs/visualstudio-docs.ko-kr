---
title: 종료 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbbbd27cfe7d720349592050419f5c73d1843c70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160220"
---
# <a name="shutdown"></a>Shutdown
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Shutdown** 옵션은 현재 프로파일링된 프로세스가 종료 또는 분리되기를 기다린 다음 프로파일러를 해제하고 프로파일링 데이터 파일을 닫습니다. **Shutdown** 옵션은 프로파일링 실행의 마지막 명령이어야 합니다.  
  
 시간 제한 매개 변수를 지정하지 않는 경우 **Shutdown** 옵션은 무기한으로 대기합니다. 시간 제한 매개 변수를 지정하는 경우 옵션은 프로파일러를 해제하거나 데이터 파일을 닫지 않고 지정된 시간(초) 후 반환합니다.  
  
 **Shutdown** 옵션은 명령줄에 지정된 유일한 옵션이어야 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>매개 변수  
`Timeout`  
- (선택 사항) 지정하는 경우 옵션은 프로파일러를 해제하거나 프로파일링 데이터 파일을 닫지 않고 지정된 시간(초) 후 반환합니다.  
  
## <a name="see-also"></a>관련 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
