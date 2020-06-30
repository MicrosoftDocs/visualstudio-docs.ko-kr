---
title: 'CA1804: 사용 하지 않는 지역 제거 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543886"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: 사용되지 않는 로컬 항목을 제거하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|범주|Microsoft 성능|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 메서드는 지역 변수를 선언 하지만 대입문을 받는 사람이 될 수 있다는 점을 제외 하 고는 변수를 사용 하지 않습니다. 이 규칙에의 한 분석을 위해 테스트 된 어셈블리는 디버깅 정보로 빌드해야 하며 연결 된 프로그램 데이터베이스 (.pdb) 파일을 사용할 수 있어야 합니다.

## <a name="rule-description"></a>규칙 설명
 사용되지 않는 지역 변수와 불필요한 할당으로 어셈블리의 크기가 증가하고 성능이 저하될 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 지역 변수를 제거 하거나 사용 합니다. 에 포함 된 c # 컴파일러는 옵션을 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 사용 하는 경우 사용 되지 않는 지역 변수를 제거 합니다 `optimize` .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 변수가 컴파일러에서 발생 한 경우이 규칙에서 경고를 표시 하지 않습니다. 또한이 규칙에서 경고를 표시 하지 않거나 성능 및 코드 유지 관리가 주요 관심사가 아닐 경우 규칙을 사용 하지 않도록 설정 하는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 사용 되지 않는 여러 지역 변수를 보여 줍니다.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1809: 불필요한 로컬 항목을 사용하지 마세요.](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: 호출되지 않는 전용 코드를 사용하지 마세요.](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: 인스턴스화되지 않은 내부 클래스를 사용하지 마세요.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: 사용되지 않은 매개 변수를 검토하세요.](../code-quality/ca1801-review-unused-parameters.md)
