---
title: n 계층 데이터 세트에 유효성 검사 추가
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 91dbe04c85491a38a221edfb064702085136780f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283023"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>n 계층 데이터 세트에 유효성 검사 추가
N 계층 솔루션으로 분리 된 데이터 집합에 유효성 검사를 추가 하는 것은 기본적으로 단일 파일 데이터 집합에 유효성 검사를 추가 하는 것과 같습니다 (단일 프로젝트의 데이터 집합). 데이터에 대 한 유효성 검사를 수행 하기 위한 제안 된 위치는 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 데이터 테이블의 및/또는 이벤트 중입니다.

데이터 집합은 데이터 집합에 있는 데이터 테이블의 열 및 행 변경 이벤트에 사용자 코드를 추가할 수 있는 partial 클래스를 만드는 기능을 제공 합니다. N 계층 솔루션의 데이터 집합에 코드를 추가 하는 방법에 대 한 자세한 내용은 n 계층 [응용 프로그램의 데이터 집합에 코드 추가](../data-tools/add-code-to-datasets-in-n-tier-applications.md)및 [n 계층 응용 프로그램에서 Tableadapter에 코드 추가](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)를 참조 하세요. Partial 클래스에 대 한 자세한 내용은 [방법: 클래스를 부분 클래스 (클래스 디자이너)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) 또는 [partial 클래스 및 메서드로](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)분할을 참조 하세요.

> [!NOTE]
> **데이터 집합 프로젝트** 속성을 설정 하 여 tableadapter의 데이터 집합을 분리 하는 경우 프로젝트의 기존 부분 데이터 집합 클래스는 자동으로 이동 되지 않습니다. 기존 부분 데이터 집합 클래스는 데이터 집합 프로젝트로 수동으로 이동 해야 합니다.

> [!NOTE]
> 데이터 집합 디자이너는 및 이벤트에 대해 c #에서 이벤트 처리기를 자동으로 만들지 않습니다 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> . 이벤트 처리기를 수동으로 만들고 이벤트 처리기를 기본 이벤트에 연결 해야 합니다. 다음 절차에서는 Visual Basic 및 c #에서 필요한 이벤트 처리기를 만드는 방법을 설명 합니다.

## <a name="validate-changes-to-individual-columns"></a>개별 열에 대 한 변경 내용 유효성 검사
이벤트를 처리 하 여 개별 열에 있는 값의 유효성을 검사 <xref:System.Data.DataTable.ColumnChanging> 합니다. <xref:System.Data.DataTable.ColumnChanging>열의 값이 수정 되 면 발생 하는 이벤트입니다. <xref:System.Data.DataTable.ColumnChanging> **데이터 세트 디자이너**에서 원하는 열을 두 번 클릭 하 여 이벤트에 대 한 이벤트 처리기를 만듭니다.

처음으로 열을 두 번 클릭 하면 디자이너에서 이벤트에 대 한 이벤트 처리기를 생성 합니다 <xref:System.Data.DataTable.ColumnChanging> . `If...Then`특정 열을 테스트 하는 문도 생성 됩니다. 예를 들어 Northwind Orders 테이블에서 **RequiredDate** 열을 두 번 클릭 하면 다음 코드가 생성 됩니다.

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> C # 프로젝트에서 데이터 세트 디자이너는 데이터 집합 및 데이터 집합의 개별 테이블에 대 한 partial 클래스를 만듭니다. 데이터 세트 디자이너는 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> Visual Basic와 같이 c #에서 및 이벤트에 대 한 이벤트 처리기를 자동으로 만들지 않습니다. C # 프로젝트에서는 이벤트를 처리 하 고 메서드를 기본 이벤트에 연결 하는 메서드를 수동으로 생성 해야 합니다. 다음 절차에서는 Visual Basic 및 c #에서 필요한 이벤트 처리기를 만드는 단계를 제공 합니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>개별 열 값을 변경 하는 동안 유효성 검사를 추가 하려면

1. **솔루션 탐색기**에서 *.xsd* 파일을 두 번 클릭 하 여 데이터 집합을 엽니다. 자세한 내용은 [연습: 데이터 세트 디자이너에서 데이터 집합 만들기](walkthrough-creating-a-dataset-with-the-dataset-designer.md)를 참조 하세요.

2. 유효성을 검사할 열을 두 번 클릭 합니다. 이 작업은 <xref:System.Data.DataTable.ColumnChanging> 이벤트 처리기를 만듭니다.

    > [!NOTE]
    > 데이터 세트 디자이너는 c # 이벤트에 대 한 이벤트 처리기를 자동으로 만들지 않습니다. C #에서 이벤트를 처리 하는 데 필요한 코드는 다음 섹션에 포함 되어 있습니다. `SampleColumnChangingEvent`가 생성 된 다음 메서드의 이벤트에 연결 됩니다 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.EndInit%2A> .

3. `e.ProposedValue`응용 프로그램의 요구 사항을 충족 하는 데이터가 포함 되어 있는지 확인 하는 코드를 추가 합니다. 제안 된 값이 허용 되지 않는 경우 열에 오류가 포함 되어 있음을 나타내는 열을 설정 합니다.

     다음 코드 예에서는 **Quantity** 열에 0 보다 큰 값이 포함 되어 있는지 확인 합니다. **Quantity** 가 0 보다 작거나 같으면 열이 오류로 설정 됩니다. `Else` **Quantity** 가 0 보다 크면 절은 오류를 지웁니다. 열 변경 이벤트 처리기의 코드는 다음과 유사 합니다.

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```

    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>전체 행의 변경 내용 유효성 검사
이벤트를 처리 하 여 전체 행의 값에 대 한 유효성을 검사 <xref:System.Data.DataTable.RowChanging> 합니다. <xref:System.Data.DataTable.RowChanging>이 이벤트는 모든 열의 값이 커밋될 때 발생 합니다. <xref:System.Data.DataTable.RowChanging>한 열의 값이 다른 열의 값에 의존할 때 이벤트의 유효성을 검사 해야 합니다. 예를 들어 Northwind의 Orders 테이블에서 OrderDate 및 RequiredDate을 고려 합니다.

주문을 입력 하는 경우 유효성 검사를 수행 하면 OrderDate의 RequiredDate 이전에 주문이 입력 되지 않습니다. 이 예에서는 RequiredDate 열과 OrderDate 열 모두에 대 한 값을 비교 해야 하므로 개별 열 변경의 유효성을 검사 하는 것은 적합 하지 않습니다.

<xref:System.Data.DataTable.RowChanging> **데이터 세트 디자이너**테이블의 제목 표시줄에 있는 테이블 이름을 두 번 클릭 하 여 이벤트에 대 한 이벤트 처리기를 만듭니다.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>전체 행을 변경 하는 동안 유효성 검사를 추가 하려면

1. **솔루션 탐색기**에서 *.xsd* 파일을 두 번 클릭 하 여 데이터 집합을 엽니다. 자세한 내용은 [연습: 데이터 세트 디자이너에서 데이터 집합 만들기](walkthrough-creating-a-dataset-with-the-dataset-designer.md)를 참조 하세요.

2. 디자이너에서 데이터 테이블의 제목 표시줄을 두 번 클릭 합니다.

     Partial 클래스는 이벤트 처리기를 사용 하 여 생성 되 `RowChanging` 고 코드 편집기에서 열립니다.

    > [!NOTE]
    > 데이터 세트 디자이너는 <xref:System.Data.DataTable.RowChanging> c # 프로젝트에서 이벤트에 대 한 이벤트 처리기를 자동으로 만들지 않습니다. 이벤트를 처리 하 고 코드를 실행 하는 메서드를 만든 <xref:System.Data.DataTable.RowChanging> 다음 테이블의 초기화 메서드에서 이벤트를 후크합니다.

3. Partial 클래스 선언 내에 사용자 코드를 추가 합니다.

4. 다음 코드에서는 이벤트 중에 유효성을 검사 하는 사용자 코드를 추가할 위치를 보여 줍니다 <xref:System.Data.DataTable.RowChanging> . 또한 c # 예제에는 이벤트 처리기 메서드를 이벤트에 후크 하는 코드도 포함 되어 있습니다 `OrdersRowChanging` .

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```

    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>참조

- [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)
- [연습: N 계층 데이터 응용 프로그램 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [데이터 세트의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)
