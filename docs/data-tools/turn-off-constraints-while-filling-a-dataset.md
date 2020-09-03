---
title: 데이터 세트를 채우는 동안 제약 조건 해제
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7bdb225a5b310f6f602619b2afcee610c3e9258b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281268"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>데이터 세트를 채우는 동안 제약 조건 해제

데이터 집합에 제약 조건 (예: foreign key 제약 조건)이 포함 된 경우 데이터 집합에 대해 수행 되는 작업의 순서와 관련 된 오류를 발생 시킬 수 있습니다. 예를 들어 관련 된 부모 레코드를 로드 하기 전에 자식 레코드를 로드 하면 제약 조건을 위반 하 여 오류가 발생할 수 있습니다. 자식 레코드를 로드 하는 즉시 제약 조건은 관련 된 부모 레코드를 확인 하 고 오류를 발생 시킵니다.

임시 제약 조건 일시 중단을 허용 하는 메커니즘이 없는 경우 자식 테이블에 레코드를 로드 하려고 할 때마다 오류가 발생 합니다. 데이터 집합의 모든 제약 조건을 일시 중단 하는 또 다른 방법은 <xref:System.Data.DataRow.BeginEdit%2A> , 및 속성을 사용 하는 것입니다 <xref:System.Data.DataRow.EndEdit%2A> .

> [!NOTE]
> 제약 조건이 해제 되 면 유효성 검사 이벤트 (예: <xref:System.Data.DataTable.ColumnChanging> 및 <xref:System.Data.DataTable.RowChanging> )가 발생 하지 않습니다.

## <a name="to-suspend-update-constraints-programmatically"></a>프로그래밍 방식으로 업데이트 제약 조건을 일시 중단 하려면

- 다음 예제에서는 데이터 집합에서 제약 조건 확인을 일시적으로 해제 하는 방법을 보여 줍니다.

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>데이터 세트 디자이너를 사용 하 여 업데이트 제약 조건을 일시 중단 하려면

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다. 자세한 내용은 [연습: 데이터 세트 디자이너에서 데이터 집합 만들기](walkthrough-creating-a-dataset-with-the-dataset-designer.md)를 참조 하세요.

2. **속성** 창에서 <xref:System.Data.DataSet.EnforceConstraints%2A> 속성을 `false`로 설정합니다.

## <a name="see-also"></a>추가 정보

- [TableAdapters를 사용하여 데이터 세트 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)
- [데이터 세트에서의 관계](../data-tools/relationships-in-datasets.md)
