---
title: 'DA0004: 프로세서 사용률이 높습니다. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b324d26d21920bae9f03f909b2eab0c1ce7ab419
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777727"
---
# <a name="da0004-high-processor-usage"></a>DA0004: 프로세서 사용률이 높습니다.

|||
|-|-|
|규칙 ID|DA0004|
|Category|프로파일링 도구 사용|
|프로파일링 방법|계측<br /><br /> 샘플링|
|메시지|프로세서 사용률이 지속적으로 75% 이상입니다. CPU 바인딩된 애플리케이션에 샘플링 모드를 사용해 보세요.|
|규칙 유형|정보|

 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 10개 이상의 샘플을 수집해야 합니다.

## <a name="cause"></a>원인
 계측 방법을 사용하여 수집된 프로파일링 데이터에서 프로세서(CPU) 사용률이 높았습니다. CPU 바인딩된 애플리케이션을 프로파일링할 경우 샘플링 프로파일링 방법을 사용해 보세요.

## <a name="rule-description"></a>규칙 설명
 이 프로파일링을 실행하는 동안 하나 이상의 프로세서가 지속적으로 사용 중이었습니다. 높은 CPU 사용률은 CPU 바인딩된 애플리케이션을 나타낼 수 있습니다. 계측된 프로필은 CPU 사용 시나리오를 조사하는 가장 효과적인 방법이 아닙니다. 프로세서에서 명령을 실행하는 데 시간이 오래 걸리는 애플리케이션을 프로파일링할 경우 샘플링이 더 효과적입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 함수 타이밍이 필요하거나 프로세서 병목 현상보다는 입/출력 이해에 더 관심이 있는 경우가 아니면 계측 방법 대신 샘플링 방법을 사용해서 애플리케이션을 다시 프로파일링해 보세요.
