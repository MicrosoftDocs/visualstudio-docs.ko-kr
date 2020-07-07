---
title: SharePoint에 대 한 사이트 정의 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f1a512218c3c1b7af179cfaba3e231a90941fe0
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015061"
---
# <a name="create-site-definitions-for-sharepoint"></a>SharePoint에 대 한 사이트 정의 만들기
  의 SharePoint 사이트 정의 프로젝트를 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 사용 하 여 새 sharepoint 사이트의 기반 역할을 하는 *사이트 정의*를 만들 수 있습니다. 이러한 정의는 SharePoint 사이트의 모양 및 동작을 결정 하는 것이 아니라 기본 콘텐츠와 기능을 결정 합니다. 정의에 미리 구성된 목록, 콘텐츠 형식, 이벤트 수신기, 이미지 및 기타 항목을 포함할 수 있습니다. SharePoint에는 블로그 등의 사이트 정의가 포함되어 있습니다. 블로그 사이트 정의를 기반으로 사이트를 만들 때 사이트에는 블로그 사이트에 필요한 목록, 웹 파트 및 기타 항목이 포함 됩니다.

 사이트 정의에 대 한 자세한 내용은 [사이트 템플릿 및 정의](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14))를 참조 하세요.

## <a name="site-definition-projects"></a>사이트 정의 프로젝트
 의 사이트 정의 프로젝트는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 사이트에 필요한 기본 파일만 제공 하며 기본 기능은 제공 하지 않습니다. 원하는 기능을 제공 하려면 파일 및 콘텐츠를 추가 해야 합니다. 필요한 파일을 만들고 추가 하 여 수동으로 사이트를 빌드할 수 있습니다.

## <a name="feature-stapling"></a>기능 스테이플링
 에서 사이트 정의를 만드는 경우의 장점 중 하나는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 자동으로 *기능 스테이플링*을 사용 한다는 것입니다. 기능 스테이플링은 사이트 정의 자체에 기능을 포함 하는 대신 사이트 정의에 기능을 연결 합니다. 이렇게 하면 원래 사이트 정의를 수정 하지 않고 사이트 정의를 사용 하 여 만든 모든 사이트에 기능을 추가할 수 있습니다. 자세한 내용은 [기능 스테이플링](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12))을 참조 하세요.

## <a name="site-definition-project-components"></a>사이트 정의 프로젝트 구성 요소
 사이트 정의 솔루션을 만들 때 다음과 같은 기본 파일이 해당 **sitedefinition** 노드에 추가 됩니다.

|파일 이름|Description|
|---------------|-----------------|
|*default.aspx*|새 SharePoint 사이트의 기본 ASPX 홈 페이지입니다.|
|*onet.xml*|새 사이트의 구성, 사이트 정의 템플릿의 구성 요소 및 기본 동작을 지정 합니다. 이러한 설정에는 사용 가능한 콘텐츠 형식, 기본 목록 보기, 문서 템플릿 파일 및 사이트에 포함 된 웹 파트와 같은 특성이 포함 될 수 있습니다. 기본적으로이 섹션에는 `Modules` SharePoint 사이트에 추가할 파일 및 구성 방법이 나열 되어 있습니다.|
|*webtemp_ \<SiteDefinitionName> .xml*|**새 SharePoint 사이트** 페이지의 **템플릿 선택** 섹션에 표시 되는 사이트 정의 구성을 지정 합니다.|

 기본적으로 모든 사이트 정의는 * \<drive:> Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* 폴더에 저장 됩니다. 각 사이트 정의에는 자체 하위 폴더가 있습니다.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[연습: 기본 사이트 정의 프로젝트 만들기](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|에서 기본 사이트 정의 프로젝트를 만드는 과정을 단계별로 안내 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다.|
|[방법: 사용자 지정 사이트 정의 및 구성 만들기](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|기존 사이트 정의를 복사한 다음 복사본을 수정 하 여 SharePoint에서 사용자 지정 사이트 정의를 만드는 방법에 대해 설명 합니다.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|**새 SharePoint 사이트** 페이지의 **템플릿 선택** 섹션에서 사용할 수 있는 사이트 정의를 지정 하는 원본 파일에 대해 설명 합니다.|
|[SharePoint 솔루션 지역화](../sharepoint/localizing-sharepoint-solutions.md)|전역 사용을 위해 SharePoint 솔루션을 준비 하는 방법을 설명 합니다.|
|[SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)|사용자가 수정할 수 있는 SharePoint 페이지의 일부를 만드는 방법을 설명 합니다.|
|[웹 파트 또는 응용 프로그램 페이지의 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|응용 프로그램 페이지 및 웹 파트에서 실행 되는 다시 사용할 수 있는 컨트롤을 만드는 방법을 설명 합니다.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|프로젝트에서 웹 페이지를 열 때 나타나는 디자이너를 사용 하는 방법을 설명 합니다.|
|[ASP.NET 웹 페이지 개요](/previous-versions/aspnet/428509ah(v=vs.100))|[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]웹 페이지 구조,에서 페이지를 처리 하는 방법 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 및 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 페이지에 XHTML 표준을 준수 하는 태그가 표시 되는 방법에 대 한 일반 정보를 제공 합니다.|
|[ASP.NET 웹 페이지 구문](/previous-versions/aspnet/k33801s3(v=vs.100))|ASP.NET 페이지를 구성 하는 태그 요소에 대해 설명 합니다.|
|[프로그래밍 ASP.NET 웹 페이지](/previous-versions/aspnet/0yt4zca8(v=vs.100))|페이지에서 이벤트 처리기를 만드는 방법과 클라이언트 스크립트를 사용 하는 방법에 대 한 정보를 제공 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 합니다.|
|[Windows SharePoint Services의 프로그래밍](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|에서 제공 하는 관리 되는 개체 모델을 사용 하는 방법에 대해 설명 합니다 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] .|

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
