---
title: 데이터를 데이터베이스에 다시 저장 | Microsoft Docs
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
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1b1a54d8be5ab4aa9703d318d0b537deff53b6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652876"
---
# <a name="save-data-back-to-the-database"></a>데이터를 다시 데이터베이스에 저장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 집합은 데이터의 메모리 내 복사본입니다. 해당 데이터를 수정 하는 경우 해당 변경 내용을 데이터베이스에 다시 저장 하는 것이 좋습니다. 다음 세 가지 방법 중 하나로이 작업을 수행 합니다.

- TableAdapter의 메서드 중 하나를 호출 하 여 `Update`

- TableAdapter의 DBDirect 메서드 중 하나를 호출 하 여

- 데이터 집합에 `TableAdapterManager` 데이터 집합의 다른 테이블과 관련 된 테이블이 포함 되어 있는 경우 Visual Studio가 생성 하는에서 UpdateAll 메서드를 호출 하 여

  Windows Form 또는 XAML 페이지의 컨트롤에 데이터 집합 테이블을 바인딩하는 경우 데이터 바인딩 아키텍처에서 모든 작업을 수행 합니다.

  Tableadapter에 대해 잘 알고 있는 경우 다음 항목 중 하나로 직접 이동할 수 있습니다.

|항목|설명|
|-----------|-----------------|
|[데이터베이스에 새 레코드 삽입](../data-tools/insert-new-records-into-a-database.md)|Tableadapter 또는 Command 개체를 사용 하 여 업데이트 및 삽입을 수행 하는 방법|
|[TableAdapter를 사용하여 데이터 업데이트](../data-tools/update-data-by-using-a-tableadapter.md)|Tableadapter를 사용 하 여 업데이트를 수행 하는 방법|
|[계층적 업데이트](../data-tools/hierarchical-update.md)|두 개 이상의 관련 테이블이 포함 된 데이터 집합에서 업데이트를 수행 하는 방법|
|[동시성 예외 처리](../data-tools/handle-a-concurrency-exception.md)|두 사용자가 동시에 데이터베이스의 동일한 데이터를 변경 하려고 시도 하는 경우 예외를 처리 하는 방법|
|[트랜잭션을 사용 하 여 데이터 저장](../data-tools/save-data-by-using-a-transaction.md)|System.object 네임 스페이스 및 TransactionScope 개체를 사용 하 여 트랜잭션에 데이터를 저장 하는 방법|
|[트랜잭션에 데이터 저장](../data-tools/save-data-in-a-transaction.md)|시스템 트랜잭션 네임 스페이스를 사용 하 여 트랜잭션에 데이터를 저장 하는 방법|
|[데이터베이스에 데이터 저장(여러 테이블)](../data-tools/save-data-to-a-database-multiple-tables.md)|레코드를 편집 하 고 여러 테이블의 변경 내용을 데이터베이스에 다시 저장 하는 방법|
|[개체에서 데이터베이스로 데이터 저장](../data-tools/save-data-from-an-object-to-a-database.md)|TableAdapter DbDirect 메서드를 사용 하 여 데이터 집합에 없는 개체에서 데이터베이스로 데이터를 전달 하는 방법|
|[TableAdapter DBDirect 메서드를 사용하여 데이터 저장](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|TableAdapter를 사용 하 여 SQL 쿼리를 데이터베이스에 직접 보내는 방법|
|[데이터 세트를 XML로 저장](../data-tools/save-a-dataset-as-xml.md)|XML 문서에 데이터 집합을 저장 하는 방법|

## <a name="two-stage-updates"></a>2 단계 업데이트
 데이터 원본 업데이트는 2 단계 프로세스로 진행 됩니다. 첫 번째 단계는 새 레코드, 변경 된 레코드 또는 삭제 된 레코드를 사용 하 여 데이터 집합을 업데이트 하는 것입니다. 응용 프로그램에서 해당 변경 내용을 데이터 원본으로 다시 보내지 않는 경우 업데이트가 완료 된 것입니다.

 변경 내용을 데이터베이스로 다시 보내는 경우 두 번째 단계가 필요 합니다. 데이터 바인딩된 컨트롤을 사용 하지 않는 경우 데이터 집합을 채우는 데 사용한 것과 동일한 TableAdapter (또는 데이터 어댑터)의 Update 메서드를 수동으로 호출 해야 합니다. 그러나 다른 어댑터를 사용 하 여 데이터 원본 간에 데이터를 이동 하거나 여러 데이터 원본을 업데이트할 수도 있습니다. 데이터 바인딩을 사용 하지 않고 관련 테이블에 대 한 변경 내용을 저장 하는 경우 자동 생성 된 TableAdapterManager 클래스의 변수를 수동으로 인스턴스화한 다음 해당 UpdateAll 메서드를 호출 해야 합니다.

 ![Visual Basic 데이터 집합 업데이트](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates") 성공적인 업데이트에서 2 단계 업데이트 프로세스 및 DataRowVersion 역할

 데이터 집합은 행 컬렉션을 포함 하는 테이블의 컬렉션을 포함 합니다. 나중에 기본 데이터 원본을 업데이트 하려는 경우에는 행을 추가 하거나 제거할 때 DataRowCollection 속성에서 메서드를 사용 해야 합니다. 이러한 메서드는 데이터 원본을 업데이트 하는 데 필요한 변경 내용 추적을 수행 합니다. Rows 속성에서 RemoveAt 컬렉션을 호출 하는 경우 삭제는 데이터베이스에 다시 전달 되지 않습니다.

## <a name="merge-datasets"></a>데이터 집합 병합
 데이터 집합을 다른 데이터 집합과 *병합* 하 여 데이터 집합의 내용을 업데이트할 수 있습니다. 여기에는 *원본* 데이터 집합의 내용을 호출 하는 데이터 집합 ( *대상* 데이터 집합 이라고 함)에 복사 하는 작업이 포함 됩니다. 데이터 집합을 병합할 때 원본 데이터 집합의 새 레코드가 대상 데이터 집합에 추가 됩니다. 또한 원본 데이터 집합의 추가 열이 대상 데이터 집합에 추가 됩니다. 로컬 데이터 집합이 있고 다른 응용 프로그램에서 두 번째 데이터 집합을 가져오는 경우 데이터 집합을 병합 하는 것이 유용 합니다. 또한 XML web services와 같은 구성 요소에서 두 번째 데이터 집합을 가져오는 경우 또는 여러 데이터 집합의 데이터를 통합 해야 하는 경우에도 유용 합니다.

 데이터 집합을 병합할 때 `preserveChanges` <xref:System.Data.DataSet.Merge%2A> 대상 데이터 집합에서 기존 수정 내용을 유지할지 여부를 메서드에 알려 주는 부울 인수 ()를 전달할 수 있습니다. 데이터 집합은 여러 버전의 레코드를 유지 하기 때문에 두 개 이상의 레코드가 병합 되 고 있다는 점을 명심 해야 합니다. 다음 표에서는 두 데이터 집합의 레코드를 병합 하는 방법을 보여 줍니다.

|DataRowVersion|대상 데이터 세트|원본 데이터 세트|
|--------------------|--------------------|--------------------|
|원래 이름|James Wilson|James C. Wilson|
|현재|Jim Wilson|James C. Wilson|

 <xref:System.Data.DataSet.Merge%2A>이전 테이블에서 메서드를 호출 하면 `preserveChanges=false targetDataset.Merge(sourceDataset)` 다음과 같은 결과가 발생 합니다.

|DataRowVersion|대상 데이터 세트|원본 데이터 세트|
|--------------------|--------------------|--------------------|
|원래 이름|James C. Wilson|James C. Wilson|
|현재|James C. Wilson|James C. Wilson|

 <xref:System.Data.DataSet.Merge%2A>를 사용 하 여 메서드를 호출 `preserveChanges = true targetDataset.Merge(sourceDataset, true)` 하면 다음과 같은 결과가 나타납니다.

|DataRowVersion|대상 데이터 세트|원본 데이터 세트|
|--------------------|--------------------|--------------------|
|원래 이름|James C. Wilson|James C. Wilson|
|현재|Jim Wilson|James C. Wilson|

> [!CAUTION]
> 시나리오에서 `preserveChanges = true` <xref:System.Data.DataSet.RejectChanges%2A> 대상 데이터 집합의 레코드에 대해 메서드를 호출 하는 경우 *원본* 데이터 집합에서 원래 데이터로 되돌립니다. 즉, 대상 데이터 집합을 사용 하 여 원래 데이터 원본을 업데이트 하려고 하면 업데이트할 원래 행을 찾지 못할 수 있습니다. 데이터 원본에서 업데이트 된 레코드로 다른 데이터 집합을 채운 다음, 동시성 위반을 방지 하기 위해 병합을 수행 하 여 동시성 위반을 방지할 수 있습니다. 데이터 집합을 채운 후 다른 사용자가 데이터 소스의 레코드를 수정 하면 동시성 위반이 발생 합니다.

## <a name="update-constraints"></a>제약 조건 업데이트
 기존 데이터 행을 변경 하려면 개별 열의 데이터를 추가 하거나 업데이트 합니다. 데이터 집합에 제약 조건 (예: 외래 키 또는 null을 허용 하지 않는 제약 조건)이 포함 된 경우 업데이트할 때 레코드가 일시적으로 오류 상태에 있을 수 있습니다. 즉, 한 열에 대 한 업데이트를 완료 한 후 다음 항목을 가져오기 전에는 오류 상태가 될 수 있습니다.

 중간 제약 조건 위반을 방지 하기 위해 업데이트 제약 조건을 일시적으로 중단할 수 있습니다. 이 두 가지 용도로 사용 됩니다.

- 한 열 업데이트를 완료 했지만 다른 열 업데이트를 시작 하지 않은 후 오류가 발생 하지 않도록 방지 합니다.

- 특정 업데이트 이벤트 (종종 유효성 검사에 사용 되는 이벤트)가 발생 하지 않도록 합니다.

  업데이트를 완료 한 후에도 업데이트 이벤트를 다시 사용 하도록 설정 하 고 발생 시키는 제약 조건 검사를 다시 활성화할 수 있습니다.

> [!NOTE]
> Windows Forms datagrid에 기본 제공 되는 데이터 바인딩 아키텍처는 포커스가 행 외부로 이동할 때까지 제약 조건 검사를 일시 중단 하 고 <xref:System.Data.DataRow.BeginEdit%2A> , 또는 메서드를 명시적으로 호출할 필요가 없습니다 <xref:System.Data.DataRow.EndEdit%2A> <xref:System.Data.DataRow.CancelEdit%2A> .

 <xref:System.Data.DataSet.Merge%2A>데이터 집합에 대해 메서드가 호출 되 면 제약 조건이 자동으로 비활성화 됩니다. 병합이 완료 되 면 사용 하도록 설정할 수 없는 데이터 집합에 대 한 제약 조건이 있으면 <xref:System.Data.ConstraintException> 이 throw 됩니다. 이 경우 속성을로 <xref:System.Data.DataSet.EnforceConstraints%2A> 설정 하 고 속성을 `false,` 로 다시 설정 하기 전에 모든 제약 조건 위반을 확인 해야 합니다 <xref:System.Data.DataSet.EnforceConstraints%2A> `true` .

 업데이트를 완료 한 후에도 업데이트 이벤트를 다시 사용 하도록 설정 하 고 발생 시키는 제약 조건 검사를 다시 활성화할 수 있습니다.

 이벤트를 일시 중단 하는 방법에 대 한 자세한 내용은 [데이터 집합을 채우는 동안 제약 조건](../data-tools/turn-off-constraints-while-filling-a-dataset.md)해제를 참조 하세요.

## <a name="dataset-update-errors"></a>데이터 집합 업데이트 오류
 데이터 집합의 레코드를 업데이트 하면 오류가 발생할 수 있습니다. 예를 들어 잘못 된 형식의 데이터를 열 또는 너무 긴 데이터 또는 다른 무결성 문제가 있는 데이터에 실수로 쓸 수 있습니다. 또는 업데이트 이벤트의 모든 단계에서 사용자 지정 오류를 발생 시킬 수 있는 응용 프로그램별 유효성 검사가 있을 수 있습니다. 자세한 내용은 [데이터 집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)를 참조 하세요.

## <a name="maintaining-information-about-changes"></a>변경 내용에 대 한 정보 유지 관리
 데이터 집합의 변경 내용에 대 한 정보는 두 가지 방법으로 유지 됩니다. 즉, 변경 된 ()을 나타내는 행에 플래그를 지정 하 <xref:System.Data.DataRow.RowState%2A> 고 레코드의 여러 복사본을 유지 <xref:System.Data.DataRowVersion> 합니다 (). 프로세스는이 정보를 사용 하 여 데이터 집합에서 변경 된 내용을 확인 하 고 데이터 원본에 적절 한 업데이트를 보낼 수 있습니다.

### <a name="rowstate-property"></a>RowState 속성
 <xref:System.Data.DataRow.RowState%2A>개체의 속성은 <xref:System.Data.DataRow> 특정 데이터 행의 상태에 대 한 정보를 제공 하는 값입니다.

 다음 표에서는 열거형의 가능한 값에 대해 자세히 설명 합니다 <xref:System.Data.DataRowState> .

|DataRowState 값|설명|
|------------------------|-----------------|
|<xref:System.Data.DataRowState>|행이에 항목으로 추가 되었습니다 <xref:System.Data.DataRowCollection> . 이 상태의 행은 마지막 메서드가 호출 될 때 존재 하지 않기 때문에 해당 하는 원래 버전이 없습니다 <xref:System.Data.DataRow.AcceptChanges%2A> .|
|<xref:System.Data.DataRowState>|개체의를 사용 하 여 행을 삭제 했습니다 <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow> .|
|<xref:System.Data.DataRowState>|행이 만들어졌지만 <xref:System.Data.DataRowCollection>의 일부는 아닙니다. <xref:System.Data.DataRow>개체는 만들어진 직후, 컬렉션에 추가 되기 전에, 그리고 컬렉션에서 제거 된 후에이 상태가 됩니다.|
|<xref:System.Data.DataRowState>|행의 열 값이 변경 되었습니다.|
|<xref:System.Data.DataRowState>|<xref:System.Data.DataRow.AcceptChanges%2A>가 마지막으로 호출된 이후에 행이 변경되지 않았습니다.|

### <a name="datarowversion-enumeration"></a>DataRowVersion 열거형
 데이터 집합은 여러 버전의 레코드를 유지 관리 합니다. <xref:System.Data.DataRowVersion>개체의 열거형은 <xref:System.Data.DataRow> 특정 개체 버전을 반환 하는 데 사용할 수 있는 값입니다 <xref:System.Data.DataRow> .

 다음 표에서는 열거형의 가능한 값에 대해 자세히 설명 합니다 <xref:System.Data.DataRowVersion> .

|DataRowVersion 값|설명|
|--------------------------|-----------------|
|<xref:System.Data.DataRowVersion>|레코드의 현재 버전에는를 마지막으로 호출한 이후 레코드에서 수행 된 모든 수정 내용이 포함 됩니다 <xref:System.Data.DataRow.AcceptChanges%2A> . 행이 삭제 된 경우에는 현재 버전이 없습니다.|
|<xref:System.Data.DataRowVersion>|데이터 집합 스키마 또는 데이터 원본에 의해 정의 된 레코드의 기본값입니다.|
|<xref:System.Data.DataRowVersion>|레코드의 원래 버전은 데이터 집합에서 변경 내용이 마지막으로 커밋된 시점의 레코드 복사본입니다. 실제로이는 일반적으로 데이터 원본에서 읽은 레코드의 버전입니다.|
|<xref:System.Data.DataRowVersion>|업데이트 중간에 (즉, 메서드와 메서드를 호출한 시간 사이)에 일시적으로 사용 가능한 레코드의 제안 된 버전입니다 <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> . 일반적으로와 같은 이벤트에 대 한 처리기에서 제안 된 버전의 레코드에 액세스 <xref:System.Data.DataTable.RowChanging> 합니다. 메서드를 호출 하면 <xref:System.Data.DataRow.CancelEdit%2A> 변경 내용이 취소 되 고 데이터 행의 제안 된 버전이 삭제 됩니다.|

 원본 및 현재 버전은 업데이트 정보가 데이터 원본으로 전송 되는 경우에 유용 합니다. 일반적으로 데이터 원본에 업데이트를 보낼 때 데이터베이스의 새 정보는 레코드의 현재 버전에 있습니다. 원래 버전의 정보는 업데이트할 레코드를 찾는 데 사용 됩니다.

 예를 들어 레코드의 기본 키가 변경 된 경우에는 변경 내용을 업데이트 하기 위해 데이터 원본에서 올바른 레코드를 찾는 방법이 필요 합니다. 원래 버전이 없는 경우 레코드는 데이터 원본에 추가 되어 원치 않는 추가 레코드 뿐만 아니라 부정확 하 고 오래 된 레코드 하나에 있을 수 있습니다. 두 버전은 동시성 제어에도 사용 됩니다. 데이터 원본에 있는 레코드와 원래 버전을 비교 하 여 레코드가 데이터 집합에 로드 된 후 변경 되었는지 확인할 수 있습니다.

 제안 된 버전은 데이터 집합에 대 한 변경 내용을 실제로 커밋하기 전에 유효성 검사를 수행 해야 하는 경우에 유용 합니다.

 레코드가 변경 된 경우에도 해당 행의 원래 버전이 나 현재 버전이 항상 존재 하지는 않습니다. 테이블에 새 행을 삽입 하는 경우 원래 버전이 없으며 현재 버전만 있습니다. 마찬가지로, 테이블의 메서드를 호출 하 여 행을 삭제 하는 경우에는 `Delete` 원래 버전이 있지만 현재 버전은 없습니다.

 데이터 행의 메서드를 쿼리하여 레코드의 특정 버전이 존재 하는지 테스트할 수 있습니다 <xref:System.Data.DataRow.HasVersion%2A> . <xref:System.Data.DataRowVersion>열의 값을 요청할 때 열거형 값을 선택적 인수로 전달 하 여 레코드의 두 버전 중 하나에 액세스할 수 있습니다.

## <a name="getting-changed-records"></a>변경 된 레코드 가져오기
 일반적으로 데이터 집합의 모든 레코드를 업데이트 하지 않는 것이 좋습니다. 예를 들어, 사용자가 <xref:System.Windows.Forms.DataGridView> 많은 레코드를 표시 하는 Windows Forms 컨트롤을 사용할 수 있습니다. 그러나 사용자는 몇 개의 레코드만 업데이트 하 고 삭제 한 다음 새 레코드만 삽입할 수 있습니다. 데이터 집합 및 데이터 테이블은 수정 된 행만 반환 하는 메서드 ()를 제공 `GetChanges` 합니다.

 `GetChanges`데이터 테이블 ( <xref:System.Data.DataTable.GetChanges%2A> ) 또는 데이터 집합 ()의 메서드를 사용 하 여 변경 된 레코드의 하위 집합을 만들 수 있습니다 <xref:System.Data.DataSet.GetChanges%2A> . 데이터 테이블에 대해 메서드를 호출 하면 변경 된 레코드만 포함 된 테이블의 복사본을 반환 합니다. 마찬가지로, 데이터 집합에서 메서드를 호출 하는 경우 변경 된 레코드만 포함 된 새 데이터 집합을 가져옵니다.

 `GetChanges` 는 자체 변경 된 모든 레코드를 반환 합니다. 반면, 원하는을 <xref:System.Data.DataRowState> 메서드에 매개 변수로 전달 하 여 `GetChanges` 새로 추가 된 레코드, 삭제 하도록 표시 된 레코드, 분리 된 레코드 또는 수정 된 레코드 중에서 변경 된 레코드의 하위 집합을 지정할 수 있습니다.

 변경 된 레코드의 하위 집합을 가져오는 작업은 처리를 위해 다른 구성 요소로 레코드를 전송 하려는 경우에 유용 합니다. 전체 데이터 집합을 전송 하는 대신 구성 요소에 필요한 레코드만 가져옴으로써 다른 구성 요소와 통신 하는 오버 헤드를 줄일 수 있습니다. 자세한 내용은 [방법: 변경 된 행 검색](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)을 참조 하세요.

## <a name="committing-changes-in-the-dataset"></a>데이터 집합의 변경 내용 커밋
 데이터 집합에서 변경이 수행 되 면 변경 된 <xref:System.Data.DataRow.RowState%2A> 행의 속성이 설정 됩니다. 원본 및 현재 버전의 레코드는 속성을 사용 하 여 설정 하 고 유지 관리 하며 사용할 수 있습니다 <xref:System.Data.DataRowView.RowVersion%2A> . 이러한 변경 된 행의 속성에 저장 된 메타 데이터는 데이터 원본에 대 한 올바른 업데이트를 전송 하는 데 필요 합니다.

 변경 내용이 데이터 원본의 현재 상태를 반영 하는 경우 더 이상이 정보를 유지 관리할 필요가 없습니다. 일반적으로 데이터 집합 및 해당 소스가 동기화 되는 경우는 두 번입니다.

- 원본에서 데이터를 읽는 경우와 같이 데이터 집합에 정보를 로드 한 직후

- 데이터 집합에서 데이터 원본으로 변경 내용을 보낸 후 (이전에는 변경 하지 않고 데이터베이스에 변경 내용을 전송 하는 데 필요한 변경 정보를 잃지 않음)

  메서드를 호출 하 여 데이터 집합에 대 한 보류 중인 변경 내용을 커밋할 수 있습니다 <xref:System.Data.DataSet.AcceptChanges%2A> . 일반적으로는 <xref:System.Data.DataSet.AcceptChanges%2A> 응용 프로그램에서 다음과 같은 시간에 호출 됩니다.

- 데이터 집합을 로드 한 후 TableAdapter의 메서드를 호출 하 여 데이터 집합을 로드 하는 경우 `Fill` 어댑터는 자동으로 변경 내용을 커밋합니다. 그러나 다른 데이터 집합을 병합 하 여 데이터 집합을 로드 하는 경우에는 변경 내용을 수동으로 커밋해야 합니다.

  > [!NOTE]
  > `Fill`어댑터의 속성을로 설정 하 여 메서드를 호출할 때 어댑터가 자동으로 변경 내용을 커밋하는 것을 방지할 수 있습니다 `AcceptChangesDuringFill` `false` . 로 설정 된 경우 `false` <xref:System.Data.DataRow.RowState%2A> 채우기 중에 삽입 된 각 행의는로 설정 됩니다 <xref:System.Data.DataRowState> .

- XML Web services와 같은 다른 프로세스에 데이터 집합 변경 내용을 전송 합니다.

  > [!CAUTION]
  > 이 방법으로 변경 내용을 커밋하면 변경 정보가 지워집니다. 응용 프로그램이 데이터 집합에서 변경 된 내용을 확인 하는 데 필요한 작업을 완료 한 후에 변경 내용을 커밋하지 않습니다.

  이 메서드는 다음을 수행 합니다.

- 버전 <xref:System.Data.DataRowVersion> 에 레코드의 버전을 쓰고 <xref:System.Data.DataRowVersion> 원래 버전을 덮어씁니다.

- <xref:System.Data.DataRow.RowState%2A>속성이로 설정 된 모든 행을 제거 <xref:System.Data.DataRowState> 합니다.

- <xref:System.Data.DataRow.RowState%2A>레코드의 속성을로 설정 합니다 <xref:System.Data.DataRowState> .

  <xref:System.Data.DataSet.AcceptChanges%2A>메서드는 세 가지 수준에서 사용할 수 있습니다. 개체에 대해이 메서드를 호출 <xref:System.Data.DataRow> 하 여 해당 행에 대 한 변경 내용을 커밋할 수 있습니다. 또한 개체에 대해이 메서드 <xref:System.Data.DataTable> 를 호출 하 여 테이블의 모든 행을 커밋할 수 있습니다. 마지막으로 개체에 대해이 메서드를 호출 <xref:System.Data.DataSet> 하 여 데이터 집합의 모든 테이블에 있는 모든 레코드의 보류 중인 모든 변경 내용을 커밋할 수 있습니다.

  다음 표에서는 메서드가 호출 되는 개체에 따라 커밋된 변경 내용을 설명 합니다.

|메서드|결과|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|특정 행에 대해서만 변경 내용이 커밋됩니다.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|특정 테이블의 모든 행에 대 한 변경 내용이 커밋됩니다.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|데이터 집합의 모든 테이블에 있는 모든 행에 대 한 변경 내용이 커밋됩니다.|

> [!NOTE]
> TableAdapter의 메서드를 호출 하 여 데이터 집합을 로드 하는 경우에는 `Fill` 변경 내용을 명시적으로 수락할 필요가 없습니다. 기본적으로 메서드는 `Fill` `AcceptChanges` 데이터 테이블 채우기를 완료 한 후 메서드를 호출 합니다.

 관련 메서드인는 `RejectChanges` <xref:System.Data.DataRowVersion> 버전을 다시 레코드 버전으로 복사 하 여 변경의 영향을 취소 합니다 <xref:System.Data.DataRowVersion> . 또한 <xref:System.Data.DataRow.RowState%2A> 각 레코드의를 다시로 설정 합니다 <xref:System.Data.DataRowState> .

## <a name="data-validation"></a>데이터 유효성 검사
 응용 프로그램의 데이터가 전달 되는 프로세스의 요구 사항을 충족 하는지 확인 하기 위해 종종 유효성 검사를 추가 해야 합니다. 이렇게 하려면 폼의 사용자 항목이 올바른지, 다른 응용 프로그램에 의해 응용 프로그램에 전송 된 데이터의 유효성을 검사 하는지 확인 하거나, 구성 요소 내에서 계산 된 정보가 데이터 원본 및 응용 프로그램 요구 사항의 제약 조건 내에 포함 되는지 확인 해야 합니다.

 다음과 같은 여러 가지 방법으로 데이터의 유효성을 검사할 수 있습니다.

- 비즈니스 계층에서 데이터의 유효성을 검사 하는 코드를 응용 프로그램에 추가 합니다. 데이터 집합은이 작업을 수행할 수 있는 한 곳입니다. 데이터 집합 디자이너는 열 및 행 값이 변경 될 때 변경 내용의 유효성을 검사 하는 기능과 같은 백 엔드 유효성 검사의 이점 중 일부를 제공 합니다. 자세한 내용은 [데이터 집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)를 참조 하세요.

- 프레젠테이션 계층에서 폼에 유효성 검사를 추가 합니다. 자세한 내용은 [Windows Forms에서 사용자 입력 유효성 검사](https://msdn.microsoft.com/library/4ec07681-1dee-4bf9-be5e-718f635a33a1)를 참조 하세요.

- 데이터 백 엔드에서 데이터 원본으로 데이터를 보내고 (예: 데이터베이스) 데이터를 수락 하거나 거부 하도록 허용 합니다. 데이터의 유효성을 검사 하 고 오류 정보를 제공 하기 위한 정교한 기능이 있는 데이터베이스를 사용 하 여 작업 하는 경우에는 데이터의 출처에 상관 없이 데이터의 유효성을 검사할 수 있으므로 실용적인 방법이 될 수 있습니다. 그러나이 방법은 응용 프로그램별 유효성 검사 요구 사항을 수용 하지 못할 수 있습니다. 또한 데이터 원본의 유효성을 검사 하는 경우 백 엔드에서 발생 하는 유효성 검사 오류를 응용 프로그램에서 얼마나 쉽게 해결할 수 있는지에 따라 데이터 원본에 대 한 많은 왕복이 발생할 수 있습니다.

  > [!IMPORTANT]
  > 로 설정 된 속성을 사용 하 여 데이터 명령을 사용 하는 경우 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> <xref:System.Data.CommandType> 클라이언트에서 전송 된 정보를 데이터베이스에 전달 하기 전에 주의 깊게 확인 합니다. 악의적인 사용자가 인증되지 않은 액세스 권한을 얻거나 데이터베이스를 손상시키기 위해 수정되었거나 추가된 SQL 문을 전송(주입)할 수도 있습니다. 사용자 입력을 데이터베이스로 전송 하기 전에 항상 정보가 유효한 지 확인 하십시오. 가능 하면 항상 매개 변수가 있는 쿼리 또는 저장 프로시저를 사용 하는 것이 좋습니다. 자세한 내용은 [Script Exploits Overview](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)를 참조하세요.

  데이터 집합에서 변경한 후에는 변경 내용을 데이터 원본에 전송할 수 있습니다. 가장 일반적으로 `Update` TableAdapter (또는 데이터 어댑터)의 메서드를 호출 하 여이 작업을 수행 합니다. 메서드는 데이터 테이블의 각 레코드를 반복 하 여 필요한 업데이트 유형 (있는 경우)을 결정 하 고 적절 한 명령을 실행 합니다.

## <a name="transmitting-updates-to-the-data-source"></a>데이터 원본에 업데이트 전송
 업데이트를 수행 하는 방법에 대 한 예시는 응용 프로그램에서 단일 데이터 테이블이 포함 된 데이터 집합을 사용 한다고 가정 합니다. 응용 프로그램은 데이터베이스에서 두 개의 행을 페치합니다. 검색 후 메모리 내 데이터 테이블은 다음과 같습니다.

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

 응용 프로그램이 김소미의 상태를 "기본 설정"으로 변경 합니다. 이러한 변경으로 인해 <xref:System.Data.DataRow.RowState%2A> 해당 행의 속성 값이에서 <xref:System.Data.DataRowState> 로 변경 <xref:System.Data.DataRowState> 됩니다. <xref:System.Data.DataRow.RowState%2A>첫 번째 행에 대 한 속성 값은 그대로 유지 <xref:System.Data.DataRowState> 됩니다. 이제 데이터 테이블은 다음과 같습니다.

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

 이제 애플리케이션에서 `Update` 메서드를 호출하여 데이터 세트을 데이터베이스로 전송합니다. 메서드는 각 행을 차례로 검사 합니다. 첫 번째 행의 경우 메서드는 데이터베이스에서 원래 가져온 이후 해당 행이 변경 되지 않았기 때문에 SQL 문을 데이터베이스에 전송 하지 않습니다.

 그러나 두 번째 행의 경우 메서드는 `Update` 올바른 데이터 명령을 자동으로 호출 하 여 데이터베이스에 전송 합니다. SQL 문의 특정 구문은 기본 데이터 저장소에서 지 원하는 SQL 언어에 따라 달라 집니다. 하지만 전송 된 SQL 문의 다음과 같은 일반적인 특성은 중요 합니다.

- 전송 된 SQL 문은 UPDATE 문입니다. 어댑터는 속성 값이 이기 때문에 UPDATE 문을 사용 하는 <xref:System.Data.DataRow.RowState%2A> 것을 알고 <xref:System.Data.DataRowState> 있습니다.

- 전송 된 SQL 문에는 UPDATE 문의 대상이 행 임을 나타내는 WHERE 절이 포함 되어 있습니다 `CustomerID = 'c400'` . SELECT 문의이 부분은 `CustomerID` 가 대상 테이블의 기본 키 이기 때문에 다른 모든의 대상 행을 구분 합니다. `DataRowVersion.Original`행을 식별 하는 데 필요한 값이 변경 되는 경우 WHERE 절에 대 한 정보는 레코드의 원래 버전 ()에서 파생 됩니다.

- 전송 된 SQL 문에는 수정 된 열의 새 값을 설정 하는 SET 절이 포함 되어 있습니다.

    > [!NOTE]
    > TableAdapter의 `UpdateCommand` 속성이 저장 프로시저의 이름으로 설정 된 경우 어댑터는 SQL 문을 생성 하지 않습니다. 대신 전달 된 적절 한 매개 변수를 사용 하 여 저장 프로시저를 호출 합니다.

## <a name="passing-parameters"></a>매개 변수 전달
 일반적으로 매개 변수를 사용 하 여 데이터베이스에서 업데이트할 레코드의 값을 전달 합니다.  TableAdapter의 메서드는 `Update` UPDATE 문을 실행할 때 매개 변수 값을 입력 해야 합니다. `Parameters`적절 한 데이터 명령 (이 경우 TableAdapter의 개체)에 대 한 컬렉션에서 이러한 값을 가져옵니다 `UpdateCommand` .

 Visual Studio 도구를 사용 하 여 데이터 어댑터를 생성 한 경우 개체는 `UpdateCommand` 문의 각 매개 변수 자리 표시자에 해당 하는 매개 변수 컬렉션을 포함 합니다.

 <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName>각 매개 변수의 속성은 데이터 테이블의 열을 가리킵니다. 예를 `SourceColumn` `au_id` 들어 및 매개 변수에 대 한 속성 `Original_au_id` 은 데이터 테이블의 어떤 열에 author id가 포함 되어 있는 것으로 설정 됩니다. 어댑터의 `Update` 메서드가 실행 될 때 업데이트 되는 레코드에서 author id 열을 읽고 해당 값을 문으로 채웁니다.

 UPDATE 문에서는 레코드에 기록 될 새 값과 이전 값 (레코드를 데이터베이스에서 찾을 수 있도록)을 둘 다 지정 해야 합니다. 따라서 각 값에 대해 두 개의 매개 변수, 즉 SET 절 및 WHERE 절에 대 한 다른 매개 변수가 있습니다. 두 매개 변수는 업데이트 되는 레코드에서 데이터를 읽었지만 매개 변수의 [SqlParameter 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sourceversion.aspx)에 따라 열 값의 다른 버전을 가져옵니다. SET 절의 매개 변수는 현재 버전을 가져오고 WHERE 절에 대 한 매개 변수는 원래 버전을 가져옵니다.

> [!NOTE]
> `Parameters`데이터 어댑터의 이벤트에 대 한 이벤트 처리기에서 일반적으로 수행 하는 코드에서 컬렉션의 값을 직접 설정할 수도 있습니다 <xref:System.Data.DataTable.RowChanging> .

## <a name="see-also"></a>관련 항목
 [TableAdapter를 사용 하 여 데이터 업데이트](../data-tools/update-data-by-using-a-tableadapter.md) [Visual Studio에서 데이터에 데이터 바인딩을](../data-tools/bind-controls-to-data-in-visual-studio.md) [수신 하도록 응용 프로그램 준비](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [데이터 유효성 검사](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
