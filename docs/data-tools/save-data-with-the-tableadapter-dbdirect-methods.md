---
title: TableAdapter DBDirect 메서드를 사용하여 데이터 저장
description: 이 연습에서는 TableAdapter의 DBDirect 메서드를 사용 하 여 데이터베이스에 대해 직접 SQL 문을 실행 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 00f508163dc039d5c29013538a78fa7dab6091fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858451"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>TableAdapter DBDirect 메서드를 사용하여 데이터 저장

이 연습에서는 TableAdapter의 DBDirect 메서드를 사용 하 여 데이터베이스에 대해 직접 SQL 문을 실행 하기 위한 자세한 지침을 제공 합니다. TableAdapter의 DBDirect 메서드는 데이터베이스 업데이트에 대한 상세 제어 수준을 제공합니다. 응용 프로그램에서 필요에 따라 개별, 및 메서드를 호출 하 여 특정 SQL 문 및 저장 프로시저를 실행 하는 데 사용할 수 있습니다 `Insert` `Update` `Delete` `Update` .이 메서드는 한 번의 호출로 UPDATE, INSERT 및 DELETE 문을 수행 하는 오버 로드 된 메서드가 아니라

이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- 새 **Windows Forms 응용 프로그램** 을 만듭니다.

- [데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png)를 사용 하 여 데이터 집합을 만들고 구성 합니다.

- **데이터 원본** 창에서 항목을 끌어오는 경우 폼에 만들어질 컨트롤을 선택합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

- **데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 폼을 만듭니다.

- 데이터베이스에 직접 액세스 하 고 삽입, 업데이트 및 삭제를 수행 하는 메서드를 추가 합니다.

## <a name="prerequisites"></a>사전 준비 사항

이 연습에서는 SQL Server Express LocalDB 및 Northwind 샘플 데이터베이스를 사용 합니다.

1. LocalDB SQL Server Express 없는 경우 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 또는 **Visual Studio 설치 관리자** 를 통해 설치 합니다. **Visual Studio 설치 관리자** 에서 **데이터 저장소 및 처리** 워크 로드의 일부로 또는 개별 구성 요소로 SQL Server Express LocalDB를 설치할 수 있습니다.

2. 다음 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 **SQL Server 개체 탐색기** 창을 엽니다. SQL Server 개체 탐색기는 **데이터 저장소 및 처리** 워크 로드의 일부로 Visual Studio 설치 관리자에 설치 됩니다. **SQL Server** 노드를 확장 합니다. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 **새 쿼리** 를 선택 합니다.

       쿼리 편집기 창이 열립니다.

    2. [Northwind transact-sql 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 를 클립보드에 복사 합니다. 이 T-sql 스크립트는 Northwind 데이터베이스를 처음부터 만들어 데이터로 채웁니다.

    3. T-sql 스크립트를 쿼리 편집기에 붙여 넣은 다음 **실행** 단추를 선택 합니다.

       잠시 후 쿼리 실행이 완료 되 고 Northwind 데이터베이스가 만들어집니다.

## <a name="create-a-windows-forms-application"></a>Windows Forms 애플리케이션 만들기

첫 번째 단계는 **Windows Forms 응용 프로그램** 을 만드는 것입니다.

1. Visual Studio의 **파일** 메뉴에서 **새로 만들기** > **프로젝트** 를 차례로 선택합니다.

2. 왼쪽 창에서 **Visual c #** 또는 **Visual Basic** 을 확장 한 다음 **Windows 데스크톱** 을 선택 합니다.

3. 가운데 창에서 **Windows Forms 앱** 프로젝트 형식을 선택 합니다.

4. 프로젝트 이름을 **TableAdapterDbDirectMethodsWalkthrough** 로 지정한 다음 **확인** 을 선택 합니다.

     **TableAdapterDbDirectMethodsWalkthrough** 프로젝트가 만들어져 **솔루션 탐색기** 에 추가됩니다.

## <a name="create-a-data-source-from-your-database"></a>데이터베이스에서 데이터 원본 만들기

이 단계에서는 **데이터 소스 구성 마법사** 를 사용 하 여 `Region` Northwind 샘플 데이터베이스의 테이블을 기반으로 데이터 원본을 만듭니다. 연결을 만들려면 Northwind 샘플 데이터베이스에 액세스해야 합니다. Northwind 샘플 데이터베이스를 설정 하는 방법에 대 한 자세한 내용은 [방법: 샘플 데이터베이스 설치](../data-tools/installing-database-systems-tools-and-samples.md)를 참조 하세요.

### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면

1. **데이터** 메뉴에서 **데이터 원본 표시** 를 선택합니다.

   **데이터 원본** 창이 열립니다.

2. **데이터** 소스 창에서 **새 데이터 소스 추가** 를 선택 하 여 **데이터 소스 구성 마법사** 를 시작 합니다.

3. **데이터 소스 형식 선택** 화면에서 **데이터베이스** 를 선택 하 고 **다음** 을 선택 합니다.

4. **데이터 연결 선택** 화면에서 다음 중 하나를 수행 합니다.

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

         또는

    - **새 연결** 을 선택하여 **연결 추가/수정** 대화 상자를 시작합니다.

5. 데이터베이스에 암호가 필요 하면 중요 한 데이터를 포함 하는 옵션을 선택 하 고 **다음** 을 선택 합니다.

6. **응용 프로그램 구성 파일에 연결 문자열 저장** 화면에서 **다음** 을 선택 합니다.

7. **데이터베이스 개체 선택** 화면에서 **테이블** 노드를 확장 합니다.

8. `Region`테이블을 선택 하 고 **마침** 을 선택 합니다.

     **NorthwindDataSet** 가 프로젝트에 추가되고 `Region` 테이블이 **데이터 원본** 창에 나타납니다.

## <a name="add-controls-to-the-form-to-display-the-data"></a>폼에 데이터를 표시 하는 컨트롤 추가

**데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만듭니다.

Windows form에서 데이터 바인딩된 컨트롤을 만들려면 주 **지역** 노드를 **데이터 소스** 창에서 폼으로 끌어 옵니다.

<xref:System.Windows.Forms.DataGridView> 컨트롤과 레코드 탐색에 사용되는 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>가 폼에 나타납니다. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md),, `RegionTableAdapter` <xref:System.Windows.Forms.BindingSource> 및가 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>개별 TableAdapter DbDirect 메서드를 호출하는 단추를 추가하려면

1. <xref:System.Windows.Forms.Button> 컨트롤 3개를 **도구 상자** 에서 **Form1** 의 **RegionDataGridView** 아래로 끌어 옵니다.

2. 각 단추에 대해 다음 **이름** 및 **텍스트** 속성을 설정합니다.

    |이름|텍스트|
    |----------|----------|
    |`InsertButton`|**삽입**|
    |`UpdateButton`|**업데이트**|
    |`DeleteButton`|**Delete**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>데이터베이스에 새 레코드를 삽입하는 코드를 추가하려면

1. **InsertButton** 를 선택 하 여 click 이벤트에 대 한 이벤트 처리기를 만들고 코드 편집기에서 폼을 엽니다.

2. `InsertButton_Click` 이벤트 처리기를 다음 코드로 바꿉니다.

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>데이터베이스에서 레코드를 업데이트하는 코드를 추가하려면

1. **UpdateButton** 을 두 번 클릭하여 클릭 이벤트에 대한 이벤트 처리기를 만들고 코드 편집기에서 폼을 엽니다.

2. `UpdateButton_Click` 이벤트 처리기를 다음 코드로 바꿉니다.

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>데이터베이스에서 레코드를 삭제 하는 코드를 추가 하려면

1. **Deletebutton** 을 선택 하 여 click 이벤트에 대 한 이벤트 처리기를 만들고 코드 편집기에서 폼을 엽니다.

2. `DeleteButton_Click` 이벤트 처리기를 다음 코드로 바꿉니다.

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>애플리케이션 실행

- **F5 키** 를 선택 하 여 응용 프로그램을 실행 합니다.

- **삽입** 단추를 선택 하 고 새 레코드가 표에 표시 되는지 확인 합니다.

- **업데이트** 단추를 선택 하 고 레코드가 표에서 업데이트 되었는지 확인 합니다.

- **삭제** 단추를 선택 하 고 레코드가 표에서 제거 되었는지 확인 합니다.

## <a name="next-steps"></a>다음 단계

응용 프로그램 요구 사항에 따라 데이터 바인딩된 폼을 만든 후 몇 단계를 더 수행 해야 할 수도 있습니다. 이 연습에서 보완할 수 있는 사항은 다음과 같습니다.

- 폼에 검색 기능을 추가합니다.

- **데이터 원본** 창에서 **마법사로 데이터 세트 구성** 을 선택하여 추가 테이블을 데이터 세트에 추가합니다. 관련 노드를 폼으로 끌어 관련 데이터를 표시하는 컨트롤을 추가할 수 있습니다. 자세한 내용은 [데이터 집합의 관계](relationships-in-datasets.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
