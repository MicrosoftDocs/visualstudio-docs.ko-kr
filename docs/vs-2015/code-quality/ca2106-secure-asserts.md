---
title: 'CA2106: 보안 어설션 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eb0e097c2f13fa9d9279a5f3e9761a53cb6e4b1d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547747"
---
# <a name="ca2106-secure-asserts"></a>CA2106: 어설션을 안전하게 보호하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 메서드에서 권한을 어설션하는데 호출자에 대해 보안 검사가 수행되지 않습니다.

## <a name="rule-description"></a>규칙 설명
 보안 검사를 수행하지 않고 보안 권한을 어설션하면 코드에 보안상 취약한 부분이 남아 있을 수 있습니다. 보안 스택 워크는 보안 권한이 어설션 될 때 중지 됩니다. 호출자에 대 한 검사를 수행 하지 않고 권한을 어설션하는 경우 호출자는 권한을 사용 하 여 간접적으로 코드를 실행할 수 있습니다. 보안 검사를 사용 하지 않는 어설션은 어설션이 유해한 방식으로 사용 될 수 없는 경우에만 허용 됩니다. 호출 하는 코드가 무해 하거나 사용자가 호출 하는 코드에 임의의 정보를 전달할 수 없는 경우 어설션이 무해 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드 또는 해당 선언 형식에 보안 요청을 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 신중한 보안 검토 후에만이 규칙에서 경고를 표시 하지 않습니다.

## <a name="see-also"></a>참고 항목
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
