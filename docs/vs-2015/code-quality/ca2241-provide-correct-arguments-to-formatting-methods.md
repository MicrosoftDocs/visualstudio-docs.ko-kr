---
title: 'CA2241: 형식 지정 메서드에 올바른 인수를 제공 하십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1dfd770efd4d690930155d2486b8ff1859065272
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543652"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: 서식 지정 메서드에 올바른 인수를 제공하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 `format`, 또는와 같은 메서드에 전달 된 문자열 인수 <xref:System.Console.WriteLine%2A> 에 <xref:System.Console.Write%2A> <xref:System.String.Format%2A?displayProperty=fullName> 각 개체 인수에 해당 하는 형식 항목이 포함 되어 있지 않거나 그 반대의 경우도 마찬가지입니다.

## <a name="rule-description"></a>규칙 설명
 ,, 등의 메서드에 대 한 인수는 <xref:System.Console.WriteLine%2A> <xref:System.Console.Write%2A> <xref:System.String.Format%2A> 형식 문자열과 여러 인스턴스로 구성 됩니다 <xref:System.Object?displayProperty=fullName> . 서식 문자열은 {index [, alignment] [: formatString]} 형식의 텍스트 및 포함 된 서식 항목으로 구성 됩니다. 'index'는 형식을 지정할 개체 부분을 나타내는 0부터 시작하는 정수입니다. 개체에 형식 문자열의 해당 인덱스가 없는 경우 개체는 무시 됩니다. ' Index '로 지정 된 개체가 없으면 <xref:System.FormatException?displayProperty=fullName> 런타임에이 throw 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 각 개체 인수에 형식 항목을 제공 하 고 각 형식 항목에 대 한 개체 인수를 제공 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는 규칙의 두 가지 위반을 보여 줍니다.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
