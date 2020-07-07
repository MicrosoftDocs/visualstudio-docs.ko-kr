---
title: SharePoint에 대 한 페이지 만들기 | Microsoft Docs
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
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015172"
---
# <a name="create-pages-for-sharepoint"></a>SharePoint에 대 한 페이지 만들기
  SharePoint 사이트에 대 한 응용 프로그램 페이지, 사이트 페이지, 마스터 페이지 및 페이지 레이아웃을 만들 수 있습니다.

 Visual Studio에서 템플릿을 사용 하 여 응용 프로그램 페이지를 만들 수 있습니다. SharePoint Designer를 사용 하 여 사이트 페이지, 마스터 페이지 및 페이지 레이아웃을 만듭니다. 그런 다음 이러한 페이지를 Visual Studio로 가져와서 SharePoint 프로젝트에서 사용할 수 있습니다.

 Css 스타일 시트, ECMAScript 및 테마를 사용 하 여 페이지의 모양과 동작을 수정할 수도 있습니다.

## <a name="types-of-sharepoint-pages"></a>SharePoint 페이지 유형
 다음 표에서는 SharePoint 사이트에 포함 된 네 가지 주요 유형의 페이지에 대해 설명 합니다.

|페이지 유형|Description|
|---------------|-----------------|
|응용 프로그램 페이지|페이지에 사용자 지정 코드를 포함 하거나 페이지를 여러 사이트에서 공유 하려는 경우 응용 프로그램 페이지를 만듭니다. 그렇지 않으면 사이트 페이지가 가장 적합할 수 있습니다.|
|사이트 페이지|다음 작업 중 하나를 수행 하려는 경우 사이트 페이지를 만듭니다.<br /><br /> -SharePoint 라이브러리에 페이지를 추가 합니다.<br />-동적 웹 파트 및 웹 파트 영역과 같은 기능을 호스트 하는 페이지를 사용 하도록 설정 합니다.<br />-사용자가 SharePoint Designer를 사용 하 여 페이지를 사용자 지정할 수 있도록 합니다.<br /><br /> 페이지에 사용자 지정 코드를 포함 하려면 사이트 페이지를 만들지 마세요. 사용자 지정 코드를 사이트 페이지에 추가할 수 있지만 사용자가 SharePoint Designer를 사용 하 여 페이지를 사용자 지정할 때 코드의 실행이 중지 됩니다.|
|마스터 페이지|사이트 페이지 및 응용 프로그램 페이지에 대 한 공용 구조를 정의 하려면 마스터 페이지를 만듭니다.|
|페이지 레이아웃|페이지 레이아웃은에만 적용 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 되며 사이트 페이지 및 응용 프로그램 페이지의 공통 구조를 추가로 정의할 수 있습니다.|

 각 페이지 형식에 대 한 개요는 구성 요소 [: 페이지 및 사용자 인터페이스](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)), [페이지 레이아웃 및 마스터 페이지](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14))를 참조 하세요.

## <a name="create-application-pages"></a>응용 프로그램 페이지 만들기
 SharePoint 프로젝트에 **응용 프로그램 페이지** 항목을 추가 하 여 Visual Studio에서 응용 프로그램 페이지를 만들 수 있습니다. 페이지에 컨트롤을 추가한 다음 코드를 추가 하 여 컨트롤 이벤트를 처리할 수 있습니다.

 페이지의 코드 파일에서 중단점을 설정 하 고, 디버거를 시작 하 고, 추가 구성 단계를 수행 하지 않고 로컬 SharePoint 사이트에서 페이지를 테스트할 수 있습니다. 자세한 내용은 [SharePoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)를 참조 하세요.

## <a name="create-site-pages-master-pages-and-page-layouts"></a>사이트 페이지, 마스터 페이지 및 페이지 레이아웃 만들기
 SharePoint Designer를 사용 하 여 사이트 페이지, 마스터 페이지 및 페이지 레이아웃을 만들 수 있습니다. 그런 다음 이러한 페이지를 Visual Studio로 가져올 수 있습니다. Visual Studio에서 사용할 수 있는 배포 또는 소스 제어 기능을 활용 하려는 경우 페이지를 가져옵니다. 자세한 내용은 [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)를 참조 하세요.

 가져온 후에는 이러한 페이지를 수정 하기가 어렵기 때문에 페이지를 가져오기 전에 디자인 해야 합니다.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Css 스타일 시트, ECMAScript 및 테마 만들기
 Visual Studio는 SharePoint 사이트에 대 한 CSS (CSS 스타일시트), ECMAScript (JavaScript, JScript) 또는 테마 파일을 개발 하기 위한 템플릿을 제공 하지 않습니다. 이러한 파일은 SharePoint SDK에서 제공 되는 지침을 사용 하거나 SharePoint 디자이너와 같은 도구를 사용 하 여 만들 수 있습니다.

 이러한 파일을 솔루션에 직접 추가 하거나 가져올 수 있습니다. 두 경우 모두 추가 하는 각 항목에 대해 적절 한 매핑된 폴더를 만들어야 합니다. 매핑된 폴더를 만드는 방법에 대 한 자세한 내용은 [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)를 참조 하세요.

 CSS 스타일시트를 만드는 방법에 대 한 자세한 내용은 [SharePoint Foundation의 클래스 사용 CSS 스타일시트](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14))을 참조 하세요. SharePoint 솔루션용 JavaScript 및 JScript 파일을 만드는 방법에 대 한 자세한 내용은 [ECMAScript의 기본 ASPX 페이지 설정](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14))을 참조 하십시오. 테마에 대 한 자세한 내용은 [구성 요소: 페이지 및 사용자 인터페이스](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))를 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[SharePoint에 대 한 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)|응용 프로그램 페이지를 추가 하는 방법에 대해 설명 합니다. *.aspx* 콘텐츠는 SharePoint 마스터 페이지와 병합 됩니다.|
|[방법: 응용 프로그램 페이지 만들기](../sharepoint/how-to-create-an-application-page.md)|SharePoint 사이트에서 실행 되는 ASP.NET 페이지를 만드는 방법을 보여 줍니다.|
|[연습: SharePoint 응용 프로그램 페이지 만들기](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|SharePoint 사이트에 대 한 ASP.NET 웹 페이지를 디자인 하 고 디버그 하는 방법을 보여 줍니다.|
