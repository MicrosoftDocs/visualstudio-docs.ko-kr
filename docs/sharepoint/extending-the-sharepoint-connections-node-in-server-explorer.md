---
title: 서버 탐색기에서 SharePoint 연결 노드 확장 Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6615e02d84e1f252800597cb37666557e3c3fee6
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584609"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>서버 탐색기의 SharePoint 연결 노드 확장
  Visual Studio에서는 **서버 탐색기** 창의 **SharePoint 연결** 노드를 사용 하 여 개발 컴퓨터의 로컬 SharePoint 사이트에 연결할 수 있습니다. 이 노드에는 로컬 SharePoint 사이트의 여러 구성 요소가 계층적 트리 보기로 표시 됩니다. 예를 들어 로컬 사이트의 목록, 문서 라이브러리 및 콘텐츠 형식을 볼 수 있습니다. **서버 탐색기** 를 사용 하 여 로컬 SharePoint 사이트에 연결 하는 방법에 대 한 자세한 내용은 [서버 탐색기를 사용 하 여 SharePoint 연결 찾아보기](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)를 참조 하세요.

 기존 노드에 대 한 확장을 만들거나 사용자 지정 노드 유형을 만들어 노드 계층 구조에 추가 하 여 **SharePoint 연결** 노드를 확장할 수 있습니다.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>SharePoint 연결 노드 확장 작업
 기존 노드를 확장 하려면 인터페이스를 구현 하는 Visual Studio 확장을 만듭니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . 노드를 확장 하는 경우 사용자 지정 바로 가기 메뉴 항목 또는 사용자 지정 속성 등의 노드에 기능을 추가할 수 있습니다. 자세한 내용은 [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)을 참조 하세요.

 사용자 지정 노드 형식을 만들려면 인터페이스를 구현 하는 Visual Studio 확장을 만듭니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> . 기본적으로 **서버 탐색기** 에 표시 되지 않는 SharePoint 사이트의 구성 요소를 표시 하려면 사용자 지정 노드를 만듭니다. 예를 들어 **서버 탐색기** 는 기본적으로 SharePoint 사이트의 웹 파트 갤러리를 표시 하지 않지만이를 수행 하는 사용자 지정 노드를 추가할 수 있습니다. 자세한 내용은 [방법: 서버 탐색기에 사용자 지정 SharePoint 노드 추가](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) 및 [연습: 서버 탐색기를 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)를 참조 하세요.

## <a name="add-custom-properties-to-nodes"></a>노드에 사용자 지정 속성 추가
 노드를 확장 하거나 사용자 지정 노드 유형을 만들 때 노드에 사용자 지정 속성을 추가할 수 있습니다. 속성은 노드를 선택할 때 **속성** 창에 표시 됩니다.

 노드에 추가할 수 있는 사용자 지정 속성에는 두 가지 유형이 있습니다.

- SharePoint 사이트의 읽기 전용 데이터 집합을 표시 하는 속성입니다. 데이터는 노드가 나타내는 SharePoint 구성 요소를 설명 합니다. 이 작업을 수행 하는 방법을 보여 주는 연습은 [연습: 서버 탐색기 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)를 참조 하세요.

- 사용자 지정 읽기/쓰기 데이터를 표시 하는 속성입니다. 이 작업을 수행 하는 방법을 보여 주는 코드 예제는 [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)을 참조 하세요.

## <a name="get-data-for-built-in-nodes"></a>기본 제공 노드에 대 한 데이터 가져오기
 Visual Studio에서 제공 하는 모든 기본 제공 노드에는 표시 되는 SharePoint 구성 요소에 대 한 데이터가 포함 됩니다. 예를 들어 SharePoint 사이트의 목록을 나타내는 노드는 목록에 대 한 기본 보기의 제목 및 URL과 같은 일부 데이터를 목록에 제공 합니다.

 이 데이터에 액세스 하려면 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 관심 있는 노드를 나타내는 개체의 속성에서 데이터 개체를 검색 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 합니다. 데이터 개체의 유형은 노드의 유형에 따라 달라 집니다.

 다음 코드 예제에서는 목록 노드에 대 한 데이터 개체를 가져오는 방법을 보여 줍니다. 큰 예제의 컨텍스트에서이 예제를 보려면 [방법: 서버 탐색기에서 기본 제공 SharePoint 노드에 대 한 데이터 가져오기](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)를 참조 하세요.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]

 다음 표에서는 각 기본 제공 노드 형식에 대 한 데이터 개체 유형을 나열 합니다.

|노드 형식|데이터 개체 형식|
|---------------|----------------------|
|SharePoint 사이트 노드|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|내용 유형|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|기능|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|필드|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|목록|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|템플릿 목록|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|목록 뷰 (node.js)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|워크플로 연결|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|워크플로 템플릿|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 속성 사용에 대 한 자세한 내용은 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [연습: 서버 탐색기 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [방법: 서버 탐색기에 사용자 지정 SharePoint 노드 추가](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [방법: 서버 탐색기에서 기본 제공 SharePoint 노드에 대 한 데이터 가져오기](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [서버 탐색기를 사용하여 SharePoint 연결 찾아보기](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Visual Studio의 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
