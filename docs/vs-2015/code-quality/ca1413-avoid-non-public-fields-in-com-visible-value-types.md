---
title: 'CA1413: COM 노출 값 형식에 public이 아닌 필드를 사용 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1054330b26cf145ebcbc943a56dc699fe793999f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548462"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: COM 노출 값 형식에 public이 아닌 필드를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 COM (구성 요소 개체 모델)에 표시 되도록 특별히 표시 되는 값 형식은 public이 아닌 인스턴스 필드를 선언 합니다.

## <a name="rule-description"></a>규칙 설명
 public이 아니며 값 형식이 COM에 노출되는 인스턴스 필드는 COM 클라이언트에서 볼 수 있습니다. 필드의 내용을 검토 하 여 노출 되지 않아야 하거나 의도 하지 않은 디자인 또는 보안 효과가 적용 되는 정보를 검토 합니다.

 기본적으로 모든 공용 값 형식은 COM에 표시 됩니다. 그러나 가양성을 줄이기 위해이 규칙을 사용 하려면 형식에 대 한 COM 표시 유형을 명시적으로 명시 해야 합니다. 포함 하는 어셈블리는로 설정 된로 표시 되어야 하 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> `false` 고 형식은로 설정 된로 표시 되어야 합니다 <xref:System.Runtime.InteropServices.ComVisibleAttribute> `true` .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하 고 필드를 숨기려면 값 형식을 참조 형식으로 변경 하거나 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 형식에서 특성을 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 필드의 공개 노출을 허용 하는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1407: COM 노출 형식에 정적 멤버를 사용하지 마세요.](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: ComVisibleAttribute로 어셈블리를 표시하세요.](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>참고 항목
 [비관리 코드와](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [상호 운용 하기 위해 .net 형식의 정규화](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
