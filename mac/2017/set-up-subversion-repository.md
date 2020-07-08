---
title: Subversion 리포지토리 설정
description: Mac용 Visual Studio에서 Subversion 사용
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.topic: how-to
ms.openlocfilehash: ae67bdd9a9dac8daed268105d830064fa6ef4cae
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950418"
---
# <a name="set-up-a-subversion-repository"></a>Subversion 리포지토리 설정

Subversion은 중앙 집중화된 _버전 제어 시스템_이므로, 모든 파일과 수정 버전을 포함하는 단일 서버가 있으며 사용자는 여기에서 임의의 파일 버전을 체크 아웃할 수 있습니다. 원격 Subversion 리포지토리에서 파일을 체크 아웃하면 사용자는 해당 시점을 기준으로 리포지토리의 스냅샷을 가져옵니다.

버전 제어를 위해 Subversion을 사용하려면 Subversion이 컴퓨터에 설치되어 있어야 합니다. 컴퓨터에 Subversion이 설치되어 있는지 확인하려면 터미널에서 다음 명령을 사용합니다.

```bash
svn --version
```

이 명령은 버전 번호를 반환합니다.

Subversion이 아직 설치되어 있지 않은 경우 Subversion을 받는 가장 쉬운 방법은 _Xcode 명령줄 도구_를 설치하는 것입니다. 아래 명령을 사용하여 Xcode 명령줄 도구 및 Subversion을 설치합니다.

```bash
xcode-select --install
```

Subversion이 컴퓨터에 설치되면 SVN에서 다음 단계를 사용하여 프로젝트를 게시합니다.

1. 온라인으로 무료 SVN 리포지토리를 만듭니다. 이 예제에서는 [Assembla](https://app.assembla.com/)를 사용했습니다. 리포지토리가 만들어지면 연결에 사용되는 URL이 제공됩니다.

    ![SVN URL 복사](media/version-control-subversion1-sml.png)

2. Mac용 Visual Studio 프로젝트를 열거나 만듭니다.

3. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **버전 제어 > 버전 제어에서 게시...** 를 선택합니다.

    ![프로젝트 게시 시작](media/version-control-subversion2.png)

4. **리포지토리에 연결** 탭의 상단 드롭다운에서 **Subversion**을 선택합니다.

5. 1단계에서 제공된 URL을 입력합니다. URL이 입력되면 다른 필드는 기본적으로 채워집니다.

    ![리포지토리 선택 및 세부 정보 입력 대화 상자](media/version-control-subversion3.png)

7. **확인**을 클릭한 다음 **게시**를 눌러 확인합니다.

7. 아래 그림과 같은 메시지가 표시되면 리포지토리를 만든 사이트에 대한 자격 증명을 입력합니다.

    ![Subversion 리포지토리에 대한 자격 증명 입력](media/version-control-subversion5.png)

8. 이제 사용할 수 있는 모든 버전 제어 명령이 버전 제어 메뉴에 표시됩니다.

## <a name="see-also"></a>참고 항목

- [Subversion 작업](working-with-subversion.md)