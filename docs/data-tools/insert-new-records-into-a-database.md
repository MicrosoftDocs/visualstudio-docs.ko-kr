---
title: 데이터베이스에 새 레코드 삽입
description: Tableadapter의 DBDirect 메서드 또는 명령 개체 중 하나인 TableAdapter. Update 메서드를 사용 하 여 데이터베이스에 새 레코드를 삽입 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3586cf45e152cd8a0149140556916b11544a00bb
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436278"
---
# <a name="insert-new-records-into-a-database"></a>데이터베이스에 새 레코드 삽입

데이터베이스에 새 레코드를 삽입 하려면 `TableAdapter.Update` 메서드 또는 TableAdapter의 DBDirect 메서드 중 하나 (특히 메서드)를 사용할 수 있습니다 `TableAdapter.Insert` . 자세한 내용은 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)를 참조 하세요.

응용 프로그램에서 Tableadapter를 사용 하지 않는 경우 명령 개체 (예:)를 사용  <xref:System.Data.SqlClient.SqlCommand> 하 여 데이터베이스에 새 레코드를 삽입할 수 있습니다.

응용 프로그램에서 데이터 집합을 사용 하 여 데이터를 저장 하는 경우 메서드를 사용 `TableAdapter.Update` 합니다. `Update`메서드는 데이터베이스에 모든 변경 내용 (업데이트, 삽입 및 삭제)을 보냅니다.

응용 프로그램에서 개체를 사용 하 여 데이터를 저장 하는 경우 또는 데이터베이스에 새 레코드를 만드는 방법을 보다 세밀 하 게 제어 하려면 메서드를 사용 `TableAdapter.Insert` 합니다.

TableAdapter에 메서드가 없는 경우에는 `Insert` tableadapter가 저장 프로시저를 사용 하도록 구성 되어 있거나 `GenerateDBDirectMethods` 속성이로 설정 되어 있음을 의미 합니다 `false` . `GenerateDBDirectMethods`데이터 세트 디자이너 내에서 TableAdapter의 속성을로 설정 하 `true` 고 데이터 집합을 저장 합니다. **Dataset Designer** 이렇게 하면 TableAdapter가 다시 생성 됩니다. TableAdapter에 아직 메서드가 없는 경우 `Insert` 테이블은 개별 행을 구분 하는 데 충분 한 스키마 정보를 제공 하지 않을 수 있습니다. 예를 들어 테이블에 기본 키 집합이 없을 수 있습니다.

## <a name="insert-new-records-by-using-tableadapters"></a>Tableadapter를 사용 하 여 새 레코드 삽입

Tableadapter는 응용 프로그램의 요구 사항에 따라 데이터베이스에 새 레코드를 삽입 하는 다양 한 방법을 제공 합니다.

응용 프로그램에서 데이터 집합을 사용 하 여 데이터를 저장 하는 경우 데이터 집합의 원하는에 새 레코드를 추가한 <xref:System.Data.DataTable> 다음 메서드를 호출할 수 있습니다 `TableAdapter.Update` . `TableAdapter.Update`메서드는 <xref:System.Data.DataTable> 수정 및 삭제 된 레코드를 포함 하 여의 변경 내용을 데이터베이스에 전송 합니다.

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter. Update 메서드를 사용 하 여 데이터베이스에 새 레코드를 삽입 하려면

1. <xref:System.Data.DataTable>새를 만들어 컬렉션에 추가 하 여 원하는에 새 레코드를 추가 <xref:System.Data.DataRow> <xref:System.Data.DataTable.Rows%2A> 합니다.

2. 에 새 행이 추가 된 후에는 <xref:System.Data.DataTable> 메서드를 호출 `TableAdapter.Update` 합니다. 전체 <xref:System.Data.DataSet> , a <xref:System.Data.DataTable> ,의 배열 <xref:System.Data.DataRow> 또는 단일를 전달 하 여 업데이트할 데이터의 양을 제어할 수 있습니다 <xref:System.Data.DataRow> .

   다음 코드에서는에 새 레코드를 추가한 <xref:System.Data.DataTable> 다음 메서드를 호출 하 여 `TableAdapter.Update` 새 행을 데이터베이스에 저장 하는 방법을 보여 줍니다. 이 예에서는 `Region` Northwind 데이터베이스의 테이블을 사용 합니다.

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter. Insert 메서드를 사용 하 여 데이터베이스에 새 레코드를 삽입 하려면

응용 프로그램에서 개체를 사용 하 여 데이터를 저장 하는 경우 메서드를 사용 `TableAdapter.Insert` 하 여 데이터베이스에 새 행을 직접 만들 수 있습니다. `Insert`메서드는 각 열에 대 한 개별 값을 매개 변수로 받아들입니다. 메서드를 호출 하면 전달 된 매개 변수 값을 사용 하 여 데이터베이스에 새 레코드가 삽입 됩니다.

- TableAdapter의 메서드를 호출 `Insert` 하 여 각 열에 대 한 값을 매개 변수로 전달 합니다.

다음 절차에서는 메서드를 사용 하 여 행을 삽입 하는 방법을 보여 줍니다 `TableAdapter.Insert` . 이 예에서는 `Region` Northwind 데이터베이스의 테이블에 데이터를 삽입 합니다.

> [!NOTE]
> 사용할 수 있는 인스턴스가 없는 경우 사용할 TableAdapter를 인스턴스화합니다.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>명령 개체를 사용 하 여 새 레코드 삽입

명령 개체를 사용 하 여 새 레코드를 데이터베이스에 직접 삽입할 수 있습니다.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>명령 개체를 사용 하 여 데이터베이스에 새 레코드를 삽입 하려면

- 새 명령 개체를 만든 다음 `Connection` , 및 속성을 설정 `CommandType` `CommandText` 합니다.

다음 예에서는 명령 개체를 사용 하 여 데이터베이스에 레코드를 삽입 하는 방법을 보여 줍니다. `Region`Northwind 데이터베이스의 테이블에 데이터를 삽입 합니다.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>.NET 보안

연결 하려는 데이터베이스에 대 한 액세스 권한과 원하는 테이블에 대 한 삽입을 수행할 수 있는 권한이 있어야 합니다.

## <a name="see-also"></a>참조

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
