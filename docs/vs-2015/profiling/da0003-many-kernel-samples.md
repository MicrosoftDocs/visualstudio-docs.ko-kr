---
title: 'DA0003: 커널 샘플이 많습니다.| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad9a0671595d4628932ff4f2db41a137e060c4d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158719"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: 커널 샘플이 많습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

규칙 Id | DA0003 |  
| 범주 | 프로파일링 도구 사용 |  
| 프로 파일링 방법 | 샘플링 |  
| 메시지 | 커널 모드의 샘플 비율이 높습니다. 이는 많은 양의 I/O 작업 또는 높은 비율의 컨텍스트 전환을 나타낼 수 있습니다. 계측 모드를 사용하여 애플리케이션을 다시 프로파일링하는 것이 좋습니다.|  
| 규칙 유형 | 정보 |  
  
## <a name="cause"></a>원인  
 애플리케이션에 대해 수집된 호출 스택 샘플의 상당 비율이 커널 모드에서 실행되었습니다. 다른 프로파일링 방법을 사용하여 애플리케이션을 프로파일링하는 것이 좋습니다.  
  
## <a name="rule-description"></a>규칙 설명  
 Windows에서 코드는 커널 모드 또는 사용자 모드에서 실행될 수 있습니다. (커널 모드를 특권 모드 라고도 합니다.) 장치 드라이버와 같은 하위 수준 시스템 코드만 커널 모드에서 실행 됩니다. 사용자 모드 애플리케이션이 커널 모드로 전환되어 I/O 작업을 수행하거나, 스레드 또는 프로세스 동기화 기본 형식을 기다리거나, 시스템 호출을 수행할 수 있습니다.  
  
 샘플링은 사용자 모드에서 대부분의 작업 시간을 소비하는 애플리케이션을 프로파일링할 때 가장 효과적입니다. 애플리케이션이 커널 모드에서 실행될 때 수집된 샘플 수는 빈번한 I/O 작업을 나타내거나 컨텍스트 스위치가 발생하는 것을 나타낼 수 있습니다. 이러한 작업은 샘플링 방법을 사용하여 조사할 수 없습니다. 너무 많은 커널 모드 샘플이 수행되는 경우 샘플링 데이터는 통계적으로 중요하도록 충분한 사용자 모드 샘플을 포함할 수 없습니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 다음 옵션 중 하나를 사용하여 애플리케이션을 다시 프로파일링하는 것이 좋습니다.  
  
- 계측 방법을 사용하여 프로파일링합니다.  
  
- 사용자 모드에서 더 많은 샘플을 수집하기 위해 샘플링 비율을 늘립니다.
