---
title: 유지 관리 경고 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e448a72e2ff92b3e3028829d4b1e7658c304ee3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667889"
---
# <a name="maintainability-warnings"></a>유지 관리 경고
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

유지 관리 경고는 라이브러리 및 응용 프로그램 유지 관리를 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA1500: 변수 이름은 필드 이름과 달라야 합니다.](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|인스턴스 메서드는 선언 형식의 인스턴스 필드와 이름이 일치 하는 매개 변수 또는 지역 변수를 선언 합니다 .이로 인해 오류가 발생 합니다.|
|[CA1501: 상속성을 너무 많이 사용하지 마세요.](../code-quality/ca1501-avoid-excessive-inheritance.md)|형식이 상속 계층 구조에서 네 단계보다 아래에 있습니다. 여러 번 중첩된 형식 계층 구조는 추적하고, 이해하고, 유지 관리하기가 어렵습니다.|
|[CA1502: 지나치게 복잡하게 만들지 마세요.](../code-quality/ca1502-avoid-excessive-complexity.md)|이 규칙은 메서드를 통과하는 선형 독립 경로의 수를 측정하며 조건부 분기의 수와 복잡성에 의해 결정됩니다.|
|[CA1504: 잘못된 필드 이름을 검토하세요.](../code-quality/ca1504-review-misleading-field-names.md)|인스턴스 필드의 이름은 "s_"로 시작 하거나 정적 (공유 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) 필드의 이름은 "m_"로 시작 합니다.|
|[CA1505: 유지 관리할 수 없는 코드를 사용하지 마세요.](../code-quality/ca1505-avoid-unmaintainable-code.md)|형식 또는 메서드에 낮은 유지 관리 인덱스 값이 있습니다. 낮은 유지 관리 인덱스는 형식 또는 메서드가 유지 관리하기 어렵고 다시 디자인될 수 있음을 나타냅니다.|
|[CA1506: 클래스를 지나치게 많이 결합하지 마세요.](../code-quality/ca1506-avoid-excessive-class-coupling.md)|이 규칙은 형식 또는 메서드에 들어 있는 고유한 형식 참조의 개수를 계산하여 클래스 결합을 측정합니다.|

## <a name="see-also"></a>관련 항목
 [관리 코드의 복잡성 및 유지 관리 용이성 측정](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
