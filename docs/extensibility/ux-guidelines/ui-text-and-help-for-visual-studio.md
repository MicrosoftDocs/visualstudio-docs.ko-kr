---
title: UI 텍스트 및 비주얼 스튜디오에 대한 도움말 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0477a0e1994e9c3b94df13ace4c1f3b4df51039
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301538"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Visual Studio의 UI 텍스트 및 도움말
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>UI 텍스트 및 용어
 효과적인 UI에는 이해할 수 있는 텍스트가 중요합니다. 소프트웨어 사용자는 먼저 레이블, 즉 당면 한 작업을 완료하는 데 가장 관련성이 있는 레이블을 읽는 경향이 있습니다. 정적 텍스트는 더 적은 빈도로 읽습니다. 사용자가 전체 창을 빠르게 스캔한 다음 이 대략적인 순서로 UI를 읽도록 계획합니다.

1. 중앙의 대화형 컨트롤

2. 커밋 단추

3. 다른 곳에서 발견된 대화형 컨트롤

4. 주요 지침

5. 추가 설명

6. 창 제목

7. 본문의 기타 정적 텍스트

### <a name="usage-patterns-for-ui-text"></a>UI 텍스트의 사용 패턴

#### <a name="title-bar-text"></a>제목 표시줄 텍스트
 제목 표시줄 텍스트는 UI를 생성한 명령과 일치해야 합니다.

#### <a name="instructional-text-helper-text"></a>교육 텍스트(도우미 텍스트)
 일부 대화 상자에서는 창이나 페이지에서 수행할 작업을 설명하는 주요 지침을 제공하는 것이 좋습니다. 이를 "도우미 텍스트"라고도 합니다.

##### <a name="writing-style-rules-for-helper-text"></a>도우미 텍스트에 대한 스타일 규칙 작성

- 명백한 설명하지 마십시오. 절대적으로 필요한 경우가 아니면 지침 텍스트를 포함하지 마십시오.

- 지침 텍스트는 항상 대화 상자의 맨 위에 배치되며 수행 중인 작업을 참조해야 합니다.

- 사용자에게 수행해야 할 작업을 정확하게 설명합니다. 과도한 통신과 중복성을 피하십시오.

- 각 창을 검토하고 중복 된 단어와 문을 제거합니다.

- 지침 텍스트를 짧게 유지합니다. 특정 사용자 나 시나리오에 대해 더 많은 정보가 필요한 경우 자세한 개념적 온라인 항목에 대한 링크를 제공합니다.

- 모든 단어가 무게를 유지하고 필요 있도록 텍스트를 작성합니다.

- [사용자 인터페이스 텍스트](/windows/desktop/uxguide/text-ui) 및 스타일 및 톤에 대한 기존 Microsoft 지침을 [따릅니다.](/windows/desktop/uxguide/text-style-tone)

#### <a name="supplemental-instructions"></a>추가 지침
 추가 지침은 사용자가 컨트롤 또는 컨트롤 그룹그룹을 이해하는 데 도움이 되는 추가 정보를 제공합니다. 여기에는 입력 컨트롤이 기대하는 형식을 이해하는 데 필요한 힌트 텍스트도 포함될 수 있습니다. 추가 지침을 아껴서 사용하십시오. 사용자가 자신이 선택한 결과를 완전히 이해하지 못하는 경우를 대비하여 예약합니다.

 ![Visual Studio의 추가 텍스트](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Visual Studio의 추가 텍스트**

 ![Visual Studio의 추가 텍스트](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Visual Studio의 추가 텍스트**

#### <a name="infotips"></a>인포팁
 종종 지침 텍스트가 UI에 배치하기에는 너무 길거나 숙련된 사용자에게 는 혼란스러울 수 있는 새 사용자에게만 유용할 수 있습니다. 이 경우 지침/정보 텍스트를 InfoTip 아래에 도구 설명으로 배치해야 합니다.

 InfoTips는 관련되어 있는 컨트롤 근처에 배치해야 하며 눈에 거슬리지 는 아직 눈에 띄지 않는 특정 InfoTip 아이콘을 사용해야 합니다.

 ![Visual Studio의 정보 팁](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **비주얼 스튜디오에서 인포팁의 예**

##### <a name="writing-style-rules-for-infotips"></a>인포팁에 스타일 규칙 작성

- 정보 팁을 완전한 문장으로 작성합니다. 특정 동사, 문장 대/소문자 및 끝 문장 부호가 필요합니다.

- InfoTips를 사용하여 주요 지침 이나 정보를 보완 합니다. 다른 단어를 사용하여 기본 아이디어를 다시 지정하는 경우 InfoTip이 필요하지 않습니다.

- 인포팁을 짧고 달콤하게 유지하세요. 사용자를 지원하고 장려하는 작은 단어와 평범하고 일상적인 언어를 사용하십시오.

- [사용자 인터페이스 텍스트](/windows/desktop/uxguide/text-ui) 및 스타일 및 톤에 대한 기존 Microsoft 지침을 [따릅니다.](/windows/desktop/uxguide/text-style-tone)

#### <a name="control-labels"></a>제어 레이블
 컨트롤 레이블은 짧고 간결해야 하며 [컨트롤에 대한 Windows 데스크톱 지침을](/windows/desktop/uxguide/controls)따라야 합니다.

 UI 내에서 컨트롤 레이블 형식 및 배치에 대한 자세한 내용은 [Visual Studio용 레이아웃을](../../extensibility/ux-guidelines/layout-for-visual-studio.md)참조하십시오.

#### <a name="help-links"></a>도움말 링크
 도움말 링크는 지침 텍스트 내에서 또는 UI 본문에 배치할 수 있습니다. 도움말 에 대한 링크이거나 내부 대화 상자를 시작할 수 있습니다.

##### <a name="visual-style-rules-for-help-links"></a>도움말 링크에 대한 시각적 스타일 규칙

- 하이퍼링크에 올바른 환경 색상을 사용합니다. 제대로 스타일이 설정된 하이퍼링크는 클릭할 때 빨간색으로 짧게 깜박이지 않습니다. 이 것을 보면 환경 색상이 사용되지 않음을 나타냅니다.

- 밑줄은 가리키거나 링크가 단락에 포함될 때만 사용해야 합니다.

- 하이퍼링크에 대한 시각적 및 상호 작용 스타일에 대한 자세한 내용은 단추 및 하이퍼링크를 참조하십시오.

##### <a name="writing-style-rules-for-help-links"></a>도움말 링크에 대한 스타일 규칙 작성

- 대화 상자를 시작할 때 타원에 대한 표준을 유지합니다: 탐색을 위한 타원이 없고, 작업에 추가 UI가 필요한 경우 타원이 됩니다.

     ![Visual Studio의 도움말 링크](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **도움말 링크의 타원(...)은 작업에 추가 UI가 필요했음을 나타냅니다.**

- 링크는 사용자의 의도가 아니기 때문에 "학습"으로 시작해서는 안 됩니다. 사용자는 일반 교육을 받지 않고 특정 질문에 답하려고 합니다.

- 구 도움말 링크는 주제가 대답할 질문을 할 수 있도록 합니다.

     올바르지 않음: "Windows Azure 모바일 서비스 가격에 대해 자세히 알아보기"

     올바른: "Windows Azure 모바일 서비스에 사용할 수 있는 가격 책정 옵션?"

- 링크 텍스트에 *클릭을* 사용하지 마십시오.

- "여기"라는 단어만 연결하지 마십시오. 이것은 하이퍼 링크 된 단어만 음성을 하는 일부 화면 판독기의 경우 문제가 됩니다.

     올바르지 않음: "Windows Azure 모바일 서비스에 대한 정보를 여기에서 찾을 **수 있습니다."**

     올바른: "Windows Azure 모바일 서비스에 사용할 수 있는 가격 책정 옵션?"

- 도움말 링크에 대한 올바른 쓰기 스타일에 대한 자세한 내용은 [도움말에 대한 Windows 데스크톱 지침을](/windows/desktop/uxguide/winenv-help)참조하십시오.

#### <a name="hint-text"></a>힌트 텍스트
 힌트 텍스트는 컨트롤 내 또는 컨트롤 아래에 워터마크로 나타납니다. 올바른 서식은 적절한 VSColors 토큰을 `Environment.GrayText`사용하여 적용됩니다.

 여러 가지 형태로 나타날 수 있습니다.

- 컨트롤 레이블 대신 다음을 수행합니다.

     ![Visual Studio의 힌트 텍스트](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- 동사, 지침을 제공:

     ![Visual Studio의 힌트 텍스트](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- 필수 항목을 나타내는 텍스트:

     ![Visual Studio의 힌트 텍스트](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>워터마크 텍스트
 빈 디자인 표면에서 텍스트는 수행할 작업을 나타내고 적절한 경우 다른 관련 창을 여는 링크를 제공해야 합니다.

 ![Visual Studio의 워터마크 텍스트](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **비주얼 스튜디오에서 워터마크 텍스트의 예**

### <a name="common-terminology"></a>일반적인 용어

|용어|설명|주석|
|----------|-----------------|-------------|
|로그인 / 로그아웃|동사는 웹 속성에 인증을 나타내는 웹과 동의어로 사용됩니다. 클라이언트 내에서 는 다른 모든 연결에서 사용할 수 없는 로밍 및 라이선스와 같은 상위 수준의 기능을 제공하는 최상위 ID를 나타내는 IDE 사용자 연결에서 로그인 및 로딩을 위한 최상위 개념으로 이 개념을 한 번 사용합니다.|IDE 사용자는 최상위 IDE 사용자를 나타내므로 로그인/로그아웃 동사를 나타내는 유일한 기능입니다.|
|연결 /연결 해제|기능이 온라인 서비스에 대한 단일 연결을 유지하는 위치에서 사용합니다.|한 번에 하나의 활성 Azure 연결만 가질 수 있는 서버 탐색기는 연결/연결 끊기의 예입니다.|
|추가/제거|비파괴. 목록에서 무언가를 추가하거나 제거할 때 사용합니다.|TFS 연결 관리자 서버 목록 대화 상자는 추가/제거의 예입니다.|
|DELETE|파괴적인. 제거중인 요소가 영구적으로 삭제되거나 디스크에서 삭제되는 경우에만 사용하십시오.|일반적으로 "삭제"는 결과가 디스크에서 파일을 삭제하는 경우 프롬프트가 필요합니다.|

## <a name="error-messages"></a>오류 메시지

### <a name="overview"></a>개요
 오류가 발생합니다. 사용자가 수행할 수 있는 작업을 제한설정하는 것은 피할 수 있는 오류 메시지를 방지하는 현명한 첫 번째 단계입니다. 그러나 오류가 발생하면 잘 작성된 오류 메시지가 문제를 완화하는 데 큰 문제가 될 수 있습니다. 오류 메시지는 동기적이며 해결해야 하는 문제를 나타내기 때문에 사용자가 보는 가장 중요한 알림 유형 중 하나입니다. 잘못 작성된 오류 메시지는 사용자가 오류의 원인과 가능한 해결 방법을 스스로 결정할 수 있도록 합니다.

 사용자가 지나치게 사용중이거나 혼란스러운 오류 메시지에 주의를 기울이지 않을 수 있으므로 사용자 경험에 가치를 더하는 필요한 메시지만 작성할 수 있습니다. 메시지가 단순히 알림인 경우 다른 프레젠테이션을 사용합니다.

### <a name="rules-for-creating-an-error-message"></a>오류 메시지를 만들기 위한 규칙

- 오류 메시지를 생성할 때 대상에 적합한 오류 수준을 선택합니다. 해당되는 경우 사용자가 취할 수 있는 작업을 제공하는 간단한 요약을 목표로 합니다. 사용자가 알 필요가 없는 것을 명시하지 마십시오.

- 건설적인 지원을 제공합니다. 명령이 포함된 오류 메시지를 읽고 조치를 하는 것이 더 쉽습니다.

- 이중 네거티브를 사용하지 마십시오.

- 작성하는 오류 메시지에 대해 자동 문법 및 수동 문법 및 맞춤법 검사를 모두 수행합니다.

- 복잡한 오류 메시지의 경우 순차적 통신을 피하십시오. 오류 메시지에 F1 연결 은 사용하지 마십시오. 메시지 자체만으로도 충분해야 합니다.

- 올바른 아이콘을 사용합니다.

- 질문을 쉽게 이해하고 '삭제' 및 '취소'와 같이 명확한 선택 사항이 있는 단추를 사용할 수 있습니다.

- 경고의 경우, 진행의 결과가 무엇인지에 대해 명확히 하십시오. 단추는 결과를 나타내야 합니다.

- 오류의 경우 사용자가 문제를 해결하기 위해 수행할 수 있는 작업을 설명합니다. 단추는 작업이거나 "닫기"라고 말해야 합니다. 오류 메시지에는 "확인" 단추를 사용하지 마십시오.

- 오류 메시지를 생성할 때 스스로에게 물어봐야 할 몇 가지 질문:

  - 사용자가 이 오류만으로 문제를 해결하는 방법을 알아낼 수 있습니까?

  - 사용자가 이 오류와 동일한 어휘를 사용합니까?

  - 이 오류는 여러 상황에서 악의적이거나 공유되고 있습니까? 그렇다면 사용자에게 필요한 솔루션으로 어떻게 안내합니까?

#### <a name="build-errors"></a>빌드 오류
 Visual Studio는 소프트웨어 개발 도구이므로 대부분의 구성 요소에는 개발자의 작업을 이진 형식으로 변환하는 컴파일, 변환 또는 인코딩 단계가 있습니다. 이러한 변환은 컴파일러가 잘못 작성된 파일을 처리할 수 없거나 컴파일러 옵션이 올바르게 설정되지 않은 경우 오류가 발생할 수 있습니다.

 Visual Studio 사용자는 빌드 오류를 해결하는 데 엄청난 시간을 할애할 수 있습니다. 이 해결 시간은 오류에 종속성이 있거나 오류 메시지가 제대로 작성되지 않은 경우 증가하므로 오류의 원인을 밝히기가 어려울 수 있습니다.

 가장 좋은 빌드 오류는 처음에 발생하지 않는 오류입니다, 그래서 Visual Studio는 자동 완성 및 IntelliSense 물결을 제공합니다. 스키마 유효성 검사기 및 유사한 도구는 동일한 종류의 피드백을 제공합니다. 이러한 메커니즘은 사용자가 잘 구성된 코드를 생성하도록 사전에 안내하여 빌드 오류 의 가능성을 줄입니다.

 Visual Studio는 사용자가 문서 창에서 발생한 오류를 읽고 탐색할 수 있는 도구 창을 제공합니다. 사용자가 많은 양의 코드를 빠르게 탐색하고 문제의 위치로 직접 이동할 수 있도록 키보드 단축키가 제공됩니다. 또한 Visual Studio를 사용하면 각 빌드 오류를 특정 도움말 키워드/컨텍스트 ID에 연결하여 사용자가 오류에 대한 자세한 정보를 제공하는 도움말 항목으로 직접 이동할 수 있습니다.

 명확하고 간결한 빌드 오류를 작성합니다.

- 컴파일러 전문 용어가 거의 또는 전혀 없는 문제를 설명하는 **일반 언어를 사용합니다.** 빌드 오류의 텍스트는 지나치게 기술적이어야 합니다.

- **가능한 원인을 간략하게 설명합니다.** 예를 들어 "속성과 값 사이의 콜론이 '(속성) : (값)' 선언에서 누락되었습니다."

- 잠재적인 수정 사항에 대한 세부 정보를 제공합니다. 공간이 충분하지 않으면 해당 도움말 항목에 추가 세부 정보를 넣을 수 있습니다.

### <a name="components-of-a-well-written-error-message"></a>잘 작성된 오류 메시지의 구성 요소

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>오류 메시지에 셸 대화 상자 서비스를 사용합니다.
 셸 대화 상자 서비스를 사용하면 개별 요소에 큰 변경 없이 메시지, 특히 글꼴의 모양을 제어할 수 있습니다. **IErrorInfo** 메커니즘을 사용 하 여 **IVsUIShell::SetErrorInfo/보고서 오류 정보**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>효과적이고 적절한 알림 프레젠테이션을 선택합니다.
 데이터 손실을 피하기 위해 즉각적인 조치가 필요한 경우 중요한 경고와 함께 모달 대화 상자를 사용합니다(동기 알림). 중요 아이콘은 메시지를 읽지 않고 닫으면 부정적인 결과를 초래할 수 있는 상황에 대해 예약되어 있습니다. 데이터 손실은 경보 수준 응답이 필요한 중요한 상황입니다. 중요 아이콘의 남용은 사용자의 중요성을 둔감하게 합니다. 오류 메시지가 본질적으로 정보인 경우 모달 대화 상자(비동기 알림)에 대한 대안을 고려합니다.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>기술적인 설명이 아니라 문제가 발생한 이유에 대한 깔끔하고 간결한 설명을 제공합니다.
 설명에서 기술적 세부 사항으로 사용자에게 과도한 부담을 주면 오류 메시지를 무시할 가능성이 높아집니다. 좋은 메시지의 예:

- "요청된 파일을 열 수 없습니다."

- "인터넷에 연결할 수 없습니다."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>문제를 해결하는 방법에 대한 정보를 제공합니다.
 문제를 해결하는 방법에 대한 사용자 제안을 제공합니다. 제안이 없는 경우 사용자에게 정직하십시오. 기술 지원 또는 커뮤니티 지원과 같은 대체 온라인 소스에 대한 직접 링크를 제공합니다. 사용자에게 문제와 관련된 특정 온라인 정보를 가리킬 수 있습니다. 오류 ID의 경우 특정 오류에 대한 토론 스레드에 사용자를 연결하는 것이 좋습니다. 좋은 메시지의 예:

- "인터넷에 연결되어 있는지 확인하고 이 작업을 다시 시도하십시오."

- "파일이 있는지, 파일을 열 수 있는 권한이 있는지 확인합니다."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>짧고 요점에 메시지를 작성합니다.
 오류 메시지는 사용자에게 알리고 설명하고 솔루션을 제공할 수 있지만 너무 단어가 많은 경우 무시됩니다. 한 가지 해결책은 세부 정보 단추를 사용하여 점진적 공개를 사용하는 것입니다. 예를 들어 간단한 설명/솔루션을 제공 한 다음 세부 정보 단추 아래에 자세한 내용을 넣습니다. 사용자가 오류에 대한 자세한 정보를 읽기로 선택한 경우 그렇게 할 수 있습니다.

 메시지의 언어는 다음과 같은 여야 합니다.

- **도메인에 적합합니다.** 사용자가 이해할 수 있는 언어를 사용합니다. 고객이 개발자이지만, 우리가 가지고 있는 맥락과 용어가 없는 경우가 많습니다.

- **특정.** 모호한 표현을 피하고 관련된 개체의 특정 이름과 위치를 지정합니다. 예를 들어 "문자가 잘못되었습니다"와 같은 오류 메시지는 유용하지 않습니다. 어떤 문자? "파일을 찾을 수 없습니다." 어떤 파일?

- **정중.** 사용자를 비난하거나 바보 처럼 느끼게 하지 마십시오. 적대적이거나 공격적인 언어(죽이거나, 실행하고, 종료하고, 치명적, 불법)를 피하십시오. 종종 외침으로 보이고 읽을 수 없는 대문자 텍스트를 사용하지 마십시오. 유머를 사용하지 마십시오.

- **맞는.** 올바른 철자와 문법(심지어 알파에서도)을 사용합니다. 오타는 전문적이지 않고 당황스럽습니다.

- **컨텍스트에 적합합니다.** 적절한 단추 텍스트를 사용합니다. "확인" 단추를 피하고 대신 "계속" 또는 "예/아니요"를 사용합니다.

### <a name="error-message-examples"></a>오류 메시지 예제

|좋음|나쁨|
|----------|---------|
|"전화를 건 번호가 더 이상 서비스되지 않습니다. 번호를 확인하고 다시 전화를 걸거나 운영자가 0으로 전화를 걸어 주십시오."|- "오류 (449): 잘못된 번호"<br />- "이 처리되지 않은 예외 오류는 작업이 성공적으로 완료했음을 나타냅니다."<br /><br /> ![Visual Studio의 잘못된 오류 메시지](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>도움말 액세스

### <a name="overview"></a>개요
 MSDN의 설명서 외에도 Visual Studio 사용자는 UI에 있는 동안 사용자를 지원하기 위해 여러 액세스 포인트를 가지고 있습니다. 이러한 액세스 포인트를 일관되게 사용할 수 있도록 하려면 기능 팀에서 환경에서 제공하는 도움말 시스템을 활용해야 합니다. 이러한 액세스 포인트는 다음과 같습니다.

- **대화 상자의 교육 및 추가 텍스트입니다.** UI 표면에서 방향이나 설명을 제공하는 정적 텍스트또는 InfoTip 아이콘 위로 마우스를 가져가면 사용할 수 있습니다.

- **F1** 도움말(편집기만). Visual Studio 편집기 내에서 사용자는 언제든지 F1을 누르면 현재 선택 항목과 관련된 도움말 항목이 표시됩니다. F1과 관련된 주제가 적절하고 유익한지 확인합니다.

- **도움말 항목에 대한 하이퍼링크입니다.** 대화 상자, 도구 창 또는 디자인 표면 내의 하이퍼링크로 사용자가 작업을 수행하는 방법에 대한 기술, 기능 또는 정보에 대해 자세히 알아보는 데 도움이 되는 주제를 시작합니다.

- **스마트 태그 및 빌드 대화 상자와 같은 도우미 UI 메커니즘입니다.** 이러한 메커니즘은 사용자가 UI 요소를 이해하는 데 도움이 되거나 스마트 태그 또는 빌더 대화 상자와 같은 작업을 용이하게 합니다.

- **UI 도움말 단추(더** 이상 사용되지 않습니다). 관련 F1 도움말 항목에 대한 액세스를 제공하는 제목 표시줄에 표시되는 표시기입니다.

### <a name="text"></a>텍스트

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>대화 상자의 교육 및 추가 텍스트
 복잡한 작업을 지원하는 대화 상자에서는 UI 내에서 종종 대화 상자의 맨 위 또는 복잡한 컨트롤 근처에 있는 지침 텍스트를 제공해야 할 수 있습니다. 쓰기 스타일에 대한 자세한 내용은 [UI 텍스트 및 용어를](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 참조하십시오.

#### <a name="infotips"></a>인포팁
 종종 지침 텍스트가 UI에 배치하기에는 너무 길거나 숙련된 사용자에게 는 혼란스러울 수 있는 새 사용자에게만 유용할 수 있습니다. 이 경우 지침/정보 텍스트를 InfoTip 아래에 도구 설명으로 배치해야 합니다.

 InfoTips는 관련되어 있는 컨트롤 근처에 배치해야 하며 눈에 거슬리지 는 아직 눈에 띄지 않는 특정 InfoTip 아이콘을 사용해야 합니다.

 ![Visual Studio의 정보 팁](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **비주얼 스튜디오에서 인포팁의 예**

### <a name="interactive-help-mechanisms"></a>대화형 도움말 메커니즘

#### <a name="f1-help"></a>F1 도움말
 F1 도움말은 편집기 또는 디자인 표면 내에서 필요하지만 Visual Studio 환경의 다른 곳에서는 필요하지 않습니다.

#### <a name="hyperlinks-to-help-topics"></a>도움말 항목에 대한 하이퍼링크
 하이퍼링크를 사용하여 작업을 수행하거나, IDE 내에서 탐색하거나, 브라우저에서 도움말을 시작할 수 있습니다. 언어및07.10.01 버튼및 하이퍼링크에 대한 자세한 내용은 [UI 텍스트 및 용어를](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 참조하세요.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>대화 상자 제목 표시줄의 도움말 [?] 단추(더 이상 사용되지 않습니다).
 대부분의 경우 대화 상자의 제목 표시줄에 있는 도움말 [?] 단추는 더 이상 사용되지 않습니다. UI 항목은 더 이상 문서 모델의 일부가 아니므로 링크할 관련 주제가 없을 수 있습니다. 기본적으로 제목 표시줄 단추는 F1 도움말과 동일하며 대화 상자에서 더 이상 필요하지 않습니다. 하이퍼링크가 최신 UI에서 더 일반적으로 사용되지만 경우에 따라 더 많은 개념적 또는 절차적 정보를 사용할 수 있다는 지표로 사용할 수 있습니다.

##### <a name="dialogs-created-through-the-environment"></a>환경을 통해 생성된 대화 상자
 많은 셸 대화 상자는 **VBDialogBoxParam** 함수를 통해 만들어집니다. 이 공유 함수는 대화 상자에서 로 **도움말** 단추를 이동하는 데 도움이 도록 **업데이트되었습니다.** 이전 버전과 호환되고 확장 가능한 아키텍처를 유지하면서 버튼을 누릅니다.

 특히 **VBDialogBoxParam** 함수는 **IDHELP** (9) 또는 레이블이 **도움말** 또는 **도움말**&있는 단추에 대한 대화 상자 템플릿을 살펴봅니다. 도움말 단추를 발견하면 숨김이 숨겨져 **있고 WS_EX_CONTEXTHELP** 스타일이 대화 상자에 추가되어 **?** 대화 상자의 제목 표시줄에 있는 단추입니다.

 대화 상자가 만들어지면 대화 상자 proc를 스택으로 밀어 내고 **DialogPreProc**라는 사전 처리 대화 상자 proc를 사용하여 대화 상자를 호출합니다. 언제 **?** 버튼을 클릭하면 대화 상자에 **SC_CONTEXTHELP** **WM_SYSCOMMAND** 보냅니다. **DialogPreProc이** 명령을 캡처하 고 원래 대화 상자 proc에 전달 되는 **WM_HELP** 메시지로 변경 합니다.

 대부분의 환경에서 만든 대화 상자에는 대화 상자에 도움말 버튼이 있습니다. 대화 상자가 표시되면 도움말 버튼이 자동으로 숨김되고 **?** 버튼이 작동합니다. **?** 버튼은 이제까지 제거하거나 Windows에서 변경, 이 솔루션을 사용하면 신속하게 원래 도움말 버튼으로 다시 이동할 수 있습니다.

 이 솔루션은 버그를 일으킬 수 있는 네 가지 가정을 만듭니다.

- 대화 상자의 도움말 버튼은 IDHELP(9)입니다. **IDHELP**

- 도움말 버튼이 숨겨져 있으면 대화 상자가 올바르게 표시됩니다.

- 대화 상자는 윈프롬을 대체하지 않습니다.

- 대화 상자는 다른 대화 상자 안에 포함되지 않습니다.

  대화 상자가 msenv 내에 있고 **VBDialogBoxParam을**사용하지 않는 경우 자체 처리기를 구현하기 전에 **VBDialogBoxParam을** 활용하는 것을 조사하십시오.

##### <a name="dialogs-created-through-other-packages"></a>다른 패키지를 통해 생성된 대화 상자
 msenv 외부에 있는 대화 상자에 대해 고유한 솔루션을 구현할 수 있습니다. VSPackage에서 공유 대화 상자 클래스의 경우 단추를 제목 표시줄로 이동하거나 각 대화 상자에서 처리기를 구현하는 것이 좋습니다. 다음 코드는 시작하는 데 도움이 되는 구현의 골격입니다.

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
 관리 코드에서 창 제목 표시줄 도움말 단추의 기본 동작을 재정의하는 것은 쉽습니다. 다음은 이 동작을 보여 주는 전체 데모 응용 프로그램입니다. 기본적으로 폼의 **WndProc** 메서드를 재정의한 다음 **SC_CONTEXTHELP** 메시지가 가로채면 F1 도움말 요청을 해제해야 합니다.

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
