---
title: '방법: SharePoint 프로젝트 항목 형식 정의 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ae709bf2d81e2b8b00dc984602c0426fdf272ebd
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016853"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>방법: SharePoint 프로젝트 항목 형식 정의
  사용자 지정 SharePoint 프로젝트 항목을 만들려는 경우 프로젝트 항목 형식을 정의 합니다. 자세한 내용은 [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)를 참조 하세요.

### <a name="to-define-a-project-item-type"></a>프로젝트 항목 형식을 정의 하려면

1. 클래스 라이브러리 프로젝트를 만듭니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    - VisualStudio

    - System.ComponentModel.Composition

3. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 인터페이스를 구현하는 클래스를 만듭니다.

4. 클래스에 다음 특성을 추가 합니다.

    - <xref:System.ComponentModel.Composition.ExportAttribute>. 이 특성을 사용 하면 Visual Studio에서 구현을 검색 하 고 로드할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> . <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>형식을 특성 생성자에 전달 합니다.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 프로젝트 항목 형식 정의에서이 특성은 새 프로젝트 항목의 문자열 식별자를 지정 합니다. *회사 이름*형식을 사용 하는 것이 좋습니다. 모든 프로젝트 항목의 이름이 고유한 지 확인 하는 데 도움이 되는 *기능 이름* 입니다.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. 이 특성은 **솔루션 탐색기**에서이 프로젝트 항목에 대해 표시할 아이콘을 지정 합니다. 이 특성은 선택 사항입니다. 클래스에 적용 하지 않는 경우 Visual Studio에서 프로젝트 항목의 기본 아이콘을 표시 합니다. 이 특성을 설정 하는 경우 어셈블리에 포함 된 아이콘 또는 비트맵의 정규화 된 이름을 전달 합니다.

5. 메서드 구현에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> *projectItemTypeDefinition* 매개 변수의 멤버를 사용 하 여 프로젝트 항목 형식의 동작을 정의 합니다. 이 매개 변수는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 및 인터페이스에 정의 된 이벤트에 대 한 액세스를 제공 하는 개체입니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . 프로젝트 항목 형식의 특정 인스턴스에 액세스 하려면 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 및와 같은 이벤트를 처리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> 합니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 간단한 프로젝트 항목 형식을 정의 하는 방법을 보여 줍니다. 이 프로젝트 항목 형식은 사용자가이 형식의 프로젝트 항목을 프로젝트에 추가할 때 **출력** 창과 **오류 목록** 창에 메시지를 기록 합니다.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]

 이 예제에서는 SharePoint 프로젝트 서비스를 사용 하 여 **출력** 창과 **오류 목록** 창에 메시지를 기록 합니다. 자세한 내용은 [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)을 참조 하세요.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요 합니다.

- VisualStudio

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>프로젝트 항목 배포
 다른 개발자가 프로젝트 항목을 사용할 수 있도록 하려면 프로젝트 템플릿 또는 프로젝트 항목 템플릿을 만듭니다. 자세한 내용은 [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)를 참조 하세요.

 프로젝트 항목을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리, 템플릿 및 프로젝트 항목과 함께 배포할 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
