---
title: 매개 변수가 있는 TableAdapter 쿼리 만들기
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a2b94e10dd09d26a17a7574db97880567f7725cd
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282607"
---
# <a name="create-parameterized-tableadapter-queries"></a>매개 변수가 있는 TableAdapter 쿼리 만들기

매개 변수가 있는 쿼리는 쿼리의 WHERE 절 조건을 충족하는 데이터를 반환합니다. 예를 들어 고객 목록을 반환하는 SQL 문 끝에 `WHERE City = @City`를 추가하여 특정 구/군/시의 고객만 표시하도록 고객 목록을 매개 변수화할 수 있습니다.

**데이터 세트 디자이너**에서 매개 변수가 있는 TableAdapter 쿼리를 만듭니다. **데이터** 메뉴에서 **데이터 소스 매개 변수화** 명령을 사용 하 여 Windows 응용 프로그램에서 만들 수도 있습니다. **데이터 소스 매개 변수화** 명령은 매개 변수 값을 입력 하 고 쿼리를 실행할 수 있는 폼에 컨트롤을 만듭니다.

> [!NOTE]
> 매개 변수가 있는 쿼리를 생성할 때 코딩 하는 데이터베이스와 관련 된 매개 변수 표기법을 사용 합니다. 예를 들어 Access 및 OleDb 데이터 소스는 물음표 '?'를 사용하여 매개 변수를 표기하므로 WHERE 절은 `WHERE City = ?`와 같습니다.

## <a name="create-a-parameterized-tableadapter-query"></a>매개 변수가 있는 TableAdapter 쿼리 만들기

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>데이터 세트 디자이너에서 매개 변수가 있는 쿼리를 만들려면

- 원하는 매개 변수가 포함된 WHERE 절을 SQL 문에 추가하여 새 TableAdapter를 만듭니다. 자세한 내용은 [Tableadapter 만들기 및 구성](../data-tools/create-and-configure-tableadapters.md)을 참조 하세요.

     또는

- 원하는 매개 변수가 포함된 WHERE 절을 SQL 문에 추가하여 기존 TableAdapter에 쿼리를 추가합니다.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>데이터 바인딩된 폼을 디자인하면서 매개 변수가 있는 쿼리를 만들려면

1. 데이터 세트에 이미 바인딩되어 있는 폼의 컨트롤을 선택합니다. 자세한 내용은 [Windows Forms 컨트롤을 Visual Studio의 데이터에 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)을 참조 하세요.

2. **데이터** 메뉴에서 **쿼리 추가**를 선택 합니다.

3. 원하는 매개 변수가 포함된 WHERE 절을 SQL 문에 추가하여 **검색 조건 작성기** 대화 상자에서 필요한 작업을 완료합니다.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>기존 데이터 바인딩된 폼에 쿼리를 추가하려면

1. **Windows Forms 디자이너**에서 폼을 엽니다.

2. **데이터** 메뉴에서 **쿼리 추가** 또는 **데이터 스마트 태그**를 선택 합니다.

    > [!NOTE]
    > **데이터** 메뉴에서 **쿼리 추가**를 사용할 수 없는 경우 매개 변수화를 추가할 데이터 소스가 표시되어 있는 폼의 컨트롤을 선택합니다. 예를 들어 폼의 <xref:System.Windows.Forms.DataGridView> 컨트롤에 데이터가 표시되는 경우 해당 컨트롤을 선택합니다. 폼의 개별 컨트롤에 데이터가 표시되는 경우에는 데이터 바인딩된 컨트롤을 선택합니다.

3. **데이터 원본 테이블 선택** 영역에서 매개 변수화를 추가 하려는 테이블을 선택 합니다.

4. 새 쿼리를 만드는 경우 **새 쿼리 이름** 상자에 이름을 입력합니다.

     또는

     **기존 쿼리 이름** 상자에서 쿼리를 선택합니다.

5. **쿼리 텍스트** 상자에 매개 변수를 사용 하는 쿼리를 입력 합니다.

6. **확인**을 선택합니다.

     매개 변수를 입력하기 위한 컨트롤과 **로드** 단추가 <xref:System.Windows.Forms.ToolStrip> 컨트롤의 폼에 추가됩니다.

### <a name="query-for-null-values"></a>Null 값 쿼리

현재 값이 없는 레코드를 쿼리하려면 TableAdapter 매개 변수에 null 값을 할당할 수 있습니다. 예를 들어, `ShippedDate` 절에 매개 변수가 있는 다음 쿼리를 살펴보세요 `WHERE` .

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

TableAdapter에 대 한 쿼리 인 경우 다음 코드와 함께 제공 되지 않은 모든 주문을 쿼리할 수 있습니다.

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

쿼리가 null 값을 허용 하도록 설정 하려면 다음을 수행 합니다.

1. **데이터 세트 디자이너**에서 null 매개 변수 값을 허용 해야 하는 TableAdapter 쿼리를 선택 합니다.

2. **속성** 창에서 **매개 변수**를 선택 하 고 줄임표 (**...**) 단추를 클릭 하 여 **매개 변수 컬렉션 편집기**를 엽니다.

3. Null 값을 허용 하는 매개 변수를 선택 하 고 **Allowdbnull** 속성을로 설정 `true` 합니다.

## <a name="see-also"></a>참조

- [TableAdapters를 사용하여 데이터 세트 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)
