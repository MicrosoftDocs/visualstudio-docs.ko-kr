---
title: 연결 및 초기화 폼이 있는 워크플로 만들기
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f257dfed2fe439c5ab22ab9951b6258116c6567
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017125"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>연습: 연결 및 초기화 폼이 있는 워크플로 만들기
  이 연습에서는 연결 및 초기화 폼의 사용을 통합 하는 기본적인 순차 워크플로를 만드는 방법을 보여 줍니다. 이러한 매개 변수는 SharePoint 관리자 (연결 양식)에서 처음으로 연결 될 때 및 사용자가 워크플로를 시작할 때 (시작 폼) 매개 변수를 워크플로에 추가할 수 있는 ASPX 폼입니다.

 이 연습에서는 사용자가 다음 요구 사항을 충족 하는 경비 보고서에 대 한 승인 워크플로를 만들려는 시나리오를 간략하게 설명 합니다.

- 워크플로가 목록과 연결 되어 있으면 관리자에 게 경비 보고서에 대 한 달러 제한을 입력 하는 연결 양식을 입력 하 라는 메시지가 표시 됩니다.

- 직원은 경비 보고서를 공유 문서 목록에 업로드 하 고 워크플로를 시작한 다음 워크플로 시작 양식에 비용 합계를 입력 합니다.

- 직원 비용 보고서 합계가 관리자의 미리 정의 된 제한을 초과 하는 경우 직원의 관리자에 게 비용 보고서를 승인 하는 작업이 생성 됩니다. 그러나 직원의 비용 보고서 합계가 비용 제한 보다 작거나 같은 경우 자동 승인 된 메시지가 워크플로의 기록 목록에 기록 됩니다.

  이 연습에서는 다음 작업을 수행합니다.

- 에서 SharePoint 목록 정의 순차 워크플로 프로젝트를 만듭니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- 워크플로 일정 만들기

- 워크플로 작업 이벤트를 처리 합니다.

- 워크플로 연결 및 초기화 폼을 만드는 중입니다.

- 워크플로 연결

- 수동으로 워크플로를 시작 합니다.

> [!NOTE]
> 이 연습에서는 순차 워크플로 프로젝트를 사용 하지만 상태 시스템 워크플로에 대 한 프로세스는 동일 합니다.
>
> 또한 컴퓨터는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음 지침에 따라 일부 사용자 인터페이스 요소에 대해 다른 이름이 나 위치를 표시할 수 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]보유 한 버전과 사용 하는 설정에 따라 이러한 요소가 결정 됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 및 SharePoint의 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint 순차 워크플로 프로젝트 만들기
 먼저에서 순차 워크플로 프로젝트를 만듭니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 순차 워크플로는 마지막 작업이 완료 될 때까지 순서 대로 실행 되는 일련의 단계입니다. 이 절차에서는 SharePoint의 공유 문서 목록에 적용 되는 순차 워크플로를 만듭니다. 워크플로의 마법사를 사용 하면 워크플로를 사이트 또는 목록 정의와 연결 하 여 워크플로가 시작 되는 시기를 결정할 수 있습니다.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint 순차 워크플로 프로젝트를 만들려면

1. 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 여 **새 프로젝트** 대화 상자를 표시 합니다.

2. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. **템플릿** 창에서 **SharePoint 2010 프로젝트** 프로젝트 템플릿을 선택 합니다.

4. **이름** 상자에 **ExpenseReport** 를 입력 하 고 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

5. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 **팜 솔루션으로 배포** 옵션 단추를 선택한 다음 **마침** 단추를 선택 하 여 신뢰 수준 및 기본 사이트를 수락 합니다.

     또한이 단계에서는 솔루션에 대 한 신뢰 수준을 팜 솔루션으로 설정 합니다 .이는 워크플로 프로젝트에 대해 유일 하 게 사용할 수 있는 옵션입니다.

6. **솔루션 탐색기**에서 프로젝트 노드를 선택합니다.

7. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

8. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

9. **템플릿** 창에서 **순차 워크플로 (팜 솔루션에만 해당)** 템플릿을 선택한 다음 **추가** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

10. **디버그할 워크플로 이름 지정** 페이지에서 기본 이름 (**ExpenseReport-workflow1.vb**)을 적용 합니다. 기본 워크플로 템플릿 형식 값 (**워크플로 나열)** 을 유지 합니다. **다음** 단추를 선택합니다.

11. **Visual Studio에서 디버그 세션에서 워크플로를 자동으로 연결** 하 시겠습니까? 페이지에서 워크플로 템플릿이 선택 된 경우 자동으로 연결 하는 확인란의 선택을 취소 합니다.

     이 단계에서는 나중에 연결 양식을 표시 하는 공유 문서 목록과 워크플로를 수동으로 연결할 수 있습니다.

12. **마침** 단추를 선택합니다.

## <a name="add-an-association-form-to-the-workflow"></a>워크플로에 연결 양식 추가
 다음으로를 만듭니다. SharePoint 관리자가 먼저 워크플로를 경비 보고서 문서에 연결할 때 표시 되는 ASPX 연결 폼입니다.

#### <a name="to-add-an-association-form-to-the-workflow"></a>워크플로에 연결 폼을 추가 하려면

1. **솔루션 탐색기**에서 **workflow1.vb** 노드를 선택 합니다.

2. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가** 를 선택 하 여 **새 항목 추가** 대화 상자를 표시 합니다.

3. 대화 상자 트리 보기에서 프로젝트 언어에 따라 **Visual c #** 또는 **Visual Basic** 을 확장 하 고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

4. 템플릿 목록에서 **워크플로 연결 양식** 템플릿을 선택 합니다.

5. **이름** 텍스트 상자에 **ExpenseReportAssocForm**을 입력 합니다.

6. **추가** 단추를 선택 하 여 프로젝트에 폼을 추가 합니다.

## <a name="designing-and-coding-the-association-form"></a>연결 폼 디자인 및 코딩
 이 절차에서는 컨트롤 및 코드를 추가 하 여 연결 폼에 기능을 도입 합니다.

#### <a name="to-design-and-code-the-association-form"></a>연결 폼을 디자인 하 고 코딩 하려면

1. 연결 폼 (ExpenseReportAssocForm .aspx)에서 `asp:Content` 가 있는 요소를 찾습니다 `ID="Main"` .

2. 이 콘텐츠 요소의 첫 번째 줄 바로 뒤에 다음 코드를 추가 하 여 비용 승인 제한 (*Autoapprovelimit*)을 요청 하는 레이블과 텍스트 상자를 만듭니다.

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. **솔루션 탐색기** 의 **ExpenseReportAssocForm** 파일을 확장 하 여 종속 파일을 표시 합니다.

    > [!NOTE]
    > 프로젝트가에 있으면 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] **모든 파일 보기** 단추를 선택 하 여이 단계를 수행 해야 합니다.

4. ExpenseReportAssocForm 파일에 대 한 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다.

5. 메서드를 `GetAssociationData` 다음으로 바꿉니다.

    ```vb
    Private Function GetAssociationData() As String
        ' TODO: Return a string that contains the association data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return Me.AutoApproveLimit.Text
    End Function
    ```

    ```csharp
    private string GetAssociationData()
    {
        // TODO: Return a string that contains the association data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.AutoApproveLimit.Text;
    }
    ```

## <a name="add-an-initiation-form-to-the-workflow"></a>워크플로에 시작 양식 추가
 그런 다음 사용자가 비용 보고서에 대해 워크플로를 실행할 때 표시 되는 시작 양식을 만듭니다.

#### <a name="to-create-an-initiation-form"></a>시작 폼을 만들려면

1. **솔루션 탐색기**에서 **workflow1.vb** 노드를 선택 합니다.

2. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가** 를 선택 하 여 **새 항목 추가** 대화 상자를 표시 합니다.

3. 대화 상자 트리 보기에서 프로젝트 언어에 따라 **Visual c #** 또는 **Visual Basic** 을 확장 하 고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

4. 템플릿 목록에서 **워크플로 시작 양식** 템플릿을 선택 합니다.

5. **이름** 텍스트 상자에 **ExpenseReportInitForm**을 입력 합니다.

6. **추가** 단추를 선택 하 여 프로젝트에 폼을 추가 합니다.

## <a name="designing-and-coding-the-initiation-form"></a>시작 양식 디자인 및 코딩
 그런 다음 컨트롤 및 코드를 추가 하 여 시작 폼에 기능을 도입 합니다.

#### <a name="to-code-the-initiation-form"></a>시작 폼을 코딩 하려면

1. 시작 양식 (ExpenseReportInitForm)에서를 `asp:Content` 포함 하는 요소를 찾습니다 `ID="Main"` .

2. 이 콘텐츠 요소의 첫 번째 줄 바로 뒤에 다음 코드를 추가 하 여 연결 폼에 입력 된 비용 승인 한도 (*Autoapprovelimit*)와 총 비용 (*ExpenseTotal*)을 묻는 다른 레이블 및 텍스트 상자를 표시 하는 레이블 및 텍스트 상자를 만듭니다.

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. **솔루션 탐색기** 의 **ExpenseReportInitForm** 파일을 확장 하 여 종속 파일을 표시 합니다.

4. ExpenseReportInitForm 파일에 대 한 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다.

5. 메서드를 `Page_Load` 다음 예제로 바꿉니다.

    ```vb
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As
      EventArgs) Handles Me.Load
        InitializeParams()
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New
          Guid(associationGuid)).AssociationData
        ' Optionally, add code here to pre-populate your form fields.
    End Sub
    ```

    ```csharp
    protected void Page_Load(object sender, EventArgs e)
    {
        InitializeParams();
        this.AutoApproveLimit.Text =
          workflowList.WorkflowAssociations[new
          Guid(associationGuid)].AssociationData;
    }
    ```

6. 메서드를 `GetInitiationData` 다음 예제로 바꿉니다.

    ```vb
    ' This method is called when the user clicks the button to start the workflow.
    Private Function GetInitiationData() As String
        Return Me.ExpenseTotal.Text
        ' TODO: Return a string that contains the initiation data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return String.Empty
    End Function
    ```

    ```csharp
    // This method is called when the user clicks the button to start the workflow.
    private string GetInitiationData()
    {
        // TODO: Return a string that contains the initiation data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.ExpenseTotal.Text;
    }
    ```

## <a name="cutomize-the-workflow"></a>워크플로 Cutomize
 그런 다음 워크플로를 사용자 지정 합니다. 나중에 두 개의 폼을 워크플로에 연결 합니다.

#### <a name="to-customize-the-workflow"></a>워크플로를 사용자 지정 하려면

1. 프로젝트에서 Workflow1.vb를 열어 workflow designer에 워크플로를 표시 합니다.

2. **도구 상자**에서 **Windows Workflow v 3.0** 노드를 확장 하 고 **IfElse** 작업을 찾습니다.

3. 다음 단계 중 하나를 수행 하 여이 활동을 워크플로에 추가 합니다.

    - **IfElse** 활동에 대 한 바로 가기 메뉴를 열고 **복사**를 선택 하 고 workflow designer의 **onWorkflowActivated1** 활동 아래에 있는 줄의 바로 가기 메뉴를 연 다음 **붙여넣기**를 선택 합니다.

    - **도구 상자**에서 **IfElse** 활동을 끌어 workflow designer의 **onWorkflowActiviated1** 활동 아래 줄에 연결 합니다.

4. 도구 상자에서 **SharePoint 워크플로** 노드를 확장 하 고 **createtask** 작업을 찾습니다.

5. 다음 단계 중 하나를 수행 하 여이 활동을 워크플로에 추가 합니다.

    - **Createtask** 작업에 대 한 바로 가기 메뉴를 열고 **복사**를 선택 하 고 workflow designer의 **IfElseActivity1** 내에서 두 개의 **작업 삭제** 영역 중 하나에 대 한 바로 가기 메뉴를 연 다음 **붙여넣기**를 선택 합니다.

    - **도구 상자** 의 **createtask** 활동을 두 개의 **Drop 활동에서 다음** 영역으로 끌어 옵니다. **IfElseActivity1**

6. **속성** 창에서 **CorrelationToken** 속성에 대 한 *tasktoken* 속성 값을 입력 합니다.

7. 옆에 있는 더하기 기호 (![TreeView plus](../sharepoint/media/plus.gif "TreeView 더하기 기호"))를 선택 하 여 **CorrelationToken** 속성을 확장 합니다.

8. **OwnerActivityName** sub 속성의 드롭다운 화살표를 선택 하 고 *workflow1.vb* 값을 설정 합니다.

9. **TaskId** 속성을 선택 하 고 줄임표 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 선택 하 여 **바인딩 속성** 대화 상자를 표시 합니다.

10. **새 멤버에 바인딩** 탭을 선택 하 고 **필드 만들기** 옵션 단추를 선택한 다음 **확인** 단추를 선택 합니다.

11. **TaskProperties** 속성을 선택한 다음 줄임표 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 선택 하 여 **바인딩 속성** 대화 상자를 표시 합니다.

12. **새 멤버에 바인딩** 탭을 선택 하 고 **필드 만들기** 옵션 단추를 선택한 다음 **확인** 단추를 선택 합니다.

13. **도구 상자**에서 **SharePoint 워크플로** 노드를 확장 하 고 **LogToHistoryListActivity** 활동을 찾습니다.

14. 다음 단계 중 하나를 수행 하 여이 활동을 워크플로에 추가 합니다.

    - **LogToHistoryListActivity** 활동에 대 한 바로 가기 메뉴를 열고 **복사**를 선택 하 고, workflow designer의 **IfElseActivity1** 내에서 기타 **작업 삭제** 영역에 대 한 바로 가기 메뉴를 연 다음 **붙여넣기**를 선택 합니다.

    - **도구 상자**에서 **LogToHistoryListActivity** 활동을 끌어 **IfElseActivity1**내의 다른 **drop 활동** 영역에 놓습니다.

## <a name="add-code-to-the-workflow"></a>워크플로에 코드 추가
 그런 다음 워크플로에 코드를 추가 하 여 기능을 제공 합니다.

#### <a name="to-add-code-to-the-workflow"></a>워크플로에 코드를 추가 하려면

1. Workflow designer에서 **createTask1** 작업에 대 한 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다.

2. 다음 메서드를 추가합니다.

    ```vb
    Private Sub createTask1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        createTask1_TaskId1 = Guid.NewGuid
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"
        createTask1_TaskProperties1.Description = "Please approve the
          expense report"
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed"
    End Sub
    ```

    ```csharp
    private void createTask1_MethodInvoking(object sender, EventArgs e)
    {
        createTask1_TaskId1 = Guid.NewGuid();
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";
        createTask1_TaskProperties1.Description = "Please approve the
          expense report";
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed";
    }
    ```

    > [!NOTE]
    > 코드에서를 `somedomain\\someuser` ""와 같이 작업이 생성 될 도메인 및 사용자 이름으로 바꿉니다 `Office\\JoeSch` . 테스트를 위해를 사용 하 여 개발 중인 계정을 사용 하는 것이 가장 쉽습니다.

3. 메서드 아래에 `MethodInvoking` 다음 예제를 추가 합니다.

    ```vb
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As
      ConditionalEventArgs)
        Dim approval As Boolean = False
        If (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData)) Then
            approval = True
        End If
        e.Result = approval
    End Sub
    ```

    ```csharp
    private void checkApprovalNeeded(object sender, ConditionalEventArgs
      e)
    {
        bool approval = false;
        if (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData))
        {
            approval = true;
        }
        e.Result = approval;
    }
    ```

4. Workflow designer에서 **ifElseBranchActivity1** 활동을 선택 합니다.

5. **속성** 창에서 **Condition** 속성의 드롭다운 화살표를 선택한 다음 *코드 조건* 값을 설정 합니다.

6. 그 옆에 있는 더하기 기호 (![TreeView plus](../sharepoint/media/plus.gif "TreeView 더하기 기호"))를 선택 하 여 **Condition** 속성을 확장 한 다음 해당 값을 *checkapprovalneeded*로 설정 합니다.

7. Workflow designer에서 **logToHistoryListActivity1** 작업에 대 한 바로 가기 메뉴를 열고 **처리기 생성** 을 선택 하 여 이벤트에 대 한 빈 메서드를 생성 `MethodInvoking` 합니다.

8. 코드를 `MethodInvoking` 다음 코드로 바꿉니다.

    ```vb
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto
          approved for " + workflowProperties.InitiationData)
    End Sub
    ```

    ```csharp
    private void logToHistoryListActivity1_MethodInvoking(object sender,
      EventArgs e)
    {
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was
          auto approved for " + workflowProperties.InitiationData;
    }
    ```

9. **F5** 키를 선택 하 여 프로그램을 디버깅 합니다.

     그러면 응용 프로그램을 컴파일하고 패키지 하 여 배포 하 고 해당 기능을 활성화 하 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 고 응용 프로그램 풀을 재활용 하 고 **사이트 Url** 속성에 지정 된 위치에서 브라우저를 시작 합니다.

## <a name="associating-the-workflow-to-the-documents-list"></a>문서 목록에 워크플로 연결
 그런 다음 워크플로를 SharePoint 사이트의 **Shareddocuments** 목록과 연결 하 여 워크플로 연결 양식을 표시 합니다.

#### <a name="to-associate-the-workflow"></a>워크플로를 연결 하려면

1. 빠른 실행 표시줄에서 **공유 문서** 링크를 선택 합니다.

2. 라이브러리 **도구** 탭에서 **라이브러리** 링크를 선택 하 고 **라이브러리 설정** 리본 단추를 선택 합니다.

3. **사용 권한 및 관리** 섹션에서 **워크플로 설정** 링크를 선택한 다음 **워크플로 페이지에서** **워크플로 추가** 링크를 선택 합니다.

4. 워크플로 설정 페이지의 위쪽 목록에서 **ExpenseReport-workflow1.vb** 템플릿을 선택 합니다.

5. 다음 필드에 **ExpenseReportWorkflow** 를 입력 하 고 **다음** 단추를 선택 합니다.

     이렇게 하면 워크플로가 **공유 문서** 목록에 연결 되 고 워크플로 연결 양식이 표시 됩니다.

6. **자동 승인 제한** 텍스트 상자에 **1200** 를 입력 한 다음 **워크플로 연결** 단추를 선택 합니다.

## <a name="start-the-workflow"></a>워크플로 시작
 그런 다음 워크플로를 **공유 문서** 목록의 문서 중 하나에 연결 하 여 워크플로 시작 양식을 표시 합니다.

#### <a name="to-start-the-workflow"></a>워크플로를 시작 하려면

1. SharePoint 페이지에서 **홈** 단추를 선택 합니다.

2. 빠른 실행 모음에서 **공유 문서** 링크를 선택 하 여 **공유 문서** 목록을 표시 합니다.

3. 페이지 위쪽의 **라이브러리 도구** 탭에서 **문서** 링크를 선택한 다음 리본 메뉴에서 **문서 업로드** 단추를 선택 하 여 **공유 문서** 목록에 새 문서를 업로드 합니다.

4. **문서 업로드** 대화 상자에서 **찾아보기** 단추를 선택 하 고 문서 파일을 선택한 다음 **열기** 단추를 선택 하 고 **확인** 단추를 선택 합니다.

     이 대화 상자에서 문서에 대 한 설정을 변경할 수 있지만 **저장** 단추를 선택 하 여 기본값에 그대로 둡니다.

5. 업로드 된 문서를 선택 하 고 표시 되는 드롭다운 화살표를 선택한 다음 **워크플로** 항목을 선택 합니다.

6. ExpenseReportWorkflow 옆의 이미지를 선택 합니다.

     이렇게 하면 워크플로 시작 양식이 표시 됩니다. **자동 승인 제한** 상자에 표시 되는 값은 연결 폼에 입력 되었기 때문에 읽기 전용입니다.

7. **비용 합계** 텍스트 상자에 **1600**를 입력 한 다음 **워크플로 시작** 단추를 선택 합니다.

     그러면 **공유 문서** 목록이 다시 표시 됩니다. **완료** 된 값이 포함 된 **ExpenseReportWorkflow** 라는 새 열이 워크플로가 시작 된 항목에 추가 됩니다.

8. 업로드 된 문서 옆의 드롭다운 화살표를 선택한 다음 **워크플로 항목을 선택 하 여 워크플로** 상태 페이지를 표시 합니다. **완료 된 워크플로**아래에서 **완료** 된 값을 선택 합니다. **작업은 작업 섹션에** 나열 됩니다.

9. 작업의 제목을 선택 하 여 작업 세부 정보를 표시 합니다.

10. **Shareddocuments** 목록으로 돌아가서 동일한 문서나 다른 문서를 사용 하 여 워크플로를 다시 시작 합니다.

11. 시작 페이지에서 연결 페이지에 입력 한 금액 보다 작거나 같은 금액을 입력 합니다 (**1200**).

     이 문제가 발생 하면 작업 대신 기록 목록의 항목이 생성 됩니다. 항목이 워크플로 상태 페이지의 **워크플로 기록** 섹션에 표시 됩니다. 기록 이벤트의 **결과** 열에 있는 메시지를 확인 합니다. `logToHistoryListActivity1.MethodInvoking`자동 승인 된 금액을 포함 하는 이벤트에 입력 된 텍스트를 포함 합니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서 워크플로 템플릿을 만드는 방법에 대해 자세히 알아볼 수 있습니다.

- SharePoint 워크플로에 대 한 자세한 내용은 [Windows Sharepoint Services의 워크플로](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14))를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [SharePoint 워크플로 솔루션 만들기](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [연습: 워크플로에 응용 프로그램 페이지 추가](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
