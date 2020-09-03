---
title: 함수 뷰 - 경합 데이터 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1aaab824f40c0cd6ba0a240a6f3035d7ebcccd00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141903"
---
# <a name="functions-view---contention-data"></a>함수 뷰 - 경합 데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

경함 데이터의 함수 보고서 뷰는 프로파일링 실행 중에 실행에서 차단된 프로파일링 실행 시 함수를 나열합니다.  
  
 다음 표에서는 동시성 방법을 사용하여 수집된 프로파일링 데이터 파일의 함수 뷰에 표시된 값을 설명합니다.  
  
|Column|설명|  
|------------|-----------------|  
|**차단된 전용 시간**|이 함수가 함수 본문에서 코드를 실행할 수 없도록 차단된 시간의 양입니다. 해당 함수가 호출한 함수의 차단된 시간은 포함되지 않습니다.|  
|**차단된 전용 시간 비율(%)**|프로파일링 실행의 모든 차단된 시간 중 이 함수의 차단된 전용 시간의 백분율입니다.|  
|**전용 경합**|이 함수에서 함수 본문의 코드 실행이 차단되는 횟수입니다. 해당 함수가 호출한 함수의 경합은 포함되지 않습니다.|  
|**전용 경합 비율(%)**|프로파일링 실행의 모든 경합 중 이 함수의 전용 경합의 백분율입니다.|  
|**함수 주소**|함수의 주소입니다.|  
|**함수 이름**|함수의 정규화된 이름입니다.|  
|**차단된 포괄 시간**|이 함수 또는 이 함수에서 호출한 함수에서 실행이 차단되는 시간입니다.|  
|**차단된 포괄 시간 비율(%)**|프로파일링 실행의 모든 차단된 시간 중 이 함수 또는 모듈의 차단된 포괄 시간의 백분율입니다.|  
|**포괄 경합**|이 함수 또는 이 함수에서 호출한 함수에서 실행이 차단되는 횟수입니다.|  
|**포괄 경합 비율(%)**|프로파일링 실행의 모든 경합 중 이 함수 또는 모듈의 포괄 경합의 백분율입니다.|  
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|  
|**모듈 이름**|함수가 포함된 모듈의 이름입니다.|  
|**모듈 경로**|함수가 포함된 모듈의 경로입니다.|  
|**프로세스 ID**|함수가 실행된 프로세스의 PID(프로세스 ID)입니다.|  
|**프로세스 이름**|프로세스의 이름입니다.|  
|**소스 파일**|이 함수의 정의가 포함된 소스 파일입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [방법: 보고서 뷰 열 사용자 지정](../profiling/how-to-customize-report-view-columns.md)   
 [함수 뷰](../profiling/functions-view.md)   
 [함수 뷰-계측](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [함수 뷰-샘플링](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [함수 뷰](../profiling/functions-view-instrumentation-data.md)   
 [함수 뷰](../profiling/functions-view-sampling-data.md)
