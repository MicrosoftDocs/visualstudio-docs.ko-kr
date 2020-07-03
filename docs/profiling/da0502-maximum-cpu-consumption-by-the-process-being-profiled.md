---
title: DA0502 - 프로파일링되고 있는 프로세스의 최대 CPU 사용량 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a2555344b402513bdea7795e2e71fde1683b08d1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544562"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: 프로파일링되고 있는 프로세스의 최대 CPU 사용량

|항목|값|
|-|-|
|규칙 ID|DA0502|
|범주|리소스 모니터링|
|프로파일링 방법|모두|
|메시지|이 규칙은 참고용으로만 제공됩니다. Process()\\% Processor Time 카운터는 프로파일링 중인 프로세스의 CPU 사용량을 측정합니다. 보고된 값은 모든 측정 간격에서 관찰되는 최대값입니다.|
|규칙 유형|정보|

 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 10개 이상의 샘플을 수집해야 합니다.

## <a name="rule-description"></a>규칙 설명
 이 메시지는 애플리케이션에서 명령을 실행할 때 프로세서가 사용 중이었던 시간의 최대 백분율을 보고합니다. 보고된 값은 프로파일링되는 프로세스가 활성 상태였던 모든 측정 간격 중에 보고된 최대값입니다. 프로세서가 두 개 이상 있는 컴퓨터에서 이 백분율은 100%보다 클 수 있습니다.

## <a name="how-to-use-the-rule-data"></a>규칙 데이터를 사용하는 방법
 규칙 값을 사용하여 프로그램의 여러 가지 버전이나 빌드에 대한 성능을 비교하거나 여러 가지 프로파일링 시나리오에서 애플리케이션의 성능을 파악합니다.
