---
title: '방법: SharePoint 프로젝트 항목 확장 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 345bfa49da4bf5d5b73fe1d3f209675fe2814de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015347"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>방법: SharePoint 프로젝트 항목 확장 만들기
  Visual Studio에 이미 설치 되어 있는 SharePoint 프로젝트 항목에 기능을 추가 하려는 경우 프로젝트 항목 확장을 만듭니다. 자세한 내용은 [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)을 참조 하세요.

### <a name="to-create-a-project-item-extension"></a>프로젝트 항목 확장을 만들려면

1. 클래스 라이브러리 프로젝트를 만듭니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    - VisualStudio

    - System.ComponentModel.Composition

3. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 인터페이스를 구현하는 클래스를 만듭니다.

4. 클래스에 다음 특성을 추가 합니다.

    - <xref:System.ComponentModel.Composition.ExportAttribute>. 이 특성을 사용 하면 Visual Studio에서 구현을 검색 하 고 로드할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> . <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>형식을 특성 생성자에 전달 합니다.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 프로젝트 항목 확장에서이 특성은 확장 하려는 프로젝트 항목을 식별 합니다. 프로젝트 항목의 ID를 특성 생성자에 전달 합니다. Visual Studio에 포함 된 프로젝트 항목의 Id 목록은 [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)을 참조 하세요.

5. 메서드 구현에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> *projectItemType* 매개 변수의 멤버를 사용 하 여 확장의 동작을 정의 합니다. 이 매개 변수는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 및 인터페이스에 정의 된 이벤트에 대 한 액세스를 제공 하는 개체입니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . 확장 하는 프로젝트 항목 형식의 특정 인스턴스에 액세스 하려면 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 및와 같은 이벤트를 처리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> 합니다.

## <a name="example"></a>예
 다음 코드 예제에서는 이벤트 수신기 프로젝트 항목에 대 한 간단한 확장을 만드는 방법을 보여 줍니다. 사용자가 SharePoint 프로젝트에 이벤트 수신기 프로젝트 항목을 추가할 때마다이 확장 프로그램은 **출력** 창과 **오류 목록** 창에 메시지를 기록 합니다.

 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]

 이 예제에서는 SharePoint 프로젝트 서비스를 사용 하 여 **출력** 창과 **오류 목록** 창에 메시지를 기록 합니다. 자세한 내용은 [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)을 참조 하세요.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요 합니다.

- VisualStudio

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
