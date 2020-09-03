---
title: '연습: Visual Studio에 SharePoint Designer의 다시 사용 가능한 워크플로 가져오기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a589f14ea60d50c0062d85be81523f27c81b455
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015696"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>연습: Visual Studio에 SharePoint Designer의 다시 사용 가능한 워크플로 가져오기
  이 연습에서는 SharePoint Designer 2010에서 만든 재사용 가능한 워크플로를 sharepoint workflow 프로젝트로 가져오는 방법을 보여 줍니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 SharePoint 디자이너에서 만든 워크플로 또는 *선언적 워크플로*는 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 코드 대신 문으로 구성 됩니다. SharePoint Designer 2010은 *재사용 가능한 워크플로*를 소개 하며,이 워크플로는 sharepoint 사이트의 여러 목록에서 사용할 수 있는 이식 가능한 선언적 워크플로입니다.

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]순차 및 상태 시스템 워크플로와 같이에서 만든 워크플로를 *코드 워크플로*라고 합니다. 코드 워크플로는 사용자가 워크플로의 동작을 사용자 지정할 수 있는 XML 파일 및 코드 모듈로 구성 됩니다.

 Visual Studio에서는 SharePoint Designer 2010에서 만든 다시 사용할 수 있는 워크플로를 가져와서 SharePoint 사이트에서 사용할 수 있도록 코드 워크플로로 변환할 수 있습니다.

 이 연습에서는 다음 작업을 수행합니다.

- SharePoint 디자이너에서 간단 하 고 재사용 가능한 워크플로 만들기

- SharePoint Designer의 다시 사용 가능한 워크플로를 *.wsp* 파일 및 sharepoint로 내보내기

- *.wsp* [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 재사용 가능한 워크플로 가져오기 프로젝트를 사용 하 여 .wsp 파일을로 가져오기

- 코드를 추가 하 여 워크플로 변경

- 가져온 워크플로를 SharePoint 사이트에서 사용

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 및 SharePoint의 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>대상 SharePoint 하위 사이트 만들기
 먼저 두 개의 새 SharePoint 하위 사이트를 만듭니다. 하나는 SharePoint 디자이너에서 다시 사용할 수 있는 워크플로를 호스팅하고 다른 하나는 변환 된 워크플로를 호스트 하는 하위 사이트입니다.

#### <a name="to-create-sharepoint-subsites"></a>SharePoint 하위 사이트를 만들려면

1. SharePoint Designer 2010의 메뉴 모음에서 **파일**  >  **새로 만들기 빈 웹 사이트**를 선택 합니다.

2. **새 빈 웹 사이트** 대화 상자에서 워크플로를 만들 SharePoint 사이트를 찾아보거나 http://<em>SystemName</em>/값을 사용한 다음 **확인** 단추를 선택 합니다.

    홈 페이지가 나타납니다.

3. **하위 사이트** 섹션에서 **새로 만들기** 단추를 선택 합니다.

4. **새로 만들기** 대화 상자의 왼쪽 창에 있는 목록에서 **SharePoint 템플릿** 을 선택 하 고 오른쪽 창의 목록에서 **팀 사이트** 를 선택 합니다.

5. **웹 사이트의 위치 지정** 상자에서 URL의 **하위 사이트** 를 **SPD1**로 바꾼 다음 **확인** 단추를 선택 합니다.

    그러면 SharePoint Designer에 새 하위 사이트가 열립니다. SharePoint Designer의이 인스턴스를 닫은 다음 첫 번째 인스턴스 (최상위 사이트)로 돌아갑니다.

6. 3-5 단계를 반복 하 여 두 번째 하위 사이트를 만듭니다. 이번에는의 **하위 하위 사이트** 를 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] **SPD2**으로 바꿉니다.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer의 다시 사용 가능한 워크플로 만들기
 SharePoint에는이 예제에 사용할 수 있는 재사용 가능한 워크플로가 포함 되어 있지 않으므로 새로 만듭니다. 이 간단한 워크플로에서 사용자가 특정 제목이 있는 작업 목록에 새 작업을 입력 하면 해당 사용자에 게 태스크가 할당 됩니다.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer의 다시 사용 가능한 워크플로를 만들려면

1. **하위** 사이트 섹션에서 **SPD1** 사이트를 선택 하 여 수정 합니다.

2. 리본에서 **다시 사용할** 수 있는 워크플로 단추를 선택 합니다.

     다시 사용할 수 있는 워크플로 만들기 마법사가 나타납니다.

3. **이름** 상자에 **SPD 작업 워크플로**를 입력 합니다.

4. **콘텐츠 형식** 목록에서 **작업**을 선택한 다음 **확인** 단추를 선택 합니다.

     SharePoint Designer workflow designer에서 워크플로가 열립니다.

5. Workflow designer에서 1 단계를 선택한 다음 리본에서 **조건** 단추를 선택 합니다.

6. 조건 목록에서 **현재 항목 필드와 값이 같은지 여부**를 선택 합니다.

     이 단계에서는 **필드 값**이 인 경우 이름이 인 조건을 추가 합니다.

7. **필드와 값이 일치** 하는 경우 조건에서 **필드** 링크를 선택 합니다.

8. 값 목록에서 **제목**을 선택 합니다.

9. **If field equals 값** 조건에서 **값** 링크를 선택 합니다.

10. 상자에 **새 작업**을 입력 합니다.

     이제 condition 문이 **현재 항목: 제목이 새 작업 인 경우**를 읽습니다.

11. 조건문에서 줄을 선택한 다음 리본에서 **작업** 단추를 선택 합니다.

12. 작업 목록에서 **현재 항목의 필드 설정**을 선택 합니다.

13. **필드를 값으로 설정** 작업에서 **필드** 링크를 선택한 다음 목록에서 **담당자**를 선택 합니다.

14. **필드를 값으로 설정** 작업에서 **값** 링크를 선택한 다음 기존 사용자 및 그룹 목록에서 **항목을 만든 사용자**를 선택 합니다.

15. **추가** 단추를 선택한 다음 **확인** 단추를 선택 합니다.

     이제 action 문이 **할당 대상 Set을 현재 항목으로**읽습니다. CreatedBy.

## <a name="save-and-deploy-the-reusable-workflow"></a>재사용 가능한 워크플로 저장 및 배포
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]는 *.wsp* 파일만 가져올 수 있으므로 다시 사용 가능한 워크플로를 *.wsp* 파일로 저장 하 고를로 가져오기 전에 SharePoint에 배포 해야 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다.

> [!IMPORTANT]
> 다음 절차를 수행 하는 동안 런타임 오류가 발생 하는 경우 SharePoint 사이트에 대 한 액세스 권한이 있는 시스템에서 절차를 수행 해야 합니다.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>재사용 가능한 워크플로를 저장 하 고 배포 하려면

1. SharePoint 디자이너의 위쪽에서 **저장** 단추를 선택 하 여 진행 상황을 저장 한 다음 **게시** 단추를 선택 하 여 워크플로를 **SPD1** SharePoint 사이트에 배포 합니다.

2. 탐색 창에서 **워크플로** 개체를 선택 합니다.

3. **다시 사용할**수 있는 워크플로에서 **SPD 작업 워크플로**를 선택 합니다.

4. 리본에서 **템플릿으로 저장** 단추를 선택 하 여 워크플로를 *.wsp* 파일로 저장 합니다.

5. 브라우저에서 **SPD1** sharepoint 사이트를 열어 sharepoint의 *.wsp* 파일을 봅니다.

6. 빠른 실행 모음에서 **라이브러리** 링크를 선택 합니다.

7. **문서 라이브러리** 섹션에서 **사이트 자산** 링크를 선택 합니다.

     **SPD 작업 워크플로** 파일은 다른 사이트 자산과 함께 나열 됩니다.

8. 파일 목록에서 해당 파일의 이름을 선택합니다.

9. **파일 다운로드** 대화 상자에서 **저장** 단추를 선택 하 여 *.wsp* 파일을 로컬 시스템에 저장 합니다.

## <a name="import-the-wsp-file-into-visual-studio"></a>.Wsp 파일을 Visual Studio로 가져오기
 *.wsp* [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 재사용 가능한 워크플로 가져오기 프로젝트를 사용 하 여 .wsp 파일을로 가져옵니다. 이 프로젝트는 다시 사용할 수 있는 선언적 워크플로의 워크플로를 코드 워크플로로 변환 합니다. 워크플로를 변환한 후에는 코드를 사용 하 여 해당 동작을 수정 합니다.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>.Wsp 파일에서 워크플로를 가져오고 수정 하려면

1. 의 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic**아래의 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. **템플릿** 창에서 **재사용 가능한 SharePoint 2010 워크플로 가져오기** 템플릿을 선택 하 고 프로젝트 이름을 **WorkflowImportProject1**로 그대로 두고 **확인** 단추를 선택 합니다.

    SharePoint 사용자 지정 마법사가 나타납니다.

4. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 이전에 만든 두 번째 SharePoint 하위 사이트에 대해를 입력 합니다. Http://<em>system name</em>/SPD2.

5. **이 SharePoint 솔루션의 신뢰 수준을** 선택 하십시오. 섹션에서 **팜 솔루션으로 배포** 옵션 단추를 선택 하 고 **다음** 단추를 선택 합니다.

    샌드박스가 적용 된 솔루션과 팜 솔루션에 대 한 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

6. **새 프로젝트 소스 지정** 페이지에서 이전에 *.wsp* 파일을 저장 한 시스템의 위치로 이동 하 여 파일을 연 후에 **다음** 단추를 선택 합니다.

   > [!NOTE]
   > **[마침** ] 단추를 선택 하 여 *.wsp* 파일에서 사용 가능한 모든 항목을 가져옵니다.

    그러면 가져올 수 있는 재사용 가능한 워크플로 목록이 표시 됩니다.

7. **가져올 항목 선택** 상자에서 **SPD 작업 워크플로** 워크플로를 선택 하 고 **마침** 단추를 선택 합니다.

    가져오기 작업이 완료 되 면 **SPD_Workflow_TestFT**이라는 워크플로가 포함 된 **WorkflowImportProject1** 라는 프로젝트가 생성 됩니다. 이 폴더에는 워크플로의 정의 파일 *Elements.xml* 및 workflow designer 파일 (*xoml*)이 있습니다. 디자이너에는 두 개의 파일이 포함 됩니다. 규칙 파일 (. rules)과 코드 숨김이 파일 (프로젝트의 프로그래밍 언어에 따라 *.cs* 또는 *.vb*)입니다.

8. **솔루션 탐색기**에서 **다른 가져온 파일** 폴더를 삭제 합니다.

9. *Elements.xml* 파일에서를 삭제 `InstantiationURL="_layouts/IniErkflIP.sspx"` 합니다.

10. **솔루션 탐색기**에서 **WorkflowImportProject1**을 선택 하 고 메뉴 모음에서 **프로젝트**를  >  **시작 프로젝트로 설정** 을 선택 하 여 **WorkflowImportProject1** 를 시작 항목으로 설정 합니다.

     이렇게 하면 프로젝트를 디버그할 때 목록이 즉시 표시 됩니다.

11. **다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기** 템플릿은 가져온 워크플로에 대 한 연결 속성 값을 가져오지 않으므로 입력 해야 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1. **솔루션 탐색기**에서 **SPD_Workflow_TestFT** 노드를 선택 합니다.

    2. 목록 속성 중 하나 (예: **대상 목록** 속성) 옆에 있는 줄임표 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 선택 합니다.

    3. SharePoint 사용자 지정 마법사에서 누락 값을 입력 한 후 **마침** 단추를 선택 합니다.

12. Xoml 파일을 선택한 다음 메뉴 모음에서 **뷰**  >  **디자이너** 를 선택 하 여 워크플로 디자이너에서 가져온 워크플로를 확인 합니다.

13. **도구 상자**의 **Windows Workflow v 3.0** 노드에서 다음 단계 중 하나를 수행 합니다.

    - **코드** 작업에 대 한 바로 가기 메뉴를 열고 **복사**를 선택 합니다. Workflow designer에서 **SequenceActivity1** 활동 아래의 줄에 대 한 바로 가기 메뉴를 열고 **붙여넣기**를 선택 합니다.

    - **도구 상자** 의 **코드** 활동을 Workflow designer로 끌어 **SequenceActivity1** 활동 아래의 줄에 연결 합니다.

      그러면 **CodeActivity1**이라는 워크플로 디자이너에 활동이 추가 됩니다. 이 작업에서는 사용자가 워크플로를 시작할 때 공지 목록에서 알림을 만드는 코드 작업을 추가 합니다.

14. 다음 단계 중 하나를 수행합니다.

    - **CodeActivity1** 를 두 번 클릭 하 여 이벤트 처리기를 생성 하 고 코드를 확인 합니다.

    - **CodeActivity1**에 대 한 **속성** 창에서 **ExecuteCode** 속성의 값을 **codeActivity_ExecuteCode**로 설정 합니다.

15. 기존 **using** 또는 **Imports** 지시문 아래에 다음을 추가 합니다.

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. `codeActivity1_ExecuteCode`을 다음과 같이 바꿉니다.

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>프로젝트 배포 및 워크플로 연결
 그런 다음 WorkflowImportProject1를 실행 하 여 SharePoint 사이트에 배포한 다음 워크플로를 작업 목록과 연결 하 여 수정 된 변환 워크플로를 보고 테스트 합니다.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>프로젝트를 배포 하 고 워크플로를 연결 하려면

1. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **F5** 키를 선택 하 여 변환 된 워크플로 프로젝트를 실행 하 고 배포 합니다.

2. 빠른 실행 모음에서 작업 링크를 선택 하 **여 작업 목록을** 표시 합니다.

3. **목록 도구** 탭에서 **항목** 단추를 선택 하 고 **새 항목** 단추를 선택 합니다.

     **작업-새 항목** 대화 상자가 열립니다.

4. **제목** 상자에 **새 작업**을 입력 한 다음 **저장** 단추를 선택 합니다.

5. **목록 도구** 탭에서 **목록** 단추를 선택한 다음 **목록 설정** 단추를 선택 합니다.

     **목록 설정** 페이지가 나타납니다.

6. **사용 권한 및 관리** 섹션에서 **워크플로 설정** 링크를 선택 합니다.

     **워크플로 설정** 페이지가 나타납니다.

7. **워크플로 추가** 링크를 선택 합니다.

8. **워크플로** 목록에서 **WorkflowImportProject1-SPD 워크플로 테스트**를 선택 합니다.

9. **이름** 상자에 **SPD Workflow Test**를 입력 하 고 **확인** 단추를 선택 합니다.

10. 빠른 실행 모음에서 **작업** 목록을 선택 합니다.

11. **새 작업**옆의 화살표를 선택 하 고 목록에서 **워크플로**를 선택 합니다.

12. **새 워크플로 시작** 섹션에서 **SPD 워크플로 테스트**에 대 한 링크를 선택한 다음 **시작** 단추를 선택 하 여 워크플로를 시작 합니다.

    > [!NOTE]
    > 또는 워크플로 설정 마법사를 실행 하 고 워크플로를 자동으로 연결 하도록 설정 하 여 워크플로를 목록과 자동으로 연결할 수 있습니다.

     워크플로에서는 작업의 **할당 대상** 열에 이름이 표시 되 고 **공지** 목록에 알림이 표시 되는 것을 볼 수 있습니다.

## <a name="see-also"></a>추가 정보
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [웹 파트 또는 응용 프로그램 페이지의 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
