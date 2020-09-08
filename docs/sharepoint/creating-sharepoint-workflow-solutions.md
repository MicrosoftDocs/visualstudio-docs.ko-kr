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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015286"
---
# <a name="create-sharepoint-workflow-solutions"></a>SharePoint 워크플로 솔루션 만들기

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서는 SharePoint 웹 사이트에 있는 문서 및 목록 항목의 수명 주기를 관리하는 사용자 지정 워크플로를 만드는 데 도움이 되는 도구를 제공합니다. 제공되는 항목에는 디자이너, 작업 컨트롤 집합 및 필수 어셈블리 참조가 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에는 워크플로를 만들고 구성하는 데 도움이 되는 **SharePoint 사용자 지정 마법사**도 포함되어 있습니다.

SharePoint에 대한 자세한 내용은 [Microsoft SharePoint 제품 및 기술](/sharepoint/dev/)을 참조하세요.

## <a name="workflows-in-sharepoint"></a>SharePoint의 워크플로
 SharePoint 라이브러리 또는 목록에 워크플로를 추가하면 라이브러리 또는 목록의 모든 항목에 비즈니스 프로세스가 적용됩니다. 워크플로는 시스템 또는 사용자가 각 항목에 대해 수행해야 하는 작업(예: 편집 후 검토할 항목 보내기)을 설명합니다. 해당 작업을 ‘활동’이라고 하며 워크플로의 구성 요소입니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 SharePoint 워크플로를 만들어 SharePoint 웹 사이트에 배포할 수 있습니다. SharePoint에 워크플로를 배포한 후 라이브러리 또는 목록과 연결합니다. 그러면 프로세스를 통해 자동으로 또는 사용자가 수동으로 워크플로를 시작할 수 있습니다. 워크플로 작업에 대한 자세한 내용은 [Visual Studio를 사용하여 SharePoint 워크플로 개발](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio)을 참조하세요.

## <a name="create-custom-sharepoint-workflows"></a>사용자 지정 SharePoint 워크플로 만들기
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서는 두 가지 SharePoint 워크플로 프로젝트(**순차적 워크플로** 및 **상태 시스템 워크플로**)를 사용할 수 있습니다.

 ‘순차적 워크플로’는 일련의 단계를 나타냅니다. 마지막 활동이 완료될 때까지 단계를 차례로 수행합니다. 순차적 워크플로는 항상 엄격하게 순차적으로 실행됩니다. 외부 이벤트를 받을 수 있고 병렬 논리 흐름을 포함할 수 있기 때문에 정확한 실행 순서는 달라질 수 있습니다. 다음 그림은 순차적 워크플로의 예를 보여 줍니다.

 ![순차적 워크플로](../sharepoint/media/sp-sequential.png "순차적 워크플로")

 ‘상태 시스템 워크플로’는 상태, 전환, 작업 세트를 나타냅니다. 상태 시스템 워크플로의 단계는 비동기적으로 실행됩니다. 즉, 단계를 차례로 수행하지 않아도 되며 작업 및 상태를 통해 단계가 트리거됩니다. 한 상태가 시작 상태로 할당되고, 이벤트에 따라 다른 상태로 전환됩니다. 상태 시스템에 워크플로의 끝을 결정하는 최종 상태를 설정할 수 있습니다. 다음 다이어그램은 상태 시스템 워크플로의 예를 나타냅니다.

 ![정적 컴퓨터 워크플로](../sharepoint/media/sp-state.png "정적 컴퓨터 워크플로")

 워크플로 유형에 대한 자세한 내용은 [워크플로 유형](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14))을 참조하세요.

### <a name="use-the-wizard"></a>마법사 사용
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 SharePoint 워크플로 프로젝트를 만드는 경우, 먼저 **SharePoint 사용자 지정 마법사**에서 해당 설정을 지정합니다. 마법사는 이 설정을 사용하여 **솔루션 탐색기**에 프로젝트를 만듭니다. 이 프로젝트에는 코드 파일, 워크플로를 배포하는 데 사용되는 여러 파일, 사용자 지정 SharePoint 워크플로를 만드는 데 필요한 어셈블리에 대한 참조가 포함됩니다.

 워크플로를 만든 후 속성 창에서 해당 속성을 수정할 수 있습니다. 대부분의 워크플로 속성은 속성 창에서 직접 변경할 수 있지만, 값을 변경하기 위해 줄임표 단추(![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))를 클릭해야 하는 경우도 있습니다. 이 단추를 클릭하면 **SharePoint 사용자 지정 마법사**가 다시 시작됩니다. 속성 값을 변경한 후 **마침** 단추를 선택하여 종료합니다.

> [!NOTE]
> **워크플로 유형** 속성은 읽기 전용이며 변경할 수 없습니다. 워크플로 유형을 변경하려면 다른 워크플로를 만들어야 합니다.

## <a name="design-a-sharepoint-workflow"></a>SharePoint 워크플로 디자인
 비즈니스 프로세스의 모든 단계를 정의한 후 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로 디자이너를 사용하여 SharePoint 워크플로를 디자인합니다. 디자이너를 열려면 **솔루션 탐색기**에서 Workflow1.cs 또는 Workflow1.vb를 두 번 클릭하거나 이 파일의 바로 가기 메뉴를 열고 **열기**를 선택합니다.

### <a name="activities"></a>활동
 워크플로를 디자인하려면 **도구 상자**의 활동을 디자이너의 ‘워크플로 일정’에 추가합니다. 워크플로 일정에는 활동 시퀀스가 수행해야 하는 순서대로 포함됩니다.

 활동에는 다음 두 가지 유형이 있습니다.

- ‘단순 활동’은 “1일간 지연” 또는 “웹 서비스 시작”과 같은 한 단위 작업을 수행합니다.

- ‘복합 활동’은 다른 활동을 포함합니다. 예를 들어 조건부 활동에는 두 개의 분기가 포함될 수 있습니다.

  **도구 상자**에서 두 가지 유형의 활동을 모두 사용할 수 있습니다.

  활동에 속성, 메서드, 이벤트를 설정할 수 있습니다. **속성** 창을 사용하여 활동의 속성을 설정합니다.

  사용자 지정 활동을 만들 수도 있습니다. 자세한 내용은 [연습: 사용자 지정 사이트 워크플로 활동 만들기](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)를 참조하세요.

  활동은 **도구 상자**의 다음 탭에 구성되어 있습니다.

- **SharePoint 워크플로**

- **Windows Workflow v3.0**

- **Windows Workflow v3.5**

  SharePoint에서 핵심 워크플로 활동을 모두 지원하는 것은 아닙니다. 자세한 내용은 [Windows SharePoint Services에 대한 워크플로 활동 개요](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))를 참조하세요.

#### <a name="sharepoint-workflow-activities"></a>SharePoint 워크플로 활동
 **SharePoint 워크플로** 탭에는 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]에서 사용하기 위한 특수화된 활동이 포함되어 있습니다. 해당 활동은 문서 수명 주기 워크플로 개발을 간소화합니다. **SharePoint 워크플로** 탭에 표시되는 활동에 대한 자세한 내용은 [Windows SharePoint Services에 대한 워크플로 활동 개요](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))를 참조하세요.

#### <a name="windows-workflow-activities"></a>Windows Workflow 활동
 **Windows Workflow** 탭에는 [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]에서 제공하는 활동이 포함되어 있습니다. 해당 활동을 사용하여 모든 종류의 Windows Workflow 애플리케이션에 대한 워크플로 일정을 만들 수 있습니다.

 **Windows Workflow** 탭에 표시되는 활동에 대한 자세한 내용은 [Windows Workflow Foundation 활동](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90))을 참조하세요. Windows Workflow Foundation에 대한 자세한 내용은 [Windows Workflow Foundation 개요](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90))를 참조하세요.

### <a name="work-with-activities-in-the-designer"></a>디자이너에서 활동 작업
 워크플로 일정은 Windows Workflow 활동과 SharePoint 워크플로 활동의 조합을 포함할 수 있습니다.

 디자이너는 활동을 올바르게 배치하고 구성하는 데 도움이 되는 시각 신호를 표시합니다. 작업을 워크플로 일정으로 끌거나 복사하면 워크플로에서 해당 작업의 올바른 위치를 보여 주는 녹색 더하기 기호(+) 아이콘이 디자이너에 표시됩니다. 활동을 유효하지 않은 위치에 배치할 수는 없습니다. 예를 들어 Send 활동을 Listen 활동 분기의 첫 번째 활동으로 배치할 수 없습니다. 자세한 내용은 [SharePoint Designer 개발자 센터](https://developer.microsoft.com/office/docs)를 참조하세요.

## <a name="collect-information-during-the-workflow"></a>워크플로 중에 정보 수집
 워크플로에서 미리 정의된 시간에 사용자로부터 정보를 수집하는 것이 좋습니다. 양식 또는 항목 속성을 사용하여 정보를 수집할 수 있습니다.

### <a name="forms"></a>양식
 양식은 질문을 포함하고 사용자가 답변을 제공할 수 있는 대화 상자와 같습니다.

 워크플로에서 사용할 수 있는 네 가지 유형의 양식이 있습니다.

- 연결

- 시작

- 수정

- Task

  이 중에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에는 연결 및 시작 양식의 항목 템플릿이 포함되어 있습니다. ‘연결 양식’의 예로는 워크플로를 설치하는 관리자가 비용 워크플로의 지출 한도와 같이 워크플로와 관련된 매개 변수를 입력할 수 있는 양식이 있습니다. ‘시작 양식’의 예로는 비용 워크플로의 사용자가 워크플로에 지출 금액을 입력할 수 있는 양식이 있습니다. 이러한 유형의 양식에 대한 자세한 내용은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)을 참조하세요.

### <a name="item-properties"></a>항목 속성
 SharePoint 라이브러리 또는 목록의 항목 속성을 사용하여 사용자로부터 정보를 수집할 수도 있습니다. 주 코드 파일(Workflow1.cs 또는 Workflow1.vb)에서는 `workflowProperties`라는 Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties 클래스의 인스턴스를 선언합니다. `workflowProperties` 개체를 사용하여 코드에서 라이브러리 또는 목록의 속성에 액세스합니다. 예제를 보려면 [연습: SharePoint 워크플로 솔루션 만들기 및 디버그](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)를 참조하세요.

## <a name="debug-a-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿 디버그
 다른 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 웹 기반 프로젝트를 디버그할 때와 동일한 방법으로 SharePoint 워크플로 프로젝트를 디버그할 수 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버거를 시작하면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서 **SharePoint 사용자 지정 마법사**에 지정된 설정을 사용하여 적절한 SharePoint 웹 사이트를 열고 워크플로 템플릿을 적절한 라이브러리 또는 목록과 자동으로 연결합니다. 또한 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 *w3wp.exe*라는 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 프로세스에 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버거를 연결합니다.

 워크플로를 테스트하려면 워크플로를 수동으로 시작해야 합니다. 자세한 내용은 [SharePoint 솔루션 디버그](../sharepoint/debugging-sharepoint-solutions.md)에서 “워크플로 디버그” 섹션을 참조하세요. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 웹 애플리케이션 디버깅에 대한 자세한 내용은 [웹 애플리케이션 및 스크립트 디버그](../debugger/how-to-enable-debugging-for-aspnet-applications.md)를 참조하세요.

## <a name="deploy-a-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿 배포
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 워크플로 프로젝트는 다른 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트와 마찬가지로 배포됩니다. 자세한 내용은 [SharePoint 솔루션 패키지 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)를 참조하세요.

## <a name="import-globally-reusable-workflows"></a>전역적으로 재사용 가능한 워크플로 가져오기
 SharePoint Designer를 사용하면 사이트별로 재사용 가능한 워크플로뿐 아니라 ‘전역적으로 재사용 가능한 워크플로’(모든 SharePoint 사이트에서 사용할 수 있는 워크플로)도 만들 수 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]의 재사용 가능한 워크플로 가져오기 프로젝트는 현재 전역적으로 재사용 가능한 워크플로를 가져오지 않습니다. 그러나 SharePoint Designer를 사용하여 전역적으로 재사용 가능한 워크플로를 재사용 가능한 워크플로로 변환하거나 워크플로를 변환되지 않은 선언적 워크플로로 가져올 수 있습니다. 자세한 내용은 [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)를 참조하세요.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[연습: SharePoint 워크플로 솔루션 만들기 및 디버그](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|간단한 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로를 만들고 디버그하는 과정을 단계별로 안내합니다.|
|[연습: 연결 및 시작 양식을 사용하여 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|연결 및 시작 양식을 사용하여 더 완전한 기능을 갖춘 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로를 만드는 과정을 단계별로 안내합니다.|
|[연습: 워크플로에 애플리케이션 페이지 추가](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|[연습: 연결 및 시작 양식을 사용하여 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) 항목을 기반으로 하며, 워크플로에 입력된 데이터를 보고하는 *.aspx* 애플리케이션 페이지를 추가합니다.|
|[연습: 사용자 지정 사이트 워크플로 활동 만들기](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|두 가지 주요 작업(사이트 수준 워크플로 만들기 및 사용자 지정 워크플로 활동 만들기)을 수행하는 방법을 보여 줍니다.|
|[연습: SharePoint Designer의 재사용 가능 워크플로를 Visual Studio로 가져오기](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|SharePoint Designer 2010에서 만든 재사용 가능한 선언적 워크플로를 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트로 가져오는 방법을 보여 줍니다.|

## <a name="see-also"></a>참조

- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint용 애플리케이션 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)