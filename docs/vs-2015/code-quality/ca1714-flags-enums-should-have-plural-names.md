---
title: 'CA1714: 플래그 열거형에는 복수형 이름이 있어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 74e93a9644f365120117bd247d2ea8b9d43608cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548189"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: 플래그 열거형에는 복수형 이름을 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 열거형에가 <xref:System.FlagsAttribute?displayProperty=fullName> 있고의 이름이의 ' '로 끝나지 않습니다.

## <a name="rule-description"></a>규칙 설명
 로 표시 된 형식에는 두 개 이상의 <xref:System.FlagsAttribute> 값을 지정할 수 있음을 나타내는 특성으로 인해 복수형 이름이 있습니다. 예를 들어 요일을 정의 하는 열거형은 여러 날짜를 지정할 수 있는 응용 프로그램에서 사용 하기 위한 것입니다. 이 열거형에는를 포함 해야 <xref:System.FlagsAttribute> 하며 ' 일 '을 호출할 수 있습니다. 하루에 한 번만 지정할 수 있는 유사한 열거형은 특성이 없으며 ' Day '를 호출할 수 있습니다.

 명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 열거형의 이름을 복수 단어로 설정 하거나 <xref:System.FlagsAttribute> 여러 열거형 값을 동시에 지정 하지 않아야 하는 경우 특성을 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이름이 복수형 인 경우에는 '. '로 끝나지 않는 경우 위반을 무시 해도 됩니다. 예를 들어 앞에서 설명한 여러 날 열거의 이름이 ' DaysOfTheWeek ' 인 경우이는 규칙의 논리를 위반 하지만 의도는 위반 하지 않습니다. 이러한 위반은 suppressd 해야 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA1027: 열거형을 FlagsAttribute로 표시하세요.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: 열거형을 FlagsAttribute로 표시하지 마세요.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>관련 항목
 <xref:System.FlagsAttribute?displayProperty=fullName>[열거형 디자인](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
