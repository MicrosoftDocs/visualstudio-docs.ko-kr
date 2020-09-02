---
title: 사용자 지정 SharePoint 프로젝트 항목 형식 정의 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e5f32abba4c4cbdeab59ed66e38019d913e704e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580786"
---
# <a name="define-custom-sharepoint-project-item-types"></a>사용자 지정 SharePoint 프로젝트 항목 형식 정의
  새 종류의 SharePoint 프로젝트 항목을 만들려는 경우 새 SharePoint 프로젝트 항목 형식을 정의 합니다. 예를 들어 SharePoint 사이트에 필드 또는 사용자 지정 작업을 추가 하기 위한 SharePoint 프로젝트 항목은 Visual Studio에 포함 되지 않습니다. 필드, 사용자 지정 작업 또는 다른 유형의 SharePoint 구성 요소를 만들기 위해 고유한 유형의 SharePoint 프로젝트 항목을 정의할 수 있습니다.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>SharePoint 프로젝트 항목 형식을 정의 하는 작업
 사용자 지정 프로젝트 항목 형식을 정의 하려면 인터페이스를 구현 하는 Visual Studio 확장 어셈블리를 빌드합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> . 자세한 내용은 [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)를 참조 하세요.

 사용자 지정 프로젝트 항목 형식을 정의 하는 경우 프로젝트 항목에 다음 기능을 추가할 수도 있습니다.

- 프로젝트 항목에 바로 가기 메뉴 항목을 추가 합니다. 메뉴 항목은 프로젝트 항목을 마우스 오른쪽 단추로 클릭 하거나 선택한 다음 **Shift**F10 키를 선택 하 여 **솔루션 탐색기** 에서 프로젝트 항목의 바로 가기 메뉴를 열 때 나타납니다 + **F10** . 자세한 내용은 [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)를 참조 하세요.

- 프로젝트 항목에 사용자 지정 속성을 추가 합니다. 속성은 **솔루션 탐색기**에서 프로젝트 항목을 선택 하면 **속성** 창에 표시 됩니다. 자세한 내용은 [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)를 참조 하세요.

  다른 개발자가 Visual Studio에서 프로젝트 항목을 사용할 수 있도록 하려면 .spdata 파일을 만들고 프로젝트 항목과 연결 된 항목 템플릿 또는 프로젝트 템플릿을 만듭니다. 자세한 내용은 [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)를 참조 하세요.

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>프로젝트 항목 형식과 프로젝트 항목 인스턴스 간의 관계 이해
 SharePoint 프로젝트 항목 형식을 정의 하는 경우 연결 된 형식의 프로젝트 항목이 SharePoint 프로젝트에 추가 될 때 Visual Studio에서 확장을 로드 합니다. 예를 들어 새 **사용자 지정 작업** 프로젝트 항목 형식을 정의 하는 경우 사용자가 프로젝트에 **사용자 지정 작업** 프로젝트 항목을 추가할 때 Visual Studio에서 확장을 로드 합니다. Visual Studio는 연결 된 프로젝트 항목 형식의 모든 인스턴스에 대해 확장의 동일한 인스턴스를 사용 합니다. 이전 예제에서 사용자가 두 번째 **사용자 지정 작업** 프로젝트 항목을 프로젝트에 추가 하는 경우 동일한 확장 인스턴스를 사용 하 여 두 번째 프로젝트 항목을 사용자 지정 합니다.

 프로젝트 항목 형식의 특정 인스턴스에 액세스 하려면 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 메서드 구현에서 *projectItemTypeDefinition* 매개 변수의 이벤트 중 하나를 처리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 합니다. 예를 들어 사용자 지정 형식의 프로젝트 항목이 프로젝트에 추가 되는 시기를 확인 하기 위해 이벤트를 처리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
