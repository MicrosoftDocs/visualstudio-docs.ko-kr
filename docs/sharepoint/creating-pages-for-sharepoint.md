---
title: SharePoint용 페이지 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 942891bc9281c07966160ea9df065408fcbfd5ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015172"
---
# <a name="create-pages-for-sharepoint"></a>SharePoint용 페이지 만들기
  SharePoint 사이트의 애플리케이션 페이지, 사이트 페이지, 마스터 페이지, 페이지 레이아웃을 만들 수 있습니다.

 Visual Studio에서 템플릿을 사용하여 애플리케이션 페이지를 만들 수 있습니다. SharePoint Designer를 사용하여 사이트 페이지, 마스터 페이지, 페이지 레이아웃을 만듭니다. 그런 다음, 해당 페이지를 Visual Studio로 가져와 SharePoint 프로젝트에서 사용할 수 있습니다.

 CSS 스타일시트, ECMAScript, 테마를 사용하여 페이지의 모양과 동작을 수정할 수도 있습니다.

## <a name="types-of-sharepoint-pages"></a>SharePoint 페이지 유형
 다음 표에서는 SharePoint 사이트에 포함된 네 가지 주요 유형의 페이지에 관해 설명합니다.

|페이지 유형|설명|
|---------------|-----------------|
|애플리케이션 페이지|페이지에 사용자 지정 코드를 포함하거나 페이지를 여러 사이트에서 공유하려는 경우 애플리케이션 페이지를 만듭니다. 그러지 않으면 사이트 페이지가 가장 적합할 수 있습니다.|
|사이트 페이지|다음 작업 중 하나를 수행하려는 경우 사이트 페이지를 만듭니다.<br /><br /> -   SharePoint 라이브러리에 페이지를 추가합니다.<br />-   동적 웹 파트 및 웹 파트 영역과 같은 기능을 호스트하는 페이지를 사용하도록 설정합니다.<br />-   사용자가 SharePoint Designer를 사용하여 페이지를 사용자 지정할 수 있도록 합니다.<br /><br /> 페이지에 사용자 지정 코드를 포함하려는 경우 사이트 페이지를 만들지 않습니다. 사이트 페이지에 사용자 지정 코드를 추가할 수는 있지만 사용자가 SharePoint Designer를 사용하여 페이지를 사용자 지정하면 코드 실행이 중지됩니다.|
|마스터 페이지|사이트 페이지와 애플리케이션 페이지의 공통 구조를 정의하려면 마스터 페이지를 만듭니다.|
|페이지 레이아웃|페이지 레이아웃은 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]에만 적용되며, 사이트 페이지와 애플리케이션 페이지의 공통 구조를 추가로 정의할 수 있습니다.|

 각 페이지 유형에 대한 개요는 [구성 요소: 페이지 및 사용자 인터페이스](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))와 [페이지 레이아웃 및 마스터 페이지](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14))를 참조하세요.

## <a name="create-application-pages"></a>애플리케이션 페이지 만들기
 SharePoint 프로젝트에 **애플리케이션 페이지** 항목을 추가하여 Visual Studio에서 애플리케이션 페이지를 만들 수 있습니다. 페이지에 컨트롤을 추가한 다음, 코드를 추가하여 컨트롤 이벤트를 처리할 수 있습니다.

 페이지의 코드 파일에서 중단점을 설정하고 디버거를 시작한 다음, 추가 구성 단계 없이 로컬 SharePoint 사이트에서 페이지를 테스트할 수 있습니다. 자세한 내용은 [SharePoint용 애플리케이션 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)를 참조하세요.

## <a name="create-site-pages-master-pages-and-page-layouts"></a>사이트 페이지, 마스터 페이지, 페이지 레이아웃 만들기
 SharePoint Designer를 사용하여 사이트 페이지, 마스터 페이지, 페이지 레이아웃을 만들 수 있습니다. 그런 다음, 해당 페이지를 Visual Studio로 가져올 수 있습니다. Visual Studio에서 사용할 수 있는 배포 또는 소스 제어 기능을 활용하려는 경우 페이지를 가져옵니다. 자세한 내용은 [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)를 참조하세요.

 해당 페이지를 가져온 후에는 수정하기 어렵기 때문에 페이지를 가져오기 전에 디자인해야 합니다.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>CSS 스타일시트, ECMAScript, 테마 만들기
 Visual Studio는 SharePoint 사이트의 CSS 스타일시트, ECMAScript(JavaScript, JScript) 또는 테마 파일을 개발하기 위한 템플릿을 제공하지 않습니다. 해당 파일은 SharePoint SDK에 제공된 지침을 사용하거나 SharePoint Designer와 같은 도구를 사용하여 만들 수 있습니다.

 솔루션에 파일을 직접 추가하거나 파일을 가져올 수 있습니다. 두 경우 모두, 추가하는 각 항목에 대해 매핑된 폴더를 만들어야 합니다. 매핑된 폴더를 만드는 방법에 대한 자세한 내용은 [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)를 참조하세요.

 CSS 스타일시트를 만드는 방법에 대한 자세한 내용은 [SharePoint Foundation의 CSS 스타일시트 클래스 사용](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14))을 참조하세요. SharePoint 솔루션의 JavaScript 및 JScript 파일을 만드는 방법에 대한 자세한 내용은 [ECMAScript의 기본 ASPX 페이지 설정](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14))을 참조하세요. 테마에 대한 자세한 내용은 [구성 요소: 페이지 및 사용자 인터페이스](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))를 참조하세요.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[SharePoint용 애플리케이션 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)|애플리케이션 페이지(SharePoint 마스터 페이지와 병합된 *.aspx* 콘텐츠)를 추가하는 방법을 설명합니다.|
|[방법: 애플리케이션 페이지 만들기](../sharepoint/how-to-create-an-application-page.md)|SharePoint 사이트에서 실행되는 ASP.NET 페이지를 만드는 방법을 보여 줍니다.|
|[연습: SharePoint 애플리케이션 페이지 만들기](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|SharePoint 사이트의 ASP.NET 웹 페이지를 디자인 및 디버그하는 방법을 보여 줍니다.|
