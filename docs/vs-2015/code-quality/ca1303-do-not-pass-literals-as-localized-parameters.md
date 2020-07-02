---
title: 'CA1303: 리터럴을 지역화 된 매개 변수로 전달 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ad1f56215d002c03d346b38ce6155e8df7412b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539115"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: 리터럴을 지역화된 매개 변수로 전달하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|범주|Microsoft 세계화|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드는 문자열 리터럴을 클래스 라이브러리의 생성자 또는 메서드에 매개 변수로 전달 하 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 고 해당 문자열을 지역화할 수 있어야 합니다.

 이 경고는 리터럴 문자열이 매개 변수 또는 속성에 값으로 전달 되 고 다음 중 하나 이상이 true 인 경우에 발생 합니다.

- <xref:System.ComponentModel.LocalizableAttribute>매개 변수 또는 속성의 특성이 true로 설정 되어 있습니다.

- 매개 변수 또는 속성 이름에 "Text", "Message" 또는 "Caption"이 포함 되어 있습니다.

- 콘솔에 전달 되는 문자열 매개 변수의 이름입니다. Write 또는 Console. WriteLine 메서드는 "value" 또는 "format"입니다.

## <a name="rule-description"></a>규칙 설명
 소스 코드에 포함 된 문자열 리터럴은 지역화 하기 어렵습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 문자열 리터럴을 클래스의 인스턴스를 통해 검색 된 문자열로 바꿉니다 <xref:System.Resources.ResourceManager> .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 코드 라이브러리가 지역화 되지 않거나 최종 사용자 또는 코드 라이브러리를 사용 하는 개발자에 게 문자열이 노출 되지 않은 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

 사용자는 이름이 인 매개 변수나 속성의 이름을 바꾸거나 이러한 항목을 조건으로 표시 하 여 지역화 된 문자열을 전달 하면 안 되는 메서드에 대해 노이즈를 제거할 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 두 인수 중 하나가 범위를 벗어나는 경우 예외를 throw 하는 메서드를 보여 줍니다. 첫 번째 인수에 대해 예외 생성자는이 규칙을 위반 하는 리터럴 문자열로 전달 됩니다. 두 번째 인수의 경우 생성자는를 통해 검색 된 문자열을 올바르게 전달 합니다 <xref:System.Resources.ResourceManager> .

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>참고 항목
 [데스크톱 앱의 리소스](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
