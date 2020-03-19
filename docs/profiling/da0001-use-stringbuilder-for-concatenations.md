---
title: 'DA0001: 연결에 StringBuilder를 사용하십시오. | Microsoft 문서'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0d93de6ce901bfe4d72628f778b18420beb5ebee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779508"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: 연결에 StringBuilder를 사용하십시오.

|||
|-|-|
|규칙 ID|DA0001|
|Category|.NET Framework 사용|
|프로파일링 방법|샘플링<br /><br /> 계측|
|메시지|문자열 연결에 StringBuilder를 사용해 보세요.|
|메시지 유형|Warning|

## <a name="cause"></a>원인
 System.String.Concat 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 여러 세그먼트에서 문자열을 구성할 때 <xref:System.Text.StringBuilder> 클래스를 사용해 보세요.

## <a name="rule-description"></a>규칙 설명
 <xref:System.String> 개체는 변경할 수 없습니다. 따라서 문자열을 수정하면 새 문자열 개체와 원래 문자열의 가비지 수집이 생성됩니다. String.Concat를 명시적으로 호출하든지 아니면 문자열 연결 연산자(예: + 또는 +=.)를 사용하든지 이 동작은 같습니다. 문자가 타이트 루프의 문자열에 추가되는 경우처럼 이러한 메서드가 빈번히 호출되면 프로그램 성능이 저하될 수 있습니다.

 StringBuilder 클래스는 수정할 수 있는 개체이고, System.String과 달리 이 클래스의 인스턴스를 수정하는 StringBuilder에 대한 대부분 메서드는 같은 인스턴스에 대한 참조를 반환합니다. StringBuilder 인스턴스에 텍스트를 추가하거나 문자를 삽입할 수 있고, 새 인스턴스를 할당하고 원래 인스턴스를 삭제할 필요 없이 인스턴스에서 문자를 제거하거나 바꿀 수 있습니다.

## <a name="how-to-investigate-a-warning"></a>경고를 조사하는 방법
 **오류 목록** 창에서 메시지를 두 번 클릭하여 샘플링 프로필 데이터의 [함수 정보 뷰](../profiling/function-details-view.md)로 이동합니다. 문자열 연결을 가장 자주 사용하는 프로그램 섹션을 찾습니다. 빈번한 문자열 연결 작업을 포함하여 복잡한 문자열 조작에 StringBuilder 클래스를 사용합니다.

 문자열 사용 방법에 대한 자세한 내용은 Microsoft Patterns and Practices 라이브러리에서 [5장 - 관리 코드 성능 향상](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations)의 [문자열 작업](/previous-versions/msp-n-p/ff647790(v=pandp.10)) 섹션을 참조하세요.
