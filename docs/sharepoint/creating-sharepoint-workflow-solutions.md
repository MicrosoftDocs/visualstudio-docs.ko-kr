---
title: SharePoint 워크플로 솔루션 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c787009577735213437140513ec095f81c3f43b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015286"
---
# <a name="create-sharepoint-workflow-solutions"></a>SharePoint 워크플로 솔루션 만들기

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]는 SharePoint 웹 사이트의 문서 및 목록 항목의 수명 주기를 관리 하는 사용자 지정 워크플로를 만드는 데 도움이 되는 도구를 제공 합니다. 제공되는 항목에는 디자이너, 작업 컨트롤 집합 및 필수 어셈블리 참조가 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에는 워크플로를 만들고 구성 하는 데 도움이 되는 **SharePoint 사용자 지정 마법사**도 포함 되어 있습니다.

SharePoint에 대 한 자세한 내용은 [Microsoft Sharepoint 제품 및 기술](/sharepoint/dev/)(영문)을 참조 하십시오.

## <a name="workflows-in-sharepoint"></a>SharePoint의 워크플로
 SharePoint 라이브러리나 목록에 워크플로를 추가 하는 경우 라이브러리나 목록의 모든 항목에 비즈니스 프로세스를 적용 합니다. 워크플로는 편집 하 고 검토할 항목을 보내는 등 시스템이 각 항목에 대해 수행 해야 하는 작업을 설명 합니다. *활동*이라고 하는 이러한 작업은 워크플로의 구성 요소입니다.

 에서 SharePoint 워크플로를 만들어 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sharepoint 웹 사이트에 배포할 수 있습니다. SharePoint에 워크플로를 배포한 후 라이브러리 또는 목록과 연결 합니다. 그런 다음 사용자가 프로세스를 통해 자동으로 또는 수동으로 시작할 수 있습니다. 워크플로 작업에 대 한 자세한 내용은 [Visual Studio를 사용 하 여 SharePoint 워크플로 개발](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio)을 참조 하세요.

## <a name="create-custom-sharepoint-workflows"></a>사용자 지정 SharePoint 워크플로 만들기
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **순차 워크플로** 및 **상태 시스템 워크플로**에서 두 SharePoint 워크플로 프로젝트를 사용할 수 있습니다.

 *순차 워크플로* 는 일련의 단계를 나타냅니다. 마지막 작업이 완료 될 때까지 단계를 한 단계 더 수행 합니다. 순차 워크플로는 항상 실행 시 엄격 하 게 순차적으로 수행 됩니다. 외부 이벤트를 받을 수 있고 병렬 논리 흐름을 포함할 수 있기 때문에 정확한 실행 순서는 달라질 수 있습니다. 다음 그림에서는 순차 워크플로의 예를 보여 줍니다.

 ![순차적 워크플로](../sharepoint/media/sp-sequential.png "순차적 워크플로")

 *상태 시스템 워크플로* 는 상태, 전환 및 작업의 집합을 나타냅니다. 상태 시스템 워크플로의 단계는 비동기적으로 실행 됩니다. 즉, 다른 작업을 수행 하지 않아도 되며, 대신 작업 및 상태에 의해 트리거됩니다. 한 상태가 시작 상태로 지정 된 다음 이벤트에 따라 다른 상태로 전환 됩니다. 상태 시스템은 워크플로의 끝을 결정 하는 최종 상태를 가질 수 있습니다. 다음 다이어그램은 상태 시스템 워크플로의 예를 보여 줍니다.

 ![정적 컴퓨터 워크플로](../sharepoint/media/sp-state.png "정적 컴퓨터 워크플로")

 워크플로 유형에 대 한 자세한 내용은 [워크플로 유형](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14))을 참조 하세요.

### <a name="use-the-wizard"></a>마법사 사용
 에서 SharePoint 워크플로 프로젝트를 만드는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 먼저 **Sharepoint 사용자 지정 마법사**에서 해당 설정을 지정 합니다. 마법사는 이러한 설정을 사용 하 여 **솔루션 탐색기**에서 프로젝트를 만듭니다. 이 프로젝트에는 코드 파일, 워크플로를 배포 하는 데 사용 되는 여러 파일 및 사용자 지정 SharePoint 워크플로를 만드는 데 필요한 어셈블리에 대 한 참조가 포함 되어 있습니다.

 워크플로를 만든 후 속성 창에서 해당 속성을 수정할 수 있습니다. 대부분의 워크플로 속성은 속성 창에서 직접 변경할 수 있지만 일부 경우에는 줄임표 단추 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))를 클릭 하 여 값을 변경 해야 합니다. 이 단추를 클릭 하면 **SharePoint 사용자 지정 마법사**가 다시 시작 됩니다. 속성 값을 변경한 후 **마침** 단추를 선택 하 여 종료 합니다.

> [!NOTE]
> **워크플로 유형** 속성은 읽기 전용 이며 변경할 수 없습니다. 워크플로 유형을 변경 하려면 다른 워크플로를 만들어야 합니다.

## <a name="design-a-sharepoint-workflow"></a>SharePoint 워크플로 디자인
 비즈니스 프로세스의 모든 단계를 정의한 후에는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] workflow designer를 사용 하 여 SharePoint 워크플로를 디자인 합니다. 디자이너를 열려면 **솔루션 탐색기**에서 Workflow1.cs 또는 workflow1.vb를 두 번 클릭 하거나 이러한 파일 중 하나에 대 한 바로 가기 메뉴를 연 다음 **열기**를 선택 합니다.

### <a name="activities"></a>활동
 워크플로를 디자인 하려면 디자이너의 *워크플로 일정* 에 **도구 상자** 의 활동을 추가 합니다. 워크플로 일정은 수행 해야 하는 순서 대로 작업 시퀀스를 포함 합니다.

 활동에는 다음 두 가지 유형이 있습니다.

- *간단한 작업* 은 "1 일 지연" 또는 "웹 서비스 시작"과 같은 단일 작업 단위를 수행 합니다.

- *복합 활동* 에는 다른 활동이 포함 되어 있습니다. 예를 들어 조건부 활동에는 두 개의 분기가 포함 될 수 있습니다.

  두 가지 유형의 활동 모두 **도구 상자**에서 사용할 수 있습니다.

  활동에는 속성, 메서드 및 이벤트가 있을 수 있습니다. **속성** 창을 사용 하 여 활동의 속성을 설정할 수 있습니다.

  사용자 지정 작업을 만들 수도 있습니다. 자세한 내용은 [연습: 사용자 지정 사이트 워크플로 작업 만들기](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)를 참조 하세요.

  활동은 **도구 상자**의 다음 탭에서 구성 됩니다.

- **SharePoint 워크플로**

- **Windows Workflow v 3.0**

- **Windows Workflow v 3.5**

  모든 핵심 워크플로 작업이 SharePoint에서 지원 되는 것은 아닙니다. 자세한 내용은 [Windows SharePoint Services에 대 한 워크플로 작업 개요](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))를 참조 하세요.

#### <a name="sharepoint-workflow-activities"></a>SharePoint 워크플로 작업
 **SharePoint 워크플로** 탭에는에서 사용할 특수 한 작업이 포함 되어 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 있습니다. 이러한 활동은 문서 수명 주기 워크플로 개발을 간소화 하 고 간소화 합니다. **Sharepoint 워크플로** 탭에 나열 된 작업에 대 한 자세한 내용은 [Windows sharepoint Services에 대 한 워크플로 작업 개요](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))를 참조 하세요.

#### <a name="windows-workflow-activities"></a>Windows 워크플로 작업
 **Windows Workflow** 탭에는에서 제공 하는 활동이 포함 되어 [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] 있습니다. 이러한 활동을 사용 하 여 모든 종류의 Windows workflow 응용 프로그램에 대 한 워크플로 일정을 만들 수 있습니다.

 **Windows 워크플로** 탭에 나열 된 작업에 대 한 자세한 내용은 [Windows Workflow Foundation 작업](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90))을 참조 하세요. Windows Workflow Foundation에 대 한 자세한 내용은 [Windows Workflow Foundation 개요](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90))를 참조 하세요.

### <a name="work-with-activities-in-the-designer"></a>디자이너에서 활동 작업
 워크플로 일정은 Windows 워크플로 활동 및 SharePoint 워크플로 활동의 조합을 포함할 수 있습니다.

 디자이너는 활동의 위치를 올바르게 설정 하 고 구성 하는 데 도움이 되는 시각 신호를 표시 합니다. 작업을 워크플로 일정으로 끌거나 복사하면 워크플로에서 해당 작업의 올바른 위치를 보여 주는 녹색 더하기 기호(+) 아이콘이 디자이너에 표시됩니다. 활동을 유효 하지 않은 위치에 배치할 수 없습니다. 예를 들어 Send 활동을 Listen 활동 분기의 첫 번째 활동으로 배치할 수 없습니다. 자세한 내용은 [SharePoint Designer Developer Center](https://developer.microsoft.com/office/docs)를 참조 하세요.

## <a name="collect-information-during-the-workflow"></a>워크플로 중 정보 수집
 워크플로에서 미리 정의 된 시간에 사용자 로부터 정보를 수집 하는 것이 좋습니다. 양식 또는 항목 속성을 사용 하 여 정보를 수집할 수 있습니다.

### <a name="forms"></a>양식
 양식은 질문을 포함 하 고 사용자가 답변을 제공 하는 방법을 제공 하는 대화 상자와 같습니다.

 워크플로에서 사용할 수 있는 폼에는 다음 네 가지 유형이 있습니다.

- 연결

- 시작

- 수정

- Task

  이러한 항목에는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 연결 및 초기화 폼에 대 한 항목 템플릿이 포함 되어 있습니다. *연결 양식의* 예로는 워크플로를 설치 하는 관리자가 비용 워크플로에 대 한 지출 한도와 같이 워크플로와 관련 된 매개 변수를 입력할 수 있습니다. *시작 양식의* 예는 비용 워크플로의 사용자가 워크플로에 소요 된 금액을 입력할 수 있는 것입니다. 이러한 형식의 폼에 대 한 자세한 내용은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)을 참조 하세요.

### <a name="item-properties"></a>항목 속성
 SharePoint 라이브러리나 목록의 항목 속성을 사용 하 여 사용자 로부터 정보를 수집할 수도 있습니다. 주 코드 파일 (Workflow1.cs 또는 Workflow1.vb)은 이름이 인 Microsoft. SPWorkflowActivationProperties 클래스의 인스턴스를 선언 `workflowProperties` 합니다. 개체를 사용 `workflowProperties` 하 여 코드에서 라이브러리 또는 목록의 속성에 액세스할 수 있습니다. 예제는 [연습: SharePoint 워크플로 솔루션 만들기 및 디버그](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)를 참조 하세요.

## <a name="debug-a-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿 디버그
 다른 웹 기반 프로젝트를 디버깅할 때와 동일한 방법으로 SharePoint 워크플로 프로젝트를 디버그할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 디버거를 시작 하면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Sharepoint 사용자 지정 마법사** 에서 지정한 설정을 사용 하 여 해당 sharepoint 웹 사이트를 열고 해당 라이브러리 또는 목록과 워크플로 템플릿을 자동으로 연결 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]또한는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] *w3wp.exe*이라는 프로세스에 디버거를 연결 합니다.

 워크플로를 테스트 하려면 워크플로를 수동으로 시작 해야 합니다. 자세한 내용은 [SharePoint 솔루션 디버깅](../sharepoint/debugging-sharepoint-solutions.md)의 "워크플로 디버깅" 섹션을 참조 하세요. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]웹 응용 프로그램 디버깅에 대 한 자세한 내용은 [웹 응용 프로그램 및 스크립트 디버그](../debugger/how-to-enable-debugging-for-aspnet-applications.md)를 참조 하세요.

## <a name="deploy-a-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿 배포
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 워크플로 프로젝트는 다른 sharepoint 프로젝트와 마찬가지로 배포 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 됩니다. 자세한 내용은 [SharePoint 솔루션 패키지 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)를 참조 하세요.

## <a name="import-globally-reusable-workflows"></a>전역적으로 재사용 가능한 워크플로 가져오기
 SharePoint Designer를 사용 하면 사이트별로 재사용 가능한 워크플로를 만들 수 있을 뿐 아니라 *전 세계에서 다시 사용할*수 있는 워크플로를 만들 수 있습니다 .이 워크플로는 모든 sharepoint 사이트에서 사용할 수 있습니다. 현재의 다시 사용 가능한 워크플로 가져오기 프로젝트는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 전역적으로 재사용 가능한 워크플로를 가져오지 않습니다. 그러나 SharePoint 디자이너를 사용 하 여 전역적으로 재사용 가능한 워크플로를 재사용 가능한 워크플로로 변환 하거나 워크플로를 변환 되지 않은 선언적 워크플로로 가져올 수 있습니다. 자세한 내용은 [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)를 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[연습: SharePoint 워크플로 솔루션 만들기 및 디버깅](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|간단한 워크플로를 만들고 디버깅 하는 과정을 단계별로 안내 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다.|
|[연습: 연결 및 초기화 폼이 있는 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|연결 및 초기화 폼을 사용 하 여 완전 한 기능을 갖춘 워크플로 전체를 만드는 과정을 단계별로 안내 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다.|
|[연습: 워크플로에 응용 프로그램 페이지 추가](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|연습: 워크플로에 입력 한 데이터에 대해 보고 하는 추가 *.aspx* 응용 프로그램 페이지를 추가 하 여 [연결 및 초기화 폼이 있는 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) 항목을 기반으로 합니다.|
|[연습: 사용자 지정 사이트 워크플로 작업 만들기](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|두 가지 주요 작업을 수행 하는 방법을 보여 줍니다. 사이트 수준 워크플로를 만들고 사용자 지정 워크플로 작업을 만듭니다.|
|[연습: Visual Studio에 SharePoint Designer의 다시 사용 가능한 워크플로 가져오기](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|SharePoint Designer 2010에서 만든 재사용 가능한 선언적 워크플로를 sharepoint 프로젝트로 가져오는 방법을 보여 줍니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|

## <a name="see-also"></a>참고 항목

- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint에 대 한 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)