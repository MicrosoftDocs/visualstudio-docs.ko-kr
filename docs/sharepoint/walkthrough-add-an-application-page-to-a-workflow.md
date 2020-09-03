---
title: '연습: 워크플로에 응용 프로그램 페이지 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f54914e6676e0cc2400fa04ebb089fac08f58c3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015493"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>연습: 워크플로에 응용 프로그램 페이지 추가
  이 연습에서는 워크플로에서 파생 된 데이터를 표시 하는 응용 프로그램 페이지를 워크플로 프로젝트에 추가 하는 방법을 보여 줍니다. [연습: 연결 및 초기화 양식으로 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)항목에 설명 된 프로젝트를 기반으로 합니다.

 이 연습에서는 다음 작업을 수행합니다.

- SharePoint 워크플로 프로젝트에 ASPX 응용 프로그램 페이지 추가

- 워크플로 프로젝트에서 데이터 가져오기 및 조작

- 응용 프로그램 페이지의 테이블에 데이터를 표시 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 및 SharePoint의 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]

- Visual Studio.

- 또한 [연습: 연결 및 초기화 폼이 있는 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)항목에서 프로젝트를 완료 해야 합니다.

## <a name="ammend-the-workflow-code"></a>워크플로 코드 Ammend
 먼저 워크플로에 코드 줄을 추가 하 여 결과 열의 값을 경비 보고서의 양으로 설정 합니다. 이 값은 나중에 경비 보고서 요약 계산에 사용 됩니다.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>워크플로의 결과 열 값을 설정 하려면

1. [연습: 연결 및 초기화 폼을 사용 하 여 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) 항목에서 완료 된 프로젝트를 로드 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다.

2. *Workflow1.cs* 또는 *workflow1.vb* 에 대 한 코드 (프로그래밍 언어에 따라)를 엽니다.

3. 메서드의 맨 아래에 `createTask1_MethodInvoking` 다음 코드를 추가 합니다.

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>응용 프로그램 페이지 만들기
 다음으로 프로젝트에 ASPX 폼을 추가 합니다. 이 양식은 경비 보고서 워크플로 프로젝트에서 얻은 데이터를 표시 합니다. 이렇게 하려면 응용 프로그램 페이지를 추가 합니다. 응용 프로그램 페이지는 다른 SharePoint 페이지와 동일한 마스터 페이지를 사용 합니다. 즉, SharePoint 사이트의 다른 페이지와 유사 합니다.

#### <a name="to-add-an-application-page-to-the-project"></a>프로젝트에 응용 프로그램 페이지를 추가 하려면

1. ExpenseReport 프로젝트를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

2. **템플릿** 창에서 **응용 프로그램 페이지** 템플릿을 선택 하 고, 프로젝트 항목의 기본 이름 (**ApplicationPage1**)을 사용 하 고, **추가** 단추를 선택 합니다.

3. [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]ApplicationPage1의에서 `PlaceHolderMain` 섹션을 다음으로 바꿉니다.

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     이 코드는 제목과 함께 페이지에 테이블을 추가 합니다.

4. 섹션을 다음으로 바꿔 응용 프로그램 페이지에 제목을 추가 합니다 `PlaceHolderPageTitleInTitleArea` .

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>응용 프로그램 페이지 코딩
 그런 다음 경비 보고서 요약 응용 프로그램 페이지에 코드를 추가 합니다. 페이지를 열면 코드에서 SharePoint의 작업 목록에서 할당 된 지출 한도를 초과한 비용을 검색 합니다. 보고서는 각 항목을 비용의 합계와 함께 나열 합니다.

#### <a name="to-code-the-application-page"></a>응용 프로그램 페이지를 코딩 하려면

1. **ApplicationPage1** 노드를 선택 하 고 메뉴 모음에서 코드 **보기**를 선택  >  **Code** 하 여 응용 프로그램 페이지 뒤에 코드를 표시 합니다.

2. 클래스의 맨 위에 있는 **using** 또는 **Import** 문 (프로그래밍 언어에 따라 다름)을 다음과 같이 바꿉니다.

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3. `Page_Load` 메서드에 다음 코드를 추가합니다.

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    > 코드의 "TestServer"를 SharePoint를 실행 하는 유효한 서버의 이름으로 바꾸어야 합니다.

## <a name="test-the-application-page"></a>응용 프로그램 페이지 테스트
 그런 다음 응용 프로그램 페이지에서 비용 데이터를 올바르게 표시 하는지 확인 합니다.

#### <a name="to-test-the-application-page"></a>응용 프로그램 페이지를 테스트 하려면

1. **F5** 키를 선택 하 여 프로젝트를 실행 하 고 SharePoint에 배포 합니다.

2. **홈** 단추를 선택한 다음 빠른 실행 모음에서 **공유 문서** 링크를 선택 하 여 SharePoint 사이트의 공유 문서 목록을 표시 합니다.

3. 이 예제에 대 한 경비 보고서를 나타내려면 페이지 맨 위에 있는 **LibraryTools** 탭에서 **문서** 링크를 선택한 다음 도구 리본에서 **문서 업로드** 단추를 선택 하 여 문서 목록에 일부 새 문서를 업로드 합니다.

4. 일부 문서를 업로드 한 후에는 페이지 상단의 **LibraryTools** 탭에서 **라이브러리** 링크를 선택 하 고 도구 리본에서 **라이브러리 설정** 단추를 선택 하 여 워크플로를 인스턴스화합니다.

5. **문서 라이브러리 설정** 페이지의 **사용 권한 및 관리** 섹션에서 **워크플로 설정** 링크를 선택 합니다.

6. **워크플로 설정** 페이지에서 **워크플로 추가** 링크를 선택 합니다.

7. **워크플로 추가** 페이지에서 **ExpenseReport-workflow1.vb** 워크플로를 선택 하 고 워크플로의 이름 (예: **ExpenseTest**)을 입력 한 후 **다음** 단추를 선택 합니다.

    워크플로 연결 양식이 표시 됩니다. 이를 사용 하 여 비용 제한 금액을 보고 합니다.

8. 연결 양식에서 **자동 승인 제한** 상자에 **1000** 을 입력 한 다음 **워크플로 연결** 단추를 선택 합니다.

9. **홈** 단추를 선택 하 여 SharePoint 홈 페이지로 돌아갑니다.

10. 빠른 실행 표시줄에서 **공유 문서** 링크를 선택 합니다.

11. 업로드 된 문서 중 하나를 선택 하 여 드롭다운 화살표를 표시 하 고 선택한 다음 **워크플로** 항목을 선택 합니다.

12. ExpenseTest 옆의 이미지를 선택 하 여 워크플로 시작 양식을 표시 합니다.

13. **비용 합계** 텍스트 상자에 1000 보다 큰 값을 입력 한 다음 **워크플로 시작** 단추를 선택 합니다.

     보고 된 비용이 할당 된 비용을 초과 하면 작업이 작업 목록에 추가 됩니다. **완료** 된 값이 있는 **ExpenseTest** 이라는 열이 공유 문서 목록의 경비 보고서 항목에도 추가 됩니다.

14. 공유 문서 목록에서 다른 문서와 함께 11-13 단계를 반복 합니다. 정확한 문서 수는 중요 하지 않습니다.

15. 웹 브라우저에서 다음 URL을 열어 경비 보고서 요약 응용 프로그램 페이지를 표시 합니다. **Http://**<em>SystemName</em>**/_layouts/expensereport/applicationpage1.aspx**.

     비용 보고서 요약 페이지에는 할당 된 금액을 초과한 모든 비용 보고서, 초과한 크기 및 모든 보고서의 총 금액이 나열 됩니다.

## <a name="next-steps"></a>다음 단계
 SharePoint 응용 프로그램 페이지에 대 한 자세한 내용은 [sharepoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)를 참조 하세요.

 다음 항목에서 Visual Studio의 Visual Web Designer를 사용 하 여 SharePoint 페이지 콘텐츠를 디자인 하는 방법에 대해 자세히 알아볼 수 있습니다.

- [SharePoint 용 웹 파트를 만듭니다](../sharepoint/creating-web-parts-for-sharepoint.md).

- [웹 파트 또는 응용 프로그램 페이지에 다시 사용할 수 있는 컨트롤을 만듭니다](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>추가 정보

- [연습: 연결 및 초기화 폼이 있는 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [방법: 응용 프로그램 페이지 만들기](../sharepoint/how-to-create-an-application-page.md)
- [SharePoint에 대 한 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)