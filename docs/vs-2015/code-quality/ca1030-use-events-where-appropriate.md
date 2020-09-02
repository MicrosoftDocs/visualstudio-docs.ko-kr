---
title: 'CA1030: 적절 한 경우 이벤트를 사용 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1313c5ee79a7a13d3eb937a3431b13ea393857d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544523"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: 적절한 경우 이벤트를 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 Public, protected 또는 private 메서드 이름은 다음 중 하나로 시작 됩니다.

- 기능이

- RemoveOn

- Fire

- 올리려면

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 보통 이벤트에 사용되는 이름을 갖는 메서드를 찾아냅니다. 이벤트는 관찰자 또는 게시-구독 디자인 패턴을 따릅니다. 한 개체의 상태 변경 내용을 다른 개체와 통신 해야 하는 경우에 사용 됩니다. 명확 하 게 정의 된 상태 변경에 대 한 응답으로 메서드를 호출 하는 경우에는 이벤트 처리기에서 메서드를 호출 해야 합니다. 메서드를 호출하는 개체는 메서드를 직접 호출하는 대신 이벤트를 발생시켜야 합니다.

 사용자 인터페이스 응용 프로그램에서 단추를 클릭 하 여 코드 세그먼트를 실행 하는 것과 같은 사용자 작업을 수행 하는 몇 가지 일반적인 이벤트 예제가 있습니다. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]이벤트 모델은 사용자 인터페이스로 제한 되지 않으며, 하나 이상의 개체에 상태 변경 내용을 전달 해야 하는 모든 곳에서 사용 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 개체의 상태가 변경 될 때 메서드가 호출 되 면 이벤트 모델을 사용 하도록 디자인을 변경 하는 것이 좋습니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 메서드가 이벤트 모델에서 작동 하지 않는 경우이 규칙에서 경고를 표시 하지 않습니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .
