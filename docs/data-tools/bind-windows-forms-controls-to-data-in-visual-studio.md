---
title: 데이터에 Windows Forms 컨트롤 바인딩
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b6a1d240c865ecc6abddd399c94122a757ee0983
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283010"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Windows Forms 컨트롤을 Visual Studio의 데이터에 바인딩

데이터를 Windows Forms에 바인딩하여 응용 프로그램 사용자에 게 데이터를 표시할 수 있습니다. 이러한 데이터 바인딩된 컨트롤을 만들려면 **데이터 소스** 창에서 Visual Studio의 Windows Forms 디자이너로 항목을 끌어 옵니다.

![데이터 원본 끌기 작업](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> **데이터 소스** 창이 표시 되지 않는 경우 **View**  >  **다른 Windows**  >  **데이터 원본**보기를 선택 하거나 **Shift** + **Alt** + **D**를 눌러 열 수 있습니다. **데이터 소스** 창을 보려면 Visual Studio에서 프로젝트를 열어야 합니다.

항목을 끌기 전에 바인딩하려는 컨트롤의 형식을 설정할 수 있습니다. 테이블 자체를 선택 하는지 아니면 개별 열을 선택 하는지에 따라 다른 값이 표시 됩니다.  사용자 지정 값을 설정할 수도 있습니다. 테이블의 경우 **세부 정보** 는 각 열이 별도의 컨트롤에 바인딩되어 있음을 의미 합니다.

![DataGridView에 데이터 소스 바인딩](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource 및 BindingNavigator 컨트롤

<xref:System.Windows.Forms.BindingSource> 구성 요소는 두가지 용도로 사용됩니다. 먼저 컨트롤을 데이터에 바인딩할 때 추상화 계층을 제공 합니다. 폼의 컨트롤은 <xref:System.Windows.Forms.BindingSource> 데이터 소스에 직접 연결 하는 대신 구성 요소에 바인딩됩니다. 둘째, 개체의 컬렉션을 관리할 수 있습니다. 에 형식을 추가 하면 <xref:System.Windows.Forms.BindingSource> 해당 형식의 목록이 생성 됩니다.

구성 요소에 대 한 자세한 내용은 <xref:System.Windows.Forms.BindingSource> 다음을 참조 하세요.

- [BindingSource 구성 요소](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource 구성 요소 개요](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource 구성 요소 아키텍처](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator 컨트롤](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) 은 Windows 응용 프로그램에 표시 되는 데이터를 탐색 하기 위한 사용자 인터페이스를 제공 합니다.

## <a name="bind-to-data-in-a-datagridview-control"></a>DataGridView 컨트롤의 데이터에 바인딩

[DataGridView 컨트롤](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)의 경우 전체 테이블이 해당 단일 컨트롤에 바인딩됩니다. **DataGridView** 를 폼으로 끌면 레코드 탐색을 위한 도구 스트립 ( <xref:System.Windows.Forms.BindingNavigator> )도 표시 됩니다. [데이터 집합](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md) <xref:System.Windows.Forms.BindingSource> 및가 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다. 다음 그림에서는 Customers 테이블에 Orders 테이블과의 관계가 있으므로 [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) 도 추가 되었습니다. 이러한 변수는 모두 자동 생성 코드에서 form 클래스의 private 멤버로 선언 됩니다. **DataGridView** 를 채우기 위한 자동 생성 코드는 `Form_Load` 이벤트 처리기에 있습니다. 데이터베이스를 업데이트 하기 위해 데이터를 저장 하는 코드는 `Save` **BindingNavigator**에 대 한 이벤트 처리기에 있습니다. 필요에 따라이 코드를 이동 하거나 수정할 수 있습니다.

![BindingNavigator를 사용 하는 GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

각각의 오른쪽 위 모퉁이에 있는 스마트 태그를 클릭 하 여 **DataGridView** 및 **BindingNavigator** 의 동작을 사용자 지정할 수 있습니다.

![DataGridView 및 바인딩 탐색기 스마트 태그](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

응용 프로그램에 필요한 컨트롤을 **데이터 소스** 창에서 사용할 수 없는 경우 컨트롤을 추가할 수 있습니다. 자세한 내용은 [데이터 소스 창에 사용자 지정 컨트롤 추가](../data-tools/add-custom-controls-to-the-data-sources-window.md)를 참조 하세요.

**데이터 소스** 창에서 폼에 이미 있는 컨트롤로 항목을 끌어와 서 컨트롤을 데이터에 바인딩할 수도 있습니다. 이미 데이터에 바인딩된 컨트롤의 데이터 바인딩이 가장 최근에 끌어온 항목으로 다시 설정 됩니다. 유효한 놓기 대상이 되려면 컨트롤이 **데이터 소스** 창에서 끌어 온 항목의 기본 데이터 형식을 표시할 수 있어야 합니다. 예를 들어 데이터 형식이 인 항목을로 끌 수 없습니다 <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> .는 날짜를 표시할 수 없기 때문입니다 <xref:System.Windows.Forms.CheckBox> .

## <a name="bind-to-data-in-individual-controls"></a>개별 컨트롤의 데이터에 바인딩

데이터 소스를 **세부 정보**에 바인딩하는 경우 데이터 집합의 각 열이 별도의 컨트롤에 바인딩됩니다.

![세부 정보에 데이터 소스 바인딩](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> 위의 그림에서는 Orders 테이블이 아니라 Customers 테이블의 Orders 속성에서 끌어 옵니다. 속성에 바인딩하면 `Customer.Orders` **DataGridView** 에서 만든 탐색 명령이 details 컨트롤에 즉시 반영 됩니다. Orders 테이블에서 끌어 오면 컨트롤이 데이터 집합에 계속 바인딩되어 있지만 **DataGridView**와 동기화 되지 않습니다.

다음 그림은 Customers 테이블의 Orders 속성이 **데이터 소스** 창의 **세부 정보** 에 바인딩된 후 폼에 추가 되는 기본 데이터 바인딩된 컨트롤을 보여 줍니다.

![세부 정보에 바인딩된 Orders 테이블](../data-tools/media/raddata-orders-table-bound-to-details.png)

또한 각 컨트롤에는 스마트 태그가 있습니다. 이 태그를 사용 하면 해당 컨트롤에만 적용 되는 사용자 지정이 가능 합니다.

## <a name="see-also"></a>참조

- [Visual Studio의 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows Forms의 데이터 바인딩 (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)
