---
title: 'CA1726: 선호 하는 용어를 사용 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96e0614bc5c08c83008af4e67a2aa865f08f74f3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547812"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: 기본 설정 용어를 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대 한 최신 설명서는 [CA1726: 사용 약관 사용](/visualstudio/code-quality/ca1726-use-preferred-terms)을 참조 하세요.

|항목|값|
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|범주|Microsoft. 이름 지정|
|변경 수준|중단-어셈블리에서 발생 한 경우<br /><br /> 형식 매개 변수에 대해 발생 하는 경우에는 중단 되지 않습니다.|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 식별자의 이름에 특정 용어가 포함되어 있는데, 이 용어에는 기본 설정된 대체 용어가 있습니다. 또는 이름에 용어 플래그 또는 플래그가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 식별자를 토큰으로 구문 분석 합니다. 각 단일 토큰 및 연속 된 각 이중 토큰 조합은 규칙 및 사용자 지정 사전의 사용 되지 않는 섹션에 기본 제공 되는 용어와 비교 됩니다. 다음 표에서는 규칙에 기본 제공 되는 용어와 해당 규칙의 기본 설정 대안을 보여 줍니다.

|사용 되지 않는 용어|기본 설정 용어|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` 또는 `Flags`|대체 용어가 없습니다. 사용하지 마십시오.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 용어를 기본 대체 단어로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 식별자 이름이 의도적인 경우에만이 규칙에서 경고를 표시 하지 않고, 기본 설정 된 용어 대신 원래 용어와 관련이 있습니다.

## <a name="related-rules"></a>관련 규칙
 [이름 지정 경고](../code-quality/naming-warnings.md)
