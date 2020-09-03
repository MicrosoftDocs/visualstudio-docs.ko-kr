---
title: '방법: SharePoint 프로젝트 서비스 검색 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f49883337c5748c0f8bcab5d0a88e02612e51b4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015552"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>방법: SharePoint 프로젝트 서비스 검색
  다음 유형의 솔루션에서 SharePoint 프로젝트 서비스에 액세스할 수 있습니다.

- 프로젝트 확장, 프로젝트 항목 확장 또는 프로젝트 항목 형식 정의와 같은 SharePoint 프로젝트 시스템의 확장입니다. 이러한 확장 형식에 대 한 자세한 내용은 [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)을 참조 하세요.

- **서버 탐색기**의 **SharePoint 연결** 노드 확장입니다. 이러한 확장 유형에 대 한 자세한 내용은 [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)을 참조 하세요.

- VSPackage 등의 다른 Visual Studio 확장 형식입니다.

## <a name="retrieve-the-service-in-project-system-extensions"></a>프로젝트 시스템 확장에서 서비스를 검색 합니다.
 SharePoint 프로젝트 시스템의 모든 확장에서 개체의 속성을 사용 하 여 프로젝트 서비스에 액세스할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> .

 다음 절차를 사용 하 여 프로젝트 서비스를 검색할 수도 있습니다.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>프로젝트 확장에서 서비스를 검색 하려면

1. 인터페이스 구현에서 메서드를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 찾습니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> .

2. *Projectservice* 매개 변수를 사용 하 여 서비스에 액세스 합니다.

     다음 코드 예제에서는 프로젝트 서비스를 사용 하 여 간단한 프로젝트 확장에서 **출력** 창 및 **오류 목록** 창에 메시지를 쓰는 방법을 보여 줍니다.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     프로젝트 확장을 만드는 방법에 대 한 자세한 내용은 [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)를 참조 하세요.

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>프로젝트 항목 확장에서 서비스를 검색 하려면

1. 인터페이스 구현에서 메서드를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 찾습니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> .

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> *ProjectItemType* 매개 변수의 속성을 사용 하 여 서비스를 검색 합니다.

     다음 코드 예제에서는 프로젝트 서비스를 사용 하 여 **목록 정의** 프로젝트 항목의 간단한 확장에서 **출력** 창 및 **오류 목록** 창에 메시지를 쓰는 방법을 보여 줍니다.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     프로젝트 항목 확장을 만드는 방법에 대 한 자세한 내용은 [방법: SharePoint 프로젝트 항목 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)를 참조 하세요.

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>프로젝트 항목 형식 정의에서 서비스를 검색 하려면

1. 인터페이스 구현에서 메서드를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 찾습니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> .

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> *Typedefinition* 매개 변수의 속성을 사용 하 여 서비스를 검색 합니다.

     다음 코드 예제에서는 프로젝트 서비스를 사용 하 여 간단한 프로젝트 항목 형식 정의에서 **출력** 창 및 **오류 목록** 창에 메시지를 쓰는 방법을 보여 줍니다.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     프로젝트 항목 형식을 정의 하는 방법에 대 한 자세한 내용은 [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)를 참조 하세요.

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>서버 탐색기 확장에서 서비스를 검색 합니다.
 **서버 탐색기**의 **SharePoint 연결** 노드 확장에서 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> 개체의 속성을 사용 하 여 프로젝트 서비스에 액세스할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> .

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>서버 탐색기 확장에서 서비스를 검색 하려면

1. <xref:System.IServiceProvider> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> 확장에 있는 개체의 속성에서 개체를 가져옵니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> .

2. 메서드를 사용 <xref:System.IServiceProvider.GetService%2A> 하 여 개체를 요청 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 합니다.

     다음 코드 예제에서는 프로젝트 서비스를 사용 하 여 확장 프로그램이 **서버 탐색기**의 목록 노드에 추가 하는 바로 가기 메뉴에서 **출력** 창 및 **오류 목록** 창에 메시지를 쓰는 방법을 보여 줍니다.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     **서버 탐색기**에서 **sharepoint 연결** 노드를 확장 하는 방법에 대 한 자세한 내용은 [방법: 서버 탐색기에서 sharepoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)을 참조 하세요.

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>다른 Visual Studio 확장에서 서비스 검색
 <xref:EnvDTE80.DTE2>인터페이스를 구현 하는 프로젝트 템플릿 마법사와 같이 자동화 개체 모델의 개체에 대 한 액세스 권한이 있는 Visual Studio 확장 또는 VSPackage에서 프로젝트 서비스를 검색할 수 있습니다 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

 VSPackage에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 다음 방법 중 하나를 사용 하 여 개체를 요청할 수 있습니다.

- <xref:System.IServiceProvider.GetService%2A>클래스에서 파생 되는 관리 되는 VSPackage의 메서드입니다 <xref:Microsoft.VisualStudio.Shell.Package> . 자세한 내용은 [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md)를 참조 하세요.

- 정적 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드입니다. 자세한 내용은 [GetGlobalService 사용](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice)을 참조 하세요.

  개체에 대 한 액세스 권한이 있는 Visual Studio 확장에서 개체 <xref:EnvDTE80.DTE2> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 의 메서드를 사용 하 여 개체를 요청할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> <xref:Microsoft.VisualStudio.Shell.ServiceProvider> . 자세한 내용은 [DTE 개체에서 서비스 가져오기](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)
- [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md)
- [방법: 프로젝트 템플릿에 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md)
