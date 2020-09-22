---
title: 'DA0014: 활성 메모리를 디스크에 페이징하는 비율이 극도로 높습니다. | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf391f96cd21f0c473589d4992083963ff65d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841903"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: 활성 메모리를 디스크에 페이징하는 비율이 매우 높습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

규칙 Id | DA0014 |  
| 범주 | 메모리 및 페이징 |  
| 프로 파일링 방법 | 모두 |  
| 메시지 | 활성 메모리를 디스크에 페이징 하는 비율이 매우 높습니다. 애플리케이션이 메모리 바인딩될 수 있습니다.|  
| 규칙 유형 | 경고 |  
  
 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 25개 이상의 샘플을 수집해야 합니다.  
  
## <a name="cause"></a>원인  
 프로파일링 실행에서 수집된 시스템 성능 데이터는 프로파일링 실행 내내 디스크를 대상으로 한 활성 메모리 페이징의 비율이 극도로 높다는 것을 나타냅니다. 이 수준의 페이징 비율은 대개 애플리케이션 성능 및 응답성에 영향을 미칩니다. 알고리즘을 수정하여 메모리 할당을 줄여 보세요. 애플리케이션의 메모리 요구 사항을 고려해야 할 수도 있습니다. 컴퓨터에서 프로파일링을 실행하려면 더 많은 메모리가 필요합니다.  
  
## <a name="rule-description"></a>규칙 설명  
 디스크에 대한 지나친 페이징의 원인은 실제 메모리가 부족하기 때문일 수 있습니다. 페이징 파일이 있는 실제 디스크가 페이징 작업에 주로 사용된다면 같은 디스크에 대한 다른 애플리케이션 기반 디스크 작업이 느려질 수 있습니다.  
  
 대량 페이징 작업에서는 빈번하게 페이지를 디스크에서 읽고 디스크에 씁니다. 예를 들어 Pages Output/sec 수는 Page Writes/sec 수보다 훨씬 더 큰 경우가 많습니다. Pages Output/sec에는 시스템 파일 캐시의 변경된 데이터 페이지가 포함되기 때문입니다. 그러나 어떤 프로세스가 페이징을 직접 처리하는지 확인하는 것이 쉽지 않을 수도 있습니다.  
  
> [!NOTE]
> 활성 메모리의 페이징 수준이 매우 높은 비율에 도달하면 이 규칙이 실행됩니다. 페이징 수준이 높지만 지나치지 않으면 대신 정보 규칙 [DA0017: 활성 메모리를 디스크에 페이징하는 비율이 매우 높습니다.](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)가 발생합니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 [오류 목록] 창에서 메시지를 두 번 클릭하여 [표시](../profiling/marks-view.md) 뷰로 이동합니다. **Memory\Pages/sec** 열을 찾습니다. 다른 단계보다 페이징 IO 활동이 더 빈번한 특정 프로그램 실행 단계가 있는지 확인합니다.  
  
 부하 테스트 시나리오에서 ASP.NET 애플리케이션에 대한 프로필 데이터를 수집할 경우 추가적인 실제 메모리(또는 RAM)가 구성된 컴퓨터에서 부하 테스트를 다시 실행해 보세요.  
  
 알고리즘을 수정하고 메모리를 많이 사용하는 String.Concat, String.Substring 등의 API 사용을 줄이는 방식으로 메모리 할당을 줄여 보세요.
