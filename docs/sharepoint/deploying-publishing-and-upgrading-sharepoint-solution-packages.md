---
title: SharePoint 솔루션 패키지 배포, 게시 & 업그레이드
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
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
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444972"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>SharePoint 솔루션 패키지 배포, 게시 및 업그레이드
  Visual Studio에서 SharePoint 솔루션을 개발한 후 패키지(.wsp) 파일을 로컬 SharePoint 서버에 배포하거나 원격 또는 로컬 SharePoint 서버에 게시할 수 있습니다. 파일을 배포하는 경우 패키지 파일(.wsp)이 배포되는 방법을 사용자 지정할 수 있습니다.

> [!NOTE]
> 현재 는 샌드박스된 솔루션만 원격 SharePoint 서버에 게시할 수 있습니다. 자세한 내용은 [샌드박스 솔루션 고려 사항을](../sharepoint/sandboxed-solution-considerations.md)참조하십시오.

## <a name="deploy-publish-and-upgrade"></a>배포, 게시 및 업그레이드
 *배포는* Visual Studio의 SharePoint 프로젝트에서 로컬 호스트로 빌드된 SharePoint 솔루션 파일을 복사하는 것을 말합니다. 배포된 솔루션에서 IIS(인터넷 정보 서비스) 풀 재활용, 배포 후 솔루션 활성화 등과 같은 배포 단계를 구성할 수 있습니다. 배포하려면 **빌드** 메뉴에서 **배포** 명령을 사용합니다. 자세한 내용은 [SharePoint 배포 구성 편집](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) 방법 및 [공유점 배포 방법: 로컬 SharePoint 사이트에 SharePoint 솔루션을 배포하고 게시하는 방법을 참조하세요.](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)

 *게시는* 샌드박스된 SharePoint 솔루션 파일을 원격 SharePoint 사이트에 업로드하는 것을 말합니다. 즉, 다른 시스템에 있는 사이트입니다. SharePoint 샌드박스솔루션 파일을 로컬 SharePoint 사이트에 게시할 수도 있지만 게시된 사이트가 로컬 또는 원격 사이트인지 여부에 관계없이 배포 단계를 구성할 수 없습니다.

 *업그레이드는* 기존 원격 또는 로컬로 게시된 SharePoint 솔루션을 업데이트하는 것을 말합니다. Visual Studio의 SharePoint 솔루션을 변경한 후 솔루션의 패키지 파일 이름을 변경하고 솔루션을 다시 게시한 다음 성공적으로 다시 게시한 후 솔루션을 업그레이드합니다. 로컬로 게시된 솔루션을 다시 게시하는 경우 기존 솔루션 파일을 덮어쓸 수 있습니다.

## <a name="deploy-packages"></a>패키지 배포
 테스트 및 디버깅을 위해 개발 컴퓨터의 SharePoint 서버에 패키지 파일을 배포할 수 있습니다. 게시 **대화** 상자에서 파일 시스템 게시 옵션 단추를 선택하여 다른 컴퓨터에 **설치할** 수 있는 패키지 파일을 만들 수도 있습니다. 패키지가 만들어지고 지정된 로컬 파일 경로로 복사됩니다. 로컬 서버에 SharePoint 솔루션을 배포하려면 **빌드** 메뉴에서 **배포** 명령을 사용합니다. 자세한 내용은 [로컬 SharePoint 사이트에 SharePoint 솔루션을 배포하고 게시하는 방법을 참조하세요.](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)

 목록 정의를 배포하고, 이벤트 수신기를 추가하고, 기능 디자이너 및 패키지 디자이너를 사용하는 방법을 알아보려면 [연습: 프로젝트 작업 목록 정의 배포를](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)참조하십시오.

## <a name="customize-the-deployment-process"></a>배포 프로세스 사용자 지정
 다음 표에서는 SharePoint 솔루션을 디버깅하고 배포할 때 사용할 수 있는 두 가지 배포 구성을 보여 주십습니다.

|배포 구성|설명|
|------------------------------|-----------------|
|기본값|기본 배포 구성입니다. 다음 배포 단계가 수행됩니다.<br /><br /> 1. 배포 전 명령을 실행합니다.<br />2. IIS 응용 프로그램 풀을 재활용합니다.<br />3. 솔루션을 철회합니다.<br />4. 솔루션을 추가합니다.<br />5. 기능을 활성화합니다.<br />6. 배포 후 명령을 실행합니다.<br /><br /> 패키지를 제거하면 다음 철회 단계가 수행됩니다.<br /><br /> 1. IIS 응용 프로그램 풀을 재활용합니다.<br />2. 솔루션을 철회합니다.|
|정품 인증 없음|이 배포 구성은 기본 구성과 동일한 단계를 실행하지만 활성화 단계를 건너뜁니다.|

 고유한 배포 구성을 만들어 단일 단계를 완료하거나 배포 프로세스의 단계 순서를 변경할 수 있습니다. 자세한 내용은 [SharePoint 배포 구성 편집 방법을 참조하세요.](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)

 배포 전후에 실행할 명령을 추가할 수도 있습니다. 자세한 내용은 [SharePoint 배포 명령 설정 방법을](../sharepoint/how-to-set-sharepoint-deployment-commands.md)참조하십시오.

## <a name="publish-packages-to-a-remote-or-local-server"></a>원격 또는 로컬 서버에 패키지 게시
 sandboxed SharePoint 솔루션을 원격 서버에 게시하려면 메뉴 모음에서 **빌드**, **게시**를 선택한 다음 **게시** 대화 상자에서 SharePoint 사이트 게시 옵션 단추를 **선택하여** `https://someremoteserver.sharepoint.microsoftonline.com`원격 서버의 URL을 제공합니다.

 SharePoint 솔루션을 로컬 서버에 게시하려면 **게시** 대화 상자에서 파일 시스템 게시 옵션 **단추를 선택하여** 로컬 시스템 경로를 제공합니다.

 솔루션이 SharePoint에 성공적으로 게시되면 솔루션을 활성화할 수 있는 **솔루션 갤러리에** 표시됩니다. 자세한 내용은 [원격 서버에서 SharePoint 솔루션을 배포, 게시 및 업그레이드하는 방법을 참조하세요.](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)

### <a name="upgrade-published-packages"></a>게시된 패키지 업그레이드
 게시된 후 Visual Studio에서 SharePoint 프로젝트를 변경하는 경우 게시된 패키지를 업그레이드하여 변경 내용을 포함해야 합니다. 성공적으로 업그레이드하려면 패키지에 고유한 이름이 있어야 합니다. 기존 응용 프로그램을 업데이트할 때 발생할 수 있는 SharePoint 사이트에서 이름이 같은 패키지가 있는 경우 오류로 인해 파일 이름 충돌이 발생하고 패키지 이름을 바꿀 수 있습니다. 다시 게시된 후 새 패키지는 SharePoint 사이트에 표시되며 업그레이드할 수 있습니다. 업그레이드된 패키지는 이전 패키지의 데이터를 사용하여 솔루션을 업데이트한 다음 SharePoint에서 솔루션을 활성화합니다. 자세한 내용은 [원격 서버에서 SharePoint 솔루션을 배포, 게시 및 업그레이드하는 방법을 참조하세요.](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)

## <a name="see-also"></a>참조
- [SharePoint 솔루션 패키지 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
