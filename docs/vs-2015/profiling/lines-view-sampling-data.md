---
title: 줄 뷰 - 샘플링 데이터 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2e5511e9e2e1c863db8f696a70195573d75429f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843251"
---
# <a name="lines-view---sampling-data"></a>줄 뷰 - 샘플링 데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

샘플링 데이터의 줄 뷰에는 프로파일링 실행 시 샘플이 수집될 때 실행되고 있던 문에 대한 성능 데이터가 표시됩니다.  
  
> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. Windows 스토어 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.  
  
 소스 파일에서는 하나의 문이 소스 파일의 여러 줄에 걸쳐 있거나 한 줄에 여러 문이 포함될 수 있습니다. 문은 다음에 의해 식별됩니다.  
  
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
|**모듈 이름**|함수 줄이 포함된 모듈의 이름입니다.|  
|**모듈 경로**|함수 줄이 포함된 모듈의 경로입니다.|  
|**원본 파일**|함수 줄이 포함된 소스 파일입니다.|  
|**함수 이름**|함수의 이름입니다.|  
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|  
|**함수 주소**|함수의 시작 주소입니다.|  
|**소스 줄 시작**|소스 파일에서 이 샘플이 수집된 시작 줄 번호입니다.|  
|**소스 줄 끝**|소스 파일에서 이 샘플이 수집된 끝 줄 번호입니다.|  
|**소스 문자 시작**|소스 파일 줄에서 이 샘플이 수집된 시작 문자의 오프셋입니다.|  
|**소스 문자 끝**|소스 파일 줄에서 이 샘플이 수집된 끝 문자의 오프셋입니다.|  
|**줄 이름**|프로파일러에서 생성된 줄 식별자로 다음 구문을 사용합니다. `Source File` **;[** `Line Number Start` **,** `Character Start` **]->;[** `Line Number End` **,** `Character End` **]**|  
|**전용 샘플**|함수 줄이 실행될 때 수집된 샘플의 총 수입니다.|  
|**전용 샘플 비율(%)**|프로파일링 실행 시 함수 줄이 실행될 때 수집된 모든 샘플의 백분율입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [줄 뷰 - 샘플링](../profiling/lines-view-dotnet-memory-sampling-data.md)
