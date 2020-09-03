---
title: 서버 탐색기에서 기본 제공 SharePoint 노드에 대 한 데이터 가져오기
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5bb69773bf3f031b75d63ebe8cb1f1b4a00286c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014893"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>방법: 서버 탐색기에서 기본 제공 SharePoint 노드에 대 한 데이터 가져오기
  **서버 탐색기**의 각 기본 제공 sharepoint 노드에 대해 노드가 나타내는 기본 sharepoint 구성 요소에 대 한 데이터를 가져올 수 있습니다. 자세한 내용은 [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)을 참조 하세요.

## <a name="example"></a>예
 다음 코드 예제에서는 목록 노드가 **서버 탐색기**에서 나타내는 기본 SharePoint 목록의 데이터를 가져오는 방법을 보여 줍니다. 기본적으로 목록 노드에는 웹 브라우저에서 목록을 열 때 클릭할 수 있는 **브라우저의 상황에** 맞는 메뉴 항목이 있습니다. 이 예제에서는 visual studio에서 직접 목록을 여는 visual Studio 상황에 맞는 메뉴 항목 **의 뷰** 를 추가 하 여 목록 노드를 확장 합니다. 이 코드는 노드의 목록 데이터에 액세스 하 여 Visual Studio에서 열 목록의 URL을 가져옵니다.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 이 예제에서는 SharePoint 프로젝트 서비스를 사용 하 여 <xref:EnvDTE.DTE> Visual Studio에서 목록을 여는 데 사용 되는 개체를 가져옵니다. SharePoint 프로젝트 서비스에 대 한 자세한 내용은 [sharepoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)을 참조 하세요.

 SharePoint 노드에 대 한 확장을 만드는 기본 작업에 대 한 자세한 내용은 [방법: sharepoint 노드 확장 서버 탐색기](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)을 참조 하세요.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요 합니다.

- EnvDTE

- VisualStudio

- VisualStudio. 확장명

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 **서버 탐색기** 확장을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
