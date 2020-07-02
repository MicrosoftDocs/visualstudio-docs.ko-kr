---
title: 'CA1504: 잘못 필드 이름을 검토 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d375b64bbc877cb377157f13b3e4cfa7c7cf1592
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547877"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: 잘못된 필드 이름을 검토하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|범주|Microsoft 유지 관리|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 인스턴스 필드의 이름은 "s_"로 시작 하거나 `static` ( `Shared` 의 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) 필드 이름이 "m_"로 시작 합니다.

## <a name="rule-description"></a>규칙 설명
 "S_"로 시작 하는 필드 이름은 많은 사용자가 정적 데이터와 연결 됩니다. 마찬가지로 "m_"로 시작 하는 필드 이름은 인스턴스 (멤버) 데이터와 연결 됩니다. 더 쉽게 유지 관리 되는 코드의 경우 이름은 일반적으로 사용 되는 규칙을 따라야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 적절 한 접두사를 사용 하 여 필드의 이름을 바꿉니다. 또는 한정자를 추가 하거나 제거 하 여 필드가 현재 접미사와 일치 하는지 확인 `static` 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.
