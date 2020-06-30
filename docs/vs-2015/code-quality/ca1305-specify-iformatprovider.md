---
title: 'CA1305: IFormatProvider를 지정 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 025d76f8e946dd3021141d6736c6b4bd40d57170
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539088"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider를 지정하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|범주|Microsoft 세계화|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 메서드 또는 생성자가 매개 변수를 허용 하는 오버 로드를 포함 하는 하나 이상의 멤버를 호출 <xref:System.IFormatProvider?displayProperty=fullName> 하 고, 메서드 또는 생성자가 매개 변수를 사용 하는 오버 로드를 호출 하지 않습니다 <xref:System.IFormatProvider> . 이 규칙은 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 매개 변수를 무시 하 <xref:System.IFormatProvider> 고 다음 메서드도 추가로 설명 하는 메서드에 대 한 호출을 무시 합니다.

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>또는 개체를 <xref:System.IFormatProvider> 제공 하지 않으면 오버 로드 된 멤버에서 제공 하는 기본값이 모든 로캘에서 원하는 효과를 갖지 않을 수 있습니다. 또한 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 멤버는 코드에 적합 하지 않을 수 있는 가정을 기반으로 기본 문화권 및 서식 지정을 선택 합니다. 시나리오에 대해 코드가 예상 대로 작동 하는지 확인 하려면 다음 지침에 따라 문화권 관련 정보를 제공 해야 합니다.

- 값이 사용자에 게 표시 되 면 현재 문화권을 사용 합니다. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>을 참조하세요.

- 파일이 나 데이터베이스에 유지 되는 소프트웨어에서 값을 저장 하 고 액세스 하는 경우 고정 문화권을 사용 합니다. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>을 참조하세요.

- 값의 대상을 모르는 경우 데이터 소비자 또는 공급자가 문화권을 지정 하도록 합니다.

  는 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 클래스의 인스턴스를 사용 하 여 지역화 된 리소스를 검색 하는 데만 사용 됩니다 <xref:System.Resources.ResourceManager?displayProperty=fullName> .

  오버 로드 된 멤버의 기본 동작이 사용자의 요구 사항에 적합 한 경우에도 코드를 자체 문서화 하 고 더 쉽게 유지 관리할 수 있도록 문화권 관련 오버 로드를 명시적으로 호출 하는 것이 좋습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 또는를 사용 하는 오버 로드를 사용 하 <xref:System.Globalization.CultureInfo> <xref:System.IFormatProvider> 고 앞에 나열 된 지침에 따라 인수를 지정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 기본 culture/형식 공급자가 올바른 선택이 고 코드 유지 관리는 중요 한 개발 우선 순위가 아닌 것이 확실 한 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예에서는에서 `BadMethod` 이 규칙의 두 위반을 발생 시킵니다. `GoodMethod`는에 고정 문화권을 전달 하 여 첫 번째 위반을 수정 <xref:System.String.Compare%2A> 하 고,가 <xref:System.String.ToLower%2A> 사용자에 게 표시 되기 때문에 현재 문화권을에 전달 하 여 두 번째 위반을 수정 합니다 `string3` .

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 형식에 의해 선택 되는 기본값에 대 한 현재 문화권의 영향을 보여 줍니다 <xref:System.IFormatProvider> <xref:System.DateTime> .

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **오후 6/4/1900 12:15:12** 
 **06/04/1900 12:15:12**
## <a name="related-rules"></a>관련 규칙
 [CA1304: CultureInfo를 지정하세요.](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>참고 항목
 [NIB: CultureInfo 클래스 사용](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
