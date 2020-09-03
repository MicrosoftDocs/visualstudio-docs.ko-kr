---
title: 쿼리 데이터 집합 | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ccd5deffb0127769e2cd9dff3bf2accf75617eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607445"
---
# <a name="query-datasets"></a>데이터 세트 쿼리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 집합에서 특정 레코드를 검색 하려면 DataTable에서 FindBy 메서드를 사용 하거나, 테이블의 rows 컬렉션에 대해 고유한 foreach 루프를 작성 하거나, [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)를 사용 합니다. LINQ to DataSet.

## <a name="dataset-case-sensitivity"></a>데이터 집합 대/소문자 구분
 데이터 집합 내에서 테이블 및 열 이름은 기본적으로 대/소문자를 구분 하지 않습니다. 즉, "Customers" 라는 데이터 집합의 테이블을 "customers" 라고도 합니다. 이는 SQL Server.In SQL Server를 비롯 한 많은 데이터베이스의 명명 규칙과 일치 합니다. 기본 동작은 데이터 요소의 이름을 대/소문자로만 구분할 수 없다는 것입니다.

> [!NOTE]
> 데이터 집합과 달리 XML 문서는 대/소문자를 구분 하므로 스키마에 정의 된 데이터 요소의 이름은 대/소문자를 구분 합니다. 예를 들어 스키마 프로토콜을 사용 하면 스키마에서 "Customers" 라는 테이블과 "customers" 라는 다른 테이블을 정의할 수 있습니다. 이 경우 대/소문자만 다른 요소가 포함 된 스키마를 사용 하 여 dataset 클래스를 생성할 때 이름 충돌이 발생할 수 있습니다.

 하지만 대/소문자 구분은 데이터 집합 내에서 데이터를 해석 하는 방법에 대 한 요인이 될 수 있습니다. 예를 들어 데이터 집합 테이블에서 데이터를 필터링 하는 경우 비교 시 대/소문자를 구분 하는지 여부에 따라 검색 조건이 다른 결과를 반환할 수 있습니다. 데이터 집합의 속성을 설정 하 여 필터링, 검색 및 정렬의 대/소문자 구분 여부를 제어할 수 있습니다 <xref:System.Data.DataSet.CaseSensitive%2A> . 데이터 집합의 모든 테이블은 기본적으로이 속성의 값을 상속 합니다. 테이블의 속성을 설정 하 여 개별 테이블에 대해이 속성을 재정의할 수 있습니다 <xref:System.Data.DataTable.CaseSensitive%2A> .

## <a name="locate-a-specific-row-in-a-data-table"></a>데이터 테이블에서 특정 행 찾기

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>기본 키 값을 사용 하 여 형식화 된 데이터 집합에서 행을 찾으려면

- 행을 찾으려면 `FindBy` 테이블의 기본 키를 사용 하는 강력한 형식의 메서드를 호출 합니다.

     다음 예에서는 `CustomerID` 열이 테이블의 기본 키입니다 `Customers` . 이는 생성 된 메서드가 임을 의미 합니다 `FindBy` `FindByCustomerID` . 이 예제에서는 <xref:System.Data.DataRow> 생성 된 메서드를 사용 하 여 변수에 특정를 할당 하는 방법을 보여 줍니다 `FindBy` .

     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>기본 키 값을 사용 하 여 형식화 되지 않은 데이터 집합에서 행을 찾으려면

- <xref:System.Data.DataRowCollection.Find%2A>컬렉션의 메서드를 호출 <xref:System.Data.DataRowCollection> 하 여 기본 키를 매개 변수로 전달 합니다.

     다음 예에서는 라는 새 행을 선언 하 `foundRow` 고 메서드의 반환 값을 할당 하는 방법을 보여 줍니다 <xref:System.Data.DataRowCollection.Find%2A> . 기본 키가 있는 경우에는 열 인덱스 1의 내용이 메시지 상자에 표시 됩니다.

     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]

## <a name="findrows-by-column-values"></a>열 값으로 findrows

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>열의 값을 기준으로 행을 찾으려면

- 데이터 테이블은 메서드로 전달 된 <xref:System.Data.DataTable.Select%2A> 식에 따라의 배열을 반환 하는 메서드를 사용 하 여 생성 됩니다 <xref:System.Data.DataRow> <xref:System.Data.DataTable.Select%2A> . 유효한 식을 만드는 방법에 대 한 자세한 내용은 페이지의 속성에 대 한 "식 구문" 섹션을 참조 하세요 <xref:System.Data.DataColumn.Expression%2A> .

     다음 예제에서는의 메서드를 사용 하 여 특정 행을 찾는 방법을 보여 줍니다 <xref:System.Data.DataTable.Select%2A> <xref:System.Data.DataTable> .

     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]

## <a name="access-related-records"></a>관련 레코드 액세스
 데이터 집합의 테이블이 관련 된 경우 개체를 <xref:System.Data.DataRelation> 사용 하 여 다른 테이블에서 관련 레코드를 사용할 수 있습니다. 예를 들어 및 테이블을 포함 하는 데이터 집합을 `Customers` `Orders` 사용할 수 있습니다.

 개체를 사용 하 여 <xref:System.Data.DataRelation> <xref:System.Data.DataRow.GetChildRows%2A> <xref:System.Data.DataRow> 부모 테이블에서의 메서드를 호출 하 여 관련 레코드를 찾을 수 있습니다. 이 메서드는 관련 된 자식 레코드의 배열을 반환 합니다. 또는 <xref:System.Data.DataRow.GetParentRow%2A> 자식 테이블에서의 메서드를 호출할 수 있습니다 <xref:System.Data.DataRow> . 이 메서드는 <xref:System.Data.DataRow> 부모 테이블에서 단일를 반환 합니다.

 이 페이지에서는 형식화 된 데이터 집합을 사용 하는 예제를 제공 합니다. 형식화 되지 않은 데이터 집합에서 관계를 탐색 하는 방법은 [DataRelations 탐색](https://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e)을 참조 하세요.

> [!NOTE]
> Windows Forms 응용 프로그램에서 작업 중이 고 데이터 바인딩 기능을 사용 하 여 데이터를 표시 하는 경우 디자이너에서 생성 한 폼을 사용 하면 응용 프로그램에 충분 한 기능을 제공할 수 있습니다. 자세한 내용은 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)을 참조 하세요.

 다음 코드 예제에서는 형식화 된 데이터 집합에서 위쪽 및 아래쪽 관계를 탐색 하는 방법을 보여 줍니다. 이 코드 예제에서는 형식화 된 <xref:System.Data.DataRow> s ( `NorthwindDataSet.OrdersRow` )와 생성 된 `FindBy` *PrimaryKey* ( `FindByCustomerID` ) 메서드를 사용 하 여 원하는 행을 찾고 관련 레코드를 반환 합니다. 예제는 다음을 수행 하는 경우에만 올바르게 컴파일 및 실행 됩니다.

- 테이블이 포함 된 이라는 데이터 집합의 인스턴스입니다 `NorthwindDataSet` `Customers` .

- `Orders`테이블입니다.

- `FK_Orders_Customers`코드 범위에서 사용할 수 있는 두 테이블을 관련 하는 라는 관계

또한 반환 될 레코드에 대 한 데이터를 두 테이블에 채워야 합니다.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>선택한 부모 레코드의 자식 레코드를 반환 하려면

- <xref:System.Data.DataRow.GetChildRows%2A>특정 `Customers` 데이터 행의 메서드를 호출 하 고 테이블에서 행의 배열을 반환 합니다 `Orders` .

     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>선택한 자식 레코드의 부모 레코드를 반환 하려면

- <xref:System.Data.DataRow.GetParentRow%2A>특정 `Orders` 데이터 행의 메서드를 호출 하 고 테이블에서 단일 행을 반환 합니다 `Customers` .

     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
