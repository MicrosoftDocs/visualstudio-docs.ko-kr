---
title: SharePoint 프로젝트 확장 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6bc92d65ed179c7f2cb2f569a7d254a025887845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967483"
---
# <a name="extend-sharepoint-projects"></a>SharePoint 프로젝트 확장
  SharePoint 프로젝트의 프로젝트 수준 기능을 사용자 지정 하려는 경우 프로젝트 확장을 만듭니다. 예를 들어 사용자 지정 프로젝트 속성을 추가 하거나 사용자가 Visual Studio에서 SharePoint 솔루션을 개발 하는 경우 발생 하는 프로젝트 수준 이벤트에 응답할 수 있습니다.

## <a name="create-project-extensions"></a>프로젝트 확장 만들기
 프로젝트 항목을 확장 하려면 인터페이스를 구현 하는 Visual Studio 확장 어셈블리를 빌드합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> . 자세한 내용은 [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)를 참조 하세요.

 프로젝트 확장을 만들 때 SharePoint 프로젝트에 다음 기능을 추가할 수도 있습니다.

- 바로 가기 메뉴 항목을 추가 합니다. 노드를 마우스 오른쪽 단추로 클릭 하거나 선택 하 고 **Shift**F10 키를 선택 하 여 **솔루션 탐색기** 에서 SharePoint 프로젝트 노드에 대 한 바로 가기 메뉴를 열면 메뉴 항목이 표시 됩니다 + **F10** . 자세한 내용은 [방법: SharePoint 프로젝트에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)를 참조 하세요.

- 사용자 지정 속성을 추가 합니다. 속성은 **솔루션 탐색기**에서 SharePoint 프로젝트를 선택 하면 **속성** 창에 표시 됩니다. 자세한 내용은 [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)를 참조 하세요.

  프로젝트 확장을 만들고, 배포 하 고, 테스트 하는 방법을 보여 주는 연습은 [연습: SharePoint 프로젝트 확장 만들기](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)를 참조 하세요.

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>프로젝트 확장과 프로젝트 인스턴스 간의 관계 이해
 프로젝트 확장을 만들 때에서 모든 종류의 SharePoint 프로젝트를 열 때 확장이 로드 됩니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에는 목록 정의, 콘텐츠 형식 및 이벤트 수신기와 같은 몇 가지 SharePoint 프로젝트 템플릿이 포함 되어 있습니다. 그러나 하나의 SharePoint 프로젝트 유형만 있습니다. **새 프로젝트** 대화 상자에 표시 되는 프로젝트 형식은 하나 이상의 SharePoint 프로젝트 항목을 함께 묶는 템플릿에만 해당 됩니다. SharePoint 프로젝트 형식이 하나 뿐 이기 때문에 한 프로젝트에 대해 생성 된 확장은 모든 SharePoint 프로젝트에 적용 됩니다. 예를 들어 **콘텐츠 형식** 프로젝트에만 적용 되는 확장을 만들 수는 없습니다.

 특정 프로젝트 인스턴스에 액세스 하려면 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 메서드 구현에서 *projectservice* 매개 변수의 이벤트 중 하나를 처리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 합니다. 예를 들어 SharePoint 프로젝트가 솔루션에 추가 되는 시기를 확인 하려면 이벤트를 처리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [방법: SharePoint 프로젝트에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [연습: SharePoint 프로젝트 확장 만들기](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
