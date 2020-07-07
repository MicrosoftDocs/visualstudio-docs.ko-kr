---
title: 로컬 SharePoint 사이트에 SharePoint 솔루션 게시 & 배포
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 59d4fe41565d0aaf0c52cae9434d4a576dc26baa
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016812"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>방법: 로컬 SharePoint 사이트에 SharePoint 솔루션 배포 및 게시
  개발 컴퓨터의 로컬 SharePoint 서버에 SharePoint 솔루션을 배포 하거나 게시할 수 있습니다. 배포 프로세스는 *.wsp* 파일을 SharePoint 서버에 복사 하 고, 솔루션을 설치한 후 기능을 활성화 합니다. 게시 프로세스는 *.wsp* 파일만 SharePoint 서버에 복사 하 고 설치 합니다. SharePoint에서 사용 하도록 설정 하려면 수동으로 활성화 해야 합니다.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>로컬 SharePoint 서버에 SharePoint 솔루션을 배포 하려면

1. **솔루션 탐색기**에서 배포 하려는 프로젝트를 선택 합니다.

2. 메뉴 모음에서 **빌드**, **솔루션 배포**를 선택 합니다.

     *.Wsp* 파일은 로컬 SharePoint 서버에 생성 및 설치 됩니다. 또한 기능이 활성화 됩니다.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>SharePoint 솔루션을 로컬 SharePoint 서버에 게시 하려면

1. **솔루션 탐색기**에서 게시 하려는 SharePoint 프로젝트에 대 한 바로 가기 메뉴를 연 다음 **게시**를 선택 합니다.

2. **게시** 대화 상자에서 **파일 시스템에 게시** 옵션 단추를 선택 합니다.

3. **대상 위치** 텍스트 상자에 로컬 경로를 입력 한 다음 **게시** 단추를 선택 합니다.

     게시 진행률이 Visual Studio **출력** 창에 표시 됩니다. 프로세스가 완료 되 면 솔루션 (*.wsp*) 파일이 로컬 SharePoint 서버에 설치 됩니다. 그러나 SharePoint에서 사용 하려면 아직 활성화 되어 있어야 합니다. 솔루션 파일이 이미 있으면 오류가 발생 하 고 기존 파일을 덮어쓸지 여부를 묻는 메시지가 표시 됩니다. 패키지 업그레이드에 대 한 자세한 내용은 [방법: 원격 서버에서 SharePoint 솔루션 배포, 게시 및 업그레이드](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)에서 원격 패키지 업그레이드 섹션을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [방법: 원격 서버에서 SharePoint 솔루션 배포, 게시 및 업그레이드](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [SharePoint 솔루션 패키지 만들기](../sharepoint/creating-sharepoint-solution-packages.md)
- [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [방법: 패키지 디자이너를 사용 하 여 패키지에 기능과 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
