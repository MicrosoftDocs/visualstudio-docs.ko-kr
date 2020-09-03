---
title: SharePoint 용 응용 프로그램 페이지 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 47f403f4eec6ec66563ae88bec226e073f625716
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72981107"
---
# <a name="create-application-pages-for-sharepoint"></a>SharePoint에 대 한 응용 프로그램 페이지 만들기
  *응용 프로그램 페이지* 는 SharePoint 웹 사이트에서 사용할 수 있도록 설계 된 ASP.NET 웹 페이지입니다. 응용 프로그램 페이지는 특수 한 유형의 ASP.NET 페이지입니다. 응용 프로그램 페이지와 표준 ASP.NET 페이지의 주요 차이점은 응용 프로그램 페이지에 SharePoint 마스터 페이지와 병합 된 콘텐츠가 포함 된다는 것입니다. 마스터 페이지를 사용 하면 응용 프로그램 페이지에서 사이트의 다른 페이지와 동일한 모양 및 동작을 공유할 수 있습니다.

 Visual Studio를 사용 하면 디자이너를 사용 하 여 응용 프로그램 페이지를 디자인할 수 있습니다. 디자이너에서 마스터 페이지에 정의 된 각 콘텐츠 자리 표시자에 대 한 콘텐츠 영역을 표시 합니다. 이러한 콘텐츠 영역으로 컨트롤을 끌어 응용 프로그램 페이지를 디자인할 수 있습니다.

## <a name="application-pages"></a>응용 프로그램 페이지
 응용 프로그램 페이지는 서버의 모든 사이트에서 공유 되지만 사이트 페이지는 한 사이트에만 적용 됩니다. 자세한 내용은 [SharePoint 페이지 형식](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14))을.

 기본적으로 SharePoint 사이트를 만들 때 표시 되는 대부분의 페이지는 사이트 페이지입니다. 사이트 페이지를 SharePoint 페이지 라이브러리에 추가할 수 있습니다. 사용자는 SharePoint 디자이너와 같은 도구를 사용 하 여 사이트 페이지를 사용자 지정할 수 있습니다. 사이트 페이지는 동적 웹 파트 및 웹 파트 영역과 같은 기능을 호스팅할 수도 있습니다.

 응용 프로그램 페이지는 이러한 작업을 수행할 수 없습니다. 그러나 페이지에 사용자 지정 코드를 포함 하려는 경우에는 응용 프로그램 페이지를 만드는 것이 가장 좋은 페이지 유형입니다. 사용자 지정 코드를 사이트 페이지에 추가할 수 있지만 사용자가 SharePoint 디자이너와 같은 도구를 사용 하 여 페이지를 사용자 지정 하는 경우 코드의 실행이 중지 됩니다.

> [!NOTE]
> Visual Studio에서는 SharePoint 사이트에 대 한 사이트 페이지를 만드는 데 도움이 되는 템플릿을 제공 하지 않습니다. 자세한 내용은 [SharePoint 페이지 형식](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14))을 참조 하세요.

## <a name="create-an-application-page"></a>응용 프로그램 페이지 만들기
 응용 프로그램 페이지를 만들려면 SharePoint 프로젝트에 **응용 프로그램 페이지** 항목을 추가 합니다. 응용 프로그램 페이지를 만들 때 Visual Studio는 프로젝트에 다음 폴더를 추가 합니다.

|폴더|Description|
|------------|-----------------|
|레이아웃|SharePoint 파일 시스템의 _layouts 가상 디렉터리에 매핑됩니다.|
|레이아웃 하위 폴더|응용 프로그램 페이지를 구성 하는 파일을 포함 합니다. 기본적으로이 폴더의 이름은 프로젝트와 동일 합니다. 언제 든 지이 폴더의 이름을 바꿀 수 있습니다. 프로젝트를 실행 하면 Visual Studio에서이 폴더를 SharePoint 파일 시스템의 _layouts 가상 디렉터리에 배포 합니다.|

 Visual Studio는 프로젝트에 다음 파일을 추가 합니다.

|파일|설명|
|----------|-----------------|
|ASP.NET 페이지 파일 (*.aspx*)|페이지를 정의 하는 XML 태그를 포함 합니다.|
|응용 프로그램 페이지 코드 파일|응용 프로그램 페이지의 코드를 포함 합니다. 이 파일에 대 한 이벤트를 처리 하는 코드를 추가 합니다.|
|응용 프로그램 페이지 디자이너 코드 파일|디자이너에서 생성 된 코드를 포함 합니다. 이 파일을 직접 편집 하지 마십시오.|

## <a name="design-and-debug-an-application-page"></a>응용 프로그램 페이지 디자인 및 디버그
 Visual Studio의 디자이너 뷰를 사용 하 여 응용 프로그램 페이지의 콘텐츠를 디자인 합니다. 이 디자이너는 프로젝트에서 응용 프로그램 페이지를 두 번 클릭 하거나 바로 가기 메뉴를 열고 **열기**를 선택 하 여 응용 프로그램 페이지를 연 다음 편집기 아래쪽에 있는 **디자인** 단추를 선택 하면 나타납니다.

> [!NOTE]
> 디자이너의 **소스** 뷰에서만 페이지를 디자인할 수 있습니다. 응용 프로그램 페이지에서는 디자이너의 **디자인** 뷰를 사용할 수 없습니다.

 Visual Studio에서 다른 SharePoint 프로젝트 항목을 디버그 하는 것 처럼 응용 프로그램 페이지를 디버그할 수 있습니다. Visual Studio 디버거를 시작 하면 Visual Studio에서 SharePoint 사이트를 엽니다.

 응용 프로그램 페이지를 보려면 응용 프로그램 페이지의 위치로 수동으로 이동 해야 합니다 (예: http://<em>Server_Name</em>/_layouts/*Project_Name*/applicationpage1.aspx).

 SharePoint 프로젝트를 디버깅 하는 방법에 대 한 자세한 내용은 [sharepoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)을 참조 하세요.

## <a name="choose-a-master-page"></a>마스터 페이지 선택
 기본적으로 **응용 프로그램 페이지** 항목은 프로젝트를 디버깅 하는 데 사용 하는 사이트의 마스터 페이지를 참조 합니다. 해당 페이지의 이름은 v4. 마스터 이며이 페이지는 SharePoint 사이트의 **마스터 페이지 갤러리** 에 나와 있습니다.

 응용 프로그램 페이지에서 사용 되는 마스터 페이지는 `MasterPageFile` 응용 프로그램 요소의 특성을 설정 하 여 명시적으로 변경할 수 있습니다 `Page` . (예: `MasterPageFile="~/_layouts/applicationv4.master"` ). SharePoint 서버에서 동적 마스터 페이지를 사용 하도록 설정 하지 않은 경우에는이 특성을 설정 해야 합니다. SharePoint의 마스터 페이지에 대 한 자세한 내용은 [마스터 페이지](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint Foundation 개발 심층 분석](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [ASP.NET 개요](/aspnet/overview)
- [ASP.NET 웹 페이지 2](/aspnet/web-pages/index)
