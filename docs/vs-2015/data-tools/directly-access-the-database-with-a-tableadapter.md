---
title: TableAdapter를 사용 하 여 데이터베이스에 직접 액세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657369"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>TableAdapter를 사용하여 데이터베이스에 직접 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

, 및 외에 `InsertCommand` 도 `UpdateCommand` `DeleteCommand` tableadapter는 데이터베이스에 대해 직접 실행할 수 있는 메서드를 사용 하 여 생성 됩니다. 이러한 메서드 ( `TableAdapter.Insert` , `TableAdapter.Update` 및 `TableAdapter.Delete` )를 호출 하 여 데이터베이스에서 직접 데이터를 조작할 수 있습니다.

 이러한 직접 메서드를 만들지 않으려면 `GenerateDbDirectMethods` `false` **속성** 창에서 TableAdapter의 속성을로 설정 합니다. Tableadapter의 주 쿼리와 함께 TableAdapter에 쿼리를 추가 하는 경우 이러한 쿼리는 이러한 DbDirect 메서드를 생성 하지 않는 독립 실행형 쿼리입니다.

## <a name="sendcommandsdirectly-to-a-database"></a>데이터베이스에 Sendcommandsdirectly
 수행 하려는 작업을 수행 하는 TableAdapter DbDirect 메서드를 호출 합니다.

#### <a name="to-insert-new-records-directly-into-a-database"></a>데이터베이스에 새 레코드를 직접 삽입 하려면

- TableAdapter의 메서드를 호출 `Insert` 하 여 각 열에 대 한 값을 매개 변수로 전달 합니다. 다음 절차에서는 `Region` Northwind databaseas 테이블을 예로 사용 합니다.

    > [!NOTE]
    > 사용할 수 있는 인스턴스가 없는 경우 사용할 TableAdapter를 인스턴스화합니다.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>데이터베이스에서 직접 레코드를 업데이트 하려면

- TableAdapter의 메서드를 호출 `Update` 하 여 각 열에 대 한 새 값과 원래 값을 매개 변수로 전달 합니다.

    > [!NOTE]
    > 사용할 수 있는 인스턴스가 없는 경우 사용할 TableAdapter를 인스턴스화합니다.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>데이터베이스에서 직접 레코드를 삭제 하려면

- TableAdapter의 메서드를 호출 `Delete` 하 여 각 열에 대 한 값을 메서드의 매개 변수로 전달 `Delete` 합니다. 다음 절차에서는 `Region` Northwind databaseas 테이블을 예로 사용 합니다.

    > [!NOTE]
    > 사용할 수 있는 인스턴스가 없는 경우 사용할 TableAdapter를 인스턴스화합니다.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>관련 항목
 [TableAdapters를 사용하여 데이터 세트 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)
