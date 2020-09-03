---
title: 'CA1505: 관행 코드 사용 안 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f2f731b1ac0d87b59c7690d0cf57ade3570ed5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547825"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: 유지 관리할 수 없는 코드를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|범주|Microsoft 유지 관리|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 형식 또는 메서드에 낮은 유지 관리 인덱스 값이 있습니다.

## <a name="rule-description"></a>규칙 설명
 유지 관리 인덱스는 코드 줄, 프로그램 볼륨 및 순환 복잡성의 메트릭을 사용 하 여 계산 됩니다. 프로그램 볼륨은 코드의 연산자 및 피연산자 수를 기반으로 하는 형식 또는 메서드를 이해 하는 데 어려움이 있음을 측정 한 것입니다. 순환 복잡성은 형식 또는 메서드의 구조적 복잡성을 측정 한 것입니다. [관리 코드의 복잡성 및 유지 관리 용이성을 측정 하](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)여 코드 메트릭에 대해 자세히 알아볼 수 있습니다.

 낮은 유지 관리 인덱스는 형식 또는 메서드를 유지 관리 하기 어렵고 다시 디자인 하는 것이 어려울 수 있음을 나타냅니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 위반 문제를 해결 하려면 형식이 나 메서드를 다시 디자인 하 고 더 작고 더 중점을 둘 수 있는 형식 또는 메서드로 분할 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 형식 또는 메서드가 크기를 크게 유지 하거나 형식이 나 메서드를 분할할 수 없는 경우에도이 경고를 제외 합니다.

## <a name="see-also"></a>관련 항목
 [관리 코드의 복잡성 및 유지 관리 용이성을 측정 하는](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [유지 관리 경고](../code-quality/maintainability-warnings.md)
