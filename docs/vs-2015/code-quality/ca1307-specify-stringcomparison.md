---
title: 'CA1307: StringComparison를 지정 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538920"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison 지정하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|범주|Microsoft 세계화|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 문자열 비교 작업에서 매개 변수를 설정 하지 않는 메서드 오버 로드를 사용 <xref:System.StringComparison> 합니다.

## <a name="rule-description"></a>규칙 설명
 대부분의 문자열 작업, <xref:System.String.Compare%2A> 및 메서드는 <xref:System.String.Equals%2A> 열거형 값을 매개 변수로 허용 하는 오버 로드를 제공 <xref:System.StringComparison> 합니다.

 매개 변수를 사용 하는 오버 로드가 있으면 <xref:System.StringComparison> 이 매개 변수를 사용 하지 않는 오버 로드 대신이 오버 로드를 사용 해야 합니다. 이 매개 변수를 명시적으로 설정 하 여 코드를 더 명확 하 고 유지 관리 하는 경우가 많습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 열거형을 매개 변수로 허용 하는 오버 로드에 대 한 문자열 비교 메서드를 변경 <xref:System.StringComparison> 합니다. 예: `String.Compare(str1, str2)` 을로 변경 `String.Compare(str1, str2, StringComparison.Ordinal)` 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 라이브러리나 응용 프로그램이 제한 된 로컬 사용자를 대상으로 하는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="see-also"></a>관련 항목
 [세계화 경고](../code-quality/globalization-warnings.md) [CA1309: 서 수 StringComparison 사용](../code-quality/ca1309-use-ordinal-stringcomparison.md)
