---
title: SharePoint 솔루션 패키지 배포, 게시 및 업그레이드 &
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444972"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>SharePoint 솔루션 패키지 배포, 게시 및 업그레이드
  Visual Studio에서 SharePoint 솔루션을 개발한 후에는 해당 패키지 (.wsp) 파일을 로컬 SharePoint 서버에 배포 하거나 원격 또는 로컬 SharePoint 서버에 게시할 수 있습니다. 파일을 배포 하는 경우 패키지 파일 (.wsp)을 배포 하는 방법을 사용자 지정할 수 있습니다.

> [!NOTE]
> 현재는 샌드박스가 적용 된 솔루션도 원격 SharePoint 서버에 게시할 수 있습니다. 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

## <a name="deploy-publish-and-upgrade"></a>배포, 게시 및 업그레이드
 *배포* 는 Visual Studio의 sharepoint 프로젝트에서 빌드된 sharepoint 솔루션 파일을 로컬 호스트로 복사 하는 것을 말합니다. 배포 된 솔루션에서는 인터넷 정보 서비스 (IIS) 풀을 재활용 하 고 배포 후 솔루션을 활성화 하는 등의 배포 단계를 구성할 수 있습니다. 배포 하려면 **빌드** 메뉴에서 **배포** 명령을 사용 합니다. 자세한 내용은 [방법: sharepoint 배포 구성 편집](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) 및 [방법: 로컬 SharePoint 사이트에 sharepoint 솔루션 배포 및 게시](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)를 참조 하세요.

 *게시* 는 샌드박스 sharepoint 솔루션 파일을 원격 sharepoint 사이트에 업로드 하는 것을 말합니다. 즉, 다른 시스템에 있는 사이트입니다. SharePoint 샌드 박싱된 솔루션 파일을 로컬 SharePoint 사이트에 게시할 수도 있지만에 게시 된 사이트가 로컬 또는 원격 인지에 관계 없이 해당 배포 단계를 구성할 수 없습니다.

 *업그레이드* 는 기존 원격 또는 로컬로 게시 된 SharePoint 솔루션을 업데이트 하는 것을 말합니다. Visual Studio에서 SharePoint 솔루션을 변경한 후에는 솔루션의 패키지 파일 이름을 변경 하 고, 솔루션을 다시 게시 한 후 다시 게시를 완료 한 후 솔루션을 업그레이드 합니다. 로컬로 게시 된 솔루션을 다시 게시 하는 경우 기존 솔루션 파일을 덮어쓸 수 있습니다.

## <a name="deploy-packages"></a>패키지 배포
 테스트 및 디버깅을 위해 패키지 파일을 개발 컴퓨터의 SharePoint 서버에 배포할 수 있습니다. **게시** 대화 상자에서 **파일 시스템에 게시** 옵션 단추를 선택 하 여 다른 컴퓨터에 설치할 수 있는 패키지 파일을 만들 수도 있습니다. 패키지가 만들어지고 지정 된 로컬 파일 경로에 복사 됩니다. SharePoint 솔루션을 로컬 서버에 배포 하려면 **빌드** 메뉴에서 **배포** 명령을 사용 합니다. 자세한 내용은 [방법: 로컬 sharepoint 사이트에 sharepoint 솔루션 배포 및 게시](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)를 참조 하세요.

 목록 정의를 배포 하 고, 이벤트 수신기를 추가 하 고, 기능 디자이너 및 패키지 디자이너를 사용 하는 방법을 알아보려면 [연습: 프로젝트 작업 목록 정의 배포](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)를 참조 하세요.

## <a name="customize-the-deployment-process"></a>배포 프로세스 사용자 지정
 다음 표에서는 SharePoint 솔루션을 디버그 하 고 배포할 때 사용할 수 있는 두 가지 배포 구성을 보여 줍니다.

|배포 구성|설명|
|------------------------------|-----------------|
|기본값|기본 배포 구성입니다. 다음 배포 단계가 수행 됩니다.<br /><br /> 1. 배포 전 명령을 실행 합니다.<br />2. IIS 응용 프로그램 풀을 재생 합니다.<br />3. 솔루션을 취소 합니다.<br />4. 솔루션을 추가 합니다.<br />5. 기능을 활성화 합니다.<br />6. 배포 후 명령을 실행 합니다.<br /><br /> 패키지를 제거 하면 다음과 같은 취소 단계가 수행 됩니다.<br /><br /> 1. IIS 응용 프로그램 풀을 재활용 합니다.<br />2. 솔루션을 취소 합니다.|
|정품 인증 안 함|이 배포 구성은 기본 구성과 동일한 단계를 실행 하지만 활성화 단계를 건너뜁니다.|

 배포 구성을 직접 만들어 단일 단계를 완료 하거나 배포 프로세스의 단계 순서를 변경할 수 있습니다. 자세한 내용은 [방법: SharePoint 배포 구성 편집](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)을 참조 하세요.

 배포 전후에 실행 되는 명령을 추가할 수도 있습니다. 자세한 내용은 [방법: SharePoint 배포 명령 설정](../sharepoint/how-to-set-sharepoint-deployment-commands.md)을 참조 하세요.

## <a name="publish-packages-to-a-remote-or-local-server"></a>원격 또는 로컬 서버에 패키지 게시
 샌드 박싱된 SharePoint 솔루션을 원격 서버에 게시 하려면 메뉴 모음에서 **빌드**, **게시**를 선택한 다음 **게시** 대화 상자에서 **SharePoint 사이트에 게시** 옵션 단추를 선택 하 여와 같은 원격 서버의 URL을 제공 `https://someremoteserver.sharepoint.microsoftonline.com` 합니다.

 SharePoint 솔루션을 로컬 서버에 게시 하려면 **게시** 대화 상자에서 **파일 시스템에 게시** 옵션 단추를 선택 하 여 로컬 시스템 경로를 제공 합니다.

 솔루션이 SharePoint에 성공적으로 게시 되 면 솔루션 **갤러리** 에서 솔루션을 활성화할 수 있는 솔루션을 표시 합니다. 자세한 내용은 [방법: 원격 서버에서 SharePoint 솔루션 배포, 게시 및 업그레이드](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)를 참조 하세요.

### <a name="upgrade-published-packages"></a>게시 된 패키지 업그레이드
 Visual Studio가 게시 된 후에 Visual Studio에서 SharePoint 프로젝트를 변경 하는 경우 게시 된 패키지를 업그레이드 하 여 변경 내용을 포함 해야 합니다. 성공적으로 업그레이드 하려면 패키지의 이름이 고유 해야 합니다. SharePoint 사이트에서 이름이 같은 패키지가 있으면 (기존 응용 프로그램을 업데이트할 때 발생할 수 있음) 오류가 발생 하면 파일 이름 충돌이 발생 하 여 패키지의 이름을 바꿀 수 있습니다. 다시 게시 한 후 새 패키지가 SharePoint 사이트에 표시 되 고 업그레이드할 수 있습니다. 업그레이드 된 패키지는 이전 패키지의 데이터를 사용 하 여 솔루션을 업데이트 한 다음 SharePoint에서 솔루션을 활성화 합니다. 자세한 내용은 [방법: 원격 서버에서 SharePoint 솔루션 배포, 게시 및 업그레이드](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)를 참조 하세요.

## <a name="see-also"></a>참조
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
