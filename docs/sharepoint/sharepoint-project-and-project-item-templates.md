---
title: SharePoint 프로젝트 및 프로젝트 항목 템플릿 | Microsoft Docs
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649219"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint 프로젝트 및 프로젝트 항목 템플릿
  다음 섹션에서는 사용 가능한 SharePoint 프로젝트 및 프로젝트 항목 템플릿과 이러한 템플릿 사용 방법에 대해 설명 합니다.

## <a name="project-and-project-item-templates-overview"></a>프로젝트 및 프로젝트 항목 템플릿 개요
 Visual Studio에서 새 SharePoint 프로젝트를 만들면 해당 프로젝트 형식에 필요한 모든 프로젝트 항목과 함께 SharePoint 프로젝트가 솔루션에 추가 됩니다. 예를 들어 Silverlight 웹 파트 프로젝트를 만드는 경우 Visual Studio에서 해당 프로젝트 항목에 필요한 모든 파일과 함께 시각적 웹 파트 프로젝트 항목 및 Silverlight 응용 프로그램 프로젝트 항목을 포함 하는 솔루션을 만듭니다. 프로젝트 항목 템플릿은 이벤트 수신기, 사이트 열 또는 목록 추가와 같은 기존 SharePoint 프로젝트에 프로젝트 항목을 추가 하는 데 사용 됩니다.

 SharePoint 기본 사항에 대 한 자세한 내용은 [Sharepoint Foundation 구성 요소](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14))를 참조 하세요. 고급 사용자는 사용자 지정 프로젝트 및 프로젝트 항목 템플릿을 만들 수 있습니다. 자세한 내용은 [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)을 참조 하세요.

## <a name="project-templates"></a>프로젝트 템플릿
 다음은 SharePoint 프로젝트 템플릿 목록입니다. Visual Studio에서 SharePoint 프로젝트 템플릿을 보려면 **새 프로젝트** 대화 상자에서 **visual c #** 또는 **Visual Basic**아래의 **sharepoint** 노드를 확장 한 다음 **2010**을 선택 합니다.

### <a name="sharepoint-2010-project"></a>SharePoint 2010 프로젝트
 *Sharepoint 2010 프로젝트* 의 내용은 모든 sharepoint 프로젝트 템플릿에 포함 되어 있습니다. SharePoint 2010 프로젝트에는 다음이 포함 됩니다.

- 프로젝트 파일입니다.

- 프로젝트 속성 페이지.

- 프로젝트의 모든 어셈블리 참조가 나열 된 **참조** 폴더입니다.

- 기능을 SharePoint 서버에 배포 *.feature* 하는 데 사용 되는 기능 구성 파일을 포함 하 **는 폴더입니다** .

- SharePoint에 솔루션을 배포 하 *Package.package* 는 데 사용 되는 패키지 파일을 포함 하는 **패키지 폴더입니다** .

- 보안 강화를 위해 강력한 이름으로 어셈블리에 서명 하는 데 사용 되는 키 .snk (강력한 이름 키) 파일입니다.

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight 웹 파트
 *Sharepoint 2010 Silverlight 웹 파트* 프로젝트를 사용 하 여 silverlight 응용 프로그램을 표시 하는 sharepoint 용 웹 파트를 만들 수 있습니다. 이 프로젝트를 만들 때 새 Silverlight 응용 프로그램을 추가 하거나 기존 응용 프로그램을 참조 하는지 여부를 지정할 수 있습니다. 자세한 내용은 [sharepoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md) 및 [연습: sharepoint 용 OData를 표시 하는 Silverlight 웹 파트 만들기](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)를 참조 하세요.

### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 비주얼 웹 파트
 *SharePoint 2010 시각적 웹 파트* 프로젝트에는 *Elements.xml* 정의 파일, **웹 파트** 항목 및 **사용자 정의 컨트롤** 항목이 포함 되어 있습니다. Visual Studio 도구 상자에서 사용자 컨트롤의 화면으로 컨트롤을 끌거나 복사 하 여 비주얼 웹 파트의 모양을 디자인할 수 있습니다. 자세한 내용은 [방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 및 [구성 블록: 웹 파트](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))을 참조 하세요.

### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010 솔루션 패키지 가져오기
 *Sharepoint 2010 솔루션 패키지 프로젝트 가져오기* 를 사용 하면 sharepoint 솔루션 (*.wsp*) 파일로 내보낸 기존 sharepoint 2010 사이트 전체 또는 일부를 Visual Studio로 가져올 수 있습니다. Visual Studio로 가져온 후에는 항목을 사용자 지정 하 고 다시 배포할 수 있습니다. 자세한 내용은 [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)를 참조 하세요.

### <a name="import-reusable-sharepoint-2010-workflow"></a>다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기
 *재사용 가능한 sharepoint 2010 워크플로 프로젝트 가져오기* 를 사용 하면 sharepoint Designer 2010에서 만든 재사용 가능한 선언적 워크플로를 Visual Studio로 가져올 수 있습니다. SharePoint 사이트에서 *.wsp* 파일로 워크플로를 내보냅니다. Visual Studio로 가져온 후에는이를 사용자 지정 하 고, 코드를 추가 하 고, SharePoint 사이트에 배포할 수 있습니다. 자세한 내용은 [연습: Visual Studio에 SharePoint Designer 다시 사용 가능한 워크플로 가져오기](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)를 참조 하세요.

## <a name="project-item-templates"></a>프로젝트 항목 템플릿
 다음은 SharePoint 프로젝트 항목 템플릿 목록입니다. 프로젝트 항목 템플릿은 사이트 열, 목록, 콘텐츠 형식 등의 SharePoint 기능을 지원 하기 위해 SharePoint 솔루션에 파일을 추가 합니다. 예를 들어 사이트 열을 솔루션에 추가 하면 *Elements.xml* 정의 파일이 포함 된 사이트 열 프로젝트가 추가 됩니다. 시각적 웹 파트를 추가 하면 *Elements.xml* 파일, 사용자 정의 컨트롤 항목 및 시각적 웹 파트 항목이 포함 된 비주얼 웹 파트 프로젝트가 솔루션에 추가 됩니다.

 SharePoint 프로젝트 항목 템플릿을 보려면 **솔루션 탐색기**에서 sharepoint 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**, **새 항목**을 차례로 선택 합니다. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010**을 선택 합니다.

### <a name="application-page-farm-solution-only"></a>응용 프로그램 페이지 (팜 솔루션에만 해당)
 **응용 프로그램 페이지 (팜 솔루션에만 해당)** 항목을 사용 하면 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] SharePoint 사이트에 대 한 웹 페이지를 디자인할 수 있습니다. 응용 프로그램 페이지는 팜 솔루션 에서만 사용할 수 있습니다. 팜 솔루션에만이 프로젝트 항목을 추가할 수 있습니다. 자세한 내용은 [방법: 응용 프로그램 페이지 만들기](../sharepoint/how-to-create-an-application-page.md) 및 [응용 프로그램 _layouts 페이지 종류](/previous-versions/office/aa979604(v=office.14))를 참조 하세요.

### <a name="business-data-connectivity-model-farm-solution-only"></a>비즈니스 데이터 연결 모델 (팜 솔루션에만 해당)
 **비즈니스 데이터 연결 모델 (팜 솔루션에만 해당)** 항목을 사용 하면 비즈니스 데이터를 SharePoint에 통합할 수 있습니다. 비즈니스 데이터는 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] Siebel 및 SAP (서비스 광고 프로토콜)와 같은 백 엔드 서버 응용 프로그램에서 가져올 수 있습니다. 비즈니스 데이터 연결 모델은 팜 솔루션 에서만 사용할 수 있습니다. 팜 솔루션에만이 프로젝트 항목을 추가할 수 있습니다. 자세한 내용은 [방법: BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md), [방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한 지정](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)및 [새로운 기능: 비즈니스 연결 서비스](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14))를 참조 하세요.

### <a name="content-type"></a>내용 유형
 *콘텐츠 형식* 항목을 사용 하 여 문서, 알림 또는 작업과 같은 기존 (기본) 콘텐츠 형식을 기반으로 사용자 지정 콘텐츠 형식을 만들 수 있습니다. 사용자 지정 콘텐츠 형식은 사용자가 정의 하는 모든 사이트 열 (필드)과 함께 기본 콘텐츠 형식과 동일한 특성 및 필드를 제공 합니다. 예를 들어, SharePoint에 제공 되는 기본 연락처 콘텐츠 형식을 기반으로 하는 사용자 지정 연락처 콘텐츠 형식을 만들 수 있습니다. 기존 사이트 열을 변경 하거나 기본 콘텐츠 형식에 이미 포함 된 열에 더 많은 사이트 열을 추가 하 여 콘텐츠 형식을 사용자 지정할 수 있습니다.

> [!NOTE]
> SharePoint 제한으로 인해 샌드박스가 적용 된 솔루션 콘텐츠 형식을 기반으로 팜 솔루션 콘텐츠 형식을 만들 수 없습니다.

 자세한 내용은 [연습: 사이트 열, 콘텐츠 형식 및 SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) 및 구성 요소 목록 만들기 [: 콘텐츠 형식](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14))을 참조 하세요.

### <a name="empty-element"></a>빈 요소
 *빈 요소* 는 Visual Studio에서 프로젝트 또는 프로젝트 항목 템플릿이 없는 SharePoint 프로젝트 항목을 정의 하는 데 주로 사용 됩니다. 프로젝트에 빈 요소를 추가 하면 이름이 EmptyElement [x] ([x] 인 노드가 고유 하 게 \) 만들어집니다. EmptyElement [x]에는Elements.xml 라는 단일 파일이 포함 되어 있습니다 * .* [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]문을 사용 하 여 *Elements.xml*에서 원하는 요소를 정의 합니다.

### <a name="event-receiver"></a>이벤트 수신기
 *이벤트 수신기* 는 항목을 목록에 추가 하는 경우, 웹 항목이 삭제 될 때 또는 워크플로가 시작 된 경우와 같은 SharePoint 사이트의 항목에 대 한 이벤트를 처리 합니다. 이벤트 수신기 프로젝트 항목 템플릿을 사용 하 여 다음을 처리할 수 있습니다.

- 이벤트를 나열합니다.

- 목록 항목 이벤트

- 메일 이벤트 나열

- 웹 이벤트

- 워크플로 이벤트 나열

  이벤트 수신기 프로젝트 항목은 **SharePoint 사용자 지정 마법사**에서 프로젝트를 만들 때 지정한 모든 이벤트에 대 한 이벤트 처리기를 포함 하는 단일 클래스 파일을 사용 하 여 **이벤트 수신기** 폴더를 만듭니다. 이벤트 수신기 클래스는 파일, 필드, 항목, 목록, 첨부 파일, 웹 파트 및 워크플로와 같은 항목을 추가, 업데이트, 삭제 또는 제거 하는 경우 SharePoint 사이트에서 발생 하는 이벤트를 처리할 수 있습니다. 자세한 내용은 [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md) 및 [구성 블록: 이벤트 처리](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14))를 참조 하세요.

### <a name="list"></a>목록
 목록은 일정 또는 작업 목록과 같은 재사용 가능한 기본 SharePoint 목록 정의의 인스턴스입니다. 솔루션에 목록을 추가한 후 목록 디자이너를 사용 하 여 목록에 사이트 열을 추가 하 고 사용자 지정 목록 열을 만들 수 있습니다. 여기에는 콘텐츠 형식의 사이트 열이 포함 됩니다. 목록에 표시 되는 열을 결정 하는 목록에 대 한 *보기* 를 지정할 수 있습니다. 자세한 내용은 [연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) 및 [문서 블록: 목록 및 문서 라이브러리](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14))를 참조 하세요.

### <a name="module"></a>모듈
 *모듈 (* 모듈과 혼동 하지 않음)에는 [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] 이미지 또는 메모와 같이 SharePoint 서버에 배포할 파일이 포함 되어 있습니다. 모듈 프로젝트 항목에 **모듈** 노드가 포함 되어 있습니다. 모듈 노드에는 두 개의 프로젝트 항목 템플릿이 포함 되어 있습니다. XML 정의 파일은 모듈의 매니페스트 역할을 하 고, *sample.txt* 파일은 자리 표시자 파일입니다. 자세한 내용은 [모듈을 사용 하 여 솔루션 및 모듈에 파일 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md) 을 [Modules](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14))참조 하세요.

### <a name="sequential-workflow-farm-solution-only"></a>순차 워크플로 (팜 솔루션에만 해당)
 *순차 워크플로* 는 마지막 단계가 완료 될 때까지 순서 대로 수행 되는 일련의 비즈니스 논리 단계입니다. 순차 워크플로는 목록과 문서와 같은 SharePoint 항목을 포함 하는 프로세스를 관리 하는 데 사용 됩니다. 사이트 수준 (전역) 워크플로 또는 목록 수준 (로컬) 워크플로 중 하나를 만들 수 있으며, 워크플로를 자동으로 시작할지 수동으로 시작할지를 선택할 수 있습니다. 이 프로젝트 항목은 팜 솔루션 에서만 사용할 수 있습니다. 팜 솔루션에만이 프로젝트 항목을 추가할 수 있습니다. 자세한 내용은 [sharepoint 워크플로 솔루션 만들기](../sharepoint/creating-sharepoint-workflow-solutions.md), [sharepoint Server 2010의 워크플로](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))및 [새로운 기능: 워크플로 향상](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))을 참조 하세요.

### <a name="silverlight-web-part"></a>Silverlight 웹 파트
 *Silverlight 웹 파트* 프로젝트 항목을 사용 하면 silverlight 응용 프로그램을 표시 하는 SharePoint 용 웹 파트를 만들 수 있습니다. 솔루션에이 프로젝트 항목을 추가 하는 경우 새 Silverlight 응용 프로그램을 추가할지 아니면 나중에 기존 응용 프로그램을 참조할 것인지를 선택할 수 있습니다. 자세한 내용은 [sharepoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md) 및 [연습: sharepoint 용 OData를 표시 하는 Silverlight 웹 파트 만들기](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)를 참조 하세요.

### <a name="site-column"></a>사이트 열
 *필드*라고도 하는 *사이트 열*은 SharePoint 프로젝트에 추가할 수 있는 가장 기본적인 요소 중 하나입니다. 사이트 열은 연락처 목록에 있는 연락처의 전화 번호, 텍스트 주석 또는 도시 이름과 같은 데이터 유형을 나타냅니다. 자세한 내용은 SharePoint 및 열 [에 대 한 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) 를 [Columns](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))참조 하세요.

### <a name="site-definition-farm-solution-only"></a>사이트 정의 (팜 솔루션에만 해당)
 *사이트 정의* 프로젝트 항목은 다음 파일을 포함 하는 사이트 정의 폴더를 포함 합니다.

- Default.aspx 페이지가 사이트의 기본 웹 페이지로 사용 됩니다.

- 사이트의 구성 요소를 정의 하는 *onet.xml* 파일입니다.

- **새 SharePoint 사이트** 페이지의 **템플릿 선택** 섹션에 표시 되는 사이트 정의 구성을 지정 하는 webtemp xml 파일입니다.

  사이트 정의를 추가한 후에는 기능을 도입할 코드와 파일을 추가 합니다. 이 프로젝트 항목은 팜 솔루션 에서만 사용할 수 있습니다. 팜 솔루션에만이 프로젝트 항목을 추가할 수 있습니다. 자세한 내용은 [SharePoint에 대 한 사이트 정의 만들기](../sharepoint/creating-site-definitions-for-sharepoint.md) 및 [사이트 정의 및 구성](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14))을 참조 하세요.

### <a name="state-machine-workflow-farm-solution-only"></a>상태 시스템 워크플로 (팜 솔루션에만 해당)
 *상태 시스템 워크플로* 는 비즈니스 논리 상태, 전환 및 작업의 집합입니다. 상태 시스템 워크플로의 단계는 순서 대로 수행 되지 않습니다. 대신 작업 및 상태에 의해 트리거됩니다. 순차 워크플로와 마찬가지로 상태 시스템 워크플로는 목록 및 문서와 같은 SharePoint 항목에 연결 됩니다. 다시 한 번, 사이트 수준 (전역) 워크플로 또는 목록 수준 (로컬) 워크플로를 만들 수 있습니다. 워크플로를 자동으로 시작할지 수동으로 시작할지를 선택할 수도 있습니다. 이 프로젝트 항목은 팜 솔루션 에서만 사용할 수 있습니다. 팜 솔루션에만이 프로젝트 항목을 추가할 수 있습니다. 자세한 내용은 [sharepoint 워크플로 솔루션 만들기](../sharepoint/creating-sharepoint-workflow-solutions.md), [sharepoint Server 2010의 워크플로](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))및 [새로운 기능: 워크플로 향상](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))을 참조 하세요.

### <a name="user-control-farm-solution-only"></a>사용자 정의 컨트롤 (팜 솔루션에만 해당)
 *사용자 정의 컨트롤* 은 다른 ASP.NET 컨트롤 및 SharePoint 컨트롤을 추가할 수 있는 재사용 가능한 사용자 지정 컨트롤입니다. SharePoint에서 실행 되는 응용 프로그램 페이지 및 웹 파트에 사용자 정의 컨트롤을 추가할 수 있습니다. 이 프로젝트 항목은 팜 솔루션 에서만 사용할 수 있습니다. 팜 솔루션에만이 프로젝트 항목을 추가할 수 있습니다. 자세한 내용은 [웹 파트 또는 응용 프로그램 페이지의 재사용 가능한 컨트롤 만들기](creating-reusable-controls-for-web-parts-or-application-pages.md)를 참조 하세요.

### <a name="visual-web-part"></a>비주얼 웹 파트
 *시각적 웹 파트* 프로젝트 항목에는 *Elements.xml* 정의 파일, **웹 파트** 항목 및 **사용자 정의 컨트롤** 항목이 포함 되어 있습니다. Visual Studio 도구 상자에서 사용자 컨트롤의 화면으로 컨트롤을 끌거나 복사 하 여 비주얼 웹 파트의 모양을 디자인할 수 있습니다. 자세한 내용은 [방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 및 [구성 블록: 웹 파트](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))을 참조 하세요.

### <a name="web-part"></a>웹 파트
 *웹 파트* 는 웹 파트 페이지 라는 특수 한 형식의 페이지 내에서 실행 되는 서버측 컨트롤입니다. SharePoint 사이트에 표시 되는 페이지의 구성 요소입니다. 웹 파트 항목은 SharePoint 사이트의 웹 파트를 디자인 하는 데 사용할 수 있는 파일을 제공 합니다. 자세한 내용은 [방법: SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part.md) 및 [구성 블록: 웹 파트](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 제품 및 기술](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
