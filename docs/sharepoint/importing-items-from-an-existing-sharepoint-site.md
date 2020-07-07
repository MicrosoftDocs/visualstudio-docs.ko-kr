---
title: 기존 SharePoint 사이트에서 항목 가져오기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c2703bfdd4f47281a1fc19060cb69f8b312e7d2
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017032"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>기존 SharePoint 사이트에서 항목 가져오기
  SharePoint 솔루션 패키지 가져오기 프로젝트 템플릿을 사용하면 기존 SharePoint 사이트에 있는 콘텐츠 형식 및 필드 등의 요소를 새 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 솔루션에서 다시 사용할 수 있습니다. 수정 없이도 가져온 솔루션을 대부분 실행할 수 있지만 몇 가지 제한 및 문제를 고려해야 합니다. 항목을 가져온 후 수정한 경우에는 특히 주의해야 합니다.

> [!NOTE]
> 재사용 가능한 워크플로를 가져오려면 재사용 가능한 워크플로 가져오기 프로젝트 템플릿을 사용합니다. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][재사용 가능한 워크플로를 가져오는 방법에 대 한 지침](../sharepoint/guidelines-for-importing-reusable-workflows.md)입니다.

## <a name="supported-sharepoint-solutions"></a>지원 되는 SharePoint 솔루션
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 에서는 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 및 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]에서 만들어진 솔루션을 가져올 수 있습니다.

 다음 애플리케이션에서 만들어진 솔루션은[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 에서 가져올 수 없습니다.

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  이러한 애플리케이션에서 만든 솔루션을 가져올 수 있는 경우도 있지만 기능이 테스트되지 않아 지원되지 않습니다.

## <a name="item-import-restrictions"></a>항목 가져오기 제한 사항
 기존 *.wsp* 파일에서 대부분의 SharePoint 항목을 가져올 수 있지만 다음 항목은 지원 되지 않으며 제대로 작동 하기 위해 수정이 필요할 수 있습니다.

- BDC 엔터티

- 코드 워크플로 연결 요소

- 코드 워크플로

- 비주얼 웹 파트(.ascx)

- 웹 서비스 (*.asmx*)

- 콘텐츠 형식 바인딩

- 이벤트 수신자

- 목록 정의(템플릿)

- 사이트 정의

  또는에서 솔루션을 내보내면 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 이러한 항목이 *.wsp* 파일에서 자동으로 제외 됩니다. 그러나 지원 되지 않는 도구에서 생성 된 다른 *.wsp* 파일에는 이러한 항목이 포함 될 수 있습니다. 자세한 내용은 이 항목의 앞부분에 나오는 "지원되는 SharePoint 솔루션"을 참조하세요.

## <a name="what-happens-when-you-import-a-solution"></a>솔루션을 가져올 때 수행 되는 작업
 SharePoint 솔루션 패키지 가져오기 템플릿을 사용 하 여 솔루션을 가져올 때에서는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] *.wsp* 파일의 내용을 모두 복사 하 고 가져온 요소와 해당 파일 간의 연결 및 참조를 가능한 한 많이 조정 하 고 보존 하려고 합니다.

 가져온 항목은 모두 **솔루션 탐색기**의 해당 폴더에 복사됩니다. 예를 들어 콘텐츠 형식은 **콘텐츠 형식** 폴더 아래 나타나고 목록 인스턴스는 **목록 인스턴스**폴더 아래 나타납니다. 가져온 항목과 연결된 파일도 해당 항목 폴더로 복사됩니다. 예를 들어 가져온 목록 인스턴스에는 모듈, 양식 및 ASPX 페이지가 포함됩니다.

### <a name="dependent-items"></a>종속 항목
 SharePoint 솔루션 패키지 가져오기 마법사에서 항목을 선택했지만 종속 항목을 선택하지 않은 경우 가져오기 전에 종속 항목도 선택해야 한다는 메시지 상자가 나타납니다.

### <a name="what-are-features"></a>기능 이란?
 SharePoint 디자이너 사용자는 *솔루션 탐색기*에서 가져온 솔루션에 **기능** 이라는 예기치 않은 파일이 있는 것을 볼 수 있습니다. 기능은 SharePoint 디자이너 솔루션에 있었지만 화면에 표시되지 않았습니다. 이제 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에 기능이 표시됩니다.

 기능은 SharePoint 항목의 컨테이너입니다. 각 기능은 콘텐츠 형식 및 목록 정의 등 포함된 각 항목에 대한 참조를 유지합니다. 솔루션을 가져올 때 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서는 가져온 모든 요소에 대해 기능을 설정하고 파일에 대한 기능-요소 관계를 유지하려고 합니다. 참조를 확인할 수 없는 모든 파일은 **기타 가져온 파일** 폴더에 나타납니다.

 기능에 대 한 자세한 내용은 [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md) 및 [기능 사용](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14))을 참조 하세요.

### <a name="handle-special-cases"></a>특수 한 경우 처리
 Visual Studio에서 종속 파일이 있는 항목을 조정할 수 없는 경우가 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서 확인할 수 없는 모든 파일은 **기타 가져온 파일**폴더에 나타납니다. 또한 솔루션과 함께 배포되지 않도록 **DeploymentType** 속성이 **NoDeployment** 로 설정됩니다.

 예를 들어 목록 정의 ExpenseForms를 가져오는 경우 해당 이름의 목록 정의가 *Elements.xml* 및 *Schema.xml* 파일과 함께 **솔루션 탐색기** 의 **목록** 정의 폴더 아래에 나타납니다. 그러나 관련 ASPX 및 HTML 양식은 **기타 가져온 파일** 폴더의 **ExpenseForms** 폴더 아래 배치될 수 있습니다. 가져오기를 완료하려면 **솔루션 탐색기** 에서 이러한 파일을 ExpenseForms 목록 정의로 이동하고 각 파일의 **DeploymentType** 속성을 **NoDeployment** 에서 **ElementFile**로 변경합니다.

 이벤트 수신기를 가져올 때 *Elements.xml* 파일이 올바른 위치에 복사 되지만 솔루션과 함께 배포 되도록 어셈블리를 솔루션 패키지에 수동으로 포함 해야 합니다. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)]이 작업을 수행 하는 방법 방법 [: 추가 어셈블리 추가 및 제거](../sharepoint/how-to-add-and-remove-additional-assemblies.md)를 참조 하세요.

 워크플로를 가져오면 InfoPath 양식이 **기타 가져온 파일** 폴더에 복사됩니다. *.Wsp* 파일에 웹 템플릿이 포함 된 경우 **솔루션 탐색기**시작 페이지로 설정 됩니다.

## <a name="import-fields-and-property-bags"></a>필드 및 속성 모음 가져오기
 여러 필드를 포함 하는 솔루션을 가져오면 모든 개별 필드 정의가 **솔루션 탐색기** **필드**라는 노드 아래의 단일 *Elements.xml* 파일로 병합 됩니다. 마찬가지로 모든 속성 모음 항목은 **propertybags**이라는 노드의 *Elements.xml* 파일에 병합 됩니다.

 SharePoint에서 필드는 텍스트, 부울 또는 조회 같은 지정된 데이터 형식의 열입니다. 자세한 내용은 [구성 요소: 열 및 필드 형식](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14))을 참조하세요. 속성 모음을 사용하면 팜부터 SharePoint 사이트의 목록에 이르기까지 SharePoint의 개체에 속성을 추가할 수 있습니다. 속성 모음은 속성 이름 및 값의 해시 테이블로 구현됩니다. 자세한 내용은 [SharePoint 구성 관리](/previous-versions/msp-n-p/ff647766(v=pandp.10)) 또는 [SharePoint 속성 모음 설정](https://archive.codeplex.com/?p=pbs)을 참조하세요.

## <a name="delete-items-in-the-project"></a>프로젝트에서 항목 삭제
 SharePoint 솔루션의 대부분 항목에는 하나 이상의 종속 항목이 포함됩니다. 예를 들어 목록 인스턴스는 콘텐츠 형식에 종속되고 콘텐츠 형식은 필드에 종속됩니다. SharePoint 솔루션을 가져온 후 솔루션에서 항목을 삭제하고 종속 항목을 삭제하지 않은 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서는 솔루션을 배포할 때까지 참조 문제를 알리지 않습니다. 예를 들어 가져온 솔루션에 콘텐츠 형식에 종속된 목록 인스턴스가 있는데 해당 콘텐츠 형식을 삭제한 경우 배포 시 오류가 발생할 수 있습니다. 이 오류는 SharePoint 서버에 종속 항목이 없는 경우 발생합니다. 마찬가지로, 삭제 된 항목에도 관련 된 속성 모음이 있는 경우 **propertybags** *Elements.xml* 파일에서 해당 속성 모음 항목을 삭제 합니다. 따라서 가져온 솔루션에서 항목을 삭제하고 배포 오류가 발생한 경우 종속 항목도 삭제되어야 하는지 확인합니다.

## <a name="restore-missing-feature-attributes"></a>누락 된 기능 특성 복원
 솔루션을 가져올 때 가져온 기능 매니페스트에서 일부 선택적 기능 특성이 누락됩니다. 새 기능 파일에서 이러한 특성을 복원 하려는 경우 원래 기능 파일과 새 기능 매니페스트를 비교 하 여 누락 된 특성을 확인 하 고 [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)항목의 지침을 따릅니다.

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>기본 제공 목록 인스턴스에서 배포 충돌 검색이 수행 되지 않음
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 는 기본 제공 목록 인스턴스(SharePoint에서 제공하는 기본 목록 인스턴스)에서 배포 충돌 검색을 수행하지 않습니다. 충돌 검색을 수행하지 않는 이유는 SharePoint의 기본 제공 목록 인스턴스를 덮어쓰지 않기 위해서입니다. 기본 제공 목록 인스턴스는 계속 배포되거나 업데이트되지만 결코 삭제되거나 덮어 쓰이지는 않습니다. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint 패키징 및 배포 문제 해결](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)

## <a name="import-sharepoint-server-2010-workflows"></a>SharePoint Server 2010 워크플로 가져오기
 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]에서 만든 워크플로를 가져오면 배포 후 올바르게 실행되지 않습니다. 그 이유는 특정 어셈블리가 누락되고  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 워크플로 솔루션에서 현재 지원되지 않는 InfoPath 양식이 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로에 포함되었기 때문입니다. 그러나 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 어셈블리에 참조를 추가하고 InfoPath 양식에 다시 연결하는 등 일부 항목을 수정하여 가져온 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 워크플로가 올바르게 작동하도록 만들 수 있습니다. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint Server 2010 워크플로를 가져오는 중](/sharepoint/dev/)입니다.

## <a name="item-name-character-limit"></a>항목 이름 문자 제한
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서는 프로젝트 및 프로젝트 항목 이름에 경로를 포함하여 총 260자까지 포함할 수 있습니다. 솔루션을 가져올 때 항목 이름이 이 제한을 초과하면 오류가 발생합니다.

 **지정 된 경로, 파일 이름 또는 둘 다가 너무 깁니다. 정규화 된 파일 이름은 260 자 미만 이어야 하며, 디렉터리 이름은 248 자 미만 이어야 합니다.**

 이 오류가 발생하는 경우 항목이 만들어지지 않습니다. 이 문제는 모듈을 가져올 때 가장 자주 발생합니다. 이 문제를 방지하려면 다음을 수행합니다.

- **새 프로젝트 추가** 대화 상자에서 프로젝트 이름을 입력할 때 짧은 이름을 사용합니다.

- 경로가 짧아지도록 가능한 한 루트 폴더에 가까운 위치에 프로젝트를 만듭니다.

## <a name="the-sharepointproductversion-attribute"></a>SharePointProductVersion 특성
 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 또는 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]등 이전 버전의 SharePoint에서 만든 솔루션을 가져오는 경우 패키지 매니페스트의 SharePointProductVersion 특성 값을 12.0으로 변경하거나, 가져온 모든 웹 페이지에 스크립트 관리자 컨트롤을 삽입하고 SharePointProductVersion의 값 14.0을 그대로 유지합니다. 그렇지 않은 경우 가져온 웹 양식이 SharePoint에 표시되지 않습니다.

### <a name="background"></a>배경
 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 및 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 의 솔루션에는 SharePointProductVersion이라는 특성이 포함됩니다. SharePoint는 패키지 매니페스트에서 이 특성을 사용하여 솔루션을 디자인할 SharePoint 버전을 확인합니다. 두 유효한 값은 12.0 및 14.0입니다. 12.0 값은 항목이 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 또는 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]용으로 디자인되었다는 것을 나타내고, 14.0 값은 항목이 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 또는 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]용으로 디자인되었다는 것을 나타냅니다.

 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 및 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 에서 ASPX 페이지를 렌더링할 때 보안을 강화시키기 위해서는 모든 ASPX 또는 마스터 페이지에 스크립트 관리자 컨트롤이 있어야 합니다. 스크립트 관리자에 대한 자세한 내용은 [ScriptManager 컨트롤 개요](/previous-versions/bb398863(v=vs.140))를 참조하세요. 스크립트 관리자 컨트롤은 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 및 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]에서 사용할 수 없으므로 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 또는 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] 로 업그레이드된 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 또는 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]페이지에 추가해야 합니다. 표준 마스터 페이지에는 스크립트 관리자 컨트롤이 이미 추가되어 있으므로 표준 마스터 페이지를 사용하는 ASPX 페이지에는 스크립트 관리자 컨트롤이 필요하지 않습니다. 그러나 마스터 페이지를 사용하지 않거나 사용자 지정 마스터 페이지를 사용하는 ASPX 페이지를 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 또는 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]에서 사용하려면 스크립트 컨트롤을 추가해야 합니다.

 모든 새 프로젝트의 SharePointProductVersion 특성은 14.0으로 설정되기 때문에 스크립트 관리자 컨트롤이 없을 경우 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 또는 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] 프로젝트를 [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]으로 가져올 때 문제가 발생할 수 있습니다. 웹 양식이 있는 업그레이드된 프로젝트를 스크립트 관리자 없이 배포할 경우 SharePoint에 양식이 표시되지 않습니다.

## <a name="see-also"></a>참고 항목
- [연습: 기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [재사용 가능한 워크플로를 가져오기 위한 지침](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [연습: Visual Studio에 SharePoint Designer의 다시 사용 가능한 워크플로 가져오기](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
