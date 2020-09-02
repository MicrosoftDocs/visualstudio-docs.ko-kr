---
title: '방법: 수집 방법 선택 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ff14ce88f2032b998214ed11310a15550321dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199803"
---
# <a name="how-to-choose-collection-methods"></a>방법: 컬렉션 방법 선택
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로파일링 도구는 성능 데이터를 수집하는 세 가지 방법, 샘플링, 계측 및 동시성을 지원합니다. 샘플링 또는 계측 방법을 사용하여 .NET 메모리 할당 및 수명 데이터를 수집할 수도 있습니다.  
  
 **요구 사항**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  성능 세션 **Method** 속성을 사용하여 애플리케이션에 가장 적절한 수집 방법을 지정할 수 있습니다. 성능 마법사, 성능 탐색기 또는 성능 세션의 속성 페이지에서 수집 방법을 설정할 수 있습니다. 명령줄 도구를 사용할 경우 자세한 내용은 [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)을 참조하세요.  
  
## <a name="performance-wizard"></a>성능 마법사  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>성능 마법사를 사용하여 수집 방법을 선택하려면  
  
- 마법사의 첫 번째 페이지에서 다음 옵션 중 하나를 선택합니다.  
  
|옵션|설명|  
|------------|-----------------|  
|**CPU 샘플링**|초기 분석 및 CPU 사용률 문제 분석에 유용한 애플리케이션 통계를 수집합니다.|  
|**계측**|집중 분석 및 입/출력 성능 문제 분석에 유용한 자세한 타이밍 데이터를 수집합니다.|  
|**.NET 메모리 할당**|샘플링 프로파일링 방법을 사용하여 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 메모리 할당 데이터를 수집합니다.|  
|**동시성**|숫자 리소스 경합 데이터를 수집합니다.|  
  
## <a name="performance-explorer"></a>성능 탐색기  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>성능 탐색기를 사용하여 수집 방법을 선택하려면  
  
1. **성능 탐색기** 도구 모음에서 **방법** 드롭다운 목록 옆에 있는 화살표를 클릭합니다.  
  
2. 원하는 수집 방법을 클릭합니다.  
  
## <a name="performance-session-property-pages"></a>성능 세션 속성 페이지  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>성능 세션 속성을 사용하여 샘플링 또는 계측 방법을 선택하려면  
  
1. **성능 탐색기**에서 성능 세션을 선택합니다.  
  
     성능 세션 파일 이름의 확장명은 .psess입니다.  
  
2. 성능 세션을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
3. **속성 페이지**에서 **일반**을 클릭합니다.  
  
4. 원하는 수집 방법을 클릭합니다.  
  
    - 샘플링 데이터를 수집할 때 사용할 수 있는 다른 옵션에 대한 자세한 내용은 [샘플링을 사용하여 성능 통계 수집](../profiling/collecting-performance-statistics-by-using-sampling.md)을 참조하세요.  
  
    - 샘플링 데이터를 수집할 때 사용할 수 있는 다른 옵션에 대한 자세한 내용은 [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)을 참조하세요.  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>성능 세션 속성을 사용하여 .NET 메모리 데이터 수집을 선택하려면  
  
1. **성능 탐색기**에서 성능 세션을 선택합니다.  
  
     성능 세션 파일 이름의 확장명은 .psess입니다.  
  
2. 성능 세션을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
3. **속성 페이지**에서 **일반**을 클릭합니다.  
  
4. **샘플링** 또는 **계측**을 클릭합니다.  
  
5. **.NET 개체 할당 정보 수집**을 클릭하여 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 개체 할당의 크기와 개수를 수집합니다.  
  
6. (선택 사항) **추가적으로 .NET 개체 수명 정보 수집**을 클릭하여 개체 메모리가 회수된 가비지 수집 생성에 대한 데이터를 수집합니다.  
  
     .NET 메모리 데이터를 수집할 때 사용할 수 있는 다른 옵션에 대한 자세한 내용은 [.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)을 참조하세요.  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>성능 세션 속성을 사용하여 동시성 데이터 수집을 선택하려면  
  
1. **성능 탐색기**에서 성능 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
2. **속성 페이지**에서 **일반**을 클릭합니다.  
  
3. **동시성**을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)   
 [샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)   
 [성능 세션 속성](../profiling/performance-session-properties.md)
