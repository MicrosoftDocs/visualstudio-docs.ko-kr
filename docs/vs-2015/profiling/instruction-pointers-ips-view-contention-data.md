---
title: IP(명령 포인터) 뷰 - 경합 데이터 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b27b185e659fc3a1f0adca4379896543a1eb87ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187846"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>IP(명령 포인터) 뷰 - 경합 데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

경합 데이터의 IP 뷰는 프로파일링 실행 시 실행되지 않도록 차단된 어셈블리 명령에 대한 데이터를 나열합니다.  
  
 다음 표에서는 명령 포인터 뷰에 있는 열의 값에 대해 설명합니다.  
  
|Column|설명|  
|------------|-----------------|  
|**차단된 전용 시간**|이 함수에서 차단된 시간입니다.|  
|**차단된 전용 시간 비율(%)**|명령이 실행되는 동안 차단된 시간의 백분율입니다.|  
|**전용 경합**|명령이 실행되는 동안 발생한 경합 수입니다.|  
|**전용 경합 비율(%)**|프로파일링 실행 시 명령이 실행되는 동안 발생한 모든 경합의 백분율입니다.|  
|**함수 주소**|로드된 이진에서 함수의 시작 메모리 주소입니다.|  
|**함수 이름**|명령이 포함된 함수의 이름입니다.|  
|**명령 주소**|로드된 이진에서 명령의 메모리 주소입니다.|  
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|  
|**모듈 이름**|명령이 포함된 모듈의 이름입니다.|  
|**모듈 경로**|명령이 포함된 모듈의 경로입니다.|  
|**프로세스 ID**|프로파일링된 프로세스의 PID(프로세스 ID)입니다.|  
|**프로세스 이름**|프로세스의 이름입니다.|  
|**소스 문자 시작**|이 명령이 시작되는 소스 파일 줄에 있는 문자의 오프셋입니다.|  
|**소스 문자 끝**|이 명령이 끝나는 소스 파일 줄에 있는 문자의 오프셋입니다.|  
|**소스 파일**|명령이 포함된 소스 파일입니다.|  
|**소스 줄 시작**|이 명령이 시작되는 소스 파일의 줄 번호입니다.|  
|**소스 줄 끝**|이 명령이 끝나는 소스 파일의 줄 번호입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [방법: 보고서 뷰 열 사용자 지정](../profiling/how-to-customize-report-view-columns.md)   
 [Ip (명령 포인터) 뷰](../profiling/instruction-pointers-ips-view.md)   
 [Ip (명령 포인터) 뷰-샘플링](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [IP(명령 포인터) 뷰](../profiling/instruction-pointers-ips-view-sampling-data.md)
