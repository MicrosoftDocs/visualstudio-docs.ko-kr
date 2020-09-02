---
title: 'CA2108: 값 형식에서 선언적 보안을 검토 합니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03918353b66c36698b5d17b332da052b6d95c87a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544393"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: 값 형식에서 선언적 보안을 검토하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 공용 또는 보호 된 값 형식은 [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) 또는 [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)에 의해 보호 됩니다.

## <a name="rule-description"></a>규칙 설명
 다른 생성자가 실행 되기 전에 값 형식이 기본 생성자에 의해 할당 되 고 초기화 됩니다. 값 형식이 요청 또는 LinkDemand로 보호 되 고 호출자에 게 보안 검사를 충족 하는 권한이 없는 경우에는 기본값이 아닌 생성자가 실패 하 고 보안 예외가 throw 됩니다. 값 형식은 할당 취소 되지 않습니다. 기본 생성자로 설정 된 상태를 유지 합니다. 값 형식의 인스턴스를 전달 하는 호출자에 게 인스턴스를 만들거나 액세스할 수 있는 권한이 있다고 가정해 서는 안 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 형식에서 보안 검사를 제거 하 고 대신 메서드 수준 보안 검사를 사용 하지 않는 한이 규칙 위반 문제를 해결할 수 없습니다. 이러한 방식으로 위반 문제를 해결 하면 권한이 없는 호출자가 값 형식의 인스턴스를 가져올 수 없습니다. 값 형식의 인스턴스가 기본 상태에 있는 경우 중요 한 정보를 노출 하지 않으며 유해한 방식으로 사용할 수 없도록 해야 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 호출자가 보안 위협에 노출 하지 않고 해당 기본 상태에서 값 형식의 인스턴스를 가져올 수 있는 경우이 규칙에서 경고를 표시 하지 않을 수 있습니다.

## <a name="example"></a>예
 다음 예제에서는이 규칙을 위반 하는 값 형식이 포함 된 라이브러리를 보여 줍니다. `StructureManager`형식은 값 형식의 인스턴스를 전달 하는 호출자에 게 인스턴스를 만들거나 액세스할 수 있는 권한이 있다고 가정 합니다.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>예
 다음 응용 프로그램은 라이브러리의 약점을 보여 줍니다.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **구조 사용자 지정 생성자: 요청이 실패 했습니다.** 
 **새 값 SecuredTypeStructure 100 100** 
 **새 값 SecuredTypeStructure 200 200**
## <a name="see-also"></a>관련 항목
 [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
