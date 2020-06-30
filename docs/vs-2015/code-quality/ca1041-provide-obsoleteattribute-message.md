---
title: 'CA1041: ObsoleteAttribute 메시지 제공 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d738cf15ebe734cb74e553f38f6eb26af17e8cfd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542313"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute 메시지를 제공하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 형식 또는 멤버가 <xref:System.ObsoleteAttribute?displayProperty=fullName> 해당 속성이 지정 되지 않은 특성을 사용 하 여 표시 됩니다 <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> .

## <a name="rule-description"></a>규칙 설명
 <xref:System.ObsoleteAttribute>는 사용 되지 않는 라이브러리 형식 및 멤버를 표시 하는 데 사용 됩니다. 라이브러리 소비자는 사용 되지 않는 것으로 표시 된 형식이 나 멤버를 사용 하지 않도록 해야 합니다. 이는 지원 되지 않으며 나중 버전의 라이브러리에서 제거 될 수 있기 때문입니다. 를 사용 하 여 표시 된 형식 또는 멤버를 <xref:System.ObsoleteAttribute> 컴파일하면 <xref:System.ObsoleteAttribute.Message%2A> 특성의 속성이 표시 됩니다. 사용되지 않는 형식 또는 멤버에 대한 정보가 사용자에게 제공됩니다. 이 정보에는 일반적으로 사용 되지 않는 형식 또는 멤버가 라이브러리 디자이너에서 지원 되는 기간 및 사용 하려는 기본 설정 대체가 포함 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 `message` 매개 변수를 생성자에 추가 <xref:System.ObsoleteAttribute> 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 <xref:System.ObsoleteAttribute.Message%2A>속성이 사용 되지 않는 형식 또는 멤버에 대 한 중요 한 정보를 제공 하기 때문에이 규칙에서 경고를 표시 하지 마십시오.

## <a name="example"></a>예제
 다음 예제에서는가 올바르게 선언 된 사용 되지 않는 멤버를 보여 줍니다 <xref:System.ObsoleteAttribute> .

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
