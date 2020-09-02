---
title: 'CA1302: 로캘별 문자열을 하드 코딩 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18da0471b1ac62f0e61b303c60b46c15cdc2e428
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539011"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: 로캘별 문자열을 하드코드하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|범주|Microsoft 세계화|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 메서드는 특정 시스템 폴더의 경로 부분을 나타내는 문자열 리터럴을 사용 합니다.

## <a name="rule-description"></a>규칙 설명
 열거형에는 <xref:System.Environment.SpecialFolder?displayProperty=fullName> 특수 시스템 폴더를 참조 하는 멤버가 포함 되어 있습니다. 이러한 폴더의 위치는 운영 체제에 따라 다른 값을 가질 수 있으며, 사용자가 일부 위치를 변경 하 고 위치를 지역화할 수 있습니다. 특수 폴더의 예는 "C:\WINNT\system32 system32" [!INCLUDE[winxp](../includes/winxp-md.md)] 이지만의 "" 인 시스템 폴더입니다 [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] . <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>메서드는 열거형과 연결 된 위치를 반환 합니다 <xref:System.Environment.SpecialFolder> . 에서 반환 되는 위치는 <xref:System.Environment.GetFolderPath%2A> 지역화 되어 현재 실행 중인 컴퓨터에 적합 합니다.

 이 규칙은 메서드를 사용 하 여 검색 된 폴더 경로를 <xref:System.Environment.GetFolderPath%2A> 별도의 디렉터리 수준으로 토큰화 합니다. 각 문자열 리터럴은 토큰과 비교 됩니다. 일치 하는 항목이 있으면 메서드에서 토큰과 연결 된 시스템 위치를 참조 하는 문자열을 작성 하는 것으로 가정 합니다. 이식성 및 지역화 가능성을 위해 메서드를 사용 하 여 <xref:System.Environment.GetFolderPath%2A> 문자열 리터럴을 사용 하는 대신 특수 시스템 폴더의 위치를 검색 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드를 사용 하 여 위치를 검색 합니다 <xref:System.Environment.GetFolderPath%2A> .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 문자열 리터럴이 열거와 연결 된 시스템 위치 중 하나를 참조 하는 데 사용 되지 않는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 <xref:System.Environment.SpecialFolder> 합니다.

## <a name="example"></a>예
 다음 예제에서는이 규칙에서 3 개의 경고를 생성 하는 공용 응용 프로그램 데이터 폴더의 경로를 작성 합니다. 그런 다음 메서드를 사용 하 여 경로를 검색 합니다 <xref:System.Environment.GetFolderPath%2A> .

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1303: 리터럴을 지역화된 매개 변수로 전달하지 마세요.](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
