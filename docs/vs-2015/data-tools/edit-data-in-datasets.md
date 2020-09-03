---
title: 데이터 집합의 데이터 편집 | Microsoft Docs
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
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 699ee9b6e7a68c6a79f7f7dac526127206e8aa42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672396"
---
# <a name="edit-data-in-datasets"></a>데이터 세트의 데이터 편집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모든 데이터베이스의 테이블에서 데이터를 편집 하는 것 처럼 데이터 테이블의 데이터를 편집 합니다. 이 프로세스에는 테이블의 레코드 삽입, 업데이트 및 삭제가 포함 될 수 있습니다. 데이터 바인딩된 폼에서 사용자가 편집할 수 있는 필드를 지정할 수 있습니다. 이러한 경우 데이터 바인딩 인프라는 모든 변경 내용 추적을 처리 하 여 나중에 변경 내용을 데이터베이스로 다시 전송할 수 있도록 합니다. 프로그래밍 방식으로 데이터를 편집 하 고 해당 변경 내용을 데이터베이스에 다시 보내려면 변경 내용 추적을 수행 하는 개체 및 메서드를 사용 해야 합니다.

 실제 데이터를 변경 하는 것 외에도를 쿼리하여 <xref:System.Data.DataTable> 특정 데이터 행을 반환할 수도 있습니다. 예를 들어 개별 행, 특정 버전의 행 (원래 및 제안), 변경 된 행 또는 오류가 있는 행을 쿼리할 수 있습니다.

## <a name="to-edit-rows-in-a-dataset"></a>데이터 집합의 행을 편집 하려면
 에서 기존 행을 편집 하려면 편집 하려는를 <xref:System.Data.DataTable> 찾은 <xref:System.Data.DataRow> 다음 업데이트 된 값을 원하는 열에 할당 해야 합니다.

 편집 하려는 행의 인덱스를 모르는 경우 메서드를 사용 `FindBy` 하 여 기본 키로 검색 합니다.

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 행 인덱스를 알고 있으면 다음과 같이 행에 액세스 하 여 행을 편집할 수 있습니다.

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>데이터 집합에 새 행을 삽입 하려면
 데이터 바인딩된 컨트롤을 사용 하는 응용 프로그램은 일반적으로 [BindingNavigator 컨트롤](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e)의 **새로 추가** 단추를 통해 새 레코드를 추가 합니다.

 데이터 집합에 새 레코드를 수동으로 추가 하려면 DataTable에서 메서드를 호출 하 여 새 데이터 행을 만듭니다. 그런 다음의 컬렉션 ()에 행을 추가 합니다 <xref:System.Data.DataRow> <xref:System.Data.DataTable.Rows%2A> <xref:System.Data.DataTable> .

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 데이터 집합에서 데이터 원본에 업데이트를 전송 하는 데 필요한 정보를 유지 하려면 메서드를 사용 <xref:System.Data.DataRow.Delete%2A> 하 여 데이터 테이블에서 행을 제거 합니다. 예를 들어 응용 프로그램에서 TableAdapter (또는)를 사용 하는 경우 <xref:System.Data.Common.DataAdapter> tableadapter의 `Update` 메서드는 데이터베이스에서가 인 행을 삭제 합니다 <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState> .

 응용 프로그램이 업데이트를 다시 데이터 원본에 보낼 필요가 없는 경우 데이터 행 컬렉션 ()에 직접 액세스 하 여 레코드를 제거할 수 <xref:System.Data.DataRowCollection.Remove%2A> 있습니다.

#### <a name="to-delete-records-from-a-data-table"></a>데이터 테이블에서 레코드를 삭제 하려면

- <xref:System.Data.DataRow.Delete%2A>의 메서드를 호출 합니다 <xref:System.Data.DataRow> .

     이 메서드는 레코드를 물리적으로 제거 하지 않습니다. 대신 삭제를 위해 레코드를 표시 합니다.

    > [!NOTE]
    > 의 count 속성을 가져오는 경우 <xref:System.Data.DataRowCollection> 결과 개수는 삭제 하도록 표시 된 레코드를 포함 합니다. 삭제 하도록 표시 되지 않은 레코드의 정확한 수를 가져오려면 <xref:System.Data.DataRow.RowState%2A> 각 레코드의 속성을 확인 하는 컬렉션을 반복할 수 있습니다. 삭제 하도록 표시 된 레코드에는 <xref:System.Data.DataRow.RowState%2A> 의가 <xref:System.Data.DataRowState> 있습니다. 또는 행 상태를 기준으로 필터링 하는 데이터 집합의 데이터 뷰를 만들고 여기에서 count 속성을 가져올 수 있습니다.

     다음 예에서는 메서드를 호출 하 여 <xref:System.Data.DataRow.Delete%2A> 테이블의 첫 번째 행을 삭제 된 것으로 표시 하는 방법을 보여 줍니다 `Customers` .

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>변경 된 행이 있는지 확인
 데이터 집합의 레코드가 변경 될 때 해당 변경 내용에 대 한 정보는 커밋할 때까지 저장 됩니다. 데이터 `AcceptChanges` 집합 또는 데이터 테이블의 메서드를 호출 하거나 `Update` TableAdapter 또는 데이터 어댑터의 메서드를 호출할 때 변경 내용을 커밋합니다.

 변경 내용은 각 데이터 행에서 다음 두 가지 방법으로 추적 됩니다.

- 각 데이터 행에는와 관련 된 정보 <xref:System.Data.DataRow.RowState%2A> (예: <xref:System.Data.DataRowState> ,, <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> 또는 <xref:System.Data.DataRowState> )가 포함 되어 있습니다.

- 변경 된 각 데이터 행에는 해당 행의 여러 버전 ( <xref:System.Data.DataRowVersion> ), 원래 버전 (변경 전) 및 현재 버전 (변경 후)이 포함 됩니다. 변경이 보류 중인 기간 (이벤트에 응답할 수 있는 시간 <xref:System.Data.DataTable.RowChanging> ) 동안 세 번째 버전 (제안 된 버전)도 사용할 수 있습니다.

  데이터 집합의 <xref:System.Data.DataSet.HasChanges%2A> 메서드는 `true` 데이터 집합에 변경 내용이 적용 된 경우를 반환 합니다. 변경 된 행이 존재 하는 것을 확인 한 후에 `GetChanges` 는 또는의 메서드를 호출 <xref:System.Data.DataSet> 하 여 변경 된 <xref:System.Data.DataTable> 행 집합을 반환할 수 있습니다. 자세한 내용은 [방법: 변경 된 행 검색](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)을 참조 하세요.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>행이 변경 되었는지 확인 하려면

- <xref:System.Data.DataSet.HasChanges%2A>데이터 집합의 메서드를 호출 하 여 변경 된 행을 확인 합니다.

     다음 예제에서는 메서드에서 반환 값을 확인 하 여 <xref:System.Data.DataSet.HasChanges%2A> 데이터 집합에 변경 된 행이 있는지 여부를 검색 하는 방법을 보여 줍니다 `NorthwindDataset1` .

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>변경 유형 확인
 열거형의 값을 메서드에 전달 하 여 데이터 집합에서 수행 된 변경 내용 유형을 확인할 수도 있습니다 <xref:System.Data.DataRowState> <xref:System.Data.DataSet.HasChanges%2A> .

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>행에 대 한 변경 유형을 확인 하려면

- <xref:System.Data.DataRowState>메서드에 값을 전달 <xref:System.Data.DataSet.HasChanges%2A> 합니다.

     다음 예제에서는 라는 데이터 집합을 확인 하 여 `NorthwindDataset1` 새 행이 추가 되었는지 확인 하는 방법을 보여 줍니다.

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>오류가 있는 행을 찾으려면
 개별 열과 데이터 행을 사용할 때 오류가 발생할 수 있습니다. 속성을 확인 `HasErrors` 하 여, 또는에 오류가 있는지 확인할 수 <xref:System.Data.DataSet> 있습니다 <xref:System.Data.DataTable> <xref:System.Data.DataRow> .

1. 속성을 확인 `HasErrors` 하 여 데이터 집합에 오류가 있는지 확인 합니다.

2. `HasErrors`속성이 인 경우 `true` 테이블의 컬렉션을 반복 하 고 행을 통해를 반복 하 여 오류가 있는 행을 찾습니다.

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
