---
title: 'CA2132: 기본 생성자는 최소한 기본 형식 기본 생성자 만큼 중요 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 401aa6f5ebec4dac99bedba6f12478c7c48d1dc5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540818"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: 기본 생성자는 기본 형식의 기본 생성자 이상으로 중요해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

> [!NOTE]
> 이 경고는 CoreCLR (Silverlight 웹 응용 프로그램과 관련 된 CLR 버전)을 실행 하는 코드에만 적용 됩니다.

## <a name="cause"></a>원인
 파생 클래스의 기본 생성자에 대 한 투명도 특성은 기본 클래스의 투명도 만큼 중요 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 을 포함 하는 형식 및 멤버는 <xref:System.Security.SecurityCriticalAttribute> Silverlight 응용 프로그램 코드에서 사용할 수 없습니다. 보안에 중요한 형식 및 멤버는 .NET Framework for Silverlight 클래스 라이브러리의 신뢰할 수 있는 코드에서만 사용할 수 있습니다. 파생 클래스의 public 또는 protected 구성 요소는 투명성이 기본 클래스보다 높거나 같아야 하기 때문에 애플리케이션의 클래스는 SecurityCritical로 표시된 클래스에서 파생될 수 없습니다.

 CoreCLR 플랫폼 코드의 경우 기본 형식에 public 또는 protected 불투명 기본 생성자가 있는 경우 파생 된 형식은 기본 생성자 상속 규칙을 준수 해야 합니다. 파생 된 형식에도 기본 생성자가 있어야 하며,이 생성자는 최소한 기본 형식의 중요 한 기본 생성자 여야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 위반 문제를 해결 하려면 형식을 제거 하거나 투명 하지 않은 보안 형식에서 파생 하지 마십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 표시 하지 않습니다. 응용 프로그램 코드에서이 규칙을 위반 하면 CoreCLR이를 사용 하 여 형식을 로드 하지 않습니다 <xref:System.TypeLoadException> .

### <a name="code"></a>코드
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>주석
