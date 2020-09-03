---
title: SharePoint 워크플로 솔루션 만들기 & 디버그
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
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
ms.openlocfilehash: 65af3cbfc799a90d640579f8eed0e051fd5888f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014621"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>연습: SharePoint 워크플로 솔루션 만들기 및 디버깅
  이 연습에서는 기본 순차 워크플로 템플릿을 만드는 방법을 보여 줍니다. 워크플로는 공유 문서 라이브러리의 속성을 검사 하 여 문서가 검토 되었는지 여부를 확인 합니다. 문서가 검토 되 면 워크플로가 완료 됩니다.

 이 연습에서는 다음 작업을 수행합니다.

- 에서 SharePoint 목록 정의 순차 워크플로 프로젝트를 만듭니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- 워크플로 활동을 만드는 중입니다.

- 워크플로 작업 이벤트를 처리 합니다.

> [!NOTE]
> 이 연습에서는 순차 워크플로 프로젝트를 사용 하지만 상태 시스템 워크플로 프로젝트에 대 한 프로세스는 동일 합니다.
>
> 또한 다음 지침의 일부 Visual Studio 사용자 인터페이스 요소에 대해 컴퓨터에 다른 이름이 나 위치가 표시 될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint 공유 문서 라이브러리에 속성 추가
 **공유 문서** 라이브러리에서 문서의 검토 상태를 추적 하기 위해 SharePoint 사이트에서 공유 문서에 대 한 세 가지 새 속성인 `Status` , 및를 만듭니다 `Assignee` `Review Comments` . 이러한 속성은 **공유 문서** 라이브러리에서 정의 합니다.

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint 공유 문서 라이브러리에 속성을 추가 하려면

1. 웹 브라우저에서 SharePoint 사이트 (예: http:///SitePages/Home.aspx)를 엽니다 \<system name> .

2. 빠른 실행 모음에서 **Shareddocuments**를 선택 합니다.

3. **라이브러리 도구** 리본에서 **라이브러리** 를 선택한 다음 리본에서 **열 만들기** 단추를 선택 하 여 새 열을 만듭니다.

4. 열 **문서 상태**이름을 지정 하 고, 해당 유형을 **선택 (선택할 메뉴)** 으로 설정 하 고, 다음 세 가지 옵션을 지정한 후 **확인** 단추를 선택 합니다.

    - **검토 필요**

    - **검토 완료**

    - **변경 요청 됨**

5. 열을 두 개 더 만들고 이름을 **담당자** 로, **의견을 검토**합니다. 담당자 열 형식을 텍스트 한 줄로 설정 하 고 검토 설명 열을 여러 줄의 텍스트로 설정 합니다.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>체크 아웃을 요구 하지 않고 문서를 편집할 수 있도록 설정
 체크 아웃 하지 않고도 문서를 편집할 수 있는 경우 워크플로 템플릿을 테스트 하는 것이 더 쉽습니다. 다음 절차에서는이를 사용 하도록 SharePoint 사이트를 구성 합니다.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>문서를 체크 아웃 하지 않고 편집할 수 있도록 하려면

1. 빠른 실행 모음에서 **공유 문서** 링크를 선택 합니다.

2. **라이브러리 도구** 리본에서 **라이브러리** 탭을 선택한 다음 **라이브러리 설정** 단추를 선택 하 여 **문서 라이브러리 설정** 페이지를 표시 합니다.

3. **일반 설정** 섹션 **에서 버전 관리 설정 링크를** 선택 하 여 **버전 관리 설정** 페이지를 표시 합니다.

4. **문서를 편집 하기 전에 체크 아웃 해야 하** 는 설정이 **아니요**인지 확인 합니다. 그렇지 않으면 **아니요** 로 변경한 다음 **확인** 단추를 선택 합니다.

5. 브라우저를 닫습니다.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint 순차 워크플로 프로젝트 만들기
 순차 워크플로는 마지막 작업이 완료 될 때까지 순서 대로 실행 되는 일련의 단계입니다. 이 절차에서는 공유 문서 목록에 적용 되는 순차 워크플로를 만듭니다. 워크플로 마법사를 사용 하면 워크플로를 사이트 정의 또는 목록 정의와 연결 하 여 워크플로가 시작 되는 시기를 결정할 수 있습니다.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint 순차 워크플로 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 여 **새 프로젝트** 대화 상자를 표시 합니다.

3. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

4. **템플릿** 창에서 **SharePoint 2010 프로젝트** 템플릿을 선택 합니다.

5. **이름** 상자에 **MySharePointWorkflow** 를 입력 하 고 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

6. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 **팜 솔루션으로 배포** 옵션 단추를 선택한 다음 **마침** 단추를 선택 하 여 신뢰 수준 및 기본 사이트를 수락 합니다.

     이 단계에서는 솔루션에 대 한 신뢰 수준을 팜 솔루션으로 설정 합니다 .이 옵션은 워크플로 프로젝트에만 사용할 수 있습니다. 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

7. **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

8. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

9. **템플릿** 창에서 **순차 워크플로 (팜 솔루션에만 해당)** 템플릿을 선택한 다음 **추가** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

10. **디버그할 워크플로 이름 지정** 페이지에서 기본 이름 (**MySharePointWorkflow-workflow1.vb**)을 적용 합니다. 기본 워크플로 템플릿 유형 값을 유지 하 고 **워크플로를 나열**한 후 **다음** 단추를 선택 합니다.

11. **Visual Studio에서 디버그 세션에서 워크플로를 자동으로 연결** 하 시겠습니까? 페이지에서 **다음** 단추를 선택 하 여 모든 기본 설정을 적용 합니다.

     이 단계에서는 워크플로를 공유 문서 라이브러리에 자동으로 연결 합니다.

12. **워크플로 시작 방법에 대 한 조건 지정** 페이지에서 기본 옵션을 **워크플로를 시작** 하는 방법 섹션에서 선택 된 상태로 두고 **마침** 단추를 선택 합니다.

     이 페이지에서는 워크플로가 시작 되는 시기를 지정할 수 있습니다. 기본적으로 워크플로는 사용자가 SharePoint에서 수동으로 시작 하거나 워크플로가 연결 된 항목이 생성 될 때 시작 됩니다.

## <a name="create-workflow-activities"></a>워크플로 활동 만들기
 워크플로에는 수행할 작업을 나타내는 하나 이상의 *작업이* 포함 되어 있습니다. 워크플로 디자이너를 사용 하 여 워크플로에 대 한 작업을 정렬할 수 있습니다. 이 절차에서는 워크플로 (HandleExternalEventActivity 및 OnWorkFlowItemChanged)에 두 개의 활동을 추가 합니다. 이러한 활동은 **공유 문서** 목록에서 문서의 검토 상태를 모니터링 합니다.

#### <a name="to-create-workflow-activities"></a>워크플로 활동을 만들려면

1. 워크플로가 workflow designer에 표시 되어야 합니다. 그렇지 않으면 **솔루션 탐색기**에서 **Workflow1.cs** 또는 **workflow1.vb** 를 엽니다.

2. 디자이너에서 **OnWorkflowActivated1** 활동을 선택 합니다.

3. **속성** 창에서 **호출** 된 속성 옆에 **onworkflowactivated** 를 입력 한 다음 enter 키를 선택 합니다.

     코드 편집기가 열리고 onWorkflowActivated 이라는 이벤트 처리기 메서드가 Workflow1.vb 코드 파일에 추가 됩니다.

4. Workflow designer로 다시 전환 하 고 도구 상자를 연 다음 **Windows workflow v 3.0** 노드를 확장 합니다.

5. **도구 상자**의 **Windows Workflow v 3.0** 노드에서 다음 단계 중 하나를 수행 합니다.

    1. **While** 활동에 대 한 바로 가기 메뉴를 열고 **복사**를 선택 합니다. Workflow designer에서 **onWorkflowActivated1** 활동 아래의 줄에 대 한 바로 가기 메뉴를 열고 **붙여넣기**를 선택 합니다.

    2. **While** 활동을 **도구 상자** 에서 워크플로 디자이너로 끌고 활동을 **onWorkflowActivated1** 활동 아래의 줄에 연결 합니다.

6. **WhileActivity1** 활동을 선택 합니다.

7. **속성** 창에서 **조건** 을 코드 조건으로 설정 합니다.

8. **Condition** 속성을 확장 하 고 자식 **Condition** 속성 옆에 **isworkflowpending** 을 입력 한 다음 enter 키를 선택 합니다.

     코드 편집기가 열리고 isWorkflowPending 이라는 메서드가 Workflow1.vb 코드 파일에 추가 됩니다.

9. 워크플로 디자이너로 다시 전환 하 고 도구 상자를 연 다음 **SharePoint 워크플로** 노드를 확장 합니다.

10. **도구 상자**의 **SharePoint 워크플로** 노드에서 다음 단계 중 하나를 수행 합니다.

    - **Onworkflowitemchanged** 활동에 대 한 바로 가기 메뉴를 열고 **복사**를 선택 합니다. Workflow designer에서 **whileActivity1** 활동 내부의 줄에 대 한 바로 가기 메뉴를 열고 **붙여넣기**를 선택 합니다.

    - **도구 상자** 에서 워크플로 디자이너로 **Onworkflowitemchanged** 활동을 끌어 **whileActivity1** 활동 내부의 줄에 활동을 연결 합니다.

11. **OnWorkflowItemChanged1** 활동을 선택 합니다.

12. **속성** 창에서 다음 표와 같이 속성을 설정 합니다.

    |속성|값|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**호출됨**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>작업 이벤트 처리
 마지막으로 각 작업의 문서 상태를 확인 합니다. 문서를 검토 한 후에는 워크플로가 완료 된 것입니다.

#### <a name="to-handle-activity-events"></a>활동 이벤트를 처리 하려면

1. *Workflow1.cs* 또는 *workflow1.vb*에서 다음 필드를 클래스의 맨 위에 추가 합니다. `Workflow1` 이 필드는 워크플로가 완료 되었는지 여부를 확인 하기 위해 작업에 사용 됩니다.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. `Workflow1` 클래스에 다음 메서드를 추가합니다. 이 메서드는 문서 목록의 속성 값을 확인 `Document Status` 하 여 문서를 검토 했는지 여부를 확인 합니다. `Document Status`속성이로 설정 된 경우 `Review Complete` 메서드는 워크플로를 `checkStatus` `workflowPending` 완료할 준비가 되었음을 나타내기 위해 필드를 **false** 로 설정 합니다.

    ```vb
    Private Sub checkStatus()
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then
            workflowPending = False
        End If
    End Sub
    ```

    ```csharp
    private void checkStatus()
    {
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")
        workflowPending = false;
    }
    ```

3. 및 메서드에 다음 코드를 추가 `onWorkflowActivated` `onWorkflowItemChanged` 하 여 메서드를 호출 `checkStatus` 합니다. 워크플로가 시작 되 면 메서드는 `onWorkflowActivated` 메서드를 호출 `checkStatus` 하 여 문서가 이미 검토 되었는지 여부를 확인 합니다. 검토 되지 않은 경우 워크플로는 계속 됩니다. 문서를 저장 하면 `onWorkflowItemChanged` 메서드는 메서드를 다시 호출 `checkStatus` 하 여 문서가 검토 되었는지 여부를 확인 합니다. 필드를 `workflowPending` **true**로 설정 하는 동안 워크플로는 계속 실행 됩니다.

    ```vb
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub

    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub
    ```

    ```csharp
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }

    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }
    ```

4. 메서드에 다음 코드를 추가 `isWorkflowPending` 하 여 속성의 상태를 확인 `workflowPending` 합니다. 문서가 저장 될 때마다 **whileActivity1** 작업은 메서드를 호출 합니다 `isWorkflowPending` . 이 메서드는 <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> 개체의 속성을 검사 <xref:System.Workflow.Activities.ConditionalEventArgs> 하 여 **WhileActivity1** 활동의 지속 여부를 결정 합니다. 속성이 **true**로 설정 된 경우 활동은 계속 됩니다. 그렇지 않으면 작업이 완료 되 고 워크플로가 완료 됩니다.

    ```vb
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)
        e.Result = workflowPending
    End Sub
    ```

    ```csharp
    private void isWorkflowPending(object sender, ConditionalEventArgs e)
    {
        e.Result = workflowPending;
    }
    ```

5. 프로젝트를 저장합니다.

## <a name="test-the-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿 테스트
 디버거를 시작 하면에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로 템플릿을 SharePoint 서버에 배포 하 고 워크플로를 **공유 문서** 목록과 연결 합니다. 워크플로를 테스트 하려면 **공유 문서** 목록의 문서에서 워크플로 인스턴스를 시작 합니다.

#### <a name="to-test-the-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿을 테스트 하려면

1. *Workflow1.cs* 또는 *Workflow1.vb*에서 **onworkflowactivated** 된 메서드 옆에 중단점을 설정 합니다.

2. **F5** 키를 선택 하 여 솔루션을 빌드하고 실행 합니다.

     SharePoint 사이트가 나타납니다.

3. SharePoint의 탐색 창에서 **공유 문서** 링크를 선택 합니다.

4. **공유 문서** 페이지의 **라이브러리 도구** 탭에서 **문서** 링크를 선택한 다음 **문서 업로드** 단추를 선택 합니다.

5. **문서 업로드** 대화 상자에서 **찾아보기** 단추를 선택 하 고 문서 파일을 선택한 다음 **열기** 단추를 선택 하 고 **확인** 단추를 선택 합니다.

     그러면 선택한 문서가 **공유 문서** 목록에 업로드 되 고 워크플로가 시작 됩니다.

6. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버거가 메서드 옆의 중단점에서 중지 되는지 확인 `onWorkflowActivated` 합니다.

7. **F5** 키를 선택 하 여 실행을 계속 합니다.

8. 여기에서 문서에 대 한 설정을 변경할 수 있지만, 지금은 **저장** 단추를 선택 하 여 기본값에 그대로 둡니다.

     그러면 기본 SharePoint 웹 사이트의 **공유 문서** 페이지로 돌아갑니다.

9. **공유 문서** 페이지에서 **MySharePointWorkflow-workflow1.vb** 열 아래의 값이 **진행**중으로 설정 되어 있는지 확인 합니다. 이는 워크플로가 진행 중이 고 문서 검토가 대기 중임을 나타냅니다.

10. **공유 문서** 페이지에서 문서를 선택 하 고 나타나는 화살표를 선택한 다음 **속성 편집** 메뉴 항목을 선택 합니다.

11. **문서 상태** 를 **검토 완료**로 설정 하 고 **저장** 단추를 선택 합니다.

     그러면 기본 SharePoint 웹 사이트의 **공유 문서** 페이지로 돌아갑니다.

12. **공유 문서** 페이지에서 **문서 상태** 열 아래의 값이 **검토 완료**로 설정 되었는지 확인 합니다. **공유 문서** 페이지를 새로 고치고 **MySharePointWorkflow-workflow1.vb** 열 아래의 값이 **Completed**로 설정 되었는지 확인 합니다. 이는 워크플로가 완료 되 고 문서가 검토 되었음을 나타냅니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서 워크플로 템플릿을 만드는 방법에 대해 자세히 알아볼 수 있습니다.

- SharePoint 워크플로 작업에 대 한 자세한 내용은 [Sharepoint Foundation에 대 한 워크플로 작업](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))을 참조 하세요.

- Windows Workflow Foundation 작업에 대 한 자세한 내용은 [system.web. 작업 네임 스페이스](/dotnet/api/system.windows.media.color)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint 워크플로 솔루션 만들기](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
