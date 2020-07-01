---
title: 성능 규칙 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48659a0b5981d545a706abfcaa7c3db24052cd20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548410"
---
# <a name="performance-rules-reference"></a>성능 규칙 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로파일링 도구의 성능 규칙은 애플리케이션 성능에 대한 추가 경고 및 정보를 제공합니다. 성능 규칙은 Windows 및 프로세서 성능 카운터와 같은 출처에서 수집한 프로파일링 실행의 데이터를 분석합니다. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 통합 개발 환경의 오류 출력 창에 규칙 메시지가 표시됩니다. 메시지는 다음 규칙 수준 중 하나로 나열됩니다.  
  
|범주|설명|  
|-|-|  
|**오류**|대부분의 성능 문제는 명확한 오류가 아니므로 오류 메시지를 생성하는 규칙은 거의 없습니다. 오류 메시지는 프로파일링 데이터 수집 실패를 나타낼 수 있습니다.|  
|**경고**|경고는 성능 문제의 원인이 될 가능성이 있거나 최적화하는 경우 도움이 될 수 있는 애플리케이션 영역을 나타냅니다.|  
|**정보**|정보 메시지는 규칙 조건 분석에서 오류 메시지 생성을 위한 임계값에 도달하지 않았거나, 메시지의 정보가 유용하기는 하지만 성능 문제를 반영하지는 않음을 나타냅니다.|  
  
## <a name="in-this-section"></a>섹션 내용  
 [ID 별 성능 규칙](../profiling/performance-rules-by-id.md)  
  
 프로파일링 도구 성능 규칙은 다음의 네 가지 범주로 구성됩니다.  
  
|범주|설명|  
|-|-|  
|[.NET Framework 사용 성능 규칙](../profiling/dotnet-framework-usage-performance-rules.md)|.NET Framework를 효율적으로 사용하는 데 도움이 되는 규칙입니다.|  
|[메모리 및 페이징 성능 규칙](../profiling/memory-and-paging-performance-rules.md)|애플리케이션의 관리되는 메모리 및 페이징 동작을 분석하는 규칙입니다.|  
|[프로파일링 도구 사용 규칙](../profiling/profiling-tools-usage-rules.md)|프로파일링 도구를 효율적으로 사용하는 데 도움이 되는 규칙입니다.|  
|[리소스 모니터링 성능 규칙](../profiling/resource-monitoring-performance-rules.md)|프로파일링 실행 시의 프로세서 및 메모리 사용률에 대한 정보 메시지입니다.|
