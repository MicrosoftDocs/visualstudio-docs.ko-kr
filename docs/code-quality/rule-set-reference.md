---
title: 코드 분석 규칙 집합 참조
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d380346b7e049a6ffc4e8d03a5be27983de10249
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587240"
---
# <a name="code-analysis-rule-set-reference"></a>코드 분석 규칙 집합 참조

Visual Studio에서 관리 코드 프로젝트에 대 한 레거시 분석을 구성 하는 경우 기본 제공 *규칙 집합*목록에서 선택할 수 있습니다. 일부 규칙은 기본 제공 규칙 집합 중 하나 이상에 포함 되어 있습니다. 예를 들어 기본 수정 규칙 규칙 집합에는 관리 권장 규칙 규칙 집합에 있는 규칙이 포함 되어 있습니다.

> [!NOTE]
> 이 섹션의 규칙 집합은 레거시 분석과 관련이 있습니다. 코드 분석기 패키지에 사용할 수 있는 규칙 집합에 대 한 자세한 내용은 [코드 분석기와 함께 규칙 집합 사용](analyzer-rule-sets.md)을 참조 하세요.

이러한 기본 제공 규칙 집합 중 하나를 사용 하거나 프로젝트 요구 사항에 맞게 [규칙 집합을 사용자 지정할](../code-quality/how-to-create-a-custom-rule-set.md) 수 있습니다. 사용자 지정 규칙 집합에 동일한 규칙이 포함 된 여러 규칙 집합을 포함 하는 경우 해당 규칙은 사용자 지정 규칙 집합에 한 번만 표시 됩니다.

이 섹션의 항목에서는 기본 제공 규칙 집합과 여기에 포함 된 규칙 (또는 경고)에 대해 설명 합니다.

| 규칙 집합 | 포함 된 규칙 |
| - | - |
| [모든 규칙](all-rules-rule-set.md) | 사용 가능한 모든 관리 및 c + + 규칙을 포함 합니다. |
| [기본 정확성 규칙](basic-correctness-rules-rule-set-for-managed-code.md) | 논리 오류 및 프레임 워크 사용에 대 한 관리 권장 규칙 및 규칙을 포함 합니다. |
| [확장 정확성 규칙](extended-correctness-rules-rule-set-for-managed-code.md) | 기본 정확성 규칙 (관리 권장 규칙 포함)과 논리 오류 및 프레임 워크 사용에 대 한 추가 규칙을 포함 합니다. |
| [기본 디자인 지침 규칙](basic-design-guideline-rules-rule-set-for-managed-code.md) | 코드를 쉽게 읽고 이해 하 고 유지 관리할 수 있도록 관리 권장 규칙과 규칙을 포함 합니다. |
| [확장 디자인 지침 규칙](extended-design-guidelines-rules-rule-set-for-managed-code.md) | 기본 디자인 지침 규칙 (관리 권장 규칙 포함) 및 이름 지정에 초점을 맞춘 추가 유지 관리 규칙을 포함 합니다. |
| [전역화 규칙](globalization-rules-rule-set-for-managed-code.md) | 세계화 문제에 대 한 규칙을 포함 합니다. |
| [관리 최소 규칙](managed-minimum-rules-rule-set-for-managed-code.md) | 중요 한 관리 코드 문제에 대 한 네 가지 규칙을 포함 합니다. |
| [관리 권장 규칙](managed-recommended-rules-rule-set-for-managed-code.md) | 관리 되는 최소 규칙 및 중요 한 관리 코드 문제에 대 한 추가 규칙을 포함 합니다. |
| [혼합 최소 규칙](mixed-minimum-rules-rule-set.md) | CLR 용 c + + 코드의 중요 한 문제에 대 한 규칙을 포함 합니다. |
| [혼합 권장 규칙](mixed-recommended-rules-rule-set.md) | CLR 용 c + + 코드의 중요 한 문제에 대 한 더 많은 규칙을 포함 하는 혼합 최소 규칙 |
| [네이티브 최소 규칙](native-minimum-rules-rule-set.md) | 네이티브 코드의 중요 한 문제에 대 한 규칙을 포함 합니다. |
| [네이티브 권장 규칙](native-recommended-rules-rule-set.md) | 네이티브 코드의 주요 문제에 대 한 기본 최소 규칙 및 추가 규칙을 포함 합니다. |
| [보안 규칙](security-rules-rule-set-for-managed-code.md) | 보안 취약성을 찾기 위한 규칙을 포함 합니다. |
