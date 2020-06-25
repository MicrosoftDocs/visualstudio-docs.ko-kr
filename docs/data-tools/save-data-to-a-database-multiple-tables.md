---
title: 데이터베이스에 데이터 저장(여러 테이블)
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b512263cd5d0ca8c83b0ba6848fb16feca1a71f6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281645"
---
# <a name="save-data-to-a-database-multiple-tables"></a>데이터베이스에 데이터 저장(여러 테이블)

애플리케이션 개발에서 가장 일반적인 시나리오는 Windows 애플리케이션의 폼에 데이터를 표시하고 데이터를 편집한 다음 업데이트된 데이터를 데이터베이스로 다시 보내는 것입니다. 이 연습에서는 두 관련 테이블의 데이터를 표시하는 폼을 만들고, 레코드를 편집한 다음 변경 내용을 데이터베이스에 다시 저장하는 방법을 보여줍니다. 이 예에서는 Northwind 샘플 데이터베이스의 `Customers` 및 `Orders` 테이블을 사용합니다.

TableAdapter의 `Update` 메서드를 호출하여 애플리케이션의 데이터를 데이터베이스에 다시 저장할 수 있습니다. **데이터 소스** 창에서 폼으로 테이블을 끌어다 놓으면 데이터를 저장 하는 데 필요한 코드가 자동으로 추가 됩니다. 양식에 추가 된 추가 테이블에는이 코드를 수동으로 추가 해야 합니다. 이 연습에서는 둘 이상의 테이블에서 업데이트를 저장하는 코드를 추가하는 방법을 보여줍니다.

이 연습에서 설명하는 작업은 다음과 같습니다.

- [데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png)를 사용 하 여 응용 프로그램에서 데이터 소스를 만들고 구성 합니다.

- [데이터 소스 창](add-new-data-sources.md#data-sources-window)에서 항목의 컨트롤을 설정 합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

- **데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만듭니다.

- 데이터 집합의 각 테이블에서 몇 개의 레코드를 수정 합니다.

- 데이터 세트의 업데이트된 데이터를 데이터베이스로 다시 보내도록 코드를 수정합니다.

## <a name="prerequisites"></a>필수 구성 요소

이 연습에서는 SQL Server Express LocalDB 및 Northwind 샘플 데이터베이스를 사용 합니다.

1. LocalDB SQL Server Express 없는 경우 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 또는 **Visual Studio 설치 관리자**를 통해 설치 합니다. **Visual Studio 설치 관리자**에서 **데이터 저장소 및 처리** 워크 로드의 일부로 또는 개별 구성 요소로 SQL Server Express LocalDB를 설치할 수 있습니다.

2. 다음 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 **SQL Server 개체 탐색기** 창을 엽니다. SQL Server 개체 탐색기는 **데이터 저장소 및 처리** 워크 로드의 일부로 Visual Studio 설치 관리자에 설치 됩니다. **SQL Server** 노드를 확장 합니다. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 **새 쿼리**를 선택 합니다.

       쿼리 편집기 창이 열립니다.

    2. [Northwind transact-sql 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 를 클립보드에 복사 합니다. 이 T-sql 스크립트는 Northwind 데이터베이스를 처음부터 만들어 데이터로 채웁니다.

    3. T-sql 스크립트를 쿼리 편집기에 붙여 넣은 다음 **실행** 단추를 선택 합니다.

       잠시 후 쿼리 실행이 완료 되 고 Northwind 데이터베이스가 만들어집니다.

## <a name="create-the-windows-forms-application"></a>Windows Forms 응용 프로그램 만들기

C # 또는 Visual Basic에 대 한 새 **Windows Forms 앱** 프로젝트를 만듭니다. 프로젝트 이름을 **UpdateMultipleTablesWalkthrough**로 지정합니다.

## <a name="create-the-data-source"></a>데이터 원본 만들기

이 단계에서는 **데이터 원본 구성 마법사**를 사용하여 Northwind 데이터베이스에서 데이터 원본을 만듭니다. 연결을 만들려면 Northwind 샘플 데이터베이스에 액세스해야 합니다. Northwind 샘플 데이터베이스를 설정 하는 방법에 대 한 자세한 내용은 [방법: 샘플 데이터베이스 설치](../data-tools/installing-database-systems-tools-and-samples.md)를 참조 하세요.

1. **데이터** 메뉴에서 **데이터 소스 표시**를 선택 합니다.

   **데이터 원본** 창이 열립니다.

2. **데이터** 소스 창에서 **새 데이터 소스 추가** 를 선택 하 여 **데이터 소스 구성 마법사**를 시작 합니다.

3. **데이터 소스 형식 선택** 화면에서 **데이터베이스**를 선택 하 고 **다음**을 선택 합니다.

4. **데이터 연결 선택** 화면에서 다음 중 하나를 수행 합니다.

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

         또는

    - **새 연결**을 선택하여 **연결 추가 또는 수정** 대화 상자를 엽니다.

5. 데이터베이스에 암호가 필요 하면 중요 한 데이터를 포함 하는 옵션을 선택 하 고 **다음**을 선택 합니다.

6. **응용 프로그램 구성 파일에 연결 문자열 저장**에서 **다음**을 선택 합니다.

7. **데이터베이스 개체 선택** 화면에서 **테이블** 노드를 확장 합니다.

8. **Customers** 및 **Orders** 테이블을 선택한 다음 **마침**을 선택 합니다.

     **NorthwindDataSet**가 프로젝트에 추가되고 테이블이 **데이터 원본** 창에 나타납니다.

## <a name="set-the-controls-to-be-created"></a>만들 컨트롤 설정

이 연습에서 테이블의 데이터는 `Customers` 개별 컨트롤에 데이터가 표시 되는 **세부 정보** 레이아웃에 있습니다. 테이블의 데이터는 `Orders` 컨트롤에 표시 되는 **그리드** 레이아웃에 <xref:System.Windows.Forms.DataGridView> 있습니다.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>데이터 소스 창에서 항목에 대한 삭제 유형을 설정하려면

1. **데이터 소스** 창에서 **Customers** 노드를 확장 합니다.

2. **Customers** 노드의 컨트롤 목록에서 **세부 정보** 를 선택 하 여 **customers** 테이블의 컨트롤을 개별 컨트롤로 변경 합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

## <a name="create-the-data-bound-form"></a>데이터 바인딩된 폼 만들기

**데이터 소스** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다.

1. 주 **Customers** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어서 놓습니다.

     설명 레이블이 있는 데이터 바인딩된 컨트롤이 레코드 탐색을 위한 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>와 함께 폼에 나타납니다. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md),, `CustomersTableAdapter` <xref:System.Windows.Forms.BindingSource> 및가 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다.

2. 관련 **Orders** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어 옵니다.

    > [!NOTE]
    > **Fax** 열 아래에 있는 관련 **Orders** 노드는 **Customers** 노드의 자식 노드입니다.

     <xref:System.Windows.Forms.DataGridView> 컨트롤과 레코드 탐색에 사용되는 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>가 폼에 나타납니다. `OrdersTableAdapter`및가 <xref:System.Windows.Forms.BindingSource> 구성 요소 트레이에 나타납니다.

## <a name="add-code-to-update-the-database"></a>데이터베이스를 업데이트 하는 코드 추가

**Customers** 및 **Orders** TableAdapters의 `Update` 메서드를 호출하여 데이터베이스를 업데이트할 수 있습니다. 기본적으로의 **저장** 단추에 대 한 이벤트 처리기는 <xref:System.Windows.Forms.BindingNavigator> 데이터베이스에 업데이트를 보내기 위해 폼의 코드에 추가 됩니다. 이 절차에서는 업데이트를 올바른 순서로 보내도록 코드를 수정 합니다. 이렇게 하면 참조 무결성 오류가 발생 하는 가능성이 없어집니다. 또한 이 코드는 try-catch 블록에서 업데이트 호출을 래핑하여 오류 처리를 구현합니다. 애플리케이션의 요구 사항에 맞게 코드를 수정할 수 있습니다.

> [!NOTE]
> 명확 하 게 하기 위해이 연습에서는 트랜잭션을 사용 하지 않습니다. 그러나 두 개 이상의 관련 테이블을 업데이트 하는 경우에는 트랜잭션 내의 모든 업데이트 논리를 포함 합니다. 트랜잭션은 변경 내용을 커밋하기 전에 데이터베이스의 모든 관련 변경 내용이 성공 하도록 하는 프로세스입니다. 자세한 내용은 [트랜잭션 및 동시성](/dotnet/framework/data/adonet/transactions-and-concurrency)을 참조 하세요.

### <a name="to-add-update-logic-to-the-application"></a>애플리케이션에 업데이트 논리를 추가하려면

1. 에서 **저장** 단추를 선택 합니다 <xref:System.Windows.Forms.BindingNavigator> . 그러면 이벤트 처리기에 대 한 코드 편집기가 열립니다 `bindingNavigatorSaveItem_Click` .

2. 관련 TableAdapter의 `Update` 메서드를 호출하도록 이벤트 처리기의 코드를 바꿉니다. 다음 코드는 먼저 각 <xref:System.Data.DataRowState>(<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> 및 <xref:System.Data.DataRowState.Modified>)에 대해 업데이트된 정보를 저장할 3개 임시 데이터 테이블을 만듭니다. 업데이트는 올바른 순서 대로 실행 됩니다. 이 코드는 다음과 같습니다.

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>애플리케이션 테스트

1. **F5**키를 누릅니다.

2. 각 테이블에 포함된 레코드 하나 이상의 데이터를 변경해 봅니다.

3. **저장** 단추를 선택합니다.

4. 데이터베이스의 값을 점검하여 변경 내용이 저장되었는지 확인합니다.

## <a name="see-also"></a>참조

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
