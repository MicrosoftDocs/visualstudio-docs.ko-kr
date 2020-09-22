---
title: SharePoint용 웹 파트 만들기 | Microsoft Docs
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
ms.openlocfilehash: 4824c358f81f2cf757f037611ed70ba9b8935130
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740159"
---
# <a name="create-web-parts-for-sharepoint"></a>SharePoint용 웹 파트 만들기
  웹 파트를 사용하면 브라우저를 통해 SharePoint 사이트 페이지의 콘텐츠, 모양, 동작을 수정할 수 있습니다. 웹 파트는 웹 파트 페이지 내에서 실행되는 서버 쪽 컨트롤이며, SharePoint 사이트에 표시되는 페이지의 구성 요소입니다. [구성 요소: 웹 파트](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))를 참조하세요.

 Visual Studio의 템플릿을 사용하여 SharePoint 사이트에서 웹 파트를 만들고 디버그할 수 있습니다.

## <a name="create-a-web-part-in-visual-studio"></a>Visual Studio에서 웹 파트 만들기
 SharePoint 프로젝트에 **웹 파트** 항목을 추가하여 웹 파트를 만듭니다. 샌드박스 솔루션 또는 팜 솔루션에서 **웹 파트** 항목을 사용할 수 있습니다.

 디자이너를 사용하여 시각적으로 웹 파트를 디자인하려면 **비주얼 웹 파트** 프로젝트를 만들거나 SharePoint 프로젝트에 **비주얼 웹 파트** 항목을 추가합니다. **비주얼 웹 파트** 항목은 팜 솔루션에서만 사용할 수 있습니다.

### <a name="web-part-item"></a>웹 파트 항목
 **웹 파트** 항목은 SharePoint 사이트의 웹 파트를 디자인하는 데 사용할 수 있는 파일을 제공합니다. **웹 파트** 항목을 추가하면 Visual Studio에서 프로젝트에 폴더를 생성하고 여러 개의 파일을 폴더에 추가합니다. 다음 표에서는 각 파일에 관해 설명합니다.

|파일|설명|
|----------|-----------------|
|*Elements.xml*|프로젝트의 기능 정의 파일에서 웹 파트를 배포하는 데 사용하는 정보를 포함합니다.|
|.webpart 파일|SharePoint에서 웹 파트 갤러리에 웹 파트를 표시하는 데 필요한 정보를 제공합니다.|
|코드 파일|웹 파트에 컨트롤을 추가하고 웹 파트 내에서 사용자 지정 콘텐츠를 생성하는 메서드를 포함합니다.|

 자세한 내용은 [방법: SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part.md)를 참조하세요.

### <a name="visual-web-part-item"></a>비주얼 웹 파트 항목
 비주얼 웹 파트는 Visual Studio의 Visual Web Developer 디자이너를 사용하여 만드는 웹 파트입니다. 비주얼 웹 파트는 다른 웹 파트와 동일하게 작동합니다. 단추 및 텍스트 상자와 같은 컨트롤을 웹 파트에 추가하려면 XML 파일에 코드를 추가합니다. 그러나 Visual Studio **도구 상자**에서 웹 파트로 끌거나 복사하여 비주얼 웹 파트에 컨트롤을 추가합니다. 그러면 디자이너에서 XML 파일에 필요한 코드를 생성합니다. [방법: 디자이너를 사용하여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)를 참조하세요.

## <a name="sharepoint-controls"></a>SharePoint 컨트롤
 Visual Studio는 애플리케이션 페이지와 같은 SharePoint 페이지를 만들기 위한 몇 가지 컨트롤을 제공합니다. 해당 컨트롤은 **도구 상자**의 **SharePoint 컨트롤** 아래에 표시됩니다. 컨트롤 기능은 SharePoint 사이트 및 목록 페이지에 사용되는 ASP.NET 서버 컨트롤을 포함하는 [Microsoft.SharePoint.WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) 네임스페이스에서 파생됩니다.

|컨트롤 이름|설명|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|ASP 메뉴를 삽입합니다. 자세한 내용은 [메뉴 컨트롤 개요](/previous-versions/ecs0x9w5(v=vs.140))를 참조하세요.|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|*.aspx* 페이지에 **LINK** 요소를 삽입하고 **CssRegistration**에서 정의된 하나 이상의 외부 스타일시트를 적용합니다.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|*.aspx* 페이지에 DateTime 컨트롤을 삽입합니다.|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|*.aspx* 페이지에 보안 유효성 검사를 삽입합니다.|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|지정한 목록의 속성을 반환합니다.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|현재 웹 사이트의 전역 속성을 반환합니다.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|*.aspx* 페이지에 RSS 피드 링크를 삽입합니다.|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|페이지를 렌더링할 때 요청할 수 있도록 페이지에 스크립트와 같은 리소스를 등록하기 위한 속성과 메서드를 제공합니다.|
|[테마](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|*.aspx* 페이지에 테마를 적용합니다.|

## <a name="debug-a-web-part"></a>웹 파트 디버그
 다른 Visual Studio 프로젝트를 디버그할 때와 마찬가지로 웹 파트가 포함된 SharePoint 프로젝트를 디버그할 수 있습니다. Visual Studio 디버거를 시작하면 Visual Studio에서 SharePoint 사이트가 열립니다.

 코드 디버그를 시작하려면 SharePoint의 웹 파트 페이지에 웹 파트를 추가합니다.

 SharePoint 프로젝트를 디버그하는 방법에 대한 자세한 내용은 [SharePoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)을 참조하세요.

## <a name="visual-web-part-limitations"></a>비주얼 웹 파트 제한 사항
 Visual Studio에서 시작하여 샌드박스 SharePoint 솔루션 및 팜 솔루션에 비주얼 웹 파트를 추가할 수 있습니다. 그러나 비주얼 웹 파트에는 다음과 같은 제한 사항이 있습니다.

- 비주얼 웹 파트는 대체 가능 매개 변수를 지원하지 않습니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)를 참조하세요.

- 사용자 정의 컨트롤 또는 비주얼 웹 파트는 비주얼 웹 파트로 끌어서 놓거나 복사할 수 없습니다. 이 작업을 수행하면 빌드 오류가 발생합니다.

- 비주얼 웹 파트는 $SPUrl과 같은 SharePoint Server 토큰을 직접 지원하지 않습니다. 자세한 내용은 [SharePoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md) 항목에서 “샌드박스가 적용된 비주얼 웹 파트의 토큰 제한 사항”을 참조하세요.

- 샌드박스 솔루션의 비주얼 웹 파트에 “샌드박스가 적용된 코드 호스트 서비스의 사용량이 너무 많아 요청을 처리할 수 없으므로 샌드박스가 적용된 코드 실행 요청이 거부되었습니다.” 오류가 표시되는 경우도 있습니다. 이 오류에 대한 자세한 내용은 [SharePoint 개발자 팀 블로그](/archive/blogs/sharepointdev/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham#10149157)에서 관련 게시물을 참조하세요.

- 서버 쪽 JavaScript 디버깅은 Visual Studio에서 지원되지 않지만 클라이언트 쪽 JavaScript 디버깅은 지원됩니다.

   서버 쪽 태그 파일에 인라인 JavaScript를 추가할 수 있지만 태그에 추가된 중단점에 대한 디버깅은 지원되지 않습니다. JavaScript를 디버그하려면 태그 파일에서 외부 JavaScript 파일을 참조한 다음, JavaScript 파일에서 중단점을 설정합니다.

- 인라인 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 코드의 디버깅은 태그 파일이 아니라 생성된 코드 파일에서 수행해야 합니다.

- 비주얼 웹 파트는 `<@ Assembly Src=` 지시문 사용을 지원하지 않습니다.

- SharePoint 웹 컨트롤 및 일부 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 컨트롤은 SharePoint 샌드박스가 적용된 환경에서 지원되지 않습니다. 샌드박스 솔루션의 비주얼 웹 파트에서 지원되지 않는 컨트롤을 사용하면 “‘Microsoft.SharePoint.WebControls’ 네임스페이스에 형식 또는 네임스페이스 이름 ‘Theme’가 없습니다.” 오류가 나타납니다.

  샌드박스 솔루션에 대한 자세한 내용은 [샌드박스 솔루션과 팜 솔루션의 차이점](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)을 참조하세요.

## <a name="create-older-style-sharepoint-based-web-parts"></a>이전 스타일의 SharePoint 기반 웹 파트 만들기
 Visual Studio의 템플릿을 사용하여 SharePoint용 사용자 지정 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] 웹 파트를 만들 수 있습니다. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] 웹 파트는 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 웹 파트 인프라를 기반으로 해서 빌드되며, 새 프로젝트에 권장되는 형식입니다.

 드물긴 하지만 이전 스타일의 SharePoint 기반 웹 파트를 사용하여 웹 파트를 만들어야 하는 경우도 있습니다. Visual Studio를 사용하여 해당 유형의 웹 파트를 만들 수 있지만, Visual Studio에서 이러한 유형의 웹 파트를 만들 수 있도록 특별히 디자인된 템플릿을 제공하지는 않습니다.

 이전 스타일의 SharePoint 기반 웹 파트를 만들어야 하는 경우에 대한 자세한 내용은 [Windows SharePoint Services의 웹 파트 인프라](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14))를 참조하세요. 이전 스타일의 SharePoint 기반 웹 파트를 사용하여 웹 파트를 만드는 방법에 대한 자세한 내용은 [연습: 기본 SharePoint 웹 파트 만들기](/previous-versions/office/ms452873(v=office.14))를 참조하세요.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part.md)|SharePoint 페이지의 웹 파트를 만드는 방법을 보여 줍니다.|
|[방법: 디자이너를 사용하여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|시각적 디자인 화면을 사용하여 SharePoint용 웹 파트를 만드는 방법을 보여 줍니다.|
|[방법: SharePoint 애플리케이션 페이지 또는 웹 파트용 사용자 정의 컨트롤 만들기](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint에서 실행되는 애플리케이션 페이지와 웹 파트에 사용할 수 있는 재사용 가능한 사용자 지정 컨트롤을 만드는 방법을 보여 줍니다.|
|[연습: SharePoint용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|SharePoint용 웹 파트를 디자인하는 방법을 설명합니다.|
|[연습: 디자이너를 사용하여 SharePoint용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|시각적 디자인 화면으로 컨트롤을 끌어 SharePoint용 웹 파트를 디자인하는 방법을 설명합니다.|
|[연습: SharePoint용 OData를 표시하는 Silverlight 웹 파트 만들기](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Silverlight 애플리케이션을 호스트하고 SharePoint 목록의 데이터를 표시하는 SharePoint용 웹 파트를 디자인하는 방법을 설명합니다.|