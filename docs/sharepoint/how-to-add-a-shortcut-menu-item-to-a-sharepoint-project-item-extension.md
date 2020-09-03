---
title: SharePoint 프로젝트 항목 확장에 바로 가기 메뉴 항목 추가
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
ms.openlocfilehash: 5c0515fddc106418902cd2cca9fcba4c0e365da1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014861"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>방법: SharePoint 프로젝트 항목 확장에 바로 가기 메뉴 항목 추가
  프로젝트 항목 확장을 사용 하 여 기존 SharePoint 프로젝트 항목에 바로 가기 메뉴 항목을 추가할 수 있습니다. 메뉴 항목은 사용자가 **솔루션 탐색기**에서 프로젝트 항목을 마우스 오른쪽 단추로 클릭 하면 나타납니다.

 다음 단계에서는 프로젝트 항목 확장을 이미 만들었다고 가정 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)를 참조 하세요.

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>프로젝트 항목 확장에 바로 가기 메뉴 항목을 추가 하려면

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 구현 메서드에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> *projectItemType* 매개 변수의 이벤트를 처리 합니다.

2. 이벤트에 대 한 이벤트 처리기에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> 이벤트 인수 매개 변수의 또는 컬렉션에 새 개체를 추가 합니다.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>새 개체에 대 한 이벤트 처리기에서 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 사용자가 바로 가기 메뉴 항목을 클릭할 때 실행 하려는 작업을 수행 합니다.

## <a name="example"></a>예
 다음 코드 예제에서는 이벤트 수신기 프로젝트 항목에 바로 가기 메뉴 항목을 추가 하는 방법을 보여 줍니다. 사용자가 **솔루션 탐색기** 에서 프로젝트 항목을 마우스 오른쪽 단추로 클릭 하 고 **출력 창에 메시지 쓰기** 메뉴 항목을 클릭 하면 Visual Studio에서 **출력** 창에 메시지를 표시 합니다.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]

 이 예제에서는 SharePoint 프로젝트 서비스를 사용 하 여 **출력** 창에 메시지를 기록 합니다. 자세한 내용은 [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)을 참조 하세요.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 포함 된 클래스 라이브러리 프로젝트가 필요 합니다.

- VisualStudio

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: SharePoint 프로젝트 항목 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [방법: SharePoint 프로젝트 항목 확장에 속성 추가](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
