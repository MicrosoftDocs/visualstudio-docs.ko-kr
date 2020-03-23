---
title: Git 작업
description: Mac용 Visual Studio에서 Git 사용
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: 767c08505877391d71ca085097a0464d516f4f24
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70108018"
---
# <a name="working-with-git"></a>Git 작업

Git은 모든 팀원이 동일한 문서를 동시에 작업할 수 있는 분산형 버전 제어 시스템입니다. 즉, 모든 파일을 포함하는 중앙 서버가 있지만 이 중앙 소스에서 리포지토리를 체크 아웃하면 전체 리포지토리가 로컬 컴퓨터에 복제됩니다.

아래 섹션에서는 Mac용 Visual Studio의 버전 제어에 Git을 사용하는 방법을 살펴봅니다.

## <a name="git-version-control-menu"></a>Git 버전 제어 메뉴

아래 이미지는 Mac용 Visual Studio의 버전 제어 메뉴 항목에서 제공하는 옵션을 보여줍니다.

![버전 제어 메뉴 항목](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>푸시 및 풀

푸시 및 풀은 Git에서 가장 일반적으로 사용하는 두 가지 작업입니다. 다른 사용자가 원격 리포지토리에 적용한 변경 내용을 동기화하려면 원격 리포지토리에서 **풀**해야 합니다. Mac용 Visual Studio에서 이 작업을 수행하려면 **버전 제어 > 솔루션 업데이트**를 선택합니다.

파일을 업데이트하고 검토하여 커밋한 후에는 다른 사용자가 변경 내용에 액세스할 수 있도록 원격 리포지토리에 **푸시**해야 합니다. Mac용 Visual Studio에서 이 작업을 수행하려면 **버전 제어 > 변경 내용 푸시**를 선택합니다. 이렇게 하면 커밋된 변경 내용을 보면서 푸시할 분기를 선택할 수 있는 푸시 대화 상자가 표시됩니다.

![커밋할 분기를 보여주는 대화 상자](media/version-control-gitPush.png)

커밋 대화 상자를 통해 변경 내용을 커밋하는 동시에 푸시할 수도 있습니다.

![커밋과 동시에 푸시하는 방법을 보여주는 옵션](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>책임, 로그 및 병합

창 아래쪽에 아래 그림과 같이 다섯 개의 탭이 표시됩니다.

![버전 제어 탭](media/version-control-gitTabs.png)

다음과 같은 작업을 수행할 수 있습니다.

* **소스** - 소스 코드 파일을 표시합니다.
* **변경 내용** - 로컬 파일과 기본 파일 간의 코드 변경 내용을 표시합니다. 해시가 서로 다른 여러 파일 버전을 비교할 수도 있습니다.

    ![변경 내용 탭](media/version-control-gitChange.png)

* **책임** - 각 코드 섹션에 연결된 사용자 이름을 표시합니다.
* **로그** - 모든 커밋, 시간, 날짜, 메시지 및 파일을 담당하는 사용자를 표시합니다.

    ![로그 탭](media/version-control-gitLog.png)

* **병합** - 작업을 커밋할 때 병합 충돌이 발생한 경우에 사용할 수 있습니다. 두 코드 섹션을 깔끔하게 결합할 수 있도록 자신의 변경 내용과 다른 개발자의 변경 내용을 시각적으로 표현합니다.

## <a name="switching-branches"></a>분기 전환

기본적으로 리포지토리에서 가장 먼저 생성된 분기를 **마스터** 분기라고 합니다. 마스터 분기와 다른 분기 간에 기술적인 차이점은 없지만, 마스터 분기는 개발 팀에서 '라이브' 또는 '프로덕션' 분기로 간주되는 경우가 대부분입니다.

마스터 또는 기타 분기를 분기하여 독립적인 개발 라인을 만들 수 있습니다. 이렇게 하면 특정 시점을 기준으로 마스터 분기의 새 버전을 제공하여 '라이브' 분기와 독립적으로 개발할 수 있습니다. 소프트웨어 개발에서 형상을 관리할 때 이러한 방법으로 분기를 사용하는 경우가 많습니다.

사용자는 각 리포지토리에 대해 개수에 제한 없이 분기를 만들 수 있지만, 사용이 끝난 분기는 바로 삭제하여 리포지토리를 깔끔하게 정리하는 것이 좋습니다.

Mac용 Visual Studio에서 분기를 조회하려면 **버전 제어 > 분기 및 원격 관리...** 로 이동합니다.

![분기 보기](media/version-control-gitBranch2.png)

다른 분기로 전환하려면 목록에서 해당 분기를 선택하고 **분기로 전환** 단추를 누릅니다.

새 분기를 만들려면 Git 리포지토리 구성 대화 상자에서 **새로 만들기** 단추를 선택합니다. 새 분기 이름을 입력하세요.

![새 분기 만들기](media/version-control-gitBranch.png)

원격 분기를 _추적_ 분기로 설정할 수도 있습니다. 추적 분기에 대한 자세한 내용은 [Git 설명서](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches)를 참조하세요.

솔루션 패드에서 프로젝트 이름 옆에 표시된 현재 분기를 확인하세요.

 ![솔루션 패드에 표시된 현재 분기](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>검토 및 커밋

파일의 변경 내용을 검토하려면 이 항목의 앞에서 설명한 것처럼 각 문서의 [변경 내용], [책임], [로그] 및 [병합] 탭을 사용합니다.

**버전 제어 > 솔루션 검토 및 커밋** 메뉴 항목으로 이동하여 프로젝트의 모든 변경 내용을 검토합니다.

![코드 보기 검토](media/version-control-gitReviewCommit.png)

이렇게 하면 프로젝트의 각 파일에 포함된 변경 내용을 모두 확인하면서 [되돌리기], [패치 만들기] 또는 [커밋] 옵션을 사용할 수 있습니다.

원격 리포지토리에 파일을 커밋하려면 **커밋**을 누르고 커밋 메시지를 입력한 다음, 커밋 단추를 클릭하여 확인합니다.

![파일 커밋](media/version-control-gitCommit.png)

변경 내용을 커밋했으면 다른 사용자가 확인할 수 있도록 원격 리포지토리에 푸시합니다.

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>참고 항목

* [Visual Studio 2017 및 Azure Repos Git와 코드 공유](/azure/devops/repos/git/share-your-code-in-git-vs-2017)
