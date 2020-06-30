---
title: 코드 분석 규칙 집합 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e480869d5b13ecc051deaa97b0bfd2532519d18f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535722"
---
# <a name="code-analysis-rule-set-reference"></a>코드 분석 규칙 집합 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

, 또는에서 관리 코드 프로젝트에 대 한 코드 분석을 구성 하는 경우 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPro](../includes/vspro-md.md)] 기본 제공 *규칙 집합*목록이 표시 됩니다. 표준 규칙 집합 중 하나를 사용하거나 프로젝트 요구 사항에 맞게 규칙 집합을 사용자 지정할 수 있습니다.

## <a name="available-rule-sets"></a>사용 가능한 규칙 집합
 다음 표에는 기본 규칙 집합이 나열됩니다.

|항목|값|
|-|-|
|[모든 규칙 규칙 집합](../code-quality/all-rules-rule-set.md)|이 규칙 집합에는 모든 규칙이 포함 됩니다. 이 규칙 집합을 실행 하면 많은 수의 경고가 보고 될 수 있습니다. 이 규칙 집합을 사용 하 여 코드의 모든 문제를 포괄적으로 파악할 수 있습니다. 이렇게 하면 프로젝트에 대해 실행 하는 데 가장 적합 한 추가 규칙 집합을 결정 하는 데 도움이 됩니다.|
|[관리 코드에 대한 기본 수정 규칙 규칙 집합](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|이러한 규칙은 프레임 워크 Api 사용 시 발생 하는 논리 오류 및 일반적인 실수에 초점을 둡니다. 최소 권장 규칙에서 보고 하는 경고 목록에서 확장 하려면이 규칙 집합을 포함 합니다.|
|[관리 코드에 대한 기본 디자인 지침 규칙 규칙 집합](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|이러한 규칙은 코드를 쉽게 이해 하 고 사용할 수 있도록 모범 사례를 적용 하는 데 중점을 둡니다. 프로젝트에 라이브러리 코드가 포함 되어 있거나 유지 관리 하기 쉬운 코드를 위한 모범 사례를 적용 하려는 경우이 규칙 집합을 포함 합니다.|
|[관리 코드에 대한 확장 수정 규칙 규칙 집합](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|이러한 규칙은 기본 정확성 규칙을 확장 하 여 보고 되는 논리 및 프레임 워크 사용 오류를 최대화 합니다. COM interop 및 모바일 응용 프로그램 등의 특정 시나리오에 대 한 추가 강조가 있습니다. 이러한 시나리오 중 하나가 프로젝트에 적용 되거나 프로젝트에서 추가 문제를 발견 하는 경우이 규칙 집합을 포함 하는 것이 좋습니다.|
|[관리 코드에 대한 확장 디자인 지침 규칙 규칙 집합](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|이러한 규칙은 기본 디자인 지침 규칙을 확장 하 여 보고 되는 유용성 및 유지 관리 문제를 최대화 합니다. 이름 지정 지침에 대 한 추가 강조를 추가 합니다. 프로젝트에 라이브러리 코드가 포함 되어 있거나 유지 관리 가능한 코드를 작성 하는 데 가장 높은 표준을 적용 하려는 경우이 규칙 집합을 포함 하는 것이 좋습니다.|
|[관리 코드에 대한 전역화 규칙 규칙 집합](../code-quality/globalization-rules-rule-set-for-managed-code.md)|이러한 규칙은 다양 한 언어, 로캘 및 문화권에서 사용 하는 경우 응용 프로그램의 데이터가 제대로 표시 되지 않도록 하는 문제에 중점을 둡니다. 응용 프로그램을 지역화 하거나 세계화 하는 경우이 규칙 집합을 포함 합니다.|
|[관리 코드에 대한 관리 최소 규칙 규칙 집합](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|이러한 규칙은 코드 분석이 가장 정확한 코드의 가장 중요 한 문제에 중점을 둡니다.  이러한 규칙은 작은 숫자 이며 제한 된 Visual Studio 버전 에서만 실행 됩니다.  다른 Visual Studio 버전과 함께 MinimumRecommendedRules를 사용 합니다.|
|[관리 코드에 대한 관리 권장 규칙 규칙 집합](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|이러한 규칙은 잠재적 보안 허점, 응용 프로그램 충돌 및 기타 중요 한 논리 및 디자인 오류를 비롯 하 여 코드의 가장 중요 한 문제에 초점을 둡니다. 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에이 규칙 집합을 포함 해야 합니다.|
|[혼합 최소 규칙 규칙 집합](../code-quality/mixed-minimum-rules-rule-set.md)|이러한 규칙은 잠재적 보안 허점 및 응용 프로그램 충돌을 포함 하 여 공용 언어 런타임을 지 원하는 c + + 프로젝트의 가장 중요 한 문제에 중점을 둡니다. 공용 언어 런타임을 지 원하는 c + + 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에이 규칙 집합을 포함 해야 합니다.|
|[혼합 권장 규칙 규칙 집합](../code-quality/mixed-recommended-rules-rule-set.md)|이러한 규칙은 잠재적 보안 허점, 응용 프로그램 충돌 및 기타 중요 한 논리 및 디자인 오류를 포함 하 여 공용 언어 런타임을 지 원하는 c + + 프로젝트의 가장 일반적이 고 중요 한 문제에 중점을 둡니다. 공용 언어 런타임을 지 원하는 c + + 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에이 규칙 집합을 포함 해야 합니다.  이 규칙 집합은 Visual Studio Professional 버전 이상으로 구성 하도록 설계 되었습니다.|
|[네이티브 최소 규칙 규칙 집합](../code-quality/native-minimum-rules-rule-set.md)|이러한 규칙은 잠재적 보안 허점 및 응용 프로그램 충돌을 포함 하 여 네이티브 코드의 가장 중요 한 문제에 중점을 둡니다. 네이티브 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에 이 규칙 집합을 포함해야 합니다.|
|[네이티브 권장 규칙 규칙 집합](../code-quality/native-recommended-rules-rule-set.md)|이러한 규칙은 잠재적 보안 허점 및 응용 프로그램 충돌을 포함 하 여 네이티브 코드의 가장 중요 한 문제 및 일반적인 문제에 중점을 둡니다.  네이티브 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에 이 규칙 집합을 포함해야 합니다.  이 규칙 집합은 Visual Studio Professional 버전 이상에서 사용할 수 있도록 설계 되었습니다.|
|[관리 코드에 대한 보안 규칙 규칙 집합](../code-quality/security-rules-rule-set-for-managed-code.md)|이 규칙 집합에는 모든 Microsoft 보안 규칙이 포함 됩니다. 보고 되는 잠재적인 보안 문제 수를 최대화 하려면이 규칙 집합을 포함 합니다.|
