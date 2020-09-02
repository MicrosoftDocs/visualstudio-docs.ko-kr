---
title: 줄 뷰 - .NET 메모리 샘플링 데이터 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 251dc4279530c2d10ba8b404ee515824d0671037
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62579992"
---
# <a name="lines-view---net-memory-sampling-data"></a>줄 뷰 - .NET 메모리 샘플링 데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

샘플링 방법을 사용하는 .NET 메모리 할당 프로파일링 데이터에 대한 줄 뷰에는 프로파일링 실행 중 메모리를 할당한 문이 나열됩니다. 열에는 할당의 크기와 할당 수도 포함됩니다.  
  
 소스 파일에서는 하나의 문이 소스 파일의 여러 줄에 걸쳐 있거나 한 줄에 여러 문이 포함될 수 있습니다.  
  
 문은 다음에 의해 식별됩니다.  
  
- 함수 문이 포함된 소스 파일.  
  
- 문이 포함된 함수.  
  
- 문이 시작되는 소스 줄.  
  
- 문이 시작되는 소스 줄의 문자.  
  
- 문이 끝나는 소스 줄.  
  
- 문이 끝나는 소스 줄의 문자.  
  
  줄 이름 열은 식별자 데이터의 정렬 가능한 연결을 제공합니다.  
  
  정의에 따라 문은 다른 함수를 호출하지 않습니다. 따라서 전용 값만 나열됩니다.  
  
|열|Description|  
|------------|-----------------|  
|**프로세스 ID**|프로파일링 실행의 PID(프로세스 ID)입니다.|  
|**프로세스 이름**|프로세스의 이름입니다.|  
|**모듈 이름**|문이 포함된 모듈의 이름입니다.|  
|**모듈 경로**|문이 포함된 모듈의 경로입니다.|  
|**원본 파일**|문이 포함된 소스 파일입니다.|  
|**함수 이름**|문이 포함된 함수의 이름입니다.|  
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|  
|**함수 주소**|함수의 시작 주소입니다.|  
|**소스 줄 시작**|할당이 발생한 소스 파일의 시작 줄 번호입니다.|  
|**소스 줄 끝**|할당이 발생한 소스 파일의 끝 줄 번호입니다.|  
|**소스 문자 시작**|소스 파일 줄에서 할당이 발생한 시작 문자의 오프셋입니다.|  
|**소스 문자 끝**|소스 파일 줄에서 할당이 발생한 끝 문자의 오프셋입니다.|  
|**줄 이름**|프로파일러에서 생성된 줄 식별자로 다음 구문을 사용합니다. `Source File` **;[** `Line Number Start` **,** `Character Start` **]->;[** `Line Number Start,Character Start` **]**|  
|**제외 할당**|이 줄에서 생성된 개체의 총 수입니다.|  
|**제외 할당 비율(%)**|이 줄에서 할당되고 프로파일링 실행 시에 생성된 모든 개체의 백분율입니다.|  
|**제외 바이트**|이 줄에서 할당되고 프로파일링 실행 시에 할당된 모든 메모리 바이트의 백분율입니다.|  
|**제외 바이트(%)**|이 줄에서 할당되고 프로파일링 실행 시에 할당된 모든 메모리 바이트의 백분율입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [줄 뷰](../profiling/lines-view-sampling-data.md)
