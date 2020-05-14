---
title: 버전 제어
description: Mac용 Visual Studio에서 Git 및 Subversion 사용
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 9206ab892ef125706ab16f9a739fe88a52f5c242
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70108106"
---
# <a name="version-control"></a>버전 제어

버전 제어는 파일의 다양한 버전을 관리하는 시스템으로서, 소프트웨어 개발에서는 일반적으로 여러 개발자가 서로 다른 버전을 생성합니다. 모든 _VCS_(버전 제어 시스템)의 주목적은 모든 사용자가 동시에 코드베이스에서 작업할 수 있는 솔루션을 찾는 것입니다.

모든 버전 제어 시스템의 핵심에는 파일 서버와 비슷하게 다양한 파일의 중앙 데이터 저장소 역할을 하는 _리포지토리_가 있습니다. 그러나 리포지토리는 파일 서버와 달리 프로젝트의 전체 기록과 모든 수정 버전을 포함합니다.

중앙 데이터 저장소가 리포지토리 형태라면, 각 사용자에게 작업 가능한 로컬 데이터 저장소를 제공하는 것이 합리적입니다. 이를 _작업 복사본_이라고 합니다. Mac용 Visual Studio에서 작업 복사본은 컴퓨터의 다른 로컬 디렉터리와 동일하게 표시되므로 모든 파일을 읽고 쓸 수 있습니다. 그러나 Mac용 Visual Studio에는 버전 제어 시스템이 통합되어 있으므로 IDE 내에서 Subversion 및 Git을 사용할 수 있습니다.

Subversion은 중앙 집중화된 버전 제어 시스템이므로, 모든 파일과 수정 버전을 포함하는 단일 서버가 있으며 사용자는 여기에서 임의의 파일 버전을 체크 아웃할 수 있습니다. 원격 Subversion 리포지토리에서 파일을 체크 아웃하면 사용자는 해당 시점을 기준으로 리포지토리의 스냅샷을 가져옵니다.

Git은 모든 팀원이 동일한 문서를 동시에 작업할 수 있는 분산형 버전 제어 시스템입니다. Git을 사용하는 경우 모든 파일을 포함하는 단일 서버가 있더라도 이 중앙 소스에서 리포지토리를 체크 아웃할 때마다 리포지토리 전체가 로컬 컴퓨터에 복제됩니다.

## <a name="basic-concepts"></a>기본 개념

Mac용 Visual Studio는 Git 및 Subversion 버전 제어 시스템을 모두 지원합니다. 다음 문서에서는 Mac용 Visual Studio를 통해 Git 및 Subversion 리포지토리를 설정하는 방법 및 변경 내용 검토, 커밋, 푸시 등의 간단한 기능을 살펴봅니다.

* [Git 리포지토리 설정](set-up-git-repository.md)
* [Git 작업](working-with-git.md)
* [Subversion 리포지토리 설정](set-up-subversion-repository.md)
* [Subversion 작업](working-with-subversion.md)

## <a name="see-also"></a>참고 항목

* [Visual Studio의 버전 제어(Windows에서)](/visualstudio/version-control/)