---
title: 잠금 동작에 주석 달기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 00d3c90ce7e21ab4e9852ed937481103c351609b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77271596"
---
# <a name="annotating-locking-behavior"></a>잠금 동작에 주석 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다중 스레드 프로그램에서 동시성 버그를 방지하려면 항상 적절한 잠금 규칙을 따르고 SAL 주석을 사용합니다.  
  
 동시성 버그는 명확하지 않기 때문에 재현, 진단 및 디버깅이 상당히 어렵습니다. 스레드 인터리빙에 대한 추론은 가장 좋은 경우 어렵고 스레드가 여러 개인 코드 본문을 디자인하는 경우에는 비현실적이 됩니다. 따라서 다중 스레드 프로그램에서는 잠금 규칙을 따르는 것이 좋습니다. 예를 들어 여러 잠금을 획득한 동안 잠금 순서를 따르면 교착 상태를 방지하는 데 도움이 되고, 공유 리소스에 엑세스하기 전에 적절한 보호 잠금을 획득하면 경합 상태를 방지하는 데 도움이 됩니다.  
  
 하지만 겉보기에 간단해 보이는 잠금 규칙이 실제로는 따르기가 매우 어려울 수 있습니다. 오늘날의 프로그래밍 언어와 컴파일러의 기본적인 제한은 동시성 요구 사항의 사양 및 분석을 직접 지원하지 않는다는 것입니다. 프로그래머는 잠금을 사용하는 방법에 대한 의도를 표현하기 위해 비공식적인 코드 주석에 의존해야 합니다.  
  
 동시성 SAL 주석은 잠금 부작용, 잠금 책임, 데이터 보호, 잠금 순서 계층 구조 및 예상되는 기타 잠금 동작을 지정할 수 있도록 설계되었습니다. 암시적 규칙을 명시적으로 지정함으로써 SAL 동시성 주석은 코드에서 잠금 규칙을 사용하는 방법을 문서화할 수 있는 일관된 방법을 제공합니다. 또한 동시성 주석은 경합 상태, 교착 상태, 일치하지 않는 동기화 작업 및 다른 미묘한 동시성 오류를 찾기 위한 코드 분석 도구의 기능을 향상시킵니다.  
  
## <a name="general-guidelines"></a>일반 지침  
 주석을 사용하여 구현(호출 수신자)과 클라이언트(호출자) 간의 함수 정의에서 암시된 계약을 명시할 수 있으며, 분석을 더욱 개선할 수 있는 프로그램의 고정 항목과 기타 속성을 나타낼 수 있습니다.  
  
 SAL은 임계 영역, 뮤텍스, 스핀 잠금 및 기타 리소스 개체와 같은 다양한 종류의 잠금 기본 형식을 지원합니다. 많은 동시성 주석이 잠금 식을 매개 변수로 사용합니다. 규칙에 따라 잠금은 내부 잠금 개체의 경로 식으로 표시됩니다.  
  
 다음과 같은 스레드 소유권 규칙에 유의해야 합니다.  
  
- 스핀 잠금은 분명한 스레드 소유권이 있는 계산되지 않는 잠금입니다.  
  
- 뮤텍스와 임계 영역은 분명한 스레드 소유권이 있는 계산되는 잠금입니다.  
  
- 세마포와 이벤트는 분명한 스레드 소유권이 없는 계산되는 잠금입니다.  
  
## <a name="locking-annotations"></a>주석 잠금  
 다음 표에서는 잠금 주석을 보여 줍니다.  
  
|주석|설명|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|함수에 주석을 달고 사후 상태에서 함수가 `expr`로 명명된 잠금 개체의 단독 잠금 수를 하나 증가시킴을 나타냅니다.|  
|`_Acquires_lock_(expr)`|함수에 주석을 달고 사후 상태에서 함수가 `expr`로 명명된 잠금 개체의 잠금 수를 하나 증가시킴을 나타냅니다.|  
|`_Acquires_nonreentrant_lock_(expr)`|`expr`로 명명된 잠금이 획득됩니다.  잠금이 이미 유지되고 있으면 오류가 보고됩니다.|  
|`_Acquires_shared_lock_(expr)`|함수에 주석을 달고 사후 상태에서 함수가 `expr`로 명명된 잠금 개체의 공유 잠금 수를 하나 증가시킴을 나타냅니다.|  
|`_Create_lock_level_(name)`|기호 `name`을 잠금 수준으로 선언하여 `_Has_Lock_level_` 및 `_Lock_level_order_` 주석에서 사용될 수 있도록 하는 문입니다.|  
|`_Has_lock_kind_(kind)`|개체에 주석을 달아 리소스 개체의 형식 정보를 구체화합니다. 공용 형식이 여러 종류의 리소스에 사용되고 오버로드된 형식이 다양한 리소스 간의 의미적 요구 사항을 구분하는 데 충분하지 않은 경우가 있습니다. 미리 정의된 `kind` 매개 변수의 목록은 다음과 같습니다.<br /><br /> `_Lock_kind_mutex_`<br /> 뮤텍스에 대한 잠금 종류 ID<br /><br /> `_Lock_kind_event_`<br /> 이벤트에 대한 잠금 종류 ID<br /><br /> `_Lock_kind_semaphore_`<br /> 세마포에 대한 잠금 종류 ID<br /><br /> `_Lock_kind_spin_lock_`<br /> 스핀 잠금에 대한 잠금 종류 ID<br /><br /> `_Lock_kind_critical_section_`<br /> 임계 영역에 대한 잠금 종류 ID|  
|`_Has_lock_level_(name)`|잠금 개체에 주석을 추가하고 `name` 잠금 수준을 부여합니다.|  
|`_Lock_level_order_(name1, name2)`|`name1`과 `name2` 간의 잠금 순서를 제공하는 문입니다.|  
|`_Post_same_lock_(expr1, expr2)`|함수에 주석을 추가하고 사후 상태에서 `expr1` 및 `expr2`라는 두 잠금이 동일한 잠금 개체인 것처럼 처리됨을 나타냅니다.|  
|`_Releases_exclusive_lock_(expr)`|함수에 주석을 달고 사후 상태에서 함수가 `expr`로 명명된 잠금 개체의 단독 잠금 수를 하나 감소시킴을 나타냅니다.|  
|`_Releases_lock_(expr)`|함수에 주석을 추가하고 사후 상태에서 함수가 `expr`로 명명된 잠금 개체의 잠금 수를 하나 감소시킴을 나타냅니다.|  
|`_Releases_nonreentrant_lock_(expr)`|`expr`로 명명된 잠금이 해제됩니다. 잠금이 현재 유지되고 있지 않으면 오류가 보고됩니다.|  
|`_Releases_shared_lock_(expr)`|함수에 주석을 추가하고 사후 상태에서 함수가 `expr`로 명명된 잠금 개체의 공유 잠금 수를 하나 감소시킴을 나타냅니다.|  
|`_Requires_lock_held_(expr)`|함수에 주석을 달고 사전 상태에서 `expr`로 명명된 개체의 잠금 수가 1개 이상임을 나타냅니다.|  
|`_Requires_lock_not_held_(expr)`|함수에 주석을 달고 사전 상태에서 `expr`로 명명된 개체의 잠금 수가 0개임을 나타냅니다.|  
|`_Requires_no_locks_held_`|함수에 주석을 추가하고 검사기에 알려진 모든 잠금의 잠금 수가 0개임을 나타냅니다.|  
|`_Requires_shared_lock_held_(expr)`|함수에 주석을 추가하고 사전 상태에서 `expr`로 명명된 개체의 공유 잠금 수가 1개 이상임을 나타냅니다.|  
|`_Requires_exclusive_lock_held_(expr)`|함수에 주석을 추가하고 사전 상태에서 `expr`로 명명된 개체의 단독 잠금 수가 1개 이상임을 나타냅니다.|  
  
## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>노출되지 않은 잠금 개체에 대한 SAL 내장 함수  
 특정 잠금 개체는 연결된 잠금 함수의 구현에 의해 노출되지 않습니다.  다음 표에서는 이러한 노출되지 않는 잠금 개체에서 작동하는 함수에 주석을 사용하도록 설정하는 SAL 내장 변수를 보여 줍니다.  
  
|주석|설명|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|취소 스핀 잠금을 설명합니다.|  
|`_Global_critical_region_`|임계 영역을 설명합니다.|  
|`_Global_interlock_`|연동 작업을 설명합니다.|  
|`_Global_priority_region_`|우선 순위 영역을 설명합니다.|  
  
## <a name="shared-data-access-annotations"></a>공유 데이터 액세스 주석  
 다음 표에서는 공유 데이터 액세스에 대한 주석을 보여 줍니다.  
  
|주석|설명|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|변수에 주석을 추가하고 변수가 엑세스될 때마다 `expr`로 명명된 잠금 개체의 잠금 수가 1개 이상임을 나타냅니다.|  
|`_Interlocked_`|변수에 주석을 추가하며 `_Guarded_by_(_Global_interlock_)`와 동일합니다.|  
|`_Interlocked_operand_`|주석이 추가된 함수 매개 변수는 다양한 연동 함수 중 하나의 대상 피연산자입니다.  해당 피연산자에는 특정 추가 속성이 있어야 합니다.|  
|`_Write_guarded_by_(expr)`|변수에 주석을 추가하고 변수가 수정될 때마다 `expr`로 명명된 잠금 개체의 잠금 수가 1개 이상임을 나타냅니다.|  
  
## <a name="see-also"></a>관련 항목  
 [C/c + + 코드 오류를 줄이기 위해 SAL 주석 사용](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 이해](../code-quality/understanding-sal.md)   
 [함수 매개 변수 및 반환 값에 주석 달기](../code-quality/annotating-function-parameters-and-return-values.md)   
 [함수 동작에 주석 달기](../code-quality/annotating-function-behavior.md)   
 [구조체 및 클래스에 주석 달기](../code-quality/annotating-structs-and-classes.md)   
 [주석이 적용 되는 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [내장 함수](../code-quality/intrinsic-functions.md)   
 [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)   
 [코드 분석 팀 블로그](https://blogs.msdn.com/b/codeanalysis/)
