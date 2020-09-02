---
title: 'CA1044: 속성은 쓰기 전용 이면 안 됩니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ca0fb61c0973553ee6d410bc8b2718d19aeb28c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546863"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: 속성은 쓰기 전용이면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 속성에 set 접근자가 있지만 get 접근자가 없습니다.

## <a name="rule-description"></a>규칙 설명
 Get 접근자는 속성에 대 한 읽기 권한을 제공 하 고 set 접근자는 쓰기 권한을 제공 합니다. 읽기 전용 속성을 사용하는 것은 가능하고 종종 필요하기도 하지만 쓰기 전용 속성의 사용은 금지되어 있습니다. 사용자가 값을 설정 하 고 사용자가 값을 볼 수 없도록 하 여 보안을 제공 하지 않기 때문입니다. 또한 읽기 권한이 없으면 공유 개체의 상태를 볼 수 없으므로 사용하는 데 제한을 받습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 get 접근자를 속성에 추가 합니다. 또는 쓰기 전용 속성의 동작이 필요한 경우이 속성을 메서드로 변환 하는 것이 좋습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시 하지 않는 것이 좋습니다.

## <a name="example"></a>예
 다음 예제에서 `BadClassWithWriteOnlyProperty` 는 쓰기 전용 속성을 사용 하는 형식입니다. `GoodClassWithReadWriteProperty` 수정 된 코드를 포함 합니다.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
