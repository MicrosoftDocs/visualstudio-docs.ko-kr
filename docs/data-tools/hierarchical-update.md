---
title: 계층적 업데이트
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 158908c45d33781bc9f983950d5558a23481ad37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586577"
---
# <a name="hierarchical-update"></a>계층적 업데이트

*계층적 업데이트* 는 참조 무결성 규칙을 유지 하면서 업데이트 된 데이터를 두 개 이상의 관련 테이블이 있는 데이터 집합에서 데이터베이스에 다시 저장 하는 프로세스를 의미 합니다. *참조 무결성* 은 관련 레코드 삽입, 업데이트 및 삭제 동작을 제어 하는 데이터베이스의 제약 조건에서 제공 하는 일관성 규칙을 나타냅니다. 예를 들어 고객 레코드 만들기를 적용 하는 참조 무결성을 적용 하 여 해당 고객에 대 한 주문을 만들도록 허용 합니다.  데이터 집합의 관계에 대 한 자세한 내용은 [데이터 집합의 관계](../data-tools/relationships-in-datasets.md)를 참조 하세요.

계층적 업데이트 기능은를 사용 하 여 `TableAdapterManager` 형식화 된 `TableAdapter` 데이터 집합의를 관리 합니다. `TableAdapterManager`구성 요소는 .net 형식이 아닌 Visual Studio에서 생성 된 클래스입니다. **데이터 소스** 창에서 Windows FORM 또는 WPF 페이지로 테이블을 끌어 오면 Visual Studio에서 TableAdapterManager 형식의 변수를 폼 이나 페이지에 추가 하 고 디자이너의 구성 요소 트레이에 표시 합니다. 클래스에 대 한 자세한 내용은 `TableAdapterManager` [Tableadapter](../data-tools/create-and-configure-tableadapters.md)의 TableAdapterManager 참조 섹션을 참조 하세요.

기본적으로 데이터 집합은 관련 테이블을 "관계 전용"으로 처리 합니다. 즉, foreign key 제약 조건을 적용 하지 않습니다. **데이터 세트 디자이너**를 사용 하 여 디자인 타임에 해당 설정을 수정할 수 있습니다. 두 테이블 간의 관계 선을 선택 하 여 **관계** 대화 상자를 표시 합니다. 여기에서 변경한 내용에 따라 `TableAdapterManager` 관련 테이블의 변경 내용을 데이터베이스에 다시 보낼 때가 동작 하는 방식이 결정 됩니다.

## <a name="enable-hierarchical-update-in-a-dataset"></a>데이터 집합에서 계층적 업데이트를 사용 하도록 설정

기본적으로 계층적 업데이트는 프로젝트에서 추가 되거나 만들어진 모든 새 데이터 집합에 대해 사용 하도록 설정 됩니다. 데이터 집합에서 형식화 된 데이터 집합의 **계층적 업데이트** 속성을 **True** 또는 **False**로 설정 하 여 계층적 업데이트를 설정 하거나 해제 합니다.

![계층적 업데이트 설정](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>테이블 간에 새 관계 만들기

두 테이블 간에 새 관계를 만들려면 데이터 세트 디자이너에서 각 테이블의 제목 표시줄을 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **관계 추가**를 선택 합니다.

![계층 구조 업데이트 관계 추가 메뉴](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>외래 키 제약 조건, 연계 업데이트 및 삭제 이해

생성 된 데이터 집합 코드에서 데이터베이스의 foreign key 제약 조건 및 연계 동작을 만드는 방법을 이해 하는 것이 중요 합니다.

기본적으로 데이터 집합의 데이터 테이블은 <xref:System.Data.DataRelation> 데이터베이스의 관계와 일치 하는 관계 ()를 사용 하 여 생성 됩니다. 그러나 데이터 집합의 관계는 외래 키 제약 조건으로 생성 되지 않습니다. 는 <xref:System.Data.DataRelation> 또는가 적용 되지 않은 경우에 **만 관계로** 구성 됩니다 <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> .

기본적으로 연계 업데이트 및/또는 연계 된 삭제가 설정 된 상태에서 데이터베이스 관계가 설정 된 경우에도 연계 업데이트 및 연계 삭제는 해제 됩니다. 예를 들어 새 고객과 새 주문을 만든 다음 데이터를 저장 하려고 하면 데이터베이스에 정의 된 foreign key 제약 조건과 충돌이 발생할 수 있습니다. 자세한 내용은 [데이터 집합을 채우는 동안 제약 조건](turn-off-constraints-while-filling-a-dataset.md)해제를 참조 하세요.

## <a name="set-the-order-to-perform-updates"></a>업데이트를 수행 하는 순서 설정

업데이트를 수행 하는 순서를 설정 하면 데이터 집합의 모든 테이블에 수정 된 모든 데이터를 저장 하는 데 필요한 개별 삽입, 업데이트 및 삭제 순서가 설정 됩니다. 계층적 업데이트를 사용 하는 경우 삽입이 먼저 수행 된 다음 업데이트 및 삭제 됩니다. 는 `TableAdapterManager` `UpdateOrder` 먼저 업데이트를 수행 하 고 삽입 한 다음 삭제를 수행 하도록 설정할 수 있는 속성을 제공 합니다.

> [!NOTE]
> 업데이트 순서는 모두 포함 된다는 것을 이해 하는 것이 중요 합니다. 즉, 업데이트를 수행 하는 경우 데이터 집합의 모든 테이블에 대 한 삽입 및 삭제 작업이 수행 됩니다.

속성을 설정 하려면 `UpdateOrder` [데이터 소스 창](add-new-data-sources.md#data-sources-window) 에서 폼으로 항목을 끌어 온 후 `TableAdapterManager` 구성 요소 트레이에서를 선택 하 고 속성 `UpdateOrder` 창에서 속성을 설정 합니다. **Properties**

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>계층적 업데이트를 수행 하기 전에 데이터 집합의 백업 복사본 만들기

메서드를 호출 하 여 데이터를 저장 하면 `TableAdapterManager.UpdateAll()` 에서 `TableAdapterManager` 단일 트랜잭션으로 각 테이블에 대 한 데이터를 업데이트 하려고 시도 합니다. 테이블에 대 한 업데이트의 일부가 실패 하면 전체 트랜잭션이 롤백됩니다. 대부분의 경우 롤백은 응용 프로그램을 원래 상태로 되돌립니다.

그러나 경우에 따라 백업 복사본에서 데이터 집합을 복원 하는 것이 좋습니다. 자동 증분 값을 사용 하는 경우이에 대 한 한 가지 예가 발생할 수 있습니다. 예를 들어 저장 작업에 성공 하지 못하면 자동 증분 값이 데이터 집합에서 다시 설정 되지 않으며 데이터 집합은 자동 증분 값을 계속 만듭니다. 이로 인해 응용 프로그램에서 허용 되지 않는 번호 매기기 간격이 남아 있습니다. 이 문제가 발생 하는 상황에서는 `TableAdapterManager` `BackupDataSetBeforeUpdate` 트랜잭션이 실패할 경우 기존 데이터 집합을 백업 복사본으로 대체 하는 속성을 제공 합니다.

> [!NOTE]
> 메서드를 실행 하는 동안에만 백업 복사본이 메모리에 `TableAdapterManager.UpdateAll` 있습니다. 따라서 원래 데이터 집합을 대체 하거나 메서드가 실행을 완료 하는 즉시 범위를 벗어나기 때문에이 백업 데이터 집합에 대 한 프로그래밍 방식의 액세스는 없습니다 `TableAdapterManager.UpdateAll` .

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>생성 된 저장 코드를 수정 하 여 계층적 업데이트 수행

`TableAdapterManager.UpdateAll` 메서드를 호출한 다음 관련 테이블이 포함된 데이터 세트의 이름을 전달하여 데이터 세트의 관련 데이터 테이블에서 데이터베이스로 변경 내용을 저장합니다. 예를 들어 NorthwindDataset에 포함된 모든 테이블의 업데이트를 백 엔드 데이터베이스로 보내려면 `TableAdapterManager.UpdateAll(NorthwindDataset)` 메서드를 실행합니다.

**데이터 원본** 창에서 항목을 놓으면 코드가 `Form_Load` 이벤트에 자동으로 추가되어 각 테이블을 채웁니다(`TableAdapter.Fill` 메서드). 또한 데이터 세트의 데이터를 데이터베이스에 다시 저장할 수 있도록 <xref:System.Windows.Forms.BindingNavigator>의 **저장** 단추 클릭 이벤트에도 코드가 추가됩니다(`TableAdapterManager.UpdateAll` 메서드).

생성된 저장 코드에는 `CustomersBindingSource.EndEdit` 메서드를 호출하는 코드 줄도 포함됩니다. 구체적으로 말하면 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 폼에 추가 된 첫 번째의 메서드를 호출 합니다 <xref:System.Windows.Forms.BindingSource> . 즉,이 코드는 **데이터 소스** 창에서 폼으로 끌어온 첫 번째 테이블에 대해서만 생성 됩니다. <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 호출에서는 현재 편집 중인 데이터 바인딩된 컨트롤의 프로세스에 포함된 모든 변경 내용을 커밋합니다. 따라서 데이터 바인딩된 컨트롤에 계속 포커스가 있는 상태에서 **저장** 단추를 클릭하면 실제 저장 전에 해당 컨트롤에서 보류 중인 모든 편집 내용이 커밋됩니다(`TableAdapterManager.UpdateAll` 메서드).

> [!NOTE]
> **데이터 세트 디자이너** 는 `BindingSource.EndEdit` 폼에 끌어 놓은 첫 번째 테이블에 대해서만 코드를 추가 합니다. 그러므로 폼의 각 관련 테이블에 대해 `BindingSource.EndEdit` 메서드를 호출하는 코드 줄을 추가해야 합니다. 이 연습에서는 `OrdersBindingSource.EndEdit` 메서드 호출을 추가해야 합니다.

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>저장 전에 관련 테이블로 변경 내용을 커밋하도록 코드를 업데이트하려면

1. <xref:System.Windows.Forms.BindingNavigator>에서 **저장** 단추를 두 번 클릭하여 코드 편집기에서 **Form1**을 엽니다.

2. `OrdersBindingSource.EndEdit` 메서드를 호출하는 줄 뒤에 `CustomersBindingSource.EndEdit` 메서드를 호출하는 코드 줄을 추가합니다. **저장** 단추 클릭 이벤트 내의 코드는 다음과 같습니다.

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

이처럼 데이터를 데이터베이스에 저장하기 전에 관련 자식 테이블에 대해 변경 내용을 커밋해야 할 뿐 아니라 새 자식 레코드를 데이터 세트에 추가하기 전에 새로 만든 부모 레코드도 커밋해야 할 수 있습니다. 즉, 새 `Customer` 자식 레코드 ( `Orders` )를 데이터 집합에 추가 하기 전에 새 부모 레코드 ()를 데이터 집합에 추가 해야 할 수도 있습니다. 자식 `BindingSource.AddingNew` 이벤트를 사용하면 이 작업을 수행할 수 있습니다.

> [!NOTE]
> 새 부모 레코드를 커밋해야 하는지 여부는 데이터 원본에 바인딩하는 데 사용 되는 컨트롤의 형식에 따라 달라 집니다. 이 연습에서는 개별 컨트롤을 사용 하 여 부모 테이블에 바인딩합니다. 이렇게 하려면 새 부모 레코드를 커밋하는 추가 코드가 필요 합니다. 부모 레코드가와 같은 복합 바인딩 컨트롤에 표시 되는 경우에는 <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 부모 레코드에 대 한 추가 호출이 필요 하지 않습니다. 컨트롤의 기본 데이터 바인딩 기능이 새 레코드 커밋을 처리하기 때문입니다.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>새 자식 레코드를 추가하기 전에 데이터 세트에서 부모 레코드를 커밋하는 코드를 추가하려면

1. `OrdersBindingSource.AddingNew` 이벤트에 대한 이벤트 처리기를 만듭니다.

    - 디자인 뷰에서 **Form1** 을 열고 구성 요소 트레이에서 **OrdersBindingSource** 를 선택한 다음 **속성** 창에서 **이벤트** 를 선택 하 고 **system.windows.forms.dataconnector.addingnew** 이벤트를 두 번 클릭 합니다.

2. 메서드를 호출 하는 이벤트 처리기에 코드 줄을 추가 `CustomersBindingSource.EndEdit` 합니다. `OrdersBindingSource_AddingNew` 이벤트 처리기의 코드는 다음과 같습니다.

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager 참조

기본적으로 클래스는 `TableAdapterManager` 관련 테이블을 포함 하는 데이터 집합을 만들 때 생성 됩니다. 클래스가 생성 되지 않도록 하려면 `Hierarchical Update` 데이터 집합의 속성 값을 false로 변경 합니다. 관계가 있는 테이블을 Windows Form 또는 WPF 페이지의 디자인 화면으로 끌어 오면 Visual Studio에서 클래스의 멤버 변수를 선언 합니다. 데이터 바인딩을 사용 하지 않는 경우 변수를 수동으로 선언 해야 합니다.

`TableAdapterManager`클래스가 .net 형식이 아닙니다. 따라서 설명서에서 확인할 수 없습니다. 디자인 타임에 데이터 집합 생성 프로세스의 일부로 만들어집니다.

다음은 클래스의 자주 사용 되는 메서드와 속성입니다 `TableAdapterManager` .

|멤버|설명|
|------------|-----------------|
|`UpdateAll` 메서드|모든 데이터 테이블의 모든 데이터를 저장 합니다.|
|`BackUpDataSetBeforeUpdate` 속성|메서드를 실행 하기 전에 데이터 집합의 백업 복사본을 만들지 여부를 결정 합니다 `TableAdapterManager.UpdateAll` . 부울.|
|*tableName* `TableAdapter` 속성|를 나타냅니다 `TableAdapter` . 생성 된에는 `TableAdapterManager` 관리 하는 각 클래스에 대 한 속성이 포함 `TableAdapter` 됩니다. 예를 들어 Customers 및 Orders 테이블이 포함 된 데이터 집합은 `TableAdapterManager` 및 속성이 포함 된를 사용 하 여 생성 됩니다 `CustomersTableAdapter` `OrdersTableAdapter` .|
|`UpdateOrder` 속성|개별 insert, update 및 delete 명령의 순서를 제어 합니다. 열거형의 값 중 하나로 설정 `TableAdapterManager.UpdateOrderOption` 합니다.<br /><br /> 기본적으로은 `UpdateOrder` **Insertupdatedelete**로 설정 됩니다. 즉, 데이터 집합의 모든 테이블에 대 한 삽입, 업데이트 및 삭제 작업이 수행 됩니다.|

## <a name="see-also"></a>추가 정보

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
