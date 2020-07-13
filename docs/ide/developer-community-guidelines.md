---
title: Developer Community 지침
description: Visual Studio Developer Community 사용 지침을 설명합니다.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed52bcbd6d27a958276541c2d6813aa322c73839
ms.sourcegitcommit: a466720759426265b18b0f8d74a970e72493d700
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86092299"
---
# <a name="developer-community-guidelines"></a>Developer Community 지침

Developer Community에서는 Visual Studio에 관한 이슈 및 기능 제안을 추적합니다.

## <a name="submitting-problems-and-suggestions"></a>문제 및 제안 제출

[Visual Studio Developer Community](https://developercommunity.visualstudio.com/)에서는 Visual Studio에 관한 이슈 및 기능 제안을 추적합니다.

### <a name="before-submitting-an-issue"></a>이슈를 제출하기 전에 확인할 사항

Visual Studio Developer Community에서 이슈를 검색하여 이슈가 이미 있지 않은지 확인합니다. 이슈가 이미 있는 경우 관련 의견을 추가하고 투표합니다.

이슈가 질문인 경우 _visual-studio_ 태그를 사용하여 [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) 커뮤니티에 질문합니다. 해당 태그를 모니터링하는 고객 지원 직원이 있으며 질문에 답변하는 데 도움을 드립니다.

버그 또는 기능을 설명하는 기존 이슈를 찾을 수 없는 경우 아래 지침을 사용하여 이슈를 제출합니다.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>적합한 버그 신고 또는 기능 제안 작성

- 이슈당 하나의 문제 또는 기능 요청만 제출합니다.

  - 여러 문제나 기능 요청을 단일 이슈로 결합하면 진단하기가 더 어렵고 다른 사용자가 이슈에 투표하기가 더 어려워집니다.
  - 동일한 의견에 해당하지 않는 한 이슈를 댓글로 기존 이슈에 추가하지 마세요. 유사해 보이는 이슈가 많이 있지만 각자 다양한 원인이 있으므로 이슈를 진단하기가 더 어려워집니다.

- 더 자세한 정보를 제공할수록 Microsoft에서 이슈를 더욱 쉽게 재현하고 해결할 수 있습니다.
- 각 이슈에 다음 단계를 포함합니다.

  - 재현 가능한 단계(1... 2... 3...) 및 예상한 결과와 발생한 결과
  - 이미지, 애니메이션 또는 비디오 링크. 이미지와 애니메이션은 재현 단계를 설명하지만 대체하지 ‘않습니다’.
  - 가능한 경우 이슈를 설명하는 코드 조각 또는 손쉽게 머신으로 끌어와 이슈를 다시 생성할 수 있는 코드 리포지토리의 링크

- 다음 단계를 수행해야 합니다.

  - 검색하여 중복 이슈가 있는지 확인합니다. 중복 이슈가 있는 경우 기존 이슈에 투표하고 필요에 따라 추가 댓글이나 설명을 입력합니다.
  - 모든 확장 프로그램을 사용하지 않도록 설정한 후 이슈를 다시 생성합니다. 설치한 확장 프로그램으로 인해 이슈가 발생한 경우에는 확장 프로그램에 대한 이슈를 각각 제출합니다.
  - 이슈에 관한 코드를 단순화하여 Microsoft에서 문제를 더욱 효과적으로 파악하도록 돕습니다.

세부 정보가 많은 이슈라 할지라도 Microsoft에서 이슈를 재현하지 못할 수 있으며 추가 정보를 요청할 수 있습니다.

## <a name="managing-problem-reports"></a>문제 신고 관리

이슈 심사는 기능 팀 내에서 협업으로 수행하는 다단계 프로세스입니다. 일반적으로 심사는 1주일이 걸리지만 더 오래 걸릴 수도 있습니다. 심사의 목표는 이슈가 어떻게 처리될지 버그 신고자가 명확하게 이해하도록 돕는 것입니다. 예를 들어 심사 완료 후 버그 신고자는 Microsoft가 문제를 해결할 계획인지, 아니면 더 많은 커뮤니티 피드백을 기다릴지 알 수 있습니다.

문제를 보고한 후 상태는 제출의 해당 수명 주기를 나타냅니다. Visual Studio 제품 팀은 피드백을 검토할 때 해당 피드백을 적절한 상태로 설정합니다. [문제 상태 및 FAQ](https://docs.microsoft.com/visualstudio/ide/report-a-problem)를 참조하여 신고한 문제의 처리 상황을 추적합니다.

이슈에 중요한 정보가 누락된 경우 ‘추가 정보 필요’ 상태가 할당됩니다. Microsoft는 필요한 특정 정보를 포함하여 이슈에 댓글을 추가하며 사용자는 전자 메일 알림을 받게 됩니다. 사용자가 7일 이내에 정보를 제공하지 않으면 미리 알림이 전송됩니다. 그 후에는 14일 동안 활동이 없을 경우 티켓을 닫습니다.

### <a name="wont-fix-bugs"></a>버그 수정 안 함

Microsoft는 비용과 혜택 간에 불균형이 발생하면 일부 버그를 닫습니다. 예를 들어 수정이 너무 복잡하여 많은 사용자가 재발을 경험할 위험이 있는 경우에는 수정이 적절하지 않을 수 있습니다. 이와 같은 버그를 닫을 때 해당 이유에 관한 설명이 제공됩니다.

### <a name="other-product"></a>기타 제품

이슈 신고 시 Visual Studio가 아닌 다른 제품이 원인인 것으로 확인되는 경우도 있습니다. 즉, 다른 관련 애플리케이션 또는 확장 프로그램이 원인이 될 수 있습니다. 

이 경우 지원 팀은 이슈를 닫고 다른 제품으로 이슈를 열도록 요청합니다. 이와 같은 이슈를 제출할 수 있는 일반적인 위치 중 일부는 다음과 같습니다.

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Visual Studio 구독 지원](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [창](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>추가 정보

- [성능 이슈 해결 가능성을 높이는 방법](https://docs.microsoft.com/visualstudio/ide/how-to-increase-chances-of-performance-issue-being-fixed)
- [MSBuild의 문제 해결 및 로그 만들기](https://docs.microsoft.com/visualstudio/ide/msbuild-logs)

## <a name="managing-feature-suggestions"></a>기능 제안 관리

기능 제안은 Microsoft와 개발자 커뮤니티 멤버 간의 소통 수단입니다. 기술적으로는 모든 기능 요청을 계속 열어 둘 수 있습니다. 그러나 이슈를 열어 두면 커뮤니티에서 기능의 실제 상태가 눈에 잘 띄지 않을 수 있습니다. 따라서 처리하지 않을 기능 요청을 닫고 처리할 수 있는 기능에 ‘검토 중’ 레이블을 할당합니다.

기능을 제안했는데 해당 요청을 처리할 계획이 없다는 것을 안 사용자는 실망할 수도 있습니다. Microsoft는 이 상황을 이해하고 있으며 이 프로젝트 또는 Microsoft가 기여한 다른 프로젝트에서 똑같이 겪었던 일이므로 안심하시길 바랍니다. 또한 보내 주시는 모든 의견을 환영합니다. 다만 제안을 닫거나 제안에 ‘검토 중’ 레이블을 할당하더라도 양해해 주시길 바랍니다. 기능 제안이 열려 있어야 한다고 생각되면 사용 사례를 분명히 설명하고 문의하거나 더 많은 찬성표를 얻으세요.

의사 결정 프로세스에서 Microsoft는 기능 제안에 관한 다음 특성을 확인합니다.

- 해당 제안을 빌드하고 유지 관리할 수 있습니까?
- 전반적인 [로드맵](https://docs.microsoft.com/visualstudio/productinfo/vs-roadmap) 전략에 부합합니까?
- 투표 및 댓글로 표시된 커뮤니티 지원이 있습니까?
- 커뮤니티 지원이 적더라도 만족합니까?

해당 질문에 “예”로 답변할 수 없다면 해당 제안을 닫습니다. 그러나 종종 더 많은 커뮤니티 피드백을 수집하기 위해 제안은 ‘검토 중’ 상태로 열려 있습니다.

[제안 상태 및 FAQ](https://docs.microsoft.com/visualstudio/ide/report-a-problem)를 참조하여 기능 제안의 진행 상황을 추적합니다.

## <a name="discussion-etiquette"></a>토론 에티켓

대화를 명확하고 투명하게 유지하려면 토론을 영어로 제한하고 이슈와 관련된 사항을 다룹니다. 또한 다른 사용자를 배려하고 항상 예의 바르고 전문적인 태도를 보입니다.

자세한 내용은 [Microsoft 커뮤니티 준수 사항](https://answers.microsoft.com/en-us/page/codeofconduct)을 참조하세요.

토론 에티켓을 위반하면 댓글이 제거되며 결국 사용자 참여가 금지될 수 있습니다.

## <a name="data-privacy"></a>데이터 개인 정보

댓글과 응답은 공개적으로 표시되지만 모든 첨부 파일은 Microsoft에만 비공개적으로 공유됩니다. 이와 같은 표시 방식은 전체 커뮤니티에서 다른 사용자가 발견한 이슈와 솔루션을 볼 수 있으므로 유용합니다. 데이터 또는 ID의 개인 정보에 대한 우려가 있는 경우 관련 옵션이 있습니다. [Developer Community 데이터 개인 정보](https://docs.microsoft.com/visualstudio/ide/developer-community-privacy)에 관해 자세히 알아보세요.

## <a name="next-steps"></a>다음 단계

[Visual Studio Developer Community](https://developercommunity.visualstudio.com/)로 이동하여 문제를 신고하거나, 기능을 제안하거나, 기존 티켓을 찾아봅니다. 즐겨보세요!
