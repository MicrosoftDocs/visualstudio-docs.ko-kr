---
title: 'DA0501: 프로파일링 중인 프로세스의 평균 CPU 사용 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1462ac73e599b870f015a02998c069f7613be0ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155770"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: 프로파일링 중인 프로세스의 평균 CPU 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

규칙 Id | DA501 |  
| 범주 | 리소스 모니터링 |  
| 프로 파일링 방법 | 모두 |  
| 메시지 | 프로 파일링 되 고 있는 프로세스의 평균 CPU 사용입니다. |  
| 규칙 유형 | 정보 |  
  
 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 10개 이상의 샘플을 수집해야 합니다.  
  
## <a name="rule-description"></a>규칙 설명  
 이 메시지는 애플리케이션에서 명령을 실행할 때 프로세서가 사용 중이었던 시간의 백분율을 보고합니다. 보고된 값은 프로파일링되는 프로세스가 활성 상태였던 모든 측정 간격에 대한 평균입니다. 프로세서가 두 개 이상 있는 컴퓨터에서 이 값은 100%보다 클 수 있습니다.  
  
## <a name="how-to-use-rule-data"></a>규칙 데이터를 사용하는 방법  
 규칙 값을 사용하여 프로그램의 여러 가지 버전이나 빌드에 대한 성능을 비교하거나 여러 가지 테스트 시나리오에서 애플리케이션의 성능을 파악합니다.
