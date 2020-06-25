---
title: 데이터 바인딩 사용자 지정 개체
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a1d72ed179324b8ab7682e485fbaaf8f34b25cd4
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282932"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Visual Studio에서 개체를 데이터 원본으로 바인딩

Visual Studio는 사용자 지정 개체를 응용 프로그램의 데이터 소스로 사용 하기 위한 디자인 타임 도구를 제공 합니다. UI 컨트롤에 바인딩하는 개체의 데이터베이스에서 데이터를 저장 하려는 경우 Entity Framework를 사용 하 여 클래스를 생성 하는 것이 좋습니다. Entity Framework 모든 상용구 변경 추적 코드를 자동으로 생성 합니다. 즉, DbSet 개체에서 AcceptChanges를 호출 하면 로컬 개체에 대 한 모든 변경 내용이 데이터베이스에 자동으로 유지 됩니다. 자세한 내용은 [Entity Framework 설명서](https://ef.readthedocs.org/en/latest/)를 참조 하세요.

> [!TIP]
> 응용 프로그램이 이미 데이터 집합을 기반으로 하는 경우에만이 문서의 개체 바인딩에 대 한 접근 방식을 고려해 야 합니다. 데이터 집합에 이미 익숙한 경우에도 이러한 접근 방식을 사용할 수 있으며, 처리할 데이터는 테이블 형식이 며 너무 복잡 하거나 너무 크지 않습니다. DataReader를 사용 하 여 개체에 직접 데이터를 로드 하 고 데이터 바인딩을 사용 하지 않고 UI를 수동으로 업데이트 하는 것을 포함 하는 더 간단한 예제를 보려면 [ADO.NET를 사용 하 여 간단한 데이터 응용 프로그램 만들기](../data-tools/create-a-simple-data-application-by-using-adonet.md)

## <a name="object-requirements"></a>개체 요구 사항

Visual Studio에서 데이터 디자인 도구를 사용 하는 사용자 지정 개체의 유일한 요구 사항은 개체에 public 속성이 하나 이상 있어야 한다는 것입니다.

일반적으로 사용자 지정 개체에는 응용 프로그램의 데이터 소스 역할을 하는 특정 인터페이스, 생성자 또는 특성이 필요 하지 않습니다. 그러나 데이터 **소스** 창에서 디자인 화면으로 개체를 끌어 데이터 바인딩된 컨트롤을 만들고 개체가 또는 인터페이스를 구현 하는 경우 <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> 개체에는 기본 생성자가 있어야 합니다. 그렇지 않으면 Visual Studio에서 데이터 소스 개체를 인스턴스화할 수 없으며, 항목을 디자인 화면으로 끌 때 오류가 표시 됩니다.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>사용자 지정 개체를 데이터 원본으로 사용 하는 예

개체를 데이터 원본으로 사용할 때 응용 프로그램 논리를 구현 하는 다양 한 방법이 있지만 SQL 데이터베이스에는 Visual Studio에서 생성 한 TableAdapter 개체를 사용 하 여 단순화할 수 있는 몇 가지 표준 작업이 있습니다. 이 페이지에서는 Tableadapter를 사용 하 여 이러한 표준 프로세스를 구현 하는 방법을 설명 합니다. 사용자 지정 개체를 만드는 방법에 대 한 지침을 제공 하지는 않습니다. 예를 들어 일반적으로 개체의 특정 구현이 나 응용 프로그램의 논리에 관계 없이 다음과 같은 표준 작업을 수행 합니다.

- 데이터를 개체로 로드 (일반적으로 데이터베이스에서)

- 개체의 형식화 된 컬렉션을 만듭니다.

- 컬렉션에서 개체를 추가 하거나 제거 합니다.

- 폼의 사용자에 게 개체 데이터 표시

- 개체의 데이터 변경/편집

- 개체의 데이터를 데이터베이스에 다시 저장 합니다.

### <a name="load-data-into-objects"></a>개체에 데이터 로드

이 예에서는 Tableadapter를 사용 하 여 개체에 데이터를 로드 합니다. 기본적으로 Tableadapter는 데이터베이스에서 데이터를 가져오고 데이터 테이블을 채우는 두 가지 종류의 메서드를 사용 하 여 생성 됩니다.

- `TableAdapter.Fill`메서드는 기존 데이터 테이블을 반환 된 데이터로 채웁니다.

- `TableAdapter.GetData`메서드는 데이터로 채워진 새 데이터 테이블을 반환 합니다.

데이터를 사용 하 여 사용자 지정 개체를 로드 하는 가장 쉬운 방법은 메서드를 호출 하 `TableAdapter.GetData` 고, 반환 된 데이터 테이블의 행 컬렉션을 반복 하 고 각 개체를 각 행의 값으로 채우는 것입니다. `GetData`TableAdapter에 추가 된 쿼리에 대해 채워진 데이터 테이블을 반환 하는 메서드를 만들 수 있습니다.

> [!NOTE]
> Visual Studio는 TableAdapter 쿼리를 `Fill` `GetData` 기본적으로의 이름을 지정할 수 있지만 이러한 이름을 유효한 메서드 이름으로 변경할 수 있습니다.

다음 예에서는 데이터 테이블의 행을 반복 하 고 데이터를 사용 하 여 개체를 채우는 방법을 보여 줍니다.

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>개체의 형식화 된 컬렉션 만들기

개체에 대 한 컬렉션 클래스를 만들거나 [BindingSource 구성 요소](/dotnet/framework/winforms/controls/bindingsource-component)에서 자동으로 제공 하는 형식화 된 컬렉션을 사용할 수 있습니다.

개체에 대 한 사용자 지정 컬렉션 클래스를 만들 때에서 상속 하는 것이 좋습니다 <xref:System.ComponentModel.BindingList%601> . 이 제네릭 클래스는 컬렉션을 관리 하는 기능 뿐만 아니라 Windows Forms의 데이터 바인딩 인프라에 알림을 보내는 이벤트를 발생 시키는 기능을 제공 합니다.

에서 자동으로 생성 된 컬렉션은 <xref:System.Windows.Forms.BindingSource> <xref:System.ComponentModel.BindingList%601> 형식화 된 컬렉션에 대해를 사용 합니다. 응용 프로그램에 추가 기능이 필요 하지 않은 경우 내에서 컬렉션을 유지할 수 있습니다 <xref:System.Windows.Forms.BindingSource> . 자세한 내용은 <xref:System.Windows.Forms.BindingSource.List%2A> 클래스의 속성을 참조 하세요 <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> 컬렉션에의 기본 구현에서 제공 하지 않는 기능이 필요한 경우 필요에 따라 <xref:System.ComponentModel.BindingList%601> 클래스에 추가할 수 있도록 사용자 지정 컬렉션을 만들어야 합니다.

다음 코드에서는 강력한 형식의 개체 컬렉션에 대 한 클래스를 만드는 방법을 보여 줍니다 `Order` .

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>컬렉션에 개체 추가

사용자 지정 컬렉션 클래스 또는의 메서드를 호출 하 여 컬렉션에 개체를 추가 `Add` <xref:System.Windows.Forms.BindingSource> 합니다.

> [!NOTE]
> `Add`에서 상속 하는 경우 사용자 지정 컬렉션에 대해 메서드가 자동으로 제공 됩니다 <xref:System.ComponentModel.BindingList%601> .

다음 코드에서는의 형식화 된 컬렉션에 개체를 추가 하는 방법을 보여 줍니다 <xref:System.Windows.Forms.BindingSource> .

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

다음 코드에서는에서 상속 되는 형식화 된 컬렉션에 개체를 추가 하는 방법을 보여 줍니다 <xref:System.ComponentModel.BindingList%601> .

> [!NOTE]
> 이 예제에서 컬렉션은 `Orders` 개체의 속성입니다 `Customer` .

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>컬렉션에서 개체 제거

`Remove` `RemoveAt` 사용자 지정 컬렉션 클래스 또는의 또는 메서드를 호출 하 여 컬렉션에서 개체를 제거 <xref:System.Windows.Forms.BindingSource> 합니다.

> [!NOTE]
> `Remove` `RemoveAt` 에서 상속 하는 경우 사용자 지정 컬렉션에 대해 및 메서드가 자동으로 제공 됩니다 <xref:System.ComponentModel.BindingList%601> .

다음 코드에서는 메서드를 사용 하 여의 형식화 된 컬렉션에서 개체를 찾고 제거 하는 방법을 보여 줍니다 <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> .

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>사용자에 게 개체 데이터 표시

사용자에 게 개체의 데이터를 표시 하려면 **데이터 소스 구성** 마법사를 사용 하 여 개체 데이터 소스를 만든 다음 **데이터** 소스 창에서 전체 개체 또는 개별 속성을 폼으로 끌어 옵니다.

### <a name="modify-the-data-in-objects"></a>개체의 데이터 수정

Windows Forms 컨트롤에 데이터 바인딩된 사용자 지정 개체의 데이터를 편집 하려면 바인딩된 컨트롤의 데이터를 편집 하거나 개체의 속성에서 직접 편집 하면 됩니다. 데이터 바인딩 아키텍처는 개체의 데이터를 업데이트 합니다.

응용 프로그램에서 변경 내용을 추적 해야 하 고 제안 된 변경 내용을 원래 값으로 롤백하는 경우 개체 모델에서이 기능을 구현 해야 합니다. 데이터 테이블에서 제안 된 변경 내용을 추적 하는 방법에 대 한 예는, 및을 참조 하십시오 <xref:System.Data.DataRowState> <xref:System.Data.DataSet.HasChanges%2A> <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="save-data-in-objects-back-to-the-database"></a>개체의 데이터를 데이터베이스에 다시 저장 합니다.

개체의 값을 TableAdapter의 DBDirect 메서드로 전달 하 여 데이터를 다시 데이터베이스에 저장 합니다.

Visual Studio는 데이터베이스에 대해 직접 실행할 수 있는 DBDirect 메서드를 만듭니다. 이러한 메서드에는 DataSet 또는 DataTable 개체가 필요 하지 않습니다.

|TableAdapter DBDirect 메서드|설명|
| - |-----------------|
|`TableAdapter.Insert`|데이터베이스에 새 레코드를 추가 하 여 개별 열 값을 메서드 매개 변수로 전달할 수 있도록 합니다.|
|`TableAdapter.Update`|데이터베이스의 기존 레코드를 업데이트 합니다. Update 메서드는 원래 열 값과 새 열 값을 메서드 매개 변수로 사용 합니다. 원래 값을 사용 하 여 원래 레코드를 찾은 다음 새 값을 사용 하 여 해당 레코드를 업데이트 합니다.<br /><br /> 메서드는의,, `TableAdapter.Update` <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> 또는 배열을 <xref:System.Data.DataRow> 메서드 매개 변수로 사용 하 여 데이터 집합의 변경 내용을 데이터베이스에 다시 조정 하는 데도 사용 됩니다.|
|`TableAdapter.Delete`|메서드 매개 변수로 전달 된 원래 열 값을 기준으로 데이터베이스에서 기존 레코드를 삭제 합니다.|

개체의 컬렉션에서 데이터를 저장 하려면 개체의 컬렉션을 반복 합니다. 예를 들어 for next 루프를 사용 합니다. TableAdapter의 DBDirect 메서드를 사용 하 여 각 개체의 값을 데이터베이스로 보냅니다.

다음 예에서는 dbdirect 메서드를 사용 하 여 `TableAdapter.Insert` 새 고객을 데이터베이스에 직접 추가 하는 방법을 보여 줍니다.

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>참조

- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
