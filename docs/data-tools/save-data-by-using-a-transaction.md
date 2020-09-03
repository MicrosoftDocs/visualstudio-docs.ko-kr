---
title: '방법: 트랜잭션을 사용하여 데이터 저장'
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 40894adefb42d6de077a2e2812d26f90bc5f40dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281697"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>방법: 트랜잭션을 사용하여 데이터 저장

네임 스페이스를 사용 하 여 트랜잭션에 데이터를 저장 <xref:System.Transactions> 합니다. 개체를 사용 <xref:System.Transactions.TransactionScope> 하 여 자동으로 관리 되는 트랜잭션에 참여 합니다.

프로젝트는 *System. 트랜잭션* 어셈블리에 대 한 참조를 사용 하 여 만들어지지 않으므로 트랜잭션을 사용 하는 프로젝트에 대 한 참조를 수동으로 추가 해야 합니다.

트랜잭션을 구현 하는 가장 쉬운 방법은 문에서 개체를 인스턴스화하는 것입니다 <xref:System.Transactions.TransactionScope> `using` . 자세한 내용은 [using 문](/dotnet/visual-basic/language-reference/statements/using-statement)및 [using 문](/dotnet/csharp/language-reference/keywords/using-statement)을 참조 하세요. 문 내에서 실행 되는 코드는 `using` 트랜잭션에 참여 합니다.

트랜잭션을 커밋하려면 <xref:System.Transactions.TransactionScope.Complete%2A> using 블록의 마지막 문으로 메서드를 호출 합니다.

트랜잭션을 롤백하려면 메서드를 호출 하기 전에 예외를 throw <xref:System.Transactions.TransactionScope.Complete%2A> 합니다.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>System.Transactions.dll에 대 한 참조를 추가 하려면

1. **프로젝트** 메뉴에서 **참조 추가**를 선택합니다.

2. **.Net** 탭 (SQL Server 프로젝트에 대 한**SQL Server** 탭)에서 **시스템 트랜잭션을**선택한 다음 **확인**을 선택 합니다.

     *System.Transactions.dll* 에 대 한 참조가 프로젝트에 추가 됩니다.

## <a name="to-save-data-in-a-transaction"></a>트랜잭션에 데이터를 저장 하려면

- 트랜잭션을 포함 하는 using 문 내에 데이터를 저장 하는 코드를 추가 합니다. 다음 코드에서는 using 문에서 개체를 만들고 인스턴스화하는 방법을 보여 줍니다 <xref:System.Transactions.TransactionScope> .

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>참조

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
- [연습: 트랜잭션에 데이터 저장](../data-tools/save-data-in-a-transaction.md)
