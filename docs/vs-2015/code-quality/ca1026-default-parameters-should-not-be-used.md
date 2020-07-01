---
title: 'CA1026: 기본 매개 변수를 사용 하면 안 됩니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a63d6e788dd1722d0c593469b225a4f1aeb4738d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548448"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: 기본 매개 변수를 사용하면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 노출 되는 형식에는 기본 매개 변수를 사용 하는 외부적으로 표시 되는 메서드가 포함 됩니다.

## <a name="rule-description"></a>규칙 설명
 기본 매개 변수를 사용 하는 메서드는 CLS (공용 언어 사양)에서 허용 됩니다. 그러나 CLS를 사용 하면 컴파일러에서 이러한 매개 변수에 할당 된 값을 무시할 수 있습니다. 기본 매개 변수 값을 무시 하는 컴파일러에 대해 작성 된 코드는 각 기본 매개 변수에 대 한 인수를 명시적으로 제공 해야 합니다. 프로그래밍 언어에서 원하는 동작을 유지 하려면 기본 매개 변수를 사용 하는 메서드를 기본 매개 변수를 제공 하는 메서드 오버 로드로 바꾸어야 합니다.

 컴파일러는 관리 되는 코드에 액세스할 때 Managed Extension for c + +에 대 한 기본 매개 변수 값을 무시 합니다. Visual Basic 컴파일러는 [선택적](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) 키워드를 사용 하는 기본 매개 변수가 있는 메서드를 지원 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 기본 매개 변수를 사용 하는 메서드를 기본 매개 변수를 제공 하는 메서드 오버 로드로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 기본 매개 변수와 동등한 기능을 제공 하는 오버 로드 된 메서드를 사용 하는 메서드를 보여 줍니다.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1025: 반복 인수를 매개 변수 배열로 바꾸세요.](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>참고 항목
 [언어 독립성 및 언어 독립적 구성 요소](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
