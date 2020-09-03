---
title: 프로파일링 도구 사용 규칙 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4158a6a393ed6e64dedddfca10c1ae04a95e3d3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535553"
---
# <a name="profiling-tools-usage-rules"></a>프로파일링 도구 사용 규칙
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로파일링 도구 사용 범주의 성능 규칙은 프로파일러를 사용하여 데이터를 가장 효율적으로 수집하기 위한 지침을 제공합니다.  
  
|규칙|설명|  
|-|-|  
|[DA0002: VSPerfCorProf.dll이 없습니다.](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|명령줄 프로파일링에 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 이진 파일에 대한 불완전한 데이터가 포함되어 있을 수 있습니다. 올바른 환경 변수를 설정하지 않은 경우 이러한 현상이 발생할 수 있습니다.|  
|[DA0003: 커널 샘플이 많습니다.](../profiling/da0003-many-kernel-samples.md)|대상 이진 파일 실행 외부에서 발생한 여러 프로파일링 샘플이 기록되었습니다. 보다 정확한 데이터를 수집하려면 계측 방법을 사용해 보세요.|  
|[DA0004: 프로세서 사용률이 높습니다.](../profiling/da0004-high-processor-usage.md)|프로파일링 데이터에서 프로파일링 실행 중에 프로세서의 사용량이 계속 많았음을 나타내고 있습니다. 보다 정확한 데이터를 수집하려면 샘플링 방법을 사용해 보세요.|  
|[DA0008: 수집되는 샘플 수가 적습니다.](../profiling/da0008-few-samples-collected.md)|프로파일링 실행에서 수집되는 샘플의 수가 통계적으로 중요할 만큼 충분하지 않습니다. 다시 프로파일링하고 더 오랫동안 애플리케이션을 실행해 보세요. 계측 방법을 사용하여 데이터를 수집할 수도 있습니다.|  
|[DA0026: 커널 CPU 시간 처리 시간이 너무 깁니다.](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|프로파일링 실행에서 상당 시간이 프로세서 커널 모드에서 소요되었습니다. 시간을 기준으로 사용하는 대신 시스템 호출을 기준으로 사용하여 샘플링해 보세요.|  
|[DA0029: 지원되지 않는 CLR 버전입니다.](../profiling/da0029-unsupported-clr-version.md)|프로파일링된 이진 파일이 프로파일러가 지원하지 않는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전을 사용하고 있습니다. 프로파일러 보고서는 기호 이름을 확인할 수 없습니다.|  
|[DA0030: 데이터베이스 개체의 계층 상호 작용 측정값 수집](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|<xref:System.Data?displayProperty=fullName> 네임스페이스에서 메서드에 대한 많은 수의 호출이 수집되었습니다. 데이터베이스 호출에 대한 데이터를 포함하려면 프로파일 실행에서 계층 상호 작용 데이터를 수집해 보세요.|
