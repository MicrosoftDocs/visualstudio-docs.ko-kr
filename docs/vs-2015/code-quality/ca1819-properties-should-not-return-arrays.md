---
title: 'CA1819: 속성은 배열을 반환 해서는 안 됩니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a96d2164cbd6c03cb0d191b2d0c3c4607468209c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545329"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: 속성은 배열을 반환해서는 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|범주|Microsoft 성능|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 공용 형식의 public 또는 protected 속성은 배열을 반환 합니다.

## <a name="rule-description"></a>규칙 설명
 속성이 읽기 전용 이더라도 속성이 반환 하는 배열은 쓰기 방지 되지 않습니다. 배열을 무단으로 변경하지 못하도록 하려면 속성에서 배열의 복사본을 반환해야 합니다. 일반적으로 사용자는 이러한 속성을 호출할 경우 성능에 부정적인 영향을 준다는 것을 인식하지 못합니다. 특히 속성을 인덱싱된 속성으로 사용할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 속성을 메서드로 설정 하거나 컬렉션을 반환 하도록 속성을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 특성에는 배열을 반환 하는 속성이 포함 될 수 있지만 컬렉션을 반환 하는 속성은 포함 될 수 없습니다. [System.object]에서 파생 된 특성의 속성에 대해 발생 하는 경고를 표시 하지 않을 수 있습니다.<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  --> 클래스. 그렇지 않으면이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example-violation"></a>위반 예

### <a name="description"></a>설명
 다음 예제에서는이 규칙을 위반 하는 속성을 보여 줍니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>주석
 이 규칙 위반 문제를 해결 하려면 속성을 메서드로 설정 하거나 배열 대신 컬렉션을 반환 하도록 속성을 변경 합니다.

## <a name="change-the-property-to-a-method-example"></a>속성을 메서드 예제로 변경 합니다.

### <a name="description"></a>설명
 다음 예제에서는 속성을 메서드로 변경 하 여 위반을 수정 합니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>컬렉션 반환 예제

### <a name="description"></a>설명
 다음 예제에서는를 반환 하도록 속성을 변경 하 여 위반을 수정 합니다.

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>사용자가 속성을 수정할 수 있도록 허용

### <a name="description"></a>설명
 클래스의 소비자가 속성을 수정할 수 있도록 허용 하는 것이 좋습니다. 다음 예제에서는이 규칙을 위반 하는 읽기/쓰기 속성을 보여 줍니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>주석
 다음 예제에서는를 반환 하도록 속성을 변경 하 여 위반을 수정 합니다 <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName> .

### <a name="code"></a>코드
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1024: 적합한 속성을 사용하세요.](../code-quality/ca1024-use-properties-where-appropriate.md)
