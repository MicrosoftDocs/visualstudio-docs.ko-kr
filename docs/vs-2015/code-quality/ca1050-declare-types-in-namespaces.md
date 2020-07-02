---
title: 'CA1050: 네임 스페이스에서 형식을 선언 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0a4dcc53fac7dc9b7e189686a3b32e2fb4fd030
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539596"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: 네임스페이스에 형식을 선언하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식은 명명 된 네임 스페이스의 범위 밖에 서 정의 됩니다.

## <a name="rule-description"></a>규칙 설명
 형식은 이름 충돌을 방지 하기 위해 네임 스페이스에 선언 되며, 개체 계층 구조에서 관련 형식을 구성 하는 방법으로 선언 됩니다. 명명 된 네임 스페이스 외부에 있는 형식은 코드에서 참조할 수 없는 전역 네임 스페이스에 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 형식을 네임 스페이스에 저장 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시 하지 않아도 되지만 어셈블리를 다른 어셈블리와 함께 사용 하지 않을 경우에는이 작업을 수행 하는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 네임 스페이스 외부에 잘못 선언 된 형식 및 네임 스페이스에 선언 된 동일한 이름의 형식을 가진 라이브러리를 보여 줍니다.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>예제
 다음 응용 프로그램은 이전에 정의 된 라이브러리를 사용 합니다. 네임 스페이스에 `Test` 의해 정규화 되지 않은 이름으로 네임 스페이스 외부에서 선언 된 형식이 만들어집니다. 또한의 형식에 액세스 하려면 `Test` `Goodspace` 네임 스페이스 이름이 필요 합니다.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
