---
title: 네이티브 권장 규칙 규칙 집합
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94fd7ba7b742c2615dc8f161c5ea156b4fd0a7f4
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600020"
---
# <a name="native-recommended-rules-rule-set"></a>네이티브 권장 규칙 규칙 집합

네이티브 권장 규칙은 잠재적 보안 허점 및 응용 프로그램 충돌을 포함 하 여 네이티브 코드의 가장 중요 한 문제 및 일반적인 문제에 중점을 둡니다. 이 규칙 집합은 [기본 최소 규칙](native-minimum-rules-rule-set.md) 규칙 집합의 모든 규칙을 포함 합니다.

네이티브 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에이 규칙 집합을 포함 합니다.

|규칙|설명|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|초기화되지 않은 메모리 사용|
|[C6011](/cpp/code-quality/c6011)|Null 포인터 역참조|
|[C6029](/cpp/code-quality/c6029)|확인되지 않은 값 사용|
|[C6031](/cpp/code-quality/c6031)|반환 값이 무시 됨|
|[C6053](/cpp/code-quality/c6053)|호출의 0 종료|
|[C6054](/cpp/code-quality/c6054)|0 종료 누락|
|[C6059](/cpp/code-quality/c6059)|잘못된 연결|
|[C6063](/cpp/code-quality/c6063)|Format 함수에 문자열 인수 없음|
|[C6064](/cpp/code-quality/c6064)|Format 함수에 정수 인수 없음|
|[C6066](/cpp/code-quality/c6066)|Format 함수에 포인터 인수 없음|
|[C6067](/cpp/code-quality/c6067)|Format 함수에 문자열 포인터 인수 없음|
|[C6101](/cpp/code-quality/c6101)|초기화되지 않은 메모리 반환|
|[C6200](/cpp/code-quality/c6200)|인덱스가 버퍼 최대값을 초과함|
|[C6201](/cpp/code-quality/c6201)|인덱스가 스택 버퍼 최대값을 초과함|
|[C6214](/cpp/code-quality/c6214)|BOOL에 대 한 잘못 된 캐스트 HRESULT|
|[C6215](/cpp/code-quality/c6215)|HRESULT에 대 한 잘못 된 캐스팅 부울|
|[C6216](/cpp/code-quality/c6216)|HRESULT에 대 한 잘못 된 컴파일러 삽입 캐스트 BOOL|
|[C6217](/cpp/code-quality/c6217)|NOT을 사용 하는 잘못 된 HRESULT 테스트|
|[C6220](/cpp/code-quality/c6220)|-1과 비교할 때 잘못 된 HRESULT입니다.|
|[C6226](/cpp/code-quality/c6226)|-1에 대 한 잘못 된 HRESULT 할당|
|[C6230](/cpp/code-quality/c6230)|부울로 잘못 된 HRESULT 사용|
|[C6235](/cpp/code-quality/c6235)|논리 Or를 사용 하는 0이 아닌 상수|
|[C6236](/cpp/code-quality/c6236)|0이 아닌 상수가 포함 된 논리합|
|[C6237](/cpp/code-quality/c6237)|0 (논리 포함) 및 부작용 손실|
|[C6242](/cpp/code-quality/c6242)|강제 로컬 해제|
|[C6248](/cpp/code-quality/c6248)|Null DACL 만들기|
|[C6250](/cpp/code-quality/c6250)|릴리스되지 않은 주소 설명자|
|[C6255](/cpp/code-quality/c6255)|Alloca의 보호 되지 않는 사용|
|[C6258](/cpp/code-quality/c6258)|스레드 종료 사용|
|[C6259](/cpp/code-quality/c6259)|비트 Or 제한 된 스위치의 비활성 코드|
|[C6260](/cpp/code-quality/c6260)|바이트 산술 사용|
|[C6262](/cpp/code-quality/c6262)|과도 한 스택 사용|
|[C6263](/cpp/code-quality/c6263)|루프에서 Alloca 사용|
|[C6268](/cpp/code-quality/c6268)|캐스트에 괄호가 없습니다.|
|[C6269](/cpp/code-quality/c6269)|포인터 역참조가 무시 되었습니다.|
|[C6270](/cpp/code-quality/c6270)|Format 함수에 부동 인수 없음|
|[C6271](/cpp/code-quality/c6271)|Format 함수의 추가 인수|
|[C6272](/cpp/code-quality/c6272)|Format 함수의 비부동 인수|
|[C6273](/cpp/code-quality/c6273)|Format 함수에 비정수 인수|
|[C6274](/cpp/code-quality/c6274)|Format 함수의 비문자 인수|
|[C6276](/cpp/code-quality/c6276)|잘못된 문자열 캐스팅|
|[C6277](/cpp/code-quality/c6277)|잘못된 CreateProcess 호출|
|[C6278](/cpp/code-quality/c6278)|배열-새 스칼라-삭제 불일치|
|[C6279](/cpp/code-quality/c6279)|스칼라-새 배열-삭제 불일치|
|[C6280](/cpp/code-quality/c6280)|메모리 할당-할당 해제 불일치|
|[C6281](/cpp/code-quality/c6281)|비트 관계 우선 순위|
|[C6282](/cpp/code-quality/c6282)|할당은 테스트를 대체 합니다.|
|[C6283](/cpp/code-quality/c6283)|기본 배열-새 스칼라-삭제 불일치|
|[C6284](/cpp/code-quality/c6284)|Format 함수의 개체 인수 잘못됨|
|[C6285](/cpp/code-quality/c6285)|상수의 논리합|
|[C6286](/cpp/code-quality/c6286)|0이 아닌 논리 또는 손실 부작용|
|[C6287](/cpp/code-quality/c6287)|중복 테스트|
|[C6288](/cpp/code-quality/c6288)|논리적 And를 통한 상호 포함이 False입니다.|
|[C6289](/cpp/code-quality/c6289)|논리합에 대 한 상호 제외가 True입니다.|
|[C6290](/cpp/code-quality/c6290)|논리 부정 비트 AND 우선 순위|
|[C6291](/cpp/code-quality/c6291)|논리 부정 비트 OR 우선 순위|
|[C6292](/cpp/code-quality/c6292)|루프가 최대값부터 위로 계산 됩니다.|
|[C6293](/cpp/code-quality/c6293)|루프가 최소값부터 아래로 계산 됩니다.|
|[C6294](/cpp/code-quality/c6294)|루프 본문이 실행 되지 않음|
|[C6295](/cpp/code-quality/c6295)|무한 루프|
|[C6296](/cpp/code-quality/c6296)|루프는 한 번만 실행 됩니다.|
|[C6297](/cpp/code-quality/c6297)|더 큰 크기로의 시프트 캐스트 결과|
|[C6299](/cpp/code-quality/c6299)|부울 비교에 대 한 비트 필드|
|[C6302](/cpp/code-quality/c6302)|Format 함수에 대한 잘못된 문자열 인수|
|[C6303](/cpp/code-quality/c6303)|Format 함수에 대한 잘못된 와이드 문자열 인수|
|[C6305](/cpp/code-quality/c6305)|크기 및 개수 사용 불일치|
|[C6306](/cpp/code-quality/c6306)|잘못된 변수 인수 함수 호출|
|[C6308](/cpp/code-quality/c6308)|Realloc 누수|
|[C6310](/cpp/code-quality/c6310)|잘못 된 예외 필터 상수|
|[C6312](/cpp/code-quality/c6312)|예외 실행 루프 계속|
|[C6314](/cpp/code-quality/c6314)|비트 or 우선 순위|
|[C6317](/cpp/code-quality/c6317)|보완 하지 않음|
|[C6318](/cpp/code-quality/c6318)|예외 검색 계속|
|[C6319](/cpp/code-quality/c6319)|쉼표로 무시 됨|
|[C6324](/cpp/code-quality/c6324)|문자열 비교 대신 문자열 복사|
|[C6328](/cpp/code-quality/c6328)|잠재적 인수 형식 불일치|
|[C6331](/cpp/code-quality/c6331)|VirtualFree 잘못 된 플래그|
|[C6332](/cpp/code-quality/c6332)|VirtualFree 매개 변수가 잘못 되었습니다.|
|[C6333](/cpp/code-quality/c6333)|VirtualFree 잘못 된 크기|
|[C6335](/cpp/code-quality/c6335)|프로세스 핸들 누수|
|[C6381](/cpp/code-quality/c6381)|종료 정보 없음|
|[C6383](/cpp/code-quality/c6383)|요소-카운트 바이트 수 버퍼 오버런|
|[C6384](/cpp/code-quality/c6384)|포인터 크기 나누기|
|[C6385](/cpp/code-quality/c6385)|읽기 오버런|
|[C6386](/cpp/code-quality/c6386)|쓰기 오버런|
|[C6387](/cpp/code-quality/c6387)|잘못된 매개 변수 값|
|[C6388](/cpp/code-quality/c6388)|잘못된 매개 변수 값|
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
|[C6995](/cpp/code-quality/c6995)|XML 로그 파일을 저장 하지 못했습니다.|
|[C26100](/cpp/code-quality/c26100)|경합 조건|
|[C26101](/cpp/code-quality/c26101)|연동 작업을 제대로 사용 하지 못함|
|[C26110](/cpp/code-quality/c26110)|호출자가 잠금 유지에 실패 했습니다.|
|[C26111](/cpp/code-quality/c26111)|호출자가 잠금 해제에 실패 했습니다.|
|[C26112](/cpp/code-quality/c26112)|호출자가 잠금을 유지할 수 없음|
|[C26115](/cpp/code-quality/c26115)|잠금 해제 실패|
|[C26116](/cpp/code-quality/c26116)|잠금 획득 또는 유지 실패|
|[C26117](/cpp/code-quality/c26117)|유지 되지 않은 잠금 해제|
|[C26140](/cpp/code-quality/c26140)|동시성 SAL 주석 오류|
|[C26441](/cpp/code-quality/C26441)|NO_UNNAMED_GUARDS|
|[C26444](/cpp/code-quality/c26444)|NO_UNNAMED_RAII_OBJECTS|
|[C26498](/cpp/code-quality/C26498)|USE_CONSTEXPR_FOR_FUNCTIONCALL|
|[C28020](/cpp/code-quality/c28020)|이 식은이 호출에서 true가 아닙니다.|
|[C28021](/cpp/code-quality/c28021)|주석이 달린 매개 변수는 포인터여야 합니다.|
|[C28022](/cpp/code-quality/c28022)|이 함수의 함수 클래스는 해당 클래스를 정의 하는 데 사용 된 typedef의 함수 클래스와 일치 하지 않습니다.|
|[C28023](/cpp/code-quality/c28023)|할당 되거나 전달 되는 함수에는 \_ \_ \_ 클래스 중 하나 이상에 대 한 함수 클래스 주석이 있어야 합니다.|
|[C28024](/cpp/code-quality/c28024)|할당 되는 함수 포인터는 함수 클래스 (es) 목록에 포함 되지 않은 함수 클래스를 사용 하 여 주석 처리 됩니다.|
|[C28039](/cpp/code-quality/c28039)|실제 매개 변수의 형식은 형식과 정확히 일치 해야 합니다.|
|[C28112](/cpp/code-quality/c28112)|연동 함수를 통해 액세스 되는 변수는 항상 연동 함수를 통해 액세스 해야 합니다.|
|[C28113](/cpp/code-quality/c28113)|연동 함수를 통해 지역 변수 액세스|
|[C28125](/cpp/code-quality/c28125)|함수는 try/except 블록 내에서 호출 해야 합니다.|
|[C28137](/cpp/code-quality/c28137)|변수 인수가 대신 (리터럴) 상수 여야 합니다.|
|[C28138](/cpp/code-quality/c28138)|대신 상수 인수는 변수 여야 합니다.|
|[C28159](/cpp/code-quality/c28159)|다른 함수를 대신 사용 하십시오.|
|[C28160](/cpp/code-quality/c28160)|오류 주석|
|[C28163](/cpp/code-quality/c28163)|함수는 try/except 블록 내에서 호출 해서는 안 됩니다.|
|[C28164](/cpp/code-quality/c28164)|인수가 포인터에 대 한 포인터가 아니라 개체에 대 한 포인터가 필요한 함수로 전달 되 고 있습니다.|
|[C28182](/cpp/code-quality/c28182)|NULL 포인터를 역참조하고 있습니다. 포인터에 다른 포인터와 동일한 NULL 값이 포함되어 있습니다.|
|[C28183](/cpp/code-quality/c28183)|인수는 한 값일 수 있으며 포인터에서 찾은 값의 복사본입니다.|
|[C28193](/cpp/code-quality/c28193)|변수는 검사 해야 하는 값을 포함 합니다.|
|[C28196](/cpp/code-quality/c28196)|요구 사항이 충족 되지 않았습니다. 식이 true로 계산 되지 않습니다.|
|[C28202](/cpp/code-quality/c28202)|비정적 멤버에 대한 잘못된 참조입니다.|
|[C28203](/cpp/code-quality/c28203)|클래스 멤버에 대한 모호한 참조입니다.|
|[C28205](/cpp/code-quality/c28205)|\_\_ \_ \_ \_ 잘못 된 컨텍스트에서 사용 되는 성공 또는 실패 시|
|[C28206](/cpp/code-quality/c28206)|왼쪽 피연산자가 구조체를 가리킵니다. '->'를 사용하세요.|
|[C28207](/cpp/code-quality/c28207)|왼쪽 피연산자가 구조체입니다. '.'를 사용하세요.|
|[C28209](/cpp/code-quality/c28209)|기호의 선언에 충돌 하는 선언이 있습니다.|
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
|[C28244](/cpp/code-quality/c28244)|함수 주석에 구문 분석할 때 매개 변수/외부 주석이 있습니다.|
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
|[C28306](/cpp/code-quality/c28306)|매개 변수에 대 한 주석이 sal|
|[C28307](/cpp/code-quality/c28307)|매개 변수에 대 한 주석이 sal|
|[C28350](/cpp/code-quality/c28350)|주석이 조건부로 적용할 수 없는 상황을 설명합니다.|
|[C28351](/cpp/code-quality/c28351)|주석이 동적 값(변수)을 조건에 사용할 수 없는 경우를 설명합니다.|