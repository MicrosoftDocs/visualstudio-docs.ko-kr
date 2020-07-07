---
title: SharePoint 프로젝트가 배포 되거나 취소 될 때 코드 실행
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5bd60c9d7b30d4620630d1f6752bd4c7e8bf1182
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016059"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>방법: SharePoint 프로젝트가 배포 되거나 취소 될 때 코드 실행
  SharePoint 프로젝트가 배포 되거나 취소 될 때 추가 작업을 수행 하려는 경우에는 Visual Studio에서 발생 하는 이벤트를 처리할 수 있습니다. 자세한 내용은 [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)을 참조 하세요.

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>SharePoint 프로젝트가 배포 되거나 취소 될 때 코드를 실행 하려면

1. 프로젝트 항목 확장, 프로젝트 확장 또는 새 프로젝트 항목 형식의 정의를 만듭니다. 자세한 내용은 다음 항목을 참조하세요.

   - [방법: SharePoint 프로젝트 항목 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 확장에서 개체에 액세스 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 서비스 검색](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)을 참조 하세요.

3. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> 프로젝트 서비스의 및 이벤트를 처리 합니다.

4. 이벤트 처리기에서 매개 변수를 사용 <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> 하 여 현재 배포 세션에 대 한 정보를 가져옵니다. 예를 들어 현재 배포 세션에 있는 프로젝트 및 배포 또는 취소 여부를 확인할 수 있습니다.

   다음 코드 예제에서는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> 프로젝트 확장에서 및 이벤트를 처리 하는 방법을 보여 줍니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> . 이 확장은 SharePoint 프로젝트에 대 한 배포가 시작 되 고 완료 되 면 **출력** 창에 추가 메시지를 기록 합니다.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요 합니다.

- VisualStudio

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [방법: 배포 단계가 실행 될 때 코드 실행](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
