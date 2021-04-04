---
title: 개체에서 데이터베이스로 데이터 저장
description: Visual Studio의 데이터 집합 도구를 사용 하 여 개체의 데이터를 데이터베이스에 저장 합니다. 새 레코드를 저장 하 고, 기존 레코드를 업데이트 하 고, 기존 레코드를 삭제 하는 방법을 참조 하세요.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 50debf24fa691ba74d082543b1c0bb1a27b5786e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215788"
---
# <a name="save-data-from-an-object-to-a-database"></a>개체에서 데이터베이스로 데이터 저장

개체의 값을 TableAdapter의 DBDirect 메서드 중 하나 (예:)로 전달 하 여 개체의 데이터를 데이터베이스에 저장할 수 있습니다 `TableAdapter.Insert` . 자세한 내용은 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)를 참조 하세요.

개체 컬렉션의 데이터를 저장 하려면 개체의 컬렉션을 반복 하 고 (예: for next loop) TableAdapter의 메서드 중 하나를 사용 하 여 각 개체의 값을 데이터베이스로 보냅니다 `DBDirect` .

기본적으로 `DBDirect` 메서드는 데이터베이스에 대해 직접 실행할 수 있는 TableAdapter에 생성 됩니다. 이러한 메서드는 직접 호출할 수 있으며 <xref:System.Data.DataSet> 또는 <xref:System.Data.DataTable> 개체가 데이터베이스에 업데이트를 전송 하기 위해 변경 내용을 조정 하는 데 필요 하지 않습니다.

> [!NOTE]
> TableAdapter를 구성 하는 경우 주 쿼리는 생성 되는 메서드에 대 한 충분 한 정보를 제공 해야 합니다 `DBDirect` . 예를 들어 기본 키 열이 정의 되지 않은 테이블의 데이터를 쿼리하도록 TableAdapter가 구성 된 경우에는 메서드를 생성 하지 않습니다 `DBDirect` .

|TableAdapter DBDirect 메서드|Description|
| - |-----------------|
|`TableAdapter.Insert`|데이터베이스에 새 레코드를 추가 하 고 개별 열 값을 메서드 매개 변수로 전달할 수 있도록 합니다.|
|`TableAdapter.Update`|데이터베이스의 기존 레코드를 업데이트 합니다. `Update`메서드는 원래 열 값과 새 열 값을 메서드 매개 변수로 사용 합니다. 원래 값을 사용 하 여 원래 레코드를 찾은 다음 새 값을 사용 하 여 해당 레코드를 업데이트 합니다.<br /><br /> `TableAdapter.Update`메서드는 <xref:System.Data.DataSet> ,, <xref:System.Data.DataTable> <xref:System.Data.DataRow> 또는의 배열을 <xref:System.Data.DataRow> 메서드 매개 변수로 사용 하 여 데이터 집합의 변경 내용을 데이터베이스에 다시 조정 하는 데도 사용 됩니다.|
|`TableAdapter.Delete`|메서드 매개 변수로 전달 된 원래 열 값을 기준으로 데이터베이스에서 기존 레코드를 삭제 합니다.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>개체의 새 레코드를 데이터베이스에 저장 하려면

- 값을 메서드에 전달 하 여 레코드를 만듭니다 `TableAdapter.Insert` .

     다음 예에서는 `Customers` 개체의 값을 메서드에 전달 하 여 테이블에 새 고객 레코드를 만듭니다 `currentCustomer` `TableAdapter.Insert` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>개체의 기존 레코드를 데이터베이스로 업데이트 하려면

- 메서드를 호출 하 고 `TableAdapter.Update` 새 값을 전달 하 여 레코드를 업데이트 하 고 원래 값을 전달 하 여 레코드를 찾는 방법으로 레코드를 수정 합니다.

    > [!NOTE]
    > 개체는 메서드에 전달 하기 위해 원래 값을 유지 해야 합니다 `Update` . 이 예제에서는 접두사를 사용 하 여 `orig` 원래 값을 저장 하는 속성을 사용 합니다.

     다음 예에서는 `Customers` 개체의 새 값과 원래 값을 메서드에 전달 하 여 테이블의 기존 레코드를 업데이트 합니다 `Customer` `TableAdapter.Update` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet24":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet24":::

## <a name="to-delete-existing-records-from-a-database"></a>데이터베이스에서 기존 레코드를 삭제 하려면

- 메서드를 호출 하 고 원래 값을 전달 하 여 레코드를 찾는 방법으로 레코드를 삭제 `TableAdapter.Delete` 합니다.

    > [!NOTE]
    > 개체는 메서드에 전달 하기 위해 원래 값을 유지 해야 합니다 `Delete` . 이 예제에서는 접두사를 사용 하 여 `orig` 원래 값을 저장 하는 속성을 사용 합니다.

     다음 예에서는 `Customers` 개체의 원래 값을 메서드에 전달 하 여 테이블에서 레코드를 삭제 합니다 `Customer` `TableAdapter.Delete` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet25":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet25":::

## <a name="net-security"></a>.NET 보안

`INSERT` `UPDATE` 데이터베이스의 테이블에서 선택한, 또는를 수행할 수 있는 권한이 있어야 합니다 `DELETE` .

## <a name="see-also"></a>참고 항목

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
