---
title: 'CA1405: com 노출 형식의 기본 형식은 COM 노출 이어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779d3ec1ed520d5d48043f90e7cb6272553012a6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535046"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: COM 노출 형식의 기본 형식은 COM 노출이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|범주|Microsoft.Interoperability|
|변경 수준|DependsOnFix|

## <a name="cause"></a>원인
 Com (구성 요소 개체 모델) 표시 형식이 COM에 표시 되지 않는 형식에서 파생 됩니다.

## <a name="rule-description"></a>규칙 설명
 COM 노출 형식이 새 버전에 멤버를 추가 하는 경우 현재 버전에 바인딩하는 COM 클라이언트의 중단을 방지 하기 위해 엄격한 지침을 따라야 합니다. COM에 표시 되지 않는 형식은 새 멤버를 추가할 때 이러한 COM 버전 관리 규칙을 따르지 않을 것으로 가정 합니다. 그러나 com 노출 형식이 COM에 표시 되지 않는 형식에서 파생 되 고 또는 (기본값)의 클래스 인터페이스를 노출 하는 경우에는 <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> <xref:System.Runtime.InteropServices.ClassInterfaceType> 기본 형식의 모든 PUBLIC 멤버가 com에 표시 됩니다. 기본 형식에서 후속 버전에 새 멤버를 추가 하는 경우 파생 형식의 클래스 인터페이스에 바인딩하는 모든 COM 클라이언트는 중단 될 수 있습니다. Com 노출 형식은 com 클라이언트의 손상 가능성을 줄이기 위해 com 노출 형식 에서만 파생 되어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 기본 형식 COM을 표시 하거나 파생 형식 COM을 숨깁니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>[클래스 인터페이스 소개](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
