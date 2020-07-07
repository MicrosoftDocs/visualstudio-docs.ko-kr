---
title: '방법: SharePoint 명령 실행 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 789b77f3161b5fe566ea033060e8cab16cbaecc7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016988"
---
# <a name="how-to-execute-a-sharepoint-command"></a>방법: SharePoint 명령 실행
  SharePoint 도구 확장에서 서버 개체 모델을 사용 하려면 API를 호출 하는 사용자 지정 *SharePoint 명령을* 만들어야 합니다. 명령을 정의 하 고 SharePoint 도구 확장을 사용 하 여 배포한 후에 확장은 명령을 실행 하 여 SharePoint 서버 개체 모델을 호출할 수 있습니다. 명령을 실행 하려면 개체의 ExecuteCommand 메서드 중 하나를 사용 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 합니다.

 SharePoint 명령의 용도에 대 한 자세한 내용은 [sharepoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)을 참조 하세요.

### <a name="to-execute-a-sharepoint-command"></a>SharePoint 명령을 실행 하려면

1. SharePoint 도구 확장에서 개체를 가져옵니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> . 개체를 가져오는 방법은 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 만드는 확장의 유형에 따라 달라 집니다.

    - SharePoint 프로젝트 시스템의 확장에서 속성을 사용 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> 합니다.

         프로젝트 시스템 확장에 대 한 자세한 내용은 [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)을 참조 하세요.

    - **서버 탐색기**의 **SharePoint 연결** 노드 확장에서 속성을 사용 합니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> . 개체를 가져오려면 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> 속성을 사용 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> 합니다.

         **서버 탐색기** 확장에 대 한 자세한 내용은 [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)을 참조 하세요.

    - 프로젝트 템플릿 마법사와 같은 SharePoint 도구의 확장에 포함 되지 않는 코드에서는 속성을 사용 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> 합니다.

         프로젝트 서비스를 검색 하는 방법에 대 한 자세한 내용은 [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)을 참조 하세요.

2. 개체의 ExecuteCommand 메서드 중 하나를 호출 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> . 실행 하려는 명령의 이름을 ExecuteCommand 메서드의 첫 번째 인수에 전달 합니다. 명령에 사용자 지정 매개 변수가 있는 경우 해당 매개 변수를 ExecuteCommand 메서드의 두 번째 인수로 전달 합니다.

     지원 되는 각 명령 서명에 대해 서로 다른 ExecuteCommand 오버 로드가 있습니다. 다음 표에서는 지원 되는 시그니처와 각 서명에 사용할 오버 로드를 보여 줍니다.

    |명령 서명|사용할 ExecuteCommand 오버 로드|
    |-----------------------|------------------------------------|
    |명령에는 기본 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수만 있고 반환 값은 없습니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |명령에는 기본 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수와 반환 값만 있습니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |명령에는 두 개의 매개 변수 (기본 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수와 사용자 지정 매개 변수)와 반환 값이 없습니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |명령에는 두 개의 매개 변수와 반환 값이 있습니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>예제
 다음 코드 예제에서는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> `Contoso.Commands.UpgradeSolution` [방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)에 설명 된 명령을 호출 하는 오버 로드를 사용 하는 방법을 보여 줍니다.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 `Execute`이 예제에 표시 된 메서드는 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> 사용자 지정 배포 단계에서 인터페이스의 메서드를 구현한 것입니다. 큰 예제의 컨텍스트에서이 코드를 보려면 [연습: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)를 참조 하세요.

 메서드에 대 한 호출에 대 한 다음 세부 정보를 확인 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> .

- 첫 번째 매개 변수는 호출 하려는 명령을 식별 합니다. 이 문자열은 명령 정의에서에 전달 하는 값과 일치 합니다 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> .

- 두 번째 매개 변수는 명령의 사용자 지정 두 번째 매개 변수에 전달 하려는 값입니다. 이 경우 SharePoint 사이트로 업그레이드 되는 *.wsp* 파일의 전체 경로입니다.

- 코드는 암시적 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수를 명령에 전달 하지 않습니다. 이 매개 변수는 SharePoint 프로젝트 시스템의 확장 또는 **서버 탐색기**의 **sharepoint 연결** 노드 확장에서 명령을 호출할 때 명령에 자동으로 전달 됩니다. 인터페이스를 구현 하는 프로젝트 템플릿 마법사와 같은 다른 형식의 솔루션에서는 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 이 매개 변수가 **null**입니다.

## <a name="compile-the-code"></a>코드 컴파일
 이 예에는 VisualStudio 어셈블리에 대 한 참조가 필요 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)
- [연습: 서버 탐색기 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
