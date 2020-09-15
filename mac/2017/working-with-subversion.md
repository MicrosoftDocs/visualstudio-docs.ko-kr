---
title: Subversion 작업
description: Mac용 Visual Studio에서 Subversion 사용
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: bd46a9eba7770b73425f1461fab6cb8443ace26c
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402272"
---
# <a name="working-with-subversion"></a>Subversion 작업

Subversion은 중앙 데이터의 단일 주 복사본을 체크 아웃할 수 있는 중앙 버전 제어 시스템입니다. Subversion 리포지토리를 체크 아웃하면 Git과 달리 전체 리포지토리가 복제되지 않고 해당 시점의 스냅샷만 생성됩니다.

Subversion은 여러 사용자가 같은 리포지토리에서 동시에 작업할 수 있도록 복사-수정-병합 모델을 사용합니다. 즉, 각 사용자가 중앙 데이터의 로컬 또는 작업 복사본을 만들어 독립적으로 작업합니다. 사용자의 작업 복사본에 대한 변경 내용은 시간순으로 병합됩니다.

예를 들어 사용자 A와 사용자 B가 모두 원격 리포지토리에서 복사본을 체크 아웃하고 각각 파일을 수정한다고 가정해 보겠습니다. 사용자 A가 수정을 마치고 원격으로 커밋합니다. 사용자 B는 작업을 커밋하기 전에 원격 리포지토리의 변경 내용으로 작업 복사본을 업데이트하여 사용자 A의 변경 내용을 병합해야 합니다.

다음 섹션에서는 Mac용 Visual Studio의 버전 제어에 Subversion을 사용하는 방법을 살펴봅니다.

다음 이미지는 Mac용 Visual Studio의 버전 제어 메뉴 항목에서 제공하는 옵션을 보여줍니다.

![버전 제어 메뉴 항목](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>체크 아웃...

원격 Subversion 리포지토리를 사용하려면 리포지토리를 체크 아웃하여 로컬 컴퓨터에 해당 디렉터리의 작업 복사본을 만듭니다.

Mac용 Visual Studio에서 **체크 아웃** 기능을 사용하는 방법을 알아보려면 [Subversion 리포지토리 설정](set-up-subversion-repository.md) 섹션의 단계를 따르세요.

## <a name="update-solution"></a>솔루션 업데이트

원격 리포지토리를 사용할 때는 다른 사용자가 파일을 수정하여 내 작업 복사본이 이미 오래된 버전이 되었을 수 있다는 점에 주의해야 합니다. 따라서 충돌에 대비하여 작업을 시작하기 전이나 커밋하기 전에 리포지토리의 변경 내용을 내 솔루션으로 모두 풀하는 것이 좋습니다. 변경 내용을 풀하려면 **버전 제어 > 솔루션 업데이트** 메뉴 항목을 선택합니다.

## <a name="review-solution-and-commit"></a>솔루션 검토 및 커밋

파일의 변경 내용을 검토하려면 다음 이미지와 같이 각 문서의 [변경 내용], [책임], [로그] 및 [병합] 탭을 사용합니다.

![버전 제어 탭](media/version-control-vcTabs.png)

**버전 제어 > 솔루션 검토 및 커밋** 메뉴 항목을 탐색하여 프로젝트의 모든 변경 내용을 검토합니다.

![솔루션 검토](media/version-control-vcStatus.png)

이렇게 하면 프로젝트의 각 파일에 포함된 변경 내용을 모두 확인하면서 [되돌리기], [패치 만들기] 또는 [커밋] 옵션을 사용할 수 있습니다.

원격 리포지토리에 파일을 커밋하려면 [커밋...]을 누르고 커밋 메시지를 입력한 다음 커밋 단추를 클릭하여 확인합니다.

![파일 커밋](media/version-control-svnCommit.png)

이렇게 하면 변경 내용이 리포지토리에 전송되고 모든 수정 사항이 포함된 새 수정 버전이 생성됩니다.

## <a name="see-also"></a>참고 항목

- [Subversion 리포지토리 설정](set-up-subversion-repository.md)
