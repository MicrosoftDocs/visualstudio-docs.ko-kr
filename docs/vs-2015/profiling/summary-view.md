---
title: 요약 뷰 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4346b0e7459ee3c78669ab9178555370ffac16d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545511"
---
# <a name="summary-view"></a>요약 뷰
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요약 뷰에는 프로파일링 실행에서 성능상 가장 많은 비용이 소요된 함수 또는 개체에 대한 정보가 표시됩니다. 이 뷰는 타임라인 그래프 및 프로파일링 방법의 성능 메트릭을 기반으로 가장 많은 비용이 소요된 함수 또는 개체의 두 개 이상의 목록을 제공합니다. 이 뷰의 데이터는 사용된 프로파일링 방법(샘플링, 계측 또는 동시성) 및 .NET 메모리 할당이 수집되었는지 여부에 따라 달라집니다.  
  
 동시성 데이터의 요약 뷰를 제외한 모든 요약 뷰의 경우 요약 뷰의 시간 표시 막대 그래프에는 프로파일링이 수행된 시간 동안 프로파일링된 애플리케이션의 프로세서(CPU) 사용률이 표시됩니다.  
  
- 그래프에서 시간을 세그먼트를 지정하는 경우 해당 세그먼트에 대한 데이터를 다시 분석하거나 지정한 세그먼트에 대한 타임라인 디스플레이를 확대/축소할 수 있습니다. 자세한 내용은 [방법: 요약 시간 표시 막대에서 보고서 뷰 필터링](../profiling/how-to-filter-report-views-from-the-summary-timeline.md) 을 참조 하세요.  
  
- 요약 뷰 목록에서 함수를 클릭하여 함수에 대한 함수 정보 뷰를 열 수 있습니다. 또한 다른 뷰 옵션에 대한 함수를 마우스 오른쪽 단추로 클릭할 수도 있습니다.  
  
- 요약 뷰 목록에 표시되는 항목의 수를 수정하려면 **도구** 메뉴를 열고, **옵션**을 가리킨 다음 **성능 도구**를 클릭합니다. **일반 설정** 아래에서 **요약 뷰의 함수 개수** 설정을 수정합니다.  
  
## <a name="notifications-links"></a>알림 링크  
 알림 목록에서 링크를 클릭하여 보고서에 대한 표시 옵션을 설정할 수 있습니다. 목록은 타임라인 그래프의 오른쪽에 있습니다.  
  
|옵션|설명|  
|-|-|  
|**사용자가 작성하지 않은 코드 표시**<br /><br /> **내 코드만 표시**|네이티브 코드 또는 계측 방법을 사용하여 수집된 프로파일링 데이터에 사용할 수 없습니다. 사용자 코드에서 데이터만 표시(**내 코드만 표시**)와 시스템 코드(**사용자가 작성하지 않은 코드 표시**)를 포함하는 모든 코드에서 데이터 표시 사이를 전환합니다. 기본적으로 데이터는 사용자 코드로 제한됩니다. 설정을 변경 하려면 [방법: 보고서 뷰를 필터링 하 여 내 코드만 표시 프로파일링 도구](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)를 참조 하세요.|  
|**지침 보기**|**오류 목록** 창에 성능 규칙 경고를 표시합니다. 자세한 내용은 [성능 규칙을 사용하여 데이터 분석](../profiling/using-performance-rules-to-analyze-data.md)을 참조하세요.|  
  
## <a name="report"></a>보고서  
 보고서 목록에서 링크를 클릭하여 서로 다른 뷰를 열고 보고서를 비교, 저장 또는 필터링할 수 있습니다. 목록은 타임라인 그래프의 오른쪽에 있습니다.  
  
|Name|설명|  
|-|-|  
|**트리밍된 호출 트리 표시**|호출 트리 보기에서 가장 많은 비용이 소요된 실행 경로를 표시합니다. 자세한 내용은 [호출 트리 뷰](../profiling/call-tree-view.md)를 참조 하세요.|  
|**실행 부하 과다 라인 표시**|계측 방법을 사용하여 수집된 프로파일링 데이터에 사용할 수 없습니다. 줄 뷰에서 가장 많은 비용이 소요된 소스 코드 줄을 표시합니다. 자세한 내용은 [줄 뷰](../profiling/lines-view.md)를 참조 하세요.|  
|**보고서 비교**|현재 파일과 비교하도록 다른 프로파일링 데이터 파일을 지정할 수 있는 **비교할 분석 파일 선택** 대화 상자를 표시합니다. 자세한 내용은 [성능 데이터 파일 비교](../profiling/comparing-performance-data-files.md)를 참조하세요.|  
|**보고서 데이터 내보내기**|쉼표로 구분된 값(.csv) 또는 .xml 파일로 저장하도록 하나 이상의 보고서 뷰를 지정할 수 있는 **보고서 내보내기** 대화 상자를 표시합니다. 자세한 내용은 [방법: 프로파일링 도구 보고서 내보내기](https://msdn.microsoft.com/174b5bd3-df9b-4fd4-88d4-76032ab90451)를 참조 하세요.|  
|**분석된 보고서 저장**|현재 프로파일링 데이터 파일을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 대한 인터페이스에서 보다 신속하게 여는 .vsps 파일로 저장합니다. 자세한 내용은 [방법: 분석 된 프로 파일링 데이터 파일 저장](https://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)을 참조 하세요.|  
|**보고서 데이터 필터링**|보고서 뷰에서 데이터를 제한하도록 조건을 지정할 수 있는 프로파일링 보고서 필터 창을 표시합니다. 자세한 내용은 [성능 보고서 뷰 필터](../profiling/performance-report-view-filter.md) 를 참조 하세요.|  
|**전체 화면 설정/해제**|보고서 뷰에 대한 전체 화면 모드를 설정/해제합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [요약 뷰](../profiling/summary-view-sampling-data.md)   
 [요약 뷰](../profiling/summary-view-instrumentation-data.md)   
 [요약 뷰](../profiling/summary-view-dotnet-memory-data.md)
