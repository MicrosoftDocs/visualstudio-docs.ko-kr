---
title: TableAdapter를 사용 하 여 데이터 업데이트 | Microsoft Docs
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 312bf75100d2b9b270b45776c5f7ded21ab6ac52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602329"
---
# <a name="update-data-by-using-a-tableadapter"></a>TableAdapter를 사용하여 데이터 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 집합의 데이터를 수정 하 고 유효성을 검사 한 후에 `Update` 는 TableAdapter의 메서드를 호출 하 여 업데이트 된 데이터를 데이터베이스에 다시 보낼 수 있습니다. `Update`메서드는 단일 데이터 테이블을 업데이트 하 고 <xref:System.Data.DataRow.RowState%2A> 테이블의 각 데이터 행에 따라 올바른 명령 (INSERT, UPDATE 또는 DELETE)을 실행 합니다. 데이터 집합에 관련 테이블이 있으면 Visual Studio에서 업데이트를 수행 하는 데 사용 하는 TableAdapterManager 클래스를 생성 합니다. TableAdapterManager 클래스를 사용 하면 데이터베이스에 정의 된 외래 키 제약 조건을 기반으로 올바른 순서로 업데이트가 수행 됩니다. 데이터 바인딩된 컨트롤을 사용 하는 경우 데이터 바인딩 아키텍처는 tableAdapterManager 클래스의 멤버 변수를 만듭니다. 자세한 내용은 [계층적 업데이트 개요](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)를 참조 하세요.

> [!NOTE]
> 데이터 집합의 내용을 사용 하 여 데이터 소스를 업데이트 하려고 하면 오류가 발생할 수 있습니다. 오류를 방지 하려면 어댑터의 메서드를 호출 하는 코드를 블록 내에 thatyou 하는 것이 좋습니다 `Update` `try` / `catch` .

 데이터 원본을 업데이트 하는 정확한 방법은 비즈니스 요구 사항에 따라 다를 수 있지만 다음 단계를 포함 합니다.

1. 블록에서 어댑터의 `Update` 메서드를 호출 `try` / `catch` 합니다.

2. 예외가 catch 되 면 오류가 발생 한 데이터 행을 찾습니다. 자세한 내용은 [방법: 오류가 있는 행 찾기](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c)를 참조 하세요.

3. 데이터 행의 문제를 조정 하려면 (가능 하면 프로그래밍 방식으로 또는 사용자에 게 잘못 된 행을 표시 하 여 수정할 수 있음) 업데이트를 다시 시도 <xref:System.Data.DataRow.HasErrors%2A> 합니다 (, <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="savedata-to-a-database"></a>데이터베이스에 대 한 savedata
 `Update`TableAdapter의 메서드를 호출 합니다. 데이터베이스에 쓸 값을 포함 하는 데이터 테이블의 이름을 전달 합니다.

#### <a name="to-update-a-database-by-using-a-tableadapter"></a>TableAdapter를 사용 하 여 데이터베이스를 업데이트 하려면

- TableAdapter의 메서드를 `Update` 블록으로 묶습니다 `try` / `catch` . 다음 예에서는 `Customers` 블록 내에서의 테이블 내용을 업데이트 하는 방법을 보여 줍니다 `NorthwindDataSet` `try` / `catch` .

     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]

## <a name="see-also"></a>관련 항목
 [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
