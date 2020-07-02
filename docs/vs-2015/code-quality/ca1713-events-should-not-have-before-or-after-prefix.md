---
title: 'CA1713: 이벤트에 before 또는 after 접두사를 사용할 수 없습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b05c39a9d8a4a004359baf63919eb427c25fa5d9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543964"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: 이벤트에 Before 또는 After 접두사를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 이벤트 이름은 ' Before ' 또는 ' After '로 시작 합니다.

## <a name="rule-description"></a>규칙 설명
 이벤트 이름은 이벤트를 발생 시키는 동작을 설명 해야 합니다. 특정 시퀀스에서 발생하는 관련 이벤트의 이름을 지정하려면 현재 또는 과거 시제를 사용하여 동작 시퀀스 내의 상대적인 위치를 나타냅니다. 예를 들어 리소스를 닫을 때 발생 하는 이벤트 쌍의 이름을 지정할 때 ' BeforeClose ' 및 ' AfterClose ' 대신 ' Closing ' 및 ' Closed '로 이름을 지정할 수 있습니다.

 명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이벤트 이름에서 접두사를 제거 하 고 동사의 현재 또는 과거 시제를 사용 하도록 이름을 변경 하는 것이 좋습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.
