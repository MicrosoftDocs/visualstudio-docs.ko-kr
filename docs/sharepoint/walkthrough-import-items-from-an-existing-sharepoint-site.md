---
title: '연습: 기존 SharePoint 사이트에서 항목 가져오기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46bc2ceacfde599a70b4e84bba134c4a4d5f9757
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017119"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>연습: 기존 SharePoint 사이트에서 항목 가져오기
  이 연습에서는 기존 SharePoint 사이트에서 sharepoint 프로젝트로 항목을 가져오는 방법을 보여 줍니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 이 연습에서는 다음 작업을 수행합니다.

- 사용자 지정 사이트 열 ( *필드*라고도 함)을 추가 하 여 SharePoint 사이트 사용자 지정

- SharePoint 사이트를 .wsp 파일로 내보내기

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].Wsp 가져오기 프로젝트를 사용 하 여 .wsp 파일을 SharePoint로 가져오기

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 및 SharePoint의 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>SharePoint 사이트 사용자 지정
 이 예에서는 새 사이트 열을 추가 하 고 나중에 사용할 다른 하위 사이트를 만들어 SharePoint 하위 사이트를 만들고 사용자 지정 합니다. 나중에 첫 번째 하위 사이트를 .wsp 파일로 내보낸 다음 .wsp 가져오기 프로젝트를 사용 하 여 사용자 지정 사이트 열을 두 번째 하위 사이트에 가져옵니다.

### <a name="to-create-and-customize-a-sharepoint-site"></a>SharePoint 사이트를 만들고 사용자 지정 하려면

1. Http://<em>system name</em>/SitePages/Home.aspx.과 같은 웹 브라우저를 사용 하 여 SharePoint 사이트를 엽니다.

2. **사이트 작업** 메뉴를 연 다음 **새 사이트**를 선택 하 여 주 SharePoint 사이트에서 하위 사이트를 만듭니다.

3. 사이트의 **만들기** 대화 상자에서 **빈 사이트** 유형을 선택 합니다.

4. **제목** 상자에 **사이트 열 테스트 1**을 입력 합니다. **URL 이름** 상자에 **columntest1**;을 입력 합니다. 다른 설정은 기본값으로 둡니다. 그런 다음 **만들기** 단추를 선택 합니다.

5. 사이트를 만든 후 브라우저에서 기본 사이트인 http://<em>system name</em>/SitePages/Home.aspx.로 다시 이동 합니다.

6. **사이트 작업** 메뉴를 열고 **새 사이트**를 선택한 다음 **빈 사이트** 유형을 선택 하 여 주 SharePoint 사이트에서 빈 하위 사이트를 다시 만듭니다.

7. **제목** 상자에 **사이트 열 테스트 2**를 입력 합니다. **URL 이름** 상자에 **columntest2**;을 입력 합니다. 다른 설정은 기본값으로 둡니다. 그런 다음 **만들기** 단추를 선택 합니다.

8. 첫 번째 하위 사이트 (http://<em>SystemName</em>)로 다시 이동 합니다.

9. 사이트 **작업** 메뉴에서 사이트 **설정** 을 선택 하 여 사이트 설정 페이지를 표시 합니다.

10. **갤러리** 섹션에서 **사이트 열** 링크를 선택 합니다.

11. **사이트 열 갤러리** 페이지의 위쪽에서 **만들기** 단추를 선택 합니다.

12. **열 이름** 상자에 **테스트 열**을 입력 하 고 다른 기본값을 유지 한 다음 **확인** 단추를 선택 합니다.

13. **테스트 열** 열이 사이트 열 갤러리의 사용자 지정 열 제목 아래에 나타납니다.

## <a name="exporting-the-sharepoint-site"></a>SharePoint 사이트 내보내기
 다음으로 sharepoint 프로젝트로 가져올 sharepoint 항목 및 요소를 포함 하는 SharePoint 설치 파일 (.wsp)을 가져옵니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Wsp 파일이 아직 없는 경우 기존 SharePoint 사이트에서 만들어야 하는 것입니다. 이 예에서는 기본 SharePoint 사이트를 .wsp 파일로 내보냅니다.

> [!IMPORTANT]
> 다음 절차를 수행 하는 동안 런타임 오류가 발생 하는 경우 SharePoint 사이트에 대 한 액세스 권한이 있는 시스템에서 절차를 수행 해야 합니다.

### <a name="to-export-an-existing-sharepoint-site"></a>기존 SharePoint 사이트를 내보내려면

1. SharePoint 사이트의 사이트 **작업** 탭에서 사이트 **설정** 을 선택 하 여 사이트 설정 페이지를 표시 합니다.

2. 사이트 설정 페이지의 **사이트 작업** 섹션에서 **사이트를 템플릿으로 저장** 링크를 선택 합니다.

3. **파일 이름** 상자에 **ExampleSite**를 입력 하 고 **템플릿 이름** 상자에 **예제 사이트**를 입력 합니다.

4. 이 예에서는 **내용 포함** 확인란을 선택 하지 않은 상태로 둡니다.

     이 확인란을 선택 하면에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 모든 목록과 문서 라이브러리와 해당 내용을 .wsp 파일에 저장 합니다. 이는 일부 상황에서 유용 하지만이 예제에서는 필요 하지 않습니다.

5. 작업이 성공적으로 완료 되 면 **솔루션 갤러리** 링크를 선택 하 여 .wsp 파일을 봅니다.

     나중에 솔루션 갤러리 페이지를 보려면 사이트 **작업** 메뉴를 열고 사이트 **설정**을 선택한 다음 **사이트 모음 관리** 섹션에서 **최상위 수준 사이트 설정으로 이동** 링크를 선택 하 고 **갤러리** 섹션에서 **솔루션** 링크를 선택 합니다.

6. 솔루션 갤러리에서 **ExampleSite** 링크를 선택 합니다.

7. **파일 다운로드** 대화 상자에서 **저장** 단추를 선택 하 여 로컬 시스템의 다운로드 폴더에 파일을 저장 합니다.

## <a name="import-the-wsp-file"></a>.Wsp 파일 가져오기
 다시 사용 하려는 항목이 포함 된 *.wsp* 파일 (사용자 지정 사이트 열 테스트 열)이 있으므로 *.wsp* 파일을 가져와서 액세스 합니다.

### <a name="to-import-a-wsp-file"></a>.Wsp 파일을 가져오려면

1. 의 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 여 **새 프로젝트** 대화 상자를 표시 합니다. IDE가 Visual Basic 개발 설정을 사용 하도록 설정 된 경우 메뉴 모음에서 **파일**  >  **새로 만들기 프로젝트**를 선택 합니다.

2. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. **템플릿** 창에서 **SharePoint 2010 솔루션 패키지 가져오기** 템플릿을 선택 하 고 프로젝트 이름을 WspImportProject1로 두고 **확인** 단추를 선택 합니다.

    **SharePoint 사용자 지정 마법사** 가 나타납니다.

4. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 이전에 만든 두 번째 SharePoint 하위 사이트에 대 한를 입력 합니다. 새 사용자 지정 필드 항목인 http://<em>system name</em>/columntest2를 해당 하위 사이트에 추가 합니다.

5. **이 SharePoint 솔루션의 신뢰 수준** 섹션에서 선택 항목을 **샌드박스 솔루션으로 배포**로 유지 합니다.

6. **새 프로젝트 소스 지정** 페이지에서 *.wsp* 파일을 이전에 저장 한 시스템의 위치를 찾은 후 **다음** 단추를 선택 합니다.

   > [!NOTE]
   > 이 페이지에서 **마침** 단추를 선택 하면 *.wsp* 파일에서 사용 가능한 모든 항목을 가져옵니다.

7. **가져올 항목 선택** 상자에서 **테스트 열**을 제외 하 고 목록에 있는 모든 확인란의 선택을 취소 한 후 **마침** 단추를 선택 합니다.

    목록에 많은 항목이 포함 되어 있기 때문에 **Ctrl** + **A** 키를 선택 하 여 목록의 모든 항목을 선택 하 고 스페이스바 키를 선택 하 여 모든 확인란의 선택을 취소 한 다음 **테스트 열** 항목 옆의 확인란만 선택할 수 있습니다.

    가져오기 작업이 완료 되 면 이름이 **Fields**인 폴더를 포함 하는 **WspImportProject1** 라는 새 프로젝트가 만들어집니다. 이 폴더에는 사용자 지정 사이트 열 **테스트 열** 과 *Elements.xml*정의 파일이 있습니다.

## <a name="deploy-the-project"></a>프로젝트 배포
 마지막으로, 이전에 만든 두 번째 SharePoint 하위 사이트에 **WspImportProject1** 를 배포 하 여 사용자 지정 사이트 열을 확인 합니다.

### <a name="to-deploy-the-project"></a>프로젝트를 배포하려면

1. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **F5** 키를 선택 하 여 *.wsp* 가져오기 프로젝트를 배포 하 고 실행 합니다.

2. SharePoint 사이트에서 사이트 **작업** 메뉴를 연 다음 사이트 **설정** 을 선택 하 여 사이트 설정 페이지를 표시 합니다.

3. **갤러리** 섹션에서 **사이트 열** 링크를 선택 합니다.

4. **사용자 지정 열** 섹션까지 아래로 스크롤합니다.

     첫 번째 SharePoint 사이트에서 가져온 사용자 지정 사이트 열이 목록에 표시 됩니다.

## <a name="see-also"></a>참고 항목
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [웹 파트 또는 응용 프로그램 페이지의 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
