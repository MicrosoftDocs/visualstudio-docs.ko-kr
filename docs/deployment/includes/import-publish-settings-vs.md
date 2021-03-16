---
ms.openlocfilehash: 94c2c733b631ef5e727c79a6e093bb224aec38c4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249804"
---

1. ASP.NET 프로젝트가 Visual Studio에서 열려 있는 컴퓨터에서 솔루션 탐색기의 프로젝트를 마우스 오른쪽 단추로 클릭하고, **게시** 를 선택합니다.

   게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. **신규** 또는 **새 프로필 만들기** 를 클릭합니다.

1. 프로필을 가져오는 옵션을 선택합니다.

   ::: moniker range=">=vs-2019"
   **게시** 대화 상자에서 **프로필 가져오기** 를 클릭합니다.
   ::: moniker-end
   ::: moniker range="vs-2017"
   **게시 대상 선택** 대화 상자에서 **프로필 가져오기** 를 선택합니다.
   ::: moniker-end

   ![게시 선택](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. 이전 섹션에서 만든 게시 설정 파일의 위치로 이동합니다.

1. **게시 설정 파일 가져오기** 대화 상자에서 이전 섹션에서 만든 프로필로 이동하고 선택한 다음, **열기** 를 클릭합니다.

   ::: moniker range=">=vs-2019"
   **마침** 을 클릭하여 게시 프로필을 저장하고, **게시** 를 클릭합니다.

   Visual Studio에서 배포 프로세스를 시작하고, 출력 창에서 진행률 및 결과를 표시합니다.

   배포 오류가 발생하는 경우 **편집** 을 클릭하여 설정을 편집합니다. 설정을 수정하고 **유효성 검사** 를 클릭하여 새 설정을 테스트합니다. 호스트 이름이 없으면 **서버** 및 **대상 URL** 필드에 호스트 이름 대신 IP 주소를 시도합니다.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio에서 배포 프로세스를 시작하고, 출력 창에서 진행률 및 결과를 표시합니다.

   배포 오류가 발생하는 경우 **설정** 을 클릭하여 설정을 편집합니다. 설정을 수정하고 **유효성 검사** 를 클릭하여 새 설정을 테스트합니다. 호스트 이름이 없으면 **서버** 및 **대상 URL** 필드에 호스트 이름 대신 IP 주소를 시도합니다.
   ::: moniker-end

   ![게시 도구에서 설정 편집](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
