---
title: 쉐어포인트 프로젝트 및 프로젝트 항목 템플릿 | 마이크로 소프트 문서
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
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649219"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint 프로젝트 및 프로젝트 항목 템플릿
  다음 섹션에서는 사용 가능한 SharePoint 프로젝트 및 프로젝트 항목 템플릿과 템플릿이 사용되는 방법에 대해 설명합니다.

## <a name="project-and-project-item-templates-overview"></a>프로젝트 및 프로젝트 항목 템플릿 개요
 Visual Studio에서 새 SharePoint 프로젝트를 만들면 SharePoint 프로젝트가 해당 프로젝트 유형에 필요한 모든 프로젝트 항목과 함께 솔루션에 추가됩니다. 예를 들어 Silverlight 웹 파트 프로젝트를 만드는 경우 Visual Studio는 해당 프로젝트 항목에 필요한 모든 파일과 함께 Visual Web Part 프로젝트 항목 및 Silverlight 응용 프로그램 프로젝트 항목이 포함된 솔루션을 만듭니다. 프로젝트 항목 템플릿은 이벤트 수신기, 사이트 열 또는 목록 추가와 같은 기존 SharePoint 프로젝트에 프로젝트 항목을 추가하는 데 사용됩니다.

 SharePoint 기본 정보에 대한 자세한 내용은 [SharePoint 기반 구성 요소를](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14))참조하십시오. 고급 사용자는 사용자 지정 프로젝트 및 프로젝트 항목 템플릿을 만들 수 있습니다. 자세한 내용은 [SharePoint 프로젝트 시스템 확장을](../sharepoint/extending-the-sharepoint-project-system.md)참조하십시오.

## <a name="project-templates"></a>프로젝트 템플릿
 다음은 SharePoint 프로젝트 템플릿 목록입니다. 새 **프로젝트** 대화 상자에서 Visual Studio에서 SharePoint 프로젝트 템플릿을 보려면 **Visual C#** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장한 다음 **2010을**선택합니다.

### <a name="sharepoint-2010-project"></a>쉐어포인트 2010 프로젝트
 *SharePoint 2010 프로젝트의* 내용은 모든 SharePoint 프로젝트 템플릿에 포함됩니다. SharePoint 2010 프로젝트에는 다음이 포함됩니다.

- 프로젝트 파일입니다.

- 프로젝트 속성 페이지입니다.

- 프로젝트의 모든 어셈블리 참조를 나열하는 **참조** 폴더입니다.

- SharePoint 서버에 기능을 배포하는 데 사용되는 *.feature* 구성 파일이 포함된 기능 **폴더입니다.**

- SharePoint에 솔루션을 배포하는 데 사용되는 *Package.package* 파일이 포함된 **패키지** 폴더입니다.

- 보안을 강화하기 위해 강력한 이름으로 어셈블리에 서명하는 데 사용되는 key.snk(강력한 이름 키) 파일입니다.

### <a name="sharepoint-2010-silverlight-web-part"></a>쉐어포인트 2010 실버라이트 웹 파트
 *SharePoint 2010 실버라이트 웹 파트* 프로젝트를 사용하면 Silverlight 응용 프로그램을 표시하는 SharePoint용 웹 파트를 만들 수 있습니다. 이 프로젝트를 만들 때 새 Silverlight 응용 프로그램을 추가할지 아니면 기존 응용 프로그램을 참조할지 지정할 수 있습니다. 자세한 내용은 SharePoint 및 [연습에 대한 웹 파트 만들기: 공유점에 대한](../sharepoint/creating-web-parts-for-sharepoint.md) [OData를 표시하는 실버라이트 웹 파트 만들기를](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)참조하십시오.

### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 비주얼 웹 파트
 *SharePoint 2010 시각적 웹 파트* 프로젝트에는 *Elements.xml* 정의 파일, **웹 파트** 항목 및 사용자 **제어** 항목이 포함됩니다. Visual Studio 도구 상자에서 사용자 컨트롤의 표면으로 컨트롤을 드래그하거나 복사하여 시각적 웹 파트의 모양을 디자인할 수 있습니다. 자세한 내용은 디자이너 및 [빌딩 블록: 웹 파트를](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)) [사용하여 SharePoint 웹 파트 를 만드는 방법을 참조하세요.](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)

### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010 솔루션 패키지 가져오기
 *SharePoint 2010 솔루션 패키지 가져오기* 프로젝트를 사용하면 SharePoint 솔루션(.wsp) 파일로 내보내는 기존 *.wsp*SharePoint 2010 사이트의 전부 또는 일부를 Visual Studio로 가져올 수 있습니다. Visual Studio로 가져온 후에는 해당 항목을 사용자 지정하고 다시 배포할 수 있습니다. 자세한 내용은 [기존 SharePoint 사이트에서 항목 가져오기를](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)참조하십시오.

### <a name="import-reusable-sharepoint-2010-workflow"></a>재사용 가능한 SharePoint 2010 워크플로 가져오기
 *재사용 가능한 SharePoint 2010 워크플로* 프로젝트를 통해 SharePoint Designer 2010에서 만든 재사용 가능한 선언적 워크플로를 Visual Studio로 가져올 수 있습니다. 워크플로는 SharePoint 사이트에서 *.wsp* 파일로 내보내됩니다. Visual Studio로 가져온 후에는 사용자 지정하고 코드를 추가한 다음 SharePoint 사이트에 배포할 수 있습니다. 자세한 내용은 [연습: SharePoint 디자이너 재사용 가능한 워크플로를 Visual Studio로 가져오기](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)를 참조하십시오.

## <a name="project-item-templates"></a>프로젝트 항목 템플릿
 다음은 SharePoint 프로젝트 항목 템플릿 목록입니다. 프로젝트 항목 템플릿은 SharePoint 솔루션에 파일을 추가하여 사이트 열, 목록 및 콘텐츠 유형과 같은 SharePoint 기능을 지원합니다. 예를 들어 솔루션에 사이트 열을 추가하면 *Elements.xml* 정의 파일이 포함된 사이트 열 프로젝트가 추가됩니다. 시각적 웹 파트를 추가하면 *Elements.xml* 파일, 사용자 컨트롤 항목 및 시각적 웹 파트 항목이 포함된 시각적 웹 파트 프로젝트가 솔루션에 추가됩니다.

 SharePoint 프로젝트 항목 템플릿을 보려면 **솔루션 탐색기에서**SharePoint 프로젝트의 바로 가기 메뉴를 연 다음 **새 항목** **추가를**선택합니다. **시각적 C#** 또는 **시각적 기본**에서 **SharePoint** 노드를 확장 한 다음 **2010을**선택합니다.

### <a name="application-page-farm-solution-only"></a>응용 프로그램 페이지(팜 솔루션만)
 **응용 프로그램 페이지(팜 솔루션 전용)** 항목을 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 사용하면 SharePoint 사이트에 대한 웹 페이지를 디자인할 수 있습니다. 응용 프로그램 페이지는 팜 솔루션에서만 사용할 수 있습니다. 이 프로젝트 항목은 팜 솔루션에만 추가할 수 있습니다. 자세한 내용은 [응용 프로그램 페이지 만들기](../sharepoint/how-to-create-an-application-page.md) 및 응용 프로그램 _layouts 페이지 [유형](/previous-versions/office/aa979604(v=office.14))입니다.

### <a name="business-data-connectivity-model-farm-solution-only"></a>비즈니스 데이터 연결 모델(팜 솔루션만)
 **비즈니스 데이터 연결 모델(팜 솔루션만 해당)** 항목을 사용하면 비즈니스 데이터를 SharePoint에 통합할 수 있습니다. 비즈니스 데이터는 [Siebel] 및 SAP(서비스 광고 프로토콜)와 같은 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]백 엔드 서버 응용 프로그램에서 올 수 있습니다. 비즈니스 데이터 연결 모델은 팜 솔루션에서만 사용할 수 있습니다. 이 프로젝트 항목은 팜 솔루션에만 추가할 수 있습니다. 자세한 내용은 [BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md)방법, [방법: 리소스 파일을 사용하여 지역화된 이름, 속성 및 사용 권한을 지정하고](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md) [새로운 내용: 비즈니스 연결 서비스를](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14))참조하십시오.

### <a name="content-type"></a>내용 유형
 *컨텐트 유형* 항목을 사용하면 문서, 공지 또는 작업과 같은 기존(기본) 콘텐츠 형식을 기반으로 사용자 지정 콘텐츠 형식을 만들 수 있습니다. 사용자 지정 콘텐츠 형식은 정의하는 모든 사이트 열(필드)과 함께 기본 콘텐츠 유형과 동일한 특성 및 필드를 제공합니다. 예를 들어 SharePoint에 제공되는 기본 연락처 콘텐츠 유형을 기반으로 하는 사용자 지정 연락처 콘텐츠 형식을 만들 수 있습니다. 기존 사이트 열을 변경하거나 기본 콘텐츠 유형에 이미 포함된 사이트 열을 더 추가하여 콘텐츠 유형을 사용자 지정할 수 있습니다.

> [!NOTE]
> SharePoint 제한으로 인해 샌드박스된 솔루션 콘텐츠 형식을 기반으로 팜 솔루션 콘텐츠 형식을 만들 수 없습니다.

 자세한 내용은 [연습: 사이트 열, 콘텐츠 유형 및 공유점 및](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) 빌딩 블록에 대한 목록 [만들기: 콘텐츠 유형](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14))을 참조하십시오.

### <a name="empty-element"></a>빈 요소
 *빈 요소는* Visual Studio에서 프로젝트 또는 프로젝트 항목 템플릿이 없는 SharePoint 프로젝트 항목을 정의하는 데 가장 자주 사용됩니다. 프로젝트에 빈 요소를 추가하면 EmptyElement[x](여기서 [x]라는 노드가 고유\) 번호로 만들어집니다. EmptyElement[x]에는 *Elements.xml이라는* 단일 파일이 포함되어 있습니다. 문을 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 사용하여 *Elements.xml*에서 원하는 요소를 정의합니다.

### <a name="event-receiver"></a>이벤트 수신기
 *이벤트 수신기는* 항목이 목록에 추가된 경우, 웹 항목이 삭제된 경우 또는 워크플로가 시작된 경우와 같이 SharePoint 사이트의 항목에 대한 이벤트를 처리합니다. 이벤트 수신기 프로젝트 항목 템플릿을 사용하면

- 이벤트를 나열합니다.

- 항목 이벤트 목록

- 이메일 이벤트 목록

- 웹 이벤트

- 워크플로 이벤트 나열

  이벤트 수신기 프로젝트 항목은 **SharePoint 사용자 지정 마법사에서**프로젝트를 만들 때 지정한 모든 이벤트에 대한 이벤트 처리기를 포함하는 단일 클래스 파일이 있는 **이벤트 수신기** 폴더를 만듭니다. 이벤트 수신기 클래스는 파일, 필드, 항목, 목록, 첨부 파일, 웹 파트 및 워크플로와 같은 항목이 추가, 업데이트, 삭제 또는 제거될 때 SharePoint 사이트에서 발생하는 이벤트를 처리할 수 있습니다. 자세한 내용은 이벤트 수신기 만들기 및 [빌딩 블록: 이벤트 처리](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14))를 [참조하세요.](../sharepoint/how-to-create-an-event-receiver.md)

### <a name="list"></a>목록
 목록은 캘린더 또는 작업 목록과 같은 재사용 가능한 SharePoint 목록 정의의 인스턴스입니다. 솔루션에 목록을 추가한 후 목록 디자이너를 사용하면 목록에 사이트 열을 추가하고 사용자 지정 목록 열을 만들 수 있습니다. 여기에는 콘텐츠 형식의 사이트 열이 포함됩니다. 목록에 표시될 열을 결정하는 목록에 대한 *보기를* 지정할 수 있습니다. 자세한 내용은 [연습: 사이트 열 만들기, 콘텐츠 유형 및 공유점 및](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) [빌딩 블록: 목록 및 문서 라이브러리에](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14))대한 목록 작성을 참조하십시오.

### <a name="module"></a>Module
 *모듈과* 혼동하지 [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] 않는 모듈에는 이미지 나 메모와 같은 SharePoint 서버에 배포하려는 파일이 포함되어 있습니다. 모듈 프로젝트 **항목에모듈** 노드가 포함되어 있습니다. 모듈 노드에는 모듈의 매니페스트 역할을 하는 XML 정의 파일과 자리 표시자 파일인 *sample.txt* 파일이라는 두 개의 프로젝트 항목 템플릿이 포함되어 있습니다. 자세한 내용은 모듈 사용을 사용하여 솔루션 및 [모듈에 파일을](../sharepoint/using-modules-to-include-files-in-the-solution.md) [포함합니다.](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14))

### <a name="sequential-workflow-farm-solution-only"></a>순차 적 워크플로우(팜 솔루션만)
 *순차적 워크플로는* 마지막 단계가 완료될 때까지 순서대로 수행되는 일련의 비즈니스 논리 단계입니다. 순차적 워크플로는 목록 및 문서와 같은 SharePoint 항목이 포함된 프로세스를 관리하는 데 사용됩니다. 사이트 수준(전역) 워크플로 또는 목록 수준(로컬) 워크플로를 만들 수 있으며 워크플로가 자동으로 시작되는지 수동으로 시작할지 여부를 선택할 수 있습니다. 이 프로젝트 항목은 팜 솔루션에서만 사용할 수 있습니다. 이 프로젝트 항목은 팜 솔루션에만 추가할 수 있습니다. 자세한 내용은 [SharePoint 워크플로 솔루션 만들기,](../sharepoint/creating-sharepoint-workflow-solutions.md) [SharePoint Server 2010의 워크플로,](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14)) [최신 정보: 워크플로 개선](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))을 참조하십시오.

### <a name="silverlight-web-part"></a>실버라이트 웹 파트
 *Silverlight 웹 부품* 프로젝트 항목을 사용하면 Silverlight 응용 프로그램을 표시하는 SharePoint용 웹 파트를 만들 수 있습니다. 이 프로젝트 항목을 솔루션에 추가할 때 새 Silverlight 응용 프로그램을 추가할지 아니면 나중에 기존 응용 프로그램을 참조할지 선택할 수 있습니다. 자세한 내용은 SharePoint 및 [연습에 대한 웹 파트 만들기: 공유점에 대한](../sharepoint/creating-web-parts-for-sharepoint.md) [OData를 표시하는 실버라이트 웹 파트 만들기를](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)참조하십시오.

### <a name="site-column"></a>사이트 열
 *필드라고도*하는 *사이트 열은*SharePoint 프로젝트에 추가할 수 있는 가장 기본적인 요소 중 하나입니다. 사이트 열은 전화 번호, 텍스트 댓글 또는 연락처 목록에서 연락처의 도시 이름과 같은 데이터 유형을 나타냅니다. 자세한 내용은 [SharePoint 및 열에 대한 사이트 열, 콘텐츠 유형 및 목록 만들기를](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) 참조하십시오. [Columns](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))

### <a name="site-definition-farm-solution-only"></a>사이트 정의(팜 솔루션만)
 *사이트 정의* 프로젝트 항목에는 다음 파일이 포함된 사이트 정의 폴더가 포함되어 있습니다.

- 사이트의 기본 웹 페이지로 사용되는 기본 .aspx 페이지입니다.

- 사이트의 구성 요소를 정의하는 *onet.xml* 파일입니다.

- **새 SharePoint 사이트** 페이지의 **템플릿 선택** 섹션에 나타나는 사이트 정의 구성을 지정하는 웹템제 xml 파일입니다.

  사이트 정의를 추가한 후 코드와 파일을 추가하여 기능을 도입합니다. 이 프로젝트 항목은 팜 솔루션에서만 사용할 수 있습니다. 이 프로젝트 항목은 팜 솔루션에만 추가할 수 있습니다. 자세한 내용은 SharePoint 및 사이트 정의 [및 구성에](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)) [대한 사이트 정의 만들기를](../sharepoint/creating-site-definitions-for-sharepoint.md) 참조하십시오.

### <a name="state-machine-workflow-farm-solution-only"></a>상태 머신 워크플로(팜 솔루션만)
 *상태 머신 워크플로는* 비즈니스 논리 상태, 전환 및 작업의 집합입니다. 상태 컴퓨터 워크플로의 단계는 순서대로 수행되지 않습니다. 대신 작업 및 상태에 의해 트리거됩니다. 순차적 워크플로와 마찬가지로 상태 머신 워크플로는 목록 및 문서와 같은 SharePoint 항목과 연결됩니다. 다시 한 번 사이트 수준(전역) 워크플로 또는 목록 수준(로컬) 워크플로를 만들 수 있습니다. 워크플로가 자동으로 시작되는지 수동으로 시작할지 여부를 선택할 수도 있습니다. 이 프로젝트 항목은 팜 솔루션에서만 사용할 수 있습니다. 이 프로젝트 항목은 팜 솔루션에만 추가할 수 있습니다. 자세한 내용은 [SharePoint 워크플로 솔루션 만들기,](../sharepoint/creating-sharepoint-workflow-solutions.md) [SharePoint Server 2010의 워크플로,](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14)) [최신 정보: 워크플로 개선](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))을 참조하십시오.

### <a name="user-control-farm-solution-only"></a>사용자 제어(팜 솔루션만)
 *사용자 컨트롤은* 다른 ASP.NET 컨트롤 및 SharePoint 컨트롤을 추가할 수 있는 재사용 가능한 사용자 지정 컨트롤입니다. 사용자 컨트롤은 SharePoint에서 실행되는 응용 프로그램 페이지 및 웹 파트에 추가할 수 있습니다. 이 프로젝트 항목은 팜 솔루션에서만 사용할 수 있습니다. 이 프로젝트 항목은 팜 솔루션에만 추가할 수 있습니다. 자세한 내용은 [웹 파트 또는 응용 프로그램 페이지에 대한 재사용 가능한 컨트롤 만들기를](creating-reusable-controls-for-web-parts-or-application-pages.md)참조하십시오.

### <a name="visual-web-part"></a>비주얼 웹 파트
 *시각적 웹 파트* 프로젝트 항목에는 *Elements.xml* 정의 파일, **웹 파트** 항목 및 **사용자 제어** 항목이 포함됩니다. Visual Studio 도구 상자에서 사용자 컨트롤의 표면으로 컨트롤을 드래그하거나 복사하여 시각적 웹 파트의 모양을 디자인할 수 있습니다. 자세한 내용은 디자이너 및 [빌딩 블록: 웹 파트를](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)) [사용하여 SharePoint 웹 파트 를 만드는 방법을 참조하세요.](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)

### <a name="web-part"></a>웹 파트
 *웹 파트는* 웹 파트 페이지라는 특별한 유형의 페이지 내에서 실행되는 서버 측 컨트롤입니다. SharePoint 사이트에 나타나는 페이지의 구성 요소입니다. 웹 부품 항목은 SharePoint 사이트에 대한 웹 파트를 디자인할 수 있는 파일을 제공합니다. 자세한 내용은 SharePoint 웹 파트 및 빌딩 [블록: 웹 파트](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)) [를 만드는 방법을 참조하세요.](../sharepoint/how-to-create-a-sharepoint-web-part.md)

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 제품 및 기술](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
