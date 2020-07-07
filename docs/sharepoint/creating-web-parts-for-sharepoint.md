---
title: SharePoint에 대 한 웹 파트 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3825ef7d2c1c90f63a90f5028063c74332543841
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015046"
---
# <a name="create-web-parts-for-sharepoint"></a>SharePoint 용 웹 파트 만들기
  웹 파트를 사용 하면 브라우저를 사용 하 여 SharePoint 사이트 페이지의 콘텐츠, 모양 및 동작을 수정할 수 있습니다. 웹 파트는 웹 파트 페이지 내에서 실행 되는 서버 쪽 컨트롤이 며, SharePoint 사이트에 표시 되는 페이지의 빌딩 블록입니다. [문서 블록: 웹 파트](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))을 참조 하세요.

 Visual Studio의 템플릿을 사용 하 여 SharePoint 사이트에서 웹 파트를 만들고 디버그할 수 있습니다.

## <a name="create-a-web-part-in-visual-studio"></a>Visual Studio에서 웹 파트 만들기
 SharePoint 프로젝트에 **웹 파트** 항목을 추가 하 여 웹 파트를 만듭니다. 샌드박스 솔루션 또는 팜 솔루션에서 **웹 파트** 항목을 사용할 수 있습니다.

 디자이너를 사용 하 여 웹 파트를 시각적으로 디자인 하려면 **시각적 웹 파트** 프로젝트를 만들거나 **시각적 웹 파트** 항목을 SharePoint 프로젝트에 추가 합니다. 팜 솔루션의 **시각적 웹 파트** 항목만 사용할 수 있습니다.

### <a name="web-part-item"></a>웹 파트 항목
 **웹 파트** 항목은 SharePoint 사이트의 웹 파트를 디자인 하는 데 사용할 수 있는 파일을 제공 합니다. **웹 파트** 항목을 추가 하면 Visual Studio에서 프로젝트에 폴더를 만든 다음 여러 개의 파일을 폴더에 추가 합니다. 다음 표에서는 각 파일에 대해 설명 합니다.

|파일|Description|
|----------|-----------------|
|*Elements.xml*|프로젝트의 기능 정의 파일에서 웹 파트를 배포 하는 데 사용 하는 정보를 포함 합니다.|
|webpart 파일|SharePoint에서 웹 파트 갤러리에 웹 파트를 표시 해야 하는 정보를 제공 합니다.|
|코드 파일|웹 파트에 컨트롤을 추가 하 고 웹 파트 내에서 사용자 지정 콘텐츠를 생성 하는 메서드를 포함 합니다.|

 자세한 내용은 [방법: SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part.md)를 참조 하세요.

### <a name="visual-web-part-item"></a>시각적 웹 파트 항목
 비주얼 웹 파트는 visual Studio의 Visual Web Developer designer를 사용 하 여 만드는 웹 파트입니다. 시각적 웹 파트는 다른 웹 파트와 동일 하 게 작동 합니다. 단추 및 텍스트 상자와 같은 컨트롤을 웹 파트에 추가 하려면 XML 파일에 코드를 추가 합니다. 그러나 visual Studio **도구 상자**에서 웹 파트에 컨트롤을 끌어다 놓아 시각적 웹 파트에 컨트롤을 추가 합니다. 그런 다음 디자이너는 XML 파일에 필요한 코드를 생성 합니다. [방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기를](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)참조 하세요.

## <a name="sharepoint-controls"></a>SharePoint 컨트롤
 Visual Studio는 응용 프로그램 페이지와 같은 SharePoint 페이지를 만들기 위한 몇 가지 컨트롤을 제공 합니다. 이러한 컨트롤은 **SharePoint 컨트롤**의 **도구 상자** 에 나타납니다. 이러한 컨트롤의 기능은 SharePoint 사이트 및 목록 페이지에 사용 되는 ASP.NET 서버 컨트롤을 포함 하는 [WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) 네임 스페이스에서 파생 됩니다.

|컨트롤 이름|Description|
|------------------|-----------------|
|[기타 메뉴](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|ASP 메뉴를 삽입 합니다. 자세한 내용은 [Menu 컨트롤 개요](/previous-versions/ecs0x9w5(v=vs.140))를 참조 하세요.|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|*.Aspx* 페이지에 **링크** 요소를 삽입 하 고 **CssRegistration**로 정의 된 하나 이상의 외부 스타일 시트를 적용 합니다.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|*.Aspx* 페이지에 DateTime 컨트롤을 삽입 합니다.|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|.Aspx 페이지에 보안 유효성 검사를 삽입 *합니다.*|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|지정 된 목록의 속성을 반환 합니다.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|현재 웹 사이트의 전역 속성을 반환 합니다.|
|[.Rsslink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|RSS 피드에 대 한 링크를 *.aspx* 페이지에 삽입 합니다.|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|페이지에 스크립트와 같은 리소스를 등록 하는 속성과 메서드를 제공 하 여 페이지가 렌더링 될 때이를 요청할 수 있도록 합니다.|
|[테마](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|*.Aspx* 페이지에 테마를 적용 합니다.|

## <a name="debug-a-web-part"></a>웹 파트 디버그
 다른 Visual Studio 프로젝트를 디버깅할 때와 마찬가지로 웹 파트가 포함 된 SharePoint 프로젝트를 디버그할 수 있습니다. Visual Studio 디버거를 시작 하면 Visual Studio에서 SharePoint 사이트를 엽니다.

 코드 디버그를 시작 하려면 SharePoint의 웹 파트 페이지에 웹 파트를 추가 합니다.

 SharePoint 프로젝트를 디버깅 하는 방법에 대 한 자세한 내용은 [sharepoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)을 참조 하세요.

## <a name="visual-web-part-limitations"></a>비주얼 웹 파트 제한 사항
 Visual Studio를 시작 하 여 샌드 박싱된 SharePoint 솔루션 및 팜 솔루션에 비주얼 웹 파트를 추가할 수 있습니다. 그러나 시각적 웹 파트에는 다음과 같은 제한 사항이 있습니다.

- 시각적 웹 파트는 대체 가능 매개 변수를 지원 하지 않습니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)를 참조 하세요.

- 사용자 정의 컨트롤 또는 시각적 웹 파트는 비주얼 웹 파트로 끌어서 놓거나 복사할 수 없습니다. 이 작업을 수행 하면 빌드 오류가 발생 합니다.

- 시각적 웹 파트는 $SPUrl와 같은 SharePoint 서버 토큰을 직접 지원 하지 않습니다. 자세한 내용은 [SharePoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)항목의 "샌드박스 Visual 웹 파트의 토큰 제한 사항"을 참조 하세요.

- 샌드박스가 적용 된 솔루션의 시각적 웹 파트에는 "샌드 박싱된 코드 호스트 서비스 사용량이 너무 많아 요청을 처리할 수 없습니다." 오류가 발생 하는 경우가 있습니다. 이 오류에 대 한 자세한 내용은 [SharePoint 개발자 팀 블로그에서](https://blogs.msdn.microsoft.com/sharepointdev/2011/02/08/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham/#10149157)이 게시물을 참조 하십시오.

- 서버 쪽 JavaScript 디버깅은 Visual Studio에서 지원 되지 않지만 클라이언트 쪽 JavaScript 디버깅은 지원 됩니다.

   인라인 JavaScript를 서버 쪽 태그 파일에 추가할 수 있지만 태그에 추가 된 중단점에 대 한 디버깅은 지원 되지 않습니다. JavaScript를 디버깅 하려면 태그 파일에서 외부 JavaScript 파일을 참조 한 다음 JavaScript 파일에서 중단점을 설정 합니다.

- 인라인 코드의 디버깅은 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 태그 파일 대신 생성 된 코드 파일에서 수행 해야 합니다.

- 시각적 웹 파트는 지시문 사용을 지원 하지 않습니다 `<@ Assembly Src=` .

- Sharepoint 웹 컨트롤 및 일부 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 컨트롤은 sharepoint 샌드 박싱된 환경에서 지원 되지 않습니다. 샌드박스 솔루션의 시각적 웹 파트에서 지원 되지 않는 컨트롤을 사용 하는 경우 "' WebControls ' 네임 스페이스에 형식 또는 네임 스페이스 이름 ' 테마 '가 없습니다. 라는 오류가 나타납니다.

  샌드박스 솔루션에 대 한 자세한 내용은 [샌드박스 솔루션과 팜 솔루션의 차이점](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)을 참조 하세요.

## <a name="create-older-style-sharepoint-based-web-parts"></a>이전 스타일의 SharePoint 기반 웹 파트 만들기
 Visual Studio의 템플릿을 사용 하 여 SharePoint 용 사용자 지정 웹 파트를 만들 수 있습니다 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] . [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]웹 파트는 웹 파트 인프라를 기반으로 구축 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 되었으며 새 프로젝트에 권장 되는 형식입니다.

 경우에 따라 이전 스타일의 SharePoint 기반 웹 파트를 사용 하 여 웹 파트를 만들어야 할 수도 있습니다. Visual Studio를 사용 하 여 이러한 유형의 웹 파트를 만들 수 있지만 Visual Studio에서는 이러한 유형의 웹 파트를 만들 수 있도록 특별히 디자인 된 템플릿을 제공 하지 않습니다.

 이전 스타일의 SharePoint 기반 웹 파트를 만들 수 있는 경우에 대 한 자세한 내용은 [Windows Sharepoint Services의 웹 파트 인프라](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14))를 참조 하세요. 이전 스타일의 SharePoint 기반 웹 파트를 사용 하 여 웹 파트를 만드는 방법에 대 한 자세한 내용은 [기본 Sharepoint 웹 파트 만들기 연습](/previous-versions/office/ms452873(v=office.14))을 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[방법: SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part.md)|SharePoint 페이지의 웹 파트를 만드는 방법을 보여 줍니다.|
|[방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|시각적 디자인 화면을 사용 하 여 SharePoint 용 웹 파트를 만드는 방법을 보여 줍니다.|
|[방법: SharePoint 응용 프로그램 페이지 또는 웹 파트에 대 한 사용자 정의 컨트롤 만들기](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint에서 실행 되는 응용 프로그램 페이지 및 웹 파트에서 사용할 수 있는 재사용 가능한 사용자 지정 컨트롤을 만드는 방법을 보여 줍니다.|
|[연습: SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|SharePoint 용 웹 파트를 디자인 하는 방법을 설명 합니다.|
|[연습: 디자이너를 사용 하 여 SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|시각적 디자인 화면으로 컨트롤을 끌어 SharePoint 용 웹 파트를 디자인 하는 방법을 설명 합니다.|
|[연습: SharePoint 용 OData를 표시 하는 Silverlight 웹 파트 만들기](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Silverlight 응용 프로그램을 호스팅하고 SharePoint 목록의 데이터를 표시 하는 SharePoint 용 웹 파트를 디자인 하는 방법을 설명 합니다.|
