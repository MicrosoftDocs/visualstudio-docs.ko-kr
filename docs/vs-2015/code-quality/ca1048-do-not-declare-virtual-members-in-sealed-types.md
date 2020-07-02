---
title: 'CA1048: 가상 멤버를 sealed 형식으로 선언 하지 마세요. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19ae3a4fdc620343f18aa0845c33e1d73529adfe
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546798"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: 가상 멤버를 sealed 형식으로 선언하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 형식은 sealed 이며 `virtual` 최종이 아닌 (Visual Basic) 인 메서드를 선언 합니다 `Overridable` . 이 규칙은이 패턴을 따라야 하는 대리자 형식에 대 한 위반을 보고 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 상속 형식이 가상 메서드의 구현을 재정의할 수 있도록 하기 위해 형식은 메서드를 가상으로 선언합니다. 정의에 따라 sealed 형식에서 상속할 수 없습니다. sealed 형식의 가상 메서드는 의미가 없습니다.

 Visual Basic .NET 및 c # 컴파일러에서는 형식이이 규칙을 위반 하는 것을 허용 하지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드를 비가상으로 설정 하거나 형식을 상속 가능 하 게 설정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 현재 상태를 유지 하면 유지 관리 문제가 발생할 수 있으며 어떤 이점도 제공 하지 않습니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 형식을 보여 줍니다.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]
