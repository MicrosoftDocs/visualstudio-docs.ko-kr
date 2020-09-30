---
title: SharePoint 도구 확장과 사용자 지정 데이터 연결 | Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 434f8aaf9303f3ee9a4008094b4e98c99d635e9f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584692"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>SharePoint 도구 확장과 사용자 지정 데이터 연결
  SharePoint 도구 확장의 특정 개체에 사용자 지정 데이터를 추가할 수 있습니다. 확장의 다른 코드에서 나중에 액세스 하려는 경우 확장의 한 부분에 데이터가 있는 경우 유용 합니다. 데이터를 저장 하 고 액세스 하는 사용자 지정 방법을 구현 하는 대신 데이터를 확장의 개체와 연결한 다음 나중에 동일한 개체에서 데이터를 검색할 수 있습니다.

 개체에 사용자 지정 데이터를 추가 하는 것은 Visual Studio의 특정 항목과 관련 된 데이터를 유지 하려는 경우에도 유용 합니다. SharePoint 도구 확장은 Visual Studio에서 한 번만 로드 되므로 확장은 언제 든 지 여러 다른 항목 (예: 프로젝트, 프로젝트 항목 또는 **서버 탐색기** 노드)에서 작동할 수 있습니다. 특정 항목에만 관련 된 사용자 지정 데이터가 있는 경우 해당 항목을 나타내는 개체에 데이터를 추가할 수 있습니다.

 SharePoint tools extensions의 개체에 사용자 지정 데이터를 추가 하면 데이터가 유지 되지 않습니다. 데이터는 개체의 수명 동안에만 사용할 수 있습니다. 가비지 수집에 의해 개체가 회수 되 면 데이터가 손실 됩니다.

 SharePoint 프로젝트 시스템의 확장에서 확장이 언로드된 후 유지 되는 문자열 데이터를 저장할 수도 있습니다. 자세한 내용은 [SharePoint 프로젝트 시스템의 확장에 데이터 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)을 참조 하세요.

## <a name="objects-that-can-contain-custom-data"></a>사용자 지정 데이터를 포함할 수 있는 개체
 인터페이스를 구현 하는 SharePoint tools 개체 모델의 개체에 사용자 지정 데이터를 추가할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> . 이 인터페이스는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 사용자 지정 데이터 개체의 컬렉션인 하나의 속성만 정의 합니다. 다음 형식은를 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> .

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>사용자 지정 데이터 추가 및 검색
 SharePoint 도구 확장의 개체에 사용자 지정 데이터를 추가 하려면 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 데이터를 추가 하려는 개체의 속성을 가져온 다음 메서드를 사용 <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> 하 여 개체에 데이터를 추가 합니다.

 SharePoint 도구 확장의 개체에서 사용자 지정 데이터를 검색 하려면 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 개체의 속성을 가져온 후 다음 방법 중 하나를 사용 합니다.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. 이 메서드는 데이터 개체가 있으면 **true** 를 반환 하 고, 없으면 **false** 를 반환 합니다. 이 메서드를 사용 하 여 값 형식 또는 참조 형식의 인스턴스를 검색할 수 있습니다.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. 이 메서드는 데이터 개체가 있으면 해당 개체를 반환 하 고, 없으면 **null** 을 반환 합니다. 참조 형식의 인스턴스를 검색 하는 데만이 메서드를 사용할 수 있습니다.

  다음 코드 예제에서는 특정 데이터 개체가 프로젝트 항목과 이미 연결 되어 있는지 여부를 확인 합니다. 데이터 개체가 프로젝트 항목과 아직 연결 되지 않은 경우 코드는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 프로젝트 항목의 속성에 개체를 추가 합니다. 큰 예제의 컨텍스트에서이 예제를 보려면 [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)를 참조 하세요.

  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]

## <a name="see-also"></a>참고 항목
- [SharePoint 도구 확장의 프로그래밍 개념 및 기능](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [연습: 웹 파트를 표시 하도록 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
