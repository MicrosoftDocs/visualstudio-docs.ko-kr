---
title: '문제 보고: 상태 및 FAQ'
description: 문제 보고 도구의 개요를 제공하며 문제 상태 및 정의를 포함합니다.
ms.date: 11/15/2018
ms.custom: seodec18
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca095bf424420fb73ba8f369f7e41daea92fe33d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88584504"
---
# <a name="report-a-problem-states-and-faq"></a>문제 보고: 상태 및 FAQ

문제 보고 도구를 사용하면 Visual Studio 개발자 커뮤니티에서 문제를 제출할 수 있습니다. 각 문제 보고서는 핵심 엔지니어링 시스템의 작업 항목이 되며, 중요한 문제를 식별하고 해결하는 데 도움이 되도록 제품 팀과 직접 소통할 수 있는 권한을 부여합니다. 풍부한 진단 정보와 함께 제출된 피드백은 Visual Studio 제품군을 개선하는 데 중요합니다. 시간을 내어 문제를 보고해 주셔서 정말 감사합니다.

또한 다른 커뮤니티 구성원의 피드백에 투표하면 문제에 더 많은 관심을 기울이고 문제를 신속하게 해결할 수 있습니다.

## <a name="problem-status"></a>문제 상태

문제를 보고한 후 상태는 제출의 해당 수명 주기를 나타냅니다. Microsoft 팀이 사용자의 피드백을 검토하고 적절한 상태로 설정합니다.  해당 의미 및 색 표시기와 함께 아래 나열된 상태를 참조하여 문제 보고서의 진행 상황을 추적합니다.

![개발자 커뮤니티의 문제 보고에 대한 새로운 상태](../ide/media/ProblemStates/New.jpg)

**새로운 상태**는 버그 또는 문제가 새로 보고되었으며 아직 작업이 수행되지 않았음을 나타냅니다.

- - -

![개발자 커뮤니티의 문제 보고에 대한 심사 상태](../ide/media/ProblemStates/Triaged.jpg)

**심사**는 조정, 변환 및 중복에 대한 초기 검사와 같은 준비 단계가 완료되었음을 나타냅니다. 티켓은 고려 사항에 해당하는 엔지니어링팀으로 전달되었습니다.

- - -

![개발자 커뮤니티의 문제 보고에 대해 고려 중인 상태](../ide/media/ProblemStates/UnderConsideration.jpg)

**고려 중**은 Microsoft가 커뮤니티 영향에 대한 사용자의 문제를 검토하고 그에 따라 우선순위를 지정한다는 것을 나타냅니다. 커뮤니티 영향이 아직 명확하지 않거나 중요하지 않은 경우, 이 상태에서 문제를 계속 모니터링할 것입니다.

- - -

![개발자 커뮤니티의 문제 보고에 대해 조사 중](../ide/media/ProblemStates/UnderInvestigation.jpg)

**조사 중**은 엔지니어가 문제 해결 방법을 찾기 위해 적극적으로 조사하고 있음을 나타냅니다.

- - -

![개발자 커뮤니티의 문제 보고를 위한 추가 정보 필요 상태](../ide/media/ProblemStates/NeedMoreInfo.jpg)

**추가 정보 필요**는 조사를 계속 진행할 수 있도록 더 많은 진단 정보가 필요함을 나타냅니다.  [추가 정보 필요 요청에 응답하는 방법을 알아봅니다.](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed)

- - -

![수정됨 - 개발자 커뮤니티의 문제 보고에 대해 보류 중인 릴리스 상태](../ide/media/ProblemStates/FixedPendingRelease.jpg)

**수정됨 - 보류 중인 릴리스**는 문제에 대해 수정했으며 곧 출시될 미리 보기 또는 릴리스에서 사용할 수 있음을 나타냅니다.  수정 사항을 미리 보기에서 사용할 수 있게 되면 문제는 미리 보기 버전을 지정하는 “수정된 항목” 태그로 태그가 지정됩니다.

- - -

![종결 - 개발자 커뮤니티의 문제 보고에 대해 수정된 상태](../ide/media/ProblemStates/ClosedFixed.jpg)

**종결 - 수정됨**은 문제 해결책을 출시했음을 나타냅니다. 이제 문제는 또한 릴리스 버전을 지정하는 "수정 항목:" 태그로 태그가 지정되었습니다.

- - -

![종결 - 개발자 커뮤니티의 문제 보고에 대한 중복 상태](../ide/media/ProblemStates/ClosedDuplicate.jpg)

**종결 - 중복**은 다른 피드백을 통해 이미 문제가 보고되었음을 나타냅니다. 원래 문제 보고서를 추적할 수 있는 링크로 제공합니다.

- - -

![종결 - 개발자 커뮤니티의 문제 보고에 대한 낮은 우선순위 상태](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**종결 - 낮은 우선순위** 개발자 커뮤니티의 각 사용자를 최고의 가치로 이끌 수 있도록 집중하기 위해 고객에게 가장 큰 영향을 주는 문제의 우선순위를 지정합니다. 현재로서는 이 특정 문제를 해결할 수 없지만, 모든 피드백은 소중하며 Visual Studio를 개선하는 데 도움이 됩니다.

- - -

![종결 - 개발자 커뮤니티의 문제 보고에 대해 버그 아님 상태](../ide/media/ProblemStates/ClosedNotABug.jpg)

**종결- 버그 아님**은 보고된 기능이 현재 설계에 의한 것이라고 확인했음을 나타냅니다.

- - -

![종결 - 개발자 커뮤니티의 문제 보고에 대해 정보 부족 상태](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

**종결 - 정보 부족**은 이 문제를 조사하기에 충분한 정보가 없음을 나타냅니다. 필요한 정보를 얻을 수 있게 되면 기꺼이 피드백을 재고하겠습니다.

- - -

![종결 - 개발자 커뮤니티의 문제 보고에 대한 다른 제품 상태](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

**종결 - 다른 제품**은 문제가 다른 제품에 적용되는 것으로 확인했음을 나타냅니다. 외부 제품 및 모든 관련 링크에 대한 Microsoft의 주석을 참조하세요.

- - -

## <a name="faq"></a>FAQ

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>문제를 빨리 해결할 가능성을 높일려면 어떻게 해야 하나요?

검색을 통해 보고하려는 문제가 아직 보고되지 않았는지 확인하는 것이 좋습니다. 문제와 일치하는 기존 항목을 찾으면 해당 문제 티켓에 따라 투표합니다.

문제를 팀이 재현하는 데 도움이 되는 모든 정보를 제공합니다.  이 정보에는 필요한 재현 단계, 코드 조각, 스크린샷, 재현 기록, 로그 파일 및 기타 아티팩트가 포함됩니다.  다음은 [Visual Studio에서 문제를 보고하는 방법](./how-to-report-a-problem-with-visual-studio.md)입니다.

### <a name="how-is-my-feedback-prioritized"></a>어떻게 내 피드백 우선순위가 지정되나요?

고객으로부터 많은 중요한 문제를 받습니다. 개발자 커뮤니티에서 각 사용자에게 최고의 가치를 제공하기 위해 커뮤니티 영향이 가장 큰 피드백에 대해 우선순위를 부여합니다.

피드백에 대해 개별적으로 답변할 수 없는 경우라도 보내준 의견에 매우 감사드립니다. 모든 피드백은 적절한 팀에 전달되도록 하겠습니다.

Visual Studio를 개선하는 데 투자한 시간을 진정으로 가치있게 여깁니다.

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>해결책이 만족스럽지 않으면 어떤 조치를 취할 수 있나요?

팀은 모든 문제를 진단하고 해결하기 위해 최선을 다하고 있지만 권장 사항에 충분히 만족하지 못하는 경우도 있을 수 있습니다. 피드백에 대해 다시 언급하고 만족하지 못하는 것을 정확하게 알려주시면 고객의 요구를 충족시킬 수 있도록 최선을 다할 것입니다.

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>내 피드백의 진행 상황은 어떻게 알수 있나요?

Microsoft 엔지니어링 팀은 피드백 티켓에 대한 의견을 개진하고 진행 상황에 따라 티켓 상태를 변경함으로써 커뮤니케이션할 것입니다. 티켓 상태가 변경되거나 주석이 게시될 때 전송되는 이메일 알림을 모니터링하세요.  개발자 커뮤니티 사이트의 프로필 및 기본 설정에서 알림 빈도를 관리할 수 있습니다.

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>개발자 커뮤니티 웹 사이트에서 Visual Studio IDE에 대한 문제를 추가할 수 없는 이유는 무엇인가요?

Visual Studio를 통해 문제를 보고하면 진단 정보를 자동으로 보고서에 포함할 수 있습니다. 이 정보는 엔지니어가 문제를 완전히 이해하고 해결하는 데 필요한 컨텍스트를 제공하는 필수 정보입니다.

Visual Studio를 통해 보고하면 큰 로그 파일, 크래시 정보, 스크린샷, 재현 기록 및 고품질 해상도를 보다 빠르게 제공하는 데 도움이 되는 기타 아티팩트 등 다양한 진단 정보를 쉽게 공유할 수 있습니다.
