---
title: 함수 뷰 - .NET 메모리 샘플링 데이터 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e77c6c2b3bf079e8aae88c9779c3b487ff97fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141859"
---
# <a name="functions-view---net-memory-sampling-data"></a>함수 뷰 - .NET 메모리 샘플링 데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

샘플링 방법을 사용하여 수집된 .NET 메모리 할당 프로파일링 데이터의 함수 뷰는 프로파일링 실행 중 메모리를 할당한 함수를 나열하고 할당의 크기와 수를 보고합니다.  
  
|열|Description|  
|------------|-----------------|  
|**프로세스 ID**|프로파일링 실행의 PID(프로세스 ID)입니다.|  
|**프로세스 이름**|프로세스의 이름입니다.|  
|**모듈 이름**|함수가 포함된 모듈의 이름입니다.|  
|**모듈 경로**|함수가 포함된 모듈의 경로입니다.|  
|**원본 파일**|이 함수의 정의가 포함된 소스 파일입니다.|  
|**함수 이름**|함수의 정규화된 이름입니다.|  
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|  
|**함수 주소**|함수의 주소입니다.|  
|**포함 할당**|이 함수 및 해당 자식 함수에 할당된 개체의 총 수입니다.|  
|**포함 할당 비율(%)**|이 함수의 포함 할당으로, 프로파일링 실행 시 할당된 모든 개체의 비율입니다.|  
|**제외 할당**|함수가 호출 스택의 맨 위에서 직접 실행 중일 때 생성된 개체의 수입니다. 이 수는 자식 함수에서 만든 개체를 포함하지 않습니다.|  
|**제외 할당 비율(%)**|이 함수의 제외 할당으로, 프로파일링 실행 시 할당된 모든 개체의 비율입니다.|  
|**포함 바이트**|이 함수 및 해당 자식 함수에 의해 할당된 메모리의 바이트 수입니다.|  
|**포함 바이트 비율(%)**|이 함수의 포함 바이트로, 프로파일링 실행 시 할당된 모든 메모리 바이트의 비율입니다.|  
|**제외 바이트**|해당 자식 함수가 아닌 이 함수에 의해 할당된 메모리의 바이트 수입니다.|  
|**제외 바이트(%)**|이 함수의 전용 바이트로, 프로파일링 실행 시 할당된 모든 메모리 바이트의 비율입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [함수 뷰-계측](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [함수 뷰](../profiling/functions-view-sampling-data.md)   
 [함수 뷰](../profiling/functions-view-instrumentation-data.md)
