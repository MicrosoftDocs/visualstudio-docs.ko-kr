---
title: SharePoint 프로젝트 서비스 사용 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3aeee895810eed8e434fda93328e4e179c9d39
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740112"
---
# <a name="use-the-sharepoint-project-service"></a>SharePoint 프로젝트 서비스 사용
  SharePoint 프로젝트 시스템에는 프로젝트 시스템과 관련된 작업을 수행하는 데 사용할 수 있는 프로젝트 서비스가 포함되어 있습니다. 프로젝트 서비스는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 개체입니다.

 SharePoint 도구 확장에서 SharePoint 프로젝트 서비스에 액세스할 수 있습니다. 추가 기능, VSPackage 등의 다른 유형의 Visual Studio 확장에서도 SharePoint 프로젝트 서비스에 액세스할 수 있습니다. 자세한 내용은 [방법: SharePoint 프로젝트 서비스 검색](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)을 참조 하세요.

## <a name="project-service-features"></a>프로젝트 서비스 기능
 다음 표에는 SharePoint 프로젝트 서비스를 사용하여 수행할 수 있는 작업과 각 작업을 수행하는 데 사용할 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 메서드 또는 속성이 정리되어 있습니다.

|작업|사용할 멤버|
|----------|-------------------|
|Visual Studio에서 열려 있는 SharePoint 프로젝트에 액세스합니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> 속성|
|사용 가능한 모든 SharePoint 프로젝트 항목 형식(기본 제공 및 사용자 지정 프로젝트 항목 형식 포함)에 액세스합니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> 속성|
|SharePoint 프로젝트에서 사용 가능한 모든 배포 단계(기본 제공 및 사용자 지정 배포 단계 포함)에 액세스합니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> 속성|
|개발자가 SharePoint 프로젝트에서 코드를 리팩터링할 때 발생하는 이벤트에 액세스합니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> 속성|
|SharePoint 서버 개체 모델을 호출 하는 사용자 지정 *sharepoint 명령을* 실행 합니다. SharePoint 명령에 대 한 자세한 내용은 [sharepoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)을 참조 하세요.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> 속성|
|SharePoint 프로젝트 시스템의 형식과 Visual Studio 자동화 개체 모델 또는 통합 개체 모델의 형식을 상호 변환합니다. 자세한 내용은 [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)을 참조 하세요.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 메서드를 호출하여 생성됩니다.|
|Visual Studio의 **출력** 창 또는 **오류 목록** 창에 메시지를 씁니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> 속성|
|Visual Studio에서 사용할 수 있는 다른 서비스에 액세스합니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> 속성|
|솔루션 디버깅에 사용되는 로컬 SharePoint 사이트의 설치 폴더에 대한 경로를 검색합니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> 속성|
|[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 또는 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]이 컴퓨터에 설치되어 있는지 여부를 확인합니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> 속성|
|SharePoint 솔루션에 있는 기능이나 패키지의 유효성을 검사합니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> 속성|

## <a name="see-also"></a>추가 정보
- [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [방법: SharePoint 프로젝트 서비스 검색](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Visual Studio의 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint 도구 확장의 프로그래밍 모델 개요](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [방법: DTE 개체에서 서비스 가져오기](/previous-versions/bb166401(v=vs.140))