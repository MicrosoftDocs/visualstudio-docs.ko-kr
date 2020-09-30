---
title: '방법: 서버 탐색기에 사용자 지정 SharePoint 노드 추가 | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a74c9c879df57a5ff6444626870ee9f021fb4e9
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584887"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>방법: 서버 탐색기에 사용자 지정 SharePoint 노드 추가
  **서버 탐색기**의 **SharePoint 연결** 노드 아래에서 사용자 지정 노드를 추가할 수 있습니다. 이는 기본적으로 **서버 탐색기** 에 표시 되지 않는 추가 SharePoint 구성 요소를 표시 하려는 경우에 유용 합니다. 자세한 내용은 [서버 탐색기의 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)을 참조하세요.

 사용자 지정 노드를 추가 하려면 먼저 새 노드를 정의 하는 클래스를 만듭니다. 그런 다음 노드를 기존 노드의 자식으로 추가 하는 확장을 만듭니다.

### <a name="to-define-the-new-node"></a>새 노드를 정의 하려면

1. 클래스 라이브러리 프로젝트를 만듭니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    - VisualStudio

    - VisualStudio. 확장명

    - System.ComponentModel.Composition

    - System.Drawing

3. <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 인터페이스를 구현하는 클래스를 만듭니다.

4. 클래스에 다음 특성을 추가 합니다.

    - <xref:System.ComponentModel.Composition.ExportAttribute>. 이 특성을 사용 하면 Visual Studio에서 구현을 검색 하 고 로드할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> . <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>형식을 특성 생성자에 전달 합니다.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. 노드 정의에서이 특성은 새 노드에 대 한 문자열 식별자를 지정 합니다. *회사 이름*형식을 사용 하는 것이 좋습니다. *노드 이름* -모든 노드에 고유 식별자가 있는지 확인 합니다.

5. 메서드 구현에서 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> *typedefinition* 매개 변수의 멤버를 사용 하 여 새 노드의 동작을 구성 합니다. 이 매개 변수는 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> 인터페이스에 정의 된 이벤트에 대 한 액세스를 제공 하는 개체입니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> .

     다음 코드 예제에서는 새 노드를 정의 하는 방법을 보여 줍니다. 이 예에서는 프로젝트에 CustomChildNodeIcon 이라는 아이콘이 포함 리소스로 포함 되어 있다고 가정 합니다.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>새 노드를 기존 노드의 자식으로 추가 하려면

1. 노드 정의와 동일한 프로젝트에서 인터페이스를 구현 하는 클래스를 만듭니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> .

2. 클래스에 <xref:System.ComponentModel.Composition.ExportAttribute> 특성을 추가합니다. 이 특성을 사용 하면 Visual Studio에서 구현을 검색 하 고 로드할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>형식을 특성 생성자에 전달 합니다.

3. 클래스에 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 특성을 추가합니다. 노드 확장에서이 특성은 확장 하려는 노드 형식에 대 한 문자열 식별자를 지정 합니다.

     Visual Studio에서 제공 하는 기본 제공 노드 형식을 지정 하려면 다음 열거형 값 중 하나를 특성 생성자에 전달 합니다.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: 이러한 값을 사용 하 여 사이트 연결 노드 (사이트 Url을 표시 하는 노드), 사이트 노드 또는 **서버 탐색기**의 다른 모든 부모 노드를 지정 합니다.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: 이러한 값을 사용 하 여 목록, 필드 또는 콘텐츠 형식을 나타내는 노드와 같은 SharePoint 사이트의 개별 구성 요소를 나타내는 기본 제공 노드 중 하나를 지정 합니다.

4. 메서드 구현에서 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> 매개 변수의 이벤트를 처리 합니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> .

5. 이벤트 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> 처리기에서 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> 이벤트 인수 매개 변수에 의해 노출 되는 개체의 자식 노드 컬렉션에 새 노드를 추가 합니다.

     다음 코드 예제에서는 **서버 탐색기**에서 SharePoint 사이트 노드의 자식으로 새 노드를 추가 하는 방법을 보여 줍니다.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>전체 예제
 다음 코드 예제에서는 간단한 노드를 정의 하 고 **서버 탐색기**에 있는 SharePoint 사이트 노드의 자식으로 추가 하는 전체 코드를 제공 합니다.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>코드 컴파일
 이 예에서는 프로젝트에 CustomChildNodeIcon 이라는 아이콘이 포함 리소스로 포함 되어 있다고 가정 합니다. 이 예제에는 다음 어셈블리에 대 한 참조도 필요 합니다.

- VisualStudio

- System.ComponentModel.Composition

- System.Drawing

## <a name="deploy-the-extension"></a>확장 배포
 **서버 탐색기** 확장을 배포 하려면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [서버 탐색기의 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [연습: 서버 탐색기 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
