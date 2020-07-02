---
title: 'CA1600: 유휴 상태 프로세스 우선 순위를 사용 하지 마십시오. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3f6233136dcf7f1db5d622a02419d33e0eedacf5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545680"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: 유휴 프로세스 우선 순위를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|범주|Microsoft Mobility|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 이 규칙은 프로세스가로 설정 된 경우에 발생 `ProcessPriorityClass.Idle` 합니다.

## <a name="rule-description"></a>규칙 설명
 프로세스 우선 순위를 유휴 상태로 설정하지 마십시오. 가 있는 프로세스는 `System.Diagnostics.ProcessPriorityClass.Idle` 유휴 상태가 될 때 CPU를 차지 하므로 대기를 차단 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 프로세스를로 설정 `ProcessPriorityClass.BelowNormal` 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙은 유휴 프로세스 우선 순위가 필요한 경우에만 억제 해야 하며 이동성 고려 사항은 안전 하 게 무시할 수 있습니다.
