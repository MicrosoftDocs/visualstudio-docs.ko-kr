---
title: SharePoint 솔루션 빌드 및 디버깅 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e4b34df23c8cb612d72fed108a6c0aecbf57875c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016367"
---
# <a name="build-and-debug-sharepoint-solutions"></a>SharePoint 솔루션 빌드 및 디버그
  일반적으로 SharePoint 솔루션 빌드 및 디버깅은에서 다른 형식의 프로젝트를 빌드하고 디버깅 하는 것과 같습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 이 섹션의 항목에서는 차이점에 대해 설명합니다.

## <a name="project-output-for-sharepoint-solutions"></a>SharePoint 솔루션에 대 한 프로젝트 출력
 SharePoint 솔루션을 빌드하면 어셈블리 및 솔루션 패키지 (*.wsp*) 파일이 생성 됩니다. 다음 표에서는 빌드하는 동안 이러한 파일의 위치를 보여 줍니다.

|빌드 항목|출력 폴더|
|----------------|-------------------|
|어셈블리, 프로그램 데이터베이스 (*.pdb*) 및 *.wsp* 파일이 있습니다.|* \<ProjectName> \bin\debug* 또는 * \<ProjectName> \bin\release*|
|SharePoint 프로젝트 항목 파일입니다.|* \<ProjectName> \pkg\debug* 또는 * \<ProjectName> \pkg\release*|
|중간 파일을 빌드합니다.|* \<ProjectName> \obj\debug* * \<ProjectName> *|
|중간 파일을 패키지 합니다.|* \<ProjectName> \pkgobj\debug* 또는 * \<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>SharePoint 솔루션 빌드
 SharePoint 솔루션을 빌드하려면 개발 컴퓨터에 올바른 버전의 SharePoint server가 설치 되어 있어야 합니다. 그렇지 않으면에서 SharePoint 솔루션을 빌드하는 것은에서 다른 형식의 프로젝트를 빌드하는 것과 같습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 자세한 내용은 [방법: SharePoint 솔루션 빌드](../sharepoint/how-to-build-sharepoint-solutions.md)를 참조 하세요.

## <a name="debug-and-test-sharepoint-solutions"></a>SharePoint 솔루션 디버그 및 테스트
 디버깅 하기 전에는 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] *.wsp* 패키지를 SharePoint 서버에 복사 하 고, 사이트 및 웹 범위 기능을 활성화 하 고, 경우에 따라 프로젝트를 시작 합니다. 수동으로 프로젝트를 열어야 하는 경우도 있습니다. 자세한 내용은 [sharepoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md) 및 [sharepoint 솔루션 디버그](../sharepoint/debugging-sharepoint-solutions.md)를 참조 하세요.

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Azure DevOps Services 기능을 사용 하 여 SharePoint 솔루션 디버그 및 확인
 단위 테스트 및 IntelliTrace와 같은 Azure DevOps Services 기능을 사용 하면 SharePoint 솔루션에서 보다 정확 하 게 문제를 찾아낼 수 있습니다. 프로파일링을 통해 SharePoint 솔루션에서 성능 문제 영역을 찾고 식별할 수 있습니다. 자세한 내용은 sharepoint [코드 확인 및 디버깅](../sharepoint/verifying-and-debugging-sharepoint-code.md) 및 [sharepoint 응용 프로그램의 성능 프로 파일링](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)을 참조 하세요.

## <a name="security-during-the-build-process"></a>빌드 프로세스 중 보안
 SharePoint 솔루션을 패키지 하거나 배포 하려면에 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sharepoint 서버에 파일을 복사할 수 있는 권한이 있어야 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]관리자 권한으로를 실행 해야 하며 사용자 계정은 SharePoint 서버에서 사이트 모음 관리자 여야 합니다. 또한 프로젝트가 샌드박스가 적용 된 솔루션 인지 또는 팜 솔루션 인지를 지정 해야 합니다. 자세한 내용은 [샌드박스 솔루션과 팜 솔루션의 차이점](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)을 참조 하세요.

## <a name="using-the-clean-command"></a>정리 명령 사용
 Sharepoint 솔루션을 디버깅을 위해 SharePoint 서버에 설치 하는 경우에는 **Clean** 명령이 솔루션을 제거 하지 않습니다. 대신 SharePoint 구성을 통해 기능을 비활성화 해야 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [서버 탐색기를 사용 하 여 SharePoint 연결 찾아보기](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
