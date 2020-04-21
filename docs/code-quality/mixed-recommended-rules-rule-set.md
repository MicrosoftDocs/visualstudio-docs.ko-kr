---
title: 혼합 권장 규칙 규칙 집합
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ce28a8c1dd5c9ec510e4bf30b6e710b2b4dbc2a
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649334"
---
# <a name="mixed-recommended-rules-rule-set"></a>혼합 권장 규칙 규칙 집합

Microsoft 혼합 권장 규칙은 잠재적인 보안 허점, 응용 프로그램 충돌 및 기타 중요한 논리 및 디자인 오류를 포함하여 공통 언어 런타임을 지원하는 C++ 프로젝트의 가장 일반적이고 중요한 문제에 중점을 둡니다. 이 규칙 집합에는 [혼합 최소 규칙](mixed-minimum-rules-rule-set.md) 규칙 집합의 모든 규칙이 포함됩니다.

공통 언어 런타임을 지원하는 C++ 프로젝트에 대해 만든 사용자 지정 규칙 집합에 이 규칙 집합을 포함합니다.

|규칙|설명|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|초기화되지 않은 메모리 사용|
|[C6011](../code-quality/c6011.md)|Null 포인터 역참조|
|[C6029](../code-quality/c6029.md)|확인되지 않은 값 사용|
|[C6031](../code-quality/c6031.md)|반환 값 무시|
|[C6053](../code-quality/c6053.md)|호출의 0 종료|
|[C6054](../code-quality/c6054.md)|종료 가 0개 누락|
|[C6059](../code-quality/c6059.md)|잘못된 연결|
|[C6063](../code-quality/c6063.md)|Format 함수에 문자열 인수 없음|
|[C6064](../code-quality/c6064.md)|Format 함수에 정수 인수 없음|
|[C6066](../code-quality/c6066.md)|Format 함수에 포인터 인수 없음|
|[C6067](../code-quality/c6067.md)|Format 함수에 문자열 포인터 인수 없음|
|[C6101](../code-quality/c6101.md)|초기화되지 않은 메모리 반환|
|[C6200](../code-quality/c6200.md)|인덱스가 버퍼 최대값을 초과함|
|[C6201](../code-quality/c6201.md)|인덱스가 스택 버퍼 최대값을 초과함|
|[C6214](../code-quality/c6214.md)|BOOL에 잘못된 캐스트 HRESULT|
|[C6215](../code-quality/c6215.md)|HRESULT에 잘못된 캐스트 BOOL|
|[C6216](../code-quality/c6216.md)|잘못된 컴파일러 삽입 캐스트 BOOL 을 HRESULT로|
|[C6217](../code-quality/c6217.md)|잘못된 HRESULT 테스트(not)가 없는 경우|
|[C6220](../code-quality/c6220.md)|잘못된 HRESULT 와 -1 비교|
|[C6226](../code-quality/c6226.md)|잘못된 HRESULT 할당 -1|
|[C6230](../code-quality/c6230.md)|부울로 잘못된 HRESULT 사용|
|[C6235](../code-quality/c6235.md)|논리적 또는 영하가 아닌 상수|
|[C6236](../code-quality/c6236.md)|논리적 또는 0이 아닌 상수|
|[C6237](../code-quality/c6237.md)|논리적으로 0과 부작용을 잃는다|
|[C6242](../code-quality/c6242.md)|로컬 풀림 강제|
|[C6248](../code-quality/c6248.md)|Null DACL 만들기|
|[C6250](../code-quality/c6250.md)|릴리스되지 않은 주소 설명자|
|[C6255](../code-quality/c6255.md)|알로카의 보호되지 않은 사용|
|[C6258](../code-quality/c6258.md)|스레드 종료 사용|
|[C6259](../code-quality/c6259.md)|비트와이즈 또는 제한된 스위치의 데드 코드|
|[C6260](../code-quality/c6260.md)|바이트 산술 사용|
|[C6262](../code-quality/c6262.md)|과도한 스택 사용|
|[C6263](../code-quality/c6263.md)|알로카 인 루프 사용|
|[C6268](../code-quality/c6268.md)|캐스트에서 누락된 괄호|
|[C6269](../code-quality/c6269.md)|포인터 디레퍼런스 무시|
|[C6270](../code-quality/c6270.md)|Format 함수에 부동 인수 없음|
|[C6271](../code-quality/c6271.md)|Format 함수의 추가 인수|
|[C6272](../code-quality/c6272.md)|Format 함수의 비부동 인수|
|[C6273](../code-quality/c6273.md)|Format 함수에 비정수 인수|
|[C6274](../code-quality/c6274.md)|Format 함수의 비문자 인수|
|[C6276](../code-quality/c6276.md)|잘못된 문자열 캐스팅|
|[C6277](../code-quality/c6277.md)|잘못된 CreateProcess 호출|
|[C6278](../code-quality/c6278.md)|어레이-새로운 스칼라 삭제 불일치|
|[C6279](../code-quality/c6279.md)|스칼라-새로운 어레이-삭제 불일치|
|[C6280](../code-quality/c6280.md)|메모리 할당-할당 할당 불일치|
|[C6281](../code-quality/c6281.md)|비트별 관계 우선 순위|
|[C6282](../code-quality/c6282.md)|과제는 시험을 대체합니다.|
|[C6283](../code-quality/c6283.md)|원시 어레이-새로운 스칼라 삭제 불일치|
|[C6284](../code-quality/c6284.md)|Format 함수의 개체 인수 잘못됨|
|[C6285](../code-quality/c6285.md)|상수의 논리 적 또는|
|[C6286](../code-quality/c6286.md)|제로가 아닌 논리적 또는 손실 부작용|
|[C6287](../code-quality/c6287.md)|중복 테스트|
|[C6288](../code-quality/c6288.md)|논리적 인 이상 상호 포용과 거짓|
|[C6289](../code-quality/c6289.md)|논리적 또는 사실에 대한 상호 배제|
|[C6290](../code-quality/c6290.md)|논리 부정 비트 AND 우선 순위|
|[C6291](../code-quality/c6291.md)|논리 부정 비트 OR 우선 순위|
|[C6292](../code-quality/c6292.md)|최대에서 루프 카운트 업|
|[C6293](../code-quality/c6293.md)|루프가 최소에서 카운트 다운|
|[C6294](../code-quality/c6294.md)|루프 본문이 실행되지 않습니다.|
|[C6295](../code-quality/c6295.md)|무한 루프|
|[C6296](../code-quality/c6296.md)|루프는 한 번만 실행됩니다.|
|[C6297](../code-quality/c6297.md)|더 큰 크기로 시프트 캐스트의 결과|
|[C6299](../code-quality/c6299.md)|비트필드에서 부울 비교까지|
|[C6302](../code-quality/c6302.md)|Format 함수에 대한 잘못된 문자열 인수|
|[C6303](../code-quality/c6303.md)|Format 함수에 대한 잘못된 와이드 문자열 인수|
|[C6305](../code-quality/c6305.md)|크기 및 개수 사용 불일치|
|[C6306](../code-quality/c6306.md)|잘못된 변수 인수 함수 호출|
|[C6308](../code-quality/c6308.md)|리알록 누출|
|[C6310](../code-quality/c6310.md)|잘못된 예외 필터 상수|
|[C6312](../code-quality/c6312.md)|예외 계속 실행 루프|
|[C6314](../code-quality/c6314.md)|비트와이즈 또는 우선 순위|
|[C6317](../code-quality/c6317.md)|보완하지 않음|
|[C6318](../code-quality/c6318.md)|예외 계속 검색|
|[C6319](../code-quality/c6319.md)|쉼표에 의해 무시됨|
|[C6324](../code-quality/c6324.md)|문자열 비교 대신 문자열 복사|
|[C6328](../code-quality/c6328.md)|잠재적 인수 형식 불일치|
|[C6331](../code-quality/c6331.md)|버추얼프리 유효하지 않은 플래그|
|[C6332](../code-quality/c6332.md)|버추얼프리 잘못된 매개 변수|
|[C6333](../code-quality/c6333.md)|버추얼프리 유효하지 않은 크기|
|[C6335](../code-quality/c6335.md)|누수 프로세스 핸들|
|[C6381](../code-quality/c6381.md)|종료 정보 누락|
|[C6383](../code-quality/c6383.md)|요소 수 바이트 수 버퍼 오버런|
|[C6384](../code-quality/c6384.md)|포인터 크기 구분|
|[C6385](../code-quality/c6385.md)|읽기 오버런|
|[C6386](../code-quality/c6386.md)|쓰기 오버런|
|[C6387](../code-quality/c6387.md)|잘못된 매개 변수 값|
|[C6388](../code-quality/c6388.md)|잘못된 매개 변수 값|
|[C6500](../code-quality/c6500.md)|잘못된 특성 속성|
|[C6501](../code-quality/c6501.md)|특성 속성 값 충돌|
|[C6503](../code-quality/c6503.md)|참조는 Null일 수 없음|
|[C6504](../code-quality/c6504.md)|비포인터에 대한 Null|
|[C6505](../code-quality/c6505.md)|Void에 대한 MustCheck|
|[C6506](../code-quality/c6506.md)|비포인터 또는 배열에 대한 버퍼 크기|
|[C6508](../code-quality/c6508.md)|상수에 대한 쓰기 액세스|
|[C6509](../code-quality/c6509.md)|사전 조건에서 반환이 사용됨|
|[C6510](../code-quality/c6510.md)|비포인터에 대한 Null 종료|
|[C6511](../code-quality/c6511.md)|MustCheck는 Yes 또는 No여야 함|
|[C6513](../code-quality/c6513.md)|버퍼 크기가 없는 요소 크기|
|[C6514](../code-quality/c6514.md)|버퍼 크기가 배열 크기를 초과함|
|[C6515](../code-quality/c6515.md)|비포인터에 대한 버퍼 크기|
|[C6516](../code-quality/c6516.md)|특성에 대한 속성 없음|
|[C6517](../code-quality/c6517.md)|읽기 불가능 버퍼에 대한 유효 크기|
|[C6518](../code-quality/c6518.md)|쓰기 불가능 버퍼에 대한 쓰기 가능 크기|
|[C6522](../code-quality/c6522.md)|잘못된 크기 문자열 유형|
|[C6525](../code-quality/c6525.md)|잘못된 크기 문자열 접근할 수 없는 위치|
|[C6527](../code-quality/c6527.md)|주석이 잘못되었습니다. 'NeedsRelease' 속성은 void 형식 값에 사용할 수 없습니다.|
|[C6530](../code-quality/c6530.md)|인식할 수 없는 형식 문자열 스타일|
|[C6540](../code-quality/c6540.md)|이 함수에 특성 주석을 사용하면 기존의 모든 __declspec 주석이 무효화됩니다.|
|[C6551](../code-quality/c6551.md)|크기 사양이 잘못되었습니다. 식을 구문 분석할 수 없습니다.|
|[C6552](../code-quality/c6552.md)|Deref= 또는 Notref=가 잘못되었습니다. 식을 구문 분석할 수 없습니다.|
|[C6701](../code-quality/c6701.md)|값이 올바른 Yes/No/Maybe 값이 아닙니다|
|[C6702](../code-quality/c6702.md)|값이 문자열 값이 아닙니다.|
|[C6703](../code-quality/c6703.md)|값이 숫자가 아닙니다.|
|[C6704](../code-quality/c6704.md)|예기치 않은 주석 식 오류가 발생했습니다.|
|[C6705](../code-quality/c6705.md)|필요한 주석 인수 개수가 실제 주석 인수 개수와 일치하지 않습니다.|
|[C6706](../code-quality/c6706.md)|예기치 않은 주석 오류가 발생했습니다.|
|[C6995](../code-quality/c6995.md)|XML 로그 파일을 저장하지 못했습니다.|
|[C26100](../code-quality/c26100.md)|경합 조건|
|[C26101](../code-quality/c26101.md)|연동 된 작업을 제대로 사용하지 못했습니다.|
|[C26110](../code-quality/c26110.md)|잠금을 유지하지 못하는 발신자|
|[C26111](../code-quality/c26111.md)|잠금을 해제하지 못하는 발신자|
|[C26112](../code-quality/c26112.md)|호출자는 잠금을 보유할 수 없습니다.|
|[C26115](../code-quality/c26115.md)|잠금을 해제하지 못|
|[C26116](../code-quality/c26116.md)|잠금 을 획득하거나 보유하지 못했습니다.|
|[C26117](../code-quality/c26117.md)|보류되지 않은 잠금 해제|
|[C26140](../code-quality/c26140.md)|동시성 SAL 추가 오류|
|[C28020](../code-quality/c28020.md)|이 호출에서 식이 true가 아닙니다.|
|[C28021](../code-quality/c28021.md)|주석이 달린 매개 변수는 포인터여야 합니다.|
|[C28022](../code-quality/c28022.md)|이 함수의 함수 클래스(es)는 함수를 정의하는 데 사용되는 typedef의 함수 클래스(es)와 일치하지 않습니다.|
|[C28023](../code-quality/c28023.md)|할당되거나 전달되는 함수에는 \_\_하나\_ 이상의 클래스(es)에 대한 Function 클래스 추가가 있어야 합니다.|
|[C28024](../code-quality/c28024.md)|할당되는 함수 포인터는 함수 클래스(es) 목록에 포함되지 않은 함수 클래스에 추가됩니다.|
|[C28039](../code-quality/c28039.md)|실제 매개 변수의 형식이 형식과 정확히 일치해야 합니다.|
|[C28112](../code-quality/c28112.md)|인터로직 된 함수를 통해 액세스되는 변수는 항상 인터로직 된 함수를 통해 액세스해야합니다.|
|[C28113](../code-quality/c28113.md)|연동 함수를 통해 로컬 변수액세스|
|[C28125](../code-quality/c28125.md)|함수는 try/제외 블록 내에서 호출되어야 합니다.|
|[C28137](../code-quality/c28137.md)|변수 인수는 대신 (리터럴) 상수여야 합니다.|
|[C28138](../code-quality/c28138.md)|상수 인수는 대신 변수여야 합니다.|
|[C28159](../code-quality/c28159.md)|대신 다른 함수를 사용하는 것이 좋습니다.|
|[C28160](../code-quality/c28160.md)|오류 주석|
|[C28163](../code-quality/c28163.md)|try/제외 블록 내에서 함수를 호출해서는 안 됩니다.|
|[C28164](../code-quality/c28164.md)|인수는 개체에 대한 포인터를 기대하는 함수에 전달되고 있습니다(포인터에 대한 포인터가 아님).|
|[C28182](../code-quality/c28182.md)|NULL 포인터를 역참조하고 있습니다. 포인터에 다른 포인터와 동일한 NULL 값이 포함되어 있습니다.|
|[C28183](../code-quality/c28183.md)|인수는 하나의 값일 수 있으며 포인터에 있는 값의 복사본입니다.|
|[C28193](../code-quality/c28193.md)|변수에는 검사해야 하는 값이 있습니다.|
|[C28196](../code-quality/c28196.md)|요구 사항이 충족되지 않습니다. (식은 true로 평가되지 않습니다.)|
|[C28202](../code-quality/c28202.md)|비정적 멤버에 대한 잘못된 참조입니다.|
|[C28203](../code-quality/c28203.md)|클래스 멤버에 대한 모호한 참조입니다.|
|[C28205](../code-quality/c28205.md)|\_잘못된\_ \_컨텍스트에서 사용된\_성공 또는 실패\_ 시|
|[C28206](../code-quality/c28206.md)|왼쪽 피연산자가 구조체를 가리킵니다. '->'를 사용하세요.|
|[C28207](../code-quality/c28207.md)|왼쪽 피연산자가 구조체입니다. '.'를 사용하세요.|
|[C28209](../code-quality/c28209.md)|기호선언에 충돌선언이 있습니다.|
|[C28210](../code-quality/c28210.md)|__on_failure 컨텍스트에 대한 주석이 명시적 사전 컨텍스트에 없어야 합니다.|
|[C28211](../code-quality/c28211.md)|SAL_context에 대해 정적 컨텍스트 이름이 필요합니다.|
|[C28212](../code-quality/c28212.md)|주석에 대한 포인터 식이 있어야 합니다.|
|[C28213](../code-quality/c28213.md)|사용 \_\_디클\_주석\_ 주석은 수정 없이 이전 선언을 참조하는 데 사용해야 합니다.|
|[C28214](../code-quality/c28214.md)|특성 매개 변수 이름은 p1...p9여야 합니다.|
|[C28215](../code-quality/c28215.md)|typefix는 이미 typefix가 있는 매개 변수에 적용할 수 없습니다.|
|[C28216](../code-quality/c28216.md)|checkReturn 주석은 특정 함수 매개 변수에 대한 사전 조건에만 적용됩니다.|
|[C28217](../code-quality/c28217.md)|함수의 경우 주석에 대한 매개 변수 개수가 파일에 있는 개수와 일치하지 않습니다.|
|[C28218](../code-quality/c28218.md)|함수 매개 변수의 경우 부침의 매개 변수가 파일에서 찾은 매개 변수와 일치하지 않습니다.|
|[C28219](../code-quality/c28219.md)|주석에 있는 매개 변수 주석에 열거의 멤버가 필요합니다.|
|[C28220](../code-quality/c28220.md)|주석에 있는 매개 변수에 정수 식이 필요합니다.|
|[C28221](../code-quality/c28221.md)|주석에 있는 매개 변수에 문자열 식이 필요합니다.|
|[C28222](../code-quality/c28222.md)|주석에 __yes, \__no 또는 \__maybe가 필요합니다.|
|[C28223](../code-quality/c28223.md)|주석, 매개 변수에 필요한 토큰/식별자를 찾지 못했습니다.|
|[C28224](../code-quality/c28224.md)|주석에 매개 변수가 필요합니다.|
|[C28225](../code-quality/c28225.md)|주석에서 올바른 필수 매개 변수의 개수를 찾지 못했습니다.|
|[C28226](../code-quality/c28226.md)|또한 주석은 현재 선언에서 PrimOp일 수 없습니다.|
|[C28227](../code-quality/c28227.md)|또한 주석은 PrimOp일 수 없습니다(이전 선언 참조).|
|[C28228](../code-quality/c28228.md)|주석 매개 변수: 주석에서 형식을 사용할 수 없습니다.|
|[C28229](../code-quality/c28229.md)|주석에서 매개 변수를 지원하지 않습니다.|
|[C28230](../code-quality/c28230.md)|매개 변수 형식에 멤버가 없습니다.|
|[C28231](../code-quality/c28231.md)|주석은 배열에서만 유효합니다.|
|[C28232](../code-quality/c28232.md)|pre, post 또는 deref가 주석에 적용되지 않았습니다.|
|[C28233](../code-quality/c28233.md)|pre, post 또는 deref가 블록에 적용되었습니다.|
|[C28234](../code-quality/c28234.md)|__at 식이 현재 함수에 적용되지 않습니다.|
|[C28235](../code-quality/c28235.md)|함수를 단독으로 주석으로 사용할 수 없습니다.|
|[C28236](../code-quality/c28236.md)|함수를 식에 사용할 수 없습니다.|
|[C28237](../code-quality/c28237.md)|매개 변수에 대한 주석이 더 이상 지원되지 않습니다.|
|[C28238](../code-quality/c28238.md)|매개 변수에 대한 주석에 value, stringValue 및 longValue 중 두 개 이상이 있습니다. paramn=xxx를 사용하세요.|
|[C28239](../code-quality/c28239.md)|매개 변수에 대한 주석에 value, stringValue 또는 longValue와 paramn=xxx가 모두 있습니다. paramn=xxx만 사용하세요.|
|[C28240](../code-quality/c28240.md)|매개 변수에 대한 주석에 param1이 아니라 param2가 있습니다.|
|[C28241](../code-quality/c28241.md)|매개 변수에 대한 함수 주석이 인식되지 않습니다.|
|[C28243](../code-quality/c28243.md)|매개 변수에 대한 함수 주석에 실제 형식 주석이 허용하는 것보다 많은 역참조가 필요합니다.|
|[C28244](../code-quality/c28244.md)|함수에 대한 부침에는 비교할 수 없는 매개 변수/외부 부침이 있습니다.|
|[C28245](../code-quality/c28245.md)|함수에 대한 주석에서 멤버가 아닌 함수에 'this'를 주석으로 답니다.|
|[C28246](../code-quality/c28246.md)|함수의 매개 변수 주석이 매개 변수 형식과 일치하지 않습니다.|
|[C28250](../code-quality/c28250.md)|함수에 대한 주석이 일치하지 않습니다. 이전 인스턴스에 오류가 있습니다.|
|[C28251](../code-quality/c28251.md)|함수에 대한 주석이 일치하지 않습니다. 이 인스턴스에 오류가 있습니다.|
|[C28252](../code-quality/c28252.md)|함수에 대한 주석이 일치하지 않습니다. 이 인스턴스에 대한 다른 주석이 매개 변수에 있습니다.|
|[C28253](../code-quality/c28253.md)|함수에 대한 주석이 일치하지 않습니다. 이 인스턴스에 대한 다른 주석이 매개 변수에 있습니다.|
|[C28254](../code-quality/c28254.md)|dynamic_cast<>()는 주석에서 지원되지 않습니다.|
|[C28262](../code-quality/c28262.md)|주석에 대한 주석 구문 오류가 함수에 있습니다.|
|[C28263](../code-quality/c28263.md)|내장 주석에 대한 조건부 주석에 구문 오류가 있습니다.|
|[C28267](../code-quality/c28267.md)|함수 주석에서 주석 구문 오류가 발견되었습니다.|
|[C28272](../code-quality/c28272.md)|함수, 매개 변수에 대한 주석이 검사 시 함수 선언과 일치하지 않습니다.|
|[C28273](../code-quality/c28273.md)|함수의 경우 단서가 함수 선언과 일치하지 않습니다.|
|[C28275](../code-quality/c28275.md)|매크로 \_\_값에\_ 대한 매개 변수는 null입니다.|
|[C28279](../code-quality/c28279.md)|기호의 경우 일치하는 'end'가 없는 'begin'이 있습니다.|
|[C28280](../code-quality/c28280.md)|기호의 경우 일치하는 'begin'이 없는 'end'가 있습니다.|
|[C28282](../code-quality/c28282.md)|형식 문자열이 사전 조건에 있어야 합니다.|
|[C28285](../code-quality/c28285.md)|함수의 경우 매개 변수에 구문 오류가 있습니다.|
|[C28286](../code-quality/c28286.md)|함수의 경우 끝 부분 근처에 구문 오류가 있습니다.|
|[C28287](../code-quality/c28287.md)|함수의 경우 \_At\_() 주석에 구문 오류(인식할 수 없는 매개 변수 이름)|
|[C28288](../code-quality/c28288.md)|함수의 경우 \_At\_() 주석에 구문 오류(잘못된 매개 변수 이름)|
|[C28289](../code-quality/c28289.md)|함수의 경우 ReadableTo 또는 WritableTo에 limit-spec가 매개 변수로 포함되지 않았습니다.|
|[C28290](../code-quality/c28290.md)|함수의 주석에 실제 매개 변수 개수보다 많은 외부 참조가 있습니다.|
|[C28291](../code-quality/c28291.md)|함수의 경우 역참조 수준 0에서 post null/notnull이 의미가 없습니다.|
|[C28300](../code-quality/c28300.md)|연산자에 호환되지 않는 형식의 식 피연산자입니다.|
|[C28301](../code-quality/c28301.md)|함수의 첫 번째 선언에 대한 주석이 없습니다.|
|[C28302](../code-quality/c28302.md)|주석에 추가 \_Deref\_ 연산자가 있습니다.|
|[C28303](../code-quality/c28303.md)|주석에 모호한 \_Deref\_ 연산자가 있습니다.|
|[C28304](../code-quality/c28304.md)|토큰에 부적절하게 배치된 \_Notref\_ 연산자가 적용되었습니다.|
|[C28305](../code-quality/c28305.md)|토큰을 구문 분석하는 동안 오류가 발생했습니다.|
|[C28306](../code-quality/c28306.md)|매개 변수의 추가는 사용되지 않습니다.|
|[C28307](../code-quality/c28307.md)|매개 변수의 추가는 사용되지 않습니다.|
|[C28350](../code-quality/c28350.md)|주석이 조건부로 적용할 수 없는 상황을 설명합니다.|
|[C28351](/cpp/code-quality/c28351)|주석이 동적 값(변수)을 조건에 사용할 수 없는 경우를 설명합니다.|
|[CA1001](../code-quality/ca1001.md)|삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.|
|[CA1009](../code-quality/ca1009.md)|이벤트 처리기를 제대로 선언하십시오.|
|[CA1016](../code-quality/ca1016.md)|AssemblyVersionAttribute로 어셈블리 표시|
|[CA1033](../code-quality/ca1033.md)|인터페이스 메서드는 자식 형식에서 호출할 수 있어야 합니다.|
|[CA1049](../code-quality/ca1049.md)|네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.|
|[CA1060](../code-quality/ca1060.md)|P/Invoke를 NativeMethods 클래스로 이동|
|[CA1061](../code-quality/ca1061.md)|기본 클래스 메서드를 숨기지 마십시오.|
|[CA1063](../code-quality/ca1063.md)|IDisposable을 올바르게 구현하십시오.|
|[CA1065](../code-quality/ca1065.md)|예기치 않은 위치에서 예외를 발생시키지 마십시오.|
|[CA1301](../code-quality/ca1301.md)|중복 액셀러레이터 키를 사용하지 마십시오.|
|[CA1400](../code-quality/ca1400.md)|P/Invoke 진입점이 있어야 합니다.|
|[CA1401](../code-quality/ca1401.md)|P/Invoke는 노출되지 않아야 합니다.|
|[CA1403](../code-quality/ca1403.md)|자동 레이아웃 형식은 COM 노출이면 안 됩니다.|
|[CA1404](../code-quality/ca1404.md)|P/Invoke 다음에 바로 GetLastError를 호출하십시오.|
|[CA1405](../code-quality/ca1405.md)|COM 노출 형식의 기본 형식은 COM 노출이어야 합니다.|
|[CA1410](../code-quality/ca1410.md)|COM 등록 메서드는 일치해야 합니다.|
|[CA1415](../code-quality/ca1415.md)|P/Invoke를 올바르게 선언하십시오.|
|[CA1821](../code-quality/ca1821.md)|빈 종료자를 제거하십시오.|
|[CA1900](../code-quality/ca1900.md)|값 형식 필드는 이식 가능해야 합니다.|
|[CA1901](../code-quality/ca1901.md)|P/Invoke 선언은 이식 가능해야 합니다.|
|[CA2002](../code-quality/ca2002.md)|약한 ID를 가진 개체를 잠그지 마십시오.|
|[CA2100](../code-quality/ca2100.md)|보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.|
|[CA2101](../code-quality/ca2101.md)|P/Invoke 문자열 인수에 대해 마샬링을 지정하십시오.|
|[CA2108](../code-quality/ca2108.md)|값 형식에서 선언적 보안을 검토하십시오.|
|[CA2111](../code-quality/ca2111.md)|포인터는 노출되면 안 됩니다.|
|[CA2112](../code-quality/ca2112.md)|보안 형식은 필드를 노출하면 안 됩니다.|
|[CA2114](../code-quality/ca2114.md)|메서드 보안은 형식의 상위 집합이어야 합니다.|
|[CA2116](../code-quality/ca2116.md)|APTCA 메서드는 APTCA 메서드만 호출해야 합니다.|
|[CA2117](../code-quality/ca2117.md)|APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.|
|[CA2122](../code-quality/ca2122.md)|링크 요청이 있는 메서드를 간접적으로 노출하지 마십시오.|
|[CA2123](../code-quality/ca2123.md)|재정의 링크 요청은 기본 링크 요청과 같아야 합니다.|
|[CA2124](../code-quality/ca2124.md)|취약한 finally 절을 외부 try에 래핑하십시오.|
|[CA2126](../code-quality/ca2126.md)|형식 링크 요청에는 상속 요청이 필요합니다.|
|[CA2131](../code-quality/ca2131.md)|보안에 중요한 형식은 형식 동등에 참여할 수 없습니다.|
|[CA2132](../code-quality/ca2132.md)|기본 생성자는 기본 형식의 기본 생성자 이상으로 중요해야 합니다.|
|[CA2133](../code-quality/ca2133.md)|대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.|
|[CA2134](../code-quality/ca2134.md)|메서드는 기본 메서드를 재정의할 때 일관된 투명도를 유지해야 합니다.|
|[CA2137](../code-quality/ca2137.md)|투명 메서드에는 확인할 수 있는 IL만 포함되어야 합니다.|
|[CA2138](../code-quality/ca2138.md)|투명 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용하여 메서드를 호출해서는 안 됩니다.|
|[CA2140](../code-quality/ca2140.md)|투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.|
|[CA2141](../code-quality/ca2141.md)|투명 메서드는 LinkDemands를 충족해서는 안 됩니다|
|[CA2146](../code-quality/ca2146.md)|형식은 기본 형식 및 인터페이스 이상으로 중요해야 합니다.|
|[CA2147](../code-quality/ca2147.md)|투명 메서드는 보안 어설션을 사용할 수 없습니다.|
|[CA2149](../code-quality/ca2149.md)|투명 메서드는 네이티브 코드를 호출해서는 안 됩니다.|
|[CA2200](../code-quality/ca2200.md)|스택 정보를 유지하도록 다시 throw하십시오.|
|[CA2202](../code-quality/ca2202.md)|개체를 여러 번 삭제하지 마십시오.|
|[CA2207](../code-quality/ca2207.md)|값 형식 정적 필드 인라인을 초기화하십시오.|
|[CA2212](../code-quality/ca2212.md)|서비스 구성 요소를 WebMethod를 사용하여 표시하지 마십시오.|
|[CA2213](../code-quality/ca2213.md)|삭제 가능한 필드는 삭제해야 합니다.|
|[CA2214](../code-quality/ca2214.md)|재정의 가능한 메서드를 생성자에서 호출하지 마십시오.|
|[CA2216](../code-quality/ca2216.md)|삭제 가능한 형식은 종료자를 선언해야 합니다.|
|[CA2220](../code-quality/ca2220.md)|종료자는 기본 클래스 종료자를 호출해야 합니다.|
|[CA2229](../code-quality/ca2229.md)|serialization 생성자를 구현하십시오.|
|[CA2231](../code-quality/ca2231.md)|ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.|
|[CA2232](../code-quality/ca2232.md)|Windows Forms 진입점을 STAThread를 사용하여 표시하십시오.|
|[CA2235](../code-quality/ca2235.md)|모두 serialize할 수 없는 필드로 표시하십시오.|
|[CA2236](../code-quality/ca2236.md)|ISerializable 형식에서 기본 클래스 메서드를 호출하십시오.|
|[CA2237](../code-quality/ca2237.md)|SerializableAttribute로 ISerializable 형식 표시|
|[CA2238](../code-quality/ca2238.md)|serialization 메서드를 올바르게 구현하십시오.|
|[CA2240](../code-quality/ca2240.md)|ISerializable을 올바르게 구현하십시오.|
|[CA2241](../code-quality/ca2241.md)|서식 지정 메서드에 올바른 인수를 제공하십시오.|
|[CA2242](../code-quality/ca2242.md)|NaN에 대해 정확하게 테스트하십시오.|
