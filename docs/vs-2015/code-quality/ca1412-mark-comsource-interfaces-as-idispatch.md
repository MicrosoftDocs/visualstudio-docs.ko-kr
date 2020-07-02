---
title: 'CA1412: ComSource 인터페이스를 IDispatch로 표시 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5685ad7a760e00392b5f9684cdf399ee320d4a0c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540259"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: ComSource 인터페이스를 IDispatch로 표시하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식이 특성으로 표시 되 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 고 하나 이상의 지정 된 인터페이스가 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 값으로 설정 된 특성으로 표시 되지 않습니다 `InterfaceIsDispatch` .

## <a name="rule-description"></a>규칙 설명
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>는 클래스가 COM (구성 요소 개체 모델) 클라이언트에 노출 하는 이벤트 인터페이스를 식별 하는 데 사용 됩니다. 이러한 인터페이스는 `InterfaceIsIDispatch` Visual Basic 6 COM 클라이언트에서 이벤트 알림을 받을 수 있도록으로 노출 되어야 합니다. 기본적으로 인터페이스를 특성으로 표시 하지 않으면 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 이중 인터페이스로 노출 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 특성을 사용 하 여 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 지정 된 모든 인터페이스에 대해 해당 값이 InterfaceIsIDispatch로 설정 되도록 특성을 추가 하거나 수정 합니다 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 인터페이스 중 하나가 규칙을 위반 하는 클래스를 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1408: AutoDual ClassInterfaceType을 사용하지 마세요.](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>참고 항목
 [방법: COM 싱크에 의해 처리 되는 이벤트 발생](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
