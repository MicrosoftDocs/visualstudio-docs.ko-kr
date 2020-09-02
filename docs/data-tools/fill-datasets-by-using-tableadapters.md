---
title: TableAdapters를 사용하여 데이터 세트 채우기
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 888e2ac47348d7e61d115f51e3ea52d15ea9f447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282438"
---
# <a name="fill-datasets-by-using-tableadapters"></a>TableAdapters를 사용하여 데이터 세트 채우기

TableAdapter 구성 요소는 지정 된 하나 이상의 쿼리나 저장 프로시저를 기반으로 데이터베이스의 데이터로 데이터 집합을 채웁니다. Tableadapter는 데이터베이스에서 추가, 업데이트 및 삭제를 수행 하 여 데이터 집합에 대 한 변경 내용을 유지할 수도 있습니다. 특정 테이블과 관련이 없는 전역 명령을 실행할 수도 있습니다.

> [!NOTE]
> Tableadapter는 Visual Studio 디자이너에서 생성 됩니다. 프로그래밍 방식으로 데이터 집합을 만드는 경우 .NET 클래스인 DataAdapter를 사용 합니다.

TableAdapter 작업에 대 한 자세한 내용은 다음 항목 중 하나를 직접 건너뛸 수 있습니다.

|항목|설명|
|-----------|-----------------|
|[TableAdapter 만들기 및 구성](../data-tools/create-and-configure-tableadapters.md)|디자이너를 사용 하 여 Tableadapter를 만들고 구성 하는 방법|
|[매개 변수가 있는 TableAdapter 쿼리 만들기](../data-tools/create-parameterized-tableadapter-queries.md)|사용자가 TableAdapter 프로시저 또는 쿼리에 인수를 제공할 수 있게 하는 방법|
|[TableAdapter를 사용하여 데이터베이스에 직접 액세스](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Tableadapter의 Dbdirect 메서드를 사용 하는 방법|
|[데이터 세트를 채우는 동안 제약 조건 해제](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|데이터를 업데이트할 때 외래 키 제약 조건으로 작업 하는 방법|
|[TableAdapter의 기능 확장 방법](../data-tools/fill-datasets-by-using-tableadapters.md)|Tableadapter에 사용자 지정 코드를 추가 하는 방법|
|[XML 데이터를 데이터 세트에 읽어오기](../data-tools/read-xml-data-into-a-dataset.md)|XML로 작업 하는 방법|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter 개요

Tableadapter는 데이터베이스에 연결 하 고, 쿼리 또는 저장 프로시저를 실행 하 고, DataTable을 반환 된 데이터로 채우는 디자이너 생성 구성 요소입니다. Tableadapter는 또한 응용 프로그램에서 업데이트 된 데이터를 다시 데이터베이스로 보냅니다. TableAdapter가 연결 된 테이블의 스키마를 준수 하는 데이터를 반환 하는 한 TableAdapter에서 원하는 수 만큼 쿼리를 실행할 수 있습니다. 다음 다이어그램에서는 Tableadapter가 메모리의 데이터베이스 및 기타 개체와 상호 작용 하는 방법을 보여 줍니다.

![클라이언트 애플리케이션의 데이터 흐름](../data-tools/media/clientdatadiagram.gif)

Tableadapter는 **데이터 세트 디자이너**를 사용 하 여 디자인 되었지만 tableadapter 클래스는의 중첩 클래스로 생성 되지 않습니다  <xref:System.Data.DataSet> . 각 데이터 집합에 특정 한 별도의 네임 스페이스에 있습니다. 예를 들어 라는 데이터 집합이 있는 경우의 `NorthwindDataSet` 에 연결 된 tableadapter는  <xref:System.Data.DataTable> `NorthwindDataSet` `NorthwindDataSetTableAdapters` 네임 스페이스에 있습니다. 특정 TableAdapter를 프로그래밍 방식으로 액세스 하려면 TableAdapter의 새 인스턴스를 선언 해야 합니다. 예를 들면 다음과 같습니다.

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>연결 된 DataTable 스키마

TableAdapter를 만들 때 초기 쿼리 또는 저장 프로시저를 사용 하 여 연결 된 TableAdapter의 스키마를 정의 합니다 <xref:System.Data.DataTable> . Tableadapter의 메서드를 호출 하 여이 초기 쿼리 또는 저장 프로시저를 실행 `Fill` 합니다 .이는 tableadapter의 연결 된를 채웁니다 <xref:System.Data.DataTable> . TableAdapter의 주 쿼리에 적용 되는 모든 변경 내용은 연결 된 데이터 테이블의 스키마에 반영 됩니다. 예를 들어 주 쿼리에서 열을 제거 하면 연결 된 데이터 테이블 에서도 해당 열이 제거 됩니다. TableAdapter의 추가 쿼리에서 주 쿼리에 없는 열을 반환 하는 SQL 문을 사용 하는 경우 디자이너는 주 쿼리와 추가 쿼리 간의 열 변경 내용을 동기화 하려고 합니다.

## <a name="tableadapter-update-commands"></a>TableAdapter update 명령

TableAdapter의 업데이트 기능은 **Tableadapter 마법사**의 주 쿼리에서 사용할 수 있는 정보의 양에 따라 달라 집니다. 예를 들어를 사용 하 여 여러 테이블에서 값을 인출 하도록 구성 된 Tableadapter, `JOIN` 스칼라 값, 뷰 또는 집계 함수의 결과는 처음에 업데이트를 기본 데이터베이스로 다시 보내는 기능을 사용 하 여 생성 되지 않습니다. 그러나 `INSERT` `UPDATE` `DELETE` **속성** 창에서, 및 명령을 수동으로 구성할 수 있습니다.

## <a name="tableadapter-queries"></a>TableAdapter 쿼리

![쿼리가 여러 개 포함된 TableAdapter](../data-tools/media/tableadapter.gif)

Tableadapter는 여러 개의 쿼리를 포함 하 여 연결 된 데이터 테이블을 채울 수 있습니다. 각 쿼리가 연결 된 데이터 테이블과 동일한 스키마를 준수 하는 데이터를 반환 하는 한, 응용 프로그램에 필요한 만큼 TableAdapter에 대해 쿼리를 정의할 수 있습니다. 이 기능을 통해 TableAdapter는 서로 다른 조건을 기반으로 다른 결과를 로드할 수 있습니다.

예를 들어 응용 프로그램에 고객 이름이 있는 테이블이 포함 되어 있는 경우 특정 문자로 시작 하는 모든 고객 이름으로 테이블을 채우고 동일한 상태에 있는 모든 고객으로 테이블을 채우는 쿼리를 만들 수 있습니다. `Customers`테이블을 지정 된 상태의 고객으로 채우려면 `FillByState` 다음과 같이 상태 값에 대 한 매개 변수를 사용 하는 쿼리를 만들 수 있습니다 `SELECT * FROM Customers WHERE State = @State` . 메서드를 호출 하 `FillByState` 고 다음과 같이 매개 변수 값을 전달 하 여 쿼리를 실행 `CustomerTableAdapter.FillByState("WA")` 합니다.

TableAdapter의 데이터 테이블과 동일한 스키마의 데이터를 반환 하는 쿼리를 추가 하는 것 외에 스칼라 (단일) 값을 반환 하는 쿼리를 추가할 수 있습니다. 예를 들어, 반환 되는 `SELECT Count(*) From Customers` `CustomersTableAdapter,` 데이터가 테이블의 스키마를 따르지 않더라도 고객 수 ()를 반환 하는 쿼리는에 유효 합니다.

## <a name="clearbeforefill-property"></a>ClearBeforeFill 속성

기본적으로 TableAdapter의 데이터 테이블을 채우기 위해 쿼리를 실행할 때마다 기존 데이터가 지워지고 쿼리 결과만 테이블에 로드 됩니다. `ClearBeforeFill` `false` 쿼리에서 반환 되는 데이터를 데이터 테이블의 기존 데이터에 추가 하거나 병합 하려면 TableAdapter의 속성을로 설정 합니다. 데이터를 지울지 여부와 관계 없이 데이터베이스에 업데이트를 저장 하려면 데이터베이스에 명시적으로 업데이트를 다시 전송 해야 합니다. 따라서 테이블을 채우는 다른 쿼리를 실행 하기 전에 테이블의 데이터에 대 한 변경 내용을 저장 해야 합니다. 자세한 내용은 [TableAdapter를 사용 하 여 데이터 업데이트](../data-tools/update-data-by-using-a-tableadapter.md)를 참조 하세요.

## <a name="tableadapter-inheritance"></a>TableAdapter 상속

Tableadapter는 구성 된 클래스를 캡슐화 하 여 표준 데이터 어댑터의 기능을 확장 합니다 <xref:System.Data.Common.DataAdapter> . 기본적으로 TableAdapter는 클래스에서 상속 <xref:System.ComponentModel.Component> 되며 클래스로 캐스팅할 수 없습니다 <xref:System.Data.Common.DataAdapter> . TableAdapter를 클래스로 캐스팅 하면 <xref:System.Data.Common.DataAdapter> <xref:System.InvalidCastException> 오류가 발생 합니다. TableAdapter의 기본 클래스를 변경 하려면 <xref:System.ComponentModel.Component> **데이터 세트 디자이너**Tableadapter의 **기본 클래스** 속성에서 파생 되는 클래스를 지정할 수 있습니다.

## <a name="tableadapter-methods-and-properties"></a>TableAdapter 메서드 및 속성

TableAdapter 클래스는 .NET 형식이 아닙니다. 즉, 설명서 나 **개체 브라우저**에서 볼 수 없습니다. 앞에서 언급 한 마법사 중 하나를 사용 하는 경우 디자인 타임에 만들어집니다. TableAdapter를 만들 때 TableAdapter에 할당 되는 이름은 작업 중인 테이블의 이름을 기준으로 합니다. 예를 들어 라는 데이터베이스의 테이블을 기반으로 TableAdapter를 만들 경우 `Orders` tableadapter의 이름은 `OrdersTableAdapter` 입니다. TableAdapter의 클래스 이름은 **데이터 세트 디자이너**의 **name** 속성을 사용 하 여 변경할 수 있습니다.

Tableadapter의 일반적으로 사용 되는 메서드와 속성은 다음과 같습니다.

|멤버|설명|
|------------|-----------------|
|`TableAdapter.Fill`|Tableadapter의 연결 된 데이터 테이블을 TableAdapter 명령의 결과로 채웁니다 `SELECT` .|
|`TableAdapter.Update`|변경 내용을 데이터베이스에 다시 보내고 업데이트의 영향을 받는 행 수를 나타내는 정수를 반환 합니다. 자세한 내용은 [TableAdapter를 사용 하 여 데이터 업데이트](../data-tools/update-data-by-using-a-tableadapter.md)를 참조 하세요.|
|`TableAdapter.GetData`|데이터로 채워진 새을 반환 합니다 <xref:System.Data.DataTable> .|
|`TableAdapter.Insert`|데이터 테이블에 새 행을 만듭니다. 자세한 내용은 [데이터베이스에 새 레코드 삽입](../data-tools/insert-new-records-into-a-database.md)을 참조 하세요.|
|`TableAdapter.ClearBeforeFill`|메서드 중 하나를 호출 하기 전에 데이터 테이블이 비어 있는지 여부를 확인 `Fill` 합니다.|

## <a name="tableadapter-update-method"></a>TableAdapter update 메서드

Tableadapter는 데이터 명령을 사용 하 여 데이터베이스에 대 한 읽기 및 쓰기를 합니다. TableAdapter의 초기 `Fill` (주) 쿼리를 연결 된 데이터 테이블의 스키마를 만드는 기준으로 사용 하 고 `InsertCommand` `UpdateCommand` 메서드와 연결 된, 및 명령을 사용 합니다 `DeleteCommand` `TableAdapter.Update` . Tableadapter의 메서드를 호출 하면 tableadapter `Update` **쿼리 구성 마법사**를 사용 하 여 추가한 추가 쿼리 중 하나가 아니라 tableadapter를 원래 구성할 때 생성 된 문이 실행 됩니다.

TableAdapter를 사용 하는 경우 일반적으로 수행 하는 명령을 사용 하 여 동일한 작업을 효율적으로 수행 합니다. 예를 들어 어댑터의 메서드를 호출 하 `Fill` 는 경우 어댑터는 해당 속성에서 data 명령을 실행 하 `SelectCommand` 고 데이터 판독기 (예:)를 사용 <xref:System.Data.SqlClient.SqlDataReader> 하 여 결과 집합을 데이터 테이블로 로드 합니다. 마찬가지로 어댑터의 메서드를 호출 하는 경우 `Update` `UpdateCommand` `InsertCommand` `DeleteCommand` 데이터 테이블에서 변경 된 각 레코드에 대해, 및 속성에서 적절 한 명령을 실행 합니다.

> [!NOTE]
> 주 쿼리에 충분 한 정보가 있으면 `InsertCommand` `UpdateCommand` `DeleteCommand` TableAdapter가 생성 될 때 기본적으로, 및 명령이 생성 됩니다. TableAdapter의 주 쿼리가 단일 테이블 문 보다 많은 경우 `SELECT` 디자이너에서, 및를 생성할 수 없습니다 `InsertCommand` `UpdateCommand` `DeleteCommand` . 이러한 명령이 생성 되지 않으면 메서드를 실행할 때 오류가 발생할 수 있습니다 `TableAdapter.Update` .

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

, 및 외에도 `InsertCommand` `UpdateCommand` `DeleteCommand` tableadapter는 데이터베이스에 대해 직접 실행할 수 있는 메서드를 사용 하 여 생성 됩니다. 이러한 메서드 ( `TableAdapter.Insert` , `TableAdapter.Update` 및 `TableAdapter.Delete` )를 직접 호출 하 여 데이터베이스의 데이터를 조작할 수 있습니다. 즉 `TableAdapter.Update` , 연결 된 데이터 테이블에 대해 보류 중인 삽입, 업데이트 및 삭제를 처리 하기 위해를 호출 하는 대신 코드에서 이러한 개별 메서드를 호출할 수 있습니다.

이러한 직접 메서드를 만들지 않으려면 속성 창에서 TableAdapter의 **Generatedbdirectmethods** 속성을로 설정 `false` 합니다. **Properties** TableAdapter에 추가 되는 추가 쿼리는 독립 실행형 쿼리 이므로 이러한 메서드를 생성 하지 않습니다.

## <a name="tableadapter-support-for-nullable-types"></a>Nullable 형식에 대 한 TableAdapter 지원

Tableadapter는 nullable 형식 `Nullable(Of T)` 및을 지원 `T?` 합니다. Visual Basic의 nullable 형식에 대한 자세한 내용은 [Nullable 값 형식](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)을 참조하세요. C #의 nullable 형식에 대 한 자세한 내용은 [nullable 형식 사용](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)을 참조 하세요.

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager 참조

기본적으로 TableAdapterManager 클래스는 관련 테이블을 포함 하는 데이터 집합을 만들 때 생성 됩니다. 클래스가 생성 되지 않도록 하려면 `Hierarchical Update` 데이터 집합의 속성 값을 false로 변경 합니다. 관계가 있는 테이블을 Windows Form 또는 WPF 페이지의 디자인 화면으로 끌어 오면 Visual Studio에서 클래스의 멤버 변수를 선언 합니다. 데이터 바인딩을 사용 하지 않는 경우 변수를 수동으로 선언 해야 합니다.

TableAdapterManager 클래스는 .NET 형식이 아닙니다. 따라서 설명서에서 확인할 수 없습니다. 디자인 타임에 데이터 집합 생성 프로세스의 일부로 만들어집니다.

다음은 클래스의 자주 사용 되는 메서드와 속성입니다 `TableAdapterManager` .

|멤버|설명|
|------------|-----------------|
|`UpdateAll` 메서드|모든 데이터 테이블의 모든 데이터를 저장 합니다.|
|`BackUpDataSetBeforeUpdate` 속성|메서드를 실행 하기 전에 데이터 집합의 백업 복사본을 만들지 여부를 결정 합니다 `TableAdapterManager.UpdateAll` . 부울.|
|*tableName* `TableAdapter` 속성|TableAdapter를 나타냅니다. 생성 된 TableAdapterManager는 관리 하는 각 it에 대 한 속성을 포함 합니다 `TableAdapter` . 예를 들어 Customers 및 Orders 테이블이 포함 된 데이터 집합은 및 속성을 포함 하는 TableAdapterManager를 사용 하 여 생성 `CustomersTableAdapter` `OrdersTableAdapter` 됩니다.|
|`UpdateOrder` 속성|개별 insert, update 및 delete 명령의 순서를 제어 합니다. 열거형의 값 중 하나로 설정 `TableAdapterManager.UpdateOrderOption` 합니다.<br /><br /> 기본적으로은 `UpdateOrder` **Insertupdatedelete**로 설정 됩니다. 즉, 데이터 집합의 모든 테이블에 대 한 삽입, 업데이트 및 삭제 작업이 수행 됩니다.|

## <a name="security"></a>보안

CommandType 속성이로 설정 된 데이터 명령을 사용 하는 경우 <xref:System.Data.CommandType.Text> 클라이언트에서 전송 된 정보를 데이터베이스에 전달 하기 전에 신중 하 게 확인 합니다. 악의적인 사용자가 인증되지 않은 액세스 권한을 얻거나 데이터베이스를 손상시키기 위해 수정되었거나 추가된 SQL 문을 전송(주입)할 수도 있습니다. 사용자 입력을 데이터베이스로 전송 하기 전에 항상 정보가 유효한 지 확인 하십시오. 가능 하면 매개 변수가 있는 쿼리나 저장 프로시저를 항상 사용 하는 것이 가장 좋습니다.

## <a name="see-also"></a>추가 정보

- [데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)
