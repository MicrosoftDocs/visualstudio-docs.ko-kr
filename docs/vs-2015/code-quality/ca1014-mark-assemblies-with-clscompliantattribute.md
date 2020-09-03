---
title: 'CA1014: CLSCompliantAttribute를 사용 하 여 어셈블리 표시 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c6dc131a2bb5f0c54943213fbb42561a0c72d95c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545472"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: CLSCompliantAttribute로 어셈블리를 표시하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 어셈블리 <xref:System.CLSCompliantAttribute?displayProperty=fullName> 에 특성이 적용 되지 않았습니다.

## <a name="rule-description"></a>규칙 설명
 CLS(공용 언어 사양)는 어셈블리가 여러 프로그래밍 언어에 사용될 경우 준수해야 하는 명명 제한, 데이터 형식 및 규칙을 정의합니다. 바람직한 디자인은 모든 어셈블리가에 CLS 규격을 명시적으로 표시 하도록 지정 <xref:System.CLSCompliantAttribute> 합니다. 특성이 어셈블리에 없으면 어셈블리가 규격이 아닙니다.

 CLS 규격 어셈블리에는 호환 되지 않는 형식 또는 형식 멤버가 포함 될 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 어셈블리에 특성을 추가 합니다. 전체 어셈블리를 비규격으로 표시 하는 대신 호환 되지 않는 형식 또는 형식 멤버를 확인 하 고 이러한 요소를 표시 해야 합니다. 가능 하면 가능한 가장 넓은 대상이 어셈블리의 모든 기능에 액세스할 수 있도록 비규격 멤버에 대 한 CLS 규격 대체를 제공 해야 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 어셈블리를 규격으로 설정 하지 않으려는 경우 특성을 적용 하 고 해당 값을로 설정 `false` 합니다.

## <a name="example"></a>예
 다음 예제에서는 <xref:System.CLSCompliantAttribute?displayProperty=fullName> CLS 규격을 선언 하는 특성이 적용 된 어셈블리를 보여 줍니다.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>관련 항목
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [언어 독립성 및 언어 독립적 구성 요소](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
