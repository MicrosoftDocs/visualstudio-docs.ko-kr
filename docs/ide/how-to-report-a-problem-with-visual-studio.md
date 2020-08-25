---
title: Visual Studio에서 문제를 보고하는 방법
description: Visual Studio에서 문제를 보고하는 방법 찾기
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e5f64ebdf93384b7def728ac5d01bcbaf6b0271
ms.sourcegitcommit: 98af63c1a53a732558f8207338dc2722abbbe49e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88584577"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Visual Studio 또는 Visual Studio 설치 관리자로 문제를 보고하는 방법

> [!NOTE]
> Mac용 Visual Studio는 [Mac용 Visual Studio에서 문제를 보고하는 방법](/visualstudio/mac/report-a-problem)을 참조하세요.

Visual Studio 또는 해당 설치 관리자에서 문제를 신고할 수 있습니다. 기본 제공되는 피드백 도구를 사용하면 Visual Studio 팀이 문제를 진단하고 해결하는 데 도움이 되는 진단 정보를 쉽게 추가할 수 있습니다. 문제를 보고하는 단계는 다음과 같습니다.

1. **Visual Studio에서** 오른쪽 위에 있는 피드백 아이콘을 선택하고 [문제 보고]를 선택합니다. 또한 **도움말** > **피드백 보내기** > **문제 보고** 메뉴에서 피드백 도구에 액세스할 수 있습니다.
![Visual Studio 개발자 커뮤니티의 문제 보고 팝업](media/feedback-button.png) 또는 Visual Studio를 설치할 수 없거나 Visual Studio 내의 피드백 도구에 액세스할 수 없는 경우 **Visual Studio 설치 관리자**에서 문제를 보고합니다.  설치 관리자에서 오른쪽 위에 있는 피드백 아이콘을 선택하고 [문제 보고]를 선택합니다.
![Visual Studio 개발자 커뮤니티의 문제 보고 팝업](media/installer.png)

1. **문제 신고**를 클릭하면 기본 브라우저가 열리고 Visual Studio에 로그인하는 데 사용하는 것과 동일한 계정으로 로그인됩니다.

   ![로그인하여 문제 보고](../ide/media/feedback-browser-top.png)

1. 먼저 버그 신고에 대한 설명이 포함된 제목을 입력합니다. 25자 이상이어야 합니다.

    ![문제 보고](../ide/media/feedback-report.png)

1. 입력하기 시작하면 가능한 중복 항목이 제목 필드에 표시됩니다.

    ![중복 항목 검색](../ide/media/feedback-search.png)

1. 가능한 중복 버그 신고를 선택하여 고유의 문제와 일치하는 항목이 있는지 확인합니다. 일치 항목이 있는 경우 고유한 티켓을 생성하는 대신 투표합니다.

    ![중복 항목에 투표](../ide/media/feedback-duplicate.png)

2. 중복 항목이 발견되지 않는 경우 계속해서 문제에 대한 설명을 입력합니다. 버그를 재현할 수 있는 가능성을 높이기 위해 설명이 최대한 명확해야 합니다. 명확한 재현 단계를 포함해야 합니다.

3. 버그 신고와 관련이 있는 경우 ‘Include Visual Studio screenshot’(Visual Studio 스크린샷 포함) 확인란을 선택하여 화면을 캡처합니다.

    ![화면 캡처](../ide/media/feedback-screenshot.png) ‘Microsoft 엔지니어만 스크린샷을 볼 수 있음’

    브라우저에서 곧바로 스크린샷을 잘라 중요하거나 관련 없는 부분을 제거할 수도 있습니다.

4. Visual Studio 엔지니어링 팀이 문제를 해결하는 데 도움을 주는 최상의 방법 중 하나는 팀이 살펴볼 수 있도록 추적 및 힙 덤프 파일을 제공하는 것입니다. 버그를 야기한 단계를 기록하면 쉽게 도울 수 있습니다. 

    ![작업 기록](../ide/media/feedback-recording.png) ‘Microsoft 엔지니어만 기록을 볼 수 있음’

5. 첨부된 파일을 검토하고 문제를 진단하는 데 도움이 된다고 판단되는 경우 추가 파일을 업로드합니다.   

    ![첨부된 파일](../ide/media/feedback-attachments.png) ‘Microsoft 엔지니어만 첨부 파일을 볼 수 있음’

6. 마지막 단계는 **제출** 단추를 누르는 것입니다. 신고서를 제출하면 심사 대기 중인 내부 Visual Studio 버그 신고 시스템으로 직접 전송됩니다.

## <a name="when-further-information-is-needed"></a>추가 정보가 필요한 경우

이슈에 중요한 정보가 누락된 경우 ‘추가 정보 필요’ 상태가 할당됩니다. Microsoft는 필요한 특정 정보를 포함하여 이슈에 댓글을 추가하며 사용자는 전자 메일 알림을 받게 됩니다. 사용자가 7일 이내에 정보를 제공하지 않으면 미리 알림이 전송됩니다. 그 후에는 14일 동안 활동이 없을 경우 티켓을 닫습니다.

1. 전자 메일에 있는 문제 신고 링크를 따르거나 내 피드백으로 이동하여 **추가 정보 필요** 상태의 모든 신고를 확인합니다.

    ![내 피드백](../ide/media/feedback-my-feedback.png)

1. 문제 신고에서 추가 정보 제공 링크를 선택하면 새 화면으로 이동합니다. 여기에서 요청된 정보를 확인할 수 있습니다.

   ![내 피드백](../ide/media/feedback-need-more-info.png)

1. 주석, 첨부 파일 또는 기록 단계를 추가하여 자세한 정보를 제공할 수 있습니다. 이 환경은 문제에 투표하는 경우 새 문제 보고하거나 추가 정보를 제공하는 작업과 비슷합니다.

1. 요청한 Microsoft 엔지니어는 제공된 추가 정보에 대한 알림을 받습니다. 조사하는 데 충분한 정보가 있으면 문제 상태를 변경합니다. 그렇지 않으면 엔지니어도 추가 정보를 요청합니다.

해당 요청은 **내 피드백** 화면에서 다른 모든 **문제** 및 **제안**에서 볼 수 있습니다.

## <a name="search-for-solutions-or-provide-feedback"></a>솔루션 검색 또는 피드백 제공

문제를 보고하는 데 Visual Studio를 사용하지 않으려고 하거나 사용할 수 없는 경우에는 [Visual Studio 개발자 커뮤니티](https://developercommunity.visualstudio.com/) 페이지에 이미 문제가 보고되고 솔루션이 게시되었을 수 있습니다.

신고할 문제가 없지만 기능을 제안하려는 경우 따로 위치가 정해져 있습니다. 자세한 내용은 [기능 제안](https://developercommunity.visualstudio.com/content/idea/post.html?space=8) 페이지를 참조하세요.

## <a name="see-also"></a>참조

* [Developer Community 지침](https://docs.microsoft.com/visualstudio/ide/developer-community-guidelines)
* [Visual Studio 피드백 옵션](../ide/feedback-options.md)
* [Mac용 Visual Studio의 문제 보고](/visualstudio/mac/report-a-problem)
* [C++를 사용하여 문제 보고](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio 개발자 커뮤니티](https://developercommunity.visualstudio.com/)
* [개발자 커뮤니티 데이터 개인 정보](developer-community-privacy.md)
