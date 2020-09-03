---
title: 애니메이션
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825361"
---
# <a name="animations-for-visual-studio"></a>Visual Studio의 애니메이션
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>애니메이션 기본 사항

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio의 애니메이션 모범 사례
 Visual Studio의 IDE에서 일관 되 고 사용자에 게 친숙 한 애니메이션 스타일을 유지 하려면 다음 규칙을 따르세요.

- **선택 해야 합니다.** 특정 목적을 제공 하는 애니메이션으로 애니메이션을 제한 합니다.

- **타이밍 및 속도는** 전환이 빠르고 자연스럽 게 작동 하는지 확인 하는 데 중요 합니다.

  - 1 초 (500 밀리초) 내에서 애니메이션 전환을 완료 합니다.

  - 자주 발생 하는 애니메이션은 사용자의 워크플로를 중단 하지 않을 만큼 신속 하 게 수행 해야 합니다.

  - 애니메이션은 이해 하기 어렵기 때문에 jarring는 안 됩니다. 즉, 한 성급를 사용 하 여 전환을 완료할 수 있는 속도는 아닙니다.

  - 변수 타이밍을 사용 하 여 중요도를 강조 합니다. 예를 들어 클래스 다이어그램에서 항목 시퀀스를 탐색 하는 경우 항목 간의 전환을 통해 속도가 저하 되 고 중요 한 항목에 초점을 맞출 수 있습니다.

- 한 상태에서 다른 상태로 **점진적 선형 감속/가속 사용**

- 가능 하면 마우스를 **가리키면 미세한 애니메이션을 사용** 하 여 마우스 아래에 대화형 요소를 표시 합니다.

- 기능에서 애니메이션을 많이 사용 하는 경우 **도구 > 옵션** 대화 상자에서 옵션으로 로컬로 (모든 기능에 대해) 해당 기능을 **해제 하는 방법을 제공** 합니다.

- 한 번 **에 하나의 애니메이션만 발생** 하 고 정보를 한 개만 전달 해야 합니다.

- **미묘한은 중요 합니다.** 대부분의 경우 애니메이션은 용도에 맞게 사용자 주의가 필요 하지 않습니다. 타이밍, 시퀀싱 및 동작의 미묘한 변화는 인식에 상당한 영향을 줄 수 있으며 효과적이 고 비효율적인 애니메이션의 차이를 내릴 수 있습니다.

- 애니메이션을 사용 하 여 특정 항목에 주목 하는 경우 사용자가 생각 하는 것을 **방해 하는 가치가 있는지 확인**해야 합니다.

- 애니메이션 **을 통해 진행률 또는 상태를 표시** 하는 경우:

  - 기본 프로세스가 진행 되지 않는 경우 진행률 이동 표시를 중지 합니다.

  - 결정 되지 않은 프로세스를 활성화 상태의 프로세스와 구분 합니다.

  - 애니메이션에 식별 가능한 완료 및 실패 상태가 있는지 확인 합니다.

  - 상태를 표시 하 고 실제 사용에 대 한 추가 정보를 제공 하 여 실제 값이 있는지 확인 하는 효과 애니메이션 사용을 최소화 합니다. 예를 들면 일시적인 상태 변경 및 emergencies 있습니다.

#### <a name="do-not"></a>수행하지 않아야 할 작업:

- 작은 움직임 (작은 공간으로 이동)을 사용 하 여 개체를 이동 하는 동안 페이드를 사용 하 고 변경 합니다.

- 화면 부동산의 큰 영역에서 발생 하는 애니메이션을 사용 합니다. 크기에 관계 없이이 애니메이션 스타일은 사용자에 게 혼란을 주는 것입니다.

- 사용자가 현재 집중 하거나 상호 작용 중인 개체와 관련이 없는 애니메이션을 사용 합니다.

- 사용자 조작이 필요한 애니메이션을 사용 하 여 사용자가 깜박임을 중지 하기 위해 깜박이는 알림에 강제로 응답 하도록 하는 등의 상태를 다시 설정 합니다. 모든 방식으로 상호 작용 하면 해당 항목을 해제할 수 있을 만큼 충분 해야 합니다.

  이러한 모범 사례에 대 한 응용 프로그램에 대 한 자세한 내용은 [애니메이션 패턴](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)을 참조 하세요.

### <a name="animation-metrics"></a>애니메이션 메트릭

- 시스템은 10 밀리초 미만으로 사용자 제스처에 반응 해야 합니다.

- 애니메이션 전환은 완료 하는 데 500 밀리초 보다 오래 걸리지 않습니다.

- 더 긴 시간이 필요한 전환을 보정 하는 한 가지 방법은이를 두 부분으로 나누는 것입니다. 예를 들어 애니메이션의 첫 번째 부분은 빈 콘텐츠 컨테이너 (최대 500 밀리초)가 될 수 있으며, 콘텐츠가 컨테이너 (최대 500 밀리초)로 감소 합니다.

- 계산 될 수 있는 로드 시간의 경우 결정 진행률 표시기 (백분율 완료 진행률 표시기)를 선호 합니다.

- 계산할 수 없는 로드 시간의 경우 커서 또는 포함 된 회전 애니메이션 (로드 또는 작업 표시기)과 같은 사용 가능한 표시기가 적절 합니다.

### <a name="animation-as-communicator"></a>Communicator로 애니메이션
 Visual Studio의 UI에서 애니메이션은 통신 도구로만 작동 합니다.  이 클래스는 UI의 구조적 변경과 같은 다양 한 정보를 전달 하는 데 사용 됩니다. 예를 들어, 메뉴가 열리거나 닫힐 때입니다. 애니메이션을 사용 하면 설치 진행률 시각화와 같은 복잡 한 시스템의 시간 종속 동작을 시각화 하거나 경고 및 알림을 사용 하는 데 사용 하는 데 도움이 될 수 있습니다.

 UI 애니메이션은 일반적으로 표시 되는 네 가지 방법, 즉 눈에 띄게 하 고, 시뮬레이션 하 고, 응답 시간/진행 상태를 표시 합니다.

#### <a name="visualize"></a>시각화
 애니메이션은 개체의 3 차원 특성을 강조 하 고 사용자가 더 쉽게 공간 구조를 시각화할 수 있게 합니다. 이를 위해 애니메이션은 개체를 전체 원으로 회전 하거나, 천천히 켜고, 개체를 가깝게 가져오고, 롤오버 또는 포커스를 강조 하기 위해 크기를 약간 늘려야 할 수 있습니다.

 3 차원 개체는 사용자 정의 컨트롤을 사용 하 여 이동할 수 있지만, 디자이너는 개체에 대 한 최적의 이해를 제공 하는 이동에 가장 적합 한 방식으로 미리 결정 해야 합니다. 그러면 사용자가 커서를 개체 위에 배치 하 여이 프로그래밍 애니메이션을 활성화할 수 있습니다. 반면 사용자가 제어 하는 움직임을 사용 하려면 사용자가 개체를 조작 하는 방법을 이해 해야 합니다. 한 번에 하나의 축 또는 방향으로 이동을 제한 합니다. 크기 조정, 회전 또는 변환 중 하나를 동시에 수행 하지는 않습니다.

 시각화 범주에는 데이터, 관계, 상태, 구조, 시퀀스 및 시간의 측면이 포함 됩니다.

##### <a name="data"></a>데이터
 복합 및 변수 정보를 보여 줍니다.

- 차트 및 그래프와 같은 정보 시각화를 통해 이동

- 시퀀스, 둘러보기 및 페이징을 단계별로 실행

- 세부 정보를 호출 하 고 특정 정보를 가리키고 강조 표시

- 포커스가 있는 요소 위에 세부 정보 및 추가 정보 오버레이

- 구조 또는 조직 표현 간에 모핑

- 시간 슬라이더, 조그 및 셔틀 바퀴, 전송 컨트롤 (재생, 중지 및 일시 중지)을 사용 하 여 시간에 따른 변경 내용을 표시 합니다.

##### <a name="relationships"></a>관계

- 항목이 서로 관련 되는 방법 또는 지정 된 항목과 관련 된 항목을 보여 줍니다.

- 계층 및 부모-자식 또는 형제 관계 표시

- 한 요소가 다른 요소를 생성 합니다.

- 한 요소가 다른 요소를 최소화 합니다.

- 한 요소가 다른 요소에 테더 링 된

##### <a name="state"></a>시스템 상태

- 콘텐츠 업데이트.

- 사용자 포커스 및 선택

- 진행률

- 오류

##### <a name="structure"></a>구조체

- 한 노드에서 구조 피벗

- Reorienting

- 최소화 및 최대화 또는 확장/축소

##### <a name="sequence"></a>순서

- 슬라이드 쇼 시퀀스

- 그림에서 대칭 이동

##### <a name="time"></a>시간

- 시간 경과, 시간 경과 및 동영상 가이드 변경 내용 표시

- 휴지통으로 이동, 실행 취소 및 다시 실행

- 기록 상태 복원

#### <a name="attract-attention"></a>관심 있는 관심
 사용자의 단일 요소에 대 한 사용자의 주의가 나 사용자에 게 업데이트 된 정보를 알려 주는 것이 목표 인 경우 애니메이션은 적합할 수 있습니다. 예를 들어 응용 프로그램 시작 페이지에서 페이지가 로드 된 후 슬라이드를 시작 하는 시작 단추를 사용할 수 있습니다.

 규칙으로 화면의 마지막 이동 요소는 사용자의 주의를 attracts 합니다.  애니메이션이 적용 된 일련의 요소에서 사용자의 주의가 마지막으로 이동 하는 개체를 따릅니다.

##### <a name="alert"></a>경고

- 사용자에 게 경고, 주의가 필요 하 고 진행률 표시

- 제대로 수행 되 고 있는지 또는 잘못 된 것으로 표시 하거나 진행률 또는 진행률 변경을 표시 합니다.

- 온라인으로 추가 정보 찾기 또는 현재 작업에 대 한 학습 등의 작업을 수행 하는 동안 사용자에 게 확인

##### <a name="notifications"></a>공지

- 오류 조건에 대해 사용자에 게 경고

- 사용자가 다른 항목에 참석 하는지 확인 하려면 사용자를 중단 하세요.

- 다운로드가 완료 된 경우와 같이 프로세스가 완료 또는 변경 되었음을 사용자에 게 조심 스럽게 알립니다.

#### <a name="simulate"></a>Simulate
 이 범주는 physicality 및 차원에 적용 됩니다.

- 개체의 위치 또는 이동 위치를 보여 줍니다.

- 확장 및 축소 또는 열기 및 닫기

- 패닝, 스크롤 및 페이지 회전

- 스택 및 z 순서 지정

- 회전식 및 아코디언

- 대칭 이동 및 회전 UI

#### <a name="response-and-progress-indicators"></a>응답 및 진행률 표시기
 진행률 표시기에는 몇 가지 주목할 만한 이점이 있습니다.

- 활성화 상태의 및 확정 되지 않은 진행률 표시기는 모두 시스템이 충돌 하지 않고 문제에 대해 작동 하 고 있음을 사용자에 게 reassure 합니다.

- 활성화 상태의 지표는 사용자에 게 작업의 진행 상황에 대 한 이해를 제공 하 고, 완료에 더 가까운 느낌을 제공 합니다.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> 애니메이션 패턴

### <a name="overview"></a>개요
 Visual Studio의 애니메이션은 특정 기능을 제공 하 고 사용자의 생산성을 저하 시 지 않습니다. 다음을 준수 하는 일반적인 애니메이션 특징:

- 작고 조심 스럽게

- 자연적인 및 현실적인

- 미묘한 및 subdued

- 빠르고 효율적

- 완화 hurried

  다음 그림에서는 Visual Studio에서 사용 하기 위해 권장 되는 애니메이션 스타일을 보여 줍니다. 페이드 인/페이드 아웃 같은 애니메이션 및 미묘한 애니메이션은 가장 자주 사용 되지 않습니다. 확장 및 계약, X 및 Y 위치 변경, 회전과 같은 이동 애니메이션의 제한 된 응용 프로그램이 있습니다.

  ![Visual Studio에 권장되는 애니메이션 스타일](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202-a_VSAnimStyles")

  **Visual Studio에 권장되는 애니메이션 스타일**

#### <a name="appear-and-disappear"></a>표시 되 고 사라집니다.
 이 패턴을 사용 하는 경우 요소는 전환 애니메이션 없이 볼 수 없는 상태로 전환 됩니다.

 ![Visual Studio에서&#47;사라지는 애니메이션 표시](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202-b_AppearAndDisappear")

##### <a name="correct-usage"></a>올바른 사용법
 사용자가 무시 하거나 방해 하지 않도록 즉시 표시 하거나 사라지게 되는 새로운 UI 요소입니다. 또한 천천히 이동 하는 애니메이션은 성능 끌기로 인식 될 수 있으며이는 표시 되 고 사라진 스타일로 발생 하지 않습니다.

##### <a name="incorrect-usage"></a>잘못 된 사용
 UI가 갑자기 표시 되는 경우 사용자는 발생 한 상황을 알 수 없으며 애니메이션을 추가 하면 컨텍스트를 이해 하는 데 도움이 됩니다.

##### <a name="animation-properties"></a>애니메이션 속성
 시간 지연은 일반적으로 0 초입니다.

##### <a name="examples"></a>예제

- 도구 창 자동 숨기기

- IntelliSense 및 매개 변수 도움말과 같은 키보드 활성화 된 편집기 UI

- 코드 영역 확장/축소

#### <a name="fade-in-and-fade-out"></a>페이드 인 및 페이드 아웃
 이 패턴을 사용 하면 UI 요소가 표시 되지 않음 (0% 불투명도)에서 표시 (100% 불투명도)로 또는 그 반대로 전환 됩니다.

 ![Visual Studio에서 페이드&#45;&#47;페이드&#45;](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202-c_FadeInFadeOut")

##### <a name="correct-usage"></a>올바른 사용법
 가장 일반적으로 권장 되는 UI 애니메이션입니다. 흐름을 중단 하지 않고 관심을 추가 하는 미묘한 효과입니다. 경우에 따라 사용자는 애니메이션이 있음을 인식 하지 못할 수 있으며 부드러운 흐름 UI 시스템을 전달 합니다.

##### <a name="animation-properties"></a>애니메이션 속성

- 시작 불투명도: 페이드 인의 경우 0%, 페이드 아웃의 경우 100%

- 종료 불투명도: 페이드 인의 경우 100%, 페이드 아웃의 경우 0%

- 기간: 200 밀리초 독립 실행형, 100 밀리초를 조합 애니메이션 시퀀스의 일부로 사용 하는 경우

- 감속/가속 스타일: 사인 InOut

##### <a name="examples"></a>예제

- 도구 창 자동 숨기기

- 메뉴 열기 및 닫기

- 배경 및 전경 탭 전환

#### <a name="color-blend-from-a-to-b"></a>A에서 B로 색 혼합
 이 패턴을 사용 하 여 UI 요소는 색 A에서 색 B로 변경 됩니다.

 ![Visual Studio에서 색 혼합 애니메이션](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202-d_ColorBlend")

##### <a name="correct-usage"></a>올바른 사용법
 UI 요소가 한 컨텍스트 또는 상태에서 다른 컨텍스트로 색을 변경할 때 애니메이션 전환으로 사용할 수 있습니다.

##### <a name="animation-properties"></a>애니메이션 속성

- 시작 색: UI 관련

- 끝 색: UI 관련

- 기간: 200 밀리초 독립 실행형, 100 밀리초를 조합 애니메이션 시퀀스의 일부로 사용 하는 경우

- 감속/가속 스타일: 사인 InOut

##### <a name="examples"></a>예제

- 문서 창 상태 전환 (활성, 마지막 활성 및 비활성)

- 도구 창 상태 전환 (포커스가 있고 포커스가 없는)

#### <a name="expand-and-contract"></a>확장 및 축소
 이 패턴을 사용 하면 UI 요소가 X, Y 또는 양방향으로 확장 됩니다.

 ![Visual Studio에서&#47;계약 애니메이션 확장](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202-e_ExpandContract")

##### <a name="correct-usage"></a>올바른 사용법
 UI 요소의 크기를 한 컨텍스트에서 다른 컨텍스트로 변경할 때 애니메이션 전환으로 사용할 수 있습니다.

##### <a name="animation-properties"></a>애니메이션 속성

- X scale:% 또는 특정 차원 (픽셀)

- Y scale:% 또는 특정 차원 (픽셀)

- 앵커 위치: 일반적으로 왼쪽 위 (왼쪽에서 오른쪽 언어의 경우) 또는 오른쪽 위 (오른쪽에서 왼쪽으로 쓰기 언어의 경우)

- 기간: 200 밀리초 독립 실행형, 100 밀리초를 조합 애니메이션 시퀀스의 일부로 사용 하는 경우

##### <a name="examples"></a>예제

- 아키텍처 탐색기 패널 확장 및 축소

- 시작 페이지 항목 확장 및 축소

#### <a name="x-y-position-change"></a>X Y 위치 변경
 이 패턴을 사용 하 여 UI 요소는 X 또는 Y 위치를 변경 하거나 두 가지를 모두 수행 합니다.

 ![X&#47;Y 위치 변경 애니메이션 (Visual Studio)](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202-f_XYPositionChange")

##### <a name="correct-usage"></a>올바른 사용법
 UI 요소가 한 컨텍스트에서 다른 컨텍스트로의 위치를 변경할 때 애니메이션 전환으로 사용할 수 있습니다.

##### <a name="animation-properties"></a>애니메이션 속성

- 시작 X 및 Y 위치: UI 관련

- 끝 X 및 Y 위치: UI 관련

- 동작 경로: 없음

- 기간: 200 밀리초 독립 실행형, 100 밀리초를 조합 애니메이션 시퀀스의 일부로 사용 하는 경우

- 감속/가속 스타일: 사인 InOut

##### <a name="example"></a>예
 탭 다시 정렬

#### <a name="rotate"></a>회전
 이 패턴을 사용 하면 UI 요소가 다음과 같이 회전 합니다.

 ![Visual Studio에서 회전 애니메이션](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202-g_Rotate")

##### <a name="correct-usage"></a>올바른 사용법
 결정 되지 않은 회전 진행률 표시기에만 해당 합니다.

##### <a name="animation-properties"></a>애니메이션 속성

- 회전 수준: 360

- 회전 중심: 개체의 중간

- 기간: 연속

##### <a name="example"></a>예
 확정 되지 않은 진행률 표시기 (회전)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>일반적인 셸 UI 작업 및 권장 되는 애니메이션

#### <a name="tab-open"></a>탭 열기

- 스타일: 표시

- 기간: 0 초

  ![Visual Studio에서 탭 열기 애니메이션](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202-h_TabOpen")

#### <a name="tab-close"></a>탭 닫기

- 스타일: X 위치 변경

- 기간: 200 밀리초

  ![Visual Studio에서 탭 닫기 애니메이션](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202-i_TabClose")

#### <a name="tab-reorder"></a>탭 순서 바꾸기

- 스타일: X 위치 변경

- 기간: 200 밀리초

  ![Visual Studio에서 탭 순서 바꾸기 애니메이션](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202-j_TabReorder")

#### <a name="close-floating-document"></a>부동 문서 닫기

- 스타일: 표시

- 기간: 200 밀리초

  ![Visual Studio에서 부동 문서 닫기 애니메이션](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202-k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>창 상태 전환

- 스타일: 다른 창과 일치 하려면 현재 운영 체제에서 문서 닫기 애니메이션을 정의 하도록 합니다.

- 기간: 200 밀리초

  ![Visual Studio에서 창 상태 전환 애니메이션](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202-l_WindowStateTransition")

#### <a name="menu-open"></a>메뉴 열기

- 스타일: 페이드 인

- 기간: 200 밀리초

  ![Visual Studio에서 메뉴 열기 애니메이션](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202-m_MenuOpen")

#### <a name="menu-close"></a>메뉴 닫기

- 스타일: 페이드 아웃

- 기간: 200 밀리초

  ![Visual Studio에서 메뉴 닫기 애니메이션](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202-n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>자동 숨기기 도구 창 표시

- 스타일: 표시

- 기간: 0 초

  ![Visual Studio에서 도구 창 애니메이션 자동&#45;숨기기](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")
