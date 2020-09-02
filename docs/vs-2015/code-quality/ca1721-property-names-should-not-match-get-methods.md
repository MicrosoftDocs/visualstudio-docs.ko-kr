---
title: 'CA1721: 속성 이름은 get 메서드와 일치 하지 않아야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 77ec48a1164c7065ba5033ef51eb704b8361dc1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544458"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: 속성 이름은 Get 메서드와 달라야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 멤버의 이름은 ' Get '으로 시작 하 고 그렇지 않은 경우 public 또는 protected 속성의 이름과 일치 합니다. 예를 들어 이름이 ' GetColor ' 인 메서드가 포함 된 형식과 ' Color '로 명명 된 속성은이 규칙을 위반 합니다.

## <a name="rule-description"></a>규칙 설명
 Get 메서드 및 속성에는 함수를 명확 하 게 구분 하는 이름이 있어야 합니다.

 명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리를 학습 하는 데 필요한 시간이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했다는 확신을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 ' Get ' 접두사가 붙은 메서드의 이름과 일치 하지 않도록 이름을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

> [!NOTE]
> 가 iextenderprovider 인터페이스를 구현 하 여 Get 메서드가 발생 하면이 경고가 제외 될 수 있습니다.

## <a name="example"></a>예
 다음 예제에는이 규칙을 위반 하는 메서드와 속성이 포함 되어 있습니다.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1024: 적합한 속성을 사용하세요.](../code-quality/ca1024-use-properties-where-appropriate.md)
