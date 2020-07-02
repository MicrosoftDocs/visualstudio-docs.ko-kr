---
title: 'CA2207: 값 형식 정적 필드를 인라인으로 초기화 하십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792fe18a4f472d0b8a4fd62c652f2ae34fcf6864
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546304"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: 값 형식 정적 필드 인라인을 초기화하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 값 형식은 명시적 정적 생성자를 선언 합니다.

## <a name="rule-description"></a>규칙 설명
 값 형식이 선언 되 면 모든 값 형식 필드를 0으로 설정 하 고 모든 참조 형식 필드를 (Visual Basic)로 설정 하는 기본 초기화를 수행 `null` `Nothing` 합니다. 명시적 정적 생성자는 형식의 인스턴스 생성자 또는 정적 멤버를 호출 하기 전에만 실행 되도록 보장 됩니다. 따라서 인스턴스 생성자를 호출 하지 않고 형식을 만들면 정적 생성자가 실행 되지 않을 수 있습니다.

 모든 정적 데이터를 인라인으로 초기화 하 고 명시적 정적 생성자를 선언 하지 않은 경우 c # 및 Visual Basic 컴파일러는 `beforefieldinit` MSIL 클래스 정의에 플래그를 추가 합니다. 또한 컴파일러는 정적 초기화 코드를 포함 하는 전용 정적 생성자를 추가 합니다. 이 전용 정적 생성자는 형식의 정적 필드에 액세스 하기 전에 실행 되도록 보장 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 선언 될 때 모든 정적 데이터를 초기화 하 고 정적 생성자를 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA1810: 참조 형식 정적 필드를 인라인으로 초기화하세요.](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
