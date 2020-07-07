---
title: '방법: 배포 단계가 실행 될 때 코드 실행 | Microsoft Docs'
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
ms.openlocfilehash: b2b0431ab4f985d801a78159fc2d324a29f8b638
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015536"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>방법: 배포 단계가 실행 될 때 코드 실행
  SharePoint 프로젝트의 배포 단계에 대 한 추가 작업을 수행 하려는 경우에는 Visual Studio에서 각 배포 단계를 실행 하기 전과 후에 SharePoint 프로젝트 항목에 의해 발생 하는 이벤트를 처리할 수 있습니다. 자세한 내용은 [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)을 참조 하세요.

### <a name="to-run-code-when-deployment-steps-are-executed"></a>배포 단계가 실행 될 때 코드를 실행 하려면

1. 프로젝트 항목 확장, 프로젝트 확장 또는 새 프로젝트 항목 형식의 정의를 만듭니다. 자세한 내용은 다음 항목을 참조하세요.

    - [방법: SharePoint 프로젝트 항목 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 확장에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 개체 (프로젝트 항목 확장명 또는 프로젝트 확장) 또는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 개체 (새 프로젝트 항목 형식 정의)의 및 이벤트를 처리 합니다.

3. 이벤트 처리기에서 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> 및 매개 변수를 사용 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> 하 여 배포 단계에 대 한 정보를 가져옵니다. 예를 들어, 실행 중인 배포 단계와 솔루션의 배포 또는 취소 여부를 확인할 수 있습니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 목록 인스턴스 프로젝트 항목에 대 한 확장에서 및 이벤트를 처리 하는 방법을 보여 줍니다. 이 확장은 Visual Studio에서 솔루션을 배포 하 고 취소 하는 동안 응용 프로그램 풀을 재생할 때 **출력** 창에 추가 메시지를 기록 합니다.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요 합니다.

- VisualStudio

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [연습: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [방법: SharePoint 프로젝트가 배포 되거나 취소 될 때 코드 실행](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
