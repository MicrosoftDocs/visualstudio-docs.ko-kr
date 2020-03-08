---
title: Visual Studio에 대 한 UI 텍스트 및 도움말 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0477a0e1994e9c3b94df13ace4c1f3b4df51039
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409115"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Visual Studio에 대 한 UI 텍스트 및 도움말
## <a name="BKMK_UITextAndTerminology"></a>UI 텍스트 및 용어
 이해도 text는 효과적인 UI에 중요 합니다. 소프트웨어 사용자는 먼저 레이블을 읽는 것이 가장 중요 합니다. 즉, 작업을 완료 하는 데 가장 적합 합니다. 정적 텍스트는 빈도를 줄여 읽습니다. 사용자가 전체 창의 빠른 검색을 수행 하 여 작업 세션을 시작 하도록 계획 하 고 그 다음에는 다음과 같은 대략적인 순서로 UI를 읽습니다.

1. 중앙의 대화형 컨트롤

2. 커밋 단추

3. 다른 곳에서 발견 되는 대화형 컨트롤

4. 기본 지침

5. 추가 설명

6. 창 제목

7. 본문의 다른 정적 텍스트

### <a name="usage-patterns-for-ui-text"></a>UI 텍스트에 대 한 사용 패턴

#### <a name="title-bar-text"></a>제목 표시줄 텍스트
 제목 표시줄 텍스트는 UI를 생성 한 명령과 일치 해야 합니다.

#### <a name="instructional-text-helper-text"></a>지침 텍스트 (도우미 텍스트)
 일부 대화 상자에서는 창이 나 페이지에서 수행할 작업을 설명 하는 중요 한 기본 지침을 제공 하는 것이 유용 합니다. 이를 "도우미 텍스트" 라고도 합니다.

##### <a name="writing-style-rules-for-helper-text"></a>도우미 텍스트에 대 한 스타일 규칙 작성

- 명확 하 게 설명 하지 않습니다. 반드시 필요한 경우가 아니면 지침 텍스트를 포함 하지 않습니다.

- 지침 텍스트는 항상 대화 상자의 맨 위에 배치 되며 수행 중인 작업을 참조 해야 합니다.

- 사용자에 게 수행 해야 하는 작업을 정확 하 게 설명 합니다. 과도 한 통신 및 중복성을 방지 합니다.

- 각 창을 검토 하 고 중복 된 단어와 문을 제거 합니다.

- 지침 텍스트를 짧게 유지 합니다. 특정 사용자나 시나리오에 대 한 자세한 정보가 필요한 경우 자세한 개념 온라인 항목에 대 한 링크를 제공 합니다.

- 모든 단어가 가중치를 포함 하 고 필요 하도록 텍스트를 작성 합니다.

- [사용자 인터페이스 텍스트](/windows/desktop/uxguide/text-ui) 와 [스타일 및 톤](/windows/desktop/uxguide/text-style-tone)에 대 한 기존 Microsoft 지침을 따릅니다.

#### <a name="supplemental-instructions"></a>추가 지침
 추가 지침은 사용자가 컨트롤 또는 컨트롤 그룹화를 이해 하는 데 도움이 되는 추가 정보를 제공 합니다. 여기에는 입력 컨트롤의 예상 형식을 이해 하는 데 필요한 힌트 텍스트가 포함 될 수도 있습니다. 추가 지침을 사용 하는 경우에만 사용 합니다. 사용자가 선택한 항목의 결과를 완전히 이해 하지 못할 가능성이 있는 경우에 대비 합니다.

 ![Visual Studio의 추가 텍스트](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Visual Studio의 추가 텍스트**

 ![Visual Studio의 추가 텍스트](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Visual Studio의 추가 텍스트**

#### <a name="infotips"></a>InfoTips
 종종 지침 텍스트가 너무 짧기 때문에 UI에서 배치 하지 못할 수도 있고 숙련 된 사용자에 게 혼란 처럼 새로운 사용자 에게만 유용할 수도 있습니다. 이 경우 지침/정보 텍스트는 정보 팁 아래에 도구 설명으로 배치 되어야 합니다.

 InfoTips은 관련 된 컨트롤 근처에 배치 해야 하며, 특정 정보 팁 아이콘을 사용 해야 합니다 .이는 눈에 띄지 않습니다.

 ![Visual Studio의 정보 팁](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio의 정보 팁 예제**

##### <a name="writing-style-rules-for-infotips"></a>InfoTips에 대 한 스타일 규칙 작성

- InfoTips을 완전 한 문장으로 작성 합니다. 특정 동사, 문장의 대/소문자 및 끝 문장 부호를 요구 합니다.

- InfoTips을 사용 하 여 주요 지침이 나 정보를 보충 합니다. 다른 단어를 사용 하 여 주요 아이디어를 다시 말하지만 하는 경우 정보 팁이 필요 하지 않습니다.

- InfoTips을 짧고 간단 하 게 유지 합니다. 사용자를 지원 하 고 권장 하는 작은 단어 및 일반 일상 언어를 사용 합니다.

- [사용자 인터페이스 텍스트](/windows/desktop/uxguide/text-ui) 와 [스타일 및 톤](/windows/desktop/uxguide/text-style-tone)에 대 한 기존 Microsoft 지침을 따릅니다.

#### <a name="control-labels"></a>컨트롤 레이블
 컨트롤 레이블은 짧고 간결 하 고 [컨트롤에 대 한 Windows 바탕 화면 지침](/windows/desktop/uxguide/controls)을 따라야 합니다.

 UI 내의 컨트롤 레이블 형식 및 배치에 대 한 자세한 내용은 [Visual Studio의 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md)을 참조 하세요.

#### <a name="help-links"></a>도움말 링크
 도움말 링크는 지침 텍스트 내에 배치 하거나 UI 본문에 배치할 수 있습니다. 도움말에 대 한 링크 이거나 내부 대화 상자를 시작할 수 있습니다.

##### <a name="visual-style-rules-for-help-links"></a>도움말 링크에 대 한 비주얼 스타일 규칙

- 하이퍼링크에 올바른 환경 색을 사용 합니다. 클릭 하면 제대로 스타일이 지정 된 하이퍼링크가 빨간색으로 깜박이지 않습니다. 이 메시지가 표시 되 면 환경 색이 사용 되지 않음을 나타냅니다.

- 밑줄은 마우스로 또는 링크가 단락에 포함 된 경우에만 사용 해야 합니다.

- 하이퍼링크의 시각적 개체와 상호 작용 스타일에 대 한 자세한 내용은 단추 및 하이퍼링크를 참조 하십시오.

##### <a name="writing-style-rules-for-help-links"></a>도움말 링크에 대 한 스타일 규칙 작성

- 대화를 시작할 때 줄임표에 대 한 표준 (탐색에는 줄임표 없음)을 유지 하 고, 작업에 추가 UI가 필요한 경우 줄임표를 유지 합니다.

     ![Visual Studio의 도움말 링크](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **도움말 링크의 줄임표 (...)는 작업에 추가 UI가 필요 함을 나타냅니다.**

- 사용자의 의도가 아니므로 링크를 "학습"으로 시작 하면 안 됩니다. 사용자가 일반적인 교육을 받지 않고 특정 질문에 답변 하려고 합니다.

- 항목에서 대답할 질문을 묻는 문구 도움말 링크

     잘못 됨: "Windows Azure Mobile Services 가격 책정에 대 한 자세한 정보"

     해결 방법: "Windows Azure Mobile Services에서 사용할 수 있는 가격 옵션은 무엇 인가요?"

- 링크 텍스트에는 *클릭* ...을 사용 하지 마십시오.

- "여기" 라는 단어만 링크 하지 마십시오. 이는 하이퍼링크 된 단어만 음성으로 연결 되는 일부 화면 판독기의 경우 문제가 됩니다.

     잘못 됨: " **여기**에서 Windows Azure Mobile Services 정보 찾기"

     해결 방법: "Windows Azure Mobile Services에서 사용할 수 있는 가격 옵션은 무엇 인가요?"

- 도움말 링크에 대 한 올바른 작성 스타일에 대 한 자세한 내용은 [Windows 바탕 화면 설명서](/windows/desktop/uxguide/winenv-help)를 참조 하십시오.

#### <a name="hint-text"></a>힌트 텍스트
 힌트 텍스트는 컨트롤이 나 컨트롤 아래에 워터 마크로 나타납니다. 올바른 형식이 `Environment.GrayText`적절 한 VSColors 토큰을 사용 하 여 적용 됩니다.

 다양 한 형식으로 표시 될 수 있습니다.

- 컨트롤 레이블 대신:

     ![Visual Studio의 힌트 텍스트](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- 동사를 사용 하 여 명령을 제공 합니다.

     ![Visual Studio의 힌트 텍스트](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- 필요한 항목을 나타내는 텍스트 포함:

     ![Visual Studio의 힌트 텍스트](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>워터 마크 텍스트
 빈 디자인 화면에서 텍스트는 수행할 작업을 나타내고, 해당 하는 경우 다른 관련 창에 대 한 링크를 제공 해야 합니다.

 ![Visual Studio의 워터 마크 텍스트](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Visual Studio의 워터 마크 텍스트 예제**

### <a name="common-terminology"></a>일반적인 용어

|용어|설명|주석|
|----------|-----------------|-------------|
|로그인/로그 아웃|웹 속성에 대 한 인증을 나타내기 위해 웹에서 동의어 처럼 자주 사용 하는 동사입니다. 클라이언트 내에서이를 한 번 사용 하 여 다른 모든 연결에서 사용할 수 없는 로밍 및 라이선스와 같은 더 높은 수준의 기능을 제공 하는 최상위 id를 제공 하는 IDE 사용자 연결의 로그인 및 로그 아웃에 대 한 최상위 개념으로 사용 합니다.|IDE 사용자는 최상위 IDE 사용자를 나타내므로 로그인/로그 아웃 동사를 나타내야 하는 유일한 기능입니다.|
|연결/연결 끊기|기능이 온라인 서비스에 대 한 단일 연결을 유지 하는 위치에서 사용 합니다.|한 번에 하나의 활성 Azure 연결만 가질 수 있는 서버 탐색기 연결/연결 끊기의 예입니다.|
|추가/제거|비 소거식. 목록에서 항목을 추가 하거나 제거 하는 경우에 사용 합니다.|TFS 연결 관리자 서버 목록 대화 상자는 추가/제거의 예입니다.|
|DELETE|파괴적인. 제거 되는 요소가 디스크에서 영구적으로 삭제 되거나 삭제 될 때만를 사용 합니다.|일반적으로 "삭제"는 결과가 디스크에서 파일을 삭제 하는 경우 프롬프트가 필요 합니다.|

## <a name="error-messages"></a>오류 메시지

### <a name="overview"></a>개요
 오류가 발생 합니다. 사용자가 수행할 수 있는 작업에 대 한 제한을 설정 하는 것은 갖추고 오류 메시지를 방지 하는 첫 번째 단계입니다. 그러나 오류가 발생 하면 잘 작성 된 오류 메시지가 문제를 완화 하는 데 오랜 시간이 걸릴 수 있습니다. 오류 메시지는 동기식 이며 해결 해야 하는 문제를 나타내기 때문에 사용자에 게 표시 되는 가장 중요 한 유형의 알림 중 하나입니다. 잘못 작성 된 오류 메시지는 사용자를 그대로 유지 하 여 오류 및 가능한 해결 방법의 원인을 결정 합니다.

 사용자가 남용 또는 혼란 스러운 오류 메시지에 대 한 부담을 중지할 수 있으므로 사용자 환경에 값을 추가 하는 데 필요한 메시지만 작성 합니다. 메시지가 단순히 알림 인 경우에는 대체 프레젠테이션을 사용 합니다.

### <a name="rules-for-creating-an-error-message"></a>오류 메시지를 만들기 위한 규칙

- 오류 메시지를 생성할 때는 대상 그룹에 대 한 적절 한 오류 수준을 선택 합니다. 해당 하는 경우 사용자가 수행할 수 있는 작업을 제공 하는 간단한 요약을 목표로 합니다. 사용자가 알지 못하는 것은 아닙니다.

- 건설적인 지원을 제공 합니다. 명령이 포함 된 오류 메시지를 읽고 작업을 수행 하는 것이 더 쉽습니다.

- 이중 부정을 사용 하지 마세요.

- 작성 한 오류 메시지에 대해 자동화 된 문법 및 수동 문법 및 맞춤법 검사를 모두 수행 합니다.

- 복잡 한 오류 메시지의 경우 순차적 통신을 피합니다. 오류 메시지에는 F1 후크를 사용 하지 마십시오. 메시지 자체에 충분 한 권한이 있어야 합니다.

- 올바른 아이콘을 사용 합니다.

- "삭제" 및 "취소"와 같이 명확 하 게 선택할 수 있는 단추를 쉽게 이해 하 고 사용할 수 있습니다.

- 경고의 경우 진행 상황을 명확 하 게 확인 해야 합니다. 단추가 결과를 나타내야 합니다.

- 오류에 대해 사용자가 문제를 해결 하기 위해 수행할 수 있는 작업을 설명 합니다. 단추는 동작 이거나 "닫기" 여야 합니다. 오류 메시지에는 "확인" 단추를 사용 하지 마세요.

- 오류 메시지를 생성할 때 사용자에 게 다음과 같은 질문을 합니다.

  - 사용자가이 오류 만으로 문제를 해결 하는 방법을 파악할 수 있나요?

  - 사용자가이 오류와 동일한 어휘를 사용 하나요?

  - 이 오류는 여러 상황에서 모호 또는 공유 되나요? 그렇다면 사용자에 게 필요한 솔루션을 안내 하는 방법은 무엇입니까?

#### <a name="build-errors"></a>빌드 오류
 Visual Studio는 소프트웨어 개발 도구 이므로 대부분의 구성 요소에는 개발자의 작업을 이진 형식으로 변환 하는 컴파일, 변환 또는 인코딩 단계가 있습니다. 컴파일러에서 잘못 작성 된 파일을 처리할 수 없거나 컴파일러 옵션이 올바르게 설정 되지 않은 경우 이러한 변환으로 인해 오류가 발생할 수 있습니다.

 Visual Studio 사용자는 빌드 오류를 해결 하는 데 상당한 수의 개발 시간을 소비할 수 있습니다. 이 해결 시간은 오류에 종속성이 있을 때 또는 오류 메시지가 잘못 기록 된 경우에 따라 달라 지 며 오류의 원인을 확인 하기 어려울 수 있습니다.

 가장 좋은 빌드 오류는 처음에 발생 하지 않는 것으로, Visual Studio에서 자동 완성 및 IntelliSense 물결선을 제공 하는 이유입니다. 스키마 유효성 검사기와 유사한 도구는 동일한 종류의 피드백을 제공 합니다. 이러한 메커니즘은 사용자에 게 잘 구성 된 코드를 생성 하 여 빌드 오류가 발생 하는 감소을 사전에 안내 합니다.

 Visual Studio는 사용자가 문서 창에서 발생 한 오류를 읽고 탐색할 수 있는 도구 창을 제공 합니다. 사용자가 많은 양의 코드를 빠르게 탐색 하 고 문제의 위치로 바로 이동할 수 있도록 하는 바로 가기 키가 제공 됩니다. 또한 Visual Studio에서는 각 빌드 오류를 특정 도움말 키워드/컨텍스트 ID에 연결 하 여 사용자가 오류에 대 한 자세한 정보를 제공 하는 도움말 항목으로 직접 이동할 수 있도록 합니다.

 명확 하 고 간결한 빌드 오류를 작성 합니다.

- 컴파일러 전문 용어를 거의 또는 전혀 사용 하지 않는 문제를 설명 하는 **일반 언어를 사용** 합니다. 빌드 오류의 텍스트는 지나치게 기술 해서는 안 됩니다.

- **가능한 원인을 간략하게 설명 합니다.** 예를 들어, ' (속성): (값) ' 선언에서 속성과 값 사이에 콜론이 없습니다. "

- 잠재적 수정 사항에 대 한 세부 정보를 제공 합니다. 공간이 충분 하지 않으면 해당 도움말 항목에 추가 세부 정보를 추가할 수 있습니다.

### <a name="components-of-a-well-written-error-message"></a>잘 작성 된 오류 메시지의 구성 요소

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>오류 메시지에는 shell 대화 상자 서비스를 사용 합니다.
 셸 대화 상자 서비스를 사용 하면 개별 요소를 크게 변경 하지 않고 메시지의 모양, 특히 글꼴을 제어할 수 있습니다. **IErrorInfo** 메커니즘을 사용 하 고 **IVsUIShell:: Seterrorinfo/ReportErrorInfo**를 사용 하 여 보고 합니다.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>효과적이 고 적절 한 알림 프레젠테이션을 선택 합니다.
 데이터의 손실을 방지 하기 위해 즉각적인 조치가 필요한 경우에는 중요 한 경고가 있는 모달 대화 상자를 사용 합니다 (동기 알림). 중요 아이콘은 메시지를 읽지 않고 닫으면 부정적인 결과가 발생할 수 있는 상황에 대해 예약 됩니다. 데이터 손실은 경보 수준 응답이 필요한 중요 한 상황입니다. 중요 아이콘의 과도 한 desensitizes 사용자에 게 중요도를 부여 합니다. 오류 메시지의 정보를 제공 하는 경우 모달 대화 상자의 대안 (비동기 알림)을 고려 하십시오.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>기술 설명이 아닌 문제가 발생 한 이유를 명확 하 고 간결 하 게 설명 합니다.
 설명에서 기술 세부 정보를 사용 하 여 사용자에 게 오류 메시지를 무시할 가능성이 느끼지 됩니다. 좋은 메시징의 예는 다음과 같습니다.

- "요청 된 파일을 열 수 없습니다."

- "인터넷에 연결할 수 없습니다."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>문제를 해결 하는 방법에 대 한 정보를 제공 합니다.
 문제를 해결 하는 방법에 대 한 사용자 의견을 제공 합니다. 제안이 없는 경우 사용자에 게이를 사용 합니다. 기술 지원 또는 커뮤니티 지원과 같은 대체 온라인 소스에 대 한 직접 링크를 제공 합니다. 사용자가 문제와 관련 된 특정 온라인 정보를 가리키도록 합니다. 오류 ID의 경우 특정 오류에 대 한 토론 스레드에 사용자를 연결 하는 것이 좋습니다. 좋은 메시징의 예는 다음과 같습니다.

- "인터넷에 연결 되어 있는지 확인 하 고이 작업을 다시 시도 하십시오."

- "파일을 열 수 있는 권한이 있는지 확인 하십시오." 라는 메시지가 표시 됩니다.

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>짧고 지점에 메시지를 작성 합니다.
 오류 메시지는 솔루션을 알리고, 설명 하 고, 제공할 수 있지만, 너무 많은 경우에는 무시 해도 됩니다. 한 가지 해결 방법은 세부 정보 단추를 사용 하 여 점진적 공개를 사용 하는 것입니다. 예를 들어 간단한 설명/솔루션을 지정한 다음 자세히 단추를 클릭 하 여 세부 정보를 추가 합니다. 사용자가 오류에 대 한 자세한 정보를 읽도록 선택 하는 경우이 작업을 수행할 수 있습니다.

 메시지의 언어는 다음과 같아야 합니다.

- **도메인에 해당 합니다.** 사용자가 이해할 수 있는 언어를 사용 합니다. 고객이 개발자 인 경우에도 현재 보유 하 고 있는 컨텍스트와 용어는 없는 경우가 많습니다.

- **컴퓨터별.** 모호한 표현을 방지 하 고 관련 개체의 특정 이름 및 위치를 제공 합니다. 예를 들어 "문자가 올바르지 않습니다."와 같은 오류 메시지는 유용 하지 않습니다. 어떤 문자 입니까? "파일을 찾을 수 없습니다." 어떤 파일이 있나요?

- **Courteous.** 사용자를 원인 하거나 바보로 설정 하지 마세요. 악의적인 또는 비속어 (kill, execute, terminate, 치명적, 잘못 된 언어)를 사용 하지 마세요. 대문자 텍스트를 사용 하지 않습니다 .이 텍스트는 shouting으로 표시 되 고 읽을 수는 없습니다. 유머를 사용 하지 마세요.

- **맞는.** 올바른 철자와 문법을 사용 합니다 (alphas 에서도). 오타가 전문적 및 당혹입니다.

- **컨텍스트 적절 합니다.** 적절 한 단추 텍스트를 사용 합니다. "확인" 단추를 사용 하지 않고 대신 "Continue" 또는 "Yes/No"를 사용 합니다.

### <a name="error-message-examples"></a>오류 메시지 예

|좋음|불량|
|----------|---------|
|"귀하의 전화 번호는 더 이상 서비스에 없습니다. 번호를 확인 한 후 다시 전화 거 나 운영자에 대해 0으로 전화를 걸기 하세요. "|-"오류 (449): 잘못 된 숫자"<br />-"이 처리 되지 않은 예외 오류는 작업이 성공적으로 완료 되었음을 나타냅니다."<br /><br /> ![Visual Studio의 잘못 된 오류 메시지](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>도움말 액세스

### <a name="overview"></a>개요
 MSDN의 설명서 외에도 Visual Studio 사용자는 UI에서 사용자를 지 원하는 여러 액세스 지점이 있습니다. 이러한 액세스 지점이 일관 되 게 사용 가능 하도록 하기 위해 기능 팀은 환경에서 제공 하는 도움말 시스템을 활용 해야 합니다. 이러한 액세스 지점은 다음과 같습니다.

- **대화 상자의 지침 및 보완 텍스트입니다.** UI 화면에서 방향이 나 설명을 제공 하거나 정보 팁 아이콘 위에 마우스를 놓았을 때 사용할 수 있는 정적 텍스트입니다.

- **F1 도움말** (편집기에만 해당). Visual Studio 편집기 내에서 사용자는 언제 든 지이를 신뢰할 수 있으며, F1 키를 누르면 현재 선택 영역과 관련 된 도움말 항목이 표시 됩니다. F1과 관련 된 항목이 적절 하 고 정보를 제공 하는지 확인 합니다.

- **도움말 항목에 대 한 하이퍼링크입니다.** 사용자가 기술, 기능 또는 작업을 수행 하는 방법에 대 한 정보를 자세히 학습할 수 있도록 돕는 항목을 시작 하는 대화 상자, 도구 창 또는 디자인 화면 내의 하이퍼링크입니다.

- **스마트 태그 및 빌드 대화 상자와 같은 도우미 UI 메커니즘** 이러한 메커니즘은 사용자가 UI 요소를 이해 하거나 스마트 태그 또는 작성기 대화 상자와 같은 작업을 용이 하 게 하는 데 도움이 됩니다.

- **UI 도움말 단추** (사용 되지 않음) 관련 F1 도움말 항목에 대 한 액세스를 제공 하는 제목 표시줄에 표시 되는 표시기입니다.

### <a name="text"></a>텍스트

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>대화 상자의 지침 및 보완 텍스트
 복잡 한 작업을 지 원하는 대화 상자에서 UI 내에 지침 텍스트를 제공 해야 하는 경우가 있을 수 있습니다. 스타일 작성에 대 한 자세한 내용은 [UI 텍스트 및 용어](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 를 참조 하세요.

#### <a name="infotips"></a>InfoTips
 종종 지침 텍스트가 너무 짧기 때문에 UI에서 배치 하지 못할 수도 있고 숙련 된 사용자에 게 혼란을 주는 것 처럼 새로운 사용자 에게만 유용할 수도 있습니다. 이 경우 지침/정보 텍스트는 정보 팁 아래에 도구 설명으로 배치 되어야 합니다.

 InfoTips은 관련 된 컨트롤 근처에 배치 해야 하며, 특정 정보 팁 아이콘을 사용 해야 합니다 .이는 눈에 띄지 않습니다.

 ![Visual Studio의 정보 팁](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio의 정보 팁 예제**

### <a name="interactive-help-mechanisms"></a>대화형 도움말 메커니즘

#### <a name="f1-help"></a>F1 도움말
 F1 도움말은 편집기 또는 디자인 화면 내에서 필요 하지만 Visual Studio 환경의 다른 곳에서는 필요 하지 않습니다.

#### <a name="hyperlinks-to-help-topics"></a>도움말 항목에 대 한 하이퍼링크
 하이퍼링크를 사용 하 여 작업을 수행 하거나, IDE 내에서 탐색 하거나, 브라우저에서 도움말을 시작할 수 있습니다. 시각적 및 레이아웃 지침에 대 한 언어 및 07.10.01 단추 및 하이퍼링크에 대 한 자세한 내용은 [UI 텍스트 및 용어](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 를 참조 하세요.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>도움말 [?] 대화 상자 제목 표시줄의 단추 (사용 되지 않음)
 대부분의 경우 대화 상자의 제목 표시줄에 있는 도움말 [?] 단추가 더 이상 사용 되지 않습니다. UI 토픽은 더 이상 doc 모델의 일부가 아니므로 연결 하는 데 관련 된 항목이 없을 수 있습니다. 기본적으로 제목 표시줄 단추는 F1 도움말과 같지만 대화 상자에서 더 이상 필요 하지 않습니다. 일부 경우에는 더 최신 UI에서 하이퍼링크를 사용 하는 것이 더 일반적인 개념 또는 절차적 정보를 제공 하는 표시기로 계속 사용할 수 있습니다.

##### <a name="dialogs-created-through-the-environment"></a>환경을 통해 만든 대화 상자
 대부분의 셸 대화 상자는 **Vbdialogboxparam** 함수를 통해 생성 됩니다. 이 공유 함수는 대화 상자에서 **도움말** 단추를로 **이동 하는** 데 도움이 되도록 업데이트 되었습니다. 단추를 클릭 합니다.

 구체적으로, **Vbdialogboxparam** 함수는 ID가 **idhelp** (9) 또는 label이 **도움말** 또는 **& 도움말**인 단추의 대화 상자 템플릿을 찾습니다. 도움말 단추가 **있으면 해당 단추가** 숨겨지고 **WS_EX_CONTEXTHELP** 스타일이 대화 상자에 추가 됩니다. 단추를 클릭 합니다.

 대화 상자를 만들 때 대화 상자 프로시저를 스택으로 푸시하고 **DialogPreProc**이라는 전처리 대화 상자를 사용 하 여 대화 상자를 호출 합니다. **?** 단추를 클릭 하면 대화 상자에 **SC_CONTEXTHELP** **WM_SYSCOMMAND** 전송 됩니다. **DialogPreProc** 는이 명령을 캡처하여 원래 대화 상자 프로시저에 전달 되는 **WM_HELP** 메시지로 변경 합니다.

 대부분의 환경에서 만든 대화 상자에는 대화 상자에 대 한 도움말 단추가 있습니다. 대화 상자가 표시 되 면 도움말 단추가 자동으로 숨겨지고 **?** 단추가 작동 합니다. 그렇다면 Windows에서 단추가 제거 되거나 변경 된 경우이 솔루션을 사용 하면 원래 도움말 단추로 빠르게 다시 이동할 수 있습니다.

 이 솔루션은 버그를 일으킬 수 있는 네 가지 가정을 만듭니다.

- 대화 상자의 도움말 단추는 **idhelp** (9)입니다.

- 도움말 단추가 숨겨진 경우 대화 상자가 올바르게 표시 됩니다.

- 대화 상자는 해당 경우 winproc 대체 하지 않습니다.

- 대화 상자가 다른 대화 상자 내에 포함 되지 않습니다.

  대화 상자가 msenv 내에 있고 **Vbdialogboxparam**을 사용 하지 않는 경우 고유한 처리기를 구현 하기 전에 **vbdialogboxparam** 활용을 조사 합니다.

##### <a name="dialogs-created-through-other-packages"></a>다른 패키지를 통해 만든 대화 상자
 Msenv 외부에 있는 대화에 대해 사용자 고유의 솔루션을 구현할 수 있습니다. VSPackage의 공유 대화 상자 클래스의 경우 단추를 제목 표시줄로 이동 하거나 각 대화 상자에 대 한 처리기를 구현 하는 것이 좋습니다. 다음 코드는 시작 하는 데 도움이 되는 구현의 기본 구조입니다.

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>관리 코드의 도움말 단추
 관리 코드에서는 창 제목 표시줄 도움말 단추의 기본 동작을 재정의 하는 것이 쉽습니다. 이 동작을 보여 주는 전체 데모 응용 프로그램은 다음과 같습니다. 본질적으로는 폼의 **WndProc** 메서드를 재정의 한 다음 **SC_CONTEXTHELP** 메시지를 가로챌 때 F1 도움말 요청을 실행 해야 합니다.

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>참고 항목
- [Visual Studio의 글꼴 및 서식 지정](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Visual Studio의 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Visual Studio의 알림 및 진행률](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
