---
title: TableAdapter를 사용하여 데이터베이스에 직접 액세스
description: Insert, Update 및 Delete와 같은 메서드를 사용 하 여 데이터베이스에서 직접 데이터를 조작 하는 TableAdapter를 사용 하 여 데이터베이스에 직접 액세스 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 30248632eacde07cfcc94213aeeb75ecac8dcf70
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215918"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>TableAdapter를 사용하여 데이터베이스에 직접 액세스

, 및 외에 `InsertCommand` 도 `UpdateCommand` `DeleteCommand` tableadapter는 데이터베이스에 대해 직접 실행할 수 있는 메서드를 사용 하 여 생성 됩니다. 이러한 메서드 ( `TableAdapter.Insert` , `TableAdapter.Update` 및 `TableAdapter.Delete` )를 호출 하 여 데이터베이스에서 직접 데이터를 조작할 수 있습니다.

이러한 직접 메서드를 만들지 않으려면 `GenerateDbDirectMethods` `false` **속성** 창에서 TableAdapter의 속성을로 설정 합니다. Tableadapter의 주 쿼리와 함께 TableAdapter에 쿼리를 추가 하는 경우 이러한 메서드를 생성 하지 않는 독립 실행형 쿼리를 사용할 수 있습니다 `DbDirect` .

## <a name="send-commands-directly-to-a-database"></a>데이터베이스에 직접 명령 보내기

`DbDirect`수행 하려는 작업을 수행 하는 TableAdapter 메서드를 호출 합니다.

### <a name="to-insert-new-records-directly-into-a-database"></a>데이터베이스에 새 레코드를 직접 삽입 하려면

- TableAdapter의 메서드를 호출 `Insert` 하 여 각 열에 대 한 값을 매개 변수로 전달 합니다. 다음 절차에서는 `Region` Northwind 데이터베이스의 테이블을 예로 사용 합니다.

    > [!NOTE]
    > 사용할 수 있는 인스턴스가 없는 경우 사용할 TableAdapter를 인스턴스화합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

### <a name="to-update-records-directly-in-a-database"></a>데이터베이스에서 직접 레코드를 업데이트 하려면

- TableAdapter의 메서드를 호출 `Update` 하 여 각 열에 대 한 새 값과 원래 값을 매개 변수로 전달 합니다.

    > [!NOTE]
    > 사용할 수 있는 인스턴스가 없는 경우 사용할 TableAdapter를 인스턴스화합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet18":::

### <a name="to-delete-records-directly-from-a-database"></a>데이터베이스에서 직접 레코드를 삭제 하려면

- TableAdapter의 메서드를 호출 `Delete` 하 여 각 열에 대 한 값을 메서드의 매개 변수로 전달 `Delete` 합니다. 다음 절차에서는 `Region` Northwind 데이터베이스의 테이블을 예로 사용 합니다.

    > [!NOTE]
    > 사용할 수 있는 인스턴스가 없는 경우 사용할 TableAdapter를 인스턴스화합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet21":::

## <a name="see-also"></a>참고 항목

- [TableAdapters를 사용하여 데이터 세트 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)
