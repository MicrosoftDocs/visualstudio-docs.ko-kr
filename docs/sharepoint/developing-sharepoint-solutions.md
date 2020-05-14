---
title: SharePoint 솔루션 개발 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7670f05fbeced78a0c77a8ffc053cf6b607708f
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586888"
---
# <a name="develop-sharepoint-solutions"></a>SharePoint 솔루션 개발
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서 여러 가지 SharePoint 프로젝트 형식 템플릿을 사용하여 SharePoint 사이트와 사이트 요소를 만들 수 있습니다. 사용 가능한 프로젝트 형식 목록은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)을 참조 하세요. SharePoint 프로젝트의 요소와 속성에 대한 설명은 다음과 같습니다.

 SharePoint 2013 및 SharePoint 추가 기능에 대한 자세한 내용은 [SharePoint 2013](https://www.microsoft.com/microsoft-365/previous-versions/microsoft-sharepoint-2013) 및 [SharePoint 추가 기능 빌드](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)를 참조하세요.

## <a name="elements-of-a-sharepoint-project"></a>SharePoint 프로젝트의 요소
 SharePoint 프로젝트 아래에 있는 노드를 *SharePoint 항목*이라고 합니다. SharePoint 항목에는 *SharePoint 항목 파일*이라는 하위 파일이 하나 이상 포함될 수 있습니다(예: [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 구성 파일, .aspx 양식 등).

 프로젝트 항목 파일로 채워져 있는 프로젝트 템플릿을 사용하여 프로젝트를 만드는 대신, **빈 프로젝트** 템플릿을 사용하여 빈 SharePoint 프로젝트를 만들고 프로젝트 항목을 수동으로 추가할 수 있습니다. SharePoint 프로젝트에는 선택적으로 SharePoint에서 활성화에 사용되는 기능 파일 하나 이상과 프로젝트를 배포할 패키지 파일이 포함될 수 있습니다.

### <a name="special-nodes"></a>특수 노드
 모든 SharePoint 프로젝트에는 프로젝트에서 이름을 바꾸거나, 삭제하거나, 잘라내거나, 복사하거나, 끌어서 놓을 수 없는 노드 두 개가 포함됩니다. 이들 노드는 다음과 같습니다.

- 기능
- 패키지

  프로젝트에 대한 기능이나 패키지가 정의되지 않더라도 두 노드는 모두 항상 모든 SharePoint 프로젝트에 표시됩니다.

#### <a name="features-node"></a>기능 노드
 **기능** 노드에는 SharePoint 프로젝트 기능이 하나 이상 포함됩니다. 기능은 SharePoint용 확장의 컨테이너입니다. 기능이 SharePoint 서버에 배포되고 나면 SharePoint 사이트에서 SharePoint 관리자가 기능을 사이트 정의에 포함하거나 개별적으로 활성화할 수 있습니다. 자세한 내용은 [기능 작업](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14))을 참조하세요.

 콘텐츠 형식이나 목록 인스턴스와 같은 항목을 SharePoint 프로젝트에 추가하면 해당 항목은 **기능** 노드의 기능에 추가됩니다. 항목 범위에 따라 새 기능 또는 기존 기능에 추가되는지 결정됩니다. 새 항목의 범위가 기존 기능 범위와 같으면 새 항목은 기존 기능에 추가됩니다. 그러지 않으면 항목이 새 기능에 추가됩니다.

 기능을 수동으로 추가하려면 기능 노드의 바로 가기 메뉴에서 **기능 추가** 명령을 실행합니다. 기능 디자이너를 사용하여 기능 콘텐츠를 보거나 변경할 수 있습니다. 자세한 내용은 [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)을 참조 하세요.

 기능이 SharePoint 프로젝트에 추가되면 **솔루션 탐색기** 에 기본 이름인 Feature*x*.feature를 사용한 노드로 표시됩니다. 여기서 *x* 는 고유 번호입니다. 기능이 SharePoint 서버에 배포되고 나면 SharePoint 관리자가 기능을 활성화하여 SharePoint 사이트 사용자가 사용 가능하도록 설정할 수 있습니다.

#### <a name="package-node"></a>패키지 노드
 **패키지** 노드에는 SharePoint 프로젝트에 대한 배포 메커니즘으로 사용하는 단일 파일이 포함됩니다. *솔루션 패키지*라고 하는이 파일은입니다. 을 사용 하는 CAB 기반. WSP 확장. 솔루션 패키지는 SharePoint 사이트에 적용되는 기능 집합, 사이트 정의 및 어셈블리가 포함되고 개별적으로 사용하거나 사용하지 않도록 설정할 수 있는 배포 가능하고 재사용 가능한 파일입니다. **패키지** 노드에는 항상 패키지에 대한 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 정의 파일인 Package.wspdef라는 파일이 포함됩니다. 패키지가 SharePoint를 실행하는 서버에 배포되고 나면 SharePoint 관리자가 패키지를 설치하고 해당 기능을 활성화할 수 있습니다.

 패키지 노드를 두 번 클릭 하거나 바로 가기 메뉴를 연 다음 **열기**를 선택 하 여 패키지 디자이너에서 패키지의 내용을 보거나 변경할 수 있습니다. 자세한 내용은 [SharePoint 솔루션 패키지 만들기](../sharepoint/creating-sharepoint-solution-packages.md)를 참조 하세요.

## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint 프로젝트 및 프로젝트 항목 속성
 SharePoint 프로젝트는 다른 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로젝트와 마찬가지로 속성 창과 속성 페이지에 속성이 표시됩니다. 표시되는 속성은 선택된 노드에 따라 달라집니다.

 **솔루션 탐색기**에서 SharePoint 프로젝트, 프로젝트 항목 또는 프로젝트 항목 파일 노드를 선택하면 속성 창이나 속성 페이지에 다음 속성이 표시됩니다.

### <a name="project-properties"></a>프로젝트 속성

|속성 이름|설명|
|-------------------|-----------------|
|활성 배포 구성|배포하는 동안 수행되는 일련의 단계를 지정합니다. 자세한 내용은 [방법: SharePoint 배포 구성 편집](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)을 참조 하세요.|
|어셈블리 배포 대상|*SharePoint 애플리케이션 어셈블리* 가 배치되는 위치를 결정합니다. 올바른 어셈블리 위치 값은 *GlobalAssemblyCache* (기본값) 또는 *WebApplication*입니다.<br /><br /> *Sandboxed Solution* 속성을 **true**로 설정하면 이 속성이 사용하지 않도록 설정됩니다.|
|디버깅 후 자동 취소|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 디버그 모드로 애플리케이션을 실행하고 나서 SharePoint에서 배포된 솔루션을 자동으로 취소할지를 지정합니다. 이 옵션을 선택하면 디버그한 후 IDE가 디자인 뷰로 돌아가면 솔루션이 취소됩니다. 이 옵션의 선택을 취소하면 솔루션이 취소되지 않습니다. 자세한 내용은 [솔루션 취소](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14))를 참조하세요.|
|구성 편집|프로젝트에 사용할 배포 구성을 지정합니다. 자세한 내용은 [방법: sharepoint 배포 구성 편집](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) 및 [Sharepoint 솔루션 패키지 배포, 게시 및 업그레이드](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)를 참조 하세요.|
|스크립트 디버깅 대신 Silverlight 디버깅 사용|이 옵션을 선택하면 Silverlight 디버거가 디버깅 프로세스에 연결됩니다. 이 옵션의 선택을 취소하면 스크립트 디버거가 디버깅 프로세스에 연결됩니다. 자세한 내용은 [Silverlight 디버깅 개요](/previous-versions/windows/)를 참조하세요.|
|패키지에 어셈블리 포함|빌드 시간에 프로젝트 어셈블리를 패키지할지를 지정합니다.|
|배포 후 명령줄|SharePoint 솔루션을 배포한 후에 실행할 명령을 지정합니다. 이 명령줄은 MSBuild 변수 및 모든 배치 명령을 지원합니다. 자세한 내용은 [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md)을 참조하세요.|
|배포 전 명령줄|SharePoint 솔루션을 배포하기 전에 실행할 명령을 지정합니다. 이 명령줄은 MSBuild 변수 및 모든 배치 명령을 지원합니다. 자세한 내용은 [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md)을 참조하세요.|
|프로젝트 파일|프로젝트에 대한 빌드, 구성 및 기타 정보가 들어 있는 파일의 이름입니다.|
|프로젝트 폴더|시스템에서 프로젝트 파일의 위치입니다. 읽기 전용입니다.|
|Sandboxed Solution|프로젝트를 *사용자가 만든 솔루션*이라고도 하는 *샌드박스 솔루션*으로 배포할지를 지정합니다. 샌드박스 솔루션을 신뢰할 수 있어야 할 필요는 없습니다. **true** 값은 프로젝트가 샌드박스 솔루션으로 배포됨을 의미하고 **false** 값은 프로젝트가 팜 솔루션으로 배포됨을 의미합니다. 자세한 내용은 [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) 및 [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)를 참조하세요.|
|사이트 URL|이 프로젝트에 대한 대상 사이트의 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 을(를) 지정합니다.|
|시작 항목|프로젝트에서 실행할 첫 번째 항목을 지정합니다.|

 SharePoint 항목 파일(예: 기능 노드의 기능 또는 워크플로)을 선택하면 다음 속성이 속성 창에 표시됩니다.

### <a name="project-item-properties"></a>프로젝트 항목 속성

|속성 이름|설명|
|-------------------|-----------------|
|배포 충돌 해결|서버에 있는 항목의 속성과 일치하는 속성을 가진 프로젝트 항목을 배포할 때 수행할 작업을 지정합니다. 자세한 내용은 [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)을 참조하세요.|
|기능 속성|SharePoint에 배포될 때 기능과 함께 제공되는 값 집합(키/값 쌍으로 저장됨)을 지정합니다. 기능이 배포되고 나서 코드에서 속성 값에 액세스할 수 있습니다. 자세한 내용은 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조하세요.|
|기능 수신기|프로젝트 항목의 포함 기능에 대한 특정 이벤트가 발생할 때 실행되는 코드를 제공합니다. 자세한 내용은 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조하세요.|
|폴더 이름|SharePoint 프로젝트 항목 폴더의 이름입니다.|
|프로젝트 출력 참조|프로젝트 항목이 실행해야 하는 어셈블리 등의 종속성을 지정합니다. 자세한 내용은 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조하세요.|
|안전 컨트롤 항목|신뢰할 수 없는 사용자가 편집할 안전한 컨트롤을 지정합니다. 자세한 내용은 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조하세요.|

### <a name="project-item-file-properties"></a>프로젝트 항목 파일 속성

|속성 이름|설명|
|-------------------|-----------------|
|빌드 동작|파일이 빌드 및 배포 프로세스와 연결되는 방법을 지정합니다. 자세한 내용은 [파일 속성](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))을 참조하세요.|
|출력 디렉터리로 복사|소스 파일을 출력 디렉터리로 복사할 것인지를 지정합니다. 다음 값 중 하나일 수 있습니다.<br /><br /> -   *복사 안 함*<br />-   *항상 복사*<br />-   *새 버전이 면 복사*<br /><br /> 자세한 내용은 [파일 속성](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))을 참조하세요.|
|사용자 지정 도구|디자인 타임에 파일을 변환하고 변환 출력을 다른 파일에 저장하는 도구의 이름을 지정합니다. 예를 들어 데이터 세트(.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) 파일에는 기본 사용자 지정 도구가 있습니다. 자세한 내용은 [파일 속성](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))을 참조하세요.|
|사용자 지정 도구 네임스페이스|사용자 지정 도구의 출력이 복사될 네임스페이스입니다. 자세한 내용은 [파일 속성](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))을 참조하세요.|
|배포 위치|SharePoint 서버에서 파일의 정규화된 경로입니다. 이 경로는 배포 루트 및 배포 경로 하위 속성으로 구성됩니다.|
|배포 경로|SharePoint 서버 파일에서 파일의 상대 경로 (예: Workflow1.vb\\)입니다. 파일에 대한 정규화된 경로는 *Deployment Path* 값을 *Deployment Root* 값의 끝에 연결해서 만듭니다.<br /><br /> *배포 유형* 속성에 *대해 rootfile* 값을 선택 하면 *배포 루트* 속성이 \<SharePointRoot>\\로 변경 되어 SharePointRoot> \workflow1 \<\\의 정규화 된 경로가 생성 됩니다. 자세한 내용은 [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)를 참조 하세요.|
|Deployment Root|문자열입니다. SharePoint 서버에서 파일이 배포되는 루트 폴더입니다. 예를 \<들어 SharePointRoot>\\\<\template\features>\\입니다.<br /><br /> *Deployment Root* 속성 값은 *Deployment Type* 설정에 따라 결정됩니다.|
|배포 유형|*Deployment Root* 값을 결정하는 파일의 배포 유형입니다. 다음 값 중 하나일 수 있습니다.<br /><br /> Nodeployment: * \<값 없음>*<br /><br /> Elementmanifest: * \<SharePointRoot>\\\<\omFeatureName>*\\<br /><br /> Elementfile: * \<SharePointRoot>\\\<\template\features>\\*<br /><br /> 템플릿 파일: * \<SharePointRoot> \template\\*<br /><br /> Rootfile: * \<SharePointRoot>\\*<br /><br /> Globalresource: * \<SharePointRoot> \resources\\*<br /><br /> Classresource: * \<ClassResourcePath>\\*<br /><br /> 자세한 내용은 <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>를 참조하세요.|
|파일 이름|항목 파일에 대한 파일 또는 폴더의 이름입니다.|
|전체 경로|항목에 대한 파일의 위치입니다. 읽기 전용입니다.|

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 사용할 수 있는 SharePoint 프로젝트 및 프로젝트 항목 템플릿에 대해 설명합니다.|
|[방법: SharePoint 프로젝트에 항목 추가](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|기존 또는 새 항목을 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트에 추가하는 방법을 설명합니다.|
|[연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|고객 필드, 콘텐츠 형식, 목록 정의 및 목록 인스턴스를 만드는 과정을 단계별로 안내합니다.|
|[방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)|[연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)에서 만든 프로젝트에 대 한 이벤트 수신기를 추가 하는 방법에 대해 설명 합니다.|
|[SharePoint 워크플로 솔루션 만들기](../sharepoint/creating-sharepoint-workflow-solutions.md)|워크플로 연결 양식과 워크플로 시작 양식을 포함하는 워크플로 프로젝트를 만드는 방법을 설명합니다.|
|[SharePoint에 대 한 페이지 만들기](../sharepoint/creating-pages-for-sharepoint.md)|SharePoint에 대한 애플리케이션 페이지, 사이트 페이지, 마스터 페이지, 페이지 레이아웃과 같은 페이지를 만드는 방법을 설명합니다.|
|[SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)|사용자가 브라우저를 사용하여 직접 SharePoint 사이트 페이지의 콘텐츠, 모양 및 동작을 수정할 수 있도록 컨트롤을 추가하는 방법을 설명합니다.|
|[웹 파트 또는 응용 프로그램 페이지의 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|SharePoint에서 실행되는 애플리케이션 페이지 및 웹 파트에서 사용할 수 있는 사용자 컨트롤을 만드는 방법을 설명합니다.|
|[SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)|Web services 및 백 엔드 서버 애플리케이션의 데이터를 SharePoint 애플리케이션에 통합하는 방법을 설명합니다.|
|[SharePoint에 대 한 사이트 정의 만들기](../sharepoint/creating-site-definitions-for-sharepoint.md)|SharePoint 사이트를 만드는 데 사용되는 사이트 정의: 템플릿을 만드는 방법을 설명합니다.|
|[기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|기존 SharePoint 사이트의 콘텐츠 형식 및 모듈 같은 항목을 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트로 가져오는 방법을 설명합니다.|
|[모듈을 사용하여 솔루션에 파일 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md)|모듈을 사용하여 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로젝트의 파일을 SharePoint 사이트에 배포하는 방법을 설명합니다.|
|[서버 탐색기를 사용 하 여 SharePoint 연결 찾아보기](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|서버 탐색기를 사용하여 로컬 SharePoint 사이트를 찾아보는 방법을 설명합니다.|
|[프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|프로젝트 항목 속성을 사용하여 안전 컨트롤 항목, 프로젝트 출력 참조 및 기능 속성과 같은 프로젝트에 대한 패키징 및 배포 정보를 제공하는 방법을 설명합니다.|
|[방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)|SharePoint 리소스에 더 쉽게 액세스할 수 있도록 매핑된 폴더를 프로젝트에 추가하는 방법을 설명합니다.|
|[샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)|샌드박스 솔루션과 관련된 문제에 대해 설명합니다.|
|[SharePoint 솔루션 보안](../sharepoint/security-for-sharepoint-solutions.md)|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 SharePoint 솔루션을 개발하기 위한 보안 고려 사항을 설명합니다.|
|[URL 선택기 대화 상자는 Visual Studio에서 SharePoint 개발을 &#40;&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|프로젝트 또는 로컬 SharePoint 서버의 리소스에 경로 참조를 추가하는 데 사용할 수 있는 대화 상자에 대해 설명합니다.|

## <a name="see-also"></a>참고 항목
- [Visual Studio에서 SharePoint 개발 &#40;시작&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [서버 탐색기를 사용 하 여 SharePoint 연결 찾아보기](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
