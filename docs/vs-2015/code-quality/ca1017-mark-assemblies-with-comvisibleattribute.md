---
title: 'CA1017: ComVisibleAttribute를 사용 하 여 어셈블리 표시 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 17f0a540a436316d3a4fb3b71a2a51b1c5a90a6d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535072"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: ComVisibleAttribute로 어셈블리를 표시하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 어셈블리 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 에 특성이 적용 되지 않았습니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>특성은 COM 클라이언트가 관리 코드에 액세스 하는 방법을 결정 합니다. 어셈블리에서 COM에 노출할지 여부를 명시적으로 나타내는 것이 좋은 디자인입니다. COM 표시 여부는 전체 어셈블리에 대해 설정할 수 있으며, 개별 형식 및 형식 멤버에 대해 재정의 될 수 있습니다. 특성이 없으면 어셈블리의 내용이 COM 클라이언트에 표시 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 어셈블리에 특성을 추가 합니다. 어셈블리를 COM 클라이언트에 표시 하지 않으려면 특성을 적용 하 고 해당 값을로 설정 `false` 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 어셈블리를 표시 하려면 특성을 적용 하 고 해당 값을로 설정 `true` 합니다.

## <a name="example"></a>예제
 다음 예제에서는 특성이 적용 된 어셈블리를 표시 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 하 여 COM 클라이언트에 표시 되지 않도록 합니다.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>참고 항목
 [비관리 코드와](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [상호 운용 하기 위해 .net 형식의 정규화](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
