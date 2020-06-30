---
title: 'CA1300: MessageBoxOptions를 지정 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: af0017a7ee6918a80a93ca90c7cf3de78885d61f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539193"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions를 지정하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|범주|Microsoft 세계화|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 메서드는 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 인수를 사용 하지 않는 메서드의 오버 로드를 호출 합니다 <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> .

## <a name="rule-description"></a>규칙 설명
 오른쪽에서 왼쪽 읽기 순서를 사용 하는 문화권의 메시지 상자를 올바르게 표시 하려면 <xref:System.Windows.Forms.MessageBoxOptions> <xref:System.Windows.Forms.MessageBoxOptions> 열거형의 및 멤버를 <xref:System.Windows.Forms.MessageBoxOptions> 메서드에 전달 해야 합니다 <xref:System.Windows.Forms.MessageBox.Show%2A> . 포함 하는 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> 컨트롤의 속성을 검사 하 여 오른쪽에서 왼쪽 읽기 순서를 사용할지 여부를 결정 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.Windows.Forms.MessageBox.Show%2A> 인수를 사용 하는 메서드의 오버 로드를 호출 <xref:System.Windows.Forms.MessageBoxOptions> 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 오른쪽에서 왼쪽 읽기 순서를 사용 하는 문화권에 대해 코드 라이브러리를 지역화 하지 않을 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 문화권의 읽기 순서에 적합 한 옵션이 있는 메시지 상자를 표시 하는 메서드를 보여 줍니다. 예제를 빌드하려면 리소스 파일 (표시 되지 않음)이 필요 합니다. 예제의 주석을 따라 리소스 파일 없이 예제를 빌드하고 오른쪽에서 왼쪽으로 기능을 테스트 합니다.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [데스크톱 앱의 리소스](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
