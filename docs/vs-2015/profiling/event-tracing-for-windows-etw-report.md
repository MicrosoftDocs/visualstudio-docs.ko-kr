---
title: ETW(Windows용 이벤트 추적) 보고서 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bc0e139644a0b3df29109c1543140e57c5378f31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841586"
---
# <a name="event-tracing-for-windows-etw-report"></a>ETW(Windows용 이벤트 추적) 보고서
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ETW(Windows용 이벤트 추적) 보고서에는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로파일링 도구의 성능 세션에서 기록된 ETW 이벤트가 나열됩니다. ETW 데이터는 이진(.etl) 파일에 수집됩니다.  
  
> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인터페이스에는 ETW 보고서를 표시할 수 없습니다.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인터페이스에서 프로파일링 도구를 사용하여 ETW 데이터를 수집하는 방법에 대한 자세한 내용은 [방법: ETW(Windows용 이벤트 추적) 데이터 수집](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)을 참조하세요.  
  
- [VSPerfCmd](../profiling/vsperfcmd.md) 명령줄 도구를 사용하여 ETW 데이터를 수집하는 방법에 대한 자세한 내용은 [이벤트](../profiling/events-vsperfcmd.md)를 참조하세요.  
  
- **VSReport/Summary:ETW** 명령을 사용하여 ETW 보고서를 생성합니다. 자세한 내용은 [VSPerfReport](../profiling/vsperfreport.md)를 참조하세요.  
  
|열|Description|  
|------------|-----------------|  
|**Timestamp**|이벤트가 발생한 시기를 식별합니다.|  
|**프로세스 ID**|이벤트를 생성한 프로세스를 식별합니다.|  
|**스레드 ID**|이벤트를 생성한 스레드를 식별합니다.|  
|**설명**|이벤트 공급자를 식별합니다.|  
|**형식**|이벤트 유형을 식별합니다.|  
|**속성**|이벤트의 속성입니다. 각 이벤트는 쉼표로 구분되며, 대괄호로 묶인 이름 값 쌍입니다.|
