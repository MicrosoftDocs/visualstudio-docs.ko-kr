---
title: '방법: 배포 충돌 처리 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df9677fd349825983cc33c5a8ed2648f34b8c9e
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015311"
---
# <a name="how-to-handle-deployment-conflicts"></a>방법: 배포 충돌 처리
  사용자 고유의 코드를 제공 하 여 SharePoint 프로젝트 항목의 배포 충돌을 처리할 수 있습니다. 예를 들어 현재 프로젝트 항목의 파일이 배포 위치에 이미 있는지 여부를 확인 한 다음 현재 프로젝트 항목을 배포 하기 전에 배포 된 파일을 삭제할 수 있습니다. 배포 충돌에 대 한 자세한 내용은 [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)을 참조 하세요.

### <a name="to-handle-a-deployment-conflict"></a>배포 충돌을 처리 하려면

1. 프로젝트 항목 확장, 프로젝트 확장 또는 새 프로젝트 항목 형식의 정의를 만듭니다. 자세한 내용은 다음 항목을 참조하세요.

    - [방법: SharePoint 프로젝트 항목 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 확장에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 개체 (프로젝트 항목 확장명 또는 프로젝트 확장) 또는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 개체 (새 프로젝트 항목 형식 정의)의 이벤트를 처리 합니다.

3. 이벤트 처리기에서 시나리오에 적용 되는 조건에 따라 배포 중인 프로젝트 항목과 SharePoint 사이트의 배포 된 솔루션 간에 충돌이 있는지 여부를 확인 합니다. <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A>이벤트 인수 매개 변수의 속성을 사용 하 여 배포 중인 프로젝트 항목을 분석할 수 있으며,이 목적을 위해 정의 하는 SharePoint 명령을 호출 하 여 배포 위치에서 파일을 분석할 수 있습니다.

     대부분의 충돌 유형에 대해 먼저 실행 중인 배포 단계를 확인할 수 있습니다. 이벤트 인수 매개 변수의 속성을 사용 하 여이 작업을 수행할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> . 일반적으로 기본 제공 배포 단계에서 충돌을 검색 하는 것은 좋지만 <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> 모든 배포 단계에서 충돌을 확인할 수 있습니다.

4. 충돌이 있는 경우 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> 이벤트 인수의 속성에 대 한 메서드를 사용 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> 하 여 새 개체를 만듭니다 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> . 이 개체는 배포 충돌을 나타냅니다. 메서드에 대 한 호출에서 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> 충돌을 해결 하기 위해 호출 되는 메서드도 지정 합니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 목록 정의 프로젝트 항목의 프로젝트 항목 확장에서 배포 충돌을 처리 하는 기본 프로세스를 보여 줍니다. 다른 형식의 프로젝트 항목에 대 한 배포 충돌을 처리 하려면 다른 문자열을에 전달 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 합니다. 자세한 내용은 [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)을 참조 하세요.

 간단히 하기 위해 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 이 예제의 이벤트 처리기는 배포 충돌이 발생 했다고 가정 합니다. 즉, 항상 새 개체를 추가 하 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 고 `Resolve` 메서드는 충돌이 해결 되었음을 나타내는 **true** 만 반환 합니다. 실제 시나리오에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 이벤트 처리기는 먼저 현재 프로젝트 항목의 파일과 배포 위치의 파일 사이에 충돌이 있는지 확인 한 다음 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 충돌이 있는 경우에만 개체를 추가 합니다. 예를 들어 `e.ProjectItem.Files` 이벤트 처리기에서 속성을 사용 하 여 프로젝트 항목의 파일을 분석할 수 있으며, SharePoint 명령을 호출 하 여 배포 위치에서 파일을 분석할 수 있습니다. 마찬가지로 실제 시나리오에서는 `Resolve` 메서드가 sharepoint 명령을 호출 하 여 sharepoint 사이트에서 충돌을 해결할 수 있습니다. SharePoint 명령을 만드는 방법에 대 한 자세한 내용은 [방법: sharepoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)를 참조 하세요.

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요 합니다.

- VisualStudio

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [방법: 배포 단계가 실행 될 때 코드 실행](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)
