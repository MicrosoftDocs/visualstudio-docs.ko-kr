---
title: DA0029 - 지원되지 않는 CLR 버전 | Microsoft Docs
description: 프로파일링 도구에서 지원되지 않는 .NET Framework 1.1을 사용하는 애플리케이션 프로파일링하려고 합니다.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f5e5129bed479273e141af70121d5a344972e2
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465844"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: 지원되지 않는 CLR 버전

|항목|값|
|-|-|
|규칙 ID|DA0029|
|범주|프로파일링 도구 사용|
|프로파일링 방법|명령줄에서 프로파일링|
|메시지|지원되지 않는 CLR 버전이 수집하는 동안 발견되었습니다. 관리되는 기호가 제대로 확인되지 않을 수 있습니다.|
|규칙 유형|정보.|

## <a name="cause"></a>원인
 프로파일링 도구에서 지원되지 않는 [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]을(를) 사용하는 애플리케이션 프로파일링하려고 합니다.

## <a name="rule-description"></a>규칙 설명
 이 경고는 프로파일링 도구가 애플리케이션에서 실행되는 관리되는 코드에 대한 기호를 확인할 수 없기 때문에 발생합니다. 프로파일링 도구는 [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]을(를) 실행하는 애플리케이션에 대한 관리되는 코드 기호를 확인할 수 없습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 없음
