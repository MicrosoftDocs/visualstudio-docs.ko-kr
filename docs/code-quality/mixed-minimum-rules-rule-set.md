---
title: 혼합 최소 규칙 규칙 집합
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc8df61c-19af-40ab-a871-315807e5f4bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d44b12815f24ea14d35df0e27e5b3f72c296e16
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599577"
---
# <a name="mixed-minimum-rules-rule-set"></a>혼합 최소 규칙 규칙 집합

Microsoft Mixed Minimum 규칙은 잠재적 보안 허점 및 응용 프로그램 충돌을 포함 하 여 공용 언어 런타임을 지 원하는 c + + 프로젝트의 가장 중요 한 문제에 중점을 둡니다.

공용 언어 런타임을 지 원하는 c + + 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에이 규칙 집합을 포함 합니다.

|규칙|설명|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|초기화되지 않은 메모리 사용|
|[C6011](/cpp/code-quality/c6011)|Null 포인터 역참조|
|[C6029](/cpp/code-quality/c6029)|확인되지 않은 값 사용|
|[C6053](/cpp/code-quality/c6053)|호출의 0 종료|
|[C6059](/cpp/code-quality/c6059)|잘못된 연결|
|[C6063](/cpp/code-quality/c6063)|Format 함수에 문자열 인수 없음|
|[C6064](/cpp/code-quality/c6064)|Format 함수에 정수 인수 없음|
|[C6066](/cpp/code-quality/c6066)|Format 함수에 포인터 인수 없음|
|[C6067](/cpp/code-quality/c6067)|Format 함수에 문자열 포인터 인수 없음|
|[C6101](/cpp/code-quality/c6101)|초기화되지 않은 메모리 반환|
|[C6200](/cpp/code-quality/c6200)|인덱스가 버퍼 최대값을 초과함|
|[C6201](/cpp/code-quality/c6201)|인덱스가 스택 버퍼 최대값을 초과함|
|[C6270](/cpp/code-quality/c6270)|Format 함수에 부동 인수 없음|
|[C6271](/cpp/code-quality/c6271)|Format 함수의 추가 인수|
|[C6272](/cpp/code-quality/c6272)|Format 함수의 비부동 인수|
|[C6273](/cpp/code-quality/c6273)|Format 함수에 비정수 인수|
|[C6274](/cpp/code-quality/c6274)|Format 함수의 비문자 인수|
|[C6276](/cpp/code-quality/c6276)|잘못된 문자열 캐스팅|
|[C6277](/cpp/code-quality/c6277)|잘못된 CreateProcess 호출|
|[C6284](/cpp/code-quality/c6284)|Format 함수의 개체 인수 잘못됨|
|[C6290](/cpp/code-quality/c6290)|논리 부정 비트 AND 우선 순위|
|[C6291](/cpp/code-quality/c6291)|논리 부정 비트 OR 우선 순위|
|[C6302](/cpp/code-quality/c6302)|Format 함수에 대한 잘못된 문자열 인수|
|[C6303](/cpp/code-quality/c6303)|Format 함수에 대한 잘못된 와이드 문자열 인수|
|[C6305](/cpp/code-quality/c6305)|크기 및 개수 사용 불일치|
|[C6306](/cpp/code-quality/c6306)|잘못된 변수 인수 함수 호출|
|[C6328](/cpp/code-quality/c6328)|잠재적 인수 형식 불일치|
|[C6385](/cpp/code-quality/c6385)|읽기 오버런|
|[C6386](/cpp/code-quality/c6386)|쓰기 오버런|
|[C6387](/cpp/code-quality/c6387)|잘못된 매개 변수 값|
|[C6500](/cpp/code-quality/c6500)|잘못된 특성 속성|
|[C6501](/cpp/code-quality/c6501)|특성 속성 값 충돌|
|[C6503](/cpp/code-quality/c6503)|참조는 Null일 수 없음|
|[C6504](/cpp/code-quality/c6504)|비포인터에 대한 Null|
|[C6505](/cpp/code-quality/c6505)|Void에 대한 MustCheck|
|[C6506](/cpp/code-quality/c6506)|비포인터 또는 배열에 대한 버퍼 크기|
|[C6508](/cpp/code-quality/c6508)|상수에 대한 쓰기 액세스|
|[C6509](/cpp/code-quality/c6509)|사전 조건에서 반환이 사용됨|
|[C6510](/cpp/code-quality/c6510)|비포인터에 대한 Null 종료|
|[C6511](/cpp/code-quality/c6511)|MustCheck는 Yes 또는 No여야 함|
|[C6513](/cpp/code-quality/c6513)|버퍼 크기가 없는 요소 크기|
|[C6514](/cpp/code-quality/c6514)|버퍼 크기가 배열 크기를 초과함|
|[C6515](/cpp/code-quality/c6515)|비포인터에 대한 버퍼 크기|
|[C6516](/cpp/code-quality/c6516)|특성에 대한 속성 없음|
|[C6517](/cpp/code-quality/c6517)|읽기 불가능 버퍼에 대한 유효 크기|
|[C6518](/cpp/code-quality/c6518)|쓰기 불가능 버퍼에 대한 쓰기 가능 크기|
|[C6522](/cpp/code-quality/c6522)|잘못된 크기 문자열 유형|
|[C6525](/cpp/code-quality/c6525)|잘못된 크기 문자열 접근할 수 없는 위치|
|[C6527](/cpp/code-quality/c6527)|주석이 잘못되었습니다. 'NeedsRelease' 속성은 void 형식 값에 사용할 수 없습니다.|
|[C6530](/cpp/code-quality/c6530)|인식할 수 없는 형식 문자열 스타일|
|[C6540](/cpp/code-quality/c6540)|이 함수에 특성 주석을 사용하면 기존의 모든 __declspec 주석이 무효화됩니다.|
|[C6551](/cpp/code-quality/c6551)|크기 사양이 잘못되었습니다. 식을 구문 분석할 수 없습니다.|
|[C6552](/cpp/code-quality/c6552)|Deref= 또는 Notref=가 잘못되었습니다. 식을 구문 분석할 수 없습니다.|
|[C6701](/cpp/code-quality/c6701)|값이 올바른 Yes/No/Maybe 값이 아닙니다|
|[C6702](/cpp/code-quality/c6702)|값이 문자열 값이 아닙니다.|
|[C6703](/cpp/code-quality/c6703)|값이 숫자가 아닙니다.|
|[C6704](/cpp/code-quality/c6704)|예기치 않은 주석 식 오류가 발생했습니다.|
|[C6705](/cpp/code-quality/c6705)|필요한 주석 인수 개수가 실제 주석 인수 개수와 일치하지 않습니다.|
|[C6706](/cpp/code-quality/c6706)|예기치 않은 주석 오류가 발생했습니다.|
|[C28021](/cpp/code-quality/c28021)|주석이 달린 매개 변수는 포인터여야 합니다.|
|[C28182](/cpp/code-quality/c28182)|NULL 포인터를 역참조하고 있습니다. 포인터에 다른 포인터와 동일한 NULL 값이 포함되어 있습니다.|
|[C28202](/cpp/code-quality/c28202)|비정적 멤버에 대한 잘못된 참조입니다.|
|[C28203](/cpp/code-quality/c28203)|클래스 멤버에 대한 모호한 참조입니다.|
|[C28205](/cpp/code-quality/c28205)|\_\_ \_ \_ \_ 잘못 된 컨텍스트에서 사용 되는 성공 또는 실패 시|
|[C28206](/cpp/code-quality/c28206)|왼쪽 피연산자가 구조체를 가리킵니다. '->'를 사용하세요.|
|[C28207](/cpp/code-quality/c28207)|왼쪽 피연산자가 구조체입니다. '.'를 사용하세요.|
|[C28210](/cpp/code-quality/c28210)|__on_failure 컨텍스트에 대한 주석이 명시적 사전 컨텍스트에 없어야 합니다.|
|[C28211](/cpp/code-quality/c28211)|SAL_context에 대해 정적 컨텍스트 이름이 필요합니다.|
|[C28212](/cpp/code-quality/c28212)|주석에 대한 포인터 식이 있어야 합니다.|
|[C28213](/cpp/code-quality/c28213)|\_ \_ \_ \_ 이전 선언을 수정 하지 않고 참조 하려면 decl 주석 사용 주석을 사용 해야 합니다.|
|[C28214](/cpp/code-quality/c28214)|특성 매개 변수 이름은 p1...p9여야 합니다.|
|[C28215](/cpp/code-quality/c28215)|typefix는 이미 typefix가 있는 매개 변수에 적용할 수 없습니다.|
|[C28216](/cpp/code-quality/c28216)|checkReturn 주석은 특정 함수 매개 변수에 대한 사전 조건에만 적용됩니다.|
|[C28217](/cpp/code-quality/c28217)|함수의 경우 주석에 대한 매개 변수 개수가 파일에 있는 개수와 일치하지 않습니다.|
|[C28218](/cpp/code-quality/c28218)|함수 매개 변수의 경우 주석의 매개 변수가 파일에 있는 매개 변수와 일치 하지 않습니다.|
|[C28219](/cpp/code-quality/c28219)|주석에 있는 매개 변수 주석에 열거의 멤버가 필요합니다.|
|[C28220](/cpp/code-quality/c28220)|주석에 있는 매개 변수에 정수 식이 필요합니다.|
|[C28221](/cpp/code-quality/c28221)|주석에 있는 매개 변수에 문자열 식이 필요합니다.|
|[C28222](/cpp/code-quality/c28222)|주석에 __yes, \__no 또는 \__maybe가 필요합니다.|
|[C28223](/cpp/code-quality/c28223)|주석, 매개 변수에 필요한 토큰/식별자를 찾지 못했습니다.|
|[C28224](/cpp/code-quality/c28224)|주석에 매개 변수가 필요합니다.|
|[C28225](/cpp/code-quality/c28225)|주석에서 올바른 필수 매개 변수의 개수를 찾지 못했습니다.|
|[C28226](/cpp/code-quality/c28226)|또한 주석은 현재 선언에서 PrimOp일 수 없습니다.|
|[C28227](/cpp/code-quality/c28227)|또한 주석은 PrimOp일 수 없습니다(이전 선언 참조).|
|[C28228](/cpp/code-quality/c28228)|주석 매개 변수: 주석에서 형식을 사용할 수 없습니다.|
|[C28229](/cpp/code-quality/c28229)|주석에서 매개 변수를 지원하지 않습니다.|
|[C28230](/cpp/code-quality/c28230)|매개 변수 형식에 멤버가 없습니다.|
|[C28231](/cpp/code-quality/c28231)|주석은 배열에서만 유효합니다.|
|[C28232](/cpp/code-quality/c28232)|pre, post 또는 deref가 주석에 적용되지 않았습니다.|
|[C28233](/cpp/code-quality/c28233)|pre, post 또는 deref가 블록에 적용되었습니다.|
|[C28234](/cpp/code-quality/c28234)|__at 식이 현재 함수에 적용되지 않습니다.|
|[C28235](/cpp/code-quality/c28235)|함수를 단독으로 주석으로 사용할 수 없습니다.|
|[C28236](/cpp/code-quality/c28236)|함수를 식에 사용할 수 없습니다.|
|[C28237](/cpp/code-quality/c28237)|매개 변수에 대한 주석이 더 이상 지원되지 않습니다.|
|[C28238](/cpp/code-quality/c28238)|매개 변수에 대한 주석에 value, stringValue 및 longValue 중 두 개 이상이 있습니다. paramn=xxx를 사용하세요.|
|[C28239](/cpp/code-quality/c28239)|매개 변수에 대한 주석에 value, stringValue 또는 longValue와 paramn=xxx가 모두 있습니다. paramn=xxx만 사용하세요.|
|[C28240](/cpp/code-quality/c28240)|매개 변수에 대한 주석에 param1이 아니라 param2가 있습니다.|
|[C28241](/cpp/code-quality/c28241)|매개 변수에 대한 함수 주석이 인식되지 않습니다.|
|[C28243](/cpp/code-quality/c28243)|매개 변수에 대한 함수 주석에 실제 형식 주석이 허용하는 것보다 많은 역참조가 필요합니다.|
|[C28245](/cpp/code-quality/c28245)|함수에 대한 주석에서 멤버가 아닌 함수에 'this'를 주석으로 답니다.|
|[C28246](/cpp/code-quality/c28246)|함수의 매개 변수 주석이 매개 변수 형식과 일치하지 않습니다.|
|[C28250](/cpp/code-quality/c28250)|함수에 대한 주석이 일치하지 않습니다. 이전 인스턴스에 오류가 있습니다.|
|[C28251](/cpp/code-quality/c28251)|함수에 대한 주석이 일치하지 않습니다. 이 인스턴스에 오류가 있습니다.|
|[C28252](/cpp/code-quality/c28252)|함수에 대한 주석이 일치하지 않습니다. 이 인스턴스에 대한 다른 주석이 매개 변수에 있습니다.|
|[C28253](/cpp/code-quality/c28253)|함수에 대한 주석이 일치하지 않습니다. 이 인스턴스에 대한 다른 주석이 매개 변수에 있습니다.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<>()는 주석에서 지원되지 않습니다.|
|[C28262](/cpp/code-quality/c28262)|주석에 대한 주석 구문 오류가 함수에 있습니다.|
|[C28263](/cpp/code-quality/c28263)|내장 주석에 대한 조건부 주석에 구문 오류가 있습니다.|
|[C28267](/cpp/code-quality/c28267)|함수 주석에서 주석 구문 오류가 발견되었습니다.|
|[C28272](/cpp/code-quality/c28272)|함수, 매개 변수에 대한 주석이 검사 시 함수 선언과 일치하지 않습니다.|
|[C28273](/cpp/code-quality/c28273)|함수의 경우 단서가 함수 선언과 일치하지 않습니다.|
|[C28275](/cpp/code-quality/c28275)|매크로 값에 대 한 매개 변수가 \_ \_ \_ null입니다.|
|[C28279](/cpp/code-quality/c28279)|기호의 경우 일치하는 'end'가 없는 'begin'이 있습니다.|
|[C28280](/cpp/code-quality/c28280)|기호의 경우 일치하는 'begin'이 없는 'end'가 있습니다.|
|[C28282](/cpp/code-quality/c28282)|형식 문자열이 사전 조건에 있어야 합니다.|
|[C28285](/cpp/code-quality/c28285)|함수의 경우 매개 변수에 구문 오류가 있습니다.|
|[C28286](/cpp/code-quality/c28286)|함수의 경우 끝 부분 근처에 구문 오류가 있습니다.|
|[C28287](/cpp/code-quality/c28287)|함수의 경우 \_At\_() 주석에 구문 오류(인식할 수 없는 매개 변수 이름)|
|[C28288](/cpp/code-quality/c28288)|함수의 경우 \_At\_() 주석에 구문 오류(잘못된 매개 변수 이름)|
|[C28289](/cpp/code-quality/c28289)|함수의 경우 ReadableTo 또는 WritableTo에 limit-spec가 매개 변수로 포함되지 않았습니다.|
|[C28290](/cpp/code-quality/c28290)|함수의 주석에 실제 매개 변수 개수보다 많은 외부 참조가 있습니다.|
|[C28291](/cpp/code-quality/c28291)|함수의 경우 역참조 수준 0에서 post null/notnull이 의미가 없습니다.|
|[C28300](/cpp/code-quality/c28300)|연산자에 호환되지 않는 형식의 식 피연산자입니다.|
|[C28301](/cpp/code-quality/c28301)|함수의 첫 번째 선언에 대한 주석이 없습니다.|
|[C28302](/cpp/code-quality/c28302)|주석에 추가 \_Deref\_ 연산자가 있습니다.|
|[C28303](/cpp/code-quality/c28303)|주석에 모호한 \_Deref\_ 연산자가 있습니다.|
|[C28304](/cpp/code-quality/c28304)|토큰에 부적절하게 배치된 \_Notref\_ 연산자가 적용되었습니다.|
|[C28305](/cpp/code-quality/c28305)|토큰을 구문 분석하는 동안 오류가 발생했습니다.|
|[C28350](/cpp/code-quality/c28350)|주석이 조건부로 적용할 수 없는 상황을 설명합니다.|
|[C28351](/cpp/code-quality/c28351)|주석이 동적 값(변수)을 조건에 사용할 수 없는 경우를 설명합니다.|
|[CA1001](../code-quality/ca1001.md)|삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.|
|[CA1821](../code-quality/ca1821.md)|빈 종료자를 제거하십시오.|
|[CA2213](../code-quality/ca2213.md)|삭제 가능한 필드는 삭제해야 합니다.|
|[CA2231](../code-quality/ca2231.md)|ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.|