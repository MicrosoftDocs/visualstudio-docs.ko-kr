---
title: 'CA1301: 중복 된 가속기를 사용 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 772c9bee3f43c42701bfa460c622f4a225ec59cb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539180"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: 중복 액셀러레이터 키를 사용하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|범주|Microsoft 세계화|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 형식은 <xref:System.Windows.Forms.Control?displayProperty=fullName> 리소스 파일에 저장 된 것과 동일한 액세스 키를 가진 두 개 이상의 최상위 수준 컨트롤을 확장 하 고 포함 합니다.

## <a name="rule-description"></a>규칙 설명
 액셀러레이터 키라고도 하는 선택키를 사용하면 Alt 키를 사용하여 키보드로 컨트롤에 액세스할 수 있습니다. 여러 컨트롤에 중복되는 선택키가 있으면 선택키의 동작이 제대로 정의되지 않은 경우입니다. 사용자가 선택 키를 사용 하 여 의도 한 컨트롤에 액세스 하지 못할 수도 있고 의도 한 것이 아닌 다른 컨트롤을 사용할 수도 있습니다.

 이 규칙의 현재 구현은 메뉴 항목을 무시 합니다. 그러나 동일한 하위 메뉴에 있는 메뉴 항목에는 동일한 액세스 키가 없어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 모든 컨트롤에 대해 고유한 액세스 키를 정의 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 동일한 액세스 키를 가진 두 개의 컨트롤을 포함 하는 최소 폼을 보여 줍니다. 키는 리소스 파일에 저장 되며,이는 표시 되지 않습니다. 그러나 해당 값은 주석 처리 된 줄에 표시 `checkBox.Text` 됩니다. 중복 된 액셀러레이터의 동작을 검사 하 여 `checkBox.Text` 해당 줄을 주석 처리 된 항목과 교환할 수 있습니다. 그러나이 경우에는이 예제에서 규칙의 경고를 생성 하지 않습니다.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [데스크톱 앱의 리소스](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
