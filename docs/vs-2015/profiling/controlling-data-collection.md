---
title: 데이터 수집 제어 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e34c4db965cacefabe752774e393a4339042040e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182714"
---
# <a name="controlling-data-collection"></a>데이터 수집 제어
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로파일링 도구를 사용하면 성능 세션 중 프로파일링 데이터가 수집되는 시기를 제어하고 프로파일링되는 함수를 지정할 수 있습니다. 이 섹션에서는 **성능 탐색기** 및 **데이터 수집 제어** 창에서 데이터 수집을 시작하고 중지하는 방법 및 프로파일링 데이터가 수집되는 개체를 제한하는 방법을 설명합니다.  
  
## <a name="common-tasks"></a>일반 태스크  
  
|Task|관련 내용|  
|----------|---------------------|  
|**프로파일링 시작 및 중지:** 애플리케이션이 시작되는 경우 애플리케이션 프로파일링을 시작하거나 이미 실행 중인 프로세스에 프로파일러를 연결할 수 있습니다. 대상 애플리케이션이 실행 중일 때 데이터 수집을 일시 중지하고 다시 시작할 수 있습니다. 대상 애플리케이션을 닫거나 실행 중인 프로세스에서 프로파일러를 분리하여 프로파일링 세션을 종료합니다.|-   [방법: 성능 데이터 수집 시작 및 종료](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [방법: 실행 중인 프로세스에 성능 도구 연결 및 분리](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [방법: 성능 데이터 수집 일시 중지 및 다시 시작](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**수집된 데이터를 제한하도록 계측 프로파일링 구성:** 성능 세션 구성 속성을 사용하여 계측 방법을 사용하는 프로파일링 실행에서 수집되는 데이터를 제한할 수 있습니다. 특정 .dll 파일, 네임스페이스, 클래스 및 함수를 포함하거나 제외할 수 있습니다. 지정하는 크기 임계값을 충족하지 않는 함수를 제외할 수도 있습니다.|-   [방법: 계측을 특정 Dll로 제한](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [방법: 특정 함수로 계측 제한](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [방법: 계측에서 간단한 함수 제외 또는 포함](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>관련 섹션  
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>관련 항목  
 [성능 탐색기](../profiling/performance-explorer.md)
