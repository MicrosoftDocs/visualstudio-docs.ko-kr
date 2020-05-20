---
title: 'DA0008: 수집되는 샘플 수가 적습니다. | Microsoft 문서'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 15f8eeb370a3f1e61981e0e936704d33f6b44bbd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779443"
---
# <a name="da0008-few-samples-collected"></a>DA0008: 수집되는 샘플 수가 적습니다.

|||
|-|-|
|규칙 ID|DA0008|
|Category|프로파일링 도구 사용|
|프로파일링 방법|샘플링|
|메시지|샘플이 몇 개만 수집되었습니다. 보다 의미 있는 결과를 위해 실행 시간을 늘리거나 샘플링 주기를 더 빠르게 해보세요.|
|규칙 유형|정보|

## <a name="cause"></a>원인
 프로파일링 실행에서 샘플이 몇 개만 수집되었습니다.

## <a name="rule-description"></a>규칙 설명
 샘플링 방법을 사용할 경우 데이터가 실제 프로그램 동작을 나타내는지 확인하려면 통계적으로 의미 있는 수의 샘플을 수집해야 합니다. 샘플링 오류를 최소화하려면 프로그램 명령 실행 동작의 샘플을 1000개 이상 수집해야 합니다. 충분한 샘플을 수집하지 않으면 프로파일링 데이터를 분석할 때 결과가 잘못될 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 통계적으로 의미 있는 결과를 얻으려면 더 오래 실행되는 애플리케이션을 프로파일링하거나 더 빠른 샘플링 주기를 사용해 보세요. Visual Studio IDE에서 샘플링 주기를 변경하는 방법에 대한 자세한 내용은 [방법: 샘플링 이벤트 선택](../profiling/how-to-choose-sampling-events.md)을 참조하세요. 프로파일링 도구 명령줄을 사용할 때 샘플링 주기를 변경하는 방법에 대한 자세한 내용은 [VSPerfCmd](../profiling/vsperfcmd.md) 참조에서 [Timer](../profiling/timer.md)를 참조하세요.
