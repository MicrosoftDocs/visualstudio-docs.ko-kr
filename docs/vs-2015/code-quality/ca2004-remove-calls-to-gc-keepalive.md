---
title: 'CA2004: GC에 대 한 호출을 제거 합니다. KeepAlive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53fa5f61cb7c503502956831452bc3eca1a9fece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521201"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: GC.KeepAlive에 대한 호출을 제거하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|범주|Microsoft.Reliability|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 클래스는 `SafeHandle` 를 사용 하지만 여전히에 대 한 호출을 포함 `GC.KeepAlive` 합니다.

## <a name="rule-description"></a>규칙 설명
 사용으로 변환 하는 경우 `SafeHandle` (개체)에 대 한 모든 호출을 제거 `GC.KeepAlive` 합니다. 이 경우 클래스는 `GC.KeepAlive` 종료 자가 없지만이에 `SafeHandle` 대 한 OS 핸들을 완료 하기 위해를 사용 한다고 가정 하 여를 호출할 필요가 없습니다.  에 대 한 호출을 종료 하는 비용은 `GC.KeepAlive` 성능으로 측정 되는 것 보다 무시할 수 있지만,에 대 한 호출이 `GC.KeepAlive` 더 이상 존재 하지 않는 수명 문제를 해결 하는 데 필요 하거나 코드를 유지 관리 하기가 어려워질 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 에 대 한 호출을 제거 `GC.KeepAlive` 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 클래스에서 사용으로 변환 하기 위해 기술적으로 정확 하지 않은 경우에만이 경고를 표시 하지 않을 수 있습니다 `SafeHandle` .
