---
title: 'CA1500: 변수 이름은 필드 이름과 일치 하지 않아야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9565bc1ae3166c0475e8af7f0fde381497309b01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547916"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: 변수 이름은 필드 이름과 달라야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대 한 최신 설명서는 [CA1500: 변수 이름이 필드 이름과 일치 하지 않아야](/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names)합니다 .를 참조 하세요.

|항목|값|
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|범주|Microsoft 유지 관리|
|변경 수준|필드와 이름이 같은 매개 변수에서 발생 하는 경우:<br /><br /> -중단-변경 내용에 관계 없이 매개 변수를 선언 하는 필드와 메서드를 모두 어셈블리 외부에서 볼 수 없는 경우입니다.<br />-중단-필드 이름을 변경 하는 경우 어셈블리 외부에서 볼 수 있습니다.<br />-중단-매개 변수 이름을 변경 하 고이를 선언 하는 메서드를 어셈블리 외부에서 볼 수 있습니다.<br /><br /> 필드와 이름이 같은 지역 변수에 대해 발생 하는 경우:<br /><br /> -중단-변경 내용에 관계 없이 어셈블리 외부에서 필드를 볼 수 없는 경우입니다.<br />-구분 안 함-지역 변수의 이름을 변경 하 고 필드 이름을 변경 하지 않습니다.<br />-중단-필드 이름을 변경 하는 경우 어셈블리 외부에서 볼 수 있습니다.|

## <a name="cause"></a>원인
 인스턴스 메서드는 선언 형식의 인스턴스 필드와 이름이 일치 하는 매개 변수 또는 지역 변수를 선언 합니다. 규칙을 위반 하는 지역 변수를 catch 하려면 디버깅 정보를 사용 하 여 테스트 된 어셈블리를 빌드해야 하며 연결 된 프로그램 데이터베이스 (.pdb) 파일을 사용할 수 있어야 합니다.

## <a name="rule-description"></a>규칙 설명
 인스턴스 필드 이름이 매개 변수 또는 지역 변수 이름과 일치 하는 경우 `this` `Me` 메서드 본문 내에서 (in) 키워드를 사용 하 여 인스턴스 필드에 액세스 합니다 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . 코드를 유지 관리 하는 경우 이러한 차이를 잊어버릴 수 있으며, 매개 변수/지역 변수가 인스턴스 필드를 참조 하 여 오류가 발생 한다고 가정 합니다. 이는 특히 긴 메서드 본문에 적용 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 매개 변수/변수 또는 필드의 이름을 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는 규칙의 두 가지 위반을 보여 줍니다.

 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
