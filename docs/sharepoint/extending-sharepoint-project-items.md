---
title: SharePoint 프로젝트 항목 확장 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: f60c95418379399196c461e055645ae7c85a473e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967398"
---
# <a name="extend-sharepoint-project-items"></a>SharePoint 프로젝트 항목 확장
  Visual Studio에 이미 설치 되어 있는 SharePoint 프로젝트 항목의 형식에 기능을 추가 하려는 경우 프로젝트 항목 확장을 만듭니다. 예를 들어 Visual Studio에서 기본 제공 **이벤트 수신기** 또는 **목록 정의** 프로젝트 항목에 대 한 확장을 만들거나 사용자 지정 프로젝트 항목 형식에 대 한 확장을 만들 수 있습니다. 모든 SharePoint 프로젝트 항목 형식에 대 한 확장을 만들 수도 있습니다.

## <a name="tasks-for-extending-sharepoint-project-items"></a>SharePoint 프로젝트 항목을 확장 하기 위한 작업
 프로젝트 항목을 확장 하려면 인터페이스를 구현 하는 Visual Studio 확장 어셈블리를 빌드합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> . 자세한 내용은 [방법: SharePoint 프로젝트 항목 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)를 참조 하세요.

 프로젝트 항목을 확장 하는 경우 프로젝트 항목에 다음 기능을 추가할 수도 있습니다.

- 프로젝트 항목에 바로 가기 메뉴 항목을 추가 합니다. 메뉴 항목은 **솔루션 탐색기**에서 프로젝트 항목에 대 한 바로 가기 메뉴를 열면 나타납니다. 프로젝트 항목을 마우스 오른쪽 단추로 클릭 하거나 선택 하 고 **Shift** + **F10** 키를 선택 하 여 바로 가기 메뉴를 엽니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 확장에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)를 참조 하세요.

- 프로젝트 항목에 사용자 지정 속성을 추가 합니다. 속성은 **솔루션 탐색기**에서 프로젝트 항목을 선택 하면 **속성** 창에 표시 됩니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 확장에 속성 추가](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)를 참조 하세요.

  프로젝트 항목 확장을 만들고, 배포 하 고, 테스트 하는 방법을 보여 주는 연습은 [연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)을 참조 하세요.

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>프로젝트 항목 확장과 프로젝트 항목 인스턴스 간의 관계 이해
 프로젝트 항목 확장을 만들 때 Visual Studio에서는 연결 된 형식의 프로젝트 항목이 SharePoint 프로젝트에 추가 될 때 확장을 로드 합니다. 예를 들어 **이벤트 수신기** 프로젝트 항목에 대 한 확장을 만드는 경우 사용자가 프로젝트에 **이벤트 수신기** 프로젝트 항목을 추가할 때 Visual Studio에서 확장을 로드 합니다. Visual Studio는 연결 된 프로젝트 항목 형식의 모든 인스턴스에 대해 확장의 동일한 인스턴스를 사용 합니다. 이전 예제에서 사용자가 두 번째 **이벤트 수신기** 프로젝트 항목을 프로젝트에 추가 하는 경우 동일한 확장 인스턴스를 사용 하 여 두 번째 프로젝트 항목을 사용자 지정 합니다.

 확장 하는 프로젝트 항목 형식의 특정 인스턴스에 액세스 하려면 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 메서드 구현에서 *projectItemType* 매개 변수의 이벤트 중 하나를 처리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 합니다. 예를 들어 확장 하는 형식의 프로젝트 항목이 프로젝트에 추가 되는 시기를 확인 하려면 이벤트를 처리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)를 참조 하세요.

## <a name="identifiers-for-sharepoint-project-items"></a>SharePoint 프로젝트 항목의 식별자
 각 SharePoint 프로젝트 항목에는 해당 문자열 식별자가 있습니다. 다음 작업을 수행 하려면 프로젝트 항목의 식별자를 알고 있어야 합니다.

- 프로젝트 항목의 확장명을 만듭니다. 이 경우 확장 하려는 프로젝트 항목의 식별자를의 생성자에 전달 해야 합니다 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . 모든 프로젝트 항목 형식에 대 한 확장을 만들려면 **\\** * 문자열 값을 전달 합니다.

- 프로젝트에 프로젝트 항목을 프로그래밍 방식으로 추가 합니다. 이 경우 프로젝트 항목의 식별자를 메서드에 전달 해야 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> .

  다음 표에서는 Visual Studio에 포함 된 SharePoint 프로젝트 항목의 식별자를 보여 줍니다.

|프로젝트 항목 이름|문자열 식별자|
|-----------------------|-----------------------|
|비즈니스 Data Catalog 모델|VisualStudio. BusinessDataConnectivity|
|콘텐츠 유형|VisualStudio.|
|이벤트 수신기|VisualStudio. EventHandler|
|빈 요소|VisualStudio 요소입니다.|
|목록 정의<br /><br /> 콘텐츠 형식의 목록 정의|VisualStudio. ListDefinition|
|목록 인스턴스|VisualStudio. ListInstance|
|모듈|VisualStudio.|
|순차적 워크플로<br /><br /> 정적 컴퓨터 워크플로|VisualStudio. 워크플로|
|사이트 정의|VisualStudio 정의입니다.|
|비주얼 웹 파트|VisualStudio. VisualWebPart|
|웹 파트|VisualStudio.|
|워크플로 연결 양식|VisualStudio를 연결 합니다.|

## <a name="see-also"></a>추가 정보
- [방법: SharePoint 프로젝트 항목 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [방법: SharePoint 프로젝트 항목 확장에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [방법: SharePoint 프로젝트 항목 확장에 속성 추가](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
