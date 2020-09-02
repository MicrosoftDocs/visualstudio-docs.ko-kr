---
title: 프로세스 뷰 - 경합 데이터 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e43541ddb75b067faa23437d315ce5f239256b1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180227"
---
# <a name="process-view---contention-data"></a>프로세스 뷰 - 경합 데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로세스 뷰에는 프로파일링 실행 중에 실행된 프로세스와 스레드에 대한 경합 데이터가 표시됩니다.  
  
 기호를 사용할 수 있으면 프로세스는 이름순으로 나열됩니다. 기호를 사용할 수 없으면 프로세스는 메모리 주소(16진수 형식)순으로 나열됩니다. 스레드는 스레드를 생성한 프로세스의 자식으로 나열됩니다.  
  
 다음 표에서는 프로세스 뷰 테이블에 있는 열의 값에 대해 설명합니다.  
  
|Column|설명|  
|------------|-----------------|  
|**시작 시간**|프로파일링 시작에서 프로세스 또는 스레드 시작까지의 시간(밀리초) 또는 프로세서 주기 수입니다.|  
|**차단된 시간**|프로세스 또는 스레드의 함수 실행이 차단된 총 시간입니다.|  
|**차단된 시간 비율(%)**|프로세서 또는 스레드의 수명 중 프로세스 또는 스레드의 함수 실행이 차단된 시간의 백분율입니다.|  
|**경합**|프로세스 또는 스레드의 함수 실행이 차단된 횟수입니다.|  
|**경합 비율(%)**|프로파일링 실행의 모든 경합 중 프로세스 또는 스레드 경합의 백분율입니다.|  
|**종료 시간**|프로파일링 시작에서 프로세스 또는 스레드 끝까지의 시간(밀리초) 또는 프로세서 주기 수입니다.|  
|**ID**|시스템에서 생성한 프로세스 또는 스레드의 식별자입니다.|  
|**수명**|프로세스 또는 스레드 시작에서 프로세스 또는 스레드 끝이나 프로파일링 끝가지의 시간(밀리초) 또는 프로세서 주기 수입니다.|  
|**Type**|프로세스 또는 스레드의 행 형식입니다.<br /><br /> **VSReport** 명령줄 보고서에서만 사용됩니다. 자세한 내용은 [VSPerfReport](../profiling/vsperfreport.md)를 참조하세요.|  
|**이름**|프로세스 또는 스레드의 이름입니다.|  
|**고유 ID**|프로파일러에서 생성한 프로세스 또는 스레드의 고유한 식별자입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [방법: 보고서 뷰 열 사용자 지정](../profiling/how-to-customize-report-view-columns.md)   
 [프로세스 뷰](../profiling/process-view.md)
