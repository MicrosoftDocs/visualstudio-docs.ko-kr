---
title: TableAdapters를 사용하여 데이터 세트 채우기
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a79f7b781944bb93a60794e748eefb9375723384
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301196"
---
# <a name="fill-datasets-by-using-tableadapters"></a>TableAdapters를 사용하여 데이터 세트 채우기

TableAdapter 구성 요소는 지정한 하나 이상의 쿼리 또는 저장 프로시저에 따라 데이터베이스의 데이터로 데이터 집합을 채웁니다. TableAdapters는 데이터베이스에서 추가, 업데이트 및 삭제를 수행하여 데이터 집합에 대한 변경 내용을 지속할 수도 있습니다. 특정 테이블과 관련이 없는 전역 명령을 발행할 수도 있습니다.

> [!NOTE]
> 테이블 어댑터는 비주얼 스튜디오 디자이너에 의해 생성됩니다. 프로그래밍 방식으로 데이터 집합을 만드는 경우 .NET 클래스인 DataAdapter를 사용합니다.

TableAdapter 작업에 대한 자세한 내용은 다음 항목 중 하나로 직접 건너뛸 수 있습니다.

|항목|Description|
|-----------|-----------------|
|[TableAdapter 만들기 및 구성](../data-tools/create-and-configure-tableadapters.md)|디자이너를 사용하여 TableAdapters를 만들고 구성하는 방법|
|[매개 변수가 있는 TableAdapter 쿼리 만들기](../data-tools/create-parameterized-tableadapter-queries.md)|사용자가 TableAdapter 프로시저 또는 쿼리에 인수를 제공할 수 있도록 하는 방법|
|[TableAdapter를 사용하여 데이터베이스에 직접 액세스](../data-tools/directly-access-the-database-with-a-tableadapter.md)|테이블어댑터의 Dbdirect 방법을 사용하는 방법|
|[데이터 세트를 채우는 동안 제약 조건 해제](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|데이터 업데이트 시 외래 키 제약 조건으로 작업하는 방법|
|[TableAdapter의 기능 확장 방법](../data-tools/fill-datasets-by-using-tableadapters.md)|TableAdapters에 사용자 지정 코드를 추가하는 방법|
|[XML 데이터를 데이터 세트에 읽어오기](../data-tools/read-xml-data-into-a-dataset.md)|XML작업|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter 개요

TableAdapters는 데이터베이스에 연결하고 쿼리 또는 저장 프로시저를 실행하고 DataTable을 반환된 데이터로 채우는 디자이너에서 생성한 구성 요소입니다. 또한 TableAdapters는 응용 프로그램에서 업데이트된 데이터를 데이터베이스로 다시 보냅니다. TableAdapter가 연결된 테이블의 스키마에 맞는 데이터를 반환하는 한 TableAdapter에서 원하는 만큼 쿼리를 실행할 수 있습니다. 다음 다이어그램에서는 TableAdapters가 메모리의 데이터베이스 및 기타 개체와 상호 작용하는 방법을 보여 주며 있습니다.

![클라이언트 애플리케이션의 데이터 흐름](../data-tools/media/clientdatadiagram.gif)

TableAdapter는 **데이터 집합 디자이너로**설계되었지만 TableAdapter 클래스는 의 <xref:System.Data.DataSet>중첩 된 클래스로 생성되지 않습니다. 각 데이터 집합에 특정한 별도의 네임스페이스에 있습니다. 예를 `NorthwindDataSet`들어, 라는 데이터 집합이 있는 경우 , s와 <xref:System.Data.DataTable>연결된 `NorthwindDataSet` TableAdapters는 `NorthwindDataSetTableAdapters` 네임스페이스에 있을 것입니다. 특정 TableAdapter에 프로그래밍 방식으로 액세스하려면 TableAdapter의 새 인스턴스를 선언해야 합니다. 다음은 그 예입니다.

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>연결된 데이터 테이블 스키마

TableAdapter를 만들 때 초기 쿼리 또는 저장 프로시저를 사용하여 TableAdapter와 연결된 <xref:System.Data.DataTable>스키마를 정의합니다. TableAdapter의 `Fill` 메서드(TableAdapter의 관련 <xref:System.Data.DataTable>메서드를 채우는)를 호출하여 이 초기 쿼리 또는 저장 프로시저를 실행합니다. TableAdapter의 기본 쿼리에 대한 모든 변경 내용은 연결된 데이터 테이블의 스키마에 반영됩니다. 예를 들어 주 쿼리에서 열을 제거하면 연결된 데이터 테이블에서 열도 제거됩니다. TableAdapter의 추가 쿼리가 주 쿼리에 없는 열을 반환하는 SQL 문을 사용하는 경우 디자이너는 주 쿼리와 추가 쿼리 간에 열 변경 내용을 동기화하려고 시도합니다.

## <a name="tableadapter-update-commands"></a>테이블 어댑터 업데이트 명령

TableAdapter의 업데이트 기능은 **TableAdapter 마법사의**기본 쿼리에서 사용할 수 있는 정보의 양에 따라 다릅니다. 예를 들어 여러 테이블(a `JOIN`사용)에서 값을 가져오도록 구성된 TableAdapters는 기본 데이터베이스로 업데이트를 다시 보낼 수 있는 기능으로 처음에 만들어지지 않고 스칼라 값, 뷰 또는 집계 함수의 결과를 생성하지 않습니다. 그러나 속성 창에서 `INSERT` `UPDATE`에서 `DELETE` 에서 및 명령을 **Properties** 수동으로 구성할 수 있습니다.

## <a name="tableadapter-queries"></a>TableAdapter 쿼리

![쿼리가 여러 개 포함된 TableAdapter](../data-tools/media/tableadapter.gif)

TableAdapters는 연결된 데이터 테이블을 채우기 위해 여러 쿼리를 포함할 수 있습니다. 각 쿼리가 연결된 데이터 테이블과 동일한 스키마를 준수하는 데이터를 반환하는 한 응용 프로그램에 필요한 만큼 TableAdapter에 대한 쿼리를 정의할 수 있습니다. 이 기능을 사용하면 TableAdapter가 서로 다른 기준에 따라 다른 결과를 로드할 수 있습니다.

예를 들어 응용 프로그램에 고객 이름이 있는 테이블이 포함된 경우 특정 문자로 시작하는 모든 고객 이름과 동일한 상태에 있는 모든 고객으로 테이블을 채우는 쿼리를 만들 수 있습니다. 지정된 상태의 `Customers` 고객으로 테이블을 채우려면 다음과 `FillByState` 같이 상태 값에 대한 매개 변수를 취하는 쿼리를 만들 수 `SELECT * FROM Customers WHERE State = @State`있습니다. `FillByState` 메서드를 호출 하 고 다음과 같은 매개 변수 `CustomerTableAdapter.FillByState("WA")`값에 전달 하 여 쿼리를 실행 합니다.

TableAdapter의 데이터 테이블과 동일한 스키마의 데이터를 반환하는 쿼리를 추가하는 것 외에도 스칼라(단일) 값을 반환하는 쿼리를 추가할 수 있습니다. 예를 들어 고객 수()`SELECT Count(*) From Customers`수를 반환하는 쿼리는 `CustomersTableAdapter,` 반환되는 데이터가 테이블의 스키마를 따르지 않는 경우에도 유효합니다.

## <a name="clearbeforefill-property"></a>클리어전에필 속성

기본적으로 TableAdapter의 데이터 테이블을 채우기 위해 쿼리를 실행할 때마다 기존 데이터가 지워지고 쿼리 결과만 테이블에 로드됩니다. 쿼리에서 반환되는 데이터를 `ClearBeforeFill` 데이터 `false` 테이블의 기존 데이터로 추가하거나 병합할 경우 TableAdapter의 속성을 설정합니다. 데이터를 지우는지 여부에 관계없이 업데이트를 유지하려면 업데이트를 데이터베이스에 명시적으로 다시 보내야 합니다. 따라서 테이블을 채우는 다른 쿼리를 실행하기 전에 테이블에 있는 데이터에 대한 변경 내용을 저장해야 합니다. 자세한 내용은 [TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)를 사용하여 데이터 업데이트를 참조하십시오.

## <a name="tableadapter-inheritance"></a>테이블어댑터 상속

TableAdapters는 구성된 클래스를 캡슐화하여 표준 데이터 어댑터의 기능을 확장합니다. <xref:System.Data.Common.DataAdapter> 기본적으로 TableAdapter는 <xref:System.ComponentModel.Component> 클래스에서 상속되며 <xref:System.Data.Common.DataAdapter> 클래스에 캐스팅할 수 없습니다. 클래스에 TableAdapter를 <xref:System.Data.Common.DataAdapter> 캐스팅하면 <xref:System.InvalidCastException> 오류가 발생합니다. TableAdapter의 기본 클래스를 변경하려면 **데이터 집합 디자이너의** <xref:System.ComponentModel.Component> TableAdapter의 기본 **클래스** 속성에서 파생되는 클래스를 지정할 수 있습니다.

## <a name="tableadapter-methods-and-properties"></a>테이블어댑터 방법 및 속성

TableAdapter 클래스는 .NET 형식이 아닙니다. 즉, 설명서 또는 **개체 브라우저에서**찾을 수 없습니다. 앞에서 설명한 마법사 중 하나를 사용할 때 디자인 타임에 만들어집니다. TableAdapter를 만들 때 할당된 이름은 작업 중인 테이블의 이름을 기반으로 합니다. 예를 들어, 라는 `Orders`데이터베이스의 테이블을 기반으로 TableAdapter를 만들 때 TableAdapter이름이 지정됩니다. `OrdersTableAdapter` TableAdapter의 클래스 이름은 **데이터 집합 디자이너의** **Name** 속성을 사용하여 변경할 수 있습니다.

다음은 TableAdapters의 일반적으로 사용되는 방법 및 속성입니다.

|멤버|Description|
|------------|-----------------|
|`TableAdapter.Fill`|TableAdapter의 관련 데이터 테이블을 TableAdapter `SELECT` 명령의 결과로 채웁니다.|
|`TableAdapter.Update`|변경 내용을 데이터베이스로 다시 보내고 업데이트의 영향을 받는 행 수를 나타내는 정수를 반환합니다. 자세한 내용은 [TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)를 사용하여 데이터 업데이트를 참조하십시오.|
|`TableAdapter.GetData`|데이터로 <xref:System.Data.DataTable> 채워진 새 새 를 반환합니다.|
|`TableAdapter.Insert`|데이터 테이블에 새 행을 만듭니다. 자세한 내용은 [데이터베이스에 새 레코드 삽입을](../data-tools/insert-new-records-into-a-database.md)참조하십시오.|
|`TableAdapter.ClearBeforeFill`|`Fill` 메서드 중 하나를 호출하기 전에 데이터 테이블이 비워지는지 여부를 결정합니다.|

## <a name="tableadapter-update-method"></a>테이블어댑터 업데이트 방법

TableAdapters는 데이터베이스에서 읽고 쓰기 위해 데이터 명령을 사용합니다. TableAdapter의 `Fill` 초기(주) 쿼리를 연관된 데이터 테이블의 스키마와 `InsertCommand` `UpdateCommand` `DeleteCommand` `TableAdapter.Update` 메서드와 연결된 의 . 및 명령을 만드는 기준으로 사용합니다. TableAdapter의 `Update` 메서드를 호출하면 **TableAdapter**쿼리 구성 마법사로 추가한 추가 쿼리 중 하나가 아니라 TableAdapter가 원래 구성되었을 때 만들어진 문을 실행합니다.

TableAdapter를 사용하면 일반적으로 수행하는 명령과 동일한 작업을 효과적으로 수행합니다. 예를 들어 어댑터의 `Fill` 메서드를 호출할 때 어댑터는 해당 `SelectCommand` 속성에서 데이터 명령을 실행하고 <xref:System.Data.SqlClient.SqlDataReader>데이터 판독기(예: 데이터 판독기)를 사용하여 결과 집합을 데이터 테이블에 로드합니다. 마찬가지로 `Update` 어댑터의 메서드를 호출하면 데이터 테이블의 변경된 `UpdateCommand` `InsertCommand`각 `DeleteCommand` 레코드에 대해 해당 명령(의 . 및 속성)을 실행합니다.

> [!NOTE]
> 기본 쿼리에 충분한 정보가 있는 `InsertCommand`경우 `UpdateCommand`의 `DeleteCommand` 및 명령은 TableAdapter가 생성될 때 기본적으로 만들어집니다. TableAdapter의 `SELECT` 기본 쿼리가 단일 테이블 문을 초과하는 경우 디자이너가 및 `InsertCommand` `UpdateCommand` `DeleteCommand`을 생성할 수 없을 수 있습니다. 이러한 명령이 생성되지 않으면 `TableAdapter.Update` 메서드를 실행할 때 오류가 발생할 수 있습니다.

## <a name="tableadapter-generatedbdirectmethods"></a>테이블 어댑터 생성DBDirectMethod

`InsertCommand`은 `UpdateCommand`및 `DeleteCommand`, TableAdapters는 데이터베이스에 대해 직접 실행할 수 있는 메서드를 사용하여 만들어집니다. 이러한 메서드 (,`TableAdapter.Insert` `TableAdapter.Update`및) `TableAdapter.Delete`직접 호출하여 데이터베이스의 데이터를 조작할 수 있습니다. 즉, 연결된 데이터 테이블에 대해 보류 중인 `TableAdapter.Update` 삽입, 업데이트 및 삭제를 처리하기 위해 호출하는 대신 코드에서 이러한 개별 메서드를 호출할 수 있습니다.

이러한 직접 메서드를 만들지 않으려면 TableAdapter의 **GenerateDbDirectMethod** 속성을 `false` **속성** 창에서 설정합니다. TableAdapter에 추가되는 추가 쿼리는 독립 실행형 쿼리입니다.

## <a name="tableadapter-support-for-nullable-types"></a>nullable 형식에 대한 TableAdapter 지원

TableAdapters는 null `Nullable(Of T)` 형식 `T?`및 을 지원합니다. Visual Basic의 nullable 형식에 대한 자세한 내용은 [Nullable 값 형식](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)을 참조하세요. C#의 null 형식에 대한 자세한 내용은 [nullable 형식 사용을](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)참조하십시오.

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>테이블어댑터관리자 참조

기본적으로 TableAdapterManager 클래스는 관련 테이블을 포함하는 데이터 집합을 만들 때 생성됩니다. 클래스가 생성되지 않도록 하려면 데이터 집합의 `Hierarchical Update` 속성 값을 false로 변경합니다. Windows 양식 또는 WPF 페이지의 디자인 표면에 관계가 있는 테이블을 드래그하면 Visual Studio에서 클래스의 멤버 변수를 선언합니다. 데이터 바인딩을 사용하지 않는 경우 변수를 수동으로 선언해야 합니다.

TableAdapterManager 클래스는 .NET 형식이 아닙니다. 따라서 설명서에서 찾을 수 없습니다. 데이터 집합 만들기 프로세스의 일부로 디자인 타임에 만들어집니다.

다음은 클래스에서 자주 사용하는 메서드 `TableAdapterManager` 및 속성입니다.

|멤버|Description|
|------------|-----------------|
|`UpdateAll` 메서드|모든 데이터 테이블의 모든 데이터를 저장합니다.|
|`BackUpDataSetBeforeUpdate` 속성|`TableAdapterManager.UpdateAll` 메서드를 실행하기 전에 데이터 집합의 백업 복사본을 만들지 여부를 결정합니다. 부울.|
|*테이블이름* `TableAdapter` 속성|TableAdapter를 나타냅니다. 생성된 TableAdapterManager에는 관리하는 각 `TableAdapter` 에 대한 속성이 포함되어 있습니다. 예를 들어 고객 및 주문 테이블이 있는 데이터 집합은 `CustomersTableAdapter` `OrdersTableAdapter` 속성을 포함하는 TableAdapterManager를 사용하여 생성합니다.|
|`UpdateOrder` 속성|개별 삽입, 업데이트 및 삭제 명령의 순서를 제어합니다. 열거형의 값 `TableAdapterManager.UpdateOrderOption` 중 하나로 설정합니다.<br /><br /> 기본적으로 는 `UpdateOrder` **InsertUpdateDelete**로 설정됩니다. 즉, 데이터 집합의 모든 테이블에 대해 삽입, 업데이트 및 삭제가 수행됩니다.|

## <a name="security"></a>보안

로 설정된 <xref:System.Data.CommandType.Text>CommandType 속성이 있는 데이터 명령을 사용하는 경우 데이터베이스로 전달하기 전에 클라이언트에서 전송되는 정보를 주의 깊게 확인합니다. 악의적인 사용자가 인증되지 않은 액세스 권한을 얻거나 데이터베이스를 손상시키기 위해 수정되었거나 추가된 SQL 문을 전송(주입)할 수도 있습니다. 사용자 입력을 데이터베이스로 전송하기 전에 항상 정보가 유효한지 확인합니다. 가능한 경우 항상 매개 변수화된 쿼리 또는 저장 프로시저를 사용하는 것이 가장 좋습니다.

## <a name="see-also"></a>참고 항목

- [데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)
